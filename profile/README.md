# CogniSense
**Progressive AI Screening and Monitoring System for Neurological Health**

> *Small moments, repeated daily, reveal what single snapshots never can.*

---

## 1. PROBLEM CONTEXT

Neurological diseases like Parkinson's progress silently. Changes in speech, facial movement, and daily behavior often appear long before a formal clinical diagnosis — yet these signals go completely untracked between clinical visits.

By the time visible symptoms surface, the window for early intervention can already be closing. Even in advanced healthcare systems, continuous monitoring between appointments remains uncommon. In regions like India, consistent follow-up is limited further by low awareness and specialist access.

**Goal**

Build a non-diagnostic, ethical, scalable screening system that:

- Uses voice as the primary signal
- Escalates to additional analysis only when necessary
- Tracks changes over time rather than one-time predictions
- Produces clear and explainable outputs
- Meets users where they are — including on WhatsApp

---

## 2. SOLUTION OVERVIEW

CogniSense is a progressive multimodal AI screening and monitoring companion designed to identify potential early signals associated with Parkinson's Disease.

Available as a native mobile app and through WhatsApp, the system turns a 5-minute daily interaction into structured, longitudinal biomarker data — building a trend picture over time through natural conversation.

**CogniSense does not diagnose. It flags trends for clinical follow-up.**

### Core Components

**AI Levels**
- Level 1: Voice-based screening (default, low friction)
- Level 2: Facial expression analysis (conditional on risk or consent)
- Motor, sleep, and movement monitoring modules

**Channels**
- WhatsApp integration (accessibility-first for elderly users and caregivers)
- Native mobile app (clinical-grade tier with full feature depth)

**Dashboards**
- User Dashboard — simple, reassuring, trend-focused
- Clinician / Caregiver Dashboard — detailed, interpretable, longitudinal

---

## 3. HIGH-LEVEL SYSTEM FLOW

```
User App / WhatsApp
        ↓
Consent & Onboarding
        ↓
Level 1: Voice Capture
        ↓
Voice Analysis Pipeline
        ↓
Risk Score + Explainability
        ↓
   ┌──────────────────┐
   │                  │
Low Risk        Medium / High Risk
   │                  │
   ↓                  ↓
Trend View      Level 2 Unlock
                      ↓
              Facial / Motor Capture
                      ↓
              Multimodal Analysis
                      ↓
          Combined Assessment Layer
                      ↓
          Clinician Dashboard + Alerts
```

---

## 4. ACTORS AND INTERFACES

**User (Individual)**
Interaction through a mobile app or WhatsApp.

- Daily voice recordings
- Optional facial recordings
- Motor and movement interaction tasks
- Trend tracking against personal baseline

The system surfaces patterns and trends — not diagnoses.

**Clinician / Caregiver**
Access through a web dashboard.

- Longitudinal monitoring timelines
- Explainable AI insights and signal contribution analysis
- Automated monthly summaries
- Exportable monitoring reports

---

## 5. LEVEL 1 — VOICE SCREENING

**Purpose:** Detect speech-related deviations associated with Parkinson's risk using a low-friction, app-free interaction.

**Input:** 20–30 second guided speech recording via smartphone. No camera required. WhatsApp compatible — a voice note in, a risk score out.

### Voice Processing Pipeline

```
Audio Upload (API Gateway → Lambda → S3)
        ↓
Quality Check
        ↓
Feature Extraction (Praat)
   — Jitter, shimmer, pitch variation, speech rate, tremor markers
        ↓
Amazon Transcribe (speech-to-text)
        ↓
SageMaker Model Ensemble
   — Feature-based model
   — Temporal sequence model
   — Spectrogram-based model
        ↓
Risk Score + Confidence
        ↓
Explainability Layer
```

**Training Data:** Parkinson's Speech with Multiple Types of Sound Recordings dataset

**Model Performance:** ROC-AUC 0.65 on voice alone; 0.96 with UPDRS indicators on held-out test data. Real-world clinical validation is the immediate next step.

**Output:**
- Risk category: Low / Medium / High
- Confidence score
- Feature-level explanations

---

## 6. LEVEL 2 — FACIAL EXPRESSION ANALYSIS

**Trigger:** Activated when Level 1 risk crosses a threshold, or the user provides explicit consent.

**Input:** Short selfie video (5–10 seconds)

### Facial Analysis Pipeline

```
Video Upload
        ↓
Frame Extraction
        ↓
MediaPipe Face Landmark Detection
        ↓
Temporal Facial Dynamics Model (SageMaker)
        ↓
Facial Risk Score
```

**Signals Studied**
- Facial rigidity
- Blink rate
- Mouth symmetry
- Micro-movement stability

The facial model is independent from the voice model, ensuring modular and explainable system behaviour.

---

## 7. MOTOR AND MOVEMENT MODULES

The native app expands CogniSense into a clinically robust monitoring platform through four structured motor assessments, each UPDRS-aligned.

| Test | What It Measures |
|------|-----------------|
| Archimedes Spiral | Tremor, deviation, drawing speed consistency |
| Meander Wave | Tremor, stroke accuracy, speed variance |
| Finger Tapping Test | Tap frequency, hesitations, fatigue ratio (each hand, 10 seconds) |
| Clock Drawing | Spatial organisation, motor planning |

**Training Data:** Parkinson's Disease Spiral Drawings Using Digitized Graphics dataset

**Walking Assessment:** Observes 8–10 steps forward, turn, return — analysing arm swing symmetry, stride length, posture, and turning coordination. Detection is baseline-relative, not population-relative.

**LSVT BIG Rehabilitation:** Gamified large-amplitude reach exercises with real-time MediaPipe pose feedback. Outputs feed directly into the multimodal biomarker pipeline — therapy that is measurable, not just instructional.

---

## 8. SLEEP AND MEDICATION MODULES

**Sleep Monitoring**
- RBD indicator detection
- REM fragmentation and deep sleep tracking
- Resting heart rate
- Dystonia logging
- Processed via SageMaker endpoints

**Medication Tracker**
- Dose logging and adherence tracking
- Daily on/off timeline mapping
- Peak off-period window identification
- Caregiver alerts via SNS (event-driven on EventBridge + Lambda)

**Support Network**
- Connects users to a Hoehn and Yahr stage-matched peer group
- Live chat for patients at the same progression stage

---

## 9. MULTIMODAL DECISION ENGINE

Fusion occurs at the decision level — not the raw data level.

```
Voice Risk Score
Facial Risk Score
Motor Signals
Sleep / Medication Context
Confidence Weights
        ↓
Step Functions Consolidation Pipeline
        ↓
Single Longitudinal Biomarker Profile
        ↓
Final Screening / Monitoring Assessment
```

**Benefits**
- Works even when one modality is missing
- Cleaner explainability per signal
- Safer, modular, more robust real-world performance

---

## 10. CONVERSATIONAL LAYER

Amazon Bedrock powers the conversational interface, capturing sleep quality, mood, motor difficulty, and sensory context across every interaction. Amazon Polly returns responses in natural voice.

On WhatsApp, this runs without any app download — accessible to elderly users and caregivers on a platform they already trust.

---

## 11. DASHBOARD DESIGN

**User Dashboard**

Objective: awareness and reassurance

| Element | Detail |
|---------|--------|
| Daily status | Low / Medium / High with confidence |
| Trend view | Progress vs personal baseline over time |
| Biomarker breakdown | Voice, facial, motor signal split |
| Privacy controls | Consent management and data preferences |

Example output:
```
Status:     Low Risk
Trend:      Stable
Confidence: High
```

**Clinician / Caregiver Dashboard**

Objective: interpretability and longitudinal monitoring

- Timeline views across all biomarker streams
- Signal contribution breakdown (e.g. Voice 65%, Facial 35%)
- Key signal highlights (e.g. pause duration, blink rate, pitch instability)
- Automated monthly summaries via EventBridge and SES
- Built on AWS Amplify

---

## 12. ARCHITECTURE AND INFRASTRUCTURE

| Layer | Technology |
|-------|-----------|
| API / Ingestion | Amazon API Gateway + AWS Lambda |
| Auth | Amazon Cognito |
| Storage | S3 (audio/video), DynamoDB (longitudinal history) |
| Transcription | Amazon Transcribe |
| Feature Extraction | Praat |
| Model Serving | Amazon SageMaker |
| Orchestration | AWS Step Functions |
| Conversational AI | Amazon Bedrock |
| Voice Output | Amazon Polly |
| Alerts | Amazon SNS |
| Scheduling | Amazon EventBridge |
| Frontend Dashboards | AWS Amplify |

---

## 13. PRIVACY AND DATA GOVERNANCE

CogniSense operates a deliberate two-tier privacy model.

**WhatsApp Tier**
Accessibility-first channel for elderly users, caregivers, and rural populations. Consent-based, voice and facial only. Aligned with India's DPDP Act 2023.

**Native App Tier**
Clinical-grade. End-to-end encrypted. DPDP and HIPAA-aligned with strict data minimisation and explicit consent flows. The compliant path for clinical partnerships and US deployment.

**System-wide principles:**
- Screening system — not diagnostic
- Explicit uncertainty modelling
- Consent-based escalation
- Minimal raw data retention
- Feature-level storage where possible
- Federated learning: model improves with use without raw data leaving the device

---

## 14. ARCHITECTURE PRINCIPLES

- Voice-first, low-friction entry
- Progressive escalation — deeper analysis only when needed
- Modular multimodal design
- Explainable outputs at every layer
- Ethical and consent-aware workflows
- Longitudinal monitoring as the core product

---

## 15. COMPETITIVE CONTEXT

| Tool | Approach | CogniSense Difference |
|------|----------|----------------------|
| Khayyal / Speak PD | Voice-only Parkinson's screening | Adds facial, motor, sleep, and behavioural context |
| Roche / Floodlight One | Sensor + app monitoring | Requires dedicated hardware; not WhatsApp-accessible |
| mPower (Sage Bionetworks) | Research phone sensor collection | Research tool, not a user-facing wellness companion |
| Winterlight Labs | Clinical voice analysis | Enterprise/clinical only; not consumer accessible |

CogniSense's primary channel is **B2B2C** — clinics offer it as a monitoring layer between visits, with longitudinal biomarker data flowing back into clinical review. A direct consumer tier targets individuals over 40 tracking their own cognitive health proactively.

---

## 16. ONE LINE SUMMARY

CogniSense is a progressive multimodal AI screening and monitoring companion that uses voice as a first signal, conditionally expands to deeper analysis, and supports long-term neurological monitoring through interpretable outputs — for users, caregivers, and clinicians.

---

*Built for AIdeas · Team: Shambhvi Sharma, Yash Aggarwal*
