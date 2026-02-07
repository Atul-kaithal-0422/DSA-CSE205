# Figures: Intelligent Healthcare Analytics Using Wearables and IoT Data

This document presents the figures used in the chapter **Preventive Healthcare Analytics Using Wearables and IoT Data**. Each figure is provided with its original heading and a Mermaid diagram for easy rendering and reuse.

---

## Figure 1: Architecture of an Intelligent Healthcare Analytics System

```mermaid
flowchart LR
    A[Wearable Devices] --> B[Data Acquisition Layer]
    C[IoT Sensors] --> B
    D[EHR Systems] --> B

    B --> E[Data Preprocessing]
    E --> F[Feature Engineering]

    F --> G[AI / ML Models]
    G --> H[Predictive Analytics]
    G --> I[Preventive Analytics]
    G --> J[Personalized Insights]

    H --> K[Clinical Decision Support]
    I --> K
    J --> K
```

---

## Figure 2: Healthcare Data Sources and Analytics Pipeline

```mermaid
flowchart TB
    A[EHR Data] --> F[Data Integration Layer]
    B[Medical Imaging] --> F
    C[Wearables] --> F
    D[Genomics] --> F
    E[Environmental IoT] --> F

    F --> G[Data Cleaning & Quality Control]
    G --> H[Analytics & AI Models]
    H --> I[Healthcare Insights & Actions]
```

---

## Figure 3: Machine Learning Paradigms in Healthcare

```mermaid
graph TD
    A[Machine Learning in Healthcare]

    A --> B[Supervised Learning]
    B --> B1[Classification]
    B --> B2[Regression]

    A --> C[Unsupervised Learning]
    C --> C1[Clustering]
    C --> C2[Anomaly Detection]

    A --> D[Semi-Supervised Learning]

    A --> E[Reinforcement Learning]
```

---

## Figure 4: AI Models for Predictive and Preventive Healthcare

```mermaid
flowchart LR
    A[Healthcare Data Streams] --> B[CNNs]
    A --> C[RNNs / LSTMs]
    A --> D[Transformers]

    B --> E[Disease Detection]
    C --> F[Health Trend Prediction]
    D --> G[Multimodal Risk Assessment]

    E --> H[Preventive Interventions]
    F --> H
    G --> H
```

---

## Figure 5: Remote Patient Monitoring Using AI and IoT

```mermaid
sequenceDiagram
    participant Patient
    participant Wearable
    participant IoT_Gateway
    participant AI_Engine
    participant Clinician

    Patient ->> Wearable: Physiological Signals
    Wearable ->> IoT_Gateway: Sensor Data
    IoT_Gateway ->> AI_Engine: Streamed Data
    AI_Engine ->> AI_Engine: Analyze & Detect Anomalies
    AI_Engine ->> Clinician: Alerts & Risk Scores
```

---

## Figure 6: Challenges and Ethical Issues in Intelligent Healthcare Analytics

```mermaid
mindmap
  root((AI in Healthcare))
    Data Privacy
      Security
      Confidentiality
    Bias & Fairness
      Dataset Imbalance
      Population Bias
    Explainability
      Model Transparency
      Clinical Trust
    Regulation
      Legal Compliance
      Accountability
```

---

*End of Figures Document*
