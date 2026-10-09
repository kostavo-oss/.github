# Kostavo

Open-source tools for Databricks, each named after a Dutch engineer or a work of Dutch
engineering — and each with a reason for the name.

> **Terraform for your platform, Asset Bundles for your code, stevin for your data model.**

They live together in [**`tools`**](https://github.com/kostavo-oss/tools), with
[one site](https://kostavo-oss.github.io/tools/) — small tools for the ugly gaps on
Databricks, one per gap, each with a closed scope.

| Tool | What it does | Named after |
|---|---|---|
| [`stevin`](https://github.com/kostavo-oss/tools/tree/main/packages/stevin) | Puts in place the tables and access that your transformation tool doesn't own: a plan for Unity Catalog tables that knows which Delta changes are free and which rewrite 400 GB | **Simon Stevin** — engineer and mathematician, who designed sluices and introduced decimal notation. Precision before action. |
| [`lely`](https://github.com/kostavo-oss/tools/tree/main/packages/lely) | One plan for your whole Databricks deploy: the bundle and the steps around it, reviewed before anything runs | **Cornelis Lely** — designed and built the Afsluitdijk and the Zuiderzee Works. The one who actually got big plans built. |
| [`leeghwater`](https://github.com/kostavo-oss/tools/tree/main/packages/leeghwater) | Your dlt pipeline, the same on your laptop and in a Databricks job | **Jan Adriaanszoon Leeghwater** — drained the lakes north of Amsterdam with windmills. Dry land where there was water. |
| [`caland`](https://github.com/kostavo-oss/tools/tree/main/packages/caland) | Databricks secrets, by hand: a keyboard-driven page in your browser, served from your own machine | **Pieter Caland** — designed and built the Nieuwe Waterweg, the cut through the dunes that gave Rotterdam its way to the sea. |

A data product that uses them together starts from
[`vierlingh`](https://github.com/kostavo-oss/vierlingh), a template.

The tools are independent: each does one job, installs on its own
(`uv tool install <name>`), and none needs another. They are Python, Apache-2.0, and talk
to Databricks through the `databricks-sdk`, so whatever already authenticates your CLI
authenticates them.

## Who makes these

Kostavo is a company — [Kostavo B.V.](https://kostavo.com), in the Netherlands. Its product
is a governance platform for Databricks: it watches the clusters, warehouses, jobs and
settings of many workspaces, and keeps them inside the rules a platform team has set. The
tools come out of the same work.

They are not a trial of anything. Each is Apache-2.0 and complete as it is: nothing is held
back for a paid edition, none of them needs the platform, and none of them reports back.

Questions and bugs go in [the issues](https://github.com/kostavo-oss/tools/issues). If you want someone to put the tools to work with
your team, [Kostavo does that too](https://kostavo.com/contact/).

Community project, not affiliated with or endorsed by Databricks.
