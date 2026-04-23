# docker-templates

Unraid Community Apps templates for [Abrechen2](https://github.com/Abrechen2)'s self-hosted projects.

## Templates

| File | App | Project |
|---|---|---|
| [`my-travstats.xml`](my-travstats.xml) | **TravStats** — self-hosted flight tracker | [Abrechen2/TravStats](https://github.com/Abrechen2/TravStats) |
| [`my-travstats-db.xml`](my-travstats-db.xml) | **travstats-db** — PostgreSQL 15 + PostGIS 3.4 companion DB | [postgis/docker-postgis](https://github.com/postgis/docker-postgis) |

The `my-` prefix is Unraid's convention for user-added templates. Each XML is self-contained — install order, ports, volumes, env-vars and troubleshooting live inside the template's Overview.

## Install

**Unraid Community Apps (preferred):** search the app name in the **Apps** tab.

**Manual install (while CA approval is pending):** Unraid → **Docker** tab → **Add Container** → paste the raw URL of the XML into the **Template** field. Unraid pulls it directly.

## License

AGPL-3.0-or-later.
