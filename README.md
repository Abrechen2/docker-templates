# docker-templates

Unraid Community Apps templates for Abrechen2's self-hosted apps.

## TravStats

Self-hosted flight tracker — [github.com/Abrechen2/TravStats](https://github.com/Abrechen2/TravStats)

Two templates; install in this order:

1. **[travstats-db.xml](travstats-db.xml)** — PostgreSQL 15 + PostGIS 3.4, pre-configured for TravStats (DB `flights`, user `flights`, published on host port 5432).
2. **[travstats.xml](travstats.xml)** — The app itself. Reaches the DB via `host.docker.internal:5432`, so no custom Docker network required.

After the app container is healthy, open `http://<unraid-ip>:<port>/setup` and create an admin account.

Install guide: [docs/unraid/README.md](https://github.com/Abrechen2/TravStats/blob/main/docs/unraid/README.md) in the main repo.

## Adding this template repo manually (while CA submission is pending)

Unraid → **Docker** tab (top right) → **Add Container** → paste the raw URL of the relevant XML into the **Template** field. Unraid pulls the template directly. Once the CA submission is approved the templates will also be searchable via the **Apps** tab.

## License

Templates published under the same licence as TravStats itself (AGPL-3.0-or-later).
