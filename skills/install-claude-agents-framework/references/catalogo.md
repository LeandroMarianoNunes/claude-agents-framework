# Catálogo de rotinas

Para cada rotina: o que entrega, o que precisa (categorias de `CONNECTORS.md`), a frequência padrão, as perguntas específicas e o que calibrar. "Obrigatório" impede a instalação se faltar; "opcional" só reduz o relatório.

## market-intel

- **Entrega:** resumo de concorrentes e tendências do mercado da empresa, com fonte e data conferidas, leitura do impacto e até três ações sugeridas.
- **Precisa:** pesquisa na web (obrigatório), `~~canal da gestão` ou e-mail para publicar (obrigatório; sem isso, entrega só na conversa).
- **Frequência padrão:** diária em dias úteis. Alternativa: semanal.
- **Perguntas:**
  1. Quais concorrentes diretos acompanhar. Propor uma lista inicial a partir de uma pesquisa e pedir correção.
  2. Empresas vizinhas que podem virar concorrentes ou parceiras.
  3. Mercados (país, região) e idiomas de busca.
  4. Temas de tendência que interessam (tecnologia, comportamento do cliente, preço, regulação do setor).
  5. Quantos itens no máximo por edição (padrão: 10).
- **Calibrar:** nada em sistemas internos. Conferir que a pesquisa na web funciona e que dá para ler o histórico do destino (para não repetir notícia).

## radar-regulatorio

- **Entrega:** leis, normas, decisões e políticas de plataforma que afetam a empresa, separando o que está em vigor do que é proposta, com prazos acompanhados em tabela.
- **Precisa:** pesquisa na web (obrigatório), destino para publicar (obrigatório).
- **Frequência padrão:** diária. Para setores pouco regulados, semanal.
- **Perguntas:**
  1. Jurisdições que importam (onde a empresa opera e onde estão os clientes).
  2. Temas regulatórios. Propor a lista a partir do perfil (dados pessoais, consumidor, tributário, trabalhista, setorial, plataformas das quais depende, IA se usar) e pedir correção.
  3. Reguladores e fontes oficiais do setor.
  4. Quem é o jurídico (interno ou escritório) para a rotina indicar como responsável.
  5. Prazos que a empresa já sabe que precisa cumprir, para começar a tabela.
- **Calibrar:** nada em sistemas internos.

## seguranca-e-ia-responsavel

- **Entrega:** semáforo diário de segurança e vazamento de dados; para empresas com produto de IA, também a revisão de conduta da IA nas conversas do dia.
- **Precisa:** pelo menos um entre `~~banco de dados`, `~~logs` e `~~repositório de código` (obrigatório), destino para publicar (obrigatório). Cada um que faltar remove as verificações correspondentes. A parte de IA responsável exige acesso de leitura às conversas da IA.
- **Frequência padrão:** diária.
- **Perguntas:**
  1. Quais sistemas guardam dados de clientes e qual é o ambiente de produção.
  2. O que seria um incidente grave para esta empresa (para definir o que é crítico).
  3. Que dados nunca podem aparecer em relatório (define o mascaramento além do padrão).
  4. Se há produto de IA: quais são as regras de conduta que a IA nunca pode quebrar. Propor o conjunto padrão da skill e ajustar.
  5. Quem recebe alerta crítico e se o destino dos críticos é diferente do relatório normal.
- **Calibrar (o passo mais importante desta rotina):** percorrer em modo leitura cada verificação descrita na skill e traduzi-la para este ambiente: qual consulta, em qual tabela ou log, com qual limite. Rodar uma vez e gravar os números de hoje como base de comparação. Listar o que não foi possível verificar.

## cx-check-in

- **Entrega:** um e-mail pessoal por cliente, escolhido pela situação da conta, e um relatório de risco de cancelamento para a gestão.
- **Atenção:** é a única rotina que escreve para fora da empresa. Instala sempre em modo rascunhos (uma pessoa revisa e envia). O envio direto só pode ser ligado depois de pelo menos um ciclo em rascunhos e com autorização explícita de quem decide, registrada no perfil com nome e data.
- **Precisa:** lista de clientes em `~~pagamentos` ou `~~crm` (obrigatório), `~~e-mail` da caixa que vai assinar (obrigatório), destino para o relatório (obrigatório), fonte de uso em `~~banco de dados` ou no próprio `~~crm` (opcional; sem ela, os casos se baseiam só na cobrança).
- **Frequência padrão:** quinzenal. O agendador dispara toda semana, no mesmo dia, e a rotina pula as semanas fora do ciclo a partir da data-âncora.
- **Perguntas:**
  1. De onde vem a lista de clientes e quais situações entram (pagantes, em teste, cadastrados sem plano, cancelados recentes).
  2. Quem assina e de qual caixa sai. Tem de ser uma pessoa real, que vai ler as respostas.
  3. Qual é o passo de ativação: o que o cliente precisa fazer para o produto funcionar de verdade.
  4. Quais sinais de uso existem e onde ficam (último acesso, volume no período).
  5. Materiais de ajuda para citar (vídeos, artigos) e link de agenda para conversa, se houver.
  6. Quem nunca deve receber (sócios, equipe, parceiros, contas de teste).
  7. Limites: dias sem acesso e dias sem ativar que viram risco alto, dias de cancelado até sair da lista, carência de cliente novo (padrão 3 dias).
  8. Limite de e-mails por execução (padrão 50).
  9. Onde registrar pedido de saída: só pela leitura das respostas (padrão) ou também marcando o cadastro do cliente.
  10. Texto do rodapé: contato para dúvidas sobre dados pessoais e link da política de privacidade.
- **Calibrar:** ler a lista real e mostrar ao usuário quantos clientes entram em cada situação, para ele confirmar que o número faz sentido; mapear onde está cada sinal de uso e escrever a consulta, sempre filtrada por cliente; conferir que dá para criar rascunho na caixa do remetente, ler as respostas recebidas e ver os convites de agenda (para saber quem já está em conversa); gravar a contagem de hoje como base da trava de volume.
- **Ensaio:** mostra a tabela de clientes com o caso e o risco de cada um e três e-mails de exemplo (um por caso diferente). Não cria rascunho.

## finops

- **Entrega:** semáforo diário de custos: nuvem (ontem, mês, projeção contra o orçamento, o que subiu) e fornecedores pagos por uso (consumo, franquia, saldo).
- **Precisa:** pelo menos uma fonte de custo legível (obrigatório), destino para publicar (obrigatório). As fontes possíveis, da melhor para a mais limitada:
  1. conexão de `~~nuvem` ou do fornecedor que já lê custo e uso;
  2. acesso de leitura criado pela própria empresa (por exemplo, uma credencial só de leitura de custos) usado por um pequeno programa de coleta. Só funciona em tarefa agendada que roda no computador ou ambiente onde a credencial está guardada;
  3. faturas e avisos de cobrança em `~~e-mail` ou planilha em `~~documentos`: vira acompanhamento mensal daquele item, sem visão diária.
- **Frequência padrão:** diária, como primeiro relatório do dia. Só com fontes do tipo 3, semanal.
- **Perguntas:**
  1. Orçamento mensal de nuvem e moeda. Se não houver orçamento, propor um a partir da média dos últimos meses e confirmar.
  2. Quais contas de nuvem entram.
  3. Quais fornecedores são pagos por uso. Partir da lista de fornecedores críticos do perfil e perguntar por outros.
  4. Para cada fornecedor: como se cobra (por uso, franquia mensal, crédito pré-pago, fatura fixa).
  5. Recursos que devem ficar desligados (ambientes de teste, serviços pausados), para avisar se voltarem.
  6. Limites de alerta e piso de relevância (valor abaixo do qual uma variação não vira alerta), se quiser mudar os padrões da skill.
  7. Moeda do relatório e como converter as outras (taxa fixa combinada ou cotação do dia de uma fonte indicada).
- **Calibrar (o passo que decide se a rotina presta):** para cada conta e cada fornecedor, descobrir em modo leitura qual das três fontes existe, ler uma vez e registrar no perfil o método (consumo medido, franquia, saldo, só fatura), a consulta e o número de hoje. Se a única saída for o tipo 2, explicar ao usuário que acesso de leitura ele precisa criar e onde guardar, sem nunca pedir que cole a credencial na conversa; o programa de coleta é escrito na instalação, salvo na pasta de trabalho, e nunca imprime segredo. Listar o que ficou sem fonte.
- **Ensaio:** mostra o relatório com os números reais lidos na calibração. Como ainda não há edição anterior, os consumos por saldo aparecem como "começa a medir amanhã".

## comercial

- **Entrega:** funil por etapa com a variação do dia, o que se moveu, a agenda de reuniões cruzada com o CRM, o que está vencido ou esquecido e as três ações de maior valor do dia.
- **Precisa:** `~~crm` com leitura dos negócios e dos campos (obrigatório), destino para publicar (obrigatório), `~~calendário` de quem vende (opcional; sem ele, a agenda vem só do CRM).
- **Frequência padrão:** diária em dias úteis.
- **Perguntas:**
  1. Qual quadro, funil ou lista do CRM é o comercial, e quais etapas ele tem, na ordem.
  2. O que conta como lead quente, e se há campos de temperatura, tipo de cliente e origem.
  3. Onde fica o próximo contato, a data de reunião e a data de fim de teste ou de validade da proposta.
  4. Limites: dias sem primeiro contato, dias parado por etapa, antecedência do aviso de teste acabando.
  5. Metas comerciais do mês, se houver.
  6. De quem é o calendário que vale para as reuniões.
- **Calibrar:** ler a estrutura do CRM e montar o mapa de campos (nome ou identificador de cada campo e os valores possíveis); mostrar ao usuário a contagem por etapa para ele confirmar que bate com o que vê no CRM; conferir se o CRM tem histórico de atividades para calcular a variação; gravar o funil de hoje como base.

## produto

- **Entrega:** andamento do ciclo atual, o que foi entregue desde ontem, situação da esteira de publicação e o que está travado.
- **Precisa:** `~~tarefas` com o quadro do time (obrigatório), destino para publicar (obrigatório), `~~repositório de código` (opcional; sem ele, não há visão de esteira nem de código integrado).
- **Frequência padrão:** diária em dias úteis.
- **Perguntas:**
  1. Onde ficam as tarefas do time e como se identifica o ciclo atual.
  2. Quais situações existem e qual delas significa "entregue".
  3. Qual repositório e qual é a versão principal; como se reconhece que algo chegou à produção.
  4. Limites de tarefa parada e de alteração de código sem movimento.
- **Calibrar:** ler o quadro inteiro do ciclo e conferir a contagem com o usuário; mapear no repositório onde aparecem as verificações automáticas e as publicações; registrar o que é normal hoje.

## operacao

- **Entrega:** semáforo diário da saúde dos serviços: o que está no ar, o que reiniciou, filas paradas, página de status, fornecedores externos e o que não pôde ser verificado.
- **Precisa:** pelo menos uma fonte de estado dos serviços, entre `~~nuvem`, `~~monitoramento`, `~~banco de dados` ou a página de status da empresa (obrigatório), destino para publicar (obrigatório). Vale a mesma escada do FinOps: conexão que já lê; acesso de leitura criado pela empresa e usado por um programa de coleta; ou só páginas públicas de status.
- **Frequência padrão:** diária, logo depois do relatório de custos.
- **Perguntas:**
  1. Quais serviços compõem o produto e quais são de produção.
  2. O que é normal: quantos reinícios por dia, quanto de fila, quanto de erro.
  3. Recursos que ficam desligados de propósito, para não virarem alarme.
  4. Se há página de status ou verificador de disponibilidade.
  5. Quem recebe alerta crítico.
- **Calibrar:** para cada serviço, achar onde ler o estado e rodar uma vez; registrar o normal de hoje; listar o que ficou sem verificação. Lembrar o usuário de que parte não verificada deixa o semáforo amarelo.

## social-kpis

- **Entrega:** evolução de cada perfil nas redes (público, alcance, engajamento, resultado), melhores e piores posts e um ou dois aprendizados com ação.
- **Precisa:** pelo menos uma fonte de dados por perfil (obrigatório), destino para publicar (obrigatório). A escada de fontes está na skill: conexão oficial da rede, ferramenta de gestão de redes, navegador com a sessão do responsável, dados públicos ou exportação manual.
- **Frequência padrão:** diária quando a fonte é dos três primeiros degraus; semanal nos outros.
- **Perguntas:**
  1. Quais perfis acompanhar, em quais redes.
  2. Metas por perfil e a data de cada uma.
  3. Se há posts impulsionados, para ficarem fora das medianas.
  4. Se a equipe mantém algum registro do que publica (formato, objetivo), ou se vai instalar a rotina de conteúdo.
- **Calibrar (decide quanto a rotina enxerga):** por perfil, testar os degraus na ordem e registrar o primeiro que funciona, com o que ele entrega e o que não entrega. No degrau do navegador, registrar a lista exata de páginas de estatísticas a abrir e confirmar com o usuário que a sessão é dele e que a rotina só lê. Avisar que esse degrau depende do computador ligado e pode quebrar quando a rede mudar a tela. Gravar os seguidores de hoje como base.

## social-conteudo

- **Entrega:** a peça do dia para cada perfil, escrita no método da casa, com prévia para aprovação; publica só o que for aprovado e mantém o diário de conteúdo.
- **Atenção:** publica em nome da empresa ou de uma pessoa. Nada sai sem aprovação daquela peça, naquela rede. Não existe modo de publicação automática.
- **Precisa:** canal para mandar a prévia a quem aprova (obrigatório). Meio de produção das peças e caminho de publicação são opcionais: sem eles, a rotina entrega texto, roteiro e o passo a passo para publicar à mão.
- **Depende de:** rende mais com `market-intel` (pauta) e `social-kpis` (o que funcionou) instaladas.
- **Frequência padrão:** diária, com o calendário de formatos da entrevista.
- **Perguntas:**
  1. Quais perfis, e quem aprova cada um.
  2. Para quem se fala e quais dores e perguntas são temas perenes.
  3. Posicionamento, oferta e o canal de conversão (link, mensagem, formulário).
  4. Calendário: qual formato em qual dia e o objetivo padrão de cada um.
  5. Identidade visual e modelos existentes.
  6. Para perfil de porta-voz: os assuntos, as opiniões que ele defende e o que ele não comenta.
  7. Como avisar que um conteúdo foi feito com IA.
  8. Horário de publicação.
- **Calibrar:** descobrir com o que dá para produzir cada formato e por onde publicar em cada rede; fazer uma peça de ensaio completa e mostrar. No caminho pelo navegador, confirmar o perfil certo antes de qualquer teste e não publicar nada no ensaio.

## newsletter

- **Entrega:** a edição periódica (sinais de mercado, novidades da empresa, uma dica), com a lista já limpa de quem pediu para sair, e o relatório de envio.
- **Atenção:** escreve para muita gente de fora de uma vez. Instala sempre em modo rascunhos; o envio direto só pode ser ligado depois de duas edições em rascunho e com autorização registrada.
- **Precisa:** lista de contatos no `~~crm` (obrigatório), `~~e-mail` da caixa remetente (obrigatório), destino para o relatório (obrigatório).
- **Depende de:** `market-intel` para os sinais e `produto` para as novidades; sem elas, pesquisa e lê as fontes diretas.
- **Frequência padrão:** semanal.
- **Perguntas:**
  1. Quem entra na lista e com qual base legal (deixou o contato, é cliente, se inscreveu). Quem fica sempre de fora.
  2. Segmentos e a frase de "por que você recebe" de cada um.
  3. Nome, remetente, modelo de e-mail e seções.
  4. Quem é o leitor: o critério de relevância dos sinais.
  5. O que conta como novidade publicável e de onde ler.
  6. Chamada final (seguir as redes, responder, agendar).
  7. Texto do rodapé: como cancelar, contato de privacidade, link da política.
  8. Limite de destinatários por edição.
- **Calibrar:** ler a lista e mostrar quantos contatos caem em cada segmento e quantos são excluídos por cada regra; conferir a saúde do domínio remetente; conferir que dá para criar rascunho com o modelo sem perder a formatação; gravar o tamanho da lista como base da trava de volume.

## resumo-da-gestao

- **Entrega:** a apresentação da reunião de sócios ou de diretoria, atualizada com o período, e o e-mail aos participantes com as decisões a tomar.
- **Precisa:** onde salvar a apresentação em `~~documentos` (obrigatório), um meio de gerar a apresentação (obrigatório), `~~e-mail` (opcional; sem ele, só salva e avisa).
- **Depende de:** todas as outras. Com poucas rotinas instaladas, a apresentação fica com poucas seções; instalar por último.
- **Frequência padrão:** semanal, algumas horas antes da reunião.
- **Perguntas:**
  1. Dia e hora da reunião, e quem participa (a lista fixa de destinatários).
  2. Quais seções a apresentação tem. Se já existe uma, pedir o arquivo e usar como modelo.
  3. Onde salvar e como nomear.
  4. Quais números financeiros entram e de onde vêm.
  5. Taxa de câmbio combinada, se houver valores em mais de uma moeda.
- **Calibrar:** gerar uma edição de ensaio a partir do modelo e mostrar todos os slides; conferir que a pasta é acessível aos participantes.

## Ordem sugerida de instalação

1. As que não dependem de sistema interno: `market-intel`, `radar-regulatorio`.
2. As de leitura de sistemas: `finops`, `operacao`, `produto`, `comercial`, `seguranca-e-ia-responsavel`, `social-kpis`.
3. As que escrevem para fora, depois de a equipe confiar nos relatórios: `cx-check-in`, `newsletter`, `social-conteudo`.
4. Por último, `resumo-da-gestao`.

## Fora do catálogo

Se o usuário pedir uma rotina que não está aqui, dizer que não está disponível nesta versão e anotar o interesse no perfil.
