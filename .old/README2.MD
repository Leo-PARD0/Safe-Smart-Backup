## 1️⃣ Regra oficial de classificação (que vira código)

O método vai classificar por localização, que é o critério mais estável e replicável:

### Local do arquivo	Classificação
```powershell
C:\Windows\*	Reinstalável
C:\Program Files*\*	Reinstalável
C:\ProgramData\*	Cinza
C:\Users\<usuario>\AppData\*	Cinza
C:\Users\<usuario>\* (fora AppData)	Único
```

#### Regra-mãe do método
```
Classificação é feita pela capacidade de recuperação, não pelo tipo de arquivo.
```

## 2️⃣ COMANDO ÚNICO — auditoria completa + classificação + CSV

👉 Copiar, colar e executar no PowerShell
(sem precisar rodar como admin)
```powershell
$BaseOutput = "$env:USERPROFILE\Desktop\auditoria"
New-Item -ItemType Directory -Path $BaseOutput -Force | Out-Null

$Paths = @(
    "C:\Windows",
    "C:\Program Files",
    "C:\Program Files (x86)",
    "C:\ProgramData",
    "C:\Users\$env:USERNAME"
)

# Coleta base
$Files = Get-ChildItem $Paths -Recurse -File -Force -ErrorAction SilentlyContinue |
Where-Object { -not ($_.Attributes -band [IO.FileAttributes]::ReparsePoint) } |
Select-Object `
    FullName,
    @{Name="TamanhoMB"; Expression = { [math]::Round($_.Length / 1MB, 2) }},
    @{Name="Classificacao"; Expression = {
        if ($_.FullName -like "C:\Windows\*" -or
            $_.FullName -like "C:\Program Files\*" -or
            $_.FullName -like "C:\Program Files (x86)\*") {
            "Reinstalável"
        }
        elseif ($_.FullName -like "C:\ProgramData\*" -or
                $_.FullName -like "C:\Users\$env:USERNAME\AppData\*") {
            "Cinza"
        }
        else {
            "Único"
        }
    }}

# -----------------------------
# 1️⃣ RESUMO POR CLASSIFICAÇÃO
# -----------------------------
$ResumoClassificacao = $Files |
Group-Object Classificacao |
ForEach-Object {
    $Total = ($_.Group | Measure-Object TamanhoMB -Sum).Sum
    [PSCustomObject]@{
        Classificacao = $_.Name
        TamanhoMB     = [math]::Round($Total, 2)
    }
}

$TotalGeral = ($ResumoClassificacao | Measure-Object TamanhoMB -Sum).Sum

$ResumoClassificacao |
Select-Object *,
    @{Name="Percentual"; Expression = {
        [math]::Round(($_.TamanhoMB / $TotalGeral) * 100, 2)
    }} |
Export-Csv "$BaseOutput\01_resumo_classificacao.csv" -NoTypeInformation -Encoding UTF8

# -----------------------------
# 2️⃣ RESUMO POR DIRETÓRIO (CINZA + ÚNICO)
# -----------------------------
$Files |
Where-Object { $_.Classificacao -ne "Reinstalável" } |
Group-Object {
    ($_ .FullName -split '\\')[0..3] -join '\'
} |
ForEach-Object {
    [PSCustomObject]@{
        Diretorio  = $_.Name
        Classificacao = ($_.Group | Select-Object -First 1).Classificacao
        TamanhoMB = [math]::Round(
            ($_.Group | Measure-Object TamanhoMB -Sum).Sum, 2
        )
    }
} |
Sort-Object TamanhoMB -Descending |
Export-Csv "$BaseOutput\02_diretorios_relevantes.csv" -NoTypeInformation -Encoding UTF8

# -----------------------------
# 3️⃣ INVENTÁRIO COMPLETO (OPCIONAL)
# -----------------------------
$Files |
Export-Csv "$BaseOutput\03_inventario_completo.csv" -NoTypeInformation -Encoding UTF8

$BaseOutput

```

Ao final, ele retorna o caminho do arquivo gerado, para não deixar dúvida.

## 3️⃣ O que você recebe no CSV (final, único, definitivo)

O arquivo auditoria_completa.csv terá:

Coluna	O que é
FullName	Caminho completo do arquivo
TamanhoMB	Tamanho real
LastWriteTime	Última modificação
Classificacao	Reinstalável / Cinza / Único

#### 👉 Esse CSV pode ser:

aberto no Excel
importado no Google Sheets
filtrado
ordenado
usado como checklist
versionado
reutilizado daqui a 2, 5 ou 10 anos