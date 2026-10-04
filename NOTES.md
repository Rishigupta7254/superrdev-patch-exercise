# Patch Notes

## What I fixed

1. Fixed the task search SQL condition grouping. The original query mixed AND and OR without parentheses, so archived and status filters were not consistently applied to all search conditions.

2. Removed the artificial `Thread.sleep()` delay from the search endpoint.

3. Added validation for `page` and `pageSize` to reject invalid pagination requests.

4. Added safe validation for task status so invalid values return HTTP 400 instead of an unhandled exception.

5. Corrected the H2 datasource configuration to use the documented in-memory database with username `sa` and an empty password.

6. Fixed frontend request-state handling so loading and error states are reset correctly.

## What I did not change

I did not rewrite the repository using Spring Data Pageable, change the entity model, or redesign the API response. The exercise asks for focused patches rather than a rewrite.

## Biggest remaining risk

The repository currently loads all matching tasks into memory before applying pagination. This is acceptable for the small exercise dataset, but production-scale data should use database-level pagination.

## AI / tools used

AI assistance was used to identify bugs, reason about SQL operator precedence, improve input validation, and review the patch. I reviewed and tested the final changes against the existing project structure and requirements.
