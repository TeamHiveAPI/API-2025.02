# 📋 DoR - US #18: Agendamento de Exames

## 🎯 User Story
**Como usuário interno, desejo agendar exames para pacientes, buscando por data e horário, e gerenciar o status do agendamento (confirmado, cancelado, não compareceu).**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Agendamento de Exames"
  - ✅ Descrição: Sistema para agendar exames para pacientes
  - ✅ Objetivo: Facilitar o agendamento de exames médicos

- [x] **Critérios de aceitação escritos**
  - ✅ Ver seção "Critérios de Aceitação" abaixo

- [x] **Regras de negócio claras**
  - ✅ Ver seção "Regras de Negócio" abaixo

- [x] **Foi estimada pela equipe**
  - ✅ Estimativa: 8 Story Points
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
  - ✅ Wireframes de agendamento criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Seleção de Paciente e Exame
- **DADO** que sou um usuário interno
- **QUANDO** acesso o módulo de agendamento
- **ENTÃO** devo conseguir:
  - Buscar paciente por nome ou CPF
  - Selecionar tipo de exame disponível
  - Visualizar preparo necessário
  - Ver documentos necessários

### CA2 - Busca por Data e Horário
- **DADO** que selecionei paciente e exame
- **QUANDO** escolho a data desejada
- **ENTÃO** devo ver:
  - Calendário com datas disponíveis
  - Horários disponíveis por data
  - Duração estimada do exame
  - Local do exame
  - Profissional responsável

### CA3 - Confirmação do Agendamento
- **DADO** que escolhi data e horário
- **QUANDO** confirmo o agendamento
- **ENTÃO** devo conseguir:
  - Preencher dados do agendamento
  - Adicionar observações
  - Confirmar documentos necessários
  - Receber confirmação do agendamento
  - Gerar número de protocolo

### CA4 - Gestão de Status
- **DADO** que tenho agendamentos realizados
- **QUANDO** gerencio o status dos agendamentos
- **ENTÃO** devo conseguir alterar para:
  - Confirmado (padrão)
  - Cancelado (com motivo)
  - Não compareceu (com observações)
  - Realizado (após exame)

### CA5 - Notificações e Lembretes
- **DADO** que um agendamento é confirmado
- **QUANDO** o agendamento é registrado
- **ENTÃO** o sistema deve:
  - Enviar confirmação por e-mail/SMS
  - Enviar lembrete 24h antes
  - Enviar instruções de preparo
  - Notificar sobre documentos necessários

### CA6 - Consulta de Agendamentos
- **DADO** que sou um usuário interno
- **QUANDO** consulto agendamentos
- **ENTÃO** devo conseguir:
  - Filtrar por data
  - Filtrar por status
  - Filtrar por paciente
  - Filtrar por tipo de exame
  - Exportar relatórios

## 📋 Regras de Negócio

### RN1 - Disponibilidade
- Exames só podem ser agendados com 24h de antecedência
- Horário de funcionamento: 7h às 17h
- Intervalo mínimo entre exames: 30 minutos
- Máximo 3 exames por paciente por semana

### RN2 - Cancelamento e Reagendamento
- Cancelamentos podem ser feitos até 2h antes do exame
- Reagendamentos podem ser feitos até 24h antes
- Cancelamentos de última hora são registrados
- Pacientes com muitos cancelamentos têm restrições

### RN3 - Priorização
- Emergências têm prioridade sobre agendamentos
- Militares em missão têm prioridade
- Exames de retorno têm prioridade sobre primeiros exames
- Sistema de fila de espera para horários ocupados

### RN4 - Validação de Documentos
- Sistema verifica documentos necessários
- Alerta sobre documentos faltantes
- Permite agendamento condicional
- Bloqueia exame sem documentos obrigatórios

## 🗄️ Modelo de Dados

### Tabela: agendamentos_exames
```sql
- id (PK)
- paciente_id (FK, obrigatório)
- tipo_exame_id (FK, obrigatório)
- profissional_id (FK)
- data_agendamento (obrigatório)
- horario_inicio (obrigatório)
- horario_fim (obrigatório)
- status (confirmado/cancelado/nao_compareceu/realizado)
- numero_protocolo (obrigatório, único)
- observacoes
- motivo_cancelamento
- documentos_entregues
- created_at
- updated_at
- created_by (FK usuarios)
- updated_by (FK usuarios)
```

### Tabela: profissionais_exames
```sql
- id (PK)
- nome_completo (obrigatório)
- especialidade
- tipo_profissional (medico/tecnico)
- registro_profissional
- horario_funcionamento
- ativo (boolean)
- created_at
- updated_at
```

### Tabela: disponibilidade_profissionais
```sql
- id (PK)
- profissional_id (FK)
- data_disponivel
- horario_inicio
- horario_fim
- disponivel (boolean)
- motivo_indisponibilidade
- created_at
```

### Tabela: agendamento_documentos
```sql
- id (PK)
- agendamento_id (FK)
- tipo_documento
- nome_arquivo
- caminho_arquivo
- entregue (boolean)
- data_entrega
- uploaded_at
```

### Tabela: agendamento_historico
```sql
- id (PK)
- agendamento_id (FK)
- status_anterior
- status_novo
- motivo_alteracao
- usuario_id (FK)
- data_alteracao
- observacoes
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de horários disponíveis
- Regras de agendamento
- Cálculo de conflitos
- Validação de documentos

### Testes de Integração
- Sistema de agendamento completo
- Notificações automáticas
- Integração com calendário
- Sistema de cancelamento

### Testes de Interface
- Interface de agendamento
- Calendário interativo
- Responsividade mobile
- Validação de formulários

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de pacientes (US #17)
- ✅ Módulo de tipos de exames (US #17)
- ✅ Sistema de notificações (já implementado)

### Dependências Externas
- ✅ Serviço de email (já integrado)
- ✅ Serviço de SMS (já integrado)
- ✅ Sistema de calendário (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Juan
- **Data de Início:** 12/10/2024
- **Data de Conclusão:** 19/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Criar modelos de dados
   - Implementar APIs de agendamento
   - Sistema de disponibilidade
   - Notificações automáticas

2. **Frontend (24h)**
   - Interface de agendamento
   - Calendário interativo
   - Formulários de agendamento
   - Dashboard de agendamentos

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Juan Garcia Soares  
**Próximo Passo:** Iniciar desenvolvimento

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Agendamento Consultas Médicas"
  - ✅ Descrição: Sistema para agendar consultas médicas
  - ✅ Objetivo: Facilitar o agendamento de consultas médicas para usuários

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
  - ✅ Wireframes de agendamento criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Seleção de Especialidade Médica
- **DADO** que sou um usuário logado
- **QUANDO** acesso o módulo de agendamento
- **ENTÃO** devo conseguir escolher entre:
  - Clínica geral
  - Cardiologia
  - Dermatologia
  - Outras especialidades disponíveis

### CA2 - Visualização de Disponibilidade
- **DADO** que selecionei o tipo de consulta
- **QUANDO** escolho a data desejada
- **ENTÃO** devo ver:
  - Horários disponíveis
  - Profissionais disponíveis
  - Duração estimada da consulta
  - Local da consulta

### CA3 - Agendamento da Consulta
- **DADO** que escolhi um horário disponível
- **QUANDO** confirmo o agendamento
- **ENTÃO** devo conseguir:
  - Preencher dados da consulta
  - Adicionar motivo/queixa
  - Anexar documentos (opcional)
  - Receber confirmação do agendamento

### CA4 - Confirmação e Notificações
- **DADO** que agendei uma consulta
- **QUANDO** o agendamento é confirmado
- **ENTÃO** devo receber:
  - Confirmação por email/SMS
  - Lembrete 24h antes
  - Instruções de preparação
  - Localização do consultório

### CA5 - Gestão de Agendamentos
- **DADO** que tenho consultas agendadas
- **QUANDO** acesso minha área pessoal
- **ENTÃO** devo conseguir:
  - Visualizar próximas consultas
  - Cancelar agendamentos (com antecedência)
  - Reagendar consultas
  - Ver histórico de consultas

## 📋 Regras de Negócio

### RN1 - Disponibilidade
- Consultas só podem ser agendadas com 24h de antecedência
- Horário de funcionamento: 7h às 17h
- Intervalo mínimo entre consultas: 30 minutos
- Máximo 2 consultas por usuário por semana

### RN2 - Cancelamento e Reagendamento
- Cancelamentos podem ser feitos até 2h antes da consulta
- Reagendamentos podem ser feitos até 24h antes
- Cancelamentos de última hora são registrados
- Usuários com muitos cancelamentos têm restrições

### RN3 - Priorização
- Emergências têm prioridade sobre agendamentos
- Militares em missão têm prioridade
- Consultas de retorno têm prioridade sobre primeiras consultas
- Sistema de fila de espera para horários ocupados

## 🗄️ Modelo de Dados

### Tabela: consultas
```sql
- id (PK)
- usuario_id (FK)
- profissional_id (FK)
- tipo_consulta (medica)
- especialidade
- data_agendamento
- horario_inicio
- horario_fim
- status (agendada/confirmada/cancelada/realizada)
- motivo_consulta
- observacoes
- created_at
- updated_at
```

### Tabela: profissionais
```sql
- id (PK)
- nome_completo
- especialidade
- tipo_profissional (medico)
- registro_profissional
- horario_funcionamento
- ativo (boolean)
- created_at
- updated_at
```

### Tabela: disponibilidade_profissionais
```sql
- id (PK)
- profissional_id (FK)
- data_disponivel
- horario_inicio
- horario_fim
- disponivel (boolean)
- motivo_indisponibilidade
- created_at
```

### Tabela: documentos_consulta
```sql
- id (PK)
- consulta_id (FK)
- nome_arquivo
- tipo_documento
- caminho_arquivo
- tamanho_arquivo
- uploaded_at
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de horários disponíveis
- Regras de agendamento
- Cálculo de conflitos
- Validação de documentos

### Testes de Integração
- Sistema de agendamento completo
- Notificações automáticas
- Integração com calendário
- Sistema de cancelamento

### Testes de Interface
- Interface de agendamento
- Calendário interativo
- Responsividade mobile
- Validação de formulários

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de usuários (já implementado)
- ✅ Sistema de notificações (já implementado)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de email (já integrado)
- ✅ Serviço de SMS (já integrado)
- ✅ Sistema de calendário (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Erika
- **Data de Início:** 07/10/2024
- **Data de Conclusão:** 18/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Criar modelos de dados
   - Implementar APIs de agendamento
   - Sistema de disponibilidade
   - Notificações automáticas

2. **Frontend (24h)**
   - Interface de agendamento
   - Calendário interativo
   - Formulários de consulta
   - Dashboard de agendamentos

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 05/10/2024  
**Responsável pela Validação:** Erika Dias Ribeiro  
**Próximo Passo:** Iniciar desenvolvimento
