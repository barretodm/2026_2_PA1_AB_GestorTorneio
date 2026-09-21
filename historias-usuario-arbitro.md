# Histórias de Usuário — Árbitros da Competição

**Produto:** Torneioz
**Persona:** Josué Almeida, o árbitro que já apitou de tudo
**Jornada de referência:** Registrar a súmula digital de uma partida em campo, do início ao envio para homologação

---

# Acessar o módulo de súmula antes do início da partida

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Josué Almeida, o árbitro — Registrar a súmula digital de uma partida
- **Passo:** Acessar o módulo de súmula antes do início da partida

## Geral
- **Produto:** Torneioz
- **Título:** Acessar o módulo de súmula antes do início da partida
- **Narrativa:**
Como árbitro da competição,
Eu quero abrir a súmula digital da partida antes do apito inicial,
Para já conferir a escalação das duas equipes sem depender de papel.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** arbitro, sumula-digital, offline-first

## Detalhes

### Descrição Detalhada
Esta história cobre o momento pré-jogo do árbitro em campo: abrir o módulo mobile de súmula digital para a partida do dia e visualizar a escalação inicial enviada pelos times. O módulo precisa funcionar de forma ágil mesmo com conectividade instável, característica do ambiente de campo aberto.

### Orientações de Tela
- Tela: Súmula Digital (Pré-jogo)
- Lista de partidas do árbitro no dia, com a partida do momento em destaque
- Escalação inicial e reservas de cada equipe, com numeração e foto (quando disponível)
- Indicador de status de sincronização (online/offline)

### Regras de Negócio
- O módulo deve carregar os dados da partida com antecedência (cache local) para funcionar mesmo sem sinal no momento do jogo
- A escalação exibida é a última enviada pelas comissões técnicas antes do fechamento do prazo pré-jogo

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso com conectividade normal
Dado que o árbitro está autenticado e a partida do dia está disponível
Quando ele abre o módulo de Súmula Digital
Então o sistema deve exibir a escalação inicial de ambas as equipes

Acesso sem conexão de internet em campo
Dado que os dados da partida já foram sincronizados previamente no aparelho
Quando o árbitro abre o módulo sem conexão de internet
Então o sistema deve exibir os dados em cache normalmente, sem bloquear o uso

### Orientações para Implementação
- Arquitetura offline-first com sincronização em segundo plano assim que houver conexão
- Registrar evento de analytics: `open_digital_sumula` (registrado localmente e sincronizado depois, se necessário)
- Id do passo a que corresponde a história: 5.1

---

# Registrar gols e cartões durante a partida

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Josué Almeida, o árbitro — Registrar a súmula digital de uma partida
- **Passo:** Registrar gols e cartões durante a partida

## Geral
- **Produto:** Torneioz
- **Título:** Registrar gols e cartões durante a partida
- **Narrativa:**
Como árbitro da competição,
Eu quero registrar gols, cartões e substituições direto na tela do celular durante o jogo,
Para não depender de papel e caneta vulneráveis a rasura, chuva ou vento.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** arbitro, sumula-digital

## Detalhes

### Descrição Detalhada
Esta história entrega a interface principal de registro de eventos da partida, com interação otimizada para uso rápido em campo (poucos toques, botões grandes), permitindo ao árbitro marcar gol, cartão amarelo/vermelho e substituição no momento em que ocorrem, sem interromper a condução do jogo por muito tempo.

### Orientações de Tela
- Tela: Registro de Eventos da Partida
- Botões grandes por tipo de evento (Gol, Cartão Amarelo, Cartão Vermelho, Substituição)
- Seleção rápida do atleta envolvido a partir da lista de escalação já carregada
- Linha do tempo dos eventos já registrados na partida, com opção de desfazer o último lançamento

### Regras de Negócio
- Todo evento é vinculado a um atleta cadastrado na escalação da partida
- Um evento pode ser desfeito apenas enquanto a súmula não foi finalizada e enviada
- O sistema deve salvar os eventos localmente à medida que são registrados, mesmo sem conexão

## BDD & Implementação

### Critérios de Aceitação (BDD)

Registro de cartão durante o jogo
Dado que a partida está em andamento e o árbitro decide aplicar um cartão amarelo
Quando ele seleciona o atleta e o tipo de evento "Cartão Amarelo"
Então o sistema deve adicionar esse evento à linha do tempo da partida imediatamente

Registro sem conexão de internet
Dado que o árbitro está em campo sem sinal de internet
Quando ele registra um gol
Então o sistema deve salvar o evento localmente e sincronizar automaticamente assim que a conexão for restabelecida

### Orientações para Implementação
- Persistência local (ex.: IndexedDB/SQLite local) com fila de sincronização
- Registrar evento de analytics: `sumula_event_added` (sincronizado quando houver conexão)
- Id do passo a que corresponde a história: 5.2

---

# Consultar a numeração dos atletas em caso de dúvida

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Josué Almeida, o árbitro — Registrar a súmula digital de uma partida
- **Passo:** Consultar a numeração dos atletas em caso de dúvida

## Geral
- **Produto:** Torneioz
- **Título:** Consultar a numeração dos atletas em caso de dúvida
- **Narrativa:**
Como árbitro da competição,
Eu quero consultar rapidamente a numeração e identificação oficial de um atleta,
Para não errar quem fez o gol ou recebeu o cartão na hora de registrar.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** arbitro, sumula-digital

## Detalhes

### Descrição Detalhada
Esta história dá suporte à história 5.2, oferecendo uma consulta rápida à lista completa de atletas de cada equipe (número, nome, foto quando disponível) sem sair da tela de registro de eventos, reduzindo o risco de atribuição incorreta de um evento.

### Orientações de Tela
- Modal/painel deslizante: Lista de Atletas por Equipe, acessível a partir da tela de registro de eventos
- Busca rápida por número da camisa
- Foto do atleta, quando cadastrada, para conferência visual

### Regras de Negócio
- A lista reflete a escalação confirmada da partida, não o elenco completo do time
- Sempre acessível mesmo offline, pois os dados já foram carregados na história 5.1

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta durante o registro de um evento
Dado que o árbitro está registrando um evento e tem dúvida sobre o número de um atleta
Quando ele abre a Lista de Atletas por Equipe
Então o sistema deve exibir a numeração e o nome de todos os atletas escalados daquela equipe

### Orientações para Implementação
- Reaproveitar os dados de escalação já carregados na história 5.1, sem nova chamada de rede
- Id do passo a que corresponde a história: 5.3

---

# Finalizar e enviar a súmula ao apito final

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Josué Almeida, o árbitro — Registrar a súmula digital de uma partida
- **Passo:** Finalizar e enviar a súmula ao apito final

## Geral
- **Produto:** Torneioz
- **Título:** Finalizar e enviar a súmula ao apito final
- **Narrativa:**
Como árbitro da competição,
Eu quero finalizar e enviar a súmula assim que a partida termina,
Para encerrar meu trabalho administrativo ali mesmo, sem levar papel pra casa ou tirar foto de nada depois.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** arbitro, sumula-digital

## Detalhes

### Descrição Detalhada
Esta história cobre o encerramento do fluxo de súmula: uma revisão final dos eventos registrados, seguida do envio para homologação do organizador (história 1.3). É o ponto de handoff entre o trabalho do árbitro em campo e o trabalho do organizador na plataforma.

### Orientações de Tela
- Tela: Resumo Final da Súmula, com todos os eventos registrados na partida
- Botão "Finalizar e Enviar", com confirmação antes do envio definitivo
- Mensagem de sucesso clara após o envio

### Regras de Negócio
- Após o envio, a súmula não pode mais ser editada diretamente pelo árbitro (qualquer ajuste passa pelo fluxo de correção solicitado pelo organizador, história 1.3)
- Se não houver conexão no momento do envio, a súmula fica na fila de sincronização e é enviada automaticamente assim que possível

## BDD & Implementação

### Critérios de Aceitação (BDD)

Envio com conexão disponível
Dado que o árbitro revisou os eventos e confirma a finalização da súmula
Quando ele toca em "Finalizar e Enviar" com internet disponível
Então o sistema deve enviar a súmula imediatamente e marcá-la como "Enviada — aguardando homologação"

Finalização sem conexão disponível
Dado que o árbitro finaliza a súmula sem conexão de internet no momento
Quando ele confirma o envio
Então o sistema deve manter a súmula na fila local e sincronizar automaticamente assim que a conexão for restabelecida

### Orientações para Implementação
- Fila de sincronização com retry automático em background
- Registrar evento de analytics: `sumula_finalizada`
- Id do passo a que corresponde a história: 5.4

---

# Conferir a confirmação de recebimento pelo organizador

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Josué Almeida, o árbitro — Registrar a súmula digital de uma partida
- **Passo:** Conferir a confirmação de recebimento pelo organizador

## Geral
- **Produto:** Torneioz
- **Título:** Conferir a confirmação de recebimento pelo organizador
- **Narrativa:**
Como árbitro da competição,
Eu quero ver quando o organizador recebe e processa a súmula que enviei,
Para ter a segurança de que não vou ser cobrado depois por algo que já mandei certo.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** arbitro, sumula-digital, homologacao

## Detalhes

### Descrição Detalhada
Esta história fecha o ciclo de confiança do árbitro no processo digital, exibindo o status da súmula após o envio (Enviada → Homologada, ou Correção solicitada, quando aplicável), sem que o árbitro precise perguntar diretamente ao organizador se está tudo certo.

### Orientações de Tela
- Tela: Status de Homologação, acessível a partir do histórico de partidas do árbitro
- Estados exibidos: "Enviada — aguardando homologação", "Homologada", "Correção solicitada" (com o motivo, se houver)
- Notificação simples quando o status mudar

### Regras de Negócio
- O status reflete diretamente as ações do organizador na história 1.3 (mesma fonte de dado)
- Em caso de "Correção solicitada", o árbitro deve conseguir reabrir a súmula específica para ajuste

## BDD & Implementação

### Critérios de Aceitação (BDD)

Súmula homologada sem ressalvas
Dado que o organizador homologou a súmula enviada
Quando o árbitro consulta o status dessa partida
Então o sistema deve exibir "Homologada"

Súmula com correção solicitada
Dado que o organizador solicitou correção na súmula enviada
Quando o árbitro consulta o status dessa partida
Então o sistema deve exibir "Correção solicitada" junto com o motivo e permitir reabrir o registro para ajuste

### Orientações para Implementação
- Reaproveitar o mesmo dado de status gerado na história 1.3, consumido do lado do árbitro
- Notificação push opcional quando o status mudar (dependendo da disponibilidade de infraestrutura de push na Fase 2)
- Id do passo a que corresponde a história: 5.5
