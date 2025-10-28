# 📋 DoR - US #14: Gestão de Fornecedores

## 🎯 User Story
**Como tenente de almoxarifado, desejo cadastrar, editar e consultar fornecedores (Razão Social, CNPJ, e-mail, responsável) para centralizar a gestão de contatos.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Gestão de Fornecedores"
  - ✅ Descrição: Sistema para cadastrar e gerenciar fornecedores
  - ✅ Objetivo: Centralizar informações de fornecedores para facilitar comunicação

- [x] **Critérios de aceitação escritos**
  - ✅ Ver seção "Critérios de Aceitação" abaixo

- [x] **Regras de negócio claras**
  - ✅ Ver seção "Regras de Negócio" abaixo

- [x] **Foi estimada pela equipe**
  - ✅ Estimativa: 5 Story Points
  - ✅ Validação: Planning Poker realizado em 06/10/2024

- [x] **Sem dependências bloqueadoras**
  - ✅ Dependências identificadas e resolvidas
  - ✅ Ver seção "Dependências" abaixo

- [x] **Compreensão validada com o time**
  - ✅ Reunião de alinhamento realizada em 06/10/2024
  - ✅ Todos os membros compreendem o escopo

### 📋 Sobre artefatos correlatos às User Stories:
- [x] **Design/documentação disponível**
  - ✅ Protótipo no Figma: [Link do Protótipo]
  - ✅ Wireframes de cadastro criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Cadastro de Fornecedor
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** acesso o módulo de fornecedores
- **ENTÃO** devo conseguir cadastrar:
  - Razão Social (obrigatório)
  - CNPJ (obrigatório, com validação)
  - E-mail (obrigatório, com validação)
  - Telefone (opcional)
  - Nome do responsável (obrigatório)
  - Endereço completo (obrigatório)
  - Observações (opcional)

### CA2 - Edição de Fornecedor
- **DADO** que tenho fornecedores cadastrados
- **QUANDO** seleciono um fornecedor para editar
- **ENTÃO** devo conseguir:
  - Alterar todos os dados cadastrais
  - Ativar/inativar fornecedor
  - Adicionar observações
  - Visualizar histórico de alterações

### CA3 - Consulta de Fornecedores
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** acesso a lista de fornecedores
- **ENTÃO** devo conseguir:
  - Visualizar lista paginada
  - Filtrar por status (ativo/inativo)
  - Buscar por razão social ou CNPJ
  - Ordenar por data de cadastro
  - Exportar lista em PDF/Excel

### CA4 - Validação de Dados
- **DADO** que estou cadastrando/editando um fornecedor
- **QUANDO** preencho os campos obrigatórios
- **ENTÃO** o sistema deve:
  - Validar formato do CNPJ
  - Validar formato do e-mail
  - Verificar se CNPJ já existe
  - Verificar se e-mail já existe
  - Mostrar mensagens de erro claras

### CA5 - Histórico e Auditoria
- **DADO** que faço alterações em fornecedores
- **QUANDO** modifico dados de um fornecedor
- **ENTÃO** o sistema deve:
  - Registrar quem fez a alteração
  - Registrar data e hora da alteração
  - Manter histórico de mudanças
  - Permitir visualizar histórico

## 📋 Regras de Negócio

### RN1 - Validação de CNPJ
- CNPJ deve ser único no sistema
- Deve seguir formato válido (XX.XXX.XXX/XXXX-XX)
- Sistema deve validar dígitos verificadores
- CNPJ inativo pode ser reativado

### RN2 - Gestão de Status
- Fornecedores podem ser ativos ou inativos
- Apenas fornecedores ativos aparecem em pedidos
- Inativação não exclui dados históricos
- Reativação mantém histórico

### RN3 - Controle de Acesso
- Apenas tenentes de almoxarifado podem gerenciar fornecedores
- Alterações são registradas com usuário responsável
- Sistema mantém logs de auditoria
- Backup automático dos dados

## 🗄️ Modelo de Dados

### Tabela: fornecedores
```sql
- id (PK)
- razao_social (obrigatório)
- cnpj (obrigatório, único)
- email (obrigatório, único)
- telefone
- nome_responsavel (obrigatório)
- endereco_completo (obrigatório)
- observacoes
- ativo (boolean, default true)
- created_at
- updated_at
- created_by (FK usuarios)
- updated_by (FK usuarios)
```

### Tabela: fornecedor_historico
```sql
- id (PK)
- fornecedor_id (FK)
- campo_alterado
- valor_anterior
- valor_novo
- usuario_id (FK)
- data_alteracao
- motivo_alteracao
```

### Tabela: fornecedor_contatos
```sql
- id (PK)
- fornecedor_id (FK)
- tipo_contato (email/telefone)
- valor_contato
- principal (boolean)
- ativo (boolean)
- created_at
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de CNPJ
- Validação de e-mail
- Regras de negócio
- Cálculos de campos

### Testes de Integração
- CRUD completo de fornecedores
- Sistema de histórico
- Validações de unicidade
- Exportação de dados

### Testes de Interface
- Formulários de cadastro
- Listagem e filtros
- Responsividade
- Validação de campos

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de usuários (já implementado)
- ✅ Sistema de logs (já implementado)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de validação de CNPJ (já integrado)
- ✅ Serviço de e-mail (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 5
- **Desenvolvedor Responsável:** Eber
- **Data de Início:** 07/10/2024
- **Data de Conclusão:** 11/10/2024
- **Horas Estimadas:** 40 horas

## 📋 Tarefas Técnicas

1. **Backend (20h)**
   - Criar modelos de dados
   - Implementar APIs de fornecedores
   - Sistema de validação
   - Histórico de alterações

2. **Frontend (16h)**
   - Interface de cadastro
   - Listagem e filtros
   - Formulários de edição
   - Exportação de dados

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Eber de Souza Junior  
**Próximo Passo:** Iniciar desenvolvimento
