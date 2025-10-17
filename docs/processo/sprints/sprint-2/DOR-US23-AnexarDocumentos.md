# 📋 DoR - US #23: Anexar Documentos

## 🎯 User Story
**Como usuário, desejo anexar documentos (receitas, atestados) aos meus agendamentos para facilitar o processo.**

## ✅ Checklist DoR - Validação Completa

### 📝 Sobre User Stories:
- [x] **Título claro, descrição bem definida e objetivo compreendido**
  - ✅ Título: "Anexar Documentos"
  - ✅ Descrição: Sistema para anexar documentos aos agendamentos
  - ✅ Objetivo: Facilitar processo de agendamento com documentos necessários

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
  - ✅ Wireframes de upload criados

- [x] **Regras de negócio detalhadas**
  - ✅ Ver seção "Regras de Negócio Detalhadas" abaixo

- [x] **Modelo de dados disponível**
  - ✅ Ver seção "Modelo de Dados" abaixo

- [x] **Estratégia de testes definida**
  - ✅ Ver seção "Estratégia de Testes" abaixo

## 🎯 Critérios de Aceitação

### CA1 - Upload de Documentos
- **DADO** que sou um usuário logado
- **QUANDO** acesso meus agendamentos
- **ENTÃO** devo conseguir:
  - Anexar documentos aos agendamentos
  - Selecionar tipo de documento
  - Fazer upload de arquivos
  - Visualizar documentos anexados

### CA2 - Tipos de Documentos Suportados
- **DADO** que vou anexar um documento
- **QUANDO** seleciono o tipo
- **ENTÃO** devo conseguir anexar:
  - Receitas médicas
  - Atestados médicos
  - Exames anteriores
  - Documentos de identidade
  - Outros documentos relevantes

### CA3 - Validação de Arquivos
- **DADO** que vou fazer upload de um arquivo
- **QUANDO** seleciono o arquivo
- **ENTÃO** o sistema deve:
  - Validar formato do arquivo
  - Verificar tamanho máximo
  - Escanear por vírus
  - Gerar preview do documento

### CA4 - Gerenciamento de Documentos
- **DADO** que tenho documentos anexados
- **QUANDO** gerencio meus anexos
- **ENTÃO** devo conseguir:
  - Visualizar lista de documentos
  - Baixar documentos anexados
  - Remover documentos desnecessários
  - Renomear documentos

### CA5 - Integração com Agendamentos
- **DADO** que anexei documentos
- **QUANDO** processo meu agendamento
- **ENTÃO** o sistema deve:
  - Associar documentos ao agendamento
  - Validar documentos necessários
  - Notificar sobre documentos faltantes
  - Facilitar processo de aprovação

### CA6 - Segurança e Privacidade
- **DADO** que anexei documentos pessoais
- **QUANDO** documentos são armazenados
- **ENTÃO** o sistema deve:
  - Criptografar documentos sensíveis
  - Controlar acesso aos documentos
  - Manter logs de acesso
  - Cumprir LGPD

## 📋 Regras de Negócio

### RN1 - Formatos Aceitos
- Formatos permitidos: PDF, JPG, PNG, DOC, DOCX
- Tamanho máximo: 10MB por arquivo
- Máximo 5 documentos por agendamento
- Validação de integridade do arquivo

### RN2 - Segurança
- Criptografia de documentos sensíveis
- Controle de acesso por usuário
- Logs de auditoria
- Backup automático

### RN3 - Retenção
- Documentos mantidos por 5 anos
- Arquivamento automático após prazo
- Possibilidade de exclusão manual
- Notificação antes da exclusão

### RN4 - Validação
- Verificação de documentos obrigatórios
- Alerta sobre documentos faltantes
- Validação de autenticidade
- Controle de versões

## 🗄️ Modelo de Dados

### Tabela: documentos_anexos
```sql
- id (PK)
- agendamento_id (FK, obrigatório)
- usuario_id (FK, obrigatório)
- tipo_documento (obrigatório)
- nome_arquivo (obrigatório)
- nome_original (obrigatório)
- caminho_arquivo (obrigatório)
- tamanho_arquivo (obrigatório)
- tipo_mime (obrigatório)
- hash_arquivo (obrigatório)
- criptografado (boolean)
- ativo (boolean)
- uploaded_at (obrigatório)
- uploaded_by (FK usuarios)
```

### Tabela: tipos_documentos
```sql
- id (PK)
- nome_tipo (obrigatório)
- descricao
- obrigatorio (boolean)
- formato_permitido
- tamanho_maximo
- ativo (boolean)
- created_at
```

### Tabela: documento_acessos
```sql
- id (PK)
- documento_id (FK)
- usuario_id (FK)
- tipo_acesso (visualizacao/download/edicao)
- ip_origem
- user_agent
- data_acesso
- sucesso (boolean)
```

### Tabela: documento_validacoes
```sql
- id (PK)
- documento_id (FK)
- tipo_validacao (formato/tamanho/virus/conteudo)
- resultado_validacao (aprovado/rejeitado)
- detalhes_validacao
- usuario_validador (FK)
- data_validacao
```

## 🧪 Estratégia de Testes

### Testes Unitários
- Validação de formatos
- Cálculo de tamanhos
- Geração de hash
- Criptografia de arquivos

### Testes de Integração
- Sistema completo de upload
- Integração com agendamentos
- Sistema de segurança
- Backup e recuperação

### Testes de Interface
- Interface de upload
- Preview de documentos
- Responsividade
- Validação de formulários

## 🔗 Dependências

### Dependências Internas
- ✅ Sistema de autenticação (já implementado)
- ✅ Módulo de agendamentos (US #18)
- ✅ Upload de arquivos (já implementado)
- ✅ Sistema de logs (já implementado)

### Dependências Externas
- ✅ Serviço de armazenamento (já integrado)
- ✅ Serviço de antivírus (já integrado)
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
   - Implementar APIs de upload
   - Sistema de validação
   - Controle de segurança

2. **Frontend (8h)**
   - Interface de upload
   - Preview de documentos
   - Gerenciamento de anexos
   - Validação de formulários

3. **Testes (4h)**
   - Testes unitários
   - Testes de integração
   - Validação de segurança

---

**Status DoR:** ✅ **APROVADO**  
**Data de Validação:** 06/10/2024  
**Responsável pela Validação:** Marco Antonio Arantes  
**Próximo Passo:** Iniciar desenvolvimento
