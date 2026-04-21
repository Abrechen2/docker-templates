# docker-templates

Unraid Community Apps templates for Abrechen2's self-hosted apps.

## TravStats

Self-hosted flight tracker — [github.com/Abrechen2/TravStats](https://github.com/Abrechen2/TravStats)

Two templates; install in this order:

1. **[travstats-db.xml](travstats-db.xml)** — PostgreSQL 15 + PostGIS 3.4, pre-configured for TravStats (DB `flights`, user `flights`, published on host port 5432).
2. **[travstats.xml](travstats.xml)** — The app itself. Reaches the DB via `host.docker.internal:5432`, so no custom Docker network required.

After the app container is healthy, open `http://<unraid-ip>:<port>/setup` and create an admin account.

Install guide: [docs/unraid/README.md](https://github.com/Abrechen2/TravStats/blob/main/docs/unraid/README.md) in the main repo.

### Troubleshooting — `FATAL: could not open file "global/pg_filenode.map": Permission denied`

Symptom: the TravStats setup page renders but shows *"Error querying the database"*, and the `travstats-db` log repeats `Permission denied` / `could not open directory "pg_logical/snapshots"`.

Cause: the Postgres data directory on the Unraid share was left with the wrong owner — typically because an earlier install wrote into the bind-mount root directly, or because FUSE `shfs` didn't propagate the container's initial `chown`.

Fix (in order):

1. Stop both containers.
2. `rm -rf /mnt/user/appdata/travstats-db/pgdata` *(replace with your Application Data path if you changed it — and note the `pgdata/` subfolder; leave `travstats-db/` itself in place if you keep backups there).*
3. Start `travstats-db`. It now runs `initdb` fresh as UID 999.
4. Start `TravStats`.

If the fresh start still fails, switch the `travstats-db` Application Data path from `/mnt/user/appdata/...` to `/mnt/cache/appdata/...` (direct cache-pool mount — bypasses Unraid's FUSE layer). Requires a configured cache pool.

## Adding this template repo manually (while CA submission is pending)

Unraid → **Docker** tab (top right) → **Add Container** → paste the raw URL of the relevant XML into the **Template** field. Unraid pulls the template directly. Once the CA submission is approved the templates will also be searchable via the **Apps** tab.

## License

Templates published under the same licence as TravStats itself (AGPL-3.0-or-later).
