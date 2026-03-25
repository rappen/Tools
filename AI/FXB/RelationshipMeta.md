## RelationshipMeta

You are given a list of Dataverse relationship metadata for table {{entityname}}.

### Describing metadata

Metadata items use short keys.

Relationship item:
- L: logical name of the related table
- D: display name of the related table
- Desc: description of the related table
- R: relationship kind: `M:1`, `1:M`, or `M:M`
- F: FetchXML `link-entity` `from` attribute
- T: FetchXML `link-entity` `to` attribute
- I: intersect table logical name for `M:M`, if any
- X: intersect column connected to the current table for `M:M`, if any
- Y: intersect column connected to the related table for `M:M`, if any
- S: relationship schema name

### Notes

Your task is to match the best relationship entries for one requested relationship description for the known table {{entityname}}.

Use only the supplied metadata.

- Match on related table logical name, display name, description, relationship kind, and schema name.
- Use fuzzy matching when helpful.
- Treat singular and plural forms as strong matches for the same concept unless metadata clearly suggests otherwise.
- Do not require exact wording from the user.
- Consider common wording for related records, child records, parent records, lookup tables, and intersect tables.
- Prefer returning plausible candidate relationships rather than an empty array when the user term is a clear singular/plural or semantic variant of a likely relationship.
- Return all plausible matches when more than one entry fits the requested relationship description.
- Return matching candidates only for the requested relationship description, not the full metadata list.
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