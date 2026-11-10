# OB POI ★: Multi-Timeframe Order Blocks rated from 1 to 5 stars

A TradingView indicator (Pine Script v6) that finds **Order Blocks (OB)** on
**3m, 5m, 15m, 4H, Daily and Weekly** and gives each one a **1 to 5 star rating**.
The more stars an OB has, the more confluences it has and the more likely the
market is to react (bounce) when price comes back to it.

## How the stars work

Each OB earns **one star per confluence**:

| ★ | Tag     | Meaning |
|---|---------|---------|
| 1 | `DISP`  | **Displacement**: the impulse candle body is ≥ 1.5 × ATR (strong institutional move) |
| 2 | `FVG`   | **Fair Value Gap**: the impulse left an imbalance (gap) behind it |
| 3 | `BOS`   | **Break of Structure**: the move broke the last swing high (bull) or swing low (bear) |
| 4 | `SWEEP` | **Liquidity sweep**: the OB candle took out the lowest low / highest high of the last 20 bars |
| 5 | `TREND` | **Trend alignment**: price is above (bull) or below (bear) the 200 EMA of that timeframe |

**5 ★ = all confluences present = the strongest POI.** 5-star boxes are drawn in gold with a thicker border.

Detection logic, per timeframe:
- **Bullish OB**: the last *bearish* candle before a bullish candle that closes above its high.
- **Bearish OB**: the last *bullish* candle before a bearish candle that closes below its low.

## On the chart

- Each box is labelled with its timeframe and rating, e.g. `4H ★★★★★` and the confluences it has (`DISP FVG BOS SWEEP TREND`).
- **Solid border**: a fresh OB, never touched. This is the one that has the best chance of a bounce.
- **Dashed border**: price has already touched it once.
- A box is removed when a candle **closes through it** (you can switch this to "Mèche" in the settings).
- **Summary table** (top right): the best *fresh* bullish and bearish OB on each timeframe.
- Timeframes **lower** than your chart timeframe show as `off`. For example, on a 15m chart the 3m and 5m OBs aren't shown. To see every timeframe, use a 3m chart.

## Non-repainting

Higher-timeframe OBs are only confirmed once the candle on *their* timeframe
has closed (`request.security` with `[1]` + `lookahead_on`), so a box never
appears and then disappears afterwards.

## Install on TradingView

1. Open TradingView, then **Pine Editor** (bottom of the screen).
2. Delete the default code and paste in the contents of [`OB_POI_Stars.pine`](OB_POI_Stars.pine).
3. Click **Save**, then **Add to chart**.
4. Open the settings (⚙) to change the timeframes, the minimum stars shown, colours, and so on.

## Alerts

Right-click the chart, choose **Add alert**, and set the condition to **OB POI ★**. Then pick one of:
- `OB haussier 5★ touché` / `OB baissier 5★ touché`
- `OB touché (étoiles min)`: uses the "Alerte si le prix touche un OB d'au moins (étoiles)" setting, 4 by default
- **Any alert() function call**: a detailed message with the ticker, rating, timeframe and price zone

## Main settings (the indicator's settings are in French)

| Setting | Default | Notes |
|---------|---------|-------|
| Afficher les OB d'au moins | 3 ★ | Set to 5 to see only the best POIs |
| OB actifs max par UT et par sens | 3 | Keeps the chart clean |
| Zone de l'OB | Mèche | `Corps` gives a tighter zone (open–close) |
| Déplacement | 1.5 × ATR | Higher means stricter |
| Longueur swing (BOS) | 5 | |
| Recul prise de liquidité | 20 | |
| Longueur EMA tendance | 200 | |

---

### Résumé en français

Indicateur TradingView qui détecte les **Order Blocks** en 3m, 5m, 15m, 4H, Daily et Weekly
et leur donne une **note de 1 à 5 étoiles** (déplacement, FVG, cassure de structure,
prise de liquidité, alignement avec la tendance EMA 200). **5 ★ = POI avec le plus de chances
de rebond.** Un bord plein signale un OB jamais touché, un bord pointillé un OB déjà touché.
Le tableau en haut à droite résume le meilleur OB frais de chaque unité de temps.

> ⚠️ The stars measure **confluence**, not a guarantee. Always confirm with your own analysis and risk management.
