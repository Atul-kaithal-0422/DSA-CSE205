flowchart LR
    A["🌿 Plant Leaf<br/>Image"] --> B
    B["📷 Image Acquisition<br/>Camera / UAV / IoT"] --> C
    C["⚙️ Image Preprocessing<br/>Noise · Resize · Filter"] --> D
    D["🔍 Feature Extraction<br/>Color · Texture · Pattern"] --> E
    E["🧠 Deep Learning<br/>CNN Model"] --> F
    F["🏷️ Disease Classification<br/>Healthy / Diseased"] --> G
    G["💊 Farmer Recommendation<br/>Treatment / Action"]

    style A fill:#e8f5e9,stroke:#2e7d32,color:#1b5e20
    style B fill:#e3f2fd,stroke:#1565c0,color:#0d47a1
    style C fill:#fff3e0,stroke:#e65100,color:#bf360c
    style D fill:#fce4ec,stroke:#880e4f,color:#880e4f
    style E fill:#ede7f6,stroke:#4527a0,color:#311b92
    style F fill:#e0f7fa,stroke:#006064,color:#004d40
    style G fill:#f9fbe7,stroke:#558b2f,color:#33691e
