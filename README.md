# SME Internationalization

**Author:** Sotirios Panousis
**Course:** ExInt II — Research Designs in SME Research
**Semester:** SS 2026
**University:** WU Vienna

## Research Question

Does higher R&D intensity lead to greater international engagement
among small and medium-sized enterprises (SMEs)?

## Hypotheses

- **H1:** SMEs with higher R&D intensity (R&D expenses / sales)
  exhibit a higher share of foreign sales.

## Theoretical Background

Innovation creates firm-specific technological advantages that are
particularly valuable in international markets. High R&D intensity
signals product or process innovation, which helps SMEs overcome the
liability of foreignness (Zaheer, 1995) and amortize fixed R&D costs
across larger markets. The internationalization process model
(Johanson & Vahlne, 1977) and SME-specific evidence (Lu & Beamish,
2001) suggest that innovative SMEs are more likely to engage in
foreign markets.

## Project Structure

- `code/` — Python scripts for data pipeline
- `data/raw/` — Raw data from WRDS (not committed to Git)
- `data/processed/` — Cleaned datasets
- `output/tables/` — Regression tables and descriptives
- `output/figures/` — Plots and visualizations
- `references/` — Bibliography (`library.bib`)

## Reproducibility

To reproduce this project:

1. Clone the repository
2. Create a virtual environment: `python -m venv .venv`
3. Activate it: `source .venv/bin/activate` (Mac/Linux) or `.venv\Scripts\activate` (Windows)
4. Install dependencies: `pip install -r requirements.txt`
5. Add your WRDS credentials to `.env`
6. Run the pipeline: `task all`