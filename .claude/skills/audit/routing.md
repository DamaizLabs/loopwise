# Routing and skill checks

Required for every audit. Keep checks bounded and read-only. Never install, synchronize, rename, or run project workflows merely to audit them.

## 1. Establish what to check

- Read the root `CLAUDE.md`, scoped overrides, and the indexes it routes to. Identify the canonical source for each kind of information. Do not assume the newest file is authoritative.
- Inventory the project skills in `.claude/skills/` and any user-level skills the manual relies on. Folder presence alone proves neither availability nor precedence. Record the Claude Code version when available.
- Report scope numerically: manuals read, skills checked, resources checked, and workflows exercised. State what was sampled or omitted. A metadata check is not an execution test.

## 2. Check routes in both directions

- **Route to target:** resolve concrete paths from the correct base (repository, containing file, declared working directory, user home, or separate host). Verify existence and intended destination. Distinguish concrete references from placeholders, examples, globs, URLs, and remote-host paths. A remote path unavailable locally is unverified, not automatically broken.
- **Important target to route:** compare the relevant indexes/manuals with immediate project, knowledge, and skill inventories. Follow index chains; a nested project can be properly routed without a direct root-manual link. Identify useful active material with no usable entry route, using evidence of its relevance. An unclassified folder is a candidate for review, not automatically an orphan.
- Check obsolete usernames, moved folders, platform-specific absolute paths, wrong folder spelling/case where material, stale aliases/counts, archived material shown as active, and links pointing at the wrong valid destination. An existing path can still be wrong.
- Do not flag every unlinked file. Scratch, generated files, dependencies, archives, and intentionally private/specialist material may be correctly excluded. Distinguish stale factual content from an old file whose contents remain accurate.

## 3. Check skills and their resources

Match skills by declared name and purpose, not folder name alone. Inventory broadly by metadata, then inspect required resources for the selected workflows and any suspected problem.

1. **Content:** workflow steps, inputs, outputs, and boundaries match what the manual promises.
2. **Resources:** required scripts, templates, examples, assets, dependency instructions, and agent references resolve from the project. Broken symlinks and targets outside the checkout need explicit evidence.
3. **Discovery:** distinguish present on disk, listed by Claude Code, disabled, and not checked. Detect duplicate names across project and user skills and determine which one wins where supported. Report ambiguity if precedence cannot be verified. Do not assume presence in a menu means successful execution.
4. **Behavior:** check incompatible tool calls, unsupported instructions, wrong working directories, platform commands, missing environment-variable names without revealing values, and undocumented dependencies. Use safe existing evidence for actual execution; leave paid, posting, or other side-effecting workflows untested in a read-only audit.

## 4. Communicate the result

Use these finding classes:

- **Confirmed defect:** evidence shows a missing required route/resource, conflicting instruction, broken path, or unavailable required skill.
- **Verification gap:** discovery, remote access, intent, or execution was not established. State the smallest check that would resolve it.
- **Intentional difference:** a documented, deliberate exception, such as a route that points outside the project on purpose. No repair needed.
- **Improvement opportunity:** a useful simplification or extension without a demonstrated failure. Explain the benefit without calling it broken.

Show a compact routing table, using actual paths:

| Item | Evidence | Finding / ID | Practical consequence |
|---|---|---|---|
| Manual route | File/section and resolved target | Valid / broken / unlinked / not checked | Effect on retrieval |
| Sampled skill | Path and listing status | Works / missing resource / disabled / not checked | What works or fails |
| Required resource | Resolved path | Valid / broken / not checked | Effect on execution |

Follow with only actionable findings, grouped by class:

| ID / class / priority | Evidence and affected route or skill | User impact | Proposed change or verification | Completion check |
|---|---|---|---|---|
| Stable ID; repair, verify, or opportunity | Exact file/line or dated run result | Concrete failure or uncertainty | Edit, route addition, or read-only check | Observable result |

Prioritize wrong answers, lost instructions, unavailable workflows, and unsafe permissions over cosmetic differences. Use one ID for an underlying issue across manual, routing, and skill sections. Do not hide a confirmed lower-priority defect because only three actions are recommended. No fifth score, no score bonus for duplicate files. No automatic repairs.

## Calibration cases

- A relevant project is reachable through a domain index: routed; scratch with no incoming link is not a defect.
- A skill's `SKILL.md` resolves but a required template is missing: confirmed defect.
- Duplicate project/user skills exist but effective precedence is unknown: verification gap, not an assumed overwrite.
- A referenced remote host is unavailable during inspection: verification gap, not a broken local path.
- A skill is listed and enabled but was not run: discovery verified, execution unverified.
