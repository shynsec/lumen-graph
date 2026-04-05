# Lumen Graph

**A self-contained OSINT and threat intelligence graph editor for investigators.**

Lumen Graph runs entirely in your browser as a single HTML file — no installation, no server, no dependencies. Open it and start mapping.

![Lumen Graph](docs/screenshot.png)

---

## What it does

Lumen Graph lets you visually map relationships between entities in an investigation — IP addresses, domains, email addresses, people, organisations — and document your intel as you go.

It is built for **CTI analysts, OSINT investigators, and SOC teams** who need to build and share link analysis graphs without standing up infrastructure.

---

## Features

### Core graph
- **6 entity types** — IP Address, Domain, Email, Person, Organisation, Generic
- **Force-directed layout** with manual drag positioning
- **Directed edges** with relationship labels
- **Zoom, pan, and minimap** navigation

### Investigation workflow
- **Node properties panel** — notes, source, date observed, threat score (1–10), TLP classification, confidence level, group assignment
- **Evidence URLs** — attach links to each node, validated to `https://` only
- **MITRE ATT&CK tagging** — search and tag technique IDs per node, rendered as pills on the canvas
- **Investigation timeline** — nodes with dates appear as a chronological track
- **Case metadata** — case name, analyst, TLP, description, and draft/reviewed/published status

### Analysis tools
- **Path finder** — find the shortest connection path between any two nodes
- **Cluster detection** — auto-detect connected components with colour-coded rings
- **Search & filter** — `⌘K` to search, dims non-matching nodes
- **Graph statistics** — most connected node, highest threat score, cluster count, date range

### Data in / out
- **Export JSON** — full graph save including all metadata
- **Import JSON** — restore a saved graph
- **Export PNG** — canvas snapshot with mandatory TLP colour bar and watermark
- **Export STIX 2.1** — standard bundle importable into MISP, OpenCTI, QRadar
- **Import CSV** — bulk import nodes and edges from structured files
- **Auto-detect entities** — paste raw text (email headers, WHOIS, Shodan output) and extract IPs, domains, emails, hashes, CVEs automatically

### Polish
- **Auto-save** — graph persists across page refreshes via localStorage
- **Undo / Redo** — full history with `⌘Z` / `⌘⇧Z`
- **Presentation mode** — hides all UI for briefings (`F`)
- **Dark / light mode** — toggle with the sun icon, preference saved
- **Keyboard shortcuts** — press `?` for a full reference

---

## Getting started

```bash
git clone https://github.com/yourusername/lumen-graph.git
cd lumen-graph
open index.html
```

Or just download `index.html` and open it directly in any modern browser.

No npm. No build step. No internet connection required after the initial load (fonts are loaded from Google Fonts on first open).

---

## CSV Import format

### Nodes (`nodes.csv`)
```csv
label,type,notes,source,date,score,tlp
185.220.101.47,IP,Tor exit node seen in honeypot,Shodan,2024-11-01,8,RED
evil-c2.net,Domain,C2 domain registered via privacy proxy,WHOIS,2024-11-03,7,AMBER
```

**`type`** must be one of: `IP`, `Domain`, `Email`, `Person`, `Org`, `Generic`  
**`score`** is 1–10  
**`tlp`** is `WHITE`, `GREEN`, `AMBER`, or `RED`  
**`date`** is `YYYY-MM-DD`

### Edges (`edges.csv`)
```csv
source,target,label
185.220.101.47,evil-c2.net,resolves-to
evil-c2.net,attacker@proton.me,registered-by
```

Sample CSV templates are in the [`/samples`](/samples) directory.

---

## Keyboard shortcuts

| Action | Shortcut |
|---|---|
| Edge mode | `E` |
| Path finder | `P` |
| Search nodes | `⌘K` |
| Graph statistics | `S` |
| Presentation mode | `F` |
| Shortcut reference | `?` |
| Undo | `⌘Z` |
| Redo | `⌘⇧Z` |
| Cancel / close | `Esc` |
| Quick-add node | Right-click canvas |
| Open properties | Click node |

---

## Security

Lumen Graph is a local tool — it makes no network requests and stores data only in your browser's localStorage. The following mitigations are in place:

- **Content Security Policy** — blocks injected scripts from executing
- **URL validation** — evidence links must be `https://` or `http://`; `javascript:` URIs are rejected
- **Import sanitisation** — all string fields from imported JSON are stripped of HTML tags before touching the DOM
- **No `innerHTML` with user data** — all user-supplied content is set via `textContent`

---

## TLP handling

TLP classification is set at the case level in the Case Metadata panel. PNG exports always include a coloured TLP bar at the top of the image. STIX exports include TLP marking definitions.

TLP does not restrict access within the tool itself — it is a labelling and export marking system.

---

## Roadmap

- [ ] Node sizing by threat score
- [ ] Temporal graph filtering (date range slider)
- [ ] Attribution model (who added what)
- [ ] Attack chain view (kill chain layout by MITRE tactic)
- [ ] Offline font bundling

---

## License

MIT — see [LICENSE](LICENSE)

---

## Version

`v1.0.0` — Initial public release
