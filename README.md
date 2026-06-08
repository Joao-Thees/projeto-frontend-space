# Arizona Datacenter Heat Analysis — V2

Análise do impacto térmico do **CyrusOne Phoenix Datacenter** sobre a temperatura superficial (LST) em relação a uma área verde adjacente, Phoenix, AZ — 2025.

Corrobora os achados de [techxplore.com/news/2026-05-centers-nearby-temperatures-degrees-phoenix](https://techxplore.com/news/2026-05-centers-nearby-temperatures-degrees-phoenix.html) usando dados Landsat via Google Earth Engine.

## Front-End Design (FED) — documentação da entrega
## O PROJETO PRINCIPAL E COMPLETO, INTEGRANDO FRONT END E BACK END, PARA UMA FUNCIONALIDADE COMPLETA ENCONTRA-SE NO GITHUB: https://github.com/Joao-Thees/Global-Solution.git

## ESTA ENTREGA É SOMENTE O FRONT END DO PROJETO. NO PROJETO PRINCIPAL, AMBOS TRABALHAM EM CONJUNTO, FORMANDO O ECOSISTEMA COMPLETO DO PROJETO. AQUI, NÃO SE VISUALIZA O MAPA, O MAPA DE CALOR E NEM RELATÓRIOS. SOMENTE HTML E CSS.

Tema: **"A Interface da Missão"**. A pasta entregue da FED é `FRONT/`.

### Usuário e tarefa crítica
- **Usuário:** Analista de Observação da Terra de um Centro de Operações de Clima Urbano.
- **Tarefa crítica:** monitorar, via LST orbital (Landsat), o aquecimento do datacenter
  CyrusOne Phoenix frente à área verde de controle e **emitir alerta** quando a anomalia
  (Datacenter − Área verde) ultrapassa o limiar seguro configurado.
- **Conexão com a Indústria Espacial:** o produto consome dado orbital / sensoriamento remoto
  (Earth Observation) e é apresentado como **painel de missão / observação da Terra**.

### Justificativa visual
Direção visual completa (referências, análise crítica, paleta e tipografia) em
**`assets/moodboard.html`**. Resumo: tema escuro para monitoramento prolongado,
laranja como cor de missão (datacenter), verde/vermelho reservados a estado (nominal/alerta),
tipografia **Inter** com numerais tabulares para alinhar as leituras de telemetria.

### Visão das telas (uma tela, regiões)
- **Mapa orbital** (`<main>`): Leaflet com fundo RGB (GEE) + camada de anomalia LST + polígonos
  dos sites; banner de **alerta crítico** sobreposto.
- **Painel de missão** (`<aside>`): telemetria ao vivo, controles (botões + formulário),
  camadas, períodos, sites, resultados do modelo, série temporal e metodologia.

### Decisões de responsividade
- Breakpoints `@media` em **1024 / 768 / 480 px**.
- ≤768 px: layout empilha — mapa no topo (50vh) e painel rolável embaixo.
- ≤480 px: fontes/margens reduzidas e alvos de toque maiores.
- `map.invalidateSize()` no `resize`/`orientationchange` (evita tiles cinza ao girar a tela).

### Decisões de acessibilidade
- Landmarks semânticos: `header / nav / main / aside / section / footer` (sem "div soup").
- Contraste mínimo **WCAG AA** (tokens `--text-muted`/`--text-dim` conferidos sobre `#0d0d0d`).
- `aria-label`/`role`/`aria-live` nos pontos dinâmicos; `<label for>` em todos os campos;
  **skip link** "Pular para o mapa"; foco visível (`:focus-visible`);
  `prefers-reduced-motion` desliga animações.
- Tabela de telemetria com `caption`, `scope` em `th` e descrição.

### Componentes (estilizados por classe, sem estilo inline no HTML)
Alerta crítico (`.alert-banner`), tabela de telemetria (`.telemetry-table`), botões
(`.btn`/`.btn-primary`/`.btn-armed`), formulário (`.mission-form`), status pills
(`.status-pill`), navegação do painel (`.panel-nav`).

### Entregáveis FED
- `integrantes.txt` (raiz) — nome completo + RM de cada integrante.
- `moodboard.html` — moodboard com análise crítica.