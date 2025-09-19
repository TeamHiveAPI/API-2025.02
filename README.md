<!-- Logo + títulos -->
<p align="left">
  <img src="https://github.com/user-attachments/assets/d6263e54-8e7d-4358-9417-a58c240254cc" width="200" align="left">
</p>

<!-- Títulos em Markdown (fora do <p>) -->
### API 5º Semestre DSM  
### Aplicativo do Almoxarifado Militar  
### Team HIVE  

<br>
<br>
<br>

<!-- Links centralizados -->
<p align="center">
  | <a href="#desafio">Desafio</a> |
  <a href="#solucao">Solução</a> |   
  <a href="#backlog">Backlog do Produto</a> |
  <a href="#dor">DoR</a> |
  <a href="#dod">DoD</a> |
  <a href="#sprint">Cronograma de Sprints</a> |
  <a href="#tecnologias">Tecnologias</a> |
  <a href="#manual">Manual de Instalação</a> |
  <a href="#equipe">Equipe</a> |
</p>


## 🛠️ Tecnologias <a id="tecnologias"></a>

<h4 align="center">
 <a href="https://www.python.org/"><img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"></a>
 <a href="https://fastapi.tiangolo.com/"><img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/></a>
 <a href="https://www.typescriptlang.org/"><img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"></a>
 <a href="https://vuejs.org/"><img src="https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue.js&logoColor=4FC08D"/></a>
 <a href="https://www.atlassian.com/software/jira"><img src="https://img.shields.io/badge/Jira-0052CC?style=for-the-badge&logo=jira&logoColor=white"/></a>
 <a href="https://github.com/"><img src="https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white"/></a>
 <a href="https://www.figma.com/"><img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white"/></a>
</h4>

## 🎯 Desafio <a id="desafio"></a>

O projeto trata-se do desenvolvimento de um aplicativo para gestão do almoxarifado militar. Atualmente, o processo de controle de materiais é burocrático e suscetível a falhas, dificultando a organização, rastreabilidade e agilidade no atendimento das demandas. Essa dificuldade gera retrabalho, perda de tempo e risco de falta de materiais essenciais. Para resolver isso, o aplicativo precisa oferecer três pontos principais:

Cadastro de materiais: inserção e atualização de itens com informações completas.

Leitura por QR Code: agilizando entradas e saídas de materiais de forma automática e segura.

Interface intuitiva: design limpo, responsivo e de fácil uso, tanto em smartphones quanto em tablets.

## 🎯 Solução <a id="solucao"></a>

A solução proposta é um sistema simples e eficiente que centraliza o controle do almoxarifado em um único aplicativo. Ele permitirá cadastrar novos itens ou reabastecer estoque, registrar pedidos de forma rápida, gerar e ler QR Codes automaticamente e acompanhar o inventário em tempo real. Com isso, o almoxarifado terá mais organização, previsibilidade de consumo, transparência e redução de erros no processo de gestão de materiais.

---

## 📋 Backlog do Produto <a id="backlog"></a>

| Rank | Prioridade | User Story | Estimativa | Sprint |
|------|------------|------------|------------|--------|
| 1 | Alta | Como usuário, desejo fazer login no sistema para acessar minhas funcionalidades. | 3 | Sprint 1 |
| 2 | Alta | Como usuário, desejo registrar um novo pedido de material para solicitar itens necessários. | 5 | Sprint 1 |
| 3 | Alta | Como usuário, desejo agendar uma consulta (médica ou odontológica) para cuidar da minha saúde. | 4 | Sprint 1 |
| 4 | Alta | Como usuário, desejo visualizar e gerenciar meu perfil para manter minhas informações atualizadas. | 2 | Sprint 1 |
| 5 | Alta | Como usuário, desejo receber notificações sobre o status dos meus pedidos e agendamentos para me manter informado. | 4 | Sprint 1 |
| 6 | Alta | Como soldado, desejo visualizar um painel de controle simples com o status dos meus pedidos e próximas consultas para ter uma visão rápida. | 3 | Sprint 1 |
| 7 | Alta | Como soldado, desejo acompanhar o histórico e o status detalhado dos meus pedidos para saber o andamento. | 4 | Sprint 1 |
| 8 | Alta | Como gestor, desejo aprovar ou rejeitar pedidos pendentes do meu setor, com a opção de adicionar justificativa para rejeição. | 4 | Sprint 1 |
| 9 | Alta | Como gestor de almoxarifado, desejo consultar o estoque geral, incluindo lotes e validades, para ter controle dos materiais. | 4 | Sprint 1 |
| 10 | Alta | Como gestor de almoxarifado, desejo cadastrar a entrada de novos produtos com lote e data de vencimento para manter o inventário atualizado. | 3 | Sprint 1 |
| 11 | Alta | Como gestor de farmácia, desejo gerenciar o estoque de medicamentos com foco crítico em lote e data de vencimento para garantir a segurança. | 5 | Sprint 1 |
| 12 | Alta | Como gestor de farmácia, desejo receber alertas automáticos de medicamentos próximos ao vencimento para evitar perdas. | 4 | Sprint 1 |
| 13 | Alta | Como gestor odontológico, desejo gerenciar o estoque de insumos odontológicos, controlando lote e validade. | 4 | Sprint 1 |
| 14 | Média | Como soldado, desejo consultar o estoque disponível para solicitação de materiais antes de fazer um pedido. | 3 | Sprint 1 |
| 15 | Média | Como gestor de almoxarifado, desejo cadastrar novos tipos de produtos no catálogo para expandir as opções disponíveis. | 3 | Sprint 1 |
| 16 | Média | Como gestor de almoxarifado, desejo definir níveis de estoque mínimo e máximo por item para receber alertas. | 3 | Sprint 1 |
| 17 | Média | Como gestor de farmácia, desejo registrar a entrega (dispensação) de medicamentos a um paciente para controle. | 3 | Sprint 1 |
| 18 | Média | Como gestor de farmácia, desejo cadastrar novos medicamentos no sistema para manter o catálogo atualizado. | 3 | Sprint 1 |
| 19 | Média | Como gestor odontológico, desejo registrar procedimentos e materiais utilizados por paciente para histórico. | 4 | Sprint 1 |
| 20 | Média | Como gestor odontológico, desejo cadastrar novos insumos no catálogo de odontologia. | 3 | Sprint 1 |
| 21 | Alta | Como gestor de farmácia, desejo aprovar ou cancelar agendamentos de consultas médicas para organizar a agenda. | 3 | Sprint 2 |
| 22 | Alta | Como gestor odontológico, desejo aprovar ou cancelar agendamentos de consultas odontológicas. | 3 | Sprint 2 |
| 23 | Média | Como soldado, desejo visualizar meu histórico unificado de agendamentos (médicos e odonto) para ter controle das minhas consultas. | 3 | Sprint 2 |
| 24 | Média | Como soldado, desejo anexar documentos (receitas, atestados) aos meus agendamentos para facilitar o processo. | 3 | Sprint 2 |
| 25 | Média | Como soldado, desejo consultar meu histórico de medicamentos recebidos e tratamentos odontológicos realizados para referência. | 3 | Sprint 2 |
| 26 | Alta | Como gestor, desejo acessar um Painel de Controle Analítico com IA para visualizar gráficos de movimentação e alertas de validade do meu setor. | 5 | Sprint 3 |
| 27 | Alta | Como administrador, desejo visualizar o Painel de Controle Analítico com IA em uma visão global, podendo filtrar e comparar dados de todos os setores. | 5 | Sprint 3 |
| 28 | Alta | Como administrador, desejo cadastrar novos usuários no sistema. | 3 | Sprint 3 |
| 29 | Alta | Como administrador, desejo ativar/inativar usuários para gerenciar o acesso sem perder o histórico. | 3 | Sprint 3 |
| 30 | Alta | Como administrador, desejo gerenciar vínculos e patentes, atribuindo usuários a perfis de acesso e módulos de gestão específicos. | 4 | Sprint 3 |
| 31 | Alta | Como administrador, desejo acessar Logs de Auditoria completos para rastreabilidade total das ações no sistema. | 5 | Sprint 3 |
| 32 | Média | Como usuário, desejo recuperar minha senha caso a esqueça. | 2 | Sprint 3 |
| 33 | Média | Como gestor, desejo que o Dashboard com IA identifique padrões de sazonalidade de consumo dos itens do meu setor para otimizar o estoque. | 6 | Sprint 3 |
| 34 | Média | Como gestor, desejo que o Dashboard com IA preveja futuras tendências de estoque para o meu módulo para auxiliar no planejamento. | 5 | Sprint 3 |
| 35 | Média | Como gestor, desejo que o Dashboard com IA sugira ajustes nos níveis de estoque mínimo/máximo para melhorar a gestão. | 4 | Sprint 3 |
| 36 | Média | Como gestor, desejo gerar e exportar relatórios específicos do meu módulo de gestão (Estoque, Farmácia ou Odonto). | 4 | Sprint 3 |
| 37 | Média | Como administrador, desejo redefinir senhas de usuários para auxiliar no acesso. | 2 | Sprint 3 |

---

## 🏁 ‍DoR - Definition of Ready <a id="dor"></a>


* ✅ User Story escrita com **critérios de aceitação claros**  
* ✅ Subtarefas criadas a partir da **User Story**  
* ✅ **Design pronto** no Figma 
* ✅ **Modelagem do Banco de Dados** definida  
* ✅ **Fluxo de rotas** documentado  
* ✅ Dados de cliente **estruturados/vetorizados** (quando aplicável)  

## ✅ DoD - Definition of Done <a id="dod"></a>

* ✅ **Manual de Usuário** disponível  
* ✅ **Manual da Aplicação** documentado  
* ✅ **Documentação da API** atualizada  
* ✅ **Código completo e revisado**  
* ✅ **Vídeos e documentos de entrega** (explicando ou demonstrando cada etapa)  

---

## 🗓️ Cronograma de Sprints <a id="sprint"></a>

| Sprint          |    Período    | Documentação                                     |
| --------------- | :-----------: | ------------------------------------------------ |
| 🐝 **SPRINT 1** | 08/09 - 28/09 | [Sprint 1](./docs/processo/sprints/sprint-1/README.md) |
| 🐝 **SPRINT 2** | 06/10 - 26/10 | [Sprint 2](./docs/processo/sprints/sprint-2/README.md) |
| 🐝 **SPRINT 3** | 03/11 - 23/11 | [Sprint 3](./docs/processo/sprints/sprint-3/README.md) |

---

## 📖 Manual de Instalação <a id="manual"></a>

⏳ Em desenvolvimento

---

## 👷🏻 Time de Desenvolvimento <a id="equipe"></a>

| Foto | Nome | Função | Github | LinkedIn |
| :--: | :----: | :--: | :----: | :------: |
| <img src="https://github.com/maarantes.png?size=50" width=50px> | Marco Antonio Arantes | Scrum Master | <a href="https://github.com/maarantes"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com/in/marco-antonio-arantes/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
| <img src="https://github.com/eberssj.png?size=50" width=50px> | Eber de Souza Junior | DEV Team | <a href="https://github.com/eberssj"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com/in/eber-junior-b2a4a3211/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
| <a href="https://github.com/ErikaDias2"> <img src="https://avatars.githubusercontent.com/ErikaDias2" alt="fotoperfil" width="50"></a> | Erika Dias Ribeiro | DEV Team | <a href="https://github.com/erikadias2004"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com/in/erika-dias-ribeiro-608359266/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
| <a href="https://github.com/DiogoPalharini"> <img src="https://avatars.githubusercontent.com/DiogoPalharini" alt="fotoperfil" width="50"></a> | Diogo Palharini | Product Owner | <a href="https://github.com/DiogoPalharini"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com/in/diogo-palharini-10b803275/"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
| <a href="https://github.com/ojuansoares"><img src="https://avatars.githubusercontent.com/ojuansoares" alt="fotoperfil" width="50"></a> | Juan Garcia Soares | DEV Team | <a href="https://github.com/ojuansoares"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com/in/ojuansoares"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
| <a href="https://github.com/Gabriel4SS"><img src="https://avatars.githubusercontent.com/Gabriel4SS" alt="fotoperfil" width="50"></a> | Gabriel Santos | DEV Team | <a href="https://github.com/Gabriel4SS"><img src="https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white"></a> | <a href="https://www.linkedin.com"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"></a> |
