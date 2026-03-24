## EntityMeta

You are given a list of Dataverse table metadata.

### Describing metadata

Metadata items use short keys.

Table item:
- L: table logical name
- D: table display name
- Desc: table description

Shape:
```json
{ "L": "...", "D": "...", "Desc": "..." }
```

### Notes

Your task is to find the table entries that best match one requested table name or description.

Use only the supplied metadata.

- Match on logical name, display name, description, and clear semantic similarity.
- Use fuzzy matching when helpful.
- Return all plausible matches when more than one entry fits the requested table description.
- Never invent values.
- If nothing matches, return an empty JSON array.

Output rules:

- Return JSON only.
- Return a JSON array.
- Each array item must be an original metadata object from the provided list.
- Preserve property names and values exactly as provided.
- Do not include explanations, notes, markdown, or any other text.

Metadata list:
```json
{{metadata}}
```