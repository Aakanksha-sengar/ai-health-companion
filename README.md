# AI Health Companion

An agentic AI prototype that helps elderly and chronic patients take their medicines on time and keeps their families informed. It includes a machine learning model that predicts which doses are likely to be missed, so the family can be alerted in advance.

**SDG 3: Good Health and Well-being**

**Live demo:** https://YOUR-VERCEL-LINK.vercel.app
**ML notebook:** `missed_dose_model.ipynb` (open in Google Colab and click Runtime > Run all)

## Problem

Elderly people and patients with chronic conditions (BP, diabetes, thyroid, heart disease) often forget their medicines or take them at the wrong time. This worsens their health, increases hospital visits and worries their families. Existing tools like phone alarms and basic reminder apps only ring an alarm. They do not tell the family when a dose is missed and do not help with refills.

## Solution

AI Health Companion uses three agents backed by an ML risk model:

| Component | What it does |
|---|---|
| **Reminder Agent** | Sends voice and text reminders based on the patient's daily routine |
| **Family Alert Agent** | Alerts the caregiver when a dose is missed, and in advance when the ML model predicts a high risk of missing it |
| **Refill Agent** | Tracks medicine stock, reminds before it runs out and offers pharmacy ordering |
| **Missed-dose risk model** | Predicts the chance that the patient will miss the next dose |

## Machine Learning Model

**Goal:** predict whether a patient will miss their next dose, so the Family Alert Agent can act before it happens.

**Model:** Logistic Regression (compared with a Random Forest).

**Input features:**
- Age
- Number of doses per day
- Night-time dose (8 PM or later)
- Weekend
- Adherence over the last 7 days
- Lives alone
- Missed a dose yesterday

**Output:** miss risk as a percentage, shown as Low, Medium or High.

**Results on the test set (20% of the data):**

| Model | Accuracy | Precision | Recall | ROC-AUC |
|---|---|---|---|---|
| Logistic Regression | 0.718 | 0.691 | 0.575 | 0.780 |
| Random Forest | 0.703 | 0.676 | 0.545 | 0.758 |

Logistic Regression was chosen because it performs similarly to the Random Forest and every prediction can be explained.

**Data:** the dataset is **synthetic** (6,000 generated records, about 41% missed doses), because real patient data is private. The patterns in it are assumptions, for example that night doses and living alone raise the risk of missing a dose. The reported accuracy therefore applies to this synthetic data and not to real patients. The model should be retrained on real, consented data before any real use.

## Features in this prototype

- Dashboard with adherence percentage, doses taken, missed doses and refills needed
- Daily medicine schedule with "Mark as taken" and "Undo"
- Patient profile that feeds the ML model, with a live miss-risk score on every upcoming dose
- Missed dose detection and automatic caregiver alert
- Advance alert for doses the model predicts to be high risk
- Agent activity log showing what each agent did
- ML model tab with test metrics and the factors that drive risk
- Refill tracker with stock bars and a one-click pharmacy order
- Add and remove medicines
- Demo clock to simulate the time of day
- Works on mobile and desktop, with light and dark mode

## How to use the demo

1. Open the live demo link.
2. Use the **Demo clock** at the top to change the time of day.
3. On the **Today** tab, change the patient profile (for example age, lives alone) and watch the miss-risk scores change.
4. Mark doses as taken. If a dose is not taken within 30 minutes of its time, it is marked **Missed** and the Family Alert Agent sends an alert.
5. Check the **Agent activity**, **Refills** and **ML model** tabs.

## Repository contents

| File | Description |
|---|---|
| `index.html` | The prototype web app |
| `missed_dose_model.ipynb` | Notebook that creates the data, trains and evaluates the model |
| `missed_dose_dataset.csv` | Synthetic dataset used for training |
| `README.md` | This file |

## Tech

- App: HTML, CSS and JavaScript in a single file, hosted on Vercel
- Model: Python, pandas, scikit-learn (trained in the notebook)
- The trained model weights are built into the app, so there is no backend, database or external API

## Limitations

This is a concept prototype.

- Reminders and family alerts are simulated on screen. No real WhatsApp, SMS or voice messages are sent.
- The ML model is trained on synthetic data, so its accuracy is not a measure of real-world performance.
- Data is not saved. Refreshing the page resets the medicine list and profile.
- The reminder, alert and refill agents follow fixed rules. Only the risk prediction uses machine learning.

## Future scope

- Train the model on real, consented patient data
- Real WhatsApp and SMS alerts
- Voice reminders in Hindi and regional languages
- A live AI model that learns each patient's habits and chooses better reminder times
- Pharmacy and clinic integrations for real refill orders
- User accounts and saved data

## Business model

Freemium: basic reminders are free, while family alerts, risk predictions and refill support are part of a paid subscription or family plan. Extra income from pharmacy commissions and B2B plans for clinics and hospitals.

## Author

Aakanksha-sengar
