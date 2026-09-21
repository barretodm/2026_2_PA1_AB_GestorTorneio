# Histórias de Usuário — Administrador de Time (Capitão/Técnico)

**Produto:** Torneioz
**Persona:** Diego Andrade, o capitão que virou gestor sem querer
**Jornada de referência:** Saber quem está apto para escalar antes do próximo jogo, sem depender de anotações próprias

---

# Abrir o painel do time antes do treino ou jogo

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Abrir o app antes do treino/jogo para conferir o time

## Geral
- **Produto:** Torneioz
- **Título:** Abrir o painel do time antes do treino ou jogo
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero abrir um painel único com as informações do meu time,
Para não precisar catar informação espalhada em conversas de WhatsApp antes de decidir a escalação.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, painel-do-time

## Detalhes

### Descrição Detalhada
Esta história entrega o ponto de entrada do capitão/técnico na plataforma: um painel simples e rápido de carregar, mostrando as informações mais relevantes do time no momento — próximo jogo, elenco cadastrado e um atalho para a situação disciplinar. Prioriza velocidade, já que o administrador de time normalmente acessa isso com pouco tempo disponível, nos minutos antes de um treino ou jogo.

### Orientações de Tela
- Título: "Painel do Time [Nome do Time]"
- Bloco de destaque: próximo jogo (adversário, data, horário, local)
- Atalho para "Situação Disciplinar do Elenco"
- Lista resumida do elenco cadastrado com contagem de atletas ativos

### Regras de Negócio
- O painel é acessível apenas pelo capitão/técnico vinculado ao time (papel definido no módulo de autenticação)
- Caso o time não tenha elenco cadastrado, o painel deve orientar o cadastro antes de qualquer outra ação
- O próximo jogo exibido é sempre o mais próximo no calendário confirmado

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso com elenco cadastrado
Dado que o time já possui elenco cadastrado e um próximo jogo confirmado
Quando o capitão acessa o Painel do Time
Então o sistema deve exibir o próximo jogo e o resumo do elenco

Acesso sem elenco cadastrado
Dado que o time ainda não possui nenhum atleta cadastrado
Quando o capitão acessa o Painel do Time
Então o sistema deve exibir uma chamada destacada para iniciar o cadastro do elenco

### Orientações para Implementação
- Restringir o acesso ao painel pelo papel "capitão/técnico" vinculado ao time no módulo de Autenticação & Papéis
- Registrar evento de analytics: `view_team_panel`
- Id do passo a que corresponde a história: 3.1

---

# Consultar a lista de atletas suspensos ou pendurados

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Consultar a lista de atletas suspensos ou pendurados

## Geral
- **Produto:** Torneioz
- **Título:** Consultar a lista de atletas suspensos ou pendurados
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero ver claramente quais atletas estão suspensos ou pendurados por cartões,
Para não escalar por engano um jogador irregular e perder pontos por isso.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, suspensao-automatica

## Detalhes

### Descrição Detalhada
Esta história entrega, do lado do time, a visualização da situação disciplinar calculada automaticamente pelo motor de suspensões (já homologado pelo organizador). É a resposta direta à dor mais citada por capitães: descobrir tarde demais que um atleta estava impedido de jogar.

### Orientações de Tela
- Tela: Situação Disciplinar do Elenco
- Lista de atletas com status: Apto / Pendurado (a X cartões da suspensão) / Suspenso (faltam Y rodadas)
- Ordenação com atletas suspensos ou pendurados no topo da lista
- Detalhe do histórico de cartões de cada atleta ao tocar/clicar

### Regras de Negócio
- O status exibido reflete apenas súmulas já homologadas pelo organizador
- Um atleta "pendurado" é aquele a um cartão de distância da suspensão, conforme regra da liga
- A lista deve atualizar automaticamente assim que uma nova homologação alterar a situação de algum atleta

## BDD & Implementação

### Critérios de Aceitação (BDD)

Atleta suspenso aparece destacado
Dado que um atleta do time está suspenso após a homologação da última rodada
Quando o capitão acessa a Situação Disciplinar do Elenco
Então esse atleta deve aparecer destacado no topo com o motivo e as rodadas restantes de suspensão

Nenhum atleta em risco
Dado que nenhum atleta do time está suspenso ou pendurado
Quando o capitão acessa a tela
Então o sistema deve indicar claramente que todo o elenco está apto

### Orientações para Implementação
- Consumir o mesmo dado de suspensão calculado na história 1.5 (fonte única de verdade)
- Registrar evento de analytics: `view_team_disciplinary_status`
- Id do passo a que corresponde a história: 3.2

---

# Conferir o próximo jogo do time

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Conferir o próximo jogo (data, horário, local)

## Geral
- **Produto:** Torneioz
- **Título:** Conferir o próximo jogo do time
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero ver claramente data, horário e local do próximo confronto do meu time,
Para poder avisar o grupo sem precisar confirmar essa informação com o organizador.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, calendario

## Detalhes

### Descrição Detalhada
Esta história reaproveita o calendário gerado automaticamente pelo motor de tabela e confrontos (Fase 1), apresentando-o de forma filtrada e simplificada sob a ótica de um único time, para que o capitão não precise navegar pelo calendário completo do campeonato.

### Orientações de Tela
- Bloco "Próximo Jogo" no Painel do Time: adversário, data, horário, local
- Lista secundária com os próximos 2-3 jogos seguintes, para planejamento antecipado
- Indicação se o horário/local ainda está sujeito a confirmação

### Regras de Negócio
- O próximo jogo exibido é sempre o mais próximo cronologicamente com status "confirmado"
- Alterações de horário/local feitas pelo organizador devem refletir aqui imediatamente

## BDD & Implementação

### Critérios de Aceitação (BDD)

Próximo jogo confirmado
Dado que o calendário já definiu data, horário e local do próximo confronto do time
Quando o capitão consulta o Painel do Time
Então essas informações devem aparecer em destaque, sem necessidade de navegação adicional

### Orientações para Implementação
- Reaproveitar o mesmo serviço de calendário usado na página pública (história 1.6), filtrado por time
- Id do passo a que corresponde a história: 3.3

---

# Avisar o grupo do time pelo canal oficial

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Avisar o grupo do time pelo canal oficial

## Geral
- **Produto:** Torneioz
- **Título:** Avisar o grupo do time pelo canal oficial
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero compartilhar rapidamente a informação de escalação e do próximo jogo direto da plataforma,
Para não precisar digitar tudo de novo manualmente no grupo de WhatsApp do time.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, painel-do-capitao, comunicacao

## Detalhes

### Descrição Detalhada
Esta história faz parte do Painel do Capitão (entrega prevista na Fase 2) e permite gerar, a partir dos dados já existentes na plataforma (próximo jogo, situação disciplinar), uma mensagem pronta para ser compartilhada no canal que o time já usa no dia a dia (WhatsApp), evitando digitação manual repetida.

### Orientações de Tela
- Botão "Compartilhar com o time" no Painel do Time
- Prévia da mensagem gerada automaticamente (jogo, horário, local, atletas suspensos)
- Opção de editar a mensagem antes de enviar
- Integração com o compartilhamento nativo do celular (abre o WhatsApp com o texto pronto)

### Regras de Negócio
- A mensagem gerada deve sempre incluir avisos de suspensão, se houver algum atleta impedido
- O envio em si ocorre fora da plataforma (WhatsApp), a plataforma apenas prepara o conteúdo

## BDD & Implementação

### Critérios de Aceitação (BDD)

Geração de mensagem com atleta suspenso
Dado que há um atleta suspenso no elenco e um próximo jogo confirmado
Quando o capitão toca em "Compartilhar com o time"
Então a mensagem gerada deve incluir o aviso de suspensão desse atleta junto com os dados do jogo

### Orientações para Implementação
- Usar a API de compartilhamento nativo do sistema operacional (Web Share API) para abrir o WhatsApp com o texto pré-preenchido
- Registrar evento de analytics: `share_team_update`
- Id do passo a que corresponde a história: 3.4

---

# Conferir a súmula do jogo depois de encerrado

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Conferir súmula do jogo depois de encerrado

## Geral
- **Produto:** Torneioz
- **Título:** Conferir a súmula do jogo depois de encerrado
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero revisar a súmula oficial de uma partida do meu time,
Para conferir se gols e cartões foram atribuídos corretamente e evitar dúvidas depois.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, sumula-digital

## Detalhes

### Descrição Detalhada
Esta história dá visibilidade, do lado do time, à súmula já homologada pelo organizador — a mesma fonte de dado usada para tabela e suspensões. Reduz o número de discussões pós-jogo ao tornar o registro de eventos consultável por qualquer responsável do time.

### Orientações de Tela
- Tela: Súmula da Partida (visualização, sem edição)
- Linha do tempo com gols, cartões e substituições, por atleta e minuto (quando disponível)
- Indicação clara do status: "Homologada pelo organizador"

### Regras de Negócio
- A súmula só fica visível para os times após a homologação pelo organizador
- Times não podem editar a súmula, apenas visualizar (eventual contestação segue fluxo separado, fora do escopo desta história)

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta de súmula homologada
Dado que a súmula de uma partida do time já foi homologada
Quando o capitão acessa a tela da partida
Então o sistema deve exibir a linha do tempo completa de eventos da súmula

### Orientações para Implementação
- Reaproveitar o mesmo dado estruturado da súmula homologada (história 1.3), em modo somente leitura
- Id do passo a que corresponde a história: 3.5

---

# Verificar a posição atualizada na tabela

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Diego Andrade, o capitão — Saber quem está apto para escalar
- **Passo:** Verificar a posição atualizada na tabela

## Geral
- **Produto:** Torneioz
- **Título:** Verificar a posição atualizada na tabela
- **Narrativa:**
Como administrador de time (capitão/técnico),
Eu quero ver a colocação do meu time na tabela logo após a rodada,
Para saber onde estamos sem precisar perguntar diretamente ao organizador.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** administrador-time, tabela

## Detalhes

### Descrição Detalhada
Esta história reaproveita a tabela de classificação já entregue na Fase 1, com destaque visual para a linha do próprio time, facilitando a leitura rápida pelo capitão sem precisar procurar entre todos os times da competição.

### Orientações de Tela
- Reaproveita a Tela: Tabela de Classificação, com a linha do time do usuário destacada visualmente
- Atalho rápido a partir do Painel do Time

### Regras de Negócio
- O destaque do time segue a mesma lógica de atualização automática da tabela (história 1.4)

## BDD & Implementação

### Critérios de Aceitação (BDD)

Time destacado na tabela
Dado que o capitão está autenticado e vinculado a um time participante
Quando ele acessa a Tabela de Classificação a partir do Painel do Time
Então a linha correspondente ao seu time deve aparecer visualmente destacada

### Orientações para Implementação
- Nenhuma nova fonte de dado — reaproveita a história 1.4, com um parâmetro de destaque visual por time
- Id do passo a que corresponde a história: 3.6
