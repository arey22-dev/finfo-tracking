# finfo-tracking
- Tracking financial returns related to market sentiment

# basic-question
- Focusing on investiment to next-day/week performance, how long does sentiment take to correlate with price movements? Is there any correlation?

# the-idea
- Focus on specific time windows (sentiment vs. next week performance)
- Include sentiment lag analysis
- Volatility analysis compared to market sentiment
- Sector-specific sentiment vs sector ETF performance

# basic-architecture
┌─────────────┐    ┌──────────────┐    ┌───────────┐    ┌──────────┐    ┌───────────┐
│ Data Sources│ -> │  Databricks  │ -> │Delta Lake │ -> │ Analysis │ -> │ Dashboard │
│(Reddit, APIs)│   │(Spark Stream)│    │ (Storage) │    │          │    │           │
└─────────────┘    └──────────────┘    └───────────┘    └──────────┘    └───────────┘
                            │
                            ▼
                   ┌─────────────────┐    ┌───────────────────┐    ┌─────────────┐
                   │ API Schedulers  │ -> │Data Quality Checks│ -> │  ML Models  │
                   │ (Airflow/DBRX)  │    │                   │    │ (Optional)  │
                   └─────────────────┘    └───────────────────┘    └─────────────┘
