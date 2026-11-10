# Conectores

## Como as ferramentas são referenciadas

As skills deste plugin falam em categorias de ferramenta, não em produtos. Onde aparece `~~categoria`, vale a ferramenta que a empresa tiver conectada naquela categoria. A instalação (`/install-claude-agents-framework`) descobre quais existem e grava no perfil da empresa qual atende cada categoria.

O plugin não traz nenhuma conexão própria nem credencial: usa as que já estão conectadas no Claude da empresa.

## Categorias

| Categoria | Marcador | Exemplos | Usada por |
|---|---|---|---|
| Canal da gestão | `~~canal da gestão` | Microsoft Teams, Slack, Google Chat | todas (publicação e memória entre edições) |
| E-mail | `~~e-mail` | Outlook, Gmail | alternativa de publicação; check-in com clientes, newsletter e resumo da gestão |
| Calendário | `~~calendário` | Outlook, Google Agenda | comercial (reuniões), check-in com clientes |
| CRM | `~~crm` | HubSpot, Pipedrive, RD Station, monday | comercial (funil), newsletter (lista), check-in com clientes |
| Pagamentos | `~~pagamentos` | Stripe, Pagar.me, Asaas | check-in com clientes (lista e situação), resumo da gestão (receita) |
| Tarefas | `~~tarefas` | ClickUp, Jira, Linear, Asana, Trello | produto (ciclo e entregas) |
| Repositório de código | `~~repositório de código` | GitHub, GitLab, Bitbucket | produto, segurança e IA responsável |
| Banco de dados | `~~banco de dados` | Supabase, Postgres, BigQuery, Snowflake | segurança e IA responsável, operação, check-in com clientes (uso) |
| Logs | `~~logs` | logs da plataforma de dados, Datadog, CloudWatch | segurança e IA responsável, operação |
| Nuvem e custos | `~~nuvem` | Azure, AWS, Google Cloud | finops (custo), operação (estado dos serviços) |
| Monitoramento | `~~monitoramento` | Datadog, Grafana, página de status | operação |
| Redes sociais | `~~redes sociais` | conexão oficial de Instagram, LinkedIn, YouTube, TikTok; ferramentas de gestão de redes | social-kpis (estatísticas), social-conteudo (publicação) |
| Navegador | `~~navegador` | navegador do responsável com a sessão aberta | social-kpis e social-conteudo, quando não há conexão oficial |
| Documentos | `~~documentos` | SharePoint, Google Drive | resumo da gestão (apresentação), finops e social-kpis (planilhas) |
| Pesquisa na web | (nativa) | busca e leitura de páginas | market intel, radar regulatório, newsletter |
| Agendador | (nativo) | tarefas agendadas do Claude | instalação |

## Quando falta uma categoria

- Sem canal nem e-mail: a rotina entrega o resultado na própria conversa da execução.
- Sem banco, logs ou repositório: a rotina de segurança roda só com o que existir e lista o resto em "Não verificado". Sem nenhum dos três, não é instalada.
- Sem agendador: a instalação entrega os textos prontos para agendar à mão.
- Sem conexão oficial de uma rede social: as rotinas de redes descem a escada de fontes descrita na skill `social-kpis`.

## Sobre o navegador

Algumas redes sociais não oferecem conexão oficial para ler estatísticas ou publicar. Nesses casos as rotinas de redes podem usar o navegador do responsável, com a sessão dele já aberta. Limites deste caminho:

- só funciona com o computador ligado e a sessão ativa;
- quebra quando a rede muda a tela, e a calibração precisa ser refeita;
- os termos de uso de cada rede têm regras sobre automação: cabe à empresa conferir se o uso que pretende é permitido;
- a rotina nunca digita senha nem resolve verificação de segurança. Se a rede pedir login, ela para e avisa.
