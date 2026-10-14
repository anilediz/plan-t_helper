# PROJECT FACTS — Plan-t

PROJECT OWNER: Tuğberk. Agents may propose changes to this file; they apply them only after the owner confirms in the session, and record the change in the session file.
VERIFIED AGAINST: fork snapshot, master at commit 920c18bb2a71 (2026-09-17), checked 2026-10-14: paths, file sizes, scripts, test files, branch list. UNVERIFIED against the owner's working repository (it may be newer and was later touched by another rule set). Re-check lines marked UNVERIFIED on first use.

## 1. Product in one paragraph

Plan-t is the admin side of an eco-farm system: zones named on an uploaded map, what is planted, checks, irrigation, and which workers are assigned to which zones and what they did. Accumulated data may later feed an internal advisory service. The UI is Turkish-first. Workspaces are multi-user.

## 2. Product rules recorded by the owner

- Roles include Owner, Manager, Staff, Volunteer and Visitor.
- A staff member can propose a change on the map; it is not applied without a manager's approval.
- The activity-log schema is an owner decision, because later advice depends on it. Agents do not design it.

## 3. Limits

- File-count stop limit: 8 files per session (default; the owner may change it).
- Debugging attempt limit: 3 (set in CORE §7).

## 4. Where things live

- Frontend: frontend/prototype/ (vanilla JS). The OpenLayers map engine source is frontend/spatial-src/ (entry.js, openlayers-spatial-engine.js), bundled into frontend/prototype/plan-t-spatial.bundle.js.
- Backend: src/ (VenueOps.Api, VenueOps.Application, VenueOps.Domain, VenueOps.Infrastructure, VenueOps.Persistence); solution VenueOps.slnx.
- Tests: tests/frontend/*.test.js, tests/browser/ (UI contract fixtures), tests/VenueOps.Application.Tests, tests/VenueOps.Api.IntegrationTests.
- Docs: docs/architecture (ADR-001..003), docs/roadmap/development-clusters.md, docs/testing/TESTING.md, docs/Plan-T-development-launcher.md.
- Task-specific context: for frontend migration tasks, read docs/codex-context/frontend-migration.md.

## 5. Off-limits and read-carefully

- Do not open: frontend/prototype/plan-t-spatial.bundle.js (generated, about 380 KB), frontend/prototype/vendor/, package-lock.json, bin/, obj/, .tmp/, outputs/.
- Read only by search or line range: frontend/prototype/test.html (main page, about 315 KB).
- Do not open unless the brief names a migration task: src/VenueOps.Persistence/Migrations/.
- Do not open unless the brief names them: docs/technical-audits/* (large audit reports).

## 6. Architecture boundaries

- master is the product source of truth.
- frontend/prototype/spatial-application.js is the application boundary; frontend/spatial-src/openlayers-spatial-engine.js is the only map engine.
- Layout state stores presentation only, never backend or domain objects.
- Features that exist only in design references stay disabled with the message: "This feature is not ready yet."
- Do not copy changes from other branches without comparing against master. The branch codex/frontend-figma-migration is mentioned in docs but is not in the fork (UNVERIFIED whether it exists locally).
- Task, Note and Reminder are separate vertical slices, never one change.
- Authentication, users and workspace memberships exist (src/VenueOps.Api/Controllers/AuthController.cs, WorkspaceAuthorizationService). Treat them as stop-and-ask areas.

## 7. Runtime (Windows / PowerShell)

- Launcher: plan-t (installed once with scripts/install-plan-t-command.ps1; plan-t -NoBrowser to skip opening the browser).
- Start: .\scripts\start-dev.ps1 (process-scope alternative: powershell.exe -NoProfile -ExecutionPolicy Bypass -File .\scripts\start-dev.ps1). Check: .\scripts\check-dev.ps1. Stop: .\scripts\stop-dev.ps1 (stops only processes it started).
- Backend http://localhost:5261, frontend http://localhost:5500, app http://localhost:5500/test.html.
- A stale API process on 5261, or a backend moved to another port, breaks login. Check this first when login fails.
- Anonymous GET /api/auth/me returning 401 is normal.

## 8. Test commands

- Frontend unit: npm test
- UI contract check in an isolated browser: node scripts/check-ui.cjs (runs the app contracts and native interaction checks; writes a screenshot to outputs/).
- Read-only UI preview against the running backend: node scripts/preview-ui.cjs (port 5511).
- Spatial bundle build (only when frontend/spatial-src changes): npm run build
- Backend unit: dotnet test VenueOps.slnx -c Release --filter "Category=Unit"
- Backend integration: dotnet test tests\VenueOps.Api.IntegrationTests\VenueOps.Api.IntegrationTests.csproj -c Release --filter "Category=Integration"
- PostgreSQL tests: only with TEST_DATABASE_CONNECTION_STRING set to a database whose name contains "test" and is not "venueops". Never point tests at the venueops database.
- Use -c Release while a Debug API is running, to avoid locked files.
- Every new endpoint needs the checklist in docs/testing/TESTING.md (success contract, invalid route/body, not found, 401/403, cross-workspace rejection, PostgreSQL constraint, storage cleanup, Swagger contract).

## 9. Planning and task tracking

- Plans, priorities, vision ideas and technical debt live in the owner's "Dev panosu" sheet, outside the repository. The repository holds only session briefs and reports.
