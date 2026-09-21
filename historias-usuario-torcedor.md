# Histórias de Usuário — Torcedores e Comunidade Local

**Produto:** Torneioz
**Persona:** Vanessa Lima, a moradora que só quer saber se o time ganhou
**Jornada de referência:** Acompanhar resultado e tabela do time do bairro sem precisar de conta ou grupo fechado

---

# Acessar o link público do campeonato compartilhado nas redes

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Vanessa Lima, a torcedora — Acompanhar resultado e tabela do time do bairro
- **Passo:** Acessar o link público do campeonato compartilhado nas redes

## Geral
- **Produto:** Torneioz
- **Título:** Acessar o link público do campeonato compartilhado nas redes
- **Narrativa:**
Como torcedora/moradora da comunidade,
Eu quero abrir o link do campeonato compartilhado por alguém,
Para ver a informação rápido, sem precisar baixar aplicativo nem criar conta.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** torcedor, pagina-publica

## Detalhes

### Descrição Detalhada
Esta história reaproveita integralmente a página pública já entregue na Fase 1 (história 1.6), garantindo que o primeiro acesso de um visitante qualquer — sem vínculo formal com nenhum time — seja imediato e sem barreiras de entrada, já que esse público tem baixa disposição para instalar aplicativos novos.

### Orientações de Tela
- Reaproveita a Tela: Página Pública do Campeonato
- Carregamento leve, priorizando a exibição do essencial (tabela e próximos jogos) mesmo em conexões mais lentas

### Regras de Negócio
- Nenhuma barreira de login para o acesso de leitura da página pública

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso via link compartilhado
Dado que alguém recebe o link público do campeonato pelo WhatsApp
Quando essa pessoa abre o link
Então o sistema deve exibir a página pública imediatamente, sem exigir login

### Orientações para Implementação
- Nenhuma implementação nova — depende diretamente da história 1.6
- Id do passo a que corresponde a história: 6.1

---

# Consultar o resultado do último jogo do time

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Vanessa Lima, a torcedora — Acompanhar resultado e tabela do time do bairro
- **Passo:** Consultar o resultado do último jogo do time

## Geral
- **Produto:** Torneioz
- **Título:** Consultar o resultado do último jogo do time
- **Narrativa:**
Como torcedora/moradora da comunidade,
Eu quero ver o placar e os principais eventos do último jogo do time que acompanho,
Para saber se ganhou ou perdeu sem depender de ninguém do grupo do time.
- **Prioridade:** Alta
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** torcedor, resultado-da-partida

## Detalhes

### Descrição Detalhada
Esta história entrega, dentro da página pública, uma visão de resultado por time — filtrando o histórico de jogos de um time específico para que a torcedora não precise navegar por todos os confrontos do campeonato para achar o que importa para ela.

### Orientações de Tela
- Tela: Resultado da Partida, acessível a partir da página do time na página pública
- Placar final e, quando disponível, autores dos gols
- Filtro/atalho "Ver todos os jogos deste time"

### Regras de Negócio
- O resultado só aparece publicamente após a homologação da súmula pelo organizador (mesma regra da história 1.3)

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta de resultado já homologado
Dado que a súmula da última partida do time já foi homologada
Quando a torcedora acessa a página do time
Então o sistema deve exibir o placar final e os autores dos gols, se registrados

### Orientações para Implementação
- Reaproveitar o mesmo dado de súmula homologada da história 1.3, em visão pública filtrada por time
- Id do passo a que corresponde a história: 6.2

---

# Ver a tabela de classificação atualizada

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Vanessa Lima, a torcedora — Acompanhar resultado e tabela do time do bairro
- **Passo:** Ver a tabela de classificação atualizada

## Geral
- **Produto:** Torneioz
- **Título:** Ver a tabela de classificação atualizada
- **Narrativa:**
Como torcedora/moradora da comunidade,
Eu quero ver a posição do time do bairro na tabela,
Para acompanhar se ele está subindo ou descendo na competição.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** torcedor, tabela

## Detalhes

### Descrição Detalhada
Esta história reaproveita integralmente a tabela de classificação pública (história 1.4/1.6), sem necessidade de tela ou lógica exclusiva para o público torcedor.

### Orientações de Tela
- Reaproveita a Tela: Tabela de Classificação (pública)

### Regras de Negócio
- Nenhuma regra adicional além das já definidas na história 1.4

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta pública da tabela
Dado que a tabela foi recalculada após a última rodada
Quando a torcedora acessa a página pública
Então a tabela exibida deve refletir a posição mais recente do time

### Orientações para Implementação
- Nenhuma implementação nova — depende diretamente da história 1.4
- Id do passo a que corresponde a história: 6.3

---

# Consultar o próximo jogo (data, horário, local)

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Vanessa Lima, a torcedora — Acompanhar resultado e tabela do time do bairro
- **Passo:** Consultar o próximo jogo (data, horário, local)

## Geral
- **Produto:** Torneioz
- **Título:** Consultar o próximo jogo (data, horário, local)
- **Narrativa:**
Como torcedora/moradora da comunidade,
Eu quero saber quando é o próximo jogo do time,
Para decidir se vou ao campo, sem perder a partida por falta de aviso.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** torcedor, calendario

## Detalhes

### Descrição Detalhada
Esta história reaproveita o calendário público já entregue na Fase 1, com destaque para o próximo jogo do time selecionado pela torcedora dentro da página pública.

### Orientações de Tela
- Bloco "Próximo Jogo" na página do time, dentro da página pública

### Regras de Negócio
- Reflete o mesmo calendário já usado nas histórias 1.6 e 3.3

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta de próximo jogo por um visitante
Dado que o time selecionado tem um próximo jogo confirmado
Quando a torcedora acessa a página desse time
Então o sistema deve exibir data, horário e local do próximo confronto

### Orientações para Implementação
- Nenhuma implementação nova — depende diretamente da história 1.6/3.3
- Id do passo a que corresponde a história: 6.4

---

# Compartilhar resultado ou tabela nas redes sociais

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 4 – Escala B2B2C e Engajamento da Comunidade
- **Jornada de Usuário:** Vanessa Lima, a torcedora — Acompanhar resultado e tabela do time do bairro
- **Passo:** Compartilhar resultado ou tabela nas redes sociais

## Geral
- **Produto:** Torneioz
- **Título:** Compartilhar resultado ou tabela nas redes sociais
- **Narrativa:**
Como torcedora/moradora da comunidade,
Eu quero compartilhar o resultado ou a posição do time nas redes sociais,
Para torcer junto com a família e os amigos do bairro.
- **Prioridade:** Baixa
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 4 - Planejado
- **Estimativa (pontos):** —
- **Tags:** torcedor, compartilhamento, engajamento

## Detalhes

### Descrição Detalhada
Esta história adiciona um botão de compartilhamento direto a partir do resultado e da tabela, gerando um card visual simples pronto para postar no WhatsApp ou redes sociais, reforçando o alcance orgânico da página pública e, consequentemente, do próprio campeonato.

### Orientações de Tela
- Botão "Compartilhar" nas telas de Resultado da Partida e Tabela de Classificação
- Card gerado automaticamente com placar ou posição na tabela, nome do time e da competição

### Regras de Negócio
- O card compartilhado sempre traz a marca "Torneioz" discretamente, como canal de aquisição orgânica
- O conteúdo do card reflete sempre o dado mais atual no momento do compartilhamento

## BDD & Implementação

### Critérios de Aceitação (BDD)

Compartilhamento de resultado
Dado que a torcedora está vendo o resultado de uma partida já homologada
Quando ela toca em "Compartilhar"
Então o sistema deve gerar um card com o placar e abrir o compartilhamento nativo do celular

### Orientações para Implementação
- Gerar a imagem do card no servidor, reaproveitando a mesma abordagem da história 4.5 (compartilhamento do atleta)
- Registrar evento de analytics: `share_public_result`
- Id do passo a que corresponde a história: 6.5
