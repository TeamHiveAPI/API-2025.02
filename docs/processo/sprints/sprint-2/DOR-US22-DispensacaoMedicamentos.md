# 📋 DoR - US #22: Dispensação de Medicamentos

## 🎯 User Story
**Como tenente de farmácia, desejo registrar a entrega (dispensação) de medicamentos a um paciente para controle.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Dispensação de Medicamentos"
  - ✅ Descrição: Sistema para registrar entrega de medicamentos
  - ✅ Objetivo: Controlar dispensação de medicamentos para pacientes

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
  - ✅ Wireframes de dispensação criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Seleção de Paciente
- **DADO** que sou um tenente de farmácia
- **QUANDO** acesso o módulo de dispensação
- **ENTÃO** devo conseguir:
  - Buscar paciente por nome ou CPF
  - Visualizar dados do paciente
  - Verificar se paciente está ativo
  - Acessar histórico de dispensações

### CA2 - Seleção de Medicamentos
- **DADO** que selecionei um paciente
- **QUANDO** vou dispensar medicamentos
- **ENTÃO** devo conseguir:
  - Buscar medicamentos por nome ou código
  - Verificar disponibilidade no estoque
  - Visualizar lote e validade
  - Selecionar quantidade a dispensar

### CA3 - Validação de Receita
- **DADO** que vou dispensar medicamentos
- **QUANDO** processo a dispensação
- **ENTÃO** devo conseguir:
  - Anexar receita médica
  - Validar prescrição médica
  - Verificar compatibilidade de medicamentos
  - Confirmar dosagem prescrita

### CA4 - Registro da Dispensação
- **DADO** que validei todos os dados
- **QUANDO** confirmo a dispensação
- **ENTÃO** devo conseguir:
  - Registrar data e hora da dispensação
  - Registrar profissional responsável
  - Gerar número de protocolo
  - Atualizar estoque automaticamente
  - Emitir comprovante de dispensação

### CA5 - Controle de Estoque
- **DADO** que uma dispensação é realizada
- **QUANDO** o medicamento é entregue
- **ENTÃO** o sistema deve:
  - Reduzir quantidade em estoque
  - Registrar saída do medicamento
  - Alertar sobre estoque baixo
  - Manter histórico de movimentação

### CA6 - Relatórios e Consultas
- **DADO** que sou um tenente de farmácia
- **QUANDO** consulto dispensações
- **ENTÃO** devo conseguir:
  - Filtrar por período
  - Filtrar por paciente
  - Filtrar por medicamento
  - Filtrar por profissional
  - Exportar relatórios

## 📋 Regras de Negócio

### RN1 - Validação de Receita
- Receita médica obrigatória para medicamentos controlados
- Validação de assinatura do médico
- Verificação de validade da receita
- Controle de medicamentos de uso restrito

### RN2 - Controle de Estoque
- Verificação de disponibilidade antes da dispensação
- Prioridade por lote mais próximo do vencimento
- Bloqueio de dispensação se estoque insuficiente
- Alertas automáticos de reposição

### RN3 - Rastreabilidade
- Cada dispensação deve ser rastreável
- Histórico completo de movimentações
- Controle de lotes e validades
- Auditoria de todas as operações

### RN4 - Segurança
- Apenas profissionais autorizados podem dispensar
- Controle de acesso por nível hierárquico
- Logs de todas as operações
- Backup automático dos dados

## 🗄️ Modelo de Dados

### Tabela: dispensacoes
```sql
- id (PK)
- paciente_id (FK, obrigatório)
- profissional_id (FK, obrigatório)
- data_dispensacao (obrigatório)
- numero_protocolo (obrigatório, único)
- receita_anexa
- observacoes
- status (pendente/confirmada/cancelada)
- created_at
- updated_at
- created_by (FK usuarios)
```

### Tabela: dispensacao_itens
```sql
- id (PK)
- dispensacao_id (FK, obrigatório)
- medicamento_id (FK, obrigatório)
- lote_id (FK, obrigatório)
- quantidade_dispensada (obrigatório)
- dosagem_prescrita
- observacoes_item
- created_at
```

### Tabela: medicamentos
```sql
- id (PK)
- nome_medicamento (obrigatório)
- codigo_medicamento (obrigatório, único)
- principio_ativo
- concentracao
- forma_farmaceutica
- unidade_medida
- controlado (boolean)
- ativo (boolean)
- created_at
- updated_at
```

### Tabela: estoque_medicamentos
```sql
- id (PK)
- medicamento_id (FK)
- lote (obrigatório)
- data_validade (obrigatório)
- quantidade_atual (obrigatório)
- quantidade_minima
- quantidade_maxima
- localizacao_estoque
- ativo (boolean)
- created_at
- updated_at
```

### Tabela: movimentacao_estoque
```sql
- id (PK)
- medicamento_id (FK)
- lote_id (FK)
- tipo_movimentacao (entrada/saida/ajuste)
- quantidade_movimentada
- motivo_movimentacao
- referencia_id (FK)
- usuario_id (FK)
- data_movimentacao
- observacoes
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de receitas
- Cálculo de estoque
- Regras de dispensação
- Validação de medicamentos

### Testes de Integração
- Sistema completo de dispensação
- Integração com estoque
- Sistema de relatórios
- Controle de lotes

### Testes de Interface
- Interface de dispensação
- Busca de medicamentos
- Formulários de registro
- Responsividade

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de pacientes (US #17)
- ✅ Sistema de estoque (Sprint 1)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de PDF (já integrado)
- ✅ Serviço de impressão (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Erika
- **Data de Início:** 25/10/2024
- **Data de Conclusão:** 26/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Criar modelos de dados
   - Implementar APIs de dispensação
   - Sistema de controle de estoque
   - Validação de receitas

2. **Frontend (24h)**
   - Interface de dispensação
   - Busca de medicamentos
   - Formulários de registro
   - Relatórios de dispensação

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Erika Dias Ribeiro  
**Próximo Passo:** Iniciar desenvolvimento
