# 📋 DoR - US #3: Agendamento Consultas

## 🎯 User Story
**Como usuário, desejo agendar uma consulta (médica ou odontológica) para cuidar da minha saúde.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Agendamento Consultas"
  - ✅ Descrição: Sistema para agendar consultas médicas e odontológicas
  - ✅ Objetivo: Facilitar o agendamento de consultas para usuários

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

### CA1 - Seleção de Tipo de Consulta
- **DADO** que sou um usuário logado
- **QUANDO** acesso o módulo de agendamento
- **ENTÃO** devo conseguir escolher entre:
  - Consulta médica
  - Consulta odontológica
  - Especialidade específica (quando aplicável)

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
- tipo_consulta (medica/odontologica)
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
- tipo_profissional (medico/odontologo)
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
