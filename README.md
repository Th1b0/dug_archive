# Intelligence Archive — GitHub Pages starter

A Jekyll static website for Markdown reports. Includes a responsive navbar, automatic report cards, client-side search, report metadata, section table of contents, and copyable report URLs.

## 1. Create the repository

1. Create a GitHub repository (for example `intelligence-archive`).
2. Upload all files from this project, preserving the folder structure.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select branch `main` and folder `/ (root)`, then save.
6. Wait for the Pages deployment to finish. The site URL will look like `https://YOUR-USERNAME.github.io/intelligence-archive/`.

If you use a custom domain, configure it in Settings → Pages and update DNS as GitHub instructs.

## 2. Add a report

Create a file in `_reports/`, such as `_reports/002-airfield-observation.md`:

```yaml
---
title: "Airfield Observation"
report_id: "INT-002"
date: 2026-10-30
location: "Northwest Airfield"
reporting_individual: "Tybo"
classification: "Unverified Intelligence"
source_reliability: "Unassessed"
subjects:
  - Example Subject
tags:
  - Observation
  - Airfield
summary: "A short description displayed on the report card."
---
```

After the second `---`, write your report in Markdown. Use `## 1. Summary`, `## 2. Findings`, etc. The report page automatically builds a clickable table of contents from `##` and `###` headings.

Metadata tips:
- `date` uses `YYYY-MM-DD`.
- `tags` and `subjects` are YAML lists.
- Keep filenames lowercase and use hyphens.
- `report_id` is a visible reference number; use unique values such as `INT-001`.

## 3. Edit site settings

Edit `_config.yml` to change the title and description. Edit `assets/style.css` to change colours and layout. The accent colour is `--accent: #b8e600`.

For a project site at `https://YOUR-USERNAME.github.io/intelligence-archive/`, set `url` to `https://YOUR-USERNAME.github.io` and `baseurl` to `/intelligence-archive` in `_config.yml` (the starter is preconfigured this way). Replace `YOUR-USERNAME` with your GitHub username. If your repository has a different name, update `baseurl` to `/<repository-name>`. For a user/organisation site named `YOUR-USERNAME.github.io` or a custom domain, set `baseurl` to an empty string.

## 4. Password protection and confidentiality

GitHub Pages does **not** provide native password protection for published sites. A private source repository does not automatically make the published Pages website private.

Do not add a JavaScript-only password prompt for sensitive reports. It cannot protect files that are already publicly delivered to a browser. Use real access control (for example, a properly configured identity-aware access proxy with a protected origin) or host the site on a server that enforces authentication.

This sample is a public static site and should only contain material you are comfortable publishing.
