# 🏆 Plataforma de Gestão de Ligas e Campeonatos Esportivos Amadores

Uma plataforma digital **B2B2C** projetada para modernizar a gestão do esporte amador, substituindo o ecossistema fragmentado de planilhas de Excel, anotações em papel e grupos de WhatsApp por uma solução integrada, escalável e agnóstica ao esporte (com piloto inicial focado em **Futebol e Futsal**).

---

## 🔭 Visão do Produto

**Para** organizadores de ligas e campeonatos, patrocinadores locais, administradores de times, atletas amadores, árbitros e torcedores da comunidade,  
**Que** enfrentam uma gestão fragmentada em planilhas manuais, anotações de papel e grupos de WhatsApp, sofrendo com retrabalho operacional, erros no cálculo de tabelas e falta de comprovação de retorno para marcas parceiras,  
**A** [Nome da Plataforma]  
**É uma** plataforma web e mobile-first B2B2C de gestão esportiva e vitrine de ligas amadoras  
**Que** profissionaliza a experiência do esporte amador ao automatizar a apuração de resultados, chaveamentos e controle disciplinar, viabilizando súmulas digitais direto de campo e criando um canal público oficial.  
**Diferente de** planilhas de Excel, grupos fechados de mensagens e aplicativos genéricos de reservas de quadras,  
**O nosso produto** centraliza todo o ecossistema do campeonato em um único ambiente integrado: parametrização de regras, súmula digital ágil, controle financeiro básico e páginas públicas responsivas com tabelas atualizadas em tempo real.

---

## 📌 Visão Geral do Produto

O organizador de campeonatos amadores atua como o cliente pagante principal, enquanto administradores de equipes, atletas, árbitros, torcedores e patrocinadores locais utilizam a plataforma como usuários do ecossistema esportivo.

```mermaid
flowchart TD
    A["Organizador da Liga (B2B)"] --> B["Árbitro em Campo<br>(Súmula Mobile/Off)"]
    A --> C["Capitães / Técnicos<br>(Elencos / Gestão)"]
    A --> D["Patrocinadores Locais<br>(Mídia e Visibilidade)"]

    B --> E["Atletas e Torcedores<br>(Tabelas / Estatísticas)"]
    C --> E
    D --> E
```

---

## 🎯 Escopo do MVP: É / Não É / Faz / Não Faz

### É

- Plataforma de gestão de campeonatos e ligas amadoras.
- Substituto digital para a combinação planilha + WhatsApp.
- Ferramenta B2B2C (organizador paga, comunidade usa).
- Sistema com modelo de dados agnóstico (futebol/futsal no piloto).
- Vitrine digital para divulgação de marcas locais.

### Não é

- Rede social esportiva genérica.
- Sistema de streaming/transmissão ao vivo.
- Plataforma de apostas ou fantasy game.
- ERP esportivo completo (folha de pagamento, contratos, fiscal).
- Aplicativo de agendamento/reserva de quadras avulsas.

### Faz

- Gera automaticamente tabela de classificação e calendário de confrontos.
- Súmula digital móvel com cálculo automático de suspensões por cartões.
- Gerenciamento de inscrições de times, atletas e comissões técnicas.
- Controle financeiro básico (taxas de inscrição e prestação simples).
- Controle de acesso por papéis (Organizador, Capitão, Árbitro).
- Exibe marcas patrocinadoras nas páginas do torneio e súmulas.

### Não faz

- Emissão de notas fiscais ou contabilidade avançada.
- Substituição do julgamento do árbitro em campo.
- Rastreamento por vídeo ou estatísticas avançadas por IA.
- Gestão jurídica de contratos de patrocínio.

---

## 👥 Segmentos de Clientes & Stakeholders

- **Organizadores de Ligas e Campeonatos:** Clientes pagantes que buscam eliminar o trabalho operacional manual e profissionalizar a competição.
- **Patrocinadores e Marcas Locais:** Negócios locais que financiam os eventos em troca de presença digital estruturada e mensurável.
- **Administradores de Times (Capitães/Técnicos):** Responsáveis por gerenciar elencos, acompanhar suspensões e auditar súmulas.
- **Atletas Amadores:** Jogadores que buscam acompanhar seus gols, cartões e histórico pessoal em tempo real.
- **Árbitros da Competição:** Operadores de campo responsáveis pelo registro ágil e sem papel dos eventos da partida.
- **Torcedores e Comunidade Local:** Consumidores de conteúdo público que acompanham os resultados e a classificação do time do bairro.

---

## 🧭 Jobs to be Done (JTBD) — Resumo

- **Organizador:** *“Quando estou gerenciando um campeonato, quero que as tabelas e suspensões sejam calculadas automaticamente a partir das regras cadastradas, para que eu não perca horas corrigindo planilhas nem seja cobrado por erros manuais.”*
- **Árbitro:** *“Quando estou apitando rodadas consecutivas, quero preencher e enviar a súmula diretamente pelo celular, para que eu elimine relatórios em papel sujeitos a perdas e rasuras.”*
- **Capitão:** *“Antes de cada rodada, quero verificar com clareza quais atletas estão suspensos, para que meu time não cometa erros de escalação e perca pontos na justiça desportiva.”*
- **Atleta:** *“Após o término da partida, quero consultar meus gols e histórico atualizados em um link público, para que eu possa acompanhar e compartilhar meu desempenho.”*
- **Patrocinador:** *“Durante toda a temporada, quero que minha marca apareça vinculada às páginas e súmulas oficiais, para que meu investimento tenha visibilidade digital comprovada na comunidade.”*
- **Torcedor e Comunidade Local:** *“A qualquer momento da semana, quero consultar locais, horários e a classificação atualizada em um canal público confiável, para que eu possa acompanhar o time do meu bairro sem depender de grupos fechados de mensagens.”*

---

## 🛠️ Arquitetura e Modelo de Dados Agnóstico

A plataforma foi projetada para suportar diferentes modalidades esportivas através de um modelo de eventos configurável:

```mermaid
erDiagram
    Liga ||--o{ Campeonato : contem
    Liga ||--o{ Patrocinadores : exibe
    Campeonato ||--o{ Partida : possui
    Campeonato ||--o{ Time : inscreve
    Time ||--o{ Atleta : escala
    Partida ||--o{ EventoPartida : registra
```

### Principais Entidades

- `Ligas`: Ligas ou entidades organizadoras.
- `Campeonatos`: Edições de campeonatos com regras específicas de pontuação e desempate.
- `Times` & `Atletas`: Cadastro e relacionamento de elencos por edição.
- `Partidas`: Confrontos com local, data, árbitro designado e status.
- `EventosPartida`: Eventos atômicos em campo (gols, cartões amarelos/vermelhos, substituições).
- `Patrocinadores`: Banners e marcas vinculadas a campeonatos e súmulas.

---

## 🗺️ Roadmap Estratégico

### Pilares Estratégicos

1. **Automação Confiável e Tempo Real:** Eliminar erros manuais de cálculo em tabelas e suspensões.
2. **Operação de Campo Descomplicada:** Súmula digital offline-first para acelerar o fechamento das rodadas.
3. **Transparência e Canal Oficial:** Centralizar dados para eliminar desinformação.
4. **Visibilidade para Patrocinadores:** Estruturar espaços de mídia digital mensuráveis.
5. **Redução da Sobrecarga B2B:** Devolver tempo livre para o organizador.
6. **Escalabilidade Tecnológica:** Garantir testes automatizados e infraestrutura em nuvem sólida desde o MVP.

### Fases de Desenvolvimento

#### Fase 1: MVP de Gestão Essencial (Core B2B)

**Foco:** Criação da base de dados relacional em PostgreSQL e construção da API RESTful (Node.js + Express) para motor de regras, gerador de chaveamento e painel do organizador.

#### Fase 2: Automação de Campo (Súmula Digital e Suspensões)

**Foco:** App/PWA offline-first para árbitros, algoritmo de suspensão e painel disciplinar para capitães. Cobertura de testes unitários e E2E (Cypress) para garantir a precisão dos cálculos e a confiabilidade da súmula.

#### Fase 3: Monetização, Patrocínios e Gestão Financeira

**Foco:** Paywall B2B, gerenciador de banners publicitários nativos e módulo de controle de taxa de inscrição.

#### Fase 4: Infraestrutura em Nuvem e Escala Comunitária

**Foco:** Busca local de torneios, notificações de início/fim de jogo, e implantação otimizada em infraestrutura Cloud (AWS: EC2 para aplicação, S3 para assets/documentos, RDS para banco de dados).

#### Fase 5: Expansão de Esportes e Integrações

**Foco:** Abstração de regras para novas modalidades (vôlei/basquete), pagamentos PIX nativos para times e Webhooks para ligas maiores.

---

## 🚀 Próximos Passos do Desenvolvimento

- [x] Definição de Escopo (É / Não É / Faz / Não Faz)
- [x] Mapeamento de Empatia dos 6 Stakeholders
- [x] Problem-Solution Fit Canvas e Jobs to be Done
- [x] Visão do Produto e Roadmap Estratégico
- [ ] Especificação Técnica dos Casos de Uso do MVP (Súmula Offline-First)
- [ ] Prototipação UI/UX das Páginas Públicas e Módulo do Árbitro
- [ ] Implementação do Backend (Express/Node.js) e Modelagem Relacional (PostgreSQL)

