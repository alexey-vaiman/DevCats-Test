# Key AI Prompts Summary

This file summarizes the most impactful prompts used to drive the agents during development.

## 1. Frontend Architecture
**Prompt**: *"I want to build a frontend that is as modular as possible. Use Vue 3 with Feature-Sliced Design (FSD). Ensure all data structures are strictly typed and separate entities like 'Product' and 'User' into their own vertical slices."*

## 2. Backend Performance
**Prompt**: *"The backend must handle high concurrency. Use FastAPI and SQLAlchemy. Audit all queries to ensure no N+1 problems. If there are heavy operations like image processing, ensure they do not block the Event Loop."*

## 3. Premium UI Design
**Prompt**: *"Design the interface to feel premium, using HSL-based color tokens, glassmorphism, and subtle micro-animations. Avoid generic browser defaults. Use Lucide for icons."*

## 4. Scalable Pagination
**Prompt**: *"Implement infinite scrolling for the product list. Use cursor-based pagination on the backend and a virtual scroller on the frontend to handle 10k+ items without lag."*
