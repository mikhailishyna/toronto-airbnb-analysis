# Toronto Airbnb Market Analysis

Exploratory data analysis of Toronto's short-term rental market using Inside Airbnb data from **July and October 2025** (~31,000 listings across 140 neighbourhoods).

**[→ View Tableau Dashboards](https://public.tableau.com/views/Final_Project_Mikhailishyna/Chart5RegulatoryStatusMarketPerformanceComparison)**

> *Group project. My sections: Guest Experience & Reviews · Geography & Regulation*

---

## Business Questions Answered

| Section | Business Question |
|---------|------------------|
| **Guest Experience & Reviews** | What does review data reveal about guest satisfaction and seasonal demand? |
| **Geography & Regulation** | How is the rental market distributed across the city, and what does the regulatory picture look like? |
| **Price & Value** | Is higher price justified by better guest experience? |
| **Host Profiles** | Who controls the market — individual hosts or property managers? |

---

## Data Preparation (Python)

**Source:** [Inside Airbnb](http://insideairbnb.com/) — Toronto listings and reviews, two scrapes (July & October 2025)

**Cleaning steps** (`data_preparation_Toronto.ipynb`):

- Merged two scrape periods into a single dataset (31,036 listings after deduplication)
- **Price**: stripped `$` and `,` with regex → converted to `float`
- **Host rates**: removed `%` characters → converted to decimal fractions
- **Bathrooms**: extracted numeric values from free-text field (`bathrooms_text`) using regex; handled `"half-bath"` as `0.5`
- Dropped stale records (`source == 'previous scrape'`) and irrelevant columns
- Exported cleaned CSV for Tableau

---

## Key Findings

**Seasonality & Reviews**
- Demand peaks in August–September every year; in 2025 review volume grew from ~6,000 (Feb) to 24,000+ (Aug)
- YoY review growth recovered strongly after COVID: +128% in 2022, +46.5% in 2023, +35.7% in 2024
- "Value" is the weakest review dimension market-wide — even in premium Waterfront Communities (4.93 location score vs 4.70 value score)

**Geography & Licensing**
- Waterfront Communities dominates with 5,278 listings (17% of market) — 5× more than any other neighbourhood
- Licensed listings significantly outperform unlicensed: **$165 vs $104** median price, **45% vs 34%** occupancy, **4.81 vs 4.47** review score
- Only ~57% of listings have a valid licence (43.1% of licence field is NULL)

**Price & Revenue**
- Highest median price: Bridle Path ($368/night), but highest estimated revenue: Waterfront ($19,980/month) — volume beats luxury pricing
- Listings above median price ($107) do **not** consistently receive higher ratings

**Host Structure**
- Market driven by small hosts (2–5 listings): 66% of hosts, 59% of listings
- Superhosts earn 2.8× more annually ($24,399 vs $8,789) despite only ~10% higher prices

---

## Recommendations

1. **Prioritise licensed listings** in search — they generate more revenue per booking and have higher guest trust
2. **Automated disclaimers** on listings in segments with systemically low scores (e.g. shared rooms: 4.30 avg)
3. **Off-season promotions** in tourist-heavy areas to stabilise October demand without dropping prices
4. **Optimise for occupancy**, not maximum price — Waterfront's revenue model (moderate price + high occupancy) outperforms Bridle Path's premium pricing

---

## Tech Stack

| Tool | Purpose |
|------|---------|
| **Python / pandas** | Data cleaning, merging, regex transformations |
| **Google Colab** | Notebook environment |
| **Tableau Public** | Interactive dashboards and analysis |

---

*Data source: [Inside Airbnb](http://insideairbnb.com/get-the-data/) — publicly available under Creative Commons CC0 license*
