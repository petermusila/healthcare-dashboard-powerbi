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

## Data Model
