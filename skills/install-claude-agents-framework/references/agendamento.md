# Como montar a tarefa agendada

A execução agendada começa do zero: não lembra da entrevista e pode não ter acesso à pasta onde o perfil foi salvo. Por isso o texto da tarefa leva a configuração inteira da rotina. A skill leva o método; o texto leva a empresa.

## Texto da tarefa

Montar nesta ordem, substituindo tudo por valores reais (nenhum marcador pode sobrar):

```
Execute a skill "<nome da rotina>" do plugin claude-agents-framework com a configuração abaixo.
Ninguém acompanha esta execução: não faça perguntas no meio, decida e registre no resultado.

EMPRESA
<seção "Empresa" do perfil, completa>

ENTREGA
<destino desta rotina com identificadores, leitores, quem decide, fuso, regra de fim de semana>

REDAÇÃO
<idioma, tom, regras de estilo, pergunta de fechamento ligada ou desligada>

CONFIGURAÇÃO DA ROTINA
<seção da rotina no perfil: respostas da entrevista, verificações calibradas com consultas e limites, base de comparação, o que não está disponível>

Se a skill não estiver disponível nesta execução, não improvise: publique no destino uma linha dizendo que a rotina "<nome>" não rodou porque o plugin não está ativo, e encerre.
```

## Nome, horário e conexões

- Nome da tarefa: "<Rotina> · <Empresa>".
- Horário no fuso do perfil. Relatórios do mesmo dia em sequência, com intervalo de alguns minutos, e nunca em hora cheia.
- Dar à tarefa acesso às ferramentas que a rotina usa (as do inventário) e só a elas, quando o agendador permitir escolher.
- Manter o plugin ativo para a tarefa, quando o agendador tiver essa opção.

## Sem agendador

Se não existir ferramenta de agendamento, entregar ao usuário, para cada rotina, o texto completo acima em um bloco de código e a frequência combinada, com a instrução de onde colar no Claude dele. Registrar no perfil que o agendamento é manual.

## Depois de criar

Conferir que a tarefa aparece na lista e está ativa. Oferecer rodar uma vez agora, de verdade, para o primeiro relatório já servir de base de comparação.

## Mudança posterior

Qualquer ajuste (concorrente novo, limite diferente, outro canal) é feito no perfil e o texto da tarefa é remontado a partir dele. Nunca editar só a tarefa: o perfil é a fonte.
