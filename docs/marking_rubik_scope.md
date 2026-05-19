# Section A Working Draft (30 Marks) - Oladayo Folorunso

## 1) Executive Summary (10 marks)

### Business context
I lead finance in an MEP construction context where project profitability is highly exposed to cost overruns, delay-related financing pressure, and variation-order volatility. Improving forecast quality and margin control is central to strategic and working-capital performance.

### Research question
What operational and commercial factors most strongly determine project profitability, and how can management intervene to improve financial outcomes?

### Three key findings (insert final numbers)
1. [Profit margin differential by project type/client type]
2. [Impact of payment/procurement delay on margin]
3. [Regression coefficient on strongest profitability driver]

### One recommendation
[Targeted project governance/pricing intervention] is expected to improve median project margin by [X percentage points] within [time horizon].

## 2) Professional Disclosure (10 marks)

**Job title:** Head of Finance (CFO-designate)
**Organisation sector:** MEP (Mechanical, Electrical, and Plumbing) construction — capital project delivery and contract management

### Technique 1 — Exploratory Data Analysis
As Head of Finance in a project-based business, every quarterly board review begins with a portfolio-level assessment: are margins holding, which project types are over-budget, and where are cash flow pressures emerging? The dataset contains 106 project-month records spanning April 2016 to January 2026 across multiple project types and client categories. Before building any regression or test, I need to profile the distribution of `Profit Margin %`, identify whether cost overruns are concentrated in specific `Project Type` or `Client Type` categories, and flag any extreme outliers in `Contract Value` or `Variation Order Value` that would distort downstream models. This step replicates the financial health-check I conduct each month before the management accounts are distributed.

**Alternative considered:** Proceeding directly to regression with all 106 observations without profiling. Rejected because undetected outliers (e.g., one very large government contract with atypical terms) would bias regression coefficients and mislead strategic conclusions.

**Limitation:** EDA is descriptive. It identifies what the data looks like but cannot confirm whether observed patterns are statistically reliable.

### Technique 2 — Data Visualization
Construction finance reporting is inherently visual. Board members and project directors expect margin trend charts, waterfall plots showing budget-vs-actual cost movement, and heat maps of delay days by project type and client category. Visualizing the MEP project dataset allows me to communicate profitability patterns in the format that the commercial and executive teams respond to — particularly for variation order trends and payment delay clusters that explain working capital pressure. The charts produced here will feed directly into the next board finance presentation.

**Alternative considered:** Presenting all findings as tabular summaries. Rejected because tables obscure cross-group and time-trend patterns that are critical for project portfolio decisions.

**Limitation:** Without accompanying statistical tests, visual differences between groups can be misleading. All visual findings are followed by formal hypothesis tests.

### Technique 3 — Hypothesis Testing
A recurring strategic question at the company is whether government contracts (`Client Type`) are structurally less profitable than private-sector engagements, and whether MEP projects differ in margin from civil or fit-out work. If true, this is a pricing and tendering policy issue. I need formal hypothesis tests — ANOVA across project types, t-tests across client categories — to determine whether the observed differences are statistically significant before adjusting the bid strategy. Anecdotal observations from project managers are insufficient for a finance-led recommendation.

**Alternative considered:** Reporting only descriptive mean differences by group. Rejected because management decisions based on chance fluctuations would waste resources and damage credibility.

**Limitation:** ANOVA assumes approximate normality within groups and similar group variances. With 106 records split across 3–5 categories, some groups may have fewer than 30 observations; Welch correction and Kruskal-Wallis non-parametric alternative will be applied where needed.

### Technique 4 — Correlation Analysis
My hypothesis before the analysis is that `Payment Delays Days` and `Procurement Delay Days` are the primary destroyers of project margin. Correlation analysis formally maps the dependency structure across all 12 numeric and semi-numeric variables before I build a regression model. This prevents me from entering collinear predictors into the regression (e.g., `Budgeted Cost` and `Contract Value` are likely highly correlated) and focuses the model on variables with genuine independent explanatory power.

**Alternative considered:** Running a full regression with all variables simultaneously without prior screening. Rejected because this approach risks multicollinearity, inflated standard errors, and unstable coefficients.

**Limitation:** Correlation is not causation. A strong correlation between payment delay and margin decline may reflect underlying project complexity rather than a direct financing-cost mechanism.

### Technique 5 — Multiple Regression
The business purpose of this analysis is to produce a pre-contract profitability estimator. If I know the `Contract Value`, `Project Type`, and `Client Type` at the bid stage, the regression model outputs an expected `Profit Margin %` with confidence bounds. This supports three specific decisions: (1) setting project-level contingency budgets, (2) pricing negotiation with clients where margins are expected to be thin, and (3) flagging bids that are structurally below the company's minimum acceptable margin threshold before resources are committed.

**Alternative considered:** Random forest regression for non-linear interactions. While potentially more accurate, random forest outputs are not interpretable at the coefficient level and would not support the pricing conversation with clients and the board.

**Limitation:** With 106 observations and up to 6 predictors, the regression is adequately powered but at the lower end of ideal. Results should be interpreted with appropriate caution for generalization.

---

## 3) Data Collection & Sampling (10 marks)

- **Source system:** Internal project management and cost-monitoring system, MEP construction company
- **Primary dataset used:**
  - `MEP_construction_company_projs.csv` — 106 project-month records; 12 variables: Project Code, Month, Project Type, Client Type, Contract Value, Budgeted Cost, Actual Cost, Profit Margin %, Payment Delays Days, Variation Order Value, Procurement Delay Days, Completion %
- **Collection method:** Records were extracted from the company's internal project cost-monitoring database and contract management system. Each row represents one project observed in one reporting month. Multi-month contracts appear as multiple rows, one per active month. Data was compiled and structured by the Head of Finance (the student) using internal reporting tools.
- **Period covered:** April 2016 – January 2026 (approximately 10 years of project history)
- **Sample frame:** All active and completed MEP projects logged in the system during the period. [CONFIRM before submission: Were any projects excluded — e.g., cancelled projects before commencement, projects below a minimum contract value threshold, or projects in preliminary mobilization stages? If so, document the exclusion criteria here.]
- **Sample size:** 106 records, 12 variables. Meets the CS1 minimum of 100 observations and 6 variables. The 10-year time span provides variation across construction cycles, economic conditions, regulatory changes, and contract types that a single-year dataset could not capture.
- **Statistical justification:** For ANOVA or t-tests across project type and client type groups, groups need approximately 30+ observations. With 106 total records and 3–5 categories, average group sizes are 20–35 — borderline adequate. Welch correction and non-parametric alternatives (Kruskal-Wallis) will be reported alongside parametric results. For regression with up to 6 predictors, the 10-per-predictor guideline is satisfied (106/6 ≈ 17.7). The 10-year time span improves the regression's ability to capture structural effects rather than period-specific noise.
- **Ethical notes and confidentiality:** The dataset is extracted from an employer's proprietary system and is used exclusively for this academic assessment at Lagos Business School. [CONFIRM: Have client and project names been anonymised? Verify that `Project Code` values are coded identifiers and not actual client names. If not, apply coding before RPubs publication.] No employee payroll or personally identifiable data is included. [CONFIRM: Obtain and state explicit academic-use approval from your line manager, Finance Director, or equivalent authorising officer: "Use of this dataset was approved by [Name, Title] at [Company] for the purposes of this academic assessment."]
