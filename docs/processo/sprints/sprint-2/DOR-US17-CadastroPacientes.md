# 📋 DoR - US #17: Cadastro de Pacientes

## 🎯 User Story
**Como usuário interno, desejo cadastrar pacientes e os tipos de exames oferecidos, especificando preparo e documentos necessários.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Cadastro de Pacientes"
  - ✅ Descrição: Sistema para cadastrar pacientes e tipos de exames
  - ✅ Objetivo: Centralizar informações de pacientes e padronizar exames

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

### CA1 - Cadastro de Paciente
- **DADO** que sou um usuário interno
- **QUANDO** acesso o módulo de pacientes
- **ENTÃO** devo conseguir cadastrar:
  - Nome completo (obrigatório)
  - Data de nascimento (obrigatório)
  - CPF (obrigatório, com validação)
  - RG (obrigatório)
  - Telefone (obrigatório)
  - E-mail (opcional)
  - Endereço completo (obrigatório)
  - Contato de emergência (obrigatório)
  - Observações médicas (opcional)

### CA2 - Cadastro de Tipos de Exames
- **DADO** que sou um usuário interno
- **QUANDO** acesso o módulo de tipos de exames
- **ENTÃO** devo conseguir cadastrar:
  - Nome do exame (obrigatório)
  - Código do exame (obrigatório, único)
  - Descrição detalhada (obrigatório)
  - Duração estimada (obrigatório)
  - Preparo necessário (obrigatório)
  - Documentos necessários (obrigatório)
  - Validade do resultado (opcional)
  - Observações (opcional)

### CA3 - Especificação de Preparo
- **DADO** que estou cadastrando um tipo de exame
- **QUANDO** defino o preparo necessário
- **ENTÃO** devo conseguir especificar:
  - Jejum necessário (sim/não e duração)
  - Medicamentos a suspender
  - Restrições alimentares
  - Instruções específicas
  - Tempo de preparo necessário

### CA4 - Documentos Necessários
- **DADO** que estou cadastrando um tipo de exame
- **QUANDO** defino os documentos necessários
- **ENTÃO** devo conseguir especificar:
  - Requisição médica (obrigatório/opcional)
  - Identidade com foto (obrigatório/opcional)
  - Cartão do SUS (obrigatório/opcional)
  - Outros documentos específicos
  - Validade dos documentos

### CA5 - Consulta e Edição
- **DADO** que tenho pacientes e exames cadastrados
- **QUANDO** consulto os dados
- **ENTÃO** devo conseguir:
  - Buscar pacientes por nome ou CPF
  - Filtrar tipos de exames por categoria
  - Editar informações de pacientes
  - Editar tipos de exames
  - Visualizar histórico de alterações

### CA6 - Validação de Dados
- **DADO** que estou cadastrando/editando dados
- **QUANDO** preencho os campos obrigatórios
- **ENTÃO** o sistema deve:
  - Validar formato do CPF
  - Verificar se CPF já existe
  - Validar formato do RG
  - Validar formato do telefone
  - Validar formato do e-mail
  - Mostrar mensagens de erro claras

## 📋 Regras de Negócio

### RN1 - Validação de CPF
- CPF deve ser único no sistema
- Deve seguir formato válido (XXX.XXX.XXX-XX)
- Sistema deve validar dígitos verificadores
- CPF inativo pode ser reativado

### RN2 - Gestão de Pacientes
- Pacientes podem ser ativos ou inativos
- Apenas pacientes ativos podem fazer exames
- Inativação não exclui dados históricos
- Reativação mantém histórico

### RN3 - Tipos de Exames
- Código do exame deve ser único
- Exames podem ser ativos ou inativos
- Exames inativos não aparecem em agendamentos
- Alterações são registradas com usuário responsável

### RN4 - Controle de Acesso
- Apenas usuários internos podem cadastrar pacientes
- Alterações são registradas com usuário responsável
- Sistema mantém logs de auditoria
- Backup automático dos dados

## 🗄️ Modelo de Dados

### Tabela: pacientes
```sql
- id (PK)
- nome_completo (obrigatório)
- data_nascimento (obrigatório)
- cpf (obrigatório, único)
- rg (obrigatório)
- telefone (obrigatório)
- email
- endereco_completo (obrigatório)
- contato_emergencia_nome (obrigatório)
- contato_emergencia_telefone (obrigatório)
- observacoes_medicas
- ativo (boolean, default true)
- created_at
- updated_at
- created_by (FK usuarios)
- updated_by (FK usuarios)
```

### Tabela: tipos_exames
```sql
- id (PK)
- nome_exame (obrigatório)
- codigo_exame (obrigatório, único)
- descricao_detalhada (obrigatório)
- duracao_estimada (obrigatório)
- preparo_necessario (obrigatório)
- documentos_necessarios (obrigatório)
- validade_resultado
- observacoes
- ativo (boolean, default true)
- created_at
- updated_at
- created_by (FK usuarios)
- updated_by (FK usuarios)
```

### Tabela: preparo_exames
```sql
- id (PK)
- tipo_exame_id (FK)
- tipo_preparo (jejum/medicamento/restricao/instrucao)
- descricao_preparo
- duracao_preparo
- obrigatorio (boolean)
- ordem_exibicao
```

### Tabela: documentos_exames
```sql
- id (PK)
- tipo_exame_id (FK)
- tipo_documento
- descricao_documento
- obrigatorio (boolean)
- validade_dias
- observacoes
```

### Tabela: paciente_historico
```sql
- id (PK)
- paciente_id (FK)
- campo_alterado
- valor_anterior
- valor_novo
- usuario_id (FK)
- data_alteracao
- motivo_alteracao
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de CPF
- Validação de campos obrigatórios
- Regras de negócio
- Cálculos de campos

### Testes de Integração
- CRUD completo de pacientes
- CRUD completo de tipos de exames
- Sistema de histórico
- Validações de unicidade

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

### Dependências Externas
- ✅ Serviço de validação de CPF (já integrado)
- ✅ Serviço de validação de e-mail (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 5
- **Desenvolvedor Responsável:** Gabriel
- **Data de Início:** 07/10/2024
- **Data de Conclusão:** 11/10/2024
- **Horas Estimadas:** 40 horas

## 📋 Tarefas Técnicas

1. **Backend (20h)**
   - Criar modelos de dados
   - Implementar APIs de pacientes
   - Implementar APIs de tipos de exames
   - Sistema de validação

2. **Frontend (16h)**
   - Interface de cadastro de pacientes
   - Interface de cadastro de exames
   - Listagem e filtros
   - Formulários de edição

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Gabriel Santos  
**Próximo Passo:** Iniciar desenvolvimento
