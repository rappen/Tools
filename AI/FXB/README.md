# FetchXML Builder – AI Instructions

This folder contains the AI instruction files used by **FetchXML Builder** in **XrmToolBox**.

The instructions control how the AI assistant behaves when helping users build, modify, and explain **FetchXML queries**.  
They are intentionally split into separate files to avoid overlapping responsibilities and prompt conflicts.

---

## Files

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

- [Updated.md](Updated.md)
  Re-states the latest FetchXML and marks it as the authoritative current query for subsequent steps.

- [EntityMeta.md](EntityMeta.md)
  Helps the AI map a user's description to matching Dataverse tables using supplied entity metadata only.

- [AttributeMeta.md](AttributeMeta.md)
  Helps the AI map a user's description to matching Dataverse columns for a known table using supplied attribute metadata only.

---

## Runtime context

At runtime, FetchXML Builder injects dynamic context into the instructions, such as:

- The current FetchXML query
- The user’s preferred name
- Metadata information

Placeholders (for example `{{fetchxml}}` or `{{callme}}`) are populated by the tool and must not be modified.

---

## Notes

- The AI does not have access to live Dataverse data
- All schema knowledge comes from metadata provided by FetchXML Builder
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