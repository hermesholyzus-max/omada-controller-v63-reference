# Omada Controller V6.3 Reference — Start Here

This is a portable, citation-oriented skill for the TP-Link Omada SDN Controller V6.3 guide. It contains concise paraphrased notes and source-page routing only. It does **not** include the copyrighted PDF, controller exports, credentials, device backups, or any live configuration.

## For a person

1. Keep the original guide in the document store already used for it; do not add the PDF to this distribution or a Git repository unless separately authorized.
2. To make a local verification copy, place the original PDF at the relative path shown in [`SOURCE.md`](SOURCE.md): `source/Omada SDN Controller_V6.3_User Guide.pdf`.
3. Verify its SHA-256 and physical page count before relying on it.
4. Read `SKILL.md` for scope and safety boundaries; use `references/topic-index.md` to locate a subject and `references/operations.md` for cautious workflows.

## For an agent

1. Load `SKILL.md`.
2. Identify the controller form, target site/view, device model and firmware, desired result, and service-interruption risk.
3. Load the relevant reference file before offering procedural guidance.
4. Cite physical PDF pages as `PDF p.` and treat the notes as routing/paraphrase, not proof of device-specific support.
5. Do not make controller, cloud, SSH, CLI, or network changes without explicit authorization.

## Contents

- `SKILL.md` — agent instructions, scope, and routing
- `references/topic-index.md` — chapter/topic → physical PDF page index
- `references/operations.md` — safe, practical guidance and disruption cautions
- `SOURCE.md` — relative-path source retrieval and integrity instructions
- `.gitignore` — prevents accidental inclusion of the original PDF or generated local extracts
