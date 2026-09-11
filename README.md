# buildathon-PS3-TechTitans
An AI-powered food safety inspection and risk management platform that helps authorities prioritize high-risk establishments, track inspections and violations, manage corrective actions, monitor compliance, and use a GenAI assistant to analyze real inspection data and generate actionable insights.
# 🍽️ Intelligent Food Safety Inspection & Risk Management Platform

> **AI-powered decision-support platform for smarter food safety inspections, risk assessment, violation management, and compliance tracking.**

## 🚨 Problem

Food safety authorities manage a large number of food establishments, inspections, violations, corrective actions, and re-inspections.

Traditional inspection workflows can make it difficult to:

* Identify which establishments should be inspected first
* Detect recurring or critical violations
* Track unresolved corrective actions
* Monitor compliance over time
* Analyze historical inspection data
* Make data-driven inspection decisions

This creates a need for an intelligent platform that converts inspection history into actionable risk intelligence.

---

## 💡 Proposed Solution

The **Intelligent Food Safety Inspection & Risk Management Platform** is a web-based decision-support system that helps food safety authorities:

* Manage food establishments
* Create and manage inspections
* Record and track violations
* Manage corrective actions
* Schedule and conduct re-inspections
* Calculate establishment risk levels
* Prioritize inspections using AI/ML
* Monitor compliance through dashboards
* Query inspection data using a GenAI assistant

### Core Workflow

```text
Establishment
      ↓
Inspection
      ↓
Violation
      ↓
Corrective Action
      ↓
Re-inspection
      ↓
Compliance Tracking
      ↓
Risk Recalculation
```

---

# 🎯 Key Features

## 1. Role-Based Authentication

Different users can access different parts of the system.

| Role                  | Responsibility                                          |
| --------------------- | ------------------------------------------------------- |
| Inspector             | Conduct inspections and record violations               |
| Inspection Manager    | Assign, schedule and review inspections                 |
| Establishment Manager | Manage establishment information and corrective actions |
| Admin                 | Manage users and system configuration                   |

---

## 2. Establishment Management

Store and manage information about food establishments.

### Information includes:

* Establishment name
* Establishment type
* Location / zone
* Inspection history
* Current risk level
* Previous violations
* Compliance status

---

## 3. Inspection Management

Inspectors and managers can:

* Create inspections
* Assign inspectors
* Schedule inspections
* Submit inspection results
* Review completed inspections
* View historical inspections

---

## 4. Violation Management

Each violation can contain:

* Violation category
* Severity
* Description
* Evidence
* Corrective action
* Status
* Resolution date

Violations can be classified as:

```text
Minor
Major
Critical
```

---

# 🤖 AI/ML Risk Engine

The platform uses historical inspection data to estimate the risk associated with each establishment.

### Input Features

The baseline model can use:

* Previous violation count
* Critical violation count
* Recurring violation count
* Days since last inspection
* Previous corrective-action failures
* Complaint / incident count
* Unresolved violation count

### Output

```text
Risk Probability
       +
Risk Category
       ↓
LOW / MEDIUM / HIGH / CRITICAL
```

### Example

```text
Restaurant: ABC Food House

Previous Violations:       8
Critical Violations:       3
Recurring Violations:      2
Corrective Failures:       2
Days Since Inspection:    145

Predicted Risk:            87%
Risk Category:             HIGH
```

The establishment can then be moved higher in the **inspection priority list**.

---

# 🧠 Explainable Risk Assessment

The platform should not only show the risk category.

It should also explain **why** the establishment received that risk level.

Example:

```text
HIGH RISK — 87%

Main contributing factors:

🔴 3 previous critical violations
🔴 2 recurring violations
🟠 2 failed corrective actions
🟠 145 days since last inspection
```

This makes the AI output easier for inspectors and managers to understand and trust.

---

# ✨ GenAI Assistant

The platform includes a GenAI assistant connected to the application's actual inspection and violation data.

Instead of behaving like a generic chatbot, the assistant retrieves relevant project records before generating an answer.

### Example Questions

> Why is Restaurant A classified as high risk?

> Show recurring violations for Restaurant B.

> Which establishments have unresolved critical violations?

> Summarize Restaurant C's inspection history.

> Which establishments in Zone 2 should be prioritized this month?

> Generate an inspection briefing for Restaurant D.

### Example Response

```text
Restaurant A is currently classified as HIGH RISK.

Reasons:
• 3 critical violations in the last 12 months
• 2 recurring violations
• 1 failed corrective action
• Last inspection was 142 days ago

Recommendation:
Prioritize Restaurant A for inspection this month.
```

---

# 📊 Dashboard

The main dashboard provides an overview of food safety conditions.

### Key Performance Indicators

* Total establishments
* Inspections completed
* High-risk establishments
* Critical violations
* Unresolved violations
* Overdue inspections
* Pending corrective actions

### Visualizations

* Risk distribution
* Violations by category
* Violations by severity
* Inspection trends
* Compliance trends
* High-risk establishment ranking

---

# 🏗️ System Architecture

```text
                    ┌──────────────────────┐
                    │      React / Next.js │
                    │       Frontend       │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │     REST API         │
                    │ FastAPI / Node.js    │
                    └───────┬───────┬──────┘
                            │       │
                ┌───────────┘       └────────────┐
                ▼                                ▼
       ┌─────────────────┐              ┌─────────────────┐
       │   PostgreSQL    │              │   AI/ML Engine  │
       │    Database     │              │  scikit-learn   │
       └─────────────────┘              └────────┬────────┘
                                                 │
                                                 ▼
                                      ┌────────────────────┐
                                      │    GenAI Layer     │
                                      │  Retrieval + LLM   │
                                      └────────────────────┘
```

---

# 🗄️ Database Design

Main entities:

```text
Users
  │
  ├── Establishments
  │       │
  │       └── Inspections
  │               │
  │               └── Violations
  │                       │
  │                       └── Corrective Actions
  │                               │
  │                               └── Re-inspections
  │
  ├── Risk Scores
  ├── Complaints
  ├── Attachments
  └── Audit Logs
```

### Main Tables

* `users`
* `establishments`
* `inspections`
* `violations`
* `corrective_actions`
* `reinspections`
* `risk_scores`
* `complaints`
* `attachments`
* `audit_logs`

---

# 🛠️ Technology Stack

### Frontend

* React / Next.js
* Recharts / Chart.js

### Backend

* FastAPI / Node.js
* REST API

### Database

* PostgreSQL

### AI/ML

* Python
* scikit-learn
* Pandas
* NumPy

### GenAI

* LLM API
* Retrieval layer connected to application data

### Authentication

* JWT
* Role-based access control

---

# 🎬 Judge Demo Flow

Our demonstration follows a realistic inspection workflow.

### Step 1 — Login

Login as an **Inspection Manager**.

### Step 2 — Dashboard

Show:

* High-risk establishments
* Critical violations
* Overdue inspections
* Risk distribution

### Step 3 — Establishment

Open a high-risk restaurant and display its inspection history.

### Step 4 — AI Risk Prediction

Run the risk engine and show:

```text
Risk Probability: 87%
Risk Level: HIGH
```

Then show the factors contributing to the prediction.

### Step 5 — New Inspection

Create an inspection and record a critical violation.

### Step 6 — Corrective Action

Submit corrective action and supporting evidence.

### Step 7 — Re-inspection

Conduct a re-inspection and close the violation after successful remediation.

### Step 8 — GenAI Assistant

Ask:

> Why was this establishment high risk and has its risk improved?

The assistant retrieves the establishment's latest records and provides a data-backed response.

### Step 9 — Final Dashboard

Show updated:

* Risk level
* Compliance status
* Violation trends
* Inspection priorities

---

# 🚀 Development Roadmap

## Phase 1 — MVP

* Authentication
* Role management
* Establishment management
* Inspection management
* Violation management
* PostgreSQL database

## Phase 2 — Intelligence

* Risk scoring
* Baseline ML model
* Risk explanations
* Inspection prioritization

## Phase 3 — Compliance

* Corrective actions
* Evidence submission
* Re-inspection
* Compliance tracking

## Phase 4 — GenAI

* Data retrieval
* GenAI assistant
* Inspection summaries
* Risk explanations
* Inspection briefing generation

## Phase 5 — Enhancement

* Risk trend analysis
* Recurring violation detection
* Risk heatmap
* Automated inspection scheduling
* OCR
* Automated reports

---

# 🏆 Why This Solution?

The platform combines **workflow automation, data analytics, AI/ML risk prediction, and GenAI assistance** into one system.

Instead of simply storing inspection records, it transforms historical data into actionable decisions.

### From:

```text
Inspection Data
```

### To:

```text
Risk Intelligence
      ↓
Inspection Priority
      ↓
Corrective Action
      ↓
Compliance Improvement
```

---

# 🎯 Expected Impact

The proposed platform can help food safety authorities:

* Prioritize high-risk establishments
* Identify recurring violations
* Reduce unresolved violations
* Improve corrective-action tracking
* Monitor compliance
* Make more data-driven inspection decisions
* Reduce manual analysis of inspection records

---

# 📌 Project Status

**Current Stage:** Hackathon MVP / Prototype

The initial version focuses on demonstrating the complete workflow:

```text
Establishment
→ Inspection
→ Violation
→ Corrective Action
→ Re-inspection
→ Risk Assessment
→ AI-assisted Decision Support
```

---

# 👥 Team

| Name          | Role                 |
| ------------- | -------------------- |
| Team Member 1 | Full Stack / Backend |
| Team Member 2 | Frontend / UI        |
| Team Member 3 | AI/ML / database     |

---

## 🏁 Final Pitch

> **Our platform helps food-safety authorities decide where to inspect first, understand recurring violations, track corrective actions, and use AI to turn historical inspection data into actionable risk intelligence.**
