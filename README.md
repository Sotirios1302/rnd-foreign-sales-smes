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

This study builds on three theoretical perspectives that explain
why R&D intensity may translate into greater international engagement
for small and medium-sized enterprises (SMEs).

**1. Resource-Based View (Knowledge as a Competitive Advantage).**
From a resource-based perspective, R&D investments generate firm-specific,
intangible knowledge assets that are valuable, rare, and difficult to
imitate. Such assets form the basis of sustainable competitive advantage
and are particularly transferable across borders, since technological
knowledge is less context-dependent than marketing or relational assets.

**2. Cost Amortization and Appropriability.**
R&D entails high fixed and largely sunk costs. International expansion
allows innovative SMEs to amortize these costs over larger markets and
fully appropriate the returns from their innovations. Kafouros, Buckley,
Sharp, and Wang (2008) argue that firms can only fully realize the
performance benefits of innovation when they reach a sufficient
internationalization level — innovation and internationalization act as
complements rather than substitutes.

**3. Overcoming the Liability of Smallness.**
SMEs face structural disadvantages in foreign markets due to limited
resources and visibility. Booltink and Saka-Helmhout (2018) show that
R&D intensity follows an inverted U-shape with SME performance, but that
internationalization moderates this relationship positively once R&D
exceeds a critical threshold. Innovation thus serves as a mechanism for
SMEs to compete against larger incumbents abroad. Tang, Tang, and Su
(2019) further demonstrate that R&D activity is positively associated
with export performance, even when its direct effect on profitability
is mixed.

Taken together, these perspectives suggest that R&D-intensive SMEs are
both *able* to internationalize (because they possess transferable
technological knowledge) and *motivated* to internationalize (to
amortize R&D costs and capture full innovation returns).

### Summary of Key References

| Reference | Theoretical Lens | Key Finding | Relevance to H1 |
|---|---|---|---|
| Kafouros et al. (2008) | Innovation–performance link, appropriability | Internationalization moderates the innovation–performance relationship; benefits of R&D only materialize at sufficient international scope | Supports the link between R&D effort and international expansion as mutually reinforcing |
| Booltink & Saka-Helmhout (2018) | Resource-based view, SME-specific constraints | Inverted U-shape between R&D intensity and SME performance; internationalization strengthens the R&D–performance link beyond a critical R&D threshold | Provides direct empirical evidence that R&D-intensive SMEs benefit from going international |
| Tang, Tang & Su (2019) | R&D internationalization, knowledge sourcing | R&D internationalization is positively associated with foreign sales (export performance); effects vary with firm age and size | Justifies the use of the foreign sales share as the dependent variable |

Building on these arguments, this study expects a positive association
between R&D intensity and the share of foreign sales among SMEs.

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