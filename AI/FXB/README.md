# FetchXML Builder – AI Instructions

This folder contains the AI instruction files used by **FetchXML Builder** in **XrmToolBox**.

These files define how the AI assistant helps users build, modify, and explain **FetchXML queries**.  
They are split into separate files to keep responsibilities clear and avoid prompt conflicts.

---

## Instruction Set

These files are combined into the main **instruction** sent to the AI.

- [System.md](System.md)  
  Defines system-level rules, scope, and non-negotiable constraints for the assistant.

- [Behavior.md](Behavior.md)  
  Describes how the AI uses metadata, updates FetchXML, handles execution, and explains queries.

- [Style.md](Style.md)  
  Controls tone, personality, and how the user is addressed.

- [Preferences.md](Preferences.md)  
  Contains naming conventions, output formatting rules, and interaction preferences.

- [UserFlavors.md](UserFlavors.md)
  Injects optional user-specific guidance so the assistant can adapt to different user flavors.

### Strictness profiles

One strictness file can also be included in the instruction set to control how cautiously or boldly the AI should interpret the user's request.

- [Strictness.Relaxed.md](Strictness.Relaxed.md)
  Favors progress and likely interpretations when the intent seems clear enough.

- [Strictness.Balanced.md](Strictness.Balanced.md)
  Balances helpful inference with brief verification when uncertainty matters.

- [Strictness.Exact.md](Strictness.Exact.md)
  Favors literal interpretation and verification over guesswork.

---

## Runtime context

At runtime, FetchXML Builder injects dynamic context into the instructions, such as:

- The current FetchXML query
- The user’s preferred name
- Schema metadata information
- The active strictness mode, when used

Placeholders (for example `{{fetchxml}}` or `{{callme}}`) are populated by the tool and must not be modified.

---

## Helper Prompt Files

These prompt files are used during sampling to help the AI resolve specific runtime subtasks.

- [Updated.md](Updated.md)
  Re-states the latest FetchXML and marks it as the authoritative current query for subsequent steps.

- [EntityMeta.md](EntityMeta.md)
  Helps the AI match one requested table name or description to candidate Dataverse tables using supplied metadata only.

- [AttributeMeta.md](AttributeMeta.md)
  Helps the AI match one requested column description to candidate Dataverse columns for a known table using supplied metadata only.

- [RelationshipMeta.md](RelationshipMeta.md)
  Helps the AI match one requested relationship description to candidate related tables and relationships for a known table using supplied metadata only.

---

## Notes

- The AI does not have access to live Dataverse data
- FetchXML Builder sends schema metadata and current query context, not Dataverse record data
- All schema knowledge comes from schema metadata provided by FetchXML Builder
- Instructions are written in Markdown for readability and maintainability

---

## Instruction architecture

The instruction files are treated as **compiled templates**, not dynamic prompts.

Before being sent to the AI model, FetchXML Builder:

1. Loads each instruction file
2. Replaces placeholders (for example `{{fetchxml}}`, `{{prefer}}`, `{{callme}}`)
3. Sends the fully resolved instructions to the model

As a result:

- The AI never sees placeholders
- All preferences are already decided
- Instructions are interpreted as factual and authoritative

This design avoids conditional logic in prompts and produces more deterministic behavior.

---

## Links

This page: <a href="https://rappen.github.io/Tools/AI/FXB/" target="_blank">https://rappen.github.io/Tools/AI/FXB/</a>

FetchXML Builder: <a href="https://fetchxmlbuilder.com/" target="_blank">https://fetchxmlbuilder.com/</a>

FXB AI Chat: <a href="https://fetchxmlbuilder.com/features/ai/" target="_blank">https://fetchxmlbuilder.com/features/ai/</a>
