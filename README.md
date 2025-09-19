# Power BI Sales Analysis — Global Superstore

**Goal:** Diagnose sales and profitability across categories, customers, and regions using Global Superstore sample data.

## Demo
- Screenshot overview: `docs/screenshots/01_overview.png`
- Profitability deep-dive: `docs/screenshots/02_profitability.png`
- Model diagram: `docs/model-diagram.png`
  
![Dashboard Demo](docs/screenshots/Demo.gif)

This short demo showcases key interactive features of the Power BI dashboard:
- Slicer selection for dynamic filtering
- Bookmark navigation to toggle views
- Tooltip hover for contextual insights
Designed for clarity, speed, and self-service exploration—ideal for portfolio presentation and interview readiness.


## How to run
1. Download/clone this repository.
2. Ensure `data/Global_Superstore.xlsx` is present (or update the data connection in the PBIX).
3. Open `pbix/Sales_Analysis_Global_Superstore.pbix` in Power BI Desktop and **Refresh**.

## Highlights
- Executive KPIs (Sales, Profit, Profit Margin, Orders)
- Time intelligence: YoY and YTD
- Profitability deep-dive: Waterfall, Scatter (Sales vs Margin)
- Customer analysis: Pareto, Drill-through, Return rate
- UX: Field parameter metric switcher, Bookmarks, Custom tooltips, Mobile layout

## Repo structure
powerbi-sales-analysis-portfolio/
├─ data/ (raw dataset or link to dataset)
├─ pbix/Sales_Analysis_Global_Superstore.pbix
├─ docs/screenshots/
├─ measures.md
├─ README.md
└─ LICENSE

## Key Insights
1.Technology leads sales but not profit equally
Technology contributes the largest share of total sales, yet Office Supplies often delivers stronger profit margins — highlighting margin vs. revenue trade-offs.

2.Customer concentration (Pareto effect)
Roughly 20% of customers contribute ~80% of total sales, underscoring the importance of high-value customers and the need for targeted retention strategies.

3.Regional profitability imbalance
APAC and EU regions show strong sales growth, but profitability varies widely by sub-category — some product lines in high-growth markets generate very low or even negative margins.

## Model diagram:
 “Star schema: Orders (fact) linked to Date & People (dimensions)”.



## DAX & Model
See `measures.md` for all DAX measures and short explanations.  
See `docs/model-diagram.png` for the star schema.

## Data Source
Global Superstore sample dataset (Kaggle): [https://www.kaggle.com/...](https://www.kaggle.com/datasets/shekpaul/global-superstore?utm_source=chatgpt.com) (link to dataset)

## License
This project is released under the MIT License — see `LICENSE`.
