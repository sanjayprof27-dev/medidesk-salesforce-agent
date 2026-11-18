# MediDesk — Healthcare Front-Desk Assistant (Salesforce Agentforce)

## Problem Statement
Hospital front desks handle high volumes of repetitive patient inquiries regarding consultation hours, department fees, and appointment scheduling. At the same time, patients describing acute symptoms require immediate emergency redirection rather than automated medical advice.

## Agent Architecture
MediDesk is built using **Salesforce Agentforce Builder** with an **Agent Router** directing user intent across three specialized subagents (topics):

1. **`Consultation_and_Fees`**: Provides OPD consultation timings (Monday–Saturday, 9:00 AM – 6:00 PM) and consultation fee schedules across General Medicine, Pediatrics, Orthopedics, and Dermatology.
2. **`Appointment_Request`**: Collects required patient intake fields (full name, phone number, preferred department, and preferred date/time) and confirms a structured summary back to the patient.
3. **`Medical_Emergency_and_Guardrails`**: Detects emergency symptoms (such as chest pain or breathing difficulty) and immediately directs patients to call **112** or **108**, while refusing any requests for medical diagnosis or medication recommendations.

## Flow Logic & Guardrails
- **Intent Routing:** Incoming queries are evaluated by the Agent Router and matched to the corresponding topic instructions.
- **Slot Collection:** `Appointment_Request` prompts for any missing patient details before generating a confirmation summary.
- **Safety Escalation:** `Medical_Emergency_and_Guardrails` overrides standard informational flows whenever acute symptoms or diagnostic requests are detected, enforcing strict non-diagnostic guardrails.

## Repository Contents
- `medidesk_agent.yaml` — Exported Agentforce Topics & Instructions configuration.
- Screenshots of the Agent Builder canvas (`0` errors) and live Preview test conversations.
