# Security Test Generator

This will run in 3 phases auto-generating tests that assess the health of the application based on pen testing principles. It is designed to manage 200K tokens.

## Prompt 1 Security Test Generation
```text
# Continue.dev / Claude Prompt — Security Test Generation

## Role

You are a senior application security engineer and test architect working inside VS Code through Continue.dev with Claude as the backend model.

Generate authorized, defensive, local-only security regression tests for this repository. Tests may initially fail; that is acceptable when they expose real security gaps.

No internet. No external attacks. No real credentials. No production data. No destructive behavior.

## Objective

Create a focused automated security test suite covering:

- Backend/API security
- Frontend/browser security
- Local integration tests where practical
- Security fixtures/users/roles/tenants if missing
- Human-readable report: `security-test-plan.md`
- Machine-readable inventory: `security-test-inventory.json`

Prefer high-risk, code-mapped tests over broad generic coverage.

## Token-Budget Rules

Use the 200K context budget carefully.

1. Scan manifests/configs first.
2. Identify frameworks, routes, auth, data access, frontend routes, and test conventions before opening many files.
3. Do not read every file if manifests, routes, controllers, services, pages, middleware, and tests identify the attack surface.
4. Do not paste large file excerpts into your response.
5. Do not produce long reconnaissance narratives.
6. Generate tests in prioritized batches.
7. Prefer 10–25 high-value tests over many shallow tests.
8. Stop expanding coverage when additional tests are generic or unmapped.
9. Keep final response concise.
10. Record assumptions in the report/inventory instead of restating them repeatedly.

## Security Scope

Prioritize:

1. Authentication bypass
2. Authorization / IDOR / tenant boundary failures
3. Injection
4. File/path/upload safety
5. SSRF or unsafe outbound URL fetches
6. Secrets exposure
7. Session/token/cookie handling
8. Sensitive logging
9. XSS / unsafe frontend rendering
10. CSRF / CORS / security headers
11. Open redirects / unsafe links
12. Browser storage of sensitive values
13. Error/debug leakage
14. Business-logic abuse

## Required Workflow

### 1. Reconnaissance

Inspect enough of the repo to identify:

- Languages/frameworks
- Backend routes/controllers/handlers/services
- Frontend routes/pages/components/forms
- AuthN/AuthZ implementation
- Data access and external calls
- File-system/upload/download handling
- Rendering/HTML/markdown behavior
- Config/env usage
- Existing test frameworks and test layout
- CI/test commands if obvious

Produce a compact internal threat model. Do not write tests until this scan is complete.

### 2. Attack Surface Map

For each selected high-risk entry point, capture:

- Source file(s)
- Entry point
- User-controlled input
- Trust boundary
- Expected control
- Test type: unit, api, integration, browser, component, static
- Severity
- Expected failure meaning

Do not include low-value generic entries.

### 3. Implementation Plan

Before editing files, provide a concise plan:

- Test frameworks detected
- Files to create/modify
- Fixture strategy
- Test categories
- Commands to run
- Expected initial failures

Then implement.

## File Placement

Prefer:

tests/security/
  backend/
  frontend/
  integration/
  fixtures/

Use repo conventions if the framework requires another location.

Use explicit filenames such as:

- `auth-bypass.security.test.*`
- `authorization-boundaries.security.test.*`
- `xss-rendering.security.test.*`
- `csrf-cors-cookie.security.test.*`
- `open-redirect.security.test.*`
- `secrets-exposure.security.test.*`
- `path-traversal.security.test.*`
- `ssrf-url-validation.security.test.*`
- `sensitive-storage.security.test.*`
- `error-leakage.security.test.*`

## Test Requirements

Every generated test must:

- Map to a real source file, route, component, function, config, or policy.
- Assert a security outcome, not just an implementation detail.
- Be deterministic.
- Avoid internet/external services.
- Avoid real secrets.
- Avoid production data.
- Use local mocks/fixtures.
- Follow existing test conventions.
- Be CI-runnable or document limitations.

Use Arrange / Act / Assert.

## Backend/API Test Guidance

Where applicable, test:

- Missing/invalid/expired/malformed auth
- Cross-user access denial
- Cross-tenant access denial
- Non-admin denied admin actions
- Server-side authorization, not just frontend hiding
- Injection-like payload rejection/safe handling
- Path traversal/download/upload safety
- Unsafe URL/SSRF validation using mocks only
- Secrets not returned in responses
- Sensitive logs redacted
- Safe error responses
- CORS/CSRF/cookie/security header behavior

## Frontend/Browser Test Guidance

Use the strongest existing local tool:

1. Playwright/Cypress/local e2e
2. Framework integration tests
3. Component tests
4. Static tests only when runtime tests are unavailable

Where applicable, test:

- XSS payloads render inert/as text
- Unsafe HTML/markdown is sanitized
- Unsafe schemes such as `javascript:` and `data:` are rejected
- Protected routes redirect anonymous users
- Non-admin users cannot see privileged actions
- UI hiding is not treated as server-side authorization
- Tokens/secrets are not stored in localStorage/sessionStorage when secure cookies are expected
- Logout clears sensitive state
- Browser-visible errors do not leak internals
- Security headers are present where locally testable

Safe local payload examples:

- `<img src=x onerror=alert(1)>`
- `<script>alert(1)</script>`
- `<svg onload=alert(1)>`
- `javascript:alert(1)`

Do not execute exploit chains; assert payloads are escaped, absent, inert, or treated as text.

## Local Integration Test Guidance

Use local integration tests when they materially improve confidence.

Allowed:

- Local app/test server
- In-memory DB
- Existing test containers only if already supported
- Mocked services
- Test users/resources
- Framework-native request clients
- Playwright/Cypress against localhost if already configured

Prioritize local integration for:

- AuthN/AuthZ boundaries
- Cross-user/cross-tenant access
- CSRF/CORS/cookie/header checks
- Frontend route protection
- XSS rendering
- Open redirects
- File upload/download
- SSRF validation with mocks

## Fixtures

If adequate fixtures do not exist, create minimal local-only fixtures for:

- anonymous user
- normal user A
- normal user B
- admin user
- tenant A user, if multi-tenant
- tenant B user, if multi-tenant
- resources owned by different users/tenants
- mock tokens/sessions/API keys
- invalid/expired/malformed auth
- XSS/path traversal/unsafe URL payloads

Prefer extending existing factories over creating a parallel system.

If no auth system exists, write expected-contract tests and mark them as expected initial failures.

## Required Artifacts

### `security-test-plan.md`

Include:

- Executive summary
- Recon summary
- Backend attack surfaces
- Frontend/browser attack surfaces
- Tests added
- Integration tests added
- Fixtures created
- Expected initial failures
- High-risk gaps
- How to run
- CI recommendation
- Assumptions

Use concise tables.

### `security-test-inventory.json`

Create valid deterministic JSON:

{
  "schemaVersion": "1.0",
  "generatedBy": "continue-dev-claude-security-test-generation",
  "repositoryProfile": {
    "languages": [],
    "frameworks": [],
    "backendTestFrameworks": [],
    "frontendTestFrameworks": [],
    "integrationTestFrameworks": []
  },
  "securityFixtures": [],
  "attackSurfaces": [],
  "tests": [],
  "commands": {
    "backendSecurityTests": "",
    "frontendSecurityTests": "",
    "localIntegrationSecurityTests": "",
    "fullSecuritySuite": ""
  },
  "knownGaps": [],
  "assumptions": []
}

Inventory requirements:

- Every generated test appears in `tests`.
- Every test has a stable ID such as `SEC-AUTHZ-001`.
- Every test maps to source files unless it is config/static/CI.
- Every fixture appears in `securityFixtures`.
- Every covered attack surface maps to test IDs.
- Commands must be exact.
- Expected initial result must be honest: `pass`, `fail`, or `unknown`.
- Do not overstate coverage.

Recommended object shapes:

securityFixtures item:
{
  "name": "",
  "type": "user | role | tenant | resource | payload | helper | mock-auth-context",
  "file": "",
  "purpose": "",
  "securityBoundaryValidated": ""
}

attackSurfaces item:
{
  "id": "",
  "area": "backend | frontend | integration | config | ci",
  "category": "authn | authz | injection | input-validation | file-safety | ssrf | secrets | logging | xss | csrf | cors | cookie | headers | redirect | browser-storage | error-leakage | business-logic | dependency | other",
  "severity": "critical | high | medium | low",
  "files": [],
  "entryPoints": [],
  "userControlledInputs": [],
  "trustBoundary": "",
  "expectedControl": "",
  "testsAdded": []
}

tests item:
{
  "id": "",
  "name": "",
  "file": "",
  "type": "unit | integration | browser | component | api | e2e-local | static",
  "area": "backend | frontend | integration | config | ci",
  "category": "",
  "severity": "critical | high | medium | low",
  "mappedFiles": [],
  "entryPoint": "",
  "securityAssertion": "",
  "expectedInitialResult": "pass | fail | unknown",
  "failureMeaning": "",
  "requiresNetwork": false,
  "requiresSecrets": false,
  "requiresExternalService": false,
  "command": ""
}

knownGaps item:
{
  "id": "",
  "area": "backend | frontend | integration | config | ci",
  "category": "",
  "severity": "critical | high | medium | low",
  "description": "",
  "recommendedNextStep": ""
}

## Final Response

When complete, report only:

1. Files created/modified
2. Test commands
3. Expected failures
4. Highest-risk gaps
5. Fixture summary
6. Recommended next pass

Proceed now.
```

## Prompt 2 Security Test Hardening Review
```text
# Continue.dev / Claude Prompt — Security Test Hardening Review

## Role

You are a skeptical senior application security test reviewer working inside VS Code through Continue.dev with Claude.

Review and improve the security tests, fixtures, `security-test-plan.md`, and `security-test-inventory.json` created in the previous pass.

Authorized defensive local-only work only. No internet. No external attacks.

## Token-Budget Rules

Use the 200K context budget carefully.

1. Review only generated security files first.
2. Open app source files only when needed to validate mappings.
3. Do not restate full file contents.
4. Do not produce broad theory.
5. Make surgical changes.
6. Keep the final report concise.

## Review Priorities

Harden in this order:

1. AuthN/AuthZ integration tests
2. Cross-user and cross-tenant boundary tests
3. XSS rendering tests
4. CSRF/CORS/cookie/header tests
5. Open redirect tests
6. Secrets exposure tests
7. Sensitive browser storage tests
8. Error leakage tests
9. Injection tests
10. File/path safety tests
11. SSRF URL validation tests
12. Business-logic abuse tests

## Review Checklist

For every generated security test, verify:

- It maps to real code/config.
- It asserts a security outcome.
- It can fail for a meaningful vulnerability.
- It does not require internet, real secrets, external services, or production data.
- It is deterministic.
- It follows repo test conventions.
- It is listed in `security-test-inventory.json`.
- It is represented accurately in `security-test-plan.md`.

Fix tests that are:

- Generic
- Unmapped
- Brittle
- Unsafe
- Snapshot-only
- UI-only when server enforcement is required
- Overly tied to implementation details
- Able to pass while the vulnerability remains

## Frontend/Browser Checks

Verify:

- XSS tests assert inert/escaped/plain-text rendering.
- Unsafe URL schemes are rejected.
- Storage tests check localStorage/sessionStorage/cookies where relevant.
- Protected route tests do not confuse UI hiding with authorization.
- Browser-visible errors do not leak stack traces, SQL, secrets, internal paths, or env values.
- Security header tests are locally appropriate.

## Integration Checks

Verify:

- Local-only harness.
- No real cloud/external services.
- Real request/response behavior where possible.
- Server-side AuthN/AuthZ checks.
- Anonymous, owner, non-owner, admin, and tenant scenarios where applicable.
- Stable startup/teardown.

## Fixture Checks

Verify fixtures:

- Use project conventions where possible.
- Are local-test-only.
- Are deterministic.
- Do not contain real secrets.
- Support authorization-boundary tests.
- Are not unnecessarily complex.
- Are listed in inventory and report.

## Inventory and Report Checks

Validate `security-test-inventory.json`:

- Valid JSON
- Every listed test exists
- Every generated test is listed
- Commands are accurate
- Fixtures are listed
- Attack surfaces map to test IDs
- Expected initial results are honest
- Coverage is not overstated

Validate `security-test-plan.md`:

- Accurate coverage claims
- Exact test commands
- Expected failures
- High-risk gaps
- Fixture explanations
- Backend/frontend/integration separation

## Required Actions

1. Review generated security files.
2. Validate mappings against source where needed.
3. Rewrite weak tests.
4. Add missing high-value tests if supported.
5. Remove unsafe or low-value tests.
6. Correct `security-test-plan.md`.
7. Correct `security-test-inventory.json`.

## Final Response

Report only:

1. Files changed
2. Tests improved/added/removed
3. Inventory corrections
4. Report corrections
5. Exact commands
6. Remaining high-risk gaps
7. Recommended next pass

Proceed now.
```

## Prompt 1 Security Test CI Integration
```text
# Continue.dev / Claude Prompt — Security Test CI Integration

## Role

You are a senior DevSecOps engineer working inside VS Code through Continue.dev with Claude.

Integrate the existing security test suite into CI safely.

Authorized defensive local-only work only. No internet. No external attacks.

## Objective

Wire the generated security tests into CI with a safe rollout strategy.

Default to advisory CI first unless the repo already has mature blocking security gates.

Advisory means:

- Security tests run visibly.
- Failures are reported.
- Failures do not initially block unrelated builds.
- The report explains how to promote to blocking.

## Token-Budget Rules

1. Inspect CI/test config only.
2. Do not rescan application source unless needed.
3. Do not modify tests unless commands are wrong.
4. Keep changes minimal.
5. Keep final response concise.

## Workflow

### 1. CI Recon

Inspect:

- GitHub Actions
- GitLab CI
- Jenkins
- Azure Pipelines
- CircleCI
- Buildkite
- Makefiles
- package scripts
- tox/nox
- Maven/Gradle
- npm/pnpm/yarn scripts
- Python/Node/Java/.NET/Go test conventions
- Docker Compose test setup
- Existing security jobs

### 2. Confirm Commands

Read:

- `security-test-plan.md`
- `security-test-inventory.json`
- Existing test config

Confirm commands for:

- Backend security tests
- Frontend/browser security tests
- Local integration security tests
- Full security suite

Fix report/inventory if commands are wrong.

### 3. Add CI Wiring

Prefer:

1. Dedicated security test job in existing CI
2. Existing script/make target called by CI
3. New workflow only if no suitable CI exists

CI job should:

- Run security tests from the security test location.
- Avoid real secrets.
- Avoid external services.
- Use local mocks/fixtures.
- Validate `security-test-inventory.json` is valid JSON.
- Clearly mark advisory vs blocking.

### 4. Inventory Validation

Add lightweight validation:

- File exists
- Valid JSON
- Required top-level keys exist:
  - `schemaVersion`
  - `repositoryProfile`
  - `securityFixtures`
  - `attackSurfaces`
  - `tests`
  - `commands`
  - `knownGaps`
  - `assumptions`

Avoid new dependencies unless already present or unavoidable.

### 5. Update Docs

Update `security-test-plan.md` with:

- CI job name
- CI command
- Advisory/blocking status
- How to promote to blocking
- How to triage failures
- How to maintain `security-test-inventory.json`

Update `security-test-inventory.json` commands if needed.

## Final Response

Report only:

1. CI files changed
2. Scripts/config changed
3. Security commands added
4. Inventory validation added
5. Advisory or blocking status
6. How to promote to blocking
7. Local command
8. CI job/command
9. Remaining limitations

Proceed now.
```
