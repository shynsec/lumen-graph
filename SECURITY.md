# Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 1.0.x   | ✅ Yes     |

## Scope

Lumen Graph is a client-side only tool. It makes no network requests and stores data exclusively in the browser's localStorage. There is no backend, no authentication layer, and no server to attack.

The primary security surface is **data ingestion** — imported JSON files and pasted text used for entity detection.

## Mitigations in place

- **Content Security Policy** — `script-src 'unsafe-inline'` is required for the single-file architecture, but `connect-src 'none'` blocks all outbound network requests, and `object-src 'none'` blocks plugin execution
- **URL validation** — evidence URLs are parsed with the native `URL()` API; only `https://` and `http://` protocols are accepted. `javascript:`, `data:`, and `vbscript:` URIs are silently rejected
- **Import sanitisation** — all string fields from imported JSON (labels, notes, source, MITRE fields, case metadata) are stripped of HTML tags via regex before touching the DOM
- **DOM safety** — user-supplied content is always inserted via `textContent` or safe DOM construction, never `innerHTML`
- **No eval** — no use of `eval()`, `Function()`, or dynamic script injection

## Reporting a vulnerability

If you find a security issue, please open a GitHub Issue labelled `security` or email the maintainer directly. Do not disclose publicly until a fix is available.

Please include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact
- Suggested fix if you have one

## Out of scope

- Attacks that require physical access to the victim's machine
- Social engineering
- Issues in browser extensions or OS-level components
- Theoretical attacks with no practical exploit path
