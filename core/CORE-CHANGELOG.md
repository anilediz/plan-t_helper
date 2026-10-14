# CHANGELOG — PLAN-T HELPER CORE

Maintained by the helper provider. Entries are added only with a new plan-t_helper release.

────────────────────────────────────────
VERSION: 1.2
DATE: 2026-10-14
BASE: 1.1
PATCH COUNT: 5
─────────────────────────────────────────────
CORE.md — LAAS
v1.2
~ §12 Language becomes a hard boundary: everything addressed to the project owner is Turkish; files, briefs, reports, logs, commits and internal reasoning stay English; new app UI text is Turkish
~ §2 CORE-change notice delivered in Turkish
★ Owner-facing language is no longer "the user's language" but fixed to Turkish
─────────────────────────────────────────────
PLANNER.md — LAAS
v1.2
~ Language: owner-facing Turkish only; briefs English; verdict word English, explained in Turkish
─────────────────────────────────────────────
OPEN DEFECTS CARRIED FORWARD: enforcement is instruction-level only; no model validated; internal-reasoning language cannot be enforced by instruction on every model
DEPENDENCY NOTES: project-template PROJECT.md gains Language and Installed rule sets sections; disabled-state fact corrected to the app's Turkish feature-flag pattern
────────────────────────────────────────

────────────────────────────────────────
VERSION: 1.1
DATE: 2026-10-14
BASE: 1.0
PATCH COUNT: 6
─────────────────────────────────────────────
CORE.md — LAAS
v1.1
~ Personal names removed; authority refers to "the project owner" (named in PROJECT.md) and "the helper provider"
~ CORE lock message routes to the helper provider
~ §13 extended: other installed rule sets apply inside CORE's limits
★ CORE is now an installed copy of an upstream release; local edits are never authoritative
─────────────────────────────────────────────
PLANNER.md — LAAS
v1.1
~ Personal names removed; "Dev panosu" generalised to "the owner's task board"
─────────────────────────────────────────────
OPEN DEFECTS CARRIED FORWARD: enforcement is instruction-level only; no model validated yet
DEPENDENCY NOTES: PROJECT.md and log/ are project-owned and never overwritten by updates
────────────────────────────────────────

────────────────────────────────────────
VERSION: 1.0
DATE: 2026-10-14
BASE: none (initial release)
PATCH COUNT: 0
─────────────────────────────────────────────
CORE.md — NEW
v1.0
+ Authority, CORE lock, session lifecycle, proposals vs decisions, stop-and-ask, hard boundaries, debugging cap, test reporting, defaults logging, log maintenance, trust boundary, language, adapters
─────────────────────────────────────────────
PLANNER.md — NEW
v1.0
+ Planner role for chat assistants: breakdown, session briefs, strict report review
────────────────────────────────────────
