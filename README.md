# OB ★ : Order Blocks notés de 1 à 5 étoiles

Indicateur TradingView (Pine Script v6) **simple** : il repère les **order blocks** en
**3m, 5m, 15m, 4H, Daily et Weekly**, leur donne une note de **1 à 5 étoiles**,
et affiche les niveaux **PDH / PDL** et **PWH / PWL**.

## Les étoiles

Un OB gagne **une étoile par confluence** :

| ★ | Confluence | Signification |
|---|------------|---------------|
| 1 | **Déplacement** | L'impulsion qui part de l'OB est forte : son corps fait au moins 1,5 fois l'ATR |
| 2 | **BOS** | L'impulsion casse le dernier sommet (OB acheteur) ou le dernier creux (OB vendeur) |
| 3 | **Sweep liquidité** | La bougie de l'OB prend le plus bas ou le plus haut des 20 dernières bougies |
| 4 | **Discount / Premium** | L'OB acheteur est sous le 50 % du range, l'OB vendeur au-dessus |
| 5 | **Tendance** | L'OB est dans le sens de l'EMA 200 de son unité de temps |

**5 ★** = toutes les confluences, affiché en doré. **0 à 2 ★** = OB **non validé**.

## Les réglages

**① Unités de temps des OB** : une case pour chaque unité de temps (3m, 5m, 15m, 4H, Daily, Weekly).

**② OB à afficher**
- OB acheteurs ▲ / OB vendeurs ▼.
- Une case par note : 5 ★, 4 ★ et 3 ★ cochées par défaut ; 2 ★, 1 ★ et 0 ★ (non validés) décochées.
- Nombre maximum d'OB par unité de temps et par sens (2 par défaut).
- **Seulement les OB proches du prix** : les OB trop loin sont masqués. La distance se règle en ATR journalier (3 par défaut).

**③ OB cassés**
- **Un OB est cassé quand** : une bougie clôture au travers (par défaut), une mèche traverse tout l'OB, ou le prix dépasse 50 % de l'OB.
- **Garder les OB cassés à l'écran** : décoché par défaut, un OB cassé disparaît tout seul. Coché, il reste en gris pointillé.

**④ Style**
- **Style des OB** :
  - **Un seul trait** (par défaut) : le graphique le plus propre.
  - **Deux traits** : le haut et le bas de l'OB.
  - **Rectangle rempli**.
- **Position du trait unique** : **Bord d'entrée** (le haut d'un OB acheteur, le bas d'un OB vendeur, là où le prix le touche en premier) ou **Milieu de l'OB**.
- **Tous les OB d'une seule couleur** : par exemple en noir.
- Épaisseur des traits, transparence des rectangles, longueur des traits (courts près du prix ou depuis la bougie de l'OB), étiquettes, taille du texte, tableau.

**⑤ Liquidité** : PDH / PDL (plus haut et plus bas de la veille) et PWH / PWL (plus haut et plus bas de la semaine dernière).

**⑥ Couleurs**, **⑦ Détection (avancé)** et **⑧ Alertes**.

## Sur le graphique

- **Étiquette** : par exemple `▲ 4H ★★★★★` (OB acheteur 4H, 5 étoiles). Passe la souris dessus pour voir la zone de prix et les confluences ✔ / ✘.
- **Trait plein** : OB jamais touché.
- **Tirets** : OB déjà touché.
- **Tableau** : le meilleur OB acheteur et vendeur pas encore touché, pour chaque unité de temps.
- **Unités de temps plus petites que ton graphique** : elles affichent `off`. Pour tout voir, mets ton graphique en 3m ou en 1m.

## Installation

1. Dans TradingView, ouvre le **Pine Editor**.
2. Efface tout le code et colle le contenu de [`OB_POI_Stars.pine`](OB_POI_Stars.pine).
3. Clique sur **Sauvegarder**, puis sur **Ajouter au graphique**.

## Alertes

- `OB acheteur 5★ touché` et `OB vendeur 5★ touché`.
- `OB touché (étoiles min)` : à partir de 4 ★ par défaut. Tu peux changer ce minimum dans les réglages.
- **N'importe quel appel de fonction alert()** : message détaillé avec le ticker, les étoiles, l'unité de temps et la zone de prix.

> ⚠️ Les étoiles mesurent la **confluence**, elles ne garantissent pas un rebond. Garde toujours ta propre analyse et ta gestion du risque.
