# Nucleus explorer — TCGA-EM-A4FQ (thyroid adenoma)

Interactive (static) web tool to explore nuclear segmentation and embeddings of an
H&E whole-slide image, with **two linked views**:

- **Left — the slide** (tiled H&E image).
- **Right — the UMAP** of nucleus embeddings.

**Live demo:** https://synaspike.github.io/tcga-nuclei-viewer/

## Usage
- **Color by** (menu): `(none)`, PanNuke type, Leiden clusters, KMeans.
  On startup (`none`) the slide is bare; pick a coloring to reveal the nuclei.
- **Method**: **CellViT** (1280-d) or **LSP-DETR** (384-d) embeddings.
- **✋ Lasso** — `Shift + drag` (or the button) in **either** view → the selected nuclei
  light up **in both** (red on the slide). Hold `Shift` and redraw to **add** more regions;
  scroll = zoom (always on). **Clear selection** resets.
- **⬇ Slide / ⬇ UMAP** — download the **current view** (with/without coloring) as a
  publication-ready PNG.

*(A ▭ ROI export — high-res H&E crops with green nuclear contours — is available when the
optional Python backend `server.py` is running locally; it stays hidden on the static site.)*

## Data
Slide **TCGA-EM-A4FQ** (The Cancer Genome Atlas, **public de-identified data**).
Segmentation: CellViT++; comparison: LSP-DETR, InstanSeg. ~400,000 nuclei.
Embeddings reduced by UMAP, clustered (KMeans / Leiden / HDBSCAN).

## Technical
Fully **static**: `index.html` (deck.gl/WebGL via CDN) + binary data (`data/`) +
slide tiles (`tiles/`). No backend — hostable on GitHub Pages / Netlify.
