# InternScout AI

> **Your AI-powered internship scout — discover, analyze, and rank the opportunities that actually fit you.**

InternScout AI is an intelligent browser automation agent designed to eliminate the repetitive process of searching and evaluating internships across multiple platforms.

Instead of manually scrolling through hundreds of listings, reading lengthy job descriptions, and guessing whether an opportunity matches your profile, InternScout AI automates the discovery and evaluation process.

You provide your **skills, preferences, location, experience, and other requirements once**. The autonomous browser agent then discovers real internship listings, analyzes their requirements, compares them against your profile, and ranks each opportunity using a transparent **0–100 match score**.

---

## The Problem

Finding a suitable internship is surprisingly time-consuming.

Students often have to:

* Search across multiple internship and job platforms
* Open and read hundreds of individual listings
* Compare required skills with their own skill set
* Check eligibility requirements manually
* Identify whether a role matches their preferred location or work mode
* Remember which opportunities are actually worth applying to
* Repeat the same process every time they search

This results in **hours of repetitive work** and makes it easy to miss high-quality opportunities.

### The Core Problem

> **Students don't need more internship listings. They need the right internship listings.**

---

## The Solution

**InternScout AI** acts as an autonomous internship discovery and evaluation agent.

The user enters their candidate profile and preferences once. InternScout AI then:

1. 🌐 Searches internship platforms using browser automation
2. 🔍 Reads live internship listings
3. 📄 Extracts relevant job information
4. 🧠 Analyzes requirements and eligibility
5. 👤 Compares each opportunity against the candidate profile
6. 📊 Calculates a transparent match score from 0–100
7. 🎯 Ranks opportunities from strongest to weakest match
8. 💡 Explains why each opportunity is a good or weak fit
9. 🔗 Provides the official listing so the candidate can apply manually

The result is a focused shortlist of opportunities instead of an overwhelming list of job postings.

---

# Key Features

## 🌐 Multi-Platform Internship Discovery

InternScout AI is designed to discover opportunities across platforms such as:

* LinkedIn
* Wellfound (AngelList)
* Internshala
* Unstop
* Indeed
* Glassdoor

The browser agent can navigate real web pages and extract information from live listings.

---

## 🤖 Autonomous Browser Agent

The project uses the **Browser Use SDK** to perform browser-based discovery.

Instead of relying exclusively on static APIs or predefined datasets, the agent can:

* Navigate websites
* Search for relevant internship opportunities
* Read job descriptions
* Extract requirements
* Collect structured listing information
* Return the results in a machine-readable format

This allows InternScout AI to work with real-world web content.

---

## 🎯 Intelligent Candidate Matching

Every discovered internship is compared against the candidate's profile.

The matching engine considers multiple factors, including:

* Skills
* Experience
* Eligibility
* Location
* Work mode
* Role relevance
* Other candidate preferences

Each opportunity receives a **0–100 match score**.

### Example

```text
Internship: AI/ML Research Intern

Match Score: 91/100

Skills Match:       28/30
Experience Match:   18/20
Eligibility:        20/20
Preference Match:   15/15
Role Relevance:      10/15
                    --------
Total:               91/100
```

This makes the ranking explainable instead of treating the result as a mysterious AI-generated number.

---

# Match & Scoring Engine

InternScout AI uses a **rules-driven weighted scoring algorithm**.

The scoring engine evaluates each internship across five major categories and produces a final score out of 100.

### Scoring Pipeline

```text
Candidate Profile
       │
       ▼
Internship Listing
       │
       ▼
Requirement Extraction
       │
       ▼
Category-wise Comparison
       │
       ▼
Weighted Scoring
       │
       ▼
0–100 Match Score
       │
       ▼
Ranking + Explanation
```

The system also provides a breakdown of the score so users can understand **why** an opportunity received its ranking.

---

# Why InternScout AI?

| Traditional Internship Search            | InternScout AI                           |
| ---------------------------------------- | ---------------------------------------- |
| Manually search multiple websites        | Autonomous browser discovery             |
| Read every listing manually              | Automatically analyzes listings          |
| Guess whether you're eligible            | Explicit eligibility analysis            |
| Compare opportunities yourself           | Automatic candidate matching             |
| Difficult to prioritize results          | 0–100 match score                        |
| Generic search results                   | Personalized ranking                     |
| Repetitive and time-consuming            | Automated discovery workflow             |
| Application process mixed with discovery | Human remains in control of applications |

---

# Architecture

```text
┌─────────────────────────────────────────────────────┐
│                   Streamlit UI                      │
│                     app.py                          │
│                                                     │
│  Candidate Profile + Internship Preferences         │
└─────────────────────────┬───────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────┐
│             Browser Agent Orchestrator              │
│                     agent.py                        │
└─────────────────────────┬───────────────────────────┘
                          │
             ┌────────────┴────────────┐
             │                         │
             ▼                         ▼
┌─────────────────────────┐  ┌────────────────────────┐
│     Real Agent Mode     │  │      Demo Mode         │
│                         │  │                        │
│   Browser Use SDK       │  │   Built-in Mock Data   │
│   Live Web Discovery    │  │   Offline Testing      │
└────────────┬────────────┘  └───────────┬────────────┘
             │                           │
             └─────────────┬─────────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Structured Listings │
                │        JSON         │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │  Match & Scoring    │
                │      Engine         │
                │    scoring.py       │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Scored & Ranked     │
                │    Opportunities     │
                └──────────┬──────────┘
                           │
                           ▼
                ┌─────────────────────┐
                │ Interactive         │
                │ Dashboard           │
                └─────────────────────┘
```

---

# Tech Stack

| Component              | Technology      |
| ---------------------- | --------------- |
| Frontend / UI          | Streamlit       |
| Browser Automation     | Browser Use SDK |
| Data Validation        | Pydantic v2     |
| Matching Engine        | Python          |
| Environment Management | python-dotenv   |
| Data Exchange          | Structured JSON |
| Language               | Python 3.10+    |

---

# Project Structure

```text
InternScout-AI/
│
├── app.py                 # Main Streamlit application and UI
│
├── agent.py               # Browser Use SDK integration and
│                          # fallback execution logic
│
├── models.py              # Pydantic data models
│                          # UserPreferences and InternshipResult
│
├── scoring.py             # Match score calculation and
│                          # score breakdown logic
│
├── .env.example           # Environment variable template
│
└── README.md              # Project documentation
```

---

# How It Works

## Step 1 — Create Your Candidate Profile

The user provides information such as:

* Skills
* Preferred internship roles
* Experience level
* Preferred location
* Remote / hybrid / on-site preference
* Other relevant requirements

---

## Step 2 — Start the Scout

InternScout AI launches the browser agent.

In **Real Agent Mode**, the agent navigates internship platforms and searches for relevant opportunities.

---

## Step 3 — Extract Internship Data

The agent reads the available listings and extracts structured information such as:

* Internship title
* Company
* Location
* Work mode
* Required skills
* Experience requirements
* Eligibility requirements
* Internship description
* Official listing URL

---

## Step 4 — Evaluate the Opportunity

Each listing is passed to the matching engine.

The system compares the listing against the candidate profile and evaluates multiple factors.

---

## Step 5 — Generate the Match Score

The scoring engine produces a score between **0 and 100**.

Higher scores indicate stronger alignment with the candidate's profile and preferences.

---

## Step 6 — Explain the Result

Instead of simply displaying a number, InternScout AI explains:

### Why it matches

For example:

```text
✓ Strong Python match
✓ Strong machine learning relevance
✓ Meets experience requirement
✓ Remote work preference satisfied
```

### Potential concerns

For example:

```text
⚠ Requires TensorFlow experience
⚠ Internship is limited to candidates in a specific location
```

This allows the student to make an informed decision.

---

# Operating Modes

InternScout AI supports two execution modes.

## 1. Real Agent Mode

```text
DEMO_MODE=false
```

When a valid Browser Use API key is available, InternScout AI can launch the autonomous browser workflow.

The agent:

* Navigates live websites
* Searches for internships
* Reads real listings
* Extracts structured information
* Sends the results through the matching engine

This mode demonstrates the project's real browser automation capability.

---

## 2. Demo Mode

```text
DEMO_MODE=true
```

Demo Mode uses realistic built-in internship data instead of live browser automation.

This provides a reliable way to demonstrate the complete product without:

* Internet dependency
* Browser driver issues
* API keys
* API usage costs
* Live website changes

The same downstream pipeline is preserved:

```text
Mock Listings
      ↓
Structured Data
      ↓
Matching Engine
      ↓
Scoring
      ↓
Ranking
      ↓
Dashboard
```

This makes Demo Mode particularly useful for **hackathon presentations, judging, and offline testing**.

---

# Human-in-the-Loop & Responsible Agent Design

InternScout AI is designed to automate **discovery and evaluation**, not blindly automate applications.

### The agent does NOT:

* Submit applications automatically
* Enter sensitive information into application forms
* Make application decisions on behalf of the candidate

### The candidate remains in control.

After discovering a suitable opportunity, the user can click:

> **Apply Now**

The system then takes the user to the official listing URL, where the candidate can review the opportunity and complete the application themselves.

This keeps the final application decision with the human while removing the repetitive discovery workload.

---

# Setup

## Prerequisites

Make sure you have:

* Python 3.10 or newer
* Git
* A Browser Use API key for Real Agent Mode

A Browser Use API key is **not required** for Demo Mode.

---

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/InternScout-AI.git

cd InternScout-AI
```

---

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv

venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv

source venv/bin/activate
```

---

## 3. Install Dependencies

```bash
pip install streamlit pydantic python-dotenv browser-use-sdk
```

---

## 4. Configure Environment Variables

Create a `.env` file in the project root.

```env
# Browser Use API key for live browser automation
BROWSER_USE_API_KEY=your_browser_use_api_key_here

# Set to true for offline/demo execution
# Set to false for live browser automation
DEMO_MODE=false
```

### Demo Mode

If you want to run the application without an API key:

```env
DEMO_MODE=true
```

---

# Running the Application

Start the Streamlit application:

```bash
streamlit run app.py
```

Then open the local URL displayed by Streamlit, typically:

```text
http://localhost:8501
```

---

# Example User Flow

```text
1. Enter candidate profile
          ↓
2. Select internship preferences
          ↓
3. Start InternScout AI
          ↓
4. Browser agent searches platforms
          ↓
5. Listings are extracted
          ↓
6. Eligibility is analyzed
          ↓
7. Candidate fit is calculated
          ↓
8. Opportunities receive scores
          ↓
9. Results are ranked
          ↓
10. User reviews the best opportunities
          ↓
11. User clicks Apply Now
          ↓
12. Application is completed manually
```

---

# Example Output

```text
┌──────────────────────────────────────────────┐
│ AI/ML Intern — Example Company               │
│                                              │
│ MATCH SCORE                                  │
│                 92 / 100                    │
│                                              │
│ ✓ Excellent skills match                    │
│ ✓ Relevant project experience                │
│ ✓ Meets eligibility requirements             │
│ ✓ Preferred work mode                       │
│                                              │
│ Potential Concerns                           │
│ ⚠ TensorFlow experience preferred            │
│                                              │
│ [ Apply Now ]                                │
└──────────────────────────────────────────────┘
```

---

# What Makes InternScout AI Different?

InternScout AI is not simply another internship search interface.

The key idea is the combination of:

### Browser Automation

The system can interact with real-world websites instead of depending entirely on static datasets.

### Structured Extraction

Unstructured internship pages are converted into structured data that can be evaluated programmatically.

### Explainable Matching

Every opportunity receives a transparent score based on multiple measurable factors.

### Personalized Ranking

Instead of returning generic search results, the system prioritizes opportunities based on the individual candidate.

### Human-in-the-Loop Applications

The system automates the repetitive work while leaving the final application decision to the student.

### Reliable Demonstration

Demo Mode allows the complete workflow to be demonstrated even when live browser automation is unavailable.

---

# Future Roadmap

The current system focuses on internship discovery, evaluation, and ranking.

Future versions could include:

* [ ] Resume parsing from PDF and DOCX
* [ ] Automatic extraction of skills from resumes
* [ ] Personalized cover letter generation
* [ ] AI-generated application preparation
* [ ] Application status tracking
* [ ] Saved / Applied / Interviewing pipeline
* [ ] Notifications for high-score opportunities
* [ ] Webhook alerts for matches above a configurable threshold
* [ ] More internship and job platforms
* [ ] Historical application analytics
* [ ] Improved semantic skill matching
* [ ] Duplicate listing detection

---

# Project Vision

The long-term vision of InternScout AI is simple:

> **Turn internship hunting from a repetitive search task into an intelligent, personalized discovery process.**

Students should spend their time **building skills, preparing for interviews, and starting their careers** — not endlessly scrolling through job boards.

InternScout AI aims to become the intelligent layer between a student's profile and the constantly changing internship market.

---

# Disclaimer

InternScout AI is a student-focused automation project intended for internship discovery and evaluation.

Website availability, layouts, terms of service, authentication requirements, and access policies may change over time. Users are responsible for complying with the terms and policies of the websites they access.

InternScout AI does not autonomously submit internship applications. The final decision and application process remain under the user's control.

---

# License

This project is intended as a hackathon / educational project.

Add an appropriate open-source license if you plan to distribute the project publicly.

---

## Built with Python, Streamlit & Browser Automation

**InternScout AI — Find less. Match better. Apply smarter.**
