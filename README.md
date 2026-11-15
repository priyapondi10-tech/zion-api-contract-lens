# API Contract Lens

A complete dependency-free browser application for directional structural risk review of OpenAPI 3.0 / 3.1 **JSON** specifications. Complements API testing and code review with an explicit consumer migration checklist.

Live: https://priyapondi10-tech.github.io/zion-api-contract-lens/

## Run and test

```sh
python3 -m http.server 8080
node --test test.mjs
```

Open http://localhost:8080/. Node 20+ for tests; a modern ES-module browser for UI. No dependency installation or build. GitHub Pages source is main/root; `.nojekyll` is included.

## Workflow and scope

Paste or locally import the baseline and candidate. Compare, filter breaking/review/likely-compatible findings, swap direction and download a JSON report or Markdown migration checklist. Inputs are not saved or transmitted; no external `$ref` fetch, API test request, analytics or server exists. CSP blocks connections and form submission. Reports include specification titles, paths and schema names: review before sharing.

Checks include removed/added operations; inherited parameters with operation overrides; required parameters and request bodies; media types and response statuses; local JSON Pointer references including escaped pointer components; schema properties, required guarantees, types/nullable, enums and array items; selected constraint/default changes; authentication requirement changes. Request narrowing and response widening are assessed differently. Cycles, unresolved refs and changed complex schemas produce warnings.

**Not a complete validator, security auditor, JSON Schema implication solver or formal compatibility proof.** YAML, Swagger 2, advanced composition/discriminator logic, callbacks/webhooks, response headers, encoding details, generated-client quirks, server implementation and semantic behavior require manual checks. Some changes classified as likely compatible may still break strict consumers. Description/example-only changes are ignored. Continue to run consumer contract tests, security review and staged rollout checks.

Input limits: 1 MiB per specification, 64 nesting levels, 100,000 nodes, 2,000 operations and 20,000 schema comparisons. These bounds protect the browser from accidental oversized inputs, not hostile code execution (no input is executed).

## Network / domain staging

All four utilities and the staging homepage are cross-linked. `contract-lens.ziontechgroup.com` is prepared in a pending Cloudflare zone but not bound to Pages; no CNAME file is committed. The github.io HTTPS URL remains the deployment URL. Before future zone activation, verify domain ownership in GitHub, claim hostnames in Pages and check certificates to avoid dangling-domain takeover. Production repositories, nameservers and existing DNS remain untouched.
