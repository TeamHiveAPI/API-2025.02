# 📋 DoR - US #21: Área do Paciente

## 🎯 User Story
**Como paciente, desejo acessar uma área para visualizar meus agendamentos, consultar o preparo para o exame e, se necessário, realizar o cancelamento.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Área do Paciente"
  - ✅ Descrição: Portal para pacientes visualizarem seus agendamentos
  - ✅ Objetivo: Dar autonomia aos pacientes para gerenciar seus exames

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
  - ✅ Wireframes do portal criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Acesso à Área do Paciente
- **DADO** que sou um paciente cadastrado
- **QUANDO** acesso o sistema
- **ENTÃO** devo conseguir:
  - Fazer login com CPF e senha
  - Recuperar senha caso esqueça
  - Visualizar dashboard pessoal
  - Acessar menu de funcionalidades

### CA2 - Visualização de Agendamentos
- **DADO** que tenho agendamentos realizados
- **QUANDO** acesso minha área
- **ENTÃO** devo conseguir visualizar:
  - Próximos agendamentos
  - Histórico de agendamentos
  - Status de cada agendamento
  - Detalhes do exame agendado
  - Data e horário confirmados

### CA3 - Consulta de Preparo
- **DADO** que tenho um agendamento confirmado
- **QUANDO** visualizo os detalhes do exame
- **ENTÃO** devo conseguir consultar:
  - Instruções de preparo
  - Documentos necessários
  - Duração estimada do exame
  - Local do exame
  - Contato para dúvidas

### CA4 - Cancelamento de Agendamento
- **DADO** que tenho um agendamento confirmado
- **QUANDO** desejo cancelar
- **ENTÃO** devo conseguir:
  - Cancelar até 24h antes do exame
  - Informar motivo do cancelamento
  - Receber confirmação do cancelamento
  - Ser notificado sobre reagendamento

### CA5 - Notificações e Lembretes
- **DADO** que tenho agendamentos
- **QUANDO** recebo notificações
- **ENTÃO** o sistema deve enviar:
  - Confirmação de agendamento
  - Lembrete 24h antes
  - Instruções de preparo
  - Alterações de horário
  - Resultados disponíveis

### CA6 - Histórico de Exames
- **DADO** que já realizei exames
- **QUANDO** consulto meu histórico
- **ENTÃO** devo conseguir visualizar:
  - Exames realizados
  - Resultados disponíveis
  - Data de realização
  - Status de retirada
  - Download de resultados

## 📋 Regras de Negócio

### RN1 - Acesso e Segurança
- Login obrigatório com CPF e senha
- Senha deve ter complexidade mínima
- Sessão expira após inatividade
- Logs de acesso são mantidos

### RN2 - Cancelamentos
- Cancelamento permitido até 24h antes
- Cancelamentos de última hora são registrados
- Pacientes com muitos cancelamentos têm restrições
- Sistema sugere reagendamento

### RN3 - Notificações
- Notificações por e-mail e SMS
- Lembretes automáticos
- Instruções personalizadas por exame
- Confirmação de ações importantes

### RN4 - Privacidade
- Apenas o próprio paciente acessa seus dados
- Resultados protegidos por senha
- Histórico mantido por 5 anos
- Backup seguro dos dados

## 🗄️ Modelo de Dados

### Tabela: pacientes_acesso
```sql
- id (PK)
- paciente_id (FK, obrigatório)
- cpf_login (obrigatório, único)
- senha_hash (obrigatório)
- ultimo_acesso
- tentativas_login
- bloqueado (boolean)
- created_at
- updated_at
```

### Tabela: paciente_notificacoes
```sql
- id (PK)
- paciente_id (FK)
- tipo_notificacao (agendamento/lembrete/cancelamento/resultado)
- assunto
- mensagem
- metodo_envio (email/sms)
- status_envio (pendente/enviado/falhou)
- data_envio
- lida (boolean)
```

### Tabela: paciente_acoes
```sql
- id (PK)
- paciente_id (FK)
- agendamento_id (FK)
- acao_realizada (visualizacao/cancelamento/download)
- detalhes_acao
- ip_origem
- user_agent
- data_acao
```

### Tabela: paciente_preferencias
```sql
- id (PK)
- paciente_id (FK)
- notificacao_email (boolean)
- notificacao_sms (boolean)
- horario_preferido_lembrete
- idioma_preferido
- updated_at
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de login
- Regras de cancelamento
- Cálculo de prazos
- Validação de notificações

### Testes de Integração
- Sistema completo de acesso
- Notificações automáticas
- Integração com agendamentos
- Sistema de segurança

### Testes de Interface
- Portal do paciente
- Responsividade mobile
- Acessibilidade
- Validação de formulários

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de pacientes (US #17)
- ✅ Módulo de agendamentos (US #18)
- ✅ Sistema de notificações (já implementado)

### Dependências Externas
- ✅ Serviço de email (já integrado)
- ✅ Serviço de SMS (já integrado)
- ✅ Serviço de segurança (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 5
- **Desenvolvedor Responsável:** Juan
- **Data de Início:** 20/10/2024
- **Data de Conclusão:** 24/10/2024
- **Horas Estimadas:** 40 horas

## 📋 Tarefas Técnicas

1. **Backend (20h)**
   - Criar modelos de dados
   - Implementar APIs de acesso
   - Sistema de notificações
   - Controle de segurança

2. **Frontend (16h)**
   - Portal do paciente
   - Interface de agendamentos
   - Formulários de cancelamento
   - Dashboard pessoal

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Juan Garcia Soares  
**Próximo Passo:** Iniciar desenvolvimento
