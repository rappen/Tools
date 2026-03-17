# Copilot Instructions

## General Guidelines
- Use lowercase for placeholders and related tokens in AI instruction templates (e.g., `{{callme}}`, `{{prefer}}`, `{{fetchxml}}`).
- Standardize placeholder tokens to lowercase and use double curly braces `{{token}}` for FetchXML Builder AI instruction templates; update runtime replacement code accordingly.
- Ensure instructions are concise and actionable; prefer clearer, more accessible summaries for better understanding.
- Use imperative mood ("Use X", not "You should use X").
- Avoid redundant phrases.
- When improving docs/AI instruction pages, prefer minimal, non-messy visual adjustments; avoid adding extra explanatory blocks unless necessary.

## Code Style
- Follow specific formatting rules.
- Maintain consistent indentation and spacing.
- Preserve existing formatting conventions (code blocks, emphasis, links).

## Project-Specific Rules
- Check for existing instructions with the same semantic meaning before adding new ones.
- If found, enhance the existing instruction rather than adding a duplicate.
- If the new memory is more specific or comprehensive, replace the old one.
- If they complement each other, merge them into a single, cohesive instruction.
- Group semantically related instructions together, placing general instructions before specific ones.
- Create new sections only when the instruction doesn't fit existing categories.
- For FetchXML Builder AI instructions, prefer inner joins (link-entity default) unless the user requests otherwise.