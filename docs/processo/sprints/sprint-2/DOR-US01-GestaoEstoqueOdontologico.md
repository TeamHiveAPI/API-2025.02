# 📋 DoR - US #1: Gestão Estoque Odontológico

## 🎯 User Story
**Como tenente odontológico, desejo gerenciar o estoque de insumos odontológicos, controlando lote e data de vencimento para garantir a segurança dos procedimentos.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Gestão Estoque Odontológico"
  - ✅ Descrição: Controle de insumos odontológicos com foco em lote e validade
  - ✅ Objetivo: Garantir segurança dos procedimentos odontológicos

- [x] **Critérios de aceitação escritos**
  - ✅ Ver seção "Critérios de Aceitação" abaixo

- [x] **Regras de negócio claras**
  - ✅ Ver seção "Regras de Negócio" abaixo

- [x] **Foi estimada pela equipe**
  - ✅ Estimativa: 3 Story Points
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
  - ✅ Wireframes de navegação criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Cadastro de Insumos
- **DADO** que sou um tenente odontológico
- **QUANDO** acesso o módulo de estoque odontológico
- **ENTÃO** devo conseguir cadastrar novos insumos com:
  - Nome do insumo
  - Código de identificação
  - Quantidade inicial
  - Lote
  - Data de vencimento
  - Fornecedor
  - Preço unitário

### CA2 - Controle de Lote
- **DADO** que tenho insumos cadastrados
- **QUANDO** visualizo o estoque
- **ENTÃO** devo ver agrupados por lote com:
  - Quantidade disponível por lote
  - Data de vencimento de cada lote
  - Status de validade (Válido/Próximo ao vencimento/Vencido)

### CA3 - Alertas de Vencimento
- **DADO** que há insumos próximos ao vencimento
- **QUANDO** acesso o sistema
- **ENTÃO** devo receber alertas visuais para:
  - Itens que vencem em 30 dias
  - Itens que vencem em 15 dias
  - Itens já vencidos

### CA4 - Movimentação de Estoque
- **DADO** que sou um tenente odontológico
- **QUANDO** realizo procedimentos
- **ENTÃO** devo conseguir:
  - Registrar saída de insumos
  - Informar quantidade utilizada
  - Associar ao procedimento realizado
  - Atualizar estoque automaticamente

## 📋 Regras de Negócio

### RN1 - Controle de Validade
- Insumos vencidos não podem ser utilizados em procedimentos
- Sistema deve bloquear automaticamente uso de itens vencidos
- Alertas devem ser enviados 30 e 15 dias antes do vencimento

### RN2 - Gestão de Lotes
- Cada lote deve ter identificação única
- Controle FIFO (First In, First Out) deve ser aplicado
- Histórico de movimentação por lote deve ser mantido

### RN3 - Níveis de Estoque
- Estoque mínimo deve ser configurável por insumo
- Alertas de reposição quando estoque atinge nível mínimo
- Relatório de consumo mensal deve ser gerado

## 🗄️ Modelo de Dados

### Tabela: insumos_odontologicos
```sql
- id (PK)
- nome_insumo
- codigo_identificacao
- descricao
- categoria
- unidade_medida
- preco_unitario
- fornecedor_id (FK)
- ativo (boolean)
- created_at
- updated_at
```

### Tabela: lotes_insumos
```sql
- id (PK)
- insumo_id (FK)
- numero_lote
- quantidade_inicial
- quantidade_atual
- data_vencimento
- data_fabricacao
- fornecedor_id (FK)
- preco_custo
- created_at
- updated_at
```

### Tabela: movimentacoes_estoque
```sql
- id (PK)
- lote_id (FK)
- tipo_movimentacao (entrada/saida)
- quantidade
- motivo
- procedimento_id (FK) - opcional
- usuario_id (FK)
- data_movimentacao
- created_at
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de campos obrigatórios
- Cálculo de estoque atual
- Validação de datas de vencimento
- Regras de negócio de movimentação

### Testes de Integração
- CRUD completo de insumos
- CRUD completo de lotes
- Movimentação de estoque
- Geração de alertas

### Testes de Interface
- Navegação entre telas
- Responsividade mobile/tablet
- Validação de formulários
- Feedback visual de ações

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de usuários (já implementado)
- ✅ Sistema de notificações (já implementado)

### Dependências Externas
- ✅ API de fornecedores (já integrada)
- ✅ Sistema de relatórios (já implementado)

## 📊 Estimativa e Planejamento

- **Story Points:** 3
- **Desenvolvedor Responsável:** Eber
- **Data de Início:** 07/10/2024
- **Data de Conclusão:** 11/10/2024
- **Horas Estimadas:** 24 horas

## 📋 Tarefas Técnicas

1. **Backend (12h)**
   - Criar modelos de dados
   - Implementar APIs CRUD
   - Implementar regras de negócio
   - Criar sistema de alertas

2. **Frontend (8h)**
   - Criar telas de cadastro
   - Implementar listagem de estoque
   - Criar formulários de movimentação
   - Implementar alertas visuais

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 05/10/2024  
**Responsável pela Validação:** Eber de Souza Junior  
**Próximo Passo:** Iniciar desenvolvimento
