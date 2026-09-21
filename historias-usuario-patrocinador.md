# Histórias de Usuário — Patrocinadores e Marcas Locais

**Produto:** Torneioz
**Persona:** Camila Duarte, a patrocinadora que quer dado antes de investir
**Jornada de referência:** Avaliar e confirmar um pacote de visibilidade de marca no campeonato, com dado concreto de exposição

*Nota: nas Fases 1–3 do roadmap o patrocinador não possui login próprio na plataforma (o Portal do Patrocinador com acesso direto só chega na Fase 5). Por isso, algumas histórias abaixo são operadas pelo Organizador em nome do patrocinador, mesmo estando organizadas sob a jornada da Camila para manter a rastreabilidade.*

---

# Visualizar a proposta de espaços de patrocínio do campeonato

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Receber a proposta de espaço de patrocínio do organizador

## Geral
- **Produto:** Torneioz
- **Título:** Visualizar a proposta de espaços de patrocínio do campeonato
- **Narrativa:**
Como patrocinadora/marca local,
Eu quero visualizar uma página com os espaços de patrocínio disponíveis no campeonato,
Para entender rapidamente se o investimento faz sentido antes de conversar com o organizador.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** patrocinador, pagina-de-apoiadores

## Detalhes

### Descrição Detalhada
Esta história entrega uma página pública, compartilhável pelo organizador, que apresenta os espaços de mídia digital disponíveis no campeonato (banner na tabela, logo em súmulas, página de apoiadores). Substitui a conversa informal "sem nada pra mostrar" por um material de vendas padronizado que o organizador pode enviar a qualquer patrocinador em potencial.

### Orientações de Tela
- Título: "Espaços de Patrocínio Disponíveis"
- Cards com cada tipo de espaço (banner na tabela, logo na súmula, página de apoiadores) e uma prévia visual
- Indicador de alcance estimado (nº de times, jogos e visualizações médias da página pública)
- Botão de contato direto com o organizador (WhatsApp/e-mail)

### Regras de Negócio
- A página é gerada automaticamente a partir dos dados já existentes do torneio (times, jogos, visualizações)
- Não expõe dados de outros patrocinadores já fechados, apenas espaços genéricos disponíveis
- Fica acessível sem necessidade de login, via link compartilhável pelo organizador

## BDD & Implementação

### Critérios de Aceitação (BDD)

Acesso à proposta sem login
Dado que o organizador compartilha o link da página de patrocínio
Quando a patrocinadora abre esse link
Então o sistema deve exibir os espaços disponíveis com uma prévia visual de cada um

Torneio sem histórico de visualizações
Dado que o torneio é novo e ainda não possui dados de visualização acumulados
Quando a página de patrocínio é exibida
Então o sistema deve omitir o indicador de alcance em vez de mostrar um valor zerado ou incorreto

### Orientações para Implementação
- Reaproveitar dados agregados já calculados para a página pública (evitar nova fonte de verdade)
- Registrar evento de analytics: `view_sponsor_proposal`
- Id do passo a que corresponde a história: 2.1

---

# Visualizar a página pública do campeonato como avaliação

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 1 – MVP de Gestão Essencial (O Core B2B)
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Visualizar a página pública do campeonato

## Geral
- **Produto:** Torneioz
- **Título:** Visualizar a página pública do campeonato como avaliação
- **Narrativa:**
Como patrocinadora/marca local,
Eu quero ver como está a página pública do campeonato hoje,
Para avaliar se ele tem cara de coisa séria antes de decidir investir.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 1 - Priorizado
- **Estimativa (pontos):** —
- **Tags:** patrocinador, pagina-publica

## Detalhes

### Descrição Detalhada
Esta história reaproveita a página pública do campeonato (já entregue na Fase 1 para times e torcedores) como material de avaliação para patrocinadores em potencial. Não introduz tela nova — garante que a página pública já transmita profissionalismo suficiente (dados atualizados, visual limpo) para servir também a esse público.

### Orientações de Tela
- Reaproveita a Tela: Página Pública do Campeonato (classificação, calendário, times)
- Nenhum elemento exclusivo para patrocinador nesta etapa — a força da história está na qualidade visual e de atualização da página já existente

### Regras de Negócio
- A página pública deve estar sempre com dado atualizado no momento da avaliação (dependência direta da história "Ver a tabela de classificação atualizar automaticamente")
- Não há distinção de acesso entre visitante comum e potencial patrocinador nesta fase

## BDD & Implementação

### Critérios de Aceitação (BDD)

Página pública com dado atualizado
Dado que a patrocinadora acessa a página pública do campeonato
Quando a última rodada já foi homologada
Então a página deve refletir a tabela e os resultados mais recentes, sem defasagem perceptível

### Orientações para Implementação
- Nenhuma implementação nova — depende da história 1.6 (Compartilhar o link público)
- Id do passo a que corresponde a história: 2.2

---

# Consultar espaços de mídia disponíveis por porte de investimento

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Consultar os espaços de mídia disponíveis

## Geral
- **Produto:** Torneioz
- **Título:** Consultar espaços de mídia disponíveis por porte de investimento
- **Narrativa:**
Como organizador,
Eu quero gerenciar quais espaços publicitários estão disponíveis, ocupados ou reservados,
Para apresentar com clareza ao patrocinador onde exatamente a marca dele vai aparecer.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** organizador, gerenciador-de-banners

## Detalhes

### Descrição Detalhada
Esta história entrega o gerenciador de espaços publicitários do lado do organizador: cadastro dos formatos disponíveis (banner na tabela, logo em súmula, página de apoiadores) e seu status de ocupação. É o inventário que sustenta a proposta comercial mostrada à patrocinadora na história 2.1.

### Orientações de Tela
- Tela: Gerenciador de Espaços de Patrocínio (lado organizador)
- Lista de espaços com status: Disponível / Reservado / Ocupado
- Formulário de cadastro de novo espaço (tipo, posição, período de exposição)
- Upload de logo do patrocinador vinculado a um espaço ocupado

### Regras de Negócio
- Um espaço "Ocupado" exibe automaticamente o logo do patrocinador nas páginas públicas correspondentes
- Não é possível ocupar um espaço já reservado por outro patrocinador no mesmo período
- Espaços expiram automaticamente ao final do período contratado, voltando a "Disponível"

## BDD & Implementação

### Critérios de Aceitação (BDD)

Cadastro de novo espaço ocupado
Dado que o organizador cadastra um novo patrocinador em um espaço disponível
Quando ele faz upload do logo e define o período
Então o espaço deve passar para "Ocupado" e o logo deve aparecer nas páginas públicas correspondentes

Tentativa de conflito de reserva
Dado que um espaço já está reservado para um período específico
Quando o organizador tenta ocupar o mesmo espaço com outro patrocinador no período sobreposto
Então o sistema deve impedir a ação e exibir uma mensagem de conflito

### Orientações para Implementação
- Job agendado para expirar espaços automaticamente ao fim do período contratado
- Registrar evento de analytics: `sponsor_slot_created`
- Id do passo a que corresponde a história: 2.3

---

# Registrar as contrapartidas negociadas com o patrocinador

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Negociar contrapartidas com o organizador

## Geral
- **Produto:** Torneioz
- **Título:** Registrar as contrapartidas negociadas com o patrocinador
- **Narrativa:**
Como organizador,
Eu quero registrar no sistema o que foi acordado com um patrocinador (espaço, período, valor),
Para ter um controle formal do acordo em vez de depender só da memória ou de conversa informal.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** organizador, patrocinio, financeiro

## Detalhes

### Descrição Detalhada
Esta história permite ao organizador registrar formalmente os termos do acordo de patrocínio fechado — quais espaços, por quanto tempo e a que valor — vinculando esse registro ao espaço publicitário ocupado. Não substitui um contrato jurídico, mas cria um registro estruturado que sustenta o relatório de exposição da história seguinte.

### Orientações de Tela
- Formulário: Nome do patrocinador, espaços contratados, período, valor acordado (opcional)
- Campo de observações livres para condições específicas
- Listagem de patrocinadores ativos por temporada

### Regras de Negócio
- Um registro de patrocínio deve estar sempre vinculado a pelo menos um espaço publicitário
- O valor é um campo opcional (nem todo organizador quer registrar valores financeiros no sistema)
- Editar um registro existente não deve apagar o histórico de exposição já contabilizado

## BDD & Implementação

### Critérios de Aceitação (BDD)

Registro de novo acordo
Dado que o organizador fechou um acordo de patrocínio
Quando ele preenche o formulário com patrocinador, espaço e período
Então o sistema deve salvar o registro e vincular o espaço como ocupado por esse patrocinador

### Orientações para Implementação
- Relacionar o registro de patrocínio 1:N com espaços publicitários (um patrocinador pode ocupar vários espaços)
- Registrar evento de analytics: `sponsor_deal_registered`
- Id do passo a que corresponde a história: 2.4

---

# Acompanhar a exposição da marca ao longo da temporada

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Acompanhar a exposição da marca ao longo da temporada

## Geral
- **Produto:** Torneioz
- **Título:** Acompanhar a exposição da marca ao longo da temporada
- **Narrativa:**
Como patrocinadora/marca local,
Eu quero acompanhar quantas vezes e onde minha marca apareceu nas páginas do campeonato,
Para ter um dado concreto em vez de decidir só no "achismo" se o patrocínio está valendo a pena.
- **Prioridade:** Média
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** patrocinador, relatorio-de-exposicao

## Detalhes

### Descrição Detalhada
Esta história entrega o relatório básico de impressões/visualizações do espaço de patrocínio, acessível via link compartilhado pelo organizador (sem exigir login do patrocinador nesta fase). É a resposta direta à dor mais citada nas entrevistas com patrocinadores: a ausência de qualquer dado de retorno.

### Orientações de Tela
- Tela: Relatório de Exposição do Patrocinador
- Indicadores: nº de visualizações da página onde a marca aparece, período do acordo, dias restantes de exposição
- Gráfico simples de visualizações ao longo do tempo
- Link exclusivo e não listado, gerado por acordo de patrocínio

### Regras de Negócio
- O contador de visualizações reflete acessos reais às páginas públicas onde o espaço do patrocinador está ativo
- O relatório só mostra dados a partir da data de início do acordo registrado
- O link do relatório expira ou perde validade ao final do período contratado

## BDD & Implementação

### Critérios de Aceitação (BDD)

Consulta durante o período ativo do patrocínio
Dado que o acordo de patrocínio está dentro do período contratado
Quando a patrocinadora acessa o link do relatório
Então o sistema deve exibir o total de visualizações acumuladas até o momento

Consulta após o fim do período contratado
Dado que o período do acordo já expirou
Quando alguém tenta acessar o link do relatório
Então o sistema deve exibir os dados finais consolidados da temporada, sem permitir mais atualização

### Orientações para Implementação
- Contabilizar visualizações de forma assíncrona, sem impactar o tempo de carregamento da página pública
- Registrar evento de analytics: `sponsor_report_view`
- Id do passo a que corresponde a história: 2.5

---

# Consultar relatório consolidado para decisão de renovação

## Passo de Jornada
- **Fase do Roadmap Estratégico:** Fase 3 – Monetização, Patrocínios e Gestão Financeira
- **Jornada de Usuário:** Camila Duarte, a patrocinadora — Avaliar e confirmar um pacote de visibilidade de marca
- **Passo:** Decidir sobre a renovação para a próxima temporada

## Geral
- **Produto:** Torneioz
- **Título:** Consultar relatório consolidado para decisão de renovação
- **Narrativa:**
Como patrocinadora/marca local,
Eu quero ver um resumo consolidado de toda a temporada de patrocínio,
Para decidir com dado, e não no feeling, se vou renovar o apoio na próxima temporada.
- **Prioridade:** Baixa
- **Tipo:** Feature
- **Coluna:** Backlog
- **Subcoluna:** Fase 3 - Planejado
- **Estimativa (pontos):** —
- **Tags:** patrocinador, relatorio-de-exposicao

## Detalhes

### Descrição Detalhada
Esta história estende o relatório de exposição (história 2.5) com uma versão consolidada de fim de temporada, comparando o que foi prometido (espaços contratados) com o que foi de fato entregue (visualizações acumuladas), servindo como base objetiva para a conversa de renovação com o organizador.

### Orientações de Tela
- Tela: Relatório de Temporada (Patrocinador)
- Resumo: período total de exposição, visualizações totais, espaços ocupados
- Comparativo simples com a temporada anterior, quando existir dado histórico

### Regras de Negócio
- O relatório consolidado só é gerado após o encerramento oficial da temporada pelo organizador
- Quando não há temporada anterior registrada, o comparativo histórico é omitido

## BDD & Implementação

### Critérios de Aceitação (BDD)

Encerramento de temporada com histórico
Dado que a temporada foi encerrada e há uma temporada anterior registrada para o mesmo patrocinador
Quando o relatório consolidado é gerado
Então o sistema deve exibir o comparativo entre as duas temporadas

### Orientações para Implementação
- Reaproveitar os dados já coletados nas histórias 2.4 e 2.5, sem nova fonte de dado
- Id do passo a que corresponde a história: 2.6
