# VLab4Mic website

This repository contains only the MkDocs website for VLab4Mic.

The VLab4Mic source code, notebooks, and examples remain in the main repository:
<https://github.com/HenriquesLab/VLab4Mic>

## Cloudflare Pages

Use these build settings:

- Build command: `pip install -r requirements.txt && mkdocs build --strict`
- Build output directory: `site`
- Root directory: repository root

If the production Cloudflare URL or custom domain differs from
`https://website-vlab4mic.pages.dev/`, update `site_url` in `mkdocs.yml`.
