# Aegis AI: Clinical Decision Support

A clinical AI decision support system built twice - once in Next.js 14 and once in Ruby on Rails 7 - to compare how different architectures handle the same real-time medical reasoning workload.

**[Next.js Demo](https://aegis-ai-cds.vercel.app/) | [Rails Demo](https://ai-clin-cds-rails.fly.dev/) | [Portfolio Case Study](https://giannisroussos.com/projects/aegis)**

---

## What it does

Upload a clinical document (or use a pre-loaded scenario like sepsis or CHF), and the system:

1. Parses the document and extracts clinical context
2. Queries a RAG pipeline (Supabase pgvector) for relevant prior knowledge
3. Pulls live evidence from PubMed via the NCBI eUtils API
4. Sends the enriched context through a multi-model AI pipeline for clinical synthesis
5. Returns a structured analysis with source attribution and evidence citations

## Why two versions

I built the Next.js version first to optimize for edge latency and streaming (sub-2s time-to-first-token). Then I rebuilt the entire system in Ruby on Rails over a weekend to test whether a monolithic, stateful architecture would perform better for persistent clinical audit trails and background processing.

**Results:**
- Next.js: Faster TTFT (edge streaming), lighter JS payload after Rails rewrite comparison
- Rails: 60% faster total execution (5.6s vs 14.7s), 85% reduction in client-side JavaScript, persistent audit trail via PostgreSQL + Sidekiq

## Architecture

### Next.js version
- Next.js 14 (App Router), TypeScript, React 19
- Vercel AI SDK for streaming responses
- Supabase pgvector for RAG (768-dim embeddings via gemini-embedding-001)
- Zod schema validation on all API boundaries
- Upstash Redis rate limiting (sliding window + token bucket fallback)
- Deployed on Vercel

### Rails version
- Ruby on Rails 7 with Hotwire (Turbo + Stimulus)
- PostgreSQL with pgvector extension
- Sidekiq + Redis for background job processing
- ActiveRecord for persistent audit logging
- Deployed on Fly.io

### Shared
- Multi-model fallback chain: Gemini 2.5 Flash > Flash Lite > Gemma 3 4B > Gemma 1B
- Automatic 429/503 error recovery with cascade to next model
- PubMed literature grounding via NCBI eUtils REST API
- FHIR R4 data explorer (HAPI FHIR public server)
- Structured audit logging for every AI request

## Demo mode

The app ships with pre-loaded clinical scenarios (sepsis, CHF, delirium) 
so you can see the full pipeline in action without uploading your own 
documents. A guided walkthrough overlay explains each step of the 
reasoning process, and the LLMOps dashboard shows real-time inference 
cost, TTFT, and model selection for every request.

## Key technical decisions

- **Model fallback as load balancing:** Google's free tier tracks rate limits per model independently. The fallback chain is not just a safety net - it effectively distributes load across multiple models.
- **RAG chunking strategy:** 1,200 character chunks with 220-character overlap, tuned for clinical note paragraph boundaries.
- **Cosine similarity fallback:** If the Supabase RPC for vector search fails, the app computes cosine similarity in-app rather than returning no results.

## Run locally

### Next.js
```bash
cd aegis_ai_cds
cp .env.example .env.local
# Add your Google AI API key and Supabase credentials
npm install
npm run dev
```

### Rails
```bash
cd ai-clin-cds-rails
cp .env.example .env
# Add your Google AI API key and database credentials
bundle install
rails db:setup
bin/dev
```

## Tech stack

Next.js 14, Ruby on Rails 7, TypeScript, Ruby, React 19, Hotwire (Turbo/Stimulus), PostgreSQL, Supabase pgvector, Redis, Sidekiq, Vercel AI SDK, Google Gemini/Gemma, Zod, Upstash, PubMed API, HL7 FHIR R4, Vitest, GitHub Actions, Vercel, Fly.io

## Contact

Giannis Roussos - [giannisroussos.com](https://giannisroussos.com) | [LinkedIn](https://linkedin.com/in/giannisr) | grcodes@outlook.com
