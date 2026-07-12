# Kobiton (kobiton)

Kobiton is a mobile device cloud and app testing platform that lets teams run manual, automated, scriptless, and visual tests against real iOS and Android devices in the cloud (or on privately managed local devices). Its REST API at `https://api.kobiton.com/v1` exposes the real device cloud, test-run sessions and their captured commands, the app repository, data-driven test data sets, and scriptless (no-code) test runs. Scripted automation runs against a separate Appium/WebDriver hub at `https://api.kobiton.com/wd/hub`. All REST requests authenticate with HTTP Basic auth using a Kobiton username (or email) and an API key.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/kobiton/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/kobiton/refs/heads/main/apis.yml)

## Access Model (Honest Notes)

- **This is a real, documented public REST API.** Endpoints for Devices, Sessions/session commands, the App Repository, Data Sets, scriptless automation (revisit plans), and Organization administration are grounded in Kobiton's published API reference (`https://api.kobiton.com/docs`) and official code samples (`github.com/kobiton/samples`).
- **You need a Kobiton account and an API key.** API keys are created in the Kobiton portal under API Keys settings; auth is HTTP Basic (`-u <username>:<apiKey>`).
- **A newer v2 API exists** at `https://api.kobiton.com/v2` alongside v1. This entry documents the widely-referenced v1 surface; reconcile paths and payloads against the live reference.
- **Test runs consume plan minutes.** API-driven and portal-driven test runs draw from the same monthly testing-minute allowance; there is no separate API fee.
- **Modeled vs. confirmed:** endpoint paths and the presence of each resource are grounded in Kobiton docs/samples. Request and response **schemas** in the OpenAPI are modeled from documentation and sample payloads and should be reconciled against the live reference. Items so derived are flagged in the OpenAPI descriptions.
- **No public WebSocket API.** Kobiton's live manual-session device streaming and virtualUSB remote debugging are delivered through the browser portal and a desktop/CLI tunnel client, not a documented developer WebSocket endpoint. See `review.yml`.

## Tags

- Mobile Testing
- Test Runs
- Device Cloud
- Real Devices
- Appium
- Automation Testing
- Visual Testing
- QA
- Mobile

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Kobiton Devices API

Retrieve the real devices available to your account across the public cloud, your favorites, and your private or local devices. Filter by platform, version, device name, online status, booking status, and Appium availability to find a device to book for a manual or automated test run.

- **Human URL:** [https://docs.kobiton.com/automation-testing/get-available-devices](https://docs.kobiton.com/automation-testing/get-available-devices)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** Device Cloud, Real Devices, Mobile Testing, Device Discovery

### Kobiton Sessions API

Read back the results of a test run - fetch a session by ID for its metadata and status, and page through the captured session commands (the step-by-step log of Appium/WebDriver actions). Each manual or automated test produces a session that can be inspected programmatically for reporting and QA analysis.

- **Human URL:** [https://docs.kobiton.com/automation-testing/get-a-session-id/using-the-kobiton-api](https://docs.kobiton.com/automation-testing/get-a-session-id/using-the-kobiton-api)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** Test Runs, Sessions, Mobile Testing, QA

### Kobiton Scriptless Automation API

Kick off scriptless (no-code) automated test runs by replaying a baseline manual exploration session across one or more target devices. POST a revisit plan with the baseline session IDs and a device bundle to run the same test steps at scale - the foundation of Kobiton's scriptless and visual test-run workflows.

- **Human URL:** [https://docs.kobiton.com/scriptless-automation/use-rest-api](https://docs.kobiton.com/scriptless-automation/use-rest-api)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** Test Runs, Scriptless, Visual Testing, No Code, QA

### Kobiton Apps Repository API

Manage the app builds you test against. Generate a pre-signed upload URL, push a new app or version, list and retrieve apps and versions, tag versions, toggle public/private visibility, assign apps to teams, and delete old builds so every test run targets the right binary.

- **Human URL:** [https://docs.kobiton.com/app-repository/app-repository](https://docs.kobiton.com/app-repository/app-repository)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** App Repository, Uploads, Mobile Testing, Build Management

### Kobiton Data-Driven Testing API

Drive the same scriptless test run through many input permutations. List the data sets in a session and create or update them by command ID or by element property, so a single baseline test executes across a matrix of data values for broader QA coverage.

- **Human URL:** [https://docs.kobiton.com/scriptless-automation/data-driven-testing](https://docs.kobiton.com/scriptless-automation/data-driven-testing)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** Data-Driven Testing, Test Runs, Data Sets, QA

### Kobiton Appium Automation Hub

Kobiton's Appium/WebDriver endpoint for scripted mobile automation. Point an Appium or Selenium client at the hub with Kobiton desired capabilities to allocate a real device and execute a scripted test run. This is the standard W3C WebDriver protocol over HTTPS, not a Kobiton-proprietary REST resource.

- **Human URL:** [https://docs.kobiton.com/automation-testing/automation-testing](https://docs.kobiton.com/automation-testing/automation-testing)
- **Base URL:** `https://api.kobiton.com/wd/hub`
- **Tags:** Appium, Automation Testing, WebDriver, Test Runs

### Kobiton Organization API

Administer an organization programmatically - create members, activate and deactivate members, and assign roles - so device-cloud access and test-run permissions can be provisioned as code.

- **Human URL:** [https://docs.kobiton.com/administration/administration](https://docs.kobiton.com/administration/administration)
- **Base URL:** `https://api.kobiton.com/v1`
- **Tags:** Organization, Members, Administration, Teams

## Common Properties

- [Authentication](authentication/kobiton-authentication.yml)
- [GitHub Organization](https://github.com/kobiton)
- [LinkedIn](https://www.linkedin.com/company/kobiton)
- [Website](https://kobiton.com)
- [Documentation](https://docs.kobiton.com)
- [Plans](plans/kobiton-plans-pricing.yml)
- [Rate Limits](rate-limits/kobiton-rate-limits.yml)
- [Fin Ops](finops/kobiton-finops.yml)
- [Blog](https://kobiton.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
