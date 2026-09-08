# GroupVibe

A collaborative multi-user, multi-AI group chat platform for teams, communities, and AI-powered workspaces.

## Overview

GroupVibe is a real-time web application designed to bring together human users and multiple AI models in a single shared workspace. The platform enables teams to collaborate in channels, invite members, and interact with a variety of AI providers in the same conversation flow.

The product is designed around a simple but powerful idea: people and AI models should behave like first-class participants in the same collaborative environment rather than as isolated one-to-one chat experiences.

This project is currently defined as NexusChat, with GroupVibe as the working product identity and collaborative workspace concept.

## Product Vision

GroupVibe aims to create a production-ready communication platform where:

- multiple humans can collaborate in shared channels;
- multiple AI models can participate in the same conversation;
- the system intelligently prefers free-tier models before paid models;
- cost, token, and quota usage are visible across users, workspaces, models, and channels;
- AI provider integrations are modular and scalable;
- workspace-level controls support enterprise and team usage patterns.

## Core Value Proposition

- True multi-user + multi-AI collaboration in one shared conversation
- Free-first model routing with fallback to paid models when necessary
- Granular visibility into token usage, quota consumption, and cost
- Workspace-based permissions and invite-driven collaboration
- Secure, production-grade architecture with observability and scalability

## Primary Use Cases

- Product, engineering, and research teams collaborating with multiple AI models
- Friend groups and small teams running shared AI-powered workspaces
- Agencies and consultancies that need controlled multi-model access with cost visibility

## Key Features

### Human Collaboration

- Workspace creation and switching
- Channel creation and channel-level organization
- Member invitations by email or shareable links
- Role-based access control for owners, admins, members, and guests
- Real-time messaging with presence, typing indicators, and read states
- Persistent chat history with pagination and search
- Responsive web experience for desktop and mobile
- File uploads for images and documents

### AI Collaboration

- Multi-provider AI support across OpenRouter, Groq, Anthropic, OpenAI, and NVIDIA NIM
- Model-aware mentions such as @claude, @gpt-4o, or @llama-3.3
- Server-side generation pipeline with streaming responses
- Channel-level persona or system prompts
- AI message differentiation with badges, avatars, and color-coded UX
- Context window management for recent conversation state
- Graceful handling of provider failures, rate limiting, and invalid credentials

### Smart Routing and Usage Controls

- Free-first intelligent model selection
- Ranking based on model quality, latency, and availability
- Explicit model selection override
- Fallback chain when free models are rate-limited or unavailable
- Token counting for input and output per AI call
- Cost estimation using provider pricing tables
- Workspace and user-level quota monitoring
- Admin controls for free-only mode and spend caps

### Collaboration Hardening

- Threaded replies
- Message reactions and pinning
- Full-text and filtered search
- Channel memory and pinned context
- Optional parallel multi-model responses
- File-based context injection for RAG-lite workflows
- Notifications and admin audit logging

## Product Goals

The MVP is designed to achieve the following success metrics:

- support 5+ major providers
- maintain free-first routing with over 95% preference accuracy when free models are available
- deliver sub-300ms message latency for real-time human chat at p95
- track token and cost usage with variance under 2% versus provider reports
- support 500 concurrent users per workspace without degradation
- achieve a strong mobile and desktop responsive experience score above 90

## Roadmap

### Phase 0: Foundation & Discovery

Focus on product definition, architecture design, data modeling, CI/CD setup, and UI foundation.

### Phase 1: Core Platform & Human Chat

Build onboarding, authentication, workspace management, chat basics, presence, and file uploads.

### Phase 2: Multi-Provider AI Integration

Connect and validate major provider adapters, add model metadata, AI streaming, and @mention support.

### Phase 3: Smart Router + Usage Tracking

Implement intelligent routing, token counting, cost estimation, and quota governance.

### Phase 4: Collaboration Hardening + Polish

Add advanced UX, threaded conversations, search, memory, notifications, and performance tuning.

### Phase 5: Production Readiness & Launch

Complete security review, observability, backup testing, load testing, compliance review, and production launch preparation.

## Architecture Overview

GroupVibe is planned as a production-grade web application with a modular architecture that separates concerns across frontend, backend, AI orchestration, data storage, and platform operations.

### Frontend

- Next.js 15 with App Router
- TypeScript
- Tailwind CSS
- shadcn/ui + Radix Primitives
- Zustand for client state
- TanStack Query for server-state management
- React Hook Form + Zod
- TipTap or Lexical for rich text
- Recharts or Tremor for analytics dashboards
- PWA support using next-pwa or Serwist
- Testing with Vitest, React Testing Library, and Playwright

### Backend

- Node.js 22 or Bun
- Next.js Route Handlers or tRPC-based API layer
- Vercel AI SDK for orchestration
- Custom provider adapter layer for abstraction across AI providers
- Trigger.dev, Inngest, or BullMQ + Redis for background jobs
- Auth solutions such as Clerk, Supabase Auth, or Auth.js
- Custom RBAC with authorization policies

### Data Layer

- PostgreSQL 16
- Prisma ORM
- Redis for caching
- Cloud storage via Cloudflare R2 or AWS S3
- PostgreSQL full-text search and future vector support using pgvector

### AI Provider Layer

- Unified provider adapter interface
- Native support for OpenRouter, Groq, Anthropic, OpenAI, and NVIDIA NIM
- Cost and token tracking
- Model catalog service with metadata such as free/paid status, context size, and strengths

### Infrastructure

- Vercel for frontend and serverless deployment
- Supabase, Neon, or AWS RDS for database hosting
- Cloudflare for CDN and WAF
- GitHub Actions for CI/CD
- OpenTelemetry, Grafana Cloud or Datadog, and Sentry for observability
- LaunchDarkly, Unleash, or PostHog for feature flags

## Security and Compliance

Security is a core requirement for production readiness.

Planned security controls include:

- encryption at rest and in transit
- secure workspace-level API key management
- rate limiting and abuse prevention
- input sanitization and validation
- dependency scanning and automated vulnerability monitoring
- OWASP Top 10 review
- audit logging for admin actions and AI usage

The project also includes a legal and compliance review path covering privacy policy, terms, and data-processing requirements.

## Reverse Engineering and Product Research

A deliberate reverse-engineering effort is included to understand the structure and patterns used by competitive platforms and open-source reference products.

The research focuses on:

- ChatGPT Teams / Enterprise patterns
- Claude Projects and team workflows
- Poe-style multi-bot interaction
- Character.AI group dynamics
- Slack and Microsoft Teams AI patterns
- Open-source systems such as Open WebUI, LibreChat, LobeChat, AnythingLLM, and ChatbotUI

The goal is to learn from proven real-world implementations and document architectural decisions, patterns to adopt, patterns to avoid, and technical risks.

## Non-Functional Targets

The platform is being designed with the following operational targets:

- Availability: 99.9%
- Human message latency: p95 < 300ms
- AI first-token latency: p95 < 2.5s
- Horizontal scalability for real-time and API workloads
- Configurable data retention with default retention of 12 months
- RPO <= 5 minutes and RTO <= 30 minutes

## Testing Strategy

The project includes both feature validation and regression coverage across all major phases.

### Primary testing themes

- authentication and authorization flows
- real-time messaging reliability
- provider integration and streaming behavior
- model routing correctness
- token and cost accuracy
- chat UI responsiveness
- security and observability checks
- load, stress, and failover validation

## Repository and Project Status

This repository is being created as the foundation for the product definition and implementation work for GroupVibe / NexusChat.

Current status:

- product requirements defined
- roadmap structured into five delivery phases
- technology stack selected for MVP and production scaling
- architecture decisions documented in the requirements brief

## Suggested Next Steps

1. Create the monorepo structure and initialize the application skeleton.
2. Set up authentication and workspace domain models.
3. Build the real-time human chat foundation.
4. Integrate the first AI provider adapters.
5. Add routing, quotas, and token accounting.
6. Run regression testing, security review, and production hardening.

## Summary

GroupVibe is a production-oriented AI collaborative workspace platform that blends real-time human communication with multi-provider AI orchestration. The platform is designed for teams, communities, and professional workgroups that need shared conversations, model choice flexibility, visibility into usage, and a scalable foundation for future AI-native collaboration.

This README reflects the initial product and technical requirements and will evolve as the project moves from planning to implementation.

---

## Project Definition Notes

- Product name used in requirements: NexusChat
- Working product identity used here: GroupVibe
- Current status: Requirements and architecture planning stage
- Review cadence: architecture review before major changes
- Approval status: pending stakeholder sign-off
