# Privacy

Dev Hub runs entirely on your Mac.

## What Dev Hub stores

- **Project configuration** — names, folders, commands, arguments, expected ports and any environment variables you enter — in `~/Library/Application Support/Dev Hub/config.json`. The file is readable only by your user account. Environment variable values are stored unencrypted; prefer your project's own `.env` files for secrets.
- **Preferences** and **links** you create between running processes and projects, in the same file.
- **A diagnostic log** in `~/Library/Logs/Dev Hub/dev-hub.log`: timestamps, events such as "project started" or "discovery failed", process IDs and ports. It never contains environment variable values or your projects' output.
- **Project output** (stdout/stderr) is kept in memory only, limited to recent lines, and discarded when Dev Hub quits.

## What Dev Hub reads

To list servers, Dev Hub runs the macOS tools `lsof` and `ps`, which report listening ports, process IDs, command lines and working directories for processes your user can see. This information is displayed to you and is not stored, except for process links you create explicitly.

At startup Dev Hub asks your login shell for its `PATH` so it can find tools such as `npm` or `pnpm`.

## What Dev Hub sends

Nothing. Dev Hub has no account, no analytics, no telemetry, no crash reporting and no automatic updates. It makes no network requests of its own. Opening a server's URL hands it to your default browser.

## Removing your data

Quit Dev Hub and delete:

```sh
~/Library/Application Support/Dev Hub
~/Library/Logs/Dev Hub
~/Library/Preferences/ma.yassineoujaa.devhub.plist
```

The last file holds macOS window and system settings that Electron stores on the app's behalf; Dev Hub writes no data of its own there.

## Changes

If a future version changes any of this, the change will be described in the release notes and in this document before it ships.
