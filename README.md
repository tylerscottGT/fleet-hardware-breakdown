# Fleet Hardware Breakdown (MyGeotab Add-In)

A MyGeotab page add-in that summarizes a fleet's hardware in three pie charts:

- **Make/Model**: from the VIN MyGeotab has already decoded, or MyGeotab's own VIN decoder.
- **Hardware**: telematics device type (GO9, GO9B, GO Anywhere, GO Anywhere+, …).
- **Cameras**: paired cameras by model (for example Surfsight AI-12, GO Focus Plus), from the MyGeotab Camera API.

It follows MyGeotab's **Groups** filter at the top of the page, including Asset Type groups such as Vehicle › Pickup Truck. When the filter is cleared it shows the whole company.

Other features:

- An asset table under the charts, with search (name, serial number, VIN, make/model), sortable columns, 100 rows per page, and links to each asset.
- A **Communicating** column (Yes/No) from MyGeotab's device status. For more detail, use MyGeotab's Watchdog report.
- Click a slice to show only its assets in the table.
- Click a label under a chart to hide that slice.
- Each chart shows the 10 largest slices plus "Other".
- CSV exports: all assets in the current view, a summary per chart, or the table's current results (selected slice and search).

The add-in only reads data. Users see only the assets and groups their MyGeotab account can already see.

## Install

1. In MyGeotab, go to **Administration › System › System Settings › Add-Ins**.
2. Set **Allow unverified Add-Ins** to **Yes**. This is a custom add-in, so it isn't signed.
3. Click **New Add-In**, open the **Configuration** tab, and paste the contents of [`config.json`](config.json).
4. Click **Done**, then **Save**. The page appears in the menu as **Fleet Hardware Breakdown**.

## Versions and updates

Each release is a git tag (for example `v4.1.0`). The configuration points at one tag through jsDelivr:

```
https://cdn.jsdelivr.net/gh/tylerscottGT/fleet-hardware-breakdown@v4.1.0/composition.html
```

To move a database to a new release, update the version and the URL in its add-in configuration. Databases stay on their tag until someone changes them, so work in progress on `main` never reaches users.

## Requirements

- The user's account needs permission to view assets and groups. Camera data needs camera access. Without it, the camera chart shows "Camera data unavailable" and the rest still works. Likewise, without access to device status the Communicating column shows "Unknown".
- The browser must be able to reach `cdn.jsdelivr.net`.

## Files

| File | Purpose |
|---|---|
| `composition.html` | The add-in page and code |
| `config.json` | Add-in configuration to paste into MyGeotab |
| `vendor/chart.umd.min.js` | [Chart.js](https://www.chartjs.org) 4.4.1, MIT license (see `vendor/Chart.js-LICENSE.md`) |

## Credits

The original version was built with the [Vibe Coding and Geotab Guide](https://github.com/fhoffa/geotab-vibe-guide).
