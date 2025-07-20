# fuze‑dev‑portal

> **Static documentation hub (Docsify) + OpenAPI 3.1 specs**  
> One repo to publish all public API references, SDK guides, and white‑paper docs for the FUZE.ac ecosystem.

[![Docsify](https://img.shields.io/badge/Docsify-4.x-brightgreen)](https://docsify.js.org)  
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.1-blue)](https://github.com/OAI/OpenAPI-Specification)  
[![CI / Deploy](https://github.com/fuze-ac/fuze-dev-portal/actions/workflows/deploy.yml/badge.svg)](./actions)

---

## 🗂  Repository Structure

```

.
├─ docs/                        # Markdown sources (Docsify)
│  ├─ index.md                  # Landing page
│  ├─ guides/                   # Quick‑starts, tutorials
│  ├─ sdk/                      # TS / Unity SDK docs
│  └─ whitepaper/               # Split chapters for markdown view
├─ openapi/                     # Machine‑readable API specs
│  ├─ core.yaml                 # Core Gateway (bots, KPI, unlock)
│  ├─ playhub.yaml              # GameVault & session API
│  └─ otc.yaml                  # KPI‑Bond escrow endpoints
├─ static/                      # Logos, diagrams
├─ scripts/                     # Lint, bundle, spec‑merge helpers
└─ docsify.json                 # Portal configuration

````

---

## 🚀 Local Preview

```bash
git clone https://github.com/fuze-ac/fuze-dev-portal.git
cd fuze-dev-portal
npm i -g docsify-cli @redocly/cli
docsify serve docs  # http://localhost:3000
````

OpenAPI files are auto‑rendered with **Redoc** via `<iframe>` include.

---

## ⚙️ Editing Workflow

1. **Markdown docs** – update `docs/**/*.md`. Use relative image paths (`/static/img.png`).
2. **OpenAPI specs** – edit YAML in `openapi/`.

   ```bash
   redocly lint openapi/core.yaml   # validate
   ```
3. **Sidebar / nav** – modify `docs/_sidebar.md`.
4. Commit & push. GitHub Actions auto‑build and deploy to **[https://docs.fuze.ac](https://docs.fuze.ac)** (GitHub Pages).

---

## 🔄  CI Pipeline

| Step             | Tool                         | Purpose                                |
| ---------------- | ---------------------------- | -------------------------------------- |
| **Lint MD**      | `markdownlint-cli`           | Style + broken link check              |
| **Lint OpenAPI** | `@redocly/cli`               | Ensure spec validity                   |
| **Link checker** | `lychee`                     | External URL health                    |
| **Deploy**       | `peaceiris/actions-gh-pages` | Publish `/site` artefact to `gh-pages` |

---

## ✍️ Writing Guidelines

* Use **sentence‑case headings**; keep paragraphs ≤ 90 chars.
* Code blocks: `bash`, `ts`, `solidity`.
* Cross‑link specs with `[endpoint](../openapi/core.yaml#/paths/~1v1~1bots~1start/post)`.
* Add diagrams to `static/diagrams/` as SVG.

---

## 🤝 Contributing

1. Fork → create feature branch (`docs/fix-typo-*`).
2. Run `npm run lint`.
3. Submit PR to `main`. Small fixes welcome!
4. For larger rewrites, open an issue first.

All contributors must sign the CLA.

---

## 📝 License

Documentation content **CC‑BY‑4.0**.
OpenAPI specs & site code **MIT © 2025 FUZE Foundation**

