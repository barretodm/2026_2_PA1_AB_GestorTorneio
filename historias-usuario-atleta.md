# Histórias de Usuário — Atletas Amadores

**Produto:** Torneioz
**Persona:** Ícaro Rocha, o atacante que quer saber se pode jogar
**Jornada de referência:** Verificar a própria situação de suspensão e acompanhar o desempenho pessoal na competição

---

# Abrir o perfil pessoal no celular antes do jogo

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Ícaro Rocha, o atleta — Verificar a própria situação de suspensão
- **Passo:** Abrir o perfil pessoal no celular antes do jogo

## Geral
- **Produto:** Torneioz
- **Título:** Abrir o perfil pessoal no celular antes do jogo
- **Narrativa:**
Como atleta amador,
Eu quero acessar meu próprio perfil na competição,
Para consultar minha situação sem precisar perguntar ao capitão ou técnico.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** atleta, perfil-do-atleta

## Detalhes

### Descrição Detalhada
Esta história entrega o perfil digital individual do atleta, ponto de entrada para todas as consultas pessoais (situação disciplinar, estatísticas, próximos jogos). É a peça que elimina a dependência de repasses informais do capitão, apontada como uma das dores mais recorrentes nas entrevistas com atletas.

### Orientações de Tela
- Título: "Meu Perfil"
- Foto/avatar, nome, time atual
- Blocos de atalho: Situação Disciplinar, Estatísticas, Próximos Jogos
- Link de acesso simplificado (sem exigir senha complexa, dado o perfil de baixa paciência do público)

### Regras de Negócio
- O perfil só é criado quando o atleta é cadastrado no elenco de um time pelo administrador do time
- O acesso pode ocorrer via convite/link enviado pelo time, sem exigir processo de cadastro longo

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso ao perfil já vinculado a um time
Dado que o atleta já foi cadastrado no elenco de um time
Quando ele acessa seu perfil pela primeira vez usando o link de convite
Então o sistema deve exibir seus dados básicos e os atalhos para situação disciplinar e estatísticas

### Orientações para Implementação
- Priorizar fluxo de acesso simplificado (baixo atrito), já que o público tem baixa paciência para cadastro
- Registrar evento de analytics: `view_athlete_profile`
- Id do passo a que corresponde a história: 4.1

---

# Consultar cartões acumulados e status de suspensão

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 2 – Automação de Campo (Súmula Digital e Suspensões)
- **Jornada de Usuário:** Ícaro Rocha, o atleta — Verificar a própria situação de suspensão
- **Passo:** Consultar cartões acumulados e status de suspensão

## Geral
- **Produto:** Torneioz
- **Título:** Consultar cartões acumulados e status de suspensão
- **Narrativa:**
Como atleta amador,
Eu quero ver quantos cartões tenho acumulados e se estou apto para o próximo jogo,
Para não ser pego de surpresa por uma suspensão que eu não sabia que existia.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 2 - Planejado
- **Estimativa (pontos):** —
- **Tags:** atleta, suspensao-automatica

## Detalhes

### Descrição Detalhada
Esta história expõe ao próprio atleta o mesmo dado de suspensão já calculado automaticamente para o organizador (história 1.5) e para o capitão (história 3.2), fechando o ciclo de transparência disciplinar diretamente para quem mais precisa dessa informação: o jogador.

### Orientações de Tela
- Tela: Situação Disciplinar (Atleta)
- Status em destaque: Apto / Pendurado / Suspenso, com motivo e rodadas restantes quando aplicável
- Histórico de cartões recebidos na temporada, com data e adversário

### Regras de Negócio
- O status exibido reflete apenas súmulas já homologadas pelo organizador
- Não há diferença de regra entre o que o atleta vê e o que o capitão vê — é a mesma fonte de verdade

## BDD & Implementação

### Critérios de Aceitação (BDD)

Atleta suspenso consulta o próprio status
Dado que o atleta está suspenso após a última rodada homologada
Quando ele acessa a Situação Disciplinar no próprio perfil
Então o sistema deve exibir claramente o status "Suspenso", o motivo e quantas rodadas faltam

### Orientações para Implementação
- Reaproveitar o mesmo endpoint de status disciplinar usado nas histórias 1.5 e 3.2, filtrado pelo próprio atleta autenticado
- Id do passo a que corresponde a história: 4.2

---

# Ver próximos jogos e horário de convocação

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Ícaro Rocha, o atleta — Verificar a própria situação de suspensão
- **Passo:** Ver próximos jogos e horário de convocação

## Geral
- **Produto:** Torneioz
- **Título:** Ver próximos jogos e horário de convocação
- **Narrativa:**
Como atleta amador,
Eu quero ver quando e onde é o próximo jogo do meu time,
Para saber se vou conseguir chegar a tempo, sem depender de aviso informal.
- **Prioridade:** Baixa
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** atleta, calendario

## Detalhes

### Descrição Detalhada
Esta história reaproveita o calendário do time (já usado na história 3.3 do capitão) sob a ótica individual do atleta, exibido dentro do próprio perfil.

### Orientações de Tela
- Bloco "Próximo Jogo" no Perfil do Atleta: adversário, data, horário, local

### Regras de Negócio
- Reflete o mesmo calendário do time ao qual o atleta está vinculado

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta de próximo jogo pelo atleta
Dado que o time do atleta tem um próximo jogo confirmado no calendário
Quando o atleta acessa seu perfil
Então o sistema deve exibir data, horário e local desse jogo

### Orientações para Implementação
- Reaproveitar o mesmo serviço de calendário da história 3.3, filtrado pelo atleta autenticado
- Id do passo a que corresponde a história: 4.3

---

# Consultar histórico de gols e estatísticas pessoais

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Ícaro Rocha, o atleta — Verificar a própria situação de suspensão
- **Passo:** Consultar histórico de gols e estatísticas pessoais

## Geral
- **Produto:** Torneioz
- **Título:** Consultar histórico de gols e estatísticas pessoais
- **Narrativa:**
Como atleta amador,
Eu quero ver meu histórico de gols e jogos disputados na temporada,
Para ter meu desempenho registrado oficialmente, e não depender de memória ou fotos soltas.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** atleta, estatisticas

## Detalhes

### Descrição Detalhada
Esta história constrói o histórico estatístico individual do atleta a partir dos eventos já registrados nas súmulas homologadas, consolidando gols, jogos disputados e cartões ao longo da temporada em uma única tela de fácil leitura.

### Orientações de Tela
- Tela: Estatísticas do Atleta
- Indicadores: gols marcados, jogos disputados, cartões recebidos na temporada
- Lista de partidas com participação e eventos individuais (gol, cartão) em cada uma

### Regras de Negócio
- As estatísticas são recalculadas a cada nova súmula homologada envolvendo o atleta
- Estatísticas de temporadas anteriores, quando existirem, ficam disponíveis separadamente por temporada

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta após gol registrado
Dado que o atleta marcou um gol em uma súmula já homologada
Quando ele acessa suas Estatísticas
Então o contador de gols da temporada deve refletir esse gol

### Orientações para Implementação
- Recalcular estatísticas de forma incremental a cada homologação, evitando reprocessar toda a temporada
- Registrar evento de analytics: `view_athlete_stats`
- Id do passo a que corresponde a história: 4.4

---

# Compartilhar destaque pessoal nas redes sociais

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Ícaro Rocha, o atleta — Verificar a própria situação de suspensão
- **Passo:** Compartilhar destaque pessoal nas redes sociais

## Geral
- **Produto:** Torneioz
- **Título:** Compartilhar destaque pessoal nas redes sociais
- **Narrativa:**
Como atleta amador,
Eu quero compartilhar meus gols e estatísticas nas redes sociais direto da plataforma,
Para mostrar meu desempenho aos amigos com um dado oficial por trás, e não só uma foto solta.
- **Prioridade:** Baixa
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** atleta, compartilhamento

## Detalhes

### Descrição Detalhada
Esta história gera uma imagem/card compartilhável a partir dos dados de estatísticas do atleta (história 4.4), pronta para ser postada em redes sociais, reforçando o senso de reconhecimento pessoal e, indiretamente, funcionando como canal de aquisição orgânica para a plataforma.

### Orientações de Tela
- Botão "Compartilhar" na tela de Estatísticas do Atleta
- Card gerado automaticamente com nome, time, gols e destaque da rodada/temporada
- Integração com o compartilhamento nativo do celular

## Regras de Negócio
- O card é gerado sempre com dado já homologado, nunca com estatística provisória
- A marca "Torneioz" aparece discretamente no card, funcionando como divulgação orgânica da plataforma

## BDD & Implementação

### Critérios de Aceitação (BDD)

Compartilhamento após gol na rodada
Dado que o atleta marcou gol em uma súmula homologada da rodada
Quando ele toca em "Compartilhar" na tela de Estatísticas
Então o sistema deve gerar um card com o destaque do gol pronto para postar nas redes

### Orientações para Implementação
- Gerar a imagem do card no servidor (evitar depender de renderização pesada no celular do atleta)
- Registrar evento de analytics: `share_athlete_highlight`
- Id do passo a que corresponde a história: 4.5
