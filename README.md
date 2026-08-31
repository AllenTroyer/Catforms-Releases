# Catforms School Records — update feed

Velopack release assets for the offline School Records client. Nothing here is source
code; the application lives in a private repository.

## Which file do I download?

**A computer that has never had School Records on it — `CatformsSchoolRecords-Setup-<version>.exe`.**
This is the one to send a school. It brings SQL Server LocalDB and the Edge WebView2
runtime with it, installs them if they are missing, and only then installs the
application. It is large because LocalDB, the current SQL Server servicing package, and
WebView2 travel inside it—the premise is a machine with no usable connection. The
bootstrapper also upgrades stale SQL Server 2022 LocalDB installations before launching
School Records.

**`Catforms.SchoolRecords-win-Setup.exe` is not that installer.** It contains the
application alone and assumes LocalDB and WebView2 are already present. On a clean
machine it appears to install successfully and then fails at launch with *"error: 52 -
Unable to locate a Local Database Runtime installation"*. Use it only on a machine that
has run School Records before.

The remaining files — the `.nupkg` packages, `releases.win.json`, `RELEASES` — are for the
updater, not for people. Installed clients read them on their own.

## Updates

After the first install the client updates itself from this feed, downloading a delta
rather than the whole application. Nothing needs to be sent to a school for an update.

Clients built before version 0.1.11 have no feed address compiled into them and cannot
update themselves at all; those machines need the bootstrap installer above once, by hand.
