# 📋 DoR - US #24: Histórico de Medicamentos

## 🎯 User Story
**Como usuário, desejo consultar meu histórico de medicamentos recebidos para referência.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Histórico de Medicamentos"
  - ✅ Descrição: Sistema para consultar histórico de medicamentos
  - ✅ Objetivo: Permitir consulta de medicamentos recebidos pelo usuário

- [x] **Critérios de aceitação escritos**
  - ✅ Ver seção "Critérios de Aceitação" abaixo

- [x] **Regras de negócio claras**
  - ✅ Ver seção "Regras de Negócio" abaixo

- [x] **Foi estimada pela equipe**
  - ✅ Estimativa: 3 Story Points
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
  - ✅ Wireframes de histórico criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Visualização do Histórico
- **DADO** que sou um usuário logado
- **QUANDO** acesso meu histórico de medicamentos
- **ENTÃO** devo conseguir visualizar:
  - Lista cronológica de medicamentos recebidos
  - Data de dispensação
  - Quantidade dispensada
  - Dosagem prescrita
  - Profissional responsável

### CA2 - Detalhes dos Medicamentos
- **DADO** que visualizo meu histórico
- **QUANDO** clico em um medicamento
- **ENTÃO** devo conseguir ver:
  - Nome completo do medicamento
  - Princípio ativo
  - Concentração
  - Forma farmacêutica
  - Lote e validade
  - Instruções de uso

### CA3 - Filtros e Busca
- **DADO** que tenho histórico de medicamentos
- **QUANDO** preciso encontrar informações específicas
- **ENTÃO** devo conseguir:
  - Filtrar por período
  - Buscar por nome do medicamento
  - Filtrar por tipo de medicamento
  - Ordenar por data
  - Exportar relatório

### CA4 - Informações de Prescrição
- **DADO** que visualizo um medicamento no histórico
- **QUANDO** consulto os detalhes
- **ENTÃO** devo conseguir ver:
  - Receita médica anexa
  - Médico prescritor
  - Motivo da prescrição
  - Duração do tratamento
  - Observações médicas

### CA5 - Alertas e Lembretes
- **DADO** que tenho medicamentos em uso
- **QUANDO** consulto meu histórico
- **ENTÃO** o sistema deve:
  - Alertar sobre medicamentos vencidos
  - Lembrar sobre horários de uso
  - Avisar sobre interações medicamentosas
  - Sugerir consultas médicas

### CA6 - Compartilhamento de Informações
- **DADO** que preciso compartilhar meu histórico
- **QUANDO** acesso as opções de compartilhamento
- **ENTÃO** devo conseguir:
  - Gerar relatório em PDF
  - Compartilhar com médico
  - Enviar por e-mail
  - Imprimir histórico

## 📋 Regras de Negócio

### RN1 - Privacidade e Segurança
- Apenas o próprio usuário acessa seu histórico
- Dados criptografados em trânsito e repouso
- Logs de acesso são mantidos
- Cumprimento da LGPD

### RN2 - Retenção de Dados
- Histórico mantido por 5 anos
- Arquivamento automático após prazo
- Possibilidade de exclusão manual
- Backup seguro dos dados

### RN3 - Validação de Informações
- Dados sincronizados com dispensação
- Verificação de integridade
- Controle de versões
- Auditoria de alterações

### RN4 - Acessibilidade
- Interface responsiva
- Suporte a leitores de tela
- Contraste adequado
- Navegação por teclado

## 🗄️ Modelo de Dados

### Tabela: historico_medicamentos
```sql
- id (PK)
- usuario_id (FK, obrigatório)
- dispensacao_id (FK, obrigatório)
- medicamento_id (FK, obrigatório)
- data_dispensacao (obrigatório)
- quantidade_dispensada (obrigatório)
- dosagem_prescrita
- medico_prescritor
- motivo_prescricao
- duracao_tratamento
- observacoes_medicas
- receita_anexa
- created_at
```

### Tabela: medicamentos_usuario
```sql
- id (PK)
- usuario_id (FK)
- medicamento_id (FK)
- data_inicio_uso
- data_fim_uso
- status_uso (ativo/suspenso/finalizado)
- horarios_uso
- efeitos_colaterais
- observacoes_usuario
- created_at
- updated_at
```

### Tabela: alertas_medicamentos
```sql
- id (PK)
- usuario_id (FK)
- medicamento_id (FK)
- tipo_alerta (vencimento/interacao/lembrete)
- mensagem_alerta
- data_alerta
- visualizado (boolean)
- acao_tomada
- created_at
```

### Tabela: compartilhamentos_historico
```sql
- id (PK)
- usuario_id (FK)
- destinatario_email
- destinatario_nome
- tipo_compartilhamento (pdf/email/impressao)
- dados_compartilhados
- data_compartilhamento
- autorizado_por (FK usuarios)
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de dados
- Cálculo de períodos
- Geração de relatórios
- Criptografia de dados

### Testes de Integração
- Sistema completo de histórico
- Integração com dispensação
- Sistema de alertas
- Compartilhamento de dados

### Testes de Interface
- Interface de histórico
- Filtros e busca
- Responsividade
- Acessibilidade

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de dispensação (US #22)
- ✅ Sistema de logs (já implementado)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de PDF (já integrado)
- ✅ Serviço de e-mail (já integrado)
- ✅ Serviço de criptografia (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 3
- **Desenvolvedor Responsável:** Marco
- **Data de Início:** 25/10/2024
- **Data de Conclusão:** 26/10/2024
- **Horas Estimadas:** 24 horas

## 📋 Tarefas Técnicas

1. **Backend (12h)**
   - Criar modelos de dados
   - Implementar APIs de histórico
   - Sistema de alertas
   - Geração de relatórios

2. **Frontend (8h)**
   - Interface de histórico
   - Filtros e busca
   - Compartilhamento
   - Responsividade

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Marco Antonio Arantes  
**Próximo Passo:** Iniciar desenvolvimento
