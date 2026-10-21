# Technitium DNS Server

The official Technitium DNS Server image with Technitium Console as its web
interface. It is the setup from the
[Technitium Console README](https://github.com/byGarcia/technitium-console)
packaged as a single Home Assistant app.

## Getting started

1. Add this repository under **Settings › Apps › App store › ⋮ › Repositories**.
2. Install and start **Technitium DNS Server**.
3. Select **Open web UI** (port 5380) and sign in as `admin` / `admin`.
   Change the password straight away.

All configuration is done in the web console.

## Network

The app uses the host network: DNS on port 53, the web console on port 5380.
Nothing else on the Home Assistant host may already use port 53.

## Data

Server configuration, zones, logs and stats are kept in the app's `/data`
folder and are included in Home Assistant backups.

## Updates

The app version is `<dns-server>-<console>`, for example `15.6.2-1.3.4`.
Updating the app updates both.

The console checks for its own updates through the DNS server, once a day, with
one HTTPS request to `technitium-console.pages.dev`. Turn this off in the console
under **Settings › General › Check for update**.
