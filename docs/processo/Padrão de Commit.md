# 📝 Guia de Commits - Team HIVE  

Para manter a **consistência** e a **clareza** no repositório, todos os commits devem seguir o padrão definido pelo **Team HIVE**.  

---

## 📌 Formato do Commit  

```bash
<tipo>: #<numero-da-task> <descrição em gerúndio>
<informações adicionais (opcional)>
```

---

## 🔖 Tipos de Commit

- **fix** – Correção de bug (equivale ao **PATCH** no versionamento semântico).  
- **feat** – Novo recurso (equivale ao **MINOR** no versionamento semântico).  
- **docs** – Mudanças apenas em documentação (ex: README).  
- **style** – Alterações de formatação de código (pontos e vírgulas, espaços, lint).  
- **refactor** – Refatoração sem alterar comportamento (ex: melhoria de performance).  
- **build** – Alterações em arquivos de build ou dependências.  
- **test** – Criação, alteração ou remoção de testes.  
- **chore** – Tarefas administrativas ou de configuração (ex: atualizar `.gitignore`).  



## 📝 Exemplos de Commits

```bash
fix: #045 corrigindo erro de null pointer no cadastro de usuário
```
```bash
feat: #078 implementando upload de imagens no perfil
```
```bash
docs: #101 atualizando guia de instalação no README
```
```bash
style: #056 ajustando indentação e removendo espaços desnecessários
```
```bash
refactor: #089 melhorando performance da consulta no banco
```
---

## 🔀 Padrão de Merge  

Os merges devem seguir o seguinte formato:  

```bash
[MERGE] #<numero-da-task> <tipo-de-commit>: <mensagem>
```

## 📝 Exemplos de Merge
```bash
[MERGE] #31 feat: adicionando componente de tabela dinâmica
```
```bash
[MERGE] #42 fix: corrigindo bug no fluxo de autenticação
```
```bash
[MERGE] #57 docs: atualizando documentação da API
```
```bash
[MERGE] #64 refactor: reorganizando serviços de domínio
```
```bash
[MERGE] #78 style: padronizando espaçamentos no código
```
