flowchart LR
    A[🌿 Plant Leaf\nImage] --> B
    B[📷 Image\nAcquisition\nCamera / UAV / IoT] --> C
    C[⚙️ Image\nPreprocessing\nNoise · Resize · Filter] --> D
    D[🔍 Feature\nExtraction\nColor · Texture · Pattern] --> E
    E[🧠 Deep Learning\nCNN Model] --> F
    F[🏷️ Disease\nClassification\nHealthy / Diseased] --> G
    G[💊 Farmer\nRecommendation\nTreatment / Action]

    style A fill:#e8f5e9,stroke:#2e7d32,color:#1b5e20,rx:12
    style B fill:#e3f2fd,stroke:#1565c0,color:#0d47a1,rx:12
    style C fill:#fff3e0,stroke:#e65100,color:#bf360c,rx:12
    style D fill:#fce4ec,stroke:#880e4f,color:#880e4f,rx:12
    style E fill:#ede7f6,stroke:#4527a0,color:#311b92,rx:12
    style F fill:#e0f7fa,stroke:#006064,color:#004d40,rx:12
    style G fill:#f9fbe7,stroke:#558b2f,color:#33691e,rx:12
