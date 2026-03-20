# 🛡️ Aegis AI: Clinical Decision Support (CDS) System Architecture

### **Next.js | Ruby on Rails | LLMOps | FHIR R4 Integration**

Aegis AI is a dual-architecture benchmarking project designed to evaluate the performance, latency, and reliability of AI-driven Clinical Decision Support across different engineering patterns. Developed by an **Active ICU/ER Nurse** and **Veteran Special Forces Leader**, the platform prioritizes operational grounding over theoretical implementation.

**[🌐 Portfolio](https://www.giannisroussos.com)** | **[💻 GitHub Profile](https://github.com/iroussos25)**

---

## 🏗️ The Benchmarking Strategy
This root repository serves as the coordination point for two distinct implementations of the Aegis reasoning engine. The objective is to compare **Edge-Latency (Next.js)** against **Stateful Persistence (Rails)** in a high-acuity clinical context.

### 1. [Aegis-AI-CDS (Next.js 14)](https://github.com/iroussos25/aegis_ai_cds)
* **Architectural Focus:** Edge-latency and frontend orchestration.
* **Technical Driver:** Minimizes the "Time to First Token" (TTFT) by leveraging Vercel Edge Functions and a localized normalization layer.
* **Best For:** Real-time bedside analysis and mobile-first clinical interfaces.

### 2. [Aegis-on-Rails (Ruby on Rails 7)](https://github.com/iroussos25/ai-clin-cds-rails)
* **Architectural Focus:** Data persistence and background synchronization.
* **Technical Driver:** Utilizes a PostgreSQL backend and Sidekiq workers to manage longitudinal FHIR data syncing and a persistent audit trail.
* **Best For:** Comprehensive patient history tracking and retrospective clinical auditing.

---

## 🎁 Recruiter & Interview Kit
Designed for rapid evaluation of full-stack AI orchestration:
* **One-Click Demos:** Pre-loaded clinical scenarios (Sepsis, CHF, Delirium) across both platforms.
* **Guided Walkthroughs:** Step-by-step overlays to demonstrate how AI maps raw FHIR data into clinical insights.
* **LLMOps Dashboard:** Real-time visibility into inference costs ($0.0000078 avg), TTFT, and semantic consistency metrics.

## ⚙️ Core Technical Pillars
* **Clinical Reasoning Engine:** Codifying ICU/ER nursing logic into multi-tier model fallback chains (Gemini 2.5 Flash, Gemini Flash Lite, and Gemma 3).
* **FHIR Normalization:** Engineering proprietary mapping layers to transform nested FHIR R4 JSON into token-efficient, high-signal schemas.
* **Explainable AI (XAI):** Implementing direct source attribution logic that maps AI claims back to specific `ResourceID` points in the patient record.
* **System Resilience:** Multi-tier rate limiting via Upstash Redis and strict Zod schema validation across all API boundaries.

---

## ⚖️ Proprietary Notice & Licensing
**License: All Rights Reserved**

The architectural frameworks, UI patterns, and benchmarking metrics provided in these repositories are open for professional technical review. However, the core **Clinical Reasoning Engine prompts**, **FHIR Mapping weights**, and **Proprietary Logic Chains** are protected Intellectual Property.

*For inquiries regarding full-stack engineering, AI orchestration, or system licensing, contact: [grcodes@outlook.com](mailto:grcodes@outlook.com).*

---

## ⚡ Engineering Note
Aegis was architected using a high-velocity AI-orchestration workflow. By leveraging Claude 3.5 Opus to accelerate boilerplate and state logic, the system transitioned from initial concept to a deployed, multi-platform benchmark in under 6 hours.
