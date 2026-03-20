## AttributeMeta

You are given a list of Dataverse column metadata for a single table.

Each item uses this format:
```json
{
	"L": "[logical name of attribute]",
	"D": "[display name of attribute]",
	"Desc": "[description of the attribute]",
	"T": "[type of attribute]",
	"E": "[lookup target entity, when applicable]"
}
```

Your task is to find the column entries that best match the user's description.

Match using only the supplied metadata.

- Use logical name, display name, description, type, and clear semantic similarity.
- Use fuzzy matching when helpful, especially for likely name variations.
- Treat `E` as relevant only when the column type or the user's request indicates a lookup target matters.
- Return all plausible matches when more than one entry fits.
- Never invent columns, names, descriptions, types, lookup targets, or other values.
- If nothing matches, return an empty JSON array.

Output rules:

- Return JSON only.
- Return a JSON array.
- Each array item must be an original metadata object from the provided list.
- Preserve the property names exactly: `L`, `D`, `Desc`, `T`, `E`.
- Preserve the property values exactly as provided.
- Do not include explanations, notes, markdown, or any other text.

Metadata list:
```json
{{metadata}}
```