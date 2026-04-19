# Game Churn Prediction AI - System Architecture

This document contains the system architecture diagram for the Game Churn Prediction AI project, illustrating the end-to-end Machine Learning pipeline, the newly integrated Agentic AI Assistant, and the Streamlit application flow.

## Architecture Diagram (Mermaid)

```mermaid
graph TD
    %% Input Layer
    subgraph Input_Layer [Input Layer]
        A[User Upload CSV] --> B{Streamlit UI}
    end

    %% Core Application Layer
    subgraph App_Layer [Streamlit Application Layer]
        B --> C[Data Preprocessing & Validation]
        C --> D[Churn Prediction Model]
        
        %% Model predicting and returning to UI
        D --> |Predict Probabilities & Risk Levels| B
        D --> |Extracted Feature Importance| B
    end

    %% AI Agent Layer
    subgraph Agent_Layer [Agentic AI Assistant]
        B --> |Request Engagement Analysis| E[Engagement Agent]
        E --> |Query Strategies| F[(Knowledge Base: strategies.json)]
        F --> |Return Strategies| E
    end

    %% Output & Reporting Layer
    subgraph Output_Layer [Reporting & Output Layer]
        E --> |Pass Recommendations| G[Report Generator]
        G --> |Format Structured Report| B
        G --> |Generate PDF Export| B
        
        %% Results
        B --> H[Display Probabilities, Insights, & Report]
        B --> I[Download CSV/PDF]
    end
    
    %% Styling Classes
    classDef default fill:#ffffff,stroke:#333,stroke-width:1px,color:#333;
    classDef input fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:#000;
    classDef app fill:#f3e5f5,stroke:#7b1fa2,stroke-width:2px,color:#000;
    classDef agent fill:#e8f5e9,stroke:#388e3c,stroke-width:2px,color:#000;
    classDef know fill:#fff3e0,stroke:#f57c00,stroke-width:2px,color:#000;
    classDef output fill:#ffebee,stroke:#d32f2f,stroke-width:2px,color:#000;

    class A input;
    class B,C,D app;
    class E agent;
    class F know;
    class G,H,I output;
```