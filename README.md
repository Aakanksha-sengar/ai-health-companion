# AI Health Companion

An agentic AI prototype that helps elderly and chronic patients take their medicines on time and keeps their families informed.

**SDG 3: Good Health and Well-being**

**Live demo:** https://YOUR-USERNAME.github.io/ai-health-companion/

## Problem

Elderly people and patients with chronic conditions (BP, diabetes, thyroid, heart disease) often forget their medicines or take them at the wrong time. This worsens their health, increases hospital visits and worries their families. Existing tools like phone alarms and basic reminder apps only ring an alarm. They do not tell the family when a dose is missed and do not help with refills.

## Solution

AI Health Companion uses three agents that work together:

| Agent | What it does |
|---|---|
| **Reminder Agent** | Sends voice and text reminders based on the patient's daily routine |
| **Family Alert Agent** | Alerts the caregiver when a dose is missed |
| **Refill Agent** | Tracks medicine stock, reminds before it runs out and offers pharmacy ordering |

## Features in this prototype

- Dashboard with adherence percentage, doses taken, missed doses and refills needed
- Daily medicine schedule with "Mark as taken" and "Undo"
- Missed dose detection and automatic caregiver alert
- Agent activity log showing what each agent did
- Refill tracker with stock bars and a one-click pharmacy order
- Add and remove medicines
- Demo clock to simulate the time of day
- Works on mobile and desktop, with light and dark mode

## How to use the demo

1. Open the live demo link.
2. Use the **Demo clock** at the top to change the time of day.
3. Open the **Today** tab and mark doses as taken.
4. If a dose is not taken within 30 minutes of its time, it is marked **Missed** and the Family Alert Agent sends an alert.
5. Check the **Agent activity** and **Refills** tabs to see the other agents.

## Tech

- HTML, CSS and JavaScript in a single file
- No backend, database or external API
- Hosted on GitHub Pages

## Limitations

This is a concept prototype.

- Reminders and family alerts are simulated on screen. No real WhatsApp, SMS or voice messages are sent.
- Data is not saved. Refreshing the page resets the medicine list.
- The agents follow fixed rules and do not use a live AI model yet.

## Future scope

- Real WhatsApp and SMS alerts
- Voice reminders in Hindi and regional languages
- A live AI model to learn each patient's habits and choose better reminder times
- Pharmacy and clinic integrations for real refill orders
- User accounts and saved data

## Business model

Freemium: basic reminders are free, while family alerts and refill support are part of a paid subscription or family plan. Extra income from pharmacy commissions and B2B plans for clinics and hospitals.

## Author

Aakanksha-sengar
