**🌟 What is InternScout AI?**

**InternScout AI** is an intelligent browser automation agent that
eliminates the manual grind of searching for internships. College
students often waste dozens of hours scrolling through redundant
listings across multiple platforms. With InternScout AI, you enter your
skills and preferences once, and an autonomous AI agent:

-   🌐 Br**owses internship platforms (**LinkedIn, AngelList/Wellfound,
    > Internshala, Unstop, Indeed, Glassdoor).

    > 🔍 Rea**ds live, real-world job listings vi**a browser automation.

    > 📊 Anal**yzes eligibility and requirements in** real time.

    > ✓ Comp**ares opportunities against your candidate profile.**

    > **🎯** Ranks **matches on a 0--100 score usin**g a multi-factor
    > matching engine.

    > 📈 Explai**ns fit and pinpoints potential concerns for e**very
    > listing.

    > This p*roject uses actual browser automation powered by the
    > Browse**r Use SDK, supp**orted by a full fallback Demo Mode for
    > offline or keyless testing.*

*💡 Why* **This Matters**

**The Problem: Studen**ts manually comb through hundreds of job
postings, read long job descriptions, and guess whether their skill set
aligns---only to apply to positions they are ineligible for.

-   The Sol**ution: Intern**S**cout AI automa**tes the entire end-to-end
    > discovery and evaluation workflow, surfacing only high-fit,
    > qualified opportunities with actionable reasoning.

**🛠️ Architecture & Tech Stack**

┌─────────────────────────────────────────────────────────┐

│ Streamlit UI (app.py) │

└───────────────────────────┬─────────────────────────────┘

│ Inputs Preferences

▼

┌─────────────────────────────────────────────────────────┐

│ Browser Agent Orchestrator │

│ (agent.py) │

└─────────────┬─────────────────────────────┬─────────────┘

│ (Real Mode) │ (Demo Mode)

▼ ▼

┌──────────────────────────┐ ┌──────────────────────────┐

│ Browser Use SDK │ ┌ Built-in Mock Search │

│ (Live Web Scraping) │ │ (Demo Results) │

└─────────────┬────────────┘ └────────────┬─────────────┘

└──────────────┬──────────────┘

│ Structured Listings (JSON)

▼

┌─────────────────────────────────────────────────────────┐

│ Match & Scoring Engine │

│ (scoring.py) │

└───────────────────────────┬─────────────────────────────┘

│ Scored & Ranked Results

▼

┌─────────────────────────────────────────────────────────┐

│ Interactive Dashboard │

└─────────────────────────────────────────────────────────┘

Frontend**: Streaml**it (app.py) with custom CSS styling and real-time
execution logging.

-   **Browser Infrastructure: Browser** Use SDK (browser_use_sdk.v4 in
    > agent.py).

    > Data Sch**emas & Validation: Pydanti**c v2 (models.py).

    > Scoring **& Evaluation: Rules-d**riven weighted match algorithm
    > (scoring.py).

    > Envir**onment Management: python-**dotenv.

    > 🎯 Match **& Scoring Algorithm**

Each discovered internship is evaluated against the candidate profile
and awarded up to 100 point**s across 5** distinct categories:

￼

📂 Proj

  ----- ---------------- -------------------------------------------------
                         

                         

                         

                         

                         

                         
  ----- ---------------- -------------------------------------------------

**ct Structure**

**Plaintext**

.

├── app.py \# Main Streamlit web application & user interface

├── agent.py \# Browser Use SDK integration & fallback execution logic

├── models.py \# Pydantic data models (UserPreferences,
InternshipResult)

├── scoring.py \# Match score calculation & breakdown logic

├── .env.example \# Template for environment variables

└── README.md \# Project documentation

**🚀 Quickstart & Setup**

**1. Prerequisites**

**Python 3.10+ installed** on your machine.

-   A Browser Use **API Key (optional** if running in Demo Mode).

**2. Clone & Install Dependencies**

**Bash**

\# Clone the repository

git clone
\[https://github.com/your-username/InternScout-AI.git\](https://github.com/your-username/InternScout-AI.git)

cd InternScout-AI

\# Create and activate a virtual environment

python -m venv venv

source venv/bin/activate \# On Windows: venv\\Scripts\\activate

\# Install required packages

pip install streamlit pydantic python-dotenv browser-use-sdk

**3. Environment Configuration**

Create a .env file in the project root:

Bash

\# Set your Browser Use API Key for live browser automation

BROWSER_USE_API_KEY=your_browser_use_api_key_here

\# Toggle Demo Mode (set to \'true\' to use built-in mock data,
\'false\' for real scraping)

DEMO_MODE=false

**🏃 Running the Application**

Launch the Streamlit web dashboard by executing:

Bash

streamlit run app.py

Open your browser to http://localhost:8501 to view the UI.

**🎭 Operating Modes**

1.  **Real Agent Mode (DEMO_MODE=false & valid API Key):**

2.  **The Browser** Use SDK launches an autonomous browser run.

    -   Navigates live job boards, extracts structured data, and parses
        > JSON output directly into Pydantic models.

3.  **Demo Mode (DEMO_MODE=true or missing API Key):**

4.  **Executes wit**hout invoking live web drivers or incurring API
    > charges.

    -   Uses realistic mock data to showcase match scoring, reasoning,
        > UI cards, and progress activity logs.

**🛡️ Human-in-the-Loop & Responsible Agent Use**

InternScout AI strictly respects platform terms and candidate safety:

No Autonomous **Submissions: The agent gat**hers, structures, and ranks
listings, but never submits **appli**cations autonomously.

-   Human Approval**: Candidates cl**ick 🔗 Apply Now to **navigate to**
    > the official listing URL and complete applications manually.

**🗺️ Future Expansion**

-   \[ \] Automatic cover letter drafting tailored to match reasons.

    > \[ \] Profile resume parsing (.pdf/.docx) to auto-populate skills.

    > \[ \] Application status tracking dashboard (Saved, Applied,
    > Interviewing).

    > \[ \] Webhook alerts for high-score listings (≥ 90%).
