🤖 Mini-project-2026: AI-Powered GitHub Self-Analysis Dashboard

🚀 Comprehensive Overview
The AI-Powered GitHub Self-Analysis Dashboard is an advanced, interactive web application designed to give developers deep, privacy-respecting insights into their GitHub footprint.

While standard GitHub profiles show basic commit graphs and star counts, this project bridges the gap between Traditional Data Science and Generative AI. By leveraging local Large Language Models (LLMs) via Ollama, the application processes sensitive repository data directly on your hardware—ensuring zero data leakage to cloud APIs. It evaluates coding habits, extracts technical skills from project documentation, performs sentiment analysis on commit histories, and forecasts future developer activity.

✨ Deep-Dive into Features
1. 🧠 Local LLM Analysis (Privacy-First AI)
We utilize Ollama to run models like llama3.2:1b and mistral locally. This powers:

Commit Sentiment Analysis: Analyzes the emotional tone of your commit messages (e.g., frustration during bug fixing vs. excitement during feature launches).
Automated Skill Extraction: Reads through your repository README.md files and accurately extracts the core technologies, frameworks, and skills demonstrated.
AI-Driven Code/README Audits: Provides actionable feedback on how to improve your project documentation for better open-source collaboration.
Developer Persona Generation: Generates a fun, personalized title (e.g., "The Midnight Pythonista") based on your coding hours and preferred languages.
2. 📊 Traditional Data Science & Machine Learning
Repository Clustering (K-Means): Groups your repositories into clusters based on engagement metrics like Stars, Forks, and Repository Size. This helps visually identify your most impactful projects versus experimental sandboxes.
Activity Forecasting (Time-Series): Uses historical commit timestamp data to forecast your future coding activity trends, helping you maintain streaks and plan workloads.
Statistical Profiling: Calculates your longest coding streak, peak activity months, and health grades (A-D) for individual repositories.
3. 🎨 Interactive UI & Automation
Streamlit & Plotly: A sleek, dark-mode optimized dashboard featuring interactive radar charts, scatter plots, and time-series graphs.
Internationalization (i18n): Multi-language support (English, Spanish, French, German) allowing a global audience to analyze their profiles.
One-Click Resume Generator: Dynamically aggregates your GitHub stats, top languages, and AI-extracted skills into a cleanly formatted, downloadable PDF resume.
🏗️ System Architecture & Workflow
Data Ingestion: The GitHubFetcher module securely connects to the GitHub API, handling pagination and rate limits to extract User Profiles, Repositories, Commits, and READMEs.
Processing Pipeline:
Quantitative data flows into the TraditionalAnalyzer (Pandas, Scikit-learn) for clustering and statistical modeling.
Unstructured text (commits, READMEs) flows into the OllamaAnalyzer for Natural Language Processing.
Presentation Layer: The Streamlit dashboard.py merges these insights into a unified, user-friendly graphical interface.
🛠 Prerequisites
Ensure your system meets the following requirements before installation:

Python: Version 3.10 or higher.
Git: For version control and cloning.
Ollama: Installed and running as a background service.
Download from Ollama.com
Pull the required models via terminal:
bash
ollama pull llama3.2:1b
ollama pull mistral
📦 Step-by-Step Installation
1. Clone the repository:

bash
git clone https://github.com/Sudhanshugochar/Mini-project-2026.git
cd Mini-project-2026
2. Create and activate a virtual environment: Isolating dependencies ensures no conflicts with your system Python.

bash
# For Windows
python -m venv venv
venv\Scripts\activate
# For macOS/Linux
python -m venv venv
source venv/bin/activate
3. Install required Python packages:

bash
pip install -r requirements.txt
4. Configure Environment Variables (Optional but Recommended): To avoid GitHub API rate limits (60 requests/hr vs 5,000 requests/hr), set up a Personal Access Token.

Create a .env file in the root directory.
Add the following lines:
env
GITHUB_USERNAME=your_github_username
GITHUB_TOKEN=your_personal_access_token
🏃‍♂️ Usage Guide
Initialize Local AI: Open a terminal and ensure Ollama is running:

bash
ollama serve
Launch the Application: Open a new terminal, activate your virtual environment, and run:

bash
streamlit run dashboard.py
Explore Your Data:

Open the provided Localhost URL (usually http://localhost:8501).
Enter your GitHub credentials in the sidebar.
Explore the Overview, LLM Insights, GitHub Replay 2025, and generate your custom PDF Resume.
📂 Detailed Project Structure
text
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
├── tests/                     # Unit and integration tests
│   ├── test_resume.py
│   └── verify_system.py
🔮 Future Scope / Roadmap
 Multi-user Comparison: Compare two GitHub profiles side-by-side.
 Code Complexity Analysis: Analyze the Cyclomatic Complexity of specific repositories.
 More LLM Integration: Support for DeepSeek or local Llama 3 8B for deeper code reviews.
 Cloud Deployment: Dockerize the application for easy deployment on AWS/Render (with API-based LLM fallbacks).
🤝 Contributing
Contributions, issues, and feature requests are welcome! Feel free to check the issues page if you want to contribute.

📄 License
This project is open-source and available under the 

MIT License
