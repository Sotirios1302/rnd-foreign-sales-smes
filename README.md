# R&D Intensity and SME Growth

**Author:** Sotirios Ioannis Konstadinos
**Course:** ExInt II — Research Designs in SME Research
**Semester:** SS 2026
**University:** WU Vienna

## Research Question

Does R&D intensity affect firm performance (Return on Assets) among
European small and medium-sized enterprises (SMEs), and does firm size
moderate this relationship?


## Hypotheses

- **H1:** R&D intensity negatively affects current-period Return on Assets
  (RoA) among SMEs. Under IFRS, R&D expenditures are largely expensed in
  the period they are incurred, mechanically reducing current earnings
  while benefits accrue with a lag.

- **H2:** Firm size positively moderates the R&D intensity–RoA
  relationship. Larger SMEs are better able to absorb the short-run
  expensing cost of R&D through scale, internal financing, and economies
  of scope, attenuating the negative effect of R&D intensity on RoA.

## Theoretical Background

This study builds on three theoretical perspectives that explain why R&D
intensity may translate into faster revenue growth for small and
medium-sized enterprises (SMEs).

**1. Resource-Based View — Knowledge as a Competitive Advantage.**
From a resource-based perspective, R&D investments generate firm-specific,
intangible knowledge assets that are valuable, rare, and difficult to
imitate. These knowledge-based resources form the basis of sustainable
competitive advantage and translate into superior products, processes, and
ultimately market share gains that drive revenue growth.

**2. Schumpeterian Innovation and Market Expansion.**
According to Schumpeterian innovation theory, firms that invest in R&D
create new or improved products that displace existing offerings and
capture new customer segments. Kafouros, Buckley, Sharp, and Wang (2008)
demonstrate that innovation drives firm performance, but its benefits
depend on the firm's ability to commercialize knowledge across markets.

**3. Overcoming the Liability of Smallness.**
SMEs face structural disadvantages relative to larger incumbents,
including limited resources, visibility, and market power. Booltink and
Saka-Helmhout (2018) show that R&D intensity follows an inverted U-shape
with SME performance, suggesting that innovation enables SMEs to
differentiate and grow, though excessive R&D investment may strain
their limited resources. Tang, Tang, and Su (2019) further demonstrate
that R&D activity is positively associated with sales-based performance
indicators.

Taken together, these perspectives suggest that R&D-intensive SMEs are
better positioned to grow their revenues, as innovation generates the
differentiated offerings and competitive advantages required to expand
market share.

### Summary of Key References

| Reference | Theoretical Lens | Key Finding | Relevance to H1 |
|---|---|---|---|
| Kafouros et al. (2008) | Innovation–performance link, appropriability | Innovation drives firm performance, conditioned on the firm's ability to commercialize knowledge | Supports the link between R&D effort and sales-based performance outcomes |
| Booltink & Saka-Helmhout (2018) | Resource-based view, SME-specific constraints | Inverted U-shape between R&D intensity and SME performance | Provides direct empirical evidence that R&D drives SME performance up to a critical threshold |
| Tang, Tang & Su (2019) | R&D investment, knowledge sourcing | R&D activity is positively associated with sales performance; effects vary with firm age and size | Justifies the use of sales-based growth as a relevant outcome variable |

Building on these arguments, this study expects a positive association
between R&D intensity and sales growth among SMEs.

## Variables

| Variable | Field(s) | Formula | Role |
|---|---|---|---|
| RoA | `ib`, `at` | `ib / at` | Dependent (Y) |
| R&D intensity | `xrd`, `at` | `xrd.fillna(0) / at` | Independent (X) |
| R&D × Size | — | `rd_intensity × ln_at` | H2 interaction |
| Firm size | `at` | `log(at)` | Moderator + control |
| Leverage | `dltt`, `at` | `dltt / at` | Control |
| CAPX intensity | `capx`, `at` | `capx / at` | Control |
| Cash ratio | `che`, `at` | `che / at` | Control |

### Sample filters

- Data quality: `at > 0.1`, `sale > 0`, `seq > 0`
- Remove micro-firms: `at >= 1` (firms with ≥ €1m assets only)
- EU SME filter: `emp < 0.25` (less than 250 employees) **OR** `at <= 43` (assets ≤ €43m)
- Minimum 3 observations per firm (for fixed-effects estimation)

Variables `roa`, `rd_intensity`, `leverage`, `capx_intensity`, `cash_ratio` are winsorized at the 1st and 99th percentile to mitigate the impact of outliers. `ln_at` is **not** winsorized (log-transformation already handles skew).

## Data

| Item | Detail |
|---|---|
| Source | WRDS / Compustat Global |
| Table | comp_global_daily.g_funda |
| Pull date | 2026-05-30 |
| Pull filters | datafmt=HIST_STD, indfmt=INDL, popsrc=I, consol=C |
| Sample filter | Reporting currency = EUR |
| Fiscal years | 2015–2024 |
| Raw rows pulled | 338,465 |
| Clean panel rows | 26,090 firm-years |
| Unique firms | 3,430 |
| Countries | 46 (top: FRA, DEU, ITA, FIN, ESP, GRC, NLD, BEL, AUT, PRT) |
| Total columns | 444 |
| License | WRDS subscriber agreement |

### Completeness of key variables (in the clean panel)

| Variable | Completeness |
|---|---|
| `at` (Total Assets) | 99.7% |
| `sale` (Sales) | 99.7% |
| `xrd` (R&D Expense) | 44.5% |
| `emp` (Employees) | 86.4% |
| `dltt` (Long-term Debt) | 99.5% |
| `seq` (Stockholders Equity) | 99.6% |
| `sich` (SIC Code) | ~90% |

*Note: Missing `xrd` is treated as zero (firms not reporting R&D are assumed to have no R&D activity).*

## Project Structure

- `code/` — Python scripts for the data pipeline
- `data/raw/` — Raw data from WRDS (not committed to Git)
- `data/processed/` — Cleaned firm-year panel
- `output/tables/` — Regression tables and descriptives
- `output/figures/` — Plots and visualizations
- `references/` — Bibliography (`Meine Bibliothek.bib`)

## Reproducibility

To reproduce this project:

1. Clone the repository
2. Create a virtual environment: `python -m venv .venv`
3. Activate it: `source .venv/bin/activate` (Mac/Linux) or `.venv\Scripts\activate` (Windows)
4. Install dependencies: `pip install -r requirements.txt`
5. Add your WRDS credentials to `.env`
6. Run the pipeline: `task all`