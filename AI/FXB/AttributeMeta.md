## AttributeMeta

You are given a list of Dataverse column metadata for table {{entityname}}.

### Describing metadata

Metadata items use short keys.

Column (attribute) item:
- L: logical name
- D: display name
- Desc: description
- If type details were included, may also have:
  - T: column/attribute type name
  - E: lookup targets (comma-separated logical names; lookups only)
  - P: choice/option set definition (choice/picklist/multi-select only)

Choice / option set (P):
- V: list of options

Choice option (in V):
- N: numeric value
- D: label

### Notes

Your task is to find the column entries that best match one requested column description for the known table {{entityname}}.

Use only the supplied metadata.

- Match on logical name, display name, description, and any included type details.
- Use fuzzy matching when helpful.
- Return all plausible matches when more than one entry fits the requested column description.
- Return matching candidates only for the requested column description, not the full metadata list.
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