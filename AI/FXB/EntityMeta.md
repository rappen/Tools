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

Your task is to match the best table entries for one requested table name or description.

Use only the supplied metadata.

- Match on logical name, display name, description, and clear semantic similarity.
- Use fuzzy matching when helpful.
- Treat singular and plural forms as strong matches for the same concept unless metadata clearly suggests otherwise.
- Do not require exact wording from the user.
- If the requested wording is plural, still consider singular table names as likely matches, and vice versa.
- If a plural related-record term is given, consider that it may refer to a child table in a 1:N relationship even if the table logical name itself is singular.
- Prefer returning plausible candidate tables rather than an empty array when the user term is a clear singular/plural or semantic variant of a likely table.
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

Additional matching rules for custom tables:

- In Dataverse, custom table schema names use a publisher prefix before the first underscore.
- If the user asks for "custom tables", "custom entities", or similar, treat a logical name containing an underscore as a strong signal.
- Use shared publisher prefix as a strong matching signal when such a prefix is explicit in the request or otherwise available in the provided context.
- Prefer plausible custom-table matches over an empty array when the request clearly asks for custom tables.
- Use this custom-table heuristic even when the display name or description does not explicitly contain the word "custom".