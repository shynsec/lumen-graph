# Changelog

All notable changes to Lumen Graph are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [1.0.0] — 2024-11-XX — Initial Public Release

### Core graph
- Canvas-based force-directed graph with 6 entity types: IP, Domain, Email, Person, Organisation, Generic
- Directed edges with relationship labels and arrowheads
- Mesh gradient node styling per entity type
- Drag nodes, pan canvas, scroll to zoom
- Minimap for navigation on large graphs

### Investigation workflow
- Node properties panel: notes, source, date observed, threat score (1–10), TLP, confidence, group
- Threat score badge rendered on canvas node (green / amber / red)
- Evidence URL attachment with `https://` validation
- MITRE ATT&CK technique tagging with searchable dropdown (70+ techniques)
- MITRE technique pills rendered below node labels on canvas
- Investigation timeline — dated nodes as chronological markers
- Case metadata: name, analyst, TLP, description, draft/reviewed/published status

### Analysis
- Path finder — BFS shortest path between two nodes, highlighted in amber
- Cluster detection — union-find connected components with colour-coded group rings
- Node search — `⌘K` fuzzy search with canvas dim of non-matching nodes
- Graph statistics panel — degree, threat score, clusters, date range

### Data
- JSON export and import (full graph + metadata)
- PNG export with mandatory TLP colour bar, case name, analyst, version stamp
- STIX 2.1 bundle export — domain objects, relationships, kill-chain-phases, TLP markings
- CSV import — nodes and edges with preview table before commit
- Auto-detect entities from pasted text — IPv4, IPv6, email, domain, MD5, SHA1, SHA256, CVE, BTC address

### Polish
- Auto-save to localStorage — survives page refresh, restores viewport
- Undo / redo — full history stack (60 steps)
- Presentation mode — hides all UI panels for briefings (`F` key)
- Dark / light mode toggle — preference persisted
- Keyboard shortcut reference modal (`?`)
- Quick-add node via right-click on empty canvas
- Duplicate node detection on add
- Empty label guard

### Security
- Content Security Policy meta tag
- URL sanitisation — `javascript:` URIs rejected
- All user-supplied data rendered via `textContent`, not `innerHTML`
- Import sanitisation — HTML stripped from all string fields on JSON load

---

## Roadmap (Post 1.0)

- [ ] Node sizing by threat score
- [ ] Temporal graph filtering by date range
- [ ] Attribution model — track which analyst added each node
- [ ] Attack chain auto-layout by MITRE tactic order
- [ ] Offline font bundling — full air-gap support
- [ ] Multi-graph case files
