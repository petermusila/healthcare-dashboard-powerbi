# 🏥 Healthcare Financial & Provider Performance Dashboard

## The Story Behind This Dashboard

Healthcare leaders struggle with static Excel reports that don't answer questions in real-time.

I built this dashboard to solve one problem: **help institutions track provider performance and financial health instantly.**

The dashboard doesn't just show numbers — it **tells you where to focus.**

## What Makes This Dashboard Different

### 💡 Dynamic Insights Page
When users filter by provider, department, or date, the dashboard automatically generates:
- Executive summaries
- Financial highlights
- Provider performance rankings
- Areas of concern
- Actionable recommendations

**No more manual interpretation.**

---

## Key Features

### 📊 30+ Key Performance Indicators

| Category | Metrics |
|----------|---------|
| Financial | Total Revenue, YTD Revenue, Avg Cost per Visit, Out-of-Pocket |
| Provider | Revenue per Provider, Utilization %, Satisfaction Score |
| Retention | Patient Retention Rate, Returning Patients, New Patient Rate |
| Operational | Provider Workload Balance, Revenue Gap Ratio |

### 📈 3 Interactive Pages

| Page | Content |
|------|---------|
| Financial Overview | Revenue trends, service type breakdown, payment status |
| Provider Insights | Provider ranking, utilization, satisfaction matrix |
| Dynamic Insights | Auto-generated commentary based on filters |

### 🔧 Technical Implementation
- **DAX Measures:** 30+ custom measures
- **Data Model:** Star schema with 8 tables
- **Time Intelligence:** YTD, MTD calculations
- **Dynamic Text:** Auto-generated insights using CONCATENATEX, TOPN, SELECTEDVALUE

---

## Data Model
┌─────────────┐ ┌──────────────┐
│ Calendar │ │ Patients │
└─────────────┘ └──────────────┘
│ │
▼ ▼
┌─────────────┐ ┌──────────────┐
│ Visits │────▶│ Providers │
│ (Fact) │ └──────────────┘
└─────────────┘
│
▼
┌─────────────┐ ┌──────────────┐ ┌──────────────┐
│ Departments │ │ Diagnoses │ │ Procedures │
└─────────────┘ └──────────────┘ └──────────────┘
--

## Screenshots

### Page 1: Financial Overview
![Financial Overview](<img width="1268" height="730" alt="page1_financial_overview" src="https://github.com/user-attachments/assets/7ab90053-c16c-462b-b430-a1ad2411f4b2" />
)

### Page 2: Provider Insights
![Provider Insights](<img width="1920" height="1080" alt="page2_provider_insights" src="https://github.com/user-attachments/assets/6175d1bf-76ae-49cf-8e6f-28c984e51af3" />)

### Page 3: Dynamic Insights
![Dynamic Insights](<img width="1920" height="1080" alt="page3_dynamic_insights" src="https://github.com/user-attachments/assets/4056ab5a-3165-41f2-bb2b-1c53cb1a3e6c" />)

---

## DAX Highlights

```dax
// Provider Revenue Gap
Provider Revenue Gap Ratio = 
VAR TopRevenue = MAXX(ALLSELECTED(providers[Provider Name]), [Total Revenue])
VAR BottomRevenue = MINX(ALLSELECTED(providers[Provider Name]), [Total Revenue])
RETURN DIVIDE(TopRevenue, BottomRevenue)

// Patient Retention Rate
Patient Retention Rate = DIVIDE([Returning Patients], [Total Patients])

// Provider Workload Balance
Provider Workload Balance = 
AVERAGEX(VALUES(providers[Provider Name]),
    DIVIDE([Total Visits], MAXX(ALLSELECTED(providers[Provider Name]), [Total Visits]))
)
