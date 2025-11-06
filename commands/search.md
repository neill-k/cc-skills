---
name: skills-search
description: Search for skills in the CC Skills Marketplace by name, description, tags, or category
---

# Search Skills Marketplace

You are helping the user search for specific skills in the CC Skills Marketplace. Follow these instructions to perform the search and display relevant results.

## Instructions

1. **Parse Search Query**: The user will provide a search query after the command (e.g., `/skills-search testing` or `/skills-search api design`).

2. **Read the Skills Catalog**: Load the skills registry from `registry/skills-catalog.json`.

3. **Perform Search**: Search across the following fields:
   - Skill name
   - Description
   - Tags
   - Category
   - Skill ID

4. **Match Criteria**: Use case-insensitive matching. A skill matches if the query appears in any of the searched fields. Support multi-word queries by matching if ALL words appear (in any order).

5. **Rank Results**: Prioritize matches based on:
   - Exact skill name match (highest)
   - Skill ID match
   - Tag match
   - Description match
   - Category match

6. **Display Results**: Format each matching skill as:

```
### [Skill Name] ⭐ (if featured)
**ID**: skill-id
**Category**: category-name
**Description**: Brief description
**Tags**: tag1, tag2, tag3
**Difficulty**: level | **Time**: X-Y minutes
**Install**: `/skills-install skill-id`

---
```

7. **Handle No Results**: If no skills match, suggest:
   - Trying broader search terms
   - Browsing all skills with `/skills-browse`
   - Checking spelling

## Example Usage

**Command**: `/skills-search api`

**Output**:
```
# Search Results for "api"

Found 2 matching skills:

### API Design Reviewer
**ID**: api-design-reviewer
**Category**: Development
**Description**: Review API designs for consistency, usability, and best practices
**Tags**: api, design, architecture, development
**Difficulty**: advanced | **Time**: 15-30 minutes
**Install**: `/skills-install api-design-reviewer`

---

### API Documentation Generator
**ID**: api-documentation
**Category**: Documentation
**Description**: Generate clear API documentation with endpoints, parameters, examples
**Tags**: documentation, api, openapi, swagger
**Difficulty**: intermediate | **Time**: 15-25 minutes
**Install**: `/skills-install api-documentation`

---

**Tip**: Use `/skills-info <skill-id>` to see more details about a skill.
```

## Important Notes

- Always show the number of results found
- If more than 10 results, show top 10 and indicate there are more
- Include navigation hints at the end
- Handle empty or whitespace-only queries gracefully
- Preserve the case of skill names and descriptions in output
