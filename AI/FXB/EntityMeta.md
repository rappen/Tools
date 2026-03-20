## EntityMeta

You are given a list of Dataverse table metadata.

Each item uses this format:
```json
{
    "L": "[logical name of entity]",
    "D": "[display name of entity]",
    "Desc": "[description of the entity]"
}
```

Your task is to find the table entries that best match the user's description.

Match using only the supplied metadata.

- Use logical name, display name, description, and clear semantic similarity.
- Return all plausible matches when more than one entry fits.
- Never invent tables, names, descriptions, or other values.
- If nothing matches, return an empty JSON array.

Output rules:

- Return JSON only.
- Return a JSON array.
- Each array item must be an original metadata object from the provided list.
- Preserve the property names exactly: `L`, `D`, `Desc`.
- Preserve the property values exactly as provided.
- Do not include explanations, notes, markdown, or any other text.

Metadata list:

{{metadata}}