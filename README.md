# Lica Research Scientist Take-Home Assignment
**Task:** Image → SVG Generation
**Dataset:** [SVG-Stack](https://huggingface.co/datasets/starvector/svg-stack)

## Understanding the Data
- Dataset has ~2 million SVG files (mostly icons/logos).
- Preprocessed: cleaned metadata, normalized coordinates, rasterized to 256x256 PNG.
- Small sample (200) used for demo.

## Method
### B0 – Classical Vectorization (Potrace)
Converts PNG→PBM→SVG. Fast but messy paths.

### B1 – Neural Baseline (StarVector-1B)
Model: `starvector/starvector-1b-im2svg` from Hugging Face. Zero-shot SVG generation.

## Evaluation
Metrics used:
- LPIPS, SSIM, PSNR for visual.
- Chamfer distance for geometry.
- SVG length, element counts for structure.

## Results
- StarVector produced cleaner, shorter SVGs.
- Potrace bloated path counts.

## Future Work
- Grammar-aware decoding.
- DiffVG fine-tuning.
- Reward simpler SVGs.
- Extend to text→SVG with `text2svg-stack`.

## Folder Layout
Lica-Research-Assignment/
├── README.md
├── lica_notebook.ipynb
├── samples/
│   ├── gt_svg/
│   └── gt_png/
├── runs/
│   ├── B0_svg/
│   ├── B1_svg/
│   └── metrics.csv
└── requirements.txt
