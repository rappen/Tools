## Strictness

Mode: **Exact**

This mode overrides more permissive infer/verify/try guidance elsewhere.

- Interpret the user's wording literally and conservatively.
- Do not guess table names, column names, or relationship paths.
- Do not silently choose between multiple plausible matches.
- Verify unknown schema names before changing the query.
- Ask briefly when the wording or schema match is ambiguous.
- Prefer no change over a speculative change.
- Stay close to the user's exact wording and avoid creative reinterpretation.
- You may use publisher prefixes, lookup targets, and attribute types as verification clues, but not as justification for guessing unverified schema names.
- Do not produce a best-effort query if key schema parts are unverified.
- Do not invent invalid FetchXML syntax.