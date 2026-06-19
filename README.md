# Explorateur de noyaux — TCGA-EM-A4FQ (adénome thyroïdien)

Outil web interactif (statique) pour explorer la segmentation nucléaire et les
embeddings d'une lame histologique H&E, avec **deux vues liées** :

- **Gauche — la lame** (image H&E tuilée).
- **Droite — l'UMAP** des embeddings de noyaux.

## Utilisation
- **Colorer par** (menu) : `(aucune)`, type PanNuke, clusters Leiden, KMeans.
  Au démarrage (« aucune »), la lame est nue ; choisis une coloration pour voir les noyaux.
- **Méthode** : embeddings **CellViT** (1280-d) ou **LSP-DETR** (384-d).
- **✋ Lasso** : active-le, puis dessine dans **l'une OU l'autre** vue → les noyaux
  sélectionnés s'affichent **dans les deux** (sur la lame en rouge). Désactive-le pour pan/zoom.
- **Effacer sélection** : remet à zéro.

## Données
Lame **TCGA-EM-A4FQ** (The Cancer Genome Atlas, **données publiques dé-identifiées**).
Segmentation : CellViT++ ; comparaison : LSP-DETR, InstanSeg. ~400 000 noyaux.
Embeddings réduits par UMAP, clusterisés (KMeans / Leiden / HDBSCAN).

## Technique
100 % statique : `index.html` (deck.gl/WebGL via CDN) + données binaires (`data/`) +
tuiles de la lame (`tiles/`). Aucun backend. Hébergeable sur GitHub Pages / Netlify.
