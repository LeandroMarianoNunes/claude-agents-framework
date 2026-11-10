# Conectores

## Como as ferramentas são referenciadas

As skills deste plugin falam em categorias de ferramenta, não em produtos. Onde aparece `~~categoria`, vale a ferramenta que a empresa tiver conectada naquela categoria. A instalação (`/install-claude-agents-framework`) descobre quais existem e grava no perfil da empresa qual atende cada categoria.

O plugin não traz nenhuma conexão própria nem credencial: usa as que já estão conectadas no Claude da empresa.

## Categorias

| Categoria | Marcador | Exemplos | Usada por |
|---|---|---|---|
| Canal da gestão | `~~canal da gestão` | Microsoft Teams, Slack, Google Chat | todas (publicação e histórico) |
| E-mail | `~~e-mail` | Outlook, Gmail | alternativa de publicação; check-in com clientes (rascunhos e respostas) |
| Banco de dados | `~~banco de dados` | Supabase, Postgres, BigQuery, Snowflake | segurança e IA responsável |
| Logs | `~~logs` | logs da plataforma de dados, Datadog, CloudWatch | segurança e IA responsável |
| Repositório de código | `~~repositório de código` | GitHub, GitLab, Bitbucket | segurança e IA responsável |
| Pagamentos | `~~pagamentos` | Stripe, Pagar.me, Asaas | check-in com clientes (lista e situação) |
| CRM e tarefas | `~~crm` | HubSpot, Pipedrive, monday, ClickUp | check-in com clientes (lista, uso) |
| Nuvem e custos | `~~nuvem` | Azure, AWS, Google Cloud | finops (custo por dia e por recurso) |
| Documentos | `~~documentos` | SharePoint, Google Drive | finops (planilhas de fatura) |
| Pesquisa na web | (nativa) | busca e leitura de páginas | market intel, radar regulatório |
| Agendador | (nativo) | tarefas agendadas do Claude | instalação |

## Quando falta uma categoria

- Sem canal nem e-mail: a rotina entrega o resultado na própria conversa da execução.
- Sem banco, logs ou repositório: a rotina de segurança roda só com o que existir e lista o resto em "Não verificado". Sem nenhum dos três, não é instalada.
- Sem agendador: a instalação entrega os textos prontos para agendar à mão.
