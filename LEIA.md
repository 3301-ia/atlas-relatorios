# Assinatura dos Indicadores — Atlas Vectra

Registro técnico de 9 de novembro de 2026. Cada indicador recebe uma assinatura de versão, calculada sobre o arquivo-fonte, e um protocolo de assinatura de sinal, para que as leituras deixem de ser apenas visuais e passem a ser verificáveis por robô.

## Princípio

Um sinal que serve para robô precisa de três provas:

1. **Identidade** — de qual indicador e de qual versão o sinal veio. Resolvido pelo hash do arquivo-fonte.
2. **Parâmetros** — com quais valores o indicador estava configurado. Um mesmo indicador com histerese diferente é outro indicador.
3. **Fato** — o evento em si, datado pelo fechamento do candle: ativo, tempo, lado, preço de referência, stop e alvo.

Somados e resumidos por hash, os três formam a assinatura do sinal. Ela não muda com zoom, tema, orientação de tela ou ordem de carregamento, porque não depende do desenho: depende do cálculo e do candle fechado.

## Registro dos seis indicadores

### gann_square_of_nine.pine

- Declaração: `indicator("Gann Square of Nine - Universal HUD & Cycle Engine v4", shorttitle="Gann Sq9 v4", overlay=true, max_lines_cou`
- Pine Script: versão 6 · 412 linhas · 25472 bytes
- Assinatura de versão (SHA-256 do fonte): `a731787bd5b1e7d8a837ffa8ec20625bb56cf50f953140f174fcaeb35c03e444`
- Emite sinal: sim, por alertas nomeados
  - alerta: `ta.crossunder(close, p_red_90),  title="Perda 90° → Anel Vermelho",   `
  - alerta: `ta.crossover(close,  p_exp_90),  title="Rompimento +90° → Anel Verde",`
  - alerta: `ta.cross(close, p_red_1620),     title="Toque Alvo Crítico 1620°",    `
  - alerta: `ta.cross(close, p_red_1800),     title="Zona de Exaustão 1800°",      `
  - alerta: `ta.cross(close, p_exp_1440),     title="Oitava +1440° (4ª Volta Acima)`
  - alerta: `ta.cross(close, p_exp_3600),     title="TETO MÁXIMO +3600°",          `
- Parâmetros que entram na assinatura: `anchor_mode` = "Automático (Pivôs Recentes; `pivot_len` = 15, "Período do Pivô (Modo Automático; `manual_top` = 87128.0, "Preço Topo Manual (P_topo; `manual_bot` = 82467.0, "Preço Fundo Manual (P_fundo; `scale_choice` = "Automático (Auto-Detectar; `show_hud` = true, "Exibir Painel HUD", group=grp_h; `hud_position` = "Topo Direito", "Posição do Painel",; `hud_size_opt` = "Pequeno", "Tamanho da Fonte HUD",

### indicador_master_atlas_v10.pine

- Declaração: `indicator("Indicador Master: Atlas v10 + Ribbon + Bubbles", overlay=true, max_labels_count=500, max_lines_count=500, max`
- Pine Script: versão 6 · 91 linhas · 6966 bytes
- Assinatura de versão (SHA-256 do fonte): `35a40afc2272b247f47a11bc279f04a72ab0356a823b4665892b64b62b3f8c24`
- Emite sinal: não identificado no fonte
- Parâmetros que entram na assinatura: `lowerTfInput` = "", "Lower TF (Empty = Auto Scale; `minNotional` = 500, "Min notional to show (USD/USDT; `maxPerBar` = 1, "Max bubbles per bar", minval=1, ma; `bubblePos` = "Wick Extreme", "Bubble Position", opt; `showText` = true, "Show notional text", group=grpB; `textSizeOpt` = "Normal", "Text Size", options=["Auto"; `textDecoup` = true, "Separate Text (Prevents blockin; `bubbleTrans` = 40, "Bubble Transparency (0-100

### vectra_dynamic_indicator.pine

- Declaração: `indicator("Vectra Dynamic INDICATOR", overlay=true, max_labels_count=500, max_lines_count=500)`
- Pine Script: versão 5 · 162 linhas · 7275 bytes
- Assinatura de versão (SHA-256 do fonte): `37c3bae56dcbdb6a46bf25872c150c81a4d495fa94d66ce875f2629bb90dd5df`
- Emite sinal: sim, por rótulos no gráfico
  - rótulos de operação: ENTRADA L, ENTRADA S, STOP L, STOP S
- Parâmetros que entram na assinatura: `fast_len` = 10, "Período Base ZLEMA", minval=1, gr; `kama_len` = 34, "Período Lento KAMA (Filtro Macro; `hist_mult` = 0.45, "Histerese ATR (Anti-Ruído Micro; `len_atr` = 14, "Período ATR (Volatilidade; `use_slope` = true, "Exigir Inclinação da ZLEMA para; `mult_stop` = 1.8, "Multiplicador Trailing Stop (Lar; `mult_tp1` = 2.2, "Multiplicador TP 1 (Verde; `mult_tp2` = 3.4, "Multiplicador TP 2 (Azul

### vectra_dynamic_stepped_trailing.pine

- Declaração: `indicator("Vectra Dynamic (Pure Stepped Trailing & Targets) - Suavizado MTF", overlay=true, max_labels_count=500, max_li`
- Pine Script: versão 5 · 152 linhas · 6867 bytes
- Assinatura de versão (SHA-256 do fonte): `4abccbbaba730bb5d91f42505548903d93e8fb5273679e92f4abd04f21010bf2`
- Emite sinal: sim, por rótulos no gráfico
  - rótulos de operação: ENTRADA L, ENTRADA S, STOP L, STOP S
- Parâmetros que entram na assinatura: `fast_len` = 10, "Período Base ZLEMA", minval=1, gr; `kama_len` = 34, "Período Lento KAMA (Filtro Macro; `hist_mult` = 0.40, "Histerese ATR (Anti-Ruído Micro; `len_atr` = 14, "Período ATR (Volatilidade; `mult_stop` = 1.8, "Multiplicador Trailing Stop (Lar; `mult_tp1` = 2.2, "Multiplicador TP 1 (Verde; `mult_tp2` = 3.4, "Multiplicador TP 2 (Azul; `mult_tp3` = 4.8, "Multiplicador TP 3 (Rosa

### vectra_ema_ribbon_matrix_rsi.pine

- Declaração: `indicator("Vectra 8-EMA Ribbon + Matrix RSI CVD [Atlas v6]", overlay=true, max_labels_count=500)`
- Pine Script: versão 6 · 110 linhas · 6338 bytes
- Assinatura de versão (SHA-256 do fonte): `1a2b9ec727a395bdf0f596c4a3aa27b52298410799c2de37485d1791a9707671`
- Emite sinal: não identificado no fonte

### vectra_mtf_ribbon_matrix_institutional.pine

- Declaração: `indicator("Vectra MTF EMA Ribbon Matrix (1W, 3W, 1M, 12M)", overlay=false, precision=2)`
- Pine Script: versão 5 · 89 linhas · 4971 bytes
- Assinatura de versão (SHA-256 do fonte): `d2338f4dcd5ad5cd2bb1c4cba47d3c4c682894b18136fff38ea3d34c97ab2b79`
- Emite sinal: não identificado no fonte
- Parâmetros que entram na assinatura: `len_fast` = 2, "Período EMA Ultrarrápida", minval=; `len_mid` = 21, "Período EMA Intermediária", minva; `len_slow` = 200, "Período EMA Institucional", minv; `tf_1w` = "1W", "Timeframe 1: 1 Semana"; `tf_3w` = "3W", "Timeframe 2: 3 Semanas"; `tf_1m` = "1M", "Timeframe 3: 1 Mês"; `tf_12m` = "12M", "Timeframe 4: 1 Ano"

## Protocolo de assinatura de sinal

```
payload = ativo | tempo_do_candle | lado | preco | stop | alvo | id_indicador | hash_versao | hash_parametros
assinatura = SHA-256(payload)
```

O robô só aceita o sinal quando o hash_versao confere com o registro autorizado e o hash_parametros confere com a calibração vigente. Sinal sem par válido é descartado, mesmo que apareça na tela.

## Situação real dos seis

Apenas o Gann Square of Nine publica alertas nomeados, seis deles, com os anéis de 90 e 1620 graus, a exaustão de 1800, a oitava de 1440 e o teto de 3600. Os dois Vectra Dynamic emitem os rótulos ENTRADA L, ENTRADA S, STOP L e STOP S no gráfico, mas sem `alertcondition`, então não existe hoje um canal pelo qual o sinal avise o robô. O Ribbon Matrix, o MTF institucional e o Master v10 são leitura de contexto, não emissores.

Conclusão: para virar robô, cinco dos seis precisam de uma linha de alerta. É trabalho pequeno e é exatamente o que congela o sinal: alerta dispara uma vez, no fechamento do candle, com o preço daquele instante. Rótulo muda de posição com o zoom, alerta não.

## Próximo passo proposto

1. Acrescentar `alertcondition` em cada ponto de entrada e de stop dos dois Vectra Dynamic, com mensagem em formato fixo, já no padrão do payload acima.
2. Recalcular as assinaturas de versão depois da mudança e registrar a nova tabela.
3. Montar um teste determinístico: um conjunto de candles fixo, roda cada indicador e registra o hash da sequência de sinais. Se o hash mudar sem mudança de código, há sinal dependente de estado de tela, e isso é o que precisamos eliminar antes de plugar na Deriv.

Sobre a Deriv: a plataforma de automação dela é a Deriv Bot, com blocos, e o acesso programático é por contrato de API com token, via WebSocket, não por CTrader. Existem contas de demonstração gratuitas ilimitadas e as reais são derivadas delas. Quando chegarmos lá, o caminho natural é gravar os sinais em um serviço que o robô consulte, com a assinatura acima como chave de aceitação.
