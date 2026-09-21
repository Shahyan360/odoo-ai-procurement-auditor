# Odoo AI Procurement Auditor

Implemented by **Muhammad Shahyan Khalid**.

Structured vendor-confirmation extraction, purchase-order comparisons and human-reviewed procurement findings.

This repository provides an independently reconstructed implementation using
fictional business data and public Odoo Community APIs. The documented workflows
and configuration demonstrate the implementation without distributing client data.

## Implemented features

- Offline structured JSON and optional gpt-4o-mini document extraction.
- Vendor product and unit mappings with strict structured validation.
- Identity, quantity, price, currency, duplicate and total findings.
- Purchase-order fingerprinting, manager review, chatter and QWeb summary.

Odoo 17.0 Community. Addon `procurement_auditor`. Database `auditor_demo`. Port `8179`.
See `docs/FEATURES.md` for scope, assumptions and limitations.

## Setup (commands for your later use; not executed)

```powershell
python scripts/bootstrap.py
.\scripts\lab.ps1 -Action init
.\scripts\lab.ps1 -Action up
.\scripts\lab.ps1 -Action upgrade
.\scripts\lab.ps1 -Action stop
```

Open http://127.0.0.1:8179. Admin password: `.local/credentials.json`.
Local email capture: http://127.0.0.1:8029. SMTP goes to Mailpit.
`reset` deletes only this Compose project's named demonstration database.
`seed` reloads custom XML external IDs. Other projects are not dependencies.

Each project has its own Compose name, PostgreSQL volume, filestore, database,
loopback web port, credentials and addons mount. Images are pinned by digest.
Default networking is internal and blocks live providers. To use an explicitly
authorized sandbox, change the project's network setting and supply its secrets
through the private environment. No production integration is enabled by default.

User-supplied historical behavior is the evidence source. Exact thresholds,
identifiers, providers and rules absent from it are proposed configuration. Native
Odoo invoices, payments, inventory, CRM and HR are used where applicable. Configure
a suitable chart, journals, taxes and payment methods before accounting actions.

See [PUBLICATION_SAFETY_REPORT.md](PUBLICATION_SAFETY_REPORT.md) for repository
contents and exclusions. Validation history is recorded separately in
[docs/VERIFICATION.md](docs/VERIFICATION.md).


The init action builds this project's local Odoo derivative first. Its base
image remains pinned by the private ODOO_IMAGE digest; the Dockerfile installs
the listed additional Python dependency. This build has NOT been executed.
Build-time access to the official base registry and Python package index is
needed. Runtime network isolation remains enabled by default.
