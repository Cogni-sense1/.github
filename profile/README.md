# Cognisense
## Progressive AI Screening and Monitoring System
### End-to-End Architecture Overview

![Demo](../assets/one.jpeg)
![Demo](../assets/two.jpeg)

---

## 1. PROBLEM CONTEXT

Parkinson’s Disease (PD) is a progressive neurological disorder where **speech, facial expression, and movement changes often appear early**, sometimes even before formal clinical diagnosis. Traditional diagnostic pathways are specialist-driven, expensive, and difficult to scale across large populations.

**Goal**

Build a **non-diagnostic, ethical, scalable screening system** that:

- Uses **voice as the primary signal**
- Escalates to **additional analysis only when necessary**
- Tracks **changes over time rather than one-time predictions**
- Produces **clear and explainable outputs**

---

## 2. SOLUTION OVERVIEW

**Cognisense** is a **progressive multimodal AI screening and monitoring system** designed to identify potential early signals associated with Parkinson’s.

The system is built around three main ideas:

- **Voice-first screening**
- **Conditional deeper analysis**
- **Longitudinal monitoring**

### Core Components

**AI Levels**

- Level 1: Voice-based screening (default)
- Level 2: Facial expression analysis (conditional)
- Motor and movement monitoring modules

**Dashboards**

- User Dashboard (simple and reassuring)
- Clinician Dashboard (detailed and interpretable)

**System Principles**

- Modular architecture
- Progressive escalation
- Explainable outputs
- Long-term monitoring capability

---

## 3. HIGH LEVEL SYSTEM FLOW

```
User App
   ↓
Consent & Onboarding
   ↓
Level 1: Voice Capture
   ↓
Voice Analysis
   ↓
Risk + Explainability
   ↓
 ┌───────────────┐
 │               │
Low Risk     Medium / High Risk
 │               │
 ↓               ↓
Trend View   Level 2 Unlock
                 ↓
         Facial / Motor Capture
                 ↓
         Multimodal Analysis
                 ↓
         Combined Assessment Layer
                 ↓
         Clinician Dashboard
```

---

## 4. ACTORS AND INTERFACES

### User (Individual)

Interaction through a **mobile interface**.

Capabilities:

- Daily voice recordings
- Optional facial recordings
- Motor and movement interaction tasks
- Trend tracking over time

The system shows **patterns and trends instead of diagnoses**.

---

### Clinician / Researcher

Access through a **web dashboard**.

Capabilities:

- Longitudinal monitoring
- Explainable AI insights
- Signal contribution analysis
- Exportable monitoring summaries

---

## 5. LEVEL 1 — VOICE SCREENING

### Purpose

Detect **speech-related deviations** associated with Parkinson’s risk using a low-friction interaction.

### Input

- 20–30 second guided speech recording
- Smartphone-based capture
- No camera required

### Voice Processing Pipeline

```
Audio Upload
   ↓
Quality Check
   ↓
Feature Extraction
   ↓
Voice Models
   ↓
Risk Score + Confidence
   ↓
Explainability Layer
```

### Models Used

- Feature based model
- Temporal sequence model
- Spectrogram based model

### Output

- Risk category: Low / Medium / High
- Confidence score
- Feature level explanations

---

## 6. LEVEL 2 — FACIAL EXPRESSION ANALYSIS

### Trigger

Activated when:

- Level 1 risk crosses a threshold
- Or the user provides explicit consent

### Input

Short selfie video (5–10 seconds)

### Facial Analysis Pipeline

```
Video Upload
   ↓
Frame Extraction
   ↓
Face Landmark Detection
   ↓
Temporal Facial Dynamics Model
   ↓
Facial Risk Score
```

### Signals Studied

- Facial rigidity
- Blink rate
- Mouth symmetry
- Micro movement stability

### Design Principle

The facial model is **independent from the voice model**, ensuring modular and explainable system behavior.

---

## 7. MOTOR AND MOVEMENT MODULES

The system also supports **movement-based monitoring** to observe motor patterns over time.

Example tasks:

- Finger tapping tests
- Handwriting and drawing tasks
- Arm swing observation
- Posture and guided movement tracking

These modules support **longitudinal monitoring and rehabilitation-oriented interaction**.

---

## 8. MULTIMODAL DECISION ENGINE

Fusion occurs at the **decision level rather than the raw data level**.

```
Voice Risk Score
Facial Risk Score
Motor Signals
Confidence Weights
        ↓
Final Screening / Monitoring Assessment
```

### Benefits

- Works even when one modality is missing
- Easier explainability
- Safer and modular design
- More robust real-world performance

---

## 9. DASHBOARD DESIGN

### User Dashboard

Objective: **awareness and reassurance**

Features:

- Daily status indicator
- Trend vs personal baseline
- Confidence indicator
- Privacy and consent controls

Example output

```
Status: Low Risk
Trend: Stable
Confidence: High
```

---

### Clinician Dashboard

Objective: **interpretability and monitoring**

Features:

- Longitudinal timelines
- Feature contribution insights
- Voice vs facial signal split
- Structured monitoring summaries

Example insights

- Voice contribution: 65%
- Facial contribution: 35%
- Key signals: pause duration, blink rate, pitch instability

---

## 10. ARCHITECTURE PRINCIPLES

The system is designed around the following principles:

- Progressive screening
- Modular multimodal design
- Explainable outputs
- Low friction user interaction
- Ethical and consent-aware workflows
- Longitudinal monitoring

---

## 11. DATA GOVERNANCE AND ETHICS

- Screening system (not diagnostic)
- Explicit uncertainty modeling
- Consent based escalation
- Minimal raw data retention
- Feature level storage where possible
- Privacy aware processing

---

## 12. WHY THIS IS AN END TO END SYSTEM

- Voice first screening
- Conditional deeper analysis
- Multimodal monitoring
- User and clinician interfaces
- Longitudinal data tracking
- Explainable outputs
- Modular real world architecture

---

## 13. ONE LINE SUMMARY

Cognisense is a progressive multimodal AI screening and monitoring system that uses voice as a first signal, conditionally expands to deeper analysis, and supports long-term monitoring through interpretable outputs for users and clinicians.
