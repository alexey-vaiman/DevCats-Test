# AI Development Workflow

## Every Development Cycle
1. Validate domain model relevance.
2. Validate openapi.yaml consistency.
3. Update domain model if needed.
4. Update API spec if needed.
5. Generate:
   - backend code
   - frontend code
   - storage logic
   - migrations
   - docker configs
   - tests
6. Update documentation.
7. Perform system coherence check.

---

## Rules
- Все файлы генерируются полностью.
- Изменения в API → обновление openapi.yaml.
- Изменения в данных → обновление domain-model.md.
- Каждый новый эндпойнт обязан иметь тест.