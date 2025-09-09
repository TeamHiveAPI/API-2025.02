# 🌳 Estrutura de Branches do Projeto

O fluxo de desenvolvimento do projeto segue uma organização baseada em **branches por atividade**, **branch de desenvolvimento (dev)** e **branch principal (main)**.  

---

## 🚀 Fluxo de Trabalho das Branches

1. **Branches de Atividade**
   - Cada tarefa da sprint deve ser desenvolvida em uma branch específica.  
   - Nome da branch: `##<número-da-task>-<descrição>`  
     - Exemplo: `##1-criar-botao`
   - Após concluir a atividade, o desenvolvedor abre um **Pull Request (PR)** para a branch `dev`.

2. **Branch de Desenvolvimento (dev)**
   - Centraliza todas as tarefas concluídas da sprint.  
   - Cada PR de branch de atividade passa por **validação e QA**.  
   - Caso o PR seja **aprovado**, a branch de atividade é integrada à `dev`.  
   - Caso o PR seja **rejeitado**, a correção deve ser feita na **branch da atividade** e reenviada para `dev`.

3. **Branch Principal (main)**
   - Após todas as tarefas da sprint serem integradas e a `dev` estar devidamente **testada e estável**, um membro da equipe abre um **Pull Request da `dev` para a `main`**.  
   - A `main` sempre representará a versão mais estável e pronta para produção.

---

## 🔄 Ciclo por Sprint
- O processo se repete por **3 sprints**, seguindo este fluxo:
  1. Desenvolvimento das atividades → Pull Request para `dev`
  2. Testes e QA → Correções se necessário
  3. Integração de `dev` → Pull Request para `main`