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

## Em preparação

Ainda não fazem parte do plugin. Se o usuário pedir, dizer que não estão disponíveis nesta versão e anotar o interesse no perfil:

- saúde da operação
- comercial e funil
- conteúdo para redes sociais
- newsletter
- apresentação periódica para sócios
