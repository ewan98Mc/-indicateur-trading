# SMC ★ Tout-en-un : Order Blocks et POI notés de 1 à 5 étoiles

Indicateur TradingView (Pine Script v6) qui rassemble tout dans **un seul indicateur**,
pratique avec la version gratuite de TradingView (nombre d'indicateurs limité).
Chaque outil s'active ou se désactive dans les réglages.

## Les étoiles des Order Blocks

Un OB est détecté en **3m, 5m, 15m, 4H, Daily et Weekly** et gagne **une étoile par confluence** :

| ★ | Confluence | Signification |
|---|------------|---------------|
| 1 | **Déplacement** | L'impulsion qui part de l'OB est forte : son corps fait au moins 1,5 fois l'ATR |
| 2 | **BOS** | L'impulsion casse le dernier sommet (OB acheteur) ou le dernier creux (OB vendeur) |
| 3 | **Sweep liquidité** | La bougie de l'OB prend le plus bas ou le plus haut des 20 dernières bougies |
| 4 | **Discount / Premium** | L'OB acheteur est sous le 50 % du dernier range, l'OB vendeur au-dessus |
| 5 | **Tendance** | L'OB est dans le sens de l'EMA 200 de son unité de temps |

- **5 ★** : toutes les confluences, affiché en doré.
- **0 à 2 ★** : OB **non validé**.

## Les réglages

**① Affichage général**
- **Style des zones** : **Traits** (par défaut) = une ligne en haut et une ligne en bas de chaque zone. **Rectangles** = zones colorées.
- **Ligne du milieu** (50 %) en pointillés : activable.
- **Traits** : épaisseur réglable.
- **Étiquettes** : taille et transparence réglables.
- **Tableau** : affichable ou non.

**② Order Blocks**
- **OB** : affichés ou non.
- **Sens** : OB acheteurs et OB vendeurs, une case pour chacun.
- **Unités de temps** : 3m, 5m, 15m, 4H, Daily, Weekly, une case pour chacune.
- **Étoiles** : une case par note. 5 ★, 4 ★ et 3 ★ sont cochées par défaut ; 2 ★, 1 ★ et 0 ★ (**non validés**) sont décochées.

**③ POI (points d'intérêt multi-UT)**
- **Définition** : un POI est la zone où un OB d'une unité de temps se superpose à un OB d'une autre unité de temps, dans le même sens. Il prend les étoiles du meilleur des deux OB **+1 étoile bonus** (5 au maximum).
- **POI** : affichés ou non.
- **Unités de temps** : 5m, 15m, 4H, Daily, Weekly. L'unité de temps d'un POI est la plus grande des deux (un POI 15m+4H est un POI 4H).
- **Étoiles** : une case par note, de 5 ★ à 1 ★. 1 ★ et 2 ★ sont les POI non validés.
- **Construction** : les POI se forment à partir de tous les OB détectés, même ceux que tu as masqués.

**④ Liquidité** : PDH / PDL (plus haut et plus bas de la veille) et PWH / PWL (plus haut et plus bas de la semaine dernière).

**⑤ OB / POI cassés** : une zone cassée (une bougie clôture au travers) reste affichée en gris, ou est supprimée si tu décoches la case.

**⑥ Détection des OB**, **⑦ Couleurs** (tout est modifiable) et **⑧ Alertes**.

## Sur le graphique

- **Étiquette** : par exemple `▲ OB 4H ★★★★☆` ou `◆ POI 15m+4H ★★★★★`. Passe la souris dessus pour voir les ✔ et les ✘.
- **Trait plein** : zone jamais touchée.
- **Pointillés** : zone déjà touchée.
- **Petits points gris** : zone cassée.
- **Unités de temps plus petites que ton graphique** : elles ne sont pas affichées. Pour tout voir, utilise un graphique en 1m ou 3m.

## Installation

1. Dans TradingView, ouvre le **Pine Editor**.
2. Efface tout le code et colle le contenu de [`OB_POI_Stars.pine`](OB_POI_Stars.pine).
3. Clique sur **Sauvegarder**, puis sur **Ajouter au graphique**.

## Alertes

- `OB/POI acheteur 5★ touché` et `OB/POI vendeur 5★ touché`.
- `OB touché (étoiles min)` et `POI touché (étoiles min)` : se déclenchent à partir de 4 ★ par défaut. Tu peux changer ce minimum dans les réglages.
- **N'importe quel appel de fonction alert()** : message détaillé avec le ticker, les étoiles, l'unité de temps et la zone de prix.

> ⚠️ Les étoiles mesurent la **confluence**, elles ne garantissent pas un rebond. Garde toujours ta propre analyse et ta gestion du risque.
