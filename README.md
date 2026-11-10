# OB POI ★ : Order Blocks multi-unités de temps notés de 1 à 5 étoiles

Indicateur TradingView (Pine Script v6) **100 % Order Blocks / POI**, sans FVG ni IFVG.
Il détecte les Order Blocks en **3m, 5m, 15m, 4H, Daily et Weekly** et donne à chacun
une note de **1 à 5 étoiles**. Plus l'OB a d'étoiles, plus le prix a de chances de rebondir dessus.

## Les 5 étoiles

Chaque OB gagne **une étoile par confluence** :

| ★ | Confluence | Signification |
|---|------------|---------------|
| 1 | **Déplacement** | L'impulsion qui part de l'OB est forte : son corps fait au moins 1,5 fois l'ATR |
| 2 | **BOS** | L'impulsion casse le dernier sommet (OB haussier) ou le dernier creux (OB baissier) |
| 3 | **Sweep liquidité** | La bougie de l'OB prend le plus bas ou le plus haut des 20 dernières bougies |
| 4 | **Discount / Premium** | L'OB haussier est sous le 50 % du dernier range, l'OB baissier au-dessus |
| 5 | **Tendance** | L'OB est dans le sens de l'EMA 200 de son unité de temps |

**5 ★ = toutes les confluences = POI le plus fort**, affiché en doré.

- **OB haussier** : la dernière bougie baissière avant une bougie haussière qui clôture au-dessus de son plus haut.
- **OB baissier** : la dernière bougie haussière avant une bougie baissière qui clôture sous son plus bas.

## Sur le graphique

- **Étiquette** à droite de chaque zone, par exemple `▲ 4H ★★★★☆`. Le texte est écrit sur un fond plein pour rester lisible.
- **Détail des confluences** : passe la souris sur l'étiquette pour voir les ✔ et les ✘. Tu peux aussi les écrire directement sur l'étiquette dans les réglages.
- **Bordure pleine** : OB jamais touché. C'est lui qui a le plus de chances de faire rebondir le prix.
- **Bordure en pointillés** : le prix l'a déjà touché une fois.
- **OB cassé** : quand une bougie clôture à travers la zone (ou quand une mèche la traverse, selon le réglage), l'OB passe **en gris**, avec une bordure en petits points et l'étiquette `✖ 4H ★★★☆☆ cassé`. Il s'arrête à la bougie qui l'a cassé. Un OB acheteur cassé devient souvent une résistance, et un OB vendeur cassé un support (breaker block). Tu peux régler la couleur et le nombre d'OB cassés affichés (10 par défaut), ou choisir de les supprimer, dans l'onglet « OB cassés (invalidés) ».
- **Tableau en haut à droite** : le meilleur OB haussier et baissier pas encore touché, pour chaque unité de temps.
- **Unités de temps plus petites que ton graphique** : elles affichent `off`. Pour voir les 6 unités de temps, mets ton graphique en 3m.
- **Non repaint** : un OB n'apparaît qu'une fois la bougie de son unité de temps clôturée.

## Couleurs (réglages ⚙, onglet « Couleurs »)

- **Zones** : couleur de l'OB haussier, de l'OB baissier et de l'OB 5 ★.
- **Fond de la zone** : sa transparence, de 0 à 100 %.
- **Bordure** : son épaisseur.
- **Texte de l'étiquette** : sa couleur, avec une couleur à part pour les 5 ★.
- **Étiquette** : sa transparence et la taille du texte (Petit, Normal ou Grand).

## Installation

1. Dans TradingView, ouvre le **Pine Editor**.
2. Efface tout le code, puis colle le contenu de [`OB_POI_Stars.pine`](OB_POI_Stars.pine).
3. Clique sur **Sauvegarder**, puis sur **Ajouter au graphique**.

## Alertes

Clic droit sur le graphique, choisis **Ajouter une alerte**, sélectionne la condition **OB POI ★**, puis l'une de ces alertes :

- `OB haussier 5★ touché` / `OB baissier 5★ touché`
- `OB touché (étoiles min)` : se déclenche à partir de 4 ★ par défaut. Tu peux changer ce minimum dans les réglages.
- **N'importe quel appel de fonction alert()** : message détaillé avec le ticker, les étoiles, l'unité de temps et la zone de prix.

> ⚠️ Les étoiles mesurent la **confluence**, elles ne garantissent pas un rebond. Garde toujours ta propre analyse et ta gestion du risque.
