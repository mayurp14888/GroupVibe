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

# GroupVibe

GroupVibe is the working product identity for **NexusCode / NexusChat**, an enterprise AI development and collaboration platform. It combines real-time group chat, multi-provider AI orchestration, AI-assisted development tasks, and governed team workspaces.

The central product idea is simple: humans and AI models should be first-class participants in the same shared workspace, while development work remains traceable from requirement to result.

## Product Scope

GroupVibe is designed for engineering teams, product and design groups, agencies, privacy-sensitive organizations, and communities that need shared AI workspaces. The platform includes:

- invite-based workspaces with hierarchical groups and role-based permissions;
- real-time channels where multiple humans and AI models collaborate;
- AI tasks that turn natural-language requirements into plans, code, tests, and reviewable results;
- isolated cloud development environments with terminals, files, builds, tests, and previews;
- modular integrations for OpenRouter, Groq, Anthropic, OpenAI, NVIDIA NIM, xAI, local models, and custom endpoints;
- free-first model routing with explicit paid-model overrides;
- credit, token, quota, cost, and audit tracking;
- Web, Desktop, Mobile, and self-hosted deployment support.

## Core Features

### Collaboration

- Workspace and group management
- Email or link-based member invitations
- Role-based and resource-level authorization
- Real-time channels, presence, typing indicators, history, search, threads, reactions, and file sharing
- Channel memory, pinned context, notifications, and audit logs

### AI Platform

- Unified provider adapter interface for native and OpenAI-compatible APIs
- Model catalog with free/paid status, context limits, strengths, pricing, latency, and availability
- Streaming responses and `@model` mentions in group chat
- Channel personas, system prompts, tool calling, skills, rules, and MCP-style extensions
- Provider failure handling, rate-limit fallback, and credential validation

### AI Tasks and Development Environments

- Task creation from the UI or directly from chat
- Task lifecycle: pending, running, waiting, completed, and failed
- Requirement-to-plan-to-result workflow
- Git repository association and result attachments back into chat
- Isolated containers or VMs with web terminal, file browser, build, test, and preview hooks
- Automatic cleanup and resource-isolation policies

### Routing and Governance

- Free-first routing when a suitable free model is available
- Ranking by quality, latency, and availability
- Explicit model selection always takes precedence
- Workspace and group API key and model controls
- Hierarchical quota inheritance, soft and hard limits, alerts, and spend caps
- Immutable token and credit usage ledger with admin dashboards

## Delivery Roadmap

The requirements document estimates 20-26 weeks for a production-ready MVP.

### Phase 0: Foundation and Architecture

Reverse-engineer the reference platform, define the domain model, establish the monorepo and CI/CD, select the final stack, document security standards, and create the design system.

### Phase 1: Core Platform and Human Collaboration

Implement authentication, workspaces, groups, invitations, permissions, real-time human chat, message persistence, search, files, presence, and responsive web support.

### Phase 2: Multi-Provider AI and Free-First Routing

Add provider adapters, the model catalog, API-key management, free-first ranking, streaming AI messages, model mentions, channel prompts, and token counting.

### Phase 3: AI Tasks and Cloud Execution

Build the task state machine, isolated development environments, terminal and file access, build/test/preview hooks, Git integration, and chat-task linking.

### Phase 4: Governance and Usage Metering

Add credits, inherited quotas, immutable usage records, admin analytics, advanced permissions, extensibility, parallel model responses, and channel memory.

### Phase 5: Multi-Client Production Readiness

Deliver Desktop and Mobile foundations, PWA improvements, security and load testing, observability, self-hosted packaging, documentation, and production launch.

## Technical Direction

The primary architecture follows the MonkeyCode-inspired requirements while keeping provider support and group chat as first-class differentiators.

### Backend

- Go 1.23+
- Clean Architecture: Handler -> Usecase -> Repository
- Echo or Fiber with Ent or GORM
- PostgreSQL 16
- Redis for caching, queues, and real-time support
- ClickHouse or TimescaleDB for optional analytics and metering
- S3-compatible object storage such as MinIO, Cloudflare R2, or AWS S3
- REST and WebSocket APIs
- Temporal, gRPC, or a dedicated orchestration service for task environments

### Clients

- React 19, TypeScript, Vite, React Router
- Tailwind CSS, shadcn/ui, and Radix UI
- TanStack Query and Zustand
- xterm.js for cloud terminals
- TipTap or Lexical for rich content
- Tauri 2 for Desktop, with Electron as an alternative
- React Native with Expo for Mobile

### Operations

- Docker and Docker Compose for self-hosted deployments
- Kubernetes and Helm as a later deployment option
- GitHub Actions for CI/CD
- OpenTelemetry, Grafana or Datadog, and Sentry
- Vault, Doppler, or a cloud secret manager
- Cloudflare for CDN and WAF

## Security and Reliability

Security and data sovereignty are core requirements. Planned controls include encryption in transit and at rest, secure API-key management, input validation, rate limiting, dependency scanning, OWASP review, audit logging, and private deployment support.

Operational targets are:

- 99.9% availability
- Human message latency below 300 ms at p95
- AI first-token latency below 2.5 s at p95, subject to provider performance
- Support for 1,000+ concurrent users in a large workspace
- RPO of 5 minutes or less and RTO of 30 minutes or less
- Token and cost tracking within 2% of provider reports

## Testing Strategy

Testing will cover authentication and authorization, concurrent messaging, provider adapters and streaming, free-first routing, task state transitions, environment isolation and cleanup, quota inheritance, ledger immutability, cross-client synchronization, security, failover, load, and chaos scenarios.

Key acceptance targets include free-model preference of at least 95% when eligible, explicit model selection being honored, accurate token counts within 2%, and reliable real-time task and chat updates.

## Project Status

This repository is currently in the requirements and architecture planning stage. The source of truth for the current scope is [AI_Collaborative_GroupChat_Requirements (1).txt](AI_Collaborative_GroupChat_Requirements%20(1).txt).

Next actions:

1. Record architecture decisions for the final stack.
2. Define the domain model, database schema, and API surface.
3. Create the monorepo skeleton, CI/CD, and security baseline.
4. Design the Task Workspace and Group Chat user flows.
5. Implement the Phase 1 authentication and collaboration foundation.

Product naming remains provisional: NexusCode / NexusChat is used in the requirements, while GroupVibe is the current repository and product identity.
