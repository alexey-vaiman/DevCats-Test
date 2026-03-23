# AI-Driven Development Log

This document provides insight into the "negotiations" and collaboration between the human developer and various AI agents that shaped the DevCats Marketplace architecture.

## Negotiation History & Key Decisions

### 1. Architectural Foundation
-   **Decision**: Opted for **Feature-Sliced Design (FSD)** for the frontend over a flat `components/views` structure.
-   **Reasoning**: To ensure high maintainability and prevent the project from becoming a "monolithic mess" as complexity grows. AI suggested FSD to naturally enforce strict boundaries between layers.

### 2. High-Performance Asynchronous Backend
-   **Decision**: Strictly async-first approach using **aioboto3** and **FastAPI**.
-   **Reasoning**: To maximize throughput under load. AI identified potential bottlenecks in standard synchronous S3 libraries (`boto3`) and recommended `aioboto3`. 
-   **Bottleneck Handling**: Negotiated the use of `run_in_threadpool` for PIL image processing to prevent blocking the Event Loop during thumbnail generation.

### 3. Database Efficiency
-   **Decision**: Efficient SQL-side aggregations and `selectinload`.
-   **Reasoning**: Initial drafts tended toward Python-side sorting (as seen in older review artifacts). The AI "agent" insisted on utilizing the power of PostgreSQL for sorting and grouping, resulting in the current `func.min` implementation for nearest delivery dates.

### 4. Code Quality & Performance
-   **Cursor-based Pagination**: Negotiated to avoid the performance degradation of `OFFSET` on large datasets.
-   **Virtual Scrolling**: Adopted to prevent "painter's algorithm" issues on the frontend when scrolling through thousands of items.

## Prompt Philosophy

We utilized a "multi-agent" approach:
1.  **Architect Agent**: Focused on high-level design patterns (FSD, Layered Backend).
2.  **Performance Analyst Agent**: Audited queries for N+1 issues and identified blocking code.
3.  **UI/UX Specialist**: Crafted the premium design tokens and micro-animations.

---
*This collaboration ensured the project meets Middle+ standards in both architecture and engineering.*
