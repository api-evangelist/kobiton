# Kobiton (kobiton)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
