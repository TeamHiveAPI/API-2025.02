# 📋 DoR - US #2: Gestão de Perfis

## 🎯 User Story
**Como coronel, desejo visualizar e gerenciar perfis (meu, de tenentes e de soldados) para manter as informações atualizadas.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Gestão de Perfis"
  - ✅ Descrição: Sistema administrativo para gerenciar perfis de usuários
  - ✅ Objetivo: Manter informações atualizadas e controle de acesso

- [x] **Critérios de aceitação escritos**
  - ✅ Ver seção "Critérios de Aceitação" abaixo

- [x] **Regras de negócio claras**
  - ✅ Ver seção "Regras de Negócio" abaixo

- [x] **Foi estimada pela equipe**
  - ✅ Estimativa: 8 Story Points
  - ✅ Validação: Planning Poker realizado em 05/10/2024

- [x] **Sem dependências bloqueadoras**
  - ✅ Dependências identificadas e resolvidas
  - ✅ Ver seção "Dependências" abaixo

- [x] **Compreensão validada com o time**
  - ✅ Reunião de alinhamento realizada em 05/10/2024
  - ✅ Todos os membros compreendem o escopo

### 📋 Sobre artefatos correlatos às User Stories:
- [x] **Design/documentação disponível**
  - ✅ Protótipo no Figma: [Link do Protótipo]
  - ✅ Wireframes de administração criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Visualização de Perfis
- **DADO** que sou um coronel
- **QUANDO** acesso o módulo de gestão de perfis
- **ENTÃO** devo conseguir visualizar:
  - Lista de todos os usuários do sistema
  - Informações básicas (nome, patente, setor)
  - Status ativo/inativo
  - Data de último acesso
  - Permissões atribuídas

### CA2 - Edição de Perfil Próprio
- **DADO** que sou um coronel
- **QUANDO** acesso meu próprio perfil
- **ENTÃO** devo conseguir editar:
  - Dados pessoais (nome, email, telefone)
  - Foto de perfil
  - Senha de acesso
  - Preferências do sistema

### CA3 - Gerenciamento de Tenentes
- **DADO** que sou um coronel
- **QUANDO** gerencio perfis de tenentes
- **ENTÃO** devo conseguir:
  - Ativar/inativar contas
  - Alterar permissões de acesso
  - Definir setor de atuação
  - Visualizar histórico de atividades

### CA4 - Gerenciamento de Soldados
- **DADO** que sou um coronel
- **QUANDO** gerencio perfis de soldados
- **ENTÃO** devo conseguir:
  - Criar novos perfis
  - Atribuir patente e setor
  - Definir permissões básicas
  - Associar a um tenente responsável

### CA5 - Controle de Permissões
- **DADO** que sou um coronel
- **QUANDO** defino permissões
- **ENTÃO** devo conseguir:
  - Atribuir módulos de acesso
  - Definir níveis de permissão
  - Configurar restrições por setor
  - Visualizar matriz de permissões

## 📋 Regras de Negócio

### RN1 - Hierarquia de Acesso
- Coronel tem acesso total ao sistema
- Tenentes têm acesso limitado ao seu setor
- Soldados têm acesso apenas às funcionalidades básicas
- Não é possível dar permissões superiores ao próprio nível

### RN2 - Gestão de Contas
- Apenas coronéis podem criar/editar perfis de tenentes
- Tenentes podem visualizar soldados do seu setor
- Contas inativas não podem fazer login
- Histórico de alterações deve ser mantido

### RN3 - Segurança
- Senhas devem ter complexidade mínima
- Alterações críticas requerem confirmação
- Logs de acesso devem ser mantidos
- Sessões expiram após inatividade

## 🗄️ Modelo de Dados

### Tabela: usuarios
```sql
- id (PK)
- nome_completo
- email
- telefone
- patente
- setor_id (FK)
- supervisor_id (FK)
- foto_perfil
- ativo (boolean)
- ultimo_acesso
- created_at
- updated_at
```

### Tabela: permissoes
```sql
- id (PK)
- nome_permissao
- descricao
- modulo
- nivel_acesso
- created_at
```

### Tabela: usuario_permissoes
```sql
- id (PK)
- usuario_id (FK)
- permissao_id (FK)
- atribuido_por (FK)
- data_atribuicao
- ativo (boolean)
```

### Tabela: logs_acesso
```sql
- id (PK)
- usuario_id (FK)
- acao_realizada
- ip_acesso
- user_agent
- data_acesso
- resultado (sucesso/erro)
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de campos obrigatórios
- Regras de hierarquia
- Cálculo de permissões
- Validação de senhas

### Testes de Integração
- CRUD completo de usuários
- Sistema de permissões
- Logs de acesso
- Notificações de alterações

### Testes de Interface
- Navegação administrativa
- Responsividade
- Validação de formulários
- Feedback de ações

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de notificações (já implementado)
- ✅ Sistema de logs (já implementado)

### Dependências Externas
- ✅ Sistema de email (já integrado)
- ✅ Serviço de upload de imagens (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Diogo
- **Data de Início:** 07/10/2024
- **Data de Conclusão:** 18/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Criar modelos de dados
   - Implementar APIs de usuários
   - Sistema de permissões
   - Logs de auditoria

2. **Frontend (24h)**
   - Interface administrativa
   - Formulários de edição
   - Listagem de usuários
   - Dashboard de gestão

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de segurança

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 05/10/2024  
**Responsável pela Validação:** Diogo Palharini  
**Próximo Passo:** Iniciar desenvolvimento
