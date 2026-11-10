# Claude Agents Framework

Rotinas agendadas de gestão que se instalam por entrevista. A empresa instala o plugin, roda um comando e o Claude descobre as ferramentas conectadas, pergunta o que falta, ensaia cada rotina e agenda.

## Como usar

1. Instalar o plugin no Claude da empresa. No Claude Code, a partir deste repositório:
   ```
   claude plugin marketplace add LeandroMarianoNunes/claude-agents-framework
   claude plugin install claude-agents-framework@claude-agents
   ```
   O plugin só aparece em sessões abertas depois da instalação.
2. Abrir uma sessão nova e rodar `/install-claude-agents-framework` (se o Claude pedir o nome completo: `/claude-agents-framework:install-claude-agents-framework`).
3. Responder à entrevista (de 5 a 10 minutos por rotina) e aprovar o ensaio de cada uma.

Rodar o mesmo comando de novo serve para adicionar, ajustar ou remover rotinas.

## O que vem nesta versão

| Skill | O que faz | Escreve para fora? |
|---|---|---|
| `install-claude-agents-framework` | Entrevista, perfil da empresa, calibração, ensaio e agendamento | não |
| `market-intel` | Concorrentes e tendências, com fonte conferida e leitura para a empresa | não |
| `radar-regulatorio` | Leis, normas e políticas que afetam a empresa, com tabela de prazos | não |
| `finops` | Custos de nuvem e de fornecedores, com projeção do mês contra o orçamento | não |
| `operacao` | Saúde dos serviços, filas, página de status e fornecedores | não |
| `produto` | Andamento do ciclo, entregas, esteira de publicação e bloqueios | não |
| `comercial` | Funil do CRM, movimento, agenda, itens vencidos e foco do dia | não |
| `seguranca-e-ia-responsavel` | Vazamento, acesso indevido e conduta da IA | não |
| `social-kpis` | Evolução das redes, melhores posts e aprendizados | não |
| `cx-check-in` | E-mail pessoal por cliente e relatório de risco de cancelamento | sim, em rascunho |
| `newsletter` | Edição periódica com a lista limpa de quem pediu para sair | sim, em rascunho |
| `social-conteudo` | Peça do dia para as redes, no método da casa | sim, só com aprovação de cada peça |
| `resumo-da-gestao` | Apresentação da reunião de sócios ou diretoria, com as decisões a tomar | sim, para a lista fixa de participantes |

As rotinas conversam entre si pelo que publicam: a de conteúdo usa os sinais da de mercado e os números da de redes, a newsletter usa mercado e produto, e o resumo da gestão junta todas.

## Como funciona

- **As skills guardam o método**: o que verificar, como julgar, o que nunca fazer (alterar sistemas, expor dado pessoal, inventar número).
- **O perfil guarda a empresa**: quem é, onde publicar, como escrever, quais ferramentas atendem cada necessidade e as verificações calibradas para o ambiente dela. Fica em `claude-agents-framework/perfil-da-empresa.md`, na pasta de trabalho do usuário.
- **A tarefa agendada leva a configuração junto**, porque cada execução começa do zero.

Nenhuma credencial é pedida ou guardada. Ver `CONNECTORS.md` para as categorias de ferramenta.

## Limites conhecidos

- As rotinas que leem sistemas internos (segurança, custos, operação, produto, comercial) dependem da calibração feita na instalação. Sem acesso de leitura à fonte, encolhem ou não são instaladas.
- As rotinas de redes sociais dependem de como cada rede deixa ler os dados. Sem conexão oficial, usam o navegador do responsável, que é o caminho mais frágil. Ver `CONNECTORS.md`.
- A primeira semana serve para ajustar limites e ruído.
- O plugin ainda não foi testado em uma empresa além da que originou as rotinas.

## Licença

MIT. Ver `LICENSE`.
