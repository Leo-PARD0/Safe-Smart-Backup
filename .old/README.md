# Método de Backup, Formatação e Restauração Consciente

> Este documento descreve um processo de provisionamento de sistema.  
> Ele não define softwares específicos, mas critérios claros para decidir o que deve ou não fazer parte de uma instalação base.

---

## Passo 1 — Discriminação de Espaço

### Objetivo

Antes de qualquer ação de backup ou formatação, o usuário deve **entender como o espaço em disco está sendo utilizado**.

Este passo existe para permitir uma decisão consciente entre:
- backup completo do sistema
- backup parcial (somente dados)
- ou criação apenas de uma imagem de segurança

Nenhuma ação destrutiva deve ser realizada antes da conclusão deste passo.

---

### Conceito-chave

> **Backup não começa copiando arquivos. Começa entendendo o espaço.**

Sem essa discriminação inicial, o processo tende a:
- preservar lixo desnecessário
- perder dados importantes
- ou gerar reinstalações caóticas após a formatação

---

### O que deve ser identificado

O usuário deve ser capaz de responder, de forma objetiva:

1. Quanto espaço está ocupado no disco principal
2. Quanto desse espaço corresponde a **arquivos**
3. Quanto desse espaço corresponde a **programas**

Não é necessário precisão absoluta, apenas **clareza suficiente para tomada de decisão**.

---

### Classificação inicial de espaço

O método trabalha, neste primeiro momento, com apenas **duas categorias**:

#### 1. Arquivos (Dados)

Incluem, mas não se limitam a:
- Documentos
- Imagens
- Vídeos
- Downloads
- Projetos
- Arquivos pessoais em geral

Características:
- Alto valor pessoal
- Difícil ou impossível de substituir
- Devem ser preservados independentemente da reinstalação de software

---

#### 2. Programas (Software)

Incluem:
- Aplicações instaladas
- Jogos
- Ferramentas
- Dependências
- Componentes auxiliares

Características:
- Reinstaláveis
- Dependem de decisão
- Nem tudo precisa ser restaurado

---

### Decisão resultante

Com base na discriminação de espaço, o usuário deve decidir qual abordagem seguir:

#### Backup Completo
Recomendado quando:
- A maior parte do espaço ocupado é composta por arquivos
- O sistema possui muitas customizações
- O usuário deseja uma rede de segurança total

#### Backup Parcial
Recomendado quando:
- Arquivos estão bem organizados e separados
- Programas podem ser reinstalados posteriormente
- O objetivo é limpeza e otimização do sistema

---

### Resultado esperado

Ao final do Passo 1, o usuário deve ter:

- Clareza sobre o uso real do disco
- Consciência do que é dado e do que é software
- Base objetiva para decidir o tipo de backup
- Nenhuma modificação feita no sistema

---

### Regra de ouro

> **Nenhum processo de formatação deve continuar se o usuário não souber explicar, em uma frase, o que ocupa o disco.**

---
