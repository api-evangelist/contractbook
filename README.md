# Contractbook (contractbook)

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

Contractbook is a contract lifecycle management (CLM) platform that turns static contracts into structured, automatable data. Its Public API v3 (base `https://api.contractbook.com/v3`, Bearer API-key auth) lets teams generate pre-filled contract drafts from any data source, send documents for electronic signature, manage templates, organize documents into spaces, run automations, upload attachments, and receive webhook notifications on document life-cycle events. Contractbook covers the full contract lifecycle - drafting, negotiation, signing, storage, and post-signature management - for legal, sales, HR, and procurement teams.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/contractbook/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/contractbook/refs/heads/main/apis.yml)

## Access Model (be honest)

- The Contractbook Public API is **real and documented**. The current version is **v3** (OpenAPI 3.0) at [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs); a prior **v2** lives at [https://api.contractbook.com/v2/docs](https://api.contractbook.com/v2/docs). The older Apiary blueprint (`contractbook.docs.apiary.io`) is deprecated and redirects to these docs.
- **Authentication:** a Bearer **API key** created in your Contractbook profile settings (shown only once on creation), passed as `Authorization: Bearer YOUR_API_KEY`. Separate keys exist for the staging (`api-staging.contractbook.com`) and production environments.
- **API access is a paid add-on.** It is available on the **Centralize** and **Accelerate** plans (and **Custom**/enterprise), and is **not** included on the entry **Essential** plan. Access is subject to "fair usage limits"; no fixed numeric rate limits are published.
- **Webhooks** are Contractbook's outbound HTTP notification mechanism for document life-cycle events (created / updated / signed). Callbacks are **unauthenticated by default** (an optional `access_token` query parameter can be added), and subscriptions are configured inside Contractbook rather than through documented CRUD endpoints - so the webhook artifact here is **honestly modeled** from documented behavior.
- The endpoints, base URL, and auth in this entry are **grounded in the live OpenAPI** at `https://api.contractbook.com/v3/docs/public/v3/openapi-v3.json`. Pricing figures are indicative list prices observed on the pricing page and are not reconciled.

## Tags

- Contract Management
- CLM
- Contract Lifecycle
- Legal
- eSignature
- Contracts
- Document Automation
- LegalTech

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Contractbook Documents API

The core contract lifecycle surface. List and filter contracts and drafts, retrieve a single document, update its data fields, delete it, download a signed PDF copy, and send a document out for electronic signature. In Contractbook's model a contract is a "document", so this is the primary Contract Management / CLM entry point.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Contracts, Documents, CLM, Contract Lifecycle, eSignature

### Contractbook Templates API

List and retrieve the reusable contract templates in a workspace, and generate a new pre-filled draft document from a template (`POST /templates/{id}/create_document`). This is how integrations mass-produce contracts from data in an upstream system such as a CRM or HRIS.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Templates, Contract Templates, CLM, Document Generation

### Contractbook Document Sharing API

Grant and revoke collaborator access to a document. Share a contract with internal or external collaborators (`POST /documents/{id}/share`) and unshare it (`DELETE /documents/{id}/share`) to control who can view or work on a given contract.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Sharing, Collaboration, Permissions, CLM

### Contractbook Automations API

List the automations configured in a workspace and trigger a specific automation to run (`POST /automations/{id}/run`). Automations drive contract-lifecycle workflows - reminders, approvals, and event-based actions - defined in Contractbook's Automation Builder.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Automations, Workflows, CLM, Approval Workflows

### Contractbook Spaces API

Organize contracts into a hierarchy of spaces. Retrieve the space tree (`GET /spaces/{id}/tree`) and create child spaces (`POST /spaces/{id}`) to structure a workspace's documents by team, department, or matter.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Spaces, Organization, Folders, CLM

### Contractbook Attachments API

Upload a file (`POST /upload`) to attach supporting material - appendices, signed copies, exhibits - to a contract in Contractbook.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Base URL:** `https://api.contractbook.com/v3`
- **Tags:** Attachments, Uploads, Files, CLM

### Contractbook Document Webhooks

Contractbook's document life-cycle notification (webhook) mechanism. When a document is created, updated, or signed, Contractbook sends an HTTP request to a client-configured callback URL, letting integrations react to contract state changes instead of polling. Callbacks are unauthenticated by default (optional `access_token` query parameter), and recipients are advised to confirm state via an authenticated `GET /documents/{id}` call. Subscriptions are configured in Contractbook rather than via documented CRUD endpoints, so this API is **honestly modeled** from documented behavior.

- **Human URL:** [https://api.contractbook.com/v3/docs](https://api.contractbook.com/v3/docs)
- **Tags:** Webhooks, Notifications, Events, CLM, Contract Lifecycle
- **Artifact:** [webhooks/contractbook-webhooks.yml](webhooks/contractbook-webhooks.yml)

## Artifacts

- [OpenAPI (v3, real, fetched from live docs)](openapi/contractbook-openapi.json)
- [Postman Collection](collections/contractbook.postman_collection.json)
- [Open Collection](collections/contractbook.opencollection.json)
- [Authentication](authentication/contractbook-authentication.yml)
- [Plans / Pricing](plans/contractbook-plans-pricing.yml)
- [Rate Limits](rate-limits/contractbook-rate-limits.yml)
- [FinOps](finops/contractbook-finops.yml)
- [Webhooks (modeled)](webhooks/contractbook-webhooks.yml)

## Common Properties

- [Authentication](authentication/contractbook-authentication.yml)
- [LinkedIn](https://www.linkedin.com/company/contractbook)
- [Website](https://contractbook.com)
- [Documentation](https://api.contractbook.com/v3/docs)
- [Support Center](https://support.contractbook.com)
- [Plans](plans/contractbook-plans-pricing.yml)
- [Rate Limits](rate-limits/contractbook-rate-limits.yml)
- [Fin Ops](finops/contractbook-finops.yml)
- [Blog](https://contractbook.com/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
