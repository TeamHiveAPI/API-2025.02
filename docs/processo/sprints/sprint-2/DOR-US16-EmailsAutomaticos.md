# 📋 DoR - US #16: E-mails Automáticos

## 🎯 User Story
**Como tenente de almoxarifado, desejo que o sistema envie e-mails automáticos para fornecedores na entrada de um pedido (com a NE anexa), em cobranças de atraso e na finalização do pedido.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "E-mails Automáticos"
  - ✅ Descrição: Sistema de envio automático de e-mails para fornecedores
  - ✅ Objetivo: Automatizar comunicação com fornecedores em diferentes etapas

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
  - ✅ Templates de e-mail criados
  - ✅ Fluxo de comunicação definido

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - E-mail de Entrada de Pedido
- **DADO** que um pedido é criado com Nota de Empenho
- **QUANDO** o pedido é registrado no sistema
- **ENTÃO** o sistema deve enviar automaticamente:
  - E-mail para o fornecedor responsável
  - Nota de Empenho anexada em PDF
  - Detalhes do pedido (itens, quantidades, prazos)
  - Instruções de entrega
  - Contato para dúvidas

### CA2 - E-mail de Cobrança de Atraso
- **DADO** que uma Nota de Empenho está atrasada
- **QUANDO** o sistema detecta atraso conforme frequência definida
- **ENTÃO** o sistema deve enviar:
  - E-mail de cobrança automático
  - Detalhes do atraso
  - Nova data limite sugerida
  - Consequências do atraso
  - Escalação para supervisor se necessário

### CA3 - E-mail de Finalização de Pedido
- **DADO** que um pedido é finalizado/concluído
- **QUANDO** o status é alterado para "Concluído"
- **ENTÃO** o sistema deve enviar:
  - E-mail de confirmação de entrega
  - Resumo dos itens entregues
  - Comprovante de recebimento
  - Agradecimento pela parceria
  - Avaliação de satisfação (opcional)

### CA4 - Templates de E-mail Personalizáveis
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** configuro os templates de e-mail
- **ENTÃO** devo conseguir:
  - Personalizar conteúdo dos e-mails
  - Adicionar logo da instituição
  - Definir assinatura padrão
  - Configurar remetente
  - Testar envio de e-mails

### CA5 - Controle de Envios
- **DADO** que o sistema envia e-mails automáticos
- **QUANDO** ocorrem envios
- **ENTÃO** o sistema deve:
  - Registrar todos os envios
  - Controlar tentativas de envio
  - Tratar falhas de entrega
  - Permitir reenvio manual
  - Mostrar status de entrega

### CA6 - Configuração de Frequência
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** configuro cobranças automáticas
- **ENTÃO** devo conseguir:
  - Definir intervalo entre cobranças
  - Configurar horários de envio
  - Definir número máximo de cobranças
  - Escalar para supervisor após X tentativas
  - Pausar/envios em feriados

## 📋 Regras de Negócio

### RN1 - Validação de E-mails
- E-mail do fornecedor deve ser válido
- Sistema valida formato antes do envio
- E-mails inválidos são reportados
- Permite atualização de e-mail

### RN2 - Controle de Spam
- Máximo 3 e-mails por dia por fornecedor
- Intervalo mínimo de 2 horas entre envios
- Sistema detecta e-mails não lidos
- Pausa envios em caso de reclamação

### RN3 - Anexos e Documentos
- Nota de Empenho sempre anexada em PDF
- Tamanho máximo de anexo: 10MB
- Formato padrão: PDF
- Backup de documentos enviados

### RN4 - Escalação de Problemas
- Após 3 cobranças sem resposta, escala para supervisor
- Supervisor recebe relatório de situação
- Sistema sugere ações corretivas
- Histórico completo de comunicações

## 🗄️ Modelo de Dados

### Tabela: email_templates
```sql
- id (PK)
- tipo_email (entrada_pedido/cobranca_atraso/finalizacao)
- assunto (obrigatório)
- corpo_email (obrigatório)
- anexos_padrao
- ativo (boolean)
- created_at
- updated_at
- created_by (FK usuarios)
```

### Tabela: email_envios
```sql
- id (PK)
- fornecedor_id (FK)
- pedido_id (FK)
- tipo_email (FK)
- assunto
- corpo_email
- destinatario_email
- status_envio (pendente/enviado/falhou)
- data_envio
- tentativas_envio
- erro_envio
- anexos_enviados
- created_at
```

### Tabela: email_configuracoes
```sql
- id (PK)
- tipo_configuracao
- valor_configuracao
- descricao
- ativo (boolean)
- updated_at
- updated_by (FK usuarios)
```

### Tabela: email_logs
```sql
- id (PK)
- email_envio_id (FK)
- acao_realizada
- detalhes_acao
- usuario_responsavel (FK usuarios)
- data_acao
- ip_origem
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de templates
- Formatação de e-mails
- Validação de anexos
- Cálculo de frequência

### Testes de Integração
- Envio de e-mails completo
- Sistema de cobrança
- Integração com fornecedores
- Tratamento de falhas

### Testes de Interface
- Configuração de templates
- Dashboard de envios
- Relatórios de comunicação
- Responsividade

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de fornecedores (US #14)
- ✅ Módulo de Notas de Empenho (US #15)
- ✅ Sistema de pedidos (Sprint 1)

### Dependências Externas
- ✅ Serviço de e-mail (SMTP configurado)
- ✅ Serviço de PDF (já integrado)
- ✅ Serviço de templates (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Diogo
- **Data de Início:** 20/10/2024
- **Data de Conclusão:** 26/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Sistema de envio de e-mails
   - Templates personalizáveis
   - Controle de frequência
   - Sistema de logs

2. **Frontend (24h)**
   - Configuração de templates
   - Dashboard de envios
   - Relatórios de comunicação
   - Interface de configuração

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de envios

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Diogo Palharini  
**Próximo Passo:** Iniciar desenvolvimento
