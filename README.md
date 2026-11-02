# Joomla (LazyCat LPK)

Content management system.

- Upstream: https://github.com/joomla/joomla-cms
- Image: `library/joomla:6.2.0` (official Docker Hub image, mirror mode, digest-matched)
- License: GPL-2.0 (full text in `content/licenses/LICENSE`)
- Containers: Joomla + MariaDB 10.11

## Notes

- **Version detection caveat**: Docker Hub's registry `tags/list` caps at 1000 entries,
  which made this repo appear to top out at 4.2.3. Querying
  `https://hub.docker.com/v2/repositories/library/joomla/tags/?ordering=last_updated`
  shows the real latest is **6.2.0**. Always use the Hub API for version checks.
- The installer is the standard Joomla web wizard: choose MySQLi, host `db`, database
  `joomla`, user `joomla`, and the password from the deploy param. Admin account is created
  there — no seeded credential.
- `JOOMLA_DB_*` env vars pre-seed the connection so the wizard is short.
- `JOOMLA_INSTALLATION_DISABLE_LOCALHOST_CHECK=1` avoids the localhost guard behind a proxy.
- Data on `/lzcapp/var/{db,html}`.
- Not yet verified on a real device.
