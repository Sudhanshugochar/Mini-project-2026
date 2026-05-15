# 🤖 Mini-project-2026: AI-Powered GitHub Self-Analysis Dashboard

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python Version">
  <img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" alt="Ollama">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License">
</p>

---

## 🚀 Comprehensive Overview

The **AI-Powered GitHub Self-Analysis Dashboard** is an advanced, interactive web application designed to give developers deep, privacy-respecting insights into their GitHub footprint.

While standard GitHub profiles show basic commit graphs and star counts, this project bridges the gap between **Traditional Data Science** and **Generative AI**. By leveraging local Large Language Models (LLMs) via Ollama, the application processes sensitive repository data directly on your hardware—ensuring **zero data leakage to cloud APIs**. It evaluates coding habits, extracts technical skills from project documentation, performs sentiment analysis on commit histories, and forecasts future developer activity.

---

## ✨ Deep-Dive into Features

### 1. 🧠 Local LLM Analysis (Privacy-First AI)
We utilize Ollama to run models like `llama3.2:1b` and `mistral` locally. This powers:
* **Commit Sentiment Analysis:** Analyzes the emotional tone of your commit messages (e.g., frustration during bug fixing vs. excitement during feature launches).
* **Automated Skill Extraction:** Reads through your repository `README.md` files and accurately extracts core technologies, frameworks, and skills demonstrated.
* **AI-Driven Code/README Audits:** Provides actionable feedback on how to improve your project documentation for better open-source collaboration.
* **Developer Persona Generation:** Generates a fun, personalized title (e.g., *"The Midnight Pythonista"*) based on your coding hours and preferred languages.

### 2. 📊 Traditional Data Science & Machine Learning
* **Repository Clustering (K-Means):** Groups your repositories into clusters based on engagement metrics like Stars, Forks, and Repository Size. This helps visually identify your most impactful projects versus experimental sandboxes.
* **Activity Forecasting (Time-Series):** Uses historical commit timestamp data to forecast your future coding activity trends, helping you maintain streaks and plan workloads.
* **Statistical Profiling:** Calculates your longest coding streak, peak activity months, and health grades (A-D) for individual repositories.

### 3. 🎨 Interactive UI & Automation
* **Streamlit & Plotly:** A sleek, dark-mode optimized dashboard featuring interactive radar charts, scatter plots, and time-series graphs.
* **Internationalization (i18n):** Multi-language support (**English, Spanish, French, German**) allowing a global audience to analyze their profiles.
* **One-Click Resume Generator:** Dynamically aggregates your GitHub stats, top languages, and AI-extracted skills into a cleanly formatted, downloadable PDF resume.

---

## 🏗️ System Architecture & Workflow

```text
       ┌──────────┐
       │  👤 User │
       └────┬─────┘
            │ Inputs Credentials
            ▼
┌────────────────────────────────────────┐
│      💻 Streamlit Dashboard UI         │
└───────────────────┬────────────────────┘
                    │ Triggers Data Fetch
                    ▼
┌────────────────────────────────────────┐
│      🌐 GitHubFetcher Module           │
│  (Handles API, Pagination & Limits)    │
└───────────────────┬────────────────────┘
                    │ Writes Data Cache
                    ▼
┌────────────────────────────────────────┐
│     📂 data/raw_data.json Storage     │
└───────────┬──────────────────────┬─────┘
            │                      │
            │ Quantitative Data    │ Unstructured Text
            ▼                      ▼
┌───────────────────────┐  ┌───────────────────────┐
│   📊 TraditionalDS    │  │   🤖 OllamaAnalyzer   │
│ • K-Means Clustering  │  │ • Sentiment Engine    │
│ • Activity Forecast   │  │ • Skill Extractor     │
└───────────┬───────────┘  └───────────┬───────────┘
            │                          │
            └───────────┬──────────────┘
                        │ Injects Output Metrics
                        ▼
┌────────────────────────────────────────┐
│      🎨 Streamlit View Elements        │
│  • Interactive Plotly Engine Charts    │
│  • 📄 PDF Resume Engine Artifacts      │
└────────────────────────────────────────┘

* **Data Ingestion:** The `GitHubFetcher` module securely connects to the GitHub API, handling pagination and rate limits to extract User Profiles, Repositories, Commits, and READMEs.
* **Processing Pipeline:**
  * Quantitative data flows into the `TraditionalAnalyzer` (Pandas, Scikit-learn) for clustering and statistical modeling.
  * Unstructured text (commits, READMEs) flows into the `OllamaAnalyzer` for Natural Language Processing.
* **Presentation Layer:** The Streamlit `dashboard.py` merges these insights into a unified, user-friendly graphical interface.

---

## 🛠️ Prerequisites

Ensure your system meets the following requirements before installation:
* **Python:** Version 3.10 or higher.
* **Git:** For version control and cloning.
* **Ollama:** Installed and running as a background service. Download from [Ollama.com](https://ollama.com).

Pull the required models via your terminal before starting the app:
```bash
ollama pull llama3.2:1b
ollama pull mistral

## 📦 Step-by-Step Installation
**1. Clone the repository**
git clone [https://github.com/Sudhanshugochar/Mini-project-2026.git](https://github.com/Sudhanshugochar/Mini-project-2026.git)
cd Mini-project-2026
**2. Create and activate a virtual environment**
# For Windows
python -m venv venv
venv\Scripts\activate

# For macOS/Linux
python -m venv venv
source venv/bin/activate
**3. Install required Python packages**
pip install -r requirements.txt
**4. Configure Environment Variables (Optional but Recommended)**
GITHUB_USERNAME=your_github_username
GITHUB_TOKEN=your_personal_access_token

--

#📂 Detailed Project Structure
Mini-project-2026/
│
├── dashboard.py               # Main entry point for the Streamlit UI
├── requirements.txt           # Python dependencies
├── .env                       # Environment variables (Tokens/Usernames)
├── README.md                  # Project documentation
│
├── src/                       # Core Logic Modules
│   ├── data_collection.py     # GitHub API wrapper, rate limit handler
│   ├── traditional_ds.py      # Pandas logic, Clustering, Forecasting
│   ├── llm_analysis.py        # Ollama API integration & prompt engineering
│   └── resume_builder.py      # PDF generation logic (FPDF/ReportLab)
│
├── locales/                   # Internationalization (i18n) files
│   ├── en.json                # English translations
│   ├── es.json                # Spanish translations
│   └── ...                    
│
├── data/                      # Local cache for fetched JSON data (gitignored)
│   └── raw_data.json          
│
└── tests/                     # Unit and integration tests
    ├── test_resume.py
    └── verify_system.py

🔮 Future Scope / Roadmap
[1] Multi-user Comparison: Compare two GitHub profiles side-by-side.

[2] Code Complexity Analysis: Analyze the Cyclomatic Complexity of specific repositories.

[3] More LLM Integration: Support for DeepSeek or local Llama 3 8B for deeper code reviews.

[4] Cloud Deployment: Dockerize the application for easy deployment on AWS/Render (with API-based LLM fallbacks).

🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page if you want to contribute.

📄 License
This project is open-source and available under the MIT License.



