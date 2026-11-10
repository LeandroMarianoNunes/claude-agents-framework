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
3. Responder à entrevista (cerca de 15 minutos para as três rotinas) e aprovar o ensaio de cada uma.

Rodar o mesmo comando de novo serve para adicionar, ajustar ou remover rotinas.

## O que vem nesta versão

| Skill | O que faz |
|---|---|
| `install-claude-agents-framework` | Entrevista, perfil da empresa, calibração, ensaio e agendamento |
| `market-intel` | Concorrentes e tendências, com fonte conferida e leitura para a empresa |
| `radar-regulatorio` | Leis, normas e políticas que afetam a empresa, com tabela de prazos |
| `seguranca-e-ia-responsavel` | Semáforo diário de vazamento, acesso indevido e conduta da IA |
| `cx-check-in` | E-mail pessoal por cliente conforme a situação da conta, em rascunho para revisão, e relatório de risco de cancelamento |
| `finops` | Semáforo diário de custos de nuvem e de fornecedores, com projeção do mês contra o orçamento |

Em preparação: operação, comercial, redes sociais, newsletter e apresentação para sócios.

## Como funciona

- **As skills guardam o método**: o que verificar, como julgar, o que nunca fazer (alterar sistemas, expor dado pessoal, inventar número).
- **O perfil guarda a empresa**: quem é, onde publicar, como escrever, quais ferramentas atendem cada necessidade e as verificações calibradas para o ambiente dela. Fica em `claude-agents-framework/perfil-da-empresa.md`, na pasta de trabalho do usuário.
- **A tarefa agendada leva a configuração junto**, porque cada execução começa do zero.

Nenhuma credencial é pedida ou guardada. Ver `CONNECTORS.md` para as categorias de ferramenta.

## Limites conhecidos

- A rotina de segurança depende da calibração feita na instalação. Em ambientes sem acesso de leitura a banco, logs ou repositório, ela encolhe ou não é instalada.
- A primeira semana serve para ajustar limites e ruído.
- O plugin ainda não foi testado em uma empresa além da que originou as rotinas.

## Licença

MIT. Ver `LICENSE`.
