# Projeto — Assistente de Migração e Backup Inteligente para Windows

## Visão Geral
Este projeto tem como objetivo criar um **assistente inteligente de backup, formatação e migração de computadores Windows**, inspirado no conceito de ferramentas como o *Samsung Smart Switch*, porém adaptado à complexidade e abertura do ecossistema Windows.

A proposta central é **reduzir o medo, o tempo e a incerteza** associados a processos como:
- formatação do sistema
- troca de computador
- migração para um novo SSD
- reinstalação limpa do Windows

O programa atua como um **centralizador de informações**, analisando o computador do usuário, apresentando esses dados de forma visual e compreensível, e guiando decisões de backup e restauração de maneira consciente.

> **Você não faz backup para salvar arquivos.\
Você faz backup para poder apagar sem medo.**

---

## Objetivo do Programa

- Analisar automaticamente o computador Windows
- Identificar programas instalados, dados pessoais e dependências
- Apresentar essas informações em **dashboards visuais simples**
- Permitir que o usuário **escolha conscientemente** o que será levado
- Executar cópias apenas quando houver espaço e condições seguras
- Gerar um arquivo de instruções próprio para restauração futura
- Facilitar a reinstalação e restauração após uma formatação limpa

O foco não é apenas copiar dados, mas **explicar o que existe no sistema** e **dar controle ao usuário**.

---

## Filosofia do Projeto

Este projeto parte de alguns princípios fundamentais:

- **Transparência acima de automação cega**  
  O usuário deve entender o que está acontecendo, mesmo que não seja técnico.

- **Falhar é melhor do que mentir**  
  Se um backup não puder ser validado ou estiver corrompido, ele não pode ser considerado bem-sucedido.

- **Visualização é parte da solução**  
  Dashboards, ícones e agrupamentos não são estética — são explicação.

- **Controle progressivo**  
  O programa deve funcionar para quem quer apenas “resolver”, mas permitir aprofundamento para quem quiser entender mais.

- **Produto antes de método**  
  O software existe para reduzir esforço humano, não para exigir que o usuário siga manuais complexos.

---

## O que este projeto NÃO é

Para evitar ambiguidades de escopo, este projeto **não pretende ser**:

- Um clonador de disco bit a bit
- Um gerenciador de pacotes (como winget ou chocolatey)
- Um otimizador ou debloater de Windows
- Uma ferramenta que promete que “tudo ficará exatamente igual”
- Uma solução fechada ou caixa-preta

O programa **não substitui** ferramentas especializadas, mas **orquestra e explica** processos que hoje são fragmentados.

---

## Estado Atual do Projeto

Este README representa uma **versão inicial e não definitiva**.

O projeto encontra-se na fase de:
- definição de escopo
- consolidação de objetivos
- levantamento conceitual

A arquitetura técnica, tecnologias específicas e implementação ainda serão definidas e podem mudar ao longo do desenvolvimento.

---

## Evolução

Este documento será atualizado continuamente conforme:
- o escopo amadurecer
- decisões forem validadas
- limitações forem descobertas
- funcionalidades forem testadas na prática

Ele deve ser encarado como um **documento vivo**, não como especificação final.

