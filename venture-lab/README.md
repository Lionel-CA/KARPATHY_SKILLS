# venture-lab : données avant de « créer une licorne »

Collecte du 11 novembre 2026. Objectif : remplacer les intuitions par des taux de base avant de choisir un modèle d'affaires qui décorrèle le revenu des heures du fondateur.

## Ce qu'il y a ici

| Dossier / fichier | Contenu |
|---|---|
| `viz/index.html` | Page interactive autonome : 11 graphiques 2D, 1 nuage 3D, matrice des modèles, table des sources. Ouvrir dans un navigateur (charge Plotly depuis cdnjs). |
| `viz/artifact.html` | Même page, format artefact claude.ai. |
| `data/venture_data.json` | Bundle unique : 24 sections, chaque chiffre avec source et grade. |
| `data/*.csv` | 24 jeux de données à plat (un par thème), importables dans Excel, Sheets, pandas. |
| `data/licornes_cbinsights_liste.json` | Les 1 316 licornes parsées depuis la liste publique CB Insights (société, valorisation, date d'entrée, pays, ville, secteur). |

## Grades de fiabilité

| Grade | Sens | Action |
|---|---|---|
| A | Source primaire lue directement (CB Insights, PitchBook, Acquire.com, Stripe, beehiiv, INSEE, Carta, YC) | Utilisable |
| B | Presse ou analyse reprenant une primaire | Vérifier avant d'agir |
| C | Blog ou agrégateur | Vérifier avant d'agir, ne pas citer seul |
| E | Estimation de l'auteur | À challenger, c'est un jugement |

Les colonnes suffixées `_j` dans `matrice_modeles.csv` (découplage, capital, délai, plafond, probabilités, saturation) sont des jugements construits à partir des taux de base, pas des mesures.

## Sources primaires lues et sources bloquées

Lues : liste publique CB Insights (HTML), PitchBook Q1 2026 Global Unicorn Tracker (PDF du 5 mai 2026), Acquire.com Multiples Report 2025 (PDF), Stripe « top solo founder traits » (2026), beehiiv State of Paid Newsletters 2026, Y Combinator RFS Winter 2027.

Bloquées : carta.com renvoie 403 aux clients automatisés. Les chiffres Carta viennent d'extraits de recherche pointant vers des pages carta.com. La liste CB Insights affiche ~1 447 sociétés, 1 316 lignes ont été parsées proprement ; les totaux par secteur sont donc des minorants.

## Les six chiffres qui comptent

| Chiffre | Valeur | Source |
|---|---|---|
| Startups VC-backed qui deviennent licornes | < 1 % (0,5 à 2,5 % selon dataset) | TechCrunch, AngelList, Stanford, CB Insights |
| Revenu net mensuel médian d'un micro-entrepreneur français | 330 € (P90 : 1 790 €) | INSEE 2024 |
| Écart top décile / médiane chez les fondateurs solo | 61× en 2025 (34× en 2021) | Stripe Atlas |
| Ownership médian de l'équipe fondatrice après Series C | 16,1 % | Carta 2026 |
| Licornes qui n'ont pas levé depuis plus de 2 ans | 844 sur 1 680 (51 %) | PitchBook Q1 2026 |
| Prix d'un petit SaaS rentable à la revente | 3,9× le résultat net, 90 jours médians | Acquire.com 2025 |

## Ce qui manque pour passer du générique au spécifique

Les réponses à ces sept questions ne sont dans aucune base de données :

1. Avantage injuste déjà acquis (compétence rare, audience, accès marché, données, réseau), vérifiable par un tiers.
2. Capital mobilisable sans risque sur le logement.
3. Heures par semaine disponibles sur 24 mois, et revenu net mensuel à remplacer.
4. Horizon : revenu vivable en 24 mois, ou pari à 7 ans avec 75 % de chances de zéro.
5. Acceptation de la dilution et d'un board, ou volonté de garder 100 %.
6. Pays de résidence fiscale et statut actuel.
7. Problème que tu as toi-même payé pour résoudre ces 12 derniers mois.

## Régénérer

Les CSV et le JSON sont produits par un script Python sans dépendance externe. La page HTML embarque le JSON ; après modification des données, réinjecter le bundle dans `viz/artifact.html` et régénérer `viz/index.html`.
