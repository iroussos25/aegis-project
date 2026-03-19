# Aegis AI: An Architectural Stress-Test (Next.js vs. Rails 7)

### **The Mission**
Aegis is a Clinical Decision Support (CDS) agent built for high-stakes ICU/ER environments. In clinical settings, **latency isn't just a UX metric—it's a clinical barrier.** To find the "Performance Ceiling" for AI-driven medical insights, I engineered the platform twice using two fundamentally different architectural philosophies. 

This repository serves as the **Technical Case Study** and the central hub for both implementations.

---

### **The Architecture Battle Card**

| Metric | **Aegis: Next.js (Production)** | **Aegis on Rails (Benchmark)** |
| :--- | :--- | :--- |
| **Primary Stack** | TypeScript, Next.js 14, Tailwind | Ruby on Rails 7, Hotwire, Turbo |
| **Deployment** | Vercel (Edge-Optimized) | Fly.io (Centralized Monolith) |
| **Orchestration** | Serverless / Client-side Hydration | Sidekiq / Redis / SSR |
| **The Verdict** | **Winner: Superior Streaming UX** | **Insight: High Logic Density** |

---

### **Phase 1: The Next.js / TypeScript Build**
**[View Source Code](https://github.com/iroussos25/aegis_ai_cds)** | **[Live Demo](https://aegis-ai-cds.vercel.app)**

The initial build focused on **Developer Velocity** and **Reactive UI**. 
* **The "Win":** Leveraging Vercel’s global edge network allowed for an incredibly low **Time to First Token (TTFT)**. Even with complex RAG chains, the "perceived speed" for the clinician was nearly instantaneous.
* **The "Trade-off":** Managing state across serverless functions required meticulous coordination of the orchestration layer, though the ecosystem support for AI streaming is unparalleled.

### **Phase 2: The Rails 7 / Hotwire "Speed" Port**
**[View Source Code](https://github.com/iroussos25/ai-clin-cds-rails)** | **[Live Demo](https://ai-clin-cds-rails.fly.dev)**

I re-engineered the platform in Ruby on Rails to see if a monolithic approach could reduce the "Serverless Tax" and simplify the AI orchestration logic.
* **The "Win":** Achieved a **60% reduction in JavaScript payload** and a cleaner "single source of truth" for medical logic.
* **The "Friction":** Despite the backend efficiency, the centralized deployment created a "latency wall" for streaming responses compared to edge-delivery. The development experience (DX) also highlighted the importance of environment parity when working outside of a native Linux interface.

---

### **The Verdict**
While Rails provided a robust, "batteries-included" environment for complex logic, **Next.js remains the production standard for Aegis AI.** In a clinical context, the **Edge-Network Advantage**—where the AI response starts streaming the moment the clinician finishes their query—outweighs the theoretical benefits of monolithic density. **I prioritize the clinician's time over architectural tradition.**

---

### **Technical Deep Dives**
* [RAG Grounding with Supabase & pgvector](https://github.com/iroussos25/aegis-ai-cds)
* [Optimizing LLM Streaming for Clinical Environments](https://github.com/iroussos25/aegis-ai-cds)

---
*Created by Giannis Roussos | Full-Stack Builder | [Portfolio](https://www.giannisroussos.com)*
