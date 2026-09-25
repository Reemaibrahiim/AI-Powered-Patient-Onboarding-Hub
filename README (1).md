# 🏥 AI-Powered Patient Onboarding Hub

An AI patient intake assistant built with **Salesforce Agentforce** as a capstone project for the **AI–CAFE summer program by SmartBridge**. It guides patients through initial information collection, handles insurance and appointment requests, answers supported clinic questions, and routes requests for a human agent.

> **Prototype scope:** The agent collects insurance details and appointment preferences. The supplied configuration does not connect to an insurer for coverage verification or to a clinic scheduling system for confirmed bookings. It does not present either outcome as complete.

## ✨ Features

| Capability | Agent behavior |
| --- | --- |
| Patient intake | Asks for a full name, date of birth, contact information, and reason for the visit, one item at a time. |
| Insurance information | Collects the provider and member ID; directs coverage questions to the clinic or insurer for confirmation. |
| Appointment requests | Collects a preferred date and time, then asks the patient to confirm the request. A booking requires a separate clinic system. |
| Clinic FAQ | Uses the configured Salesforce Knowledge action to answer supported questions when relevant articles are available. |
| Human escalation | Routes a patient who asks for a person to a live agent. |
| Unclear or unrelated requests | Asks a clarifying question or redirects to supported patient services. |

## 🧠 How It Works

The **Patient Intake Assistant** uses an Agentforce Service Agent template. An intent router directs each message to one of seven specialized subagents: Patient Info Collection, Insurance Verification, Appointment Scheduling, General FAQ, Escalation, Off Topic, or Ambiguous Question. Agentforce variables retain information across the conversation, including the patient's name, date of birth, contact information, and insurance member ID. The agent also has messaging session variables. The `appointmentConfirmationId` variable is defined for a future completed booking flow; this prototype does not generate a confirmation ID.

The FAQ subagent is configured with the `AnswerQuestionsWithKnowledge` action. Useful answers depend on the clinic's knowledge articles and Salesforce configuration. The provided export has no RAG configuration ID and has citations disabled.

## 💬 Example Conversation

```text
Patient: I'd like to schedule an appointment.
Assistant: What date would you prefer?
Patient: Next Tuesday.
Assistant: What time would you prefer?
Patient: 10:00 AM.
Assistant: Please confirm your requested date and time.
Patient: Yes.
Assistant: Your request has been noted. The clinic must complete the booking
           before the appointment is confirmed.
```

The Agentforce Builder preview was used to test routing and the appointment conversation. The preview shows the assistant requesting confirmation and explicitly stating that the appointment is not yet booked.

## 📁 Project Files

- `AgentSourceCode.txt` — Agentforce agent definition and subagent instructions.
- `AI-Powered_Patient_Onboarding_Hub_Project_Documentation.pdf` — architecture, workflows, and test summary.
- `Agentforce Configuration & Prompt Engineering Document.pdf` — configuration and prompt design.
- `Project Plan & User Stories.pdf` — project plan and user stories.
- `lifedemo.mp4` — recorded demonstration.
- `aglist.png`, `agvlist.png`, and the other screenshots — Agentforce Builder views and conversation previews.

Place these files alongside this README if you want the repository contents to match the list above. The configuration export contains environment-specific identifiers; review and replace them before publishing or deploying it in another Salesforce organization.

## 🚀 Running the Prototype

This project is configured in **Salesforce Agentforce Builder**, rather than as a standalone application. To explore the agent in the original Salesforce environment, open **Setup → Agentforce Agents → Patient Intake Assistant**, then use **Preview / Live Test**. Deploying it in another organization requires an Agentforce-enabled Salesforce environment, the corresponding agent configuration, permissions, and any clinic-specific Knowledge or handoff setup. The text export documents the configuration; it is not an automated deployment script.

## 🔧 Limitations and Next Steps

- Integrate an insurance eligibility service before reporting verified coverage.
- Connect to a real scheduling system before showing available slots or confirming appointments.
- Add clinic Knowledge content and validate the FAQ responses against approved information.
- Review patient data handling, access controls, and applicable healthcare privacy requirements before using real patient information.

## 🙌 Acknowledgment

Developed by **Reema Alraqibah** as part of the **AI–CAFE (AI Career Accelerator for Future Engineers)** summer program, implemented by SmartBridge with Salesforce and IBM SkillsBuild support.
