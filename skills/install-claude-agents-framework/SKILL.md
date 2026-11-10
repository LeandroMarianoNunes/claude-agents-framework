---
name: install-claude-agents-framework
description: >
  Esta skill deve ser usada quando o usuário pedir para "instalar o framework de agentes",
  "instalar as rotinas", "configurar as rotinas agendadas", "/install-claude-agents-framework",
  ou quiser adicionar, alterar ou remover uma rotina já instalada. Entrevista a empresa,
  descobre as ferramentas conectadas, monta o perfil, ensaia cada rotina e cria os agendamentos.
metadata:
  version: "0.1.0"
---

# Instalação do Claude Agents Framework

Conduzir a instalação como uma conversa: descobrir o que a empresa tem, perguntar só o que não dá para descobrir, ensaiar cada rotina antes de agendar. Quem está do outro lado pode não ser técnico: falar em termos do que a rotina faz e entrega, nunca em nomes de arquivo, ferramenta interna ou campo de configuração.

Responder no idioma do usuário. Os textos desta skill estão em português; adaptar ao idioma dele.

## Princípios

- **Descobrir antes de perguntar.** Tudo o que as ferramentas conectadas respondem (nome da empresa, canais existentes, sistemas em uso) não vira pergunta, vira confirmação.
- **Uma pergunta por vez.** Pergunta de escolha vai com opções (usar a ferramenta de pergunta com botões quando existir); pergunta aberta (nome, site, lista de concorrentes) vai em texto simples, de preferência já com uma proposta para o usuário corrigir. Nunca despejar um formulário.
- **As ferramentas conectadas podem não ser desta empresa.** Quem instala pode ser um consultor ou alguém com contas de mais de uma empresa. Confirmar, antes de ler qualquer sistema interno, que ele pertence à empresa que está sendo instalada.
- **Somente leitura durante toda a instalação.** A única escrita permitida é: salvar o perfil, criar os agendamentos e, no ensaio, nada. O ensaio não publica.
- **Nunca pedir senha, token ou chave.** Se falta uma conexão, dizer qual tipo de ferramenta falta e pedir que o usuário conecte pelo caminho normal do Claude dele.
- **Rotina sem fonte de dados não é instalada pela metade em silêncio.** Oferecer a versão reduzida (dizendo o que fica de fora) ou pular.
- **Nada é agendado sem ensaio aprovado.**
- **Rotina que escreve para fora da empresa nasce em modo rascunho.** Quando o catálogo marcar "Atenção", explicar ao usuário, antes das perguntas da rotina, o que ela envia e para quem, e instalar no modo que exige revisão humana. Não oferecer o envio direto na instalação.

## Etapa 0. Já existe instalação?

Procurar o perfil da empresa (`claude-agents-framework/perfil-da-empresa.md` na pasta de trabalho, ou o local que o usuário indicar). Se existir, não refazer a entrevista: mostrar o que está instalado e perguntar se quer adicionar uma rotina, ajustar uma existente, trocar destino ou horário, ou remover. Ir direto à etapa correspondente.

Com ou sem perfil, listar as tarefas agendadas que já existem na conta. Se alguma já faz o papel de uma rotina do catálogo (mesmo assunto, mesmo destino), avisar e perguntar, rotina por rotina, se o framework substitui a tarefa existente, convive com ela ou fica de fora. Nunca desativar nem apagar tarefa existente sem essa resposta.

## Etapa 1. Inventário silencioso

Antes da primeira pergunta, levantar o que está disponível nesta conta, sem alterar nada:

1. Listar as ferramentas e conectores disponíveis (inclusive os que carregam sob demanda) e classificar cada um nas categorias de `CONNECTORS.md` na raiz do plugin: canal da gestão, e-mail, banco de dados, logs, repositório de código, CRM, pagamentos, nuvem e custos, documentos, pesquisa na web, agendador.
2. Para o canal da gestão e o e-mail, listar equipes, canais ou caixas visíveis. Para banco e repositório, listar projetos e repositórios visíveis. Só nomes, sem ler conteúdo.
3. Verificar se existe uma ferramenta de agendamento de tarefas. Se não existir, a instalação continua e termina entregando os textos prontos para o usuário agendar à mão.

Abrir a conversa com três linhas sobre o que vai acontecer (entrevista curta, ensaio de cada rotina, agendamento) e uma tabela "o que encontrei conectado" com categoria, ferramenta e para que serve aqui. Marcar as categorias vazias como "não conectado". Logo depois da primeira pergunta (qual é a empresa), confirmar quais dos sistemas encontrados são dela; os que não forem saem do inventário e contam como "não conectado".

## Etapa 2. Entrevista

Seguir `references/entrevista.md`. São quatro blocos, nesta ordem: a empresa, para quem e onde entregar, jeito de escrever, quais rotinas. O bloco de cada rotina escolhida vem depois, na etapa 4.

Encerrar o bloco de rotinas mostrando o catálogo de `references/catalogo.md` já cruzado com o inventário: para cada rotina, "pronta para instalar", "instala em versão reduzida (falta X)" ou "não dá ainda (falta X)". O usuário escolhe quais quer.

## Etapa 3. Perfil da empresa

Preencher `references/perfil-modelo.md` com as respostas e o inventário, salvar como `claude-agents-framework/perfil-da-empresa.md` na pasta de trabalho do usuário (perguntar o local só se não houver pasta de trabalho) e mostrar um resumo de dez linhas para confirmação. Corrigir o que o usuário apontar antes de seguir.

O perfil nunca guarda credencial. Guarda nomes e identificadores de onde ler e onde publicar.

## Etapa 4. Instalar cada rotina

Para cada rotina escolhida, uma de cada vez, na ordem do catálogo:

1. **Perguntas da rotina.** Fazer as perguntas específicas listadas no catálogo para ela (o que monitorar, limites de alerta, o que é crítico para esta empresa).
2. **Calibração.** Quando a rotina lê sistemas internos (banco, logs, repositório), explorar esses sistemas em modo leitura para transformar cada verificação genérica em uma verificação concreta deste ambiente: quais tabelas, quais consultas, quais endpoints, qual é o número de hoje que servirá de base de comparação. Registrar o resultado na seção da rotina no perfil. Verificação que não tem como ser feita neste ambiente é registrada como "não disponível", com o motivo.
3. **Ensaio.** Executar a skill da rotina com a configuração montada, em modo ensaio: faz todo o trabalho e mostra na conversa o que publicaria, sem publicar. Nas rotinas de pesquisa, o ensaio usa a janela de 30 dias da edição de partida (descrita na skill), porque a janela normal de 48 horas costuma vir vazia e não mostra ao usuário como o relatório fica. Perguntar se o resultado serve. Ajustar e repetir até servir (limite prático: três rodadas; depois disso, propor instalar como está e ajustar com o uso).
4. **Horário.** Propor um horário coerente com as outras rotinas (relatórios do dia em sequência, com alguns minutos entre um e outro, no fuso do usuário) e a frequência padrão do catálogo. Confirmar.
5. **Agendamento.** Criar a tarefa agendada com o texto montado conforme `references/agendamento.md`. Conferir que a tarefa foi criada e está ativa, e anotar no perfil o nome, o horário e a data de instalação.

Se o usuário cansar no meio, parar onde está: o que já foi agendado continua valendo, e o perfil registra o que falta.

## Etapa 5. Fechamento

Mostrar uma tabela final: rotina, quando roda, onde publica, o que ficou de fora e por quê. Em seguida, em poucas linhas:

- como mudar algo depois (pedir "ajustar a rotina X" ou rodar esta instalação de novo);
- como rodar uma rotina na hora (pedir pelo nome dela);
- que a primeira semana é de calibração: os primeiros relatórios servem para ajustar o que é ruído e o que importa.

Terminar com uma única pergunta sobre o próximo passo mais útil (por exemplo, rodar agora a primeira rotina de verdade).

## Remover ou pausar

Para remover uma rotina: desativar ou excluir a tarefa agendada correspondente (confirmar antes de excluir), e marcar a rotina como removida no perfil. Não apagar o perfil nem as outras rotinas.

## Arquivos de apoio

- `references/entrevista.md`: roteiro das perguntas, bloco a bloco
- `references/catalogo.md`: rotinas disponíveis, o que cada uma precisa e as perguntas específicas
- `references/perfil-modelo.md`: modelo do perfil da empresa
- `references/agendamento.md`: como montar o texto da tarefa agendada
