# 📋 DoR - US #15: Nota de Empenho

## 🎯 User Story
**Como tenente de almoxarifado, desejo cadastrar uma Nota de Empenho vinculada a um fornecedor, definindo data de entrega, frequência de cobrança e urgência, para digitalizar o controle.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Nota de Empenho"
  - ✅ Descrição: Sistema para cadastrar e gerenciar Notas de Empenho
  - ✅ Objetivo: Digitalizar controle de empenhos e vincular a fornecedores

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
  - ✅ Wireframes de cadastro criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Cadastro de Nota de Empenho
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** acesso o módulo de Notas de Empenho
- **ENTÃO** devo conseguir cadastrar:
  - Número da Nota de Empenho (obrigatório, único)
  - Fornecedor vinculado (obrigatório)
  - Data de entrega (obrigatório)
  - Frequência de cobrança (obrigatório)
  - Nível de urgência (obrigatório)
  - Valor estimado (opcional)
  - Descrição dos itens (obrigatório)
  - Observações (opcional)

### CA2 - Definição de Frequência de Cobrança
- **DADO** que estou cadastrando uma Nota de Empenho
- **QUANDO** defino a frequência de cobrança
- **ENTÃO** devo conseguir escolher entre:
  - Diária
  - Semanal
  - Quinzenal
  - Mensal
  - Personalizada (definir intervalo)

### CA3 - Definição de Urgência
- **DADO** que estou cadastrando uma Nota de Empenho
- **QUANDO** defino o nível de urgência
- **ENTÃO** devo conseguir escolher entre:
  - Baixa (verde)
  - Média (amarelo)
  - Alta (laranja)
  - Crítica (vermelho)

### CA4 - Vinculação com Fornecedor
- **DADO** que tenho fornecedores cadastrados
- **QUANDO** vinculo uma Nota de Empenho a um fornecedor
- **ENTÃO** o sistema deve:
  - Mostrar apenas fornecedores ativos
  - Permitir busca por razão social
  - Exibir dados do fornecedor selecionado
  - Validar se fornecedor está ativo

### CA5 - Gestão de Status
- **DADO** que tenho Notas de Empenho cadastradas
- **QUANDO** gerencio o status das Notas
- **ENTÃO** devo conseguir:
  - Visualizar status atual
  - Alterar status (Pendente/Em Andamento/Concluída/Cancelada)
  - Adicionar comentários de status
  - Visualizar histórico de alterações

### CA6 - Consulta e Relatórios
- **DADO** que sou um tenente de almoxarifado
- **QUANDO** consulto Notas de Empenho
- **ENTÃO** devo conseguir:
  - Filtrar por fornecedor
  - Filtrar por status
  - Filtrar por urgência
  - Filtrar por data de entrega
  - Exportar relatórios em PDF/Excel

## 📋 Regras de Negócio

### RN1 - Numeração de Notas de Empenho
- Número deve ser único no sistema
- Formato: NE-YYYY-NNNNNN (ano + sequencial)
- Sistema gera numeração automática
- Não permite duplicação

### RN2 - Validação de Datas
- Data de entrega não pode ser anterior à data atual
- Sistema alerta sobre datas próximas
- Notas vencidas são destacadas
- Permite reagendamento de entregas

### RN3 - Controle de Urgência
- Notas críticas têm prioridade máxima
- Sistema envia alertas automáticos
- Dashboard mostra indicadores de urgência
- Relatórios destacam itens críticos

### RN4 - Frequência de Cobrança
- Sistema calcula próximas cobranças automaticamente
- Envia lembretes conforme frequência
- Permite alterar frequência durante execução
- Histórico de cobranças é mantido

## 🗄️ Modelo de Dados

### Tabela: notas_empenho
```sql
- id (PK)
- numero_ne (obrigatório, único)
- fornecedor_id (FK, obrigatório)
- data_entrega (obrigatório)
- frequencia_cobranca (obrigatório)
- nivel_urgencia (obrigatório)
- valor_estimado
- descricao_itens (obrigatório)
- observacoes
- status (pendente/em_andamento/concluida/cancelada)
- data_criacao
- data_atualizacao
- criado_por (FK usuarios)
- atualizado_por (FK usuarios)
```

### Tabela: ne_cobrancas
```sql
- id (PK)
- nota_empenho_id (FK)
- data_cobranca
- status_cobranca (pendente/enviada/respondida)
- metodo_cobranca (email/telefone/presencial)
- resposta_fornecedor
- proxima_cobranca
- created_at
```

### Tabela: ne_historico
```sql
- id (PK)
- nota_empenho_id (FK)
- campo_alterado
- valor_anterior
- valor_novo
- usuario_id (FK)
- data_alteracao
- motivo_alteracao
```

### Tabela: ne_anexos
```sql
- id (PK)
- nota_empenho_id (FK)
- nome_arquivo
- tipo_arquivo
- caminho_arquivo
- tamanho_arquivo
- uploaded_at
- uploaded_by (FK usuarios)
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de numeração
- Cálculo de frequência
- Regras de urgência
- Validação de datas

### Testes de Integração
- CRUD completo de Notas de Empenho
- Sistema de cobrança
- Integração com fornecedores
- Relatórios e exportação

### Testes de Interface
- Formulários de cadastro
- Listagem e filtros
- Dashboard de urgência
- Responsividade

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de fornecedores (US #14)
- ✅ Sistema de notificações (já implementado)
- ✅ Upload de arquivos (já implementado)

### Dependências Externas
- ✅ Serviço de e-mail (já integrado)
- ✅ Serviço de relatórios (já integrado)

## 📊 Estimativa e Planejamento

- **Story Points:** 8
- **Desenvolvedor Responsável:** Eber
- **Data de Início:** 12/10/2024
- **Data de Conclusão:** 19/10/2024
- **Horas Estimadas:** 64 horas

## 📋 Tarefas Técnicas

1. **Backend (32h)**
   - Criar modelos de dados
   - Implementar APIs de Notas de Empenho
   - Sistema de cobrança automática
   - Geração de relatórios

2. **Frontend (24h)**
   - Interface de cadastro
   - Dashboard de urgência
   - Listagem e filtros
   - Formulários de edição

3. **Testes (8h)**
   - Testes unitários
   - Testes de integração
   - Validação de interface

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Eber de Souza Junior  
**Próximo Passo:** Iniciar desenvolvimento
