# 📋 DoR - US #19: Status de Exames

## 🎯 User Story
**Como usuário interno, desejo atualizar o status do exame (realizado, disponível, retirado) para notificar o paciente sobre a disponibilidade do resultado.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Status de Exames"
  - ✅ Descrição: Sistema para atualizar status de exames realizados
  - ✅ Objetivo: Controlar fluxo de exames e notificar pacientes

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
  - ✅ Wireframes de controle criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Atualização para "Realizado"
- **DADO** que sou um usuário interno
- **QUANDO** um exame é realizado
- **ENTÃO** devo conseguir:
  - Alterar status de "Confirmado" para "Realizado"
  - Registrar data e hora da realização
  - Adicionar observações do exame
  - Registrar profissional responsável
  - Iniciar processo de análise

### CA2 - Atualização para "Disponível"
- **DADO** que o exame foi analisado
- **QUANDO** o resultado está pronto
- **ENTÃO** devo conseguir:
  - Alterar status de "Realizado" para "Disponível"
  - Anexar resultado do exame
  - Registrar data de disponibilização
  - Enviar notificação automática ao paciente
  - Definir prazo para retirada

### CA3 - Atualização para "Retirado"
- **DADO** que o paciente retira o resultado
- **QUANDO** o resultado é entregue
- **ENTÃO** devo conseguir:
  - Alterar status de "Disponível" para "Retirado"
  - Registrar data e hora da retirada
  - Registrar quem retirou (paciente ou responsável)
  - Confirmar entrega de documentos
  - Finalizar processo do exame

### CA4 - Notificações Automáticas
- **DADO** que o status é alterado
- **QUANDO** o exame fica disponível
- **ENTÃO** o sistema deve:
  - Enviar e-mail/SMS para o paciente
  - Incluir instruções de retirada
  - Informar prazo para retirada
  - Enviar lembrete se não retirado em 7 dias

### CA5 - Controle de Prazos
- **DADO** que um exame está disponível
- **QUANDO** passa do prazo de retirada
- **ENTÃO** o sistema deve:
  - Alertar sobre exame não retirado
  - Enviar lembretes automáticos
  - Escalar para supervisor após 15 dias
  - Sugerir contato direto com paciente

### CA6 - Relatórios e Consultas
- **DADO** que sou um usuário interno
- **QUANDO** consulto exames por status
- **ENTÃO** devo conseguir:
  - Filtrar por status atual
  - Filtrar por período
  - Filtrar por paciente
  - Filtrar por tipo de exame
  - Exportar relatórios de status

## 📋 Regras de Negócio

### RN1 - Fluxo de Status
- Status só pode avançar sequencialmente
- Não é possível retroceder status
- Cada mudança deve ser justificada
- Histórico de alterações é mantido

### RN2 - Prazos de Retirada
- Resultados devem ser retirados em até 30 dias
- Lembrete enviado após 7 dias
- Escalação após 15 dias
- Arquivamento após 60 dias

### RN3 - Notificações
- Notificação imediata quando disponível
- Lembrete semanal se não retirado
- Notificação de escalação
- Confirmação de retirada

### RN4 - Controle de Acesso
- Apenas usuários autorizados podem alterar status
- Alterações são registradas com usuário responsável
- Sistema mantém logs de auditoria
- Backup automático dos dados

## 🗄️ Modelo de Dados

### Tabela: exames_status
```sql
- id (PK)
- agendamento_id (FK, obrigatório)
- status_atual (realizado/disponivel/retirado)
- data_realizacao
- data_disponibilizacao
- data_retirada
- profissional_realizacao (FK usuarios)
- resultado_anexo
- observacoes_realizacao
- observacoes_retirada
- quem_retirou
- prazo_retirada
- created_at
- updated_at
- updated_by (FK usuarios)
```

### Tabela: exames_notificacoes
```sql
- id (PK)
- exame_status_id (FK)
- tipo_notificacao (disponivel/lembrete/escalacao)
- destinatario_email
- destinatario_telefone
- assunto
- corpo_mensagem
- status_envio (pendente/enviado/falhou)
- data_envio
- tentativas_envio
- erro_envio
```

### Tabela: exames_historico_status
```sql
- id (PK)
- exame_status_id (FK)
- status_anterior
- status_novo
- motivo_alteracao
- usuario_id (FK)
- data_alteracao
- observacoes
- ip_origem
```

### Tabela: exames_anexos
```sql
- id (PK)
- exame_status_id (FK)
- tipo_anexo (resultado/laudo/imagem)
- nome_arquivo
- caminho_arquivo
- tamanho_arquivo
- uploaded_at
- uploaded_by (FK usuarios)
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de fluxo de status
- Cálculo de prazos
- Regras de notificação
- Validação de anexos

### Testes de Integração
- Sistema completo de status
- Notificações automáticas
- Integração com agendamentos
- Sistema de relatórios

### Testes de Interface
- Interface de controle de status
- Dashboard de exames
- Responsividade
- Validação de formulários

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de agendamentos (US #18)
- ✅ Sistema de notificações (já implementado)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de email (já integrado)
- ✅ Serviço de SMS (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 5
- **Desenvolvedor Responsável:** Erika
- **Data de Início:** 20/10/2024
- **Data de Conclusão:** 24/10/2024
- **Horas Estimadas:** 40 horas

## 📋 Tarefas Técnicas

1. **Backend (20h)**
   - Criar modelos de dados
   - Implementar APIs de status
   - Sistema de notificações
   - Controle de prazos

2. **Frontend (16h)**
   - Interface de controle de status
   - Dashboard de exames
   - Formulários de atualização
   - Relatórios de status

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Erika Dias Ribeiro  
**Próximo Passo:** Iniciar desenvolvimento
