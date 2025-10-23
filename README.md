# BigQuery Metrics AppsFlyer AI Agent

AI-powered analytics agent for querying AppsFlyer performance data in BigQuery using natural language. 
Converts plain English questions into optimized SQL queries and computes metrics based on official AppsFlyer documentation.

> Think of it as a conversational analyst for your AppsFlyer + BigQuery data.

## 4. How It Works (Flow)
1. User asks: "Compare D7 ROAS for Meta vs Google last month."  
2. Intent classification (period_compare + roas_cohort)  
3. Schema context loaded (table + column manifest)  
4. LLM drafts SQL (safe template-driven)  
5. Validation: static rules + SQL parsing + dry-run cost  
6. BigQuery execution (SELECT-only)  
7. KPI enrichment (ROAS deltas, rankings)  
8. Summarization (plain-English narrative)  
9. Visualization spec assembly  
10. Response JSON with follow-up suggestions

## 5. Architecture
```
User -> Chat/API -> Orchestrator
  -> Intent + SQL Draft (LLM)
  -> SQL Validator (rules + AST + cost dry-run)
  -> BigQuery Runner
  -> Metrics Post-Processor
  -> Insight & Visualization Generator (LLM)
```

## 8. Quick Start
Prerequisites: GCP project, BigQuery dataset with AppsFlyer exports, Python 3.10+, LLM API key.

Environment (.env example):
```
GCP_PROJECT_ID=your-gcp-project
BQ_DATASET=your-gcp-dataset
GOOGLE_APPLICATION_CREDENTIALS=/path/to/service_account.json
```

Local setup:
```bash
git clone https://github.com/rivka14/bigquery-metrics-appsflyer-ai-agent.git
cd bigquery-metrics-appsflyer-ai-agent
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```


