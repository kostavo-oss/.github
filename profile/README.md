# Kostavo

Open-source tools for Databricks, each named after a Dutch engineer or a work of Dutch
engineering — and each with a reason for the name.

> **Terraform for your platform, Asset Bundles for your code, stevin for your data model.**

| Tool | What it does | Named after |
|---|---|---|
| [`stevin`](https://github.com/kostavo-oss/stevin) | Safe plan/apply migrations for Unity Catalog tables and schemas | **Simon Stevin** — engineer and mathematician, who designed sluices and introduced decimal notation. Precision before action. |
| [`lely`](https://github.com/kostavo-oss/lely) | Better Databricks Asset Bundle deployments | **Cornelis Lely** — designed and built the Afsluitdijk and the Zuiderzee Works. The one who actually got big plans built. |
| [`maeslant`](https://github.com/kostavo-oss/maeslant) | Secrets management, in an interactive TUI | **The Maeslantkering** — one of the largest moving structures in the world; it closes when it matters. |

The tools are independent: each does one job, installs on its own
(`uv tool install <name>`), and none needs another. They are Python, Apache-2.0, and talk
to Databricks through the `databricks-sdk`, so whatever already authenticates your CLI
authenticates them.

Community project, not affiliated with or endorsed by Databricks.
