# Histórias de Usuário — Organizador de Liga/Campeonato

**Produto:** Torneioz
**Persona:** Marcos Vinícius, o organizador que profissionalizou a "pelada"
**Jornada de referência:** Homologar as súmulas de uma rodada e ver a tabela de classificação atualizar automaticamente, sem retrabalho manual

---

# Acessar o painel do organizador após o fim da rodada

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Acessar o painel do organizador após o fim da rodada

## Geral
- **Produto:** Torneioz
- **Título:** Acessar o painel do organizador após o fim da rodada
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero acessar rapidamente um painel com o resumo da rodada recém-encerrada,
Para saber de imediato quantas súmulas já chegaram e quais ainda estão pendentes, sem procurar informação em vários lugares.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** organizador, painel-administrativo

## Detalhes

### Descrição Detalhada
Esta história cobre o ponto de entrada do organizador na plataforma logo após o encerramento de uma rodada. Ao autenticar-se e acessar o painel, ele deve ver de imediato um resumo do estado da rodada — quantos jogos ocorreram, quantas súmulas já foram enviadas pelos árbitros e quantas ainda estão pendentes — sem precisar navegar por múltiplas telas. A experiência deve priorizar clareza imediata, já que o organizador normalmente acessa isso com pouco tempo disponível entre um compromisso e outro.

### Orientações de Tela
- Título: "Painel do Organizador"
- Bloco de resumo da rodada atual: "X de Y súmulas homologadas"
- Lista de jogos da rodada com status (Pendente / Enviada / Homologada)
- Atalho direto para a próxima súmula pendente
- Indicador visual (badge) quando há súmulas aguardando homologação

### Regras de Negócio
- O painel exibe por padrão a rodada mais recente com jogos já realizados
- Um jogo só é considerado "com súmula enviada" quando o árbitro concluiu o registro
- O organizador deve conseguir navegar para rodadas anteriores a partir do painel

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso ao painel com súmulas pendentes
Dado que estou autenticado como organizador e a rodada atual tem jogos com súmula pendente
Quando eu acesso o Painel do Organizador
Então o sistema deve exibir a lista de jogos da rodada com o status de cada súmula

Acesso ao painel sem jogos na rodada atual
Dado que estou autenticado como organizador e ainda não há jogos registrados na rodada atual
Quando eu acesso o Painel do Organizador
Então o sistema deve exibir uma mensagem informando que não há jogos disputados nesta rodada ainda

### Orientações para Implementação
- Endpoint único para status agregado da rodada (ex.: `/organizador/rodada-atual/status`)
- Registrar evento de analytics: `view_organizer_panel`
- Garantir carregamento rápido mesmo com múltiplos torneios ativos por organizador
- Id do passo a que corresponde a história: 1.1

---

# Conferir súmulas recebidas dos árbitros

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Conferir súmulas recebidas dos árbitros

## Geral
- **Produto:** Torneioz
- **Título:** Conferir súmulas recebidas dos árbitros
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero ver a lista de partidas da rodada com o status de envio da súmula de cada uma,
Para não precisar cobrar individualmente cada árbitro perguntando se já mandou o registro.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** organizador, sumula-digital

## Detalhes

### Descrição Detalhada
Esta história entrega a listagem de súmulas de uma rodada, permitindo ao organizador identificar de forma objetiva quais partidas já têm súmula enviada pelo árbitro e quais ainda estão pendentes. É a peça que elimina a necessidade de mensagens avulsas de cobrança no WhatsApp, centralizando a visibilidade do fluxo de homologação em um único lugar.

### Orientações de Tela
- Lista de partidas da rodada com colunas: Times, Horário, Status da Súmula
- Status possíveis: "Aguardando árbitro", "Enviada — aguardando homologação", "Homologada"
- Filtro por status para localizar rapidamente pendências
- Toque/clique em uma partida abre o detalhe da súmula enviada

### Regras de Negócio
- Uma partida só muda para "Enviada" quando o árbitro finaliza e sincroniza a súmula no módulo mobile
- Partidas sem súmula enviada 24h após o horário previsto do jogo recebem destaque visual de atenção
- O organizador não pode homologar uma súmula que ainda não foi enviada pelo árbitro

## BDD & Implementação

### Critérios de Aceitação (BDD)

Listagem com súmulas mistas
Dado que a rodada tem partidas com súmula enviada e partidas sem súmula
Quando eu acesso a Lista de Súmulas da Rodada
Então o sistema deve exibir cada partida com seu status correto e permitir filtrar por status

Partida atrasada sem súmula
Dado que uma partida terminou há mais de 24 horas e a súmula ainda não foi enviada
Quando eu visualizo a Lista de Súmulas da Rodada
Então o sistema deve destacar essa partida visualmente como pendente de atenção

### Orientações para Implementação
- Consulta paginada por rodada para suportar torneios com muitos jogos simultâneos
- Registrar evento de analytics: `view_sumula_list`
- Job assíncrono para calcular destaque de "atraso" sem sobrecarregar a consulta principal
- Id do passo a que corresponde a história: 1.2

---

# Homologar a súmula de uma partida

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Homologar a súmula de uma partida

## Geral
- **Produto:** Torneioz
- **Título:** Homologar a súmula de uma partida
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero revisar e confirmar a súmula enviada pelo árbitro de uma partida,
Para garantir que os dados usados no cálculo da tabela e das suspensões estejam corretos antes de virarem oficiais.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** organizador, sumula-digital, homologacao

## Detalhes

### Descrição Detalhada
Esta história cobre o momento em que o organizador revisa os eventos registrados pelo árbitro (gols, cartões, substituições) antes de confirmá-los como dado oficial da competição. A homologação é o ponto de controle que dá ao organizador segurança de que erros pontuais do árbitro em campo podem ser corrigidos antes de impactar a tabela e o histórico de suspensões, evitando contestação pública dos times.

### Orientações de Tela
- Tela de detalhe da súmula com lista de eventos (gol, cartão amarelo/vermelho, substituição) por atleta
- Botão "Homologar" habilitado somente após revisão completa
- Opção "Solicitar correção" que devolve a súmula ao árbitro com um campo de observação
- Indicação clara de que a homologação é irreversível sem gerar um registro de auditoria

### Regras de Negócio
- Uma súmula homologada dispara automaticamente o recálculo de tabela e suspensões
- Uma vez homologada, qualquer alteração exige um fluxo de correção auditável (não edição livre)
- Súmulas com eventos inconsistentes (ex.: mais cartões vermelhos que atletas em campo) geram alerta antes da homologação

## BDD & Implementação

### Critérios de Aceitação (BDD)

Homologação sem inconsistências
Dado que a súmula de uma partida foi enviada pelo árbitro sem inconsistências
Quando o organizador clica em "Homologar"
Então o sistema deve marcar a súmula como homologada e disparar o recálculo de tabela e suspensões

Solicitação de correção
Dado que o organizador identifica um erro na súmula enviada
Quando ele seleciona "Solicitar correção" e descreve o problema
Então o sistema deve devolver a súmula ao árbitro com o status "Correção solicitada" e a observação registrada

### Orientações para Implementação
- Homologação deve ser transacional: súmula homologada + recálculo de tabela ocorrem na mesma operação
- Registrar evento de analytics: `homologar_sumula`
- Manter log de auditoria de toda correção pós-homologação
- Id do passo a que corresponde a história: 1.3

---

# Ver a tabela de classificação atualizar automaticamente

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Ver a tabela de classificação atualizar automaticamente

## Geral
- **Produto:** Torneioz
- **Título:** Ver a tabela de classificação atualizar automaticamente
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero que a tabela de classificação recalcule sozinha após a homologação dos resultados,
Para nunca mais precisar somar pontos e saldo de gols manualmente numa planilha.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** organizador, motor-de-regras, tabela

## Detalhes

### Descrição Detalhada
Esta história entrega o núcleo do motor de regras do produto: o recálculo automático da tabela de classificação com base nos critérios parametrizados (pontos por vitória/empate, saldo de gols, confronto direto). É a funcionalidade que resolve a dor mais citada nas entrevistas — o risco de erro manual de cálculo que gera contestação pública dos times.

### Orientações de Tela
- Tela: Tabela de Classificação, com colunas de pontos, jogos, vitórias, empates, derrotas, gols pró/contra, saldo de gols
- Indicador visual de "atualizado agora" logo após um recálculo
- Ordenação automática conforme os critérios de desempate configurados na liga
- Link direto para o histórico de rodadas que compõem a posição atual de cada time

### Regras de Negócio
- O recálculo deve ser disparado automaticamente sempre que um resultado for homologado
- Os critérios de desempate seguem exatamente a ordem configurada no regulamento da competição (item já definido na Configuração de Liga)
- Times com jogos pendentes de homologação aparecem com um indicador de "posição sujeita a alteração"

## BDD & Implementação

### Critérios de Aceitação (BDD)

Recálculo após homologação
Dado que um resultado acabou de ser homologado
Quando o sistema processa a homologação
Então a tabela de classificação deve refletir o novo resultado sem necessidade de ação manual do organizador

Empate técnico entre dois times
Dado que dois times estão empatados em pontos após uma rodada
Quando a tabela é recalculada
Então o sistema deve aplicar os critérios de desempate configurados, na ordem definida, para posicioná-los corretamente

### Orientações para Implementação
- Motor de regras deve ser desacoplado (parametrizável), não hardcoded por esporte
- Registrar evento de analytics: `tabela_recalculada`
- Cobertura de testes automatizados para os principais cenários de desempate
- Id do passo a que corresponde a história: 1.4

---

# Conferir lista de suspensos gerada automaticamente

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Conferir lista de suspensos gerada automaticamente

## Geral
- **Produto:** Torneioz
- **Título:** Conferir lista de suspensos gerada automaticamente
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero que a lista de atletas suspensos seja calculada automaticamente a partir dos cartões homologados,
Para eliminar o retrabalho de somar cartões manualmente e o risco de deixar um atleta irregular entrar em campo.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** organizador, suspensao-automatica

## Detalhes

### Descrição Detalhada
Esta história implementa o algoritmo de suspensão disciplinar configurável (ex.: suspende após 3 cartões amarelos acumulados ou 1 cartão vermelho direto), disparado automaticamente a cada súmula homologada. Foi apontada nas entrevistas como o problema que, se resolvido, sozinho já justificaria a adoção da plataforma pelo organizador.

### Orientações de Tela
- Tela: Lista de Suspensos, agrupada por time
- Indicação do motivo da suspensão (quantidade de cartões acumulados ou expulsão direta)
- Indicação de quantas rodadas de suspensão restam para cada atleta
- Alerta destacado quando um atleta suspenso aparece escalado em uma súmula futura

### Regras de Negócio
- A regra de suspensão (nº de cartões, nº de rodadas de gancho) é parametrizável por liga/torneio
- A suspensão só é aplicada após a homologação da súmula que gerou o cartão decisivo
- Um atleta suspenso deve ser sinalizado automaticamente se aparecer na escalação de uma súmula futura

## BDD & Implementação

### Critérios de Aceitação (BDD)

Atleta atinge o limite de cartões
Dado que um atleta acumula o número de cartões amarelos configurado como limite após a homologação de uma súmula
Quando o sistema processa essa homologação
Então o atleta deve aparecer na Lista de Suspensos com o motivo e a quantidade de rodadas de gancho

Atleta suspenso escalado por engano
Dado que um atleta está suspenso e um árbitro tenta registrá-lo na escalação de uma nova súmula
Quando a súmula é submetida
Então o sistema deve exibir um alerta ao organizador durante a homologação

### Orientações para Implementação
- Regra de suspensão deve ser configurável via parâmetros da liga, não fixa em código
- Registrar evento de analytics: `atleta_suspenso_gerado`
- Processamento do cálculo de suspensão deve ocorrer na mesma transação da homologação da súmula
- Id do passo a que corresponde a história: 1.5

---

# Compartilhar o link público atualizado com os times

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Marcos Vinícius, o organizador — Homologar súmulas e ver a tabela atualizar automaticamente
- **Passo:** Compartilhar o link público atualizado com os times

## Geral
- **Produto:** Torneioz
- **Título:** Compartilhar o link público atualizado com os times
- **Narrativa:**
Como organizador de liga/campeonato,
Eu quero um único link público sempre atualizado com tabela, resultados e horários,
Para parar de responder repetidamente às mesmas perguntas de times e torcedores no WhatsApp.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** organizador, pagina-publica

## Detalhes

### Descrição Detalhada
Esta história entrega a página pública indexável da competição (PWA), contendo classificação, calendário e horários da rodada, acessível por qualquer pessoa via link, sem necessidade de login. É o artefato que substitui as fotos de tabela postadas manualmente em grupos e stories.

### Orientações de Tela
- URL curta e memorável por torneio (ex.: torneioz.app/liga-do-bairro)
- Página com abas: Classificação, Calendário, Times
- Botão de compartilhamento nativo (WhatsApp, Instagram, copiar link)
- Layout responsivo mobile-first, sem exigir download de aplicativo

### Regras de Negócio
- A página pública reflete os dados assim que uma homologação altera tabela ou calendário, sem necessidade de publicação manual
- O link é gerado automaticamente na criação do torneio, antes mesmo da primeira rodada
- Times sem confrontos definidos ainda aparecem na listagem, sinalizados como "calendário em definição"

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso sem login
Dado que uma pessoa recebe o link público do torneio
Quando ela abre o link em qualquer navegador móvel
Então o sistema deve exibir a classificação e o calendário atualizados sem exigir cadastro

Atualização refletida automaticamente
Dado que uma súmula acabou de ser homologada, alterando a tabela
Quando um visitante acessa a página pública logo em seguida
Então a tabela exibida deve já refletir o novo resultado

### Orientações para Implementação
- Página pública servida como PWA cacheável, com invalidação de cache no evento de homologação
- Registrar evento de analytics: `view_public_page` e `share_public_link`
- Garantir SEO básico para indexação em buscadores (nome da liga, cidade)
- Id do passo a que corresponde a história: 1.6
