# Overview
This repository demonstrates a small-scale **enterprise-grade multi-agent AI orchestration** pattern built using Flowise and OpenAI models.
The solution showcases how AI agents can be architected to:
  - Route requests through a master orchestration layer
  - FAQ answering using simple RAG implementation
  - Query structured SQL databases conversationally
  - Abstract legacy mainframe systems
  - Support multimodal interaction (Text + Voice)
  - Apply responsible AI guardrails

This implementation reflects **production-oriented architecture principles rather than a simple chatbot prototype**.

---

# Executive Summary
The implementation evaluates a **Master-Agent + Specialized-Agent architecture pattern**.
Instead of a monolithic AI bot, the system:
  - Uses a Master Agent for intent classification and routing
  - Delegates execution to domain-specific child agents
  - Maintains separation between UI, AI logic, and systems of record
  - Applies safety validation at both input and output boundaries
    
The design demonstrates how AI can be integrated **responsibly into enterprise and government systems**.

---

# Architecture Overview
The system follows a layered enterprise architecture:
  - **Presentation Layer**
    - FlowiseChatEmbed UI
    - Text and Voice input
  - **AI Orchestration Layer**
    - Master Agent (Intent Router)
    - LLM-driven routing logic
  - **Specialized Agent Layer**
    - SQL Conversational Agent
    - Mainframe Inquiry Agent
  - **Systems of Record**
    - Enterprise SQL Database
    - Legacy Mainframe System
  - **Governance Layer**
    - Input/Output content safety
    - Prompt injection mitigation
  <p align="center">
  <img src="architecture/solution architecture.png" width="600"/>
</p>
<p align="center"><em>
Figure 1: Solution Architecture building block.
</em></p>

---

# Agent Implementation Pattern
 - **Master Agent**
   - **Responsibilities:**
        - Interprets user intent using LLM reasoning
        - Routes request to appropriate child workflow
        - Applies routing logic via structured system prompts
        - Maintains decoupling between UI and backend agents
    - Architectural Pattern:
       - Mediator Pattern + AI Intent Router Pattern
- **SQL Conversational Agent**
   - **Capabilities**
       - Natural Language → SQL translation
       - Secure database query execution
       - Result interpretation and formatting
       - Voice input support via OpenAI Whisper
- **Mainframe Inquiry Agent**
    - **Capabilities**
       - Civil ID or card number validation
       - API-based backend integration
       - Structured response generation
       - Output safety validation

---

# Responsible AI & Governance
  - Input content safety validation
  - Output content safety validation
  - Controlled system prompts
  - Prompt injection mitigation
  - Langsmith observability & monitoring integration
  - Clear separation between business logic and safety layer

---

# Technology Stack & Extensibility
 - **Core Technologies**: 
    - Flowise (Agent orchestration)
    - OpenAI GPT models (Reasoning & intent classification)
    - OpenAI Whisper (Speech-to-text)
    - SQL Database
    - API abstraction layer for legacy integration
 - **Extensibility**
    - RAG agent (using vector DB) for question-answering
    - Document processing agent for key attributes extraction (from contract document) and populate to system of records
    - RBAC
