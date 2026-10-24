# Carlinkit T2C Ultimate Wrapper

A single-file web page that fixes the cropped or stretched CarPlay picture of the **Carlinkit T2C** adapter in the Tesla browser, with large on-screen controls for size and proportions.

> Unofficial project. Not affiliated with Carlinkit, Apple or Tesla.

---

## The problem

After a recent Tesla software update, the T2C's CarPlay interface (served at `tespush.com`) lays out wider than the Tesla browser window. As a result:

- the right side of the screen is cut off, hiding app controls (for example Waze's search, sound and report buttons);
- some existing workarounds squeeze the picture horizontally, so icons look stretched instead of square.

## How it works

The wrapper loads the adapter's CarPlay page inside a frame and applies two independent scale factors:

| Control | What it does |
|---|---|
| **Size** | Scales the picture evenly in both directions. A lower value gives the adapter a larger virtual screen, so more of the interface fits; a higher value makes everything bigger. It never distorts the picture. |
| **Width** | Adjusts the horizontal scale only, to correct any remaining squeeze or stretch. At 100% the picture keeps its original proportions. |

The frame always fills the browser window exactly, so nothing is cropped by the wrapper itself.

The wrapper only changes the frame's size and position. The CarPlay video stream still travels from the adapter over its own local Wi-Fi; nothing is routed through GitHub or any other server.

## Features

- Separate **Size** (40–220%) and **Width** (60–160%) controls with large, car-friendly buttons
- **Reconnect** button that reloads the CarPlay stream without reloading the page
- **Reset** button that restores the default Size and Width
- Adapter address selector: `tespush.com` (https), adapter IP (https) or adapter IP (http), plus a custom address field
- Settings button placed in the top-left corner, over the CarPlay clock, so it doesn't block app controls; it can be faded out with **Hide ⚙︎**
- Settings are saved both in the browser and in the page link, so a bookmark keeps your setup
- One self-contained HTML file with no external dependencies

## Requirements

- A Carlinkit T2C adapter already working with your Tesla
- A free GitHub account (to host the page)
- Internet access in the car to load the wrapper page itself. This normally comes through the T2C, from your phone's hotspot or the adapter's SIM.

## Setup

### 1. Host your own copy

1. Create a new **public** repository on GitHub, for example `t2c`.
2. Click **Add file → Upload files**, upload `index.html`, and commit.
3. Open **Settings → Pages**, set the source to the **main** branch (root folder), and save.
4. After a minute or two, GitHub shows your page link, for example:
   `https://<your-username>.github.io/t2c/`

Alternatively, fork this repository and enable Pages on your fork in the same way.

### 2. Use it in the car

1. Plug in the T2C and let your phone connect to CarPlay as usual.
2. Connect the Tesla to the adapter's Wi-Fi (`AutoKit-xxxx`).
3. Open the Tesla browser and go to your page link.
4. Tap the **⚙︎** button in the top-left corner and adjust **Size** and **Width** **while parked**.
5. Bookmark the page once it looks right. The bookmark stores your settings.

## Recommended settings

| Car / screen | Size | Width | Notes |
|---|---|---|---|
| Tesla Model 3 (2021), browser in normal view | 70% | 100% | Tested. These are the built-in defaults. |

Other models and screen layouts may need different values. Use this as a starting point:

- **Right side cut off:** lower **Size** one step at a time.
- **Everything too small:** raise **Size** until just before the right edge starts cutting off.
- **Icons tall and narrow:** press **Width +**.
- **Icons short and wide:** press **Width −**.
- Square icons mean the proportions are correct.

Tip: the Tesla browser's full-screen button (⤢) gives the page more room, which lets you use a higher Size before anything is cut off.

## URL parameters

All settings can also be set in the link, which is useful for keeping several bookmarks:

| Parameter | Values | Default | Description |
|---|---|---|---|
| `zoom` | `0.4`–`2.2` | `0.7` | Size (0.7 = 70%) |
| `aspect` | `0.6`–`1.6` | `1.0` | Width correction (1.0 = original proportions) |
| `src` | URL | `https://tespush.com/` | Address of the adapter's CarPlay page |
| `gear` | `1` or `0` | `1` | `0` fades out the settings button |

Example:

```
https://<your-username>.github.io/t2c/?zoom=0.7&aspect=1&src=https://tespush.com/
```

Adding `#settings` to the link opens the settings panel on load.

Settings in the link take priority over settings saved in the browser.

## Troubleshooting

**The page loads but stays black**
- Make sure your phone is connected to the T2C and CarPlay is running. The frame stays black until the adapter sends a picture.
- Open ⚙︎ and try another adapter address, then press **Reconnect**. The Tesla browser blocks plain `http://` content inside an `https://` page, so the https options are the most likely to work.
- Check that an old bookmark isn't loading outdated settings. Open the clean link (no `?…` at the end) and bookmark it again.

**The page doesn't load at all**
- The car needs internet access to fetch the wrapper. Check that your phone's hotspot (or the adapter's SIM) is providing data to the T2C.

**The right edge is still cut off**
- Lower **Size** one step at a time.

**Everything looks blurry when enlarged**
- The wrapper enlarges the picture the adapter sends; it can't add detail. Sharpness depends on the adapter's own output resolution.

**The settings button is in the way**
- Tap ⚙︎ → **Hide ⚙︎**. Tapping the faded button brings it back.

## Limitations

- This is a display workaround, not a firmware fix. A corrected official firmware from Carlinkit would make it unnecessary.
- It can't increase sharpness beyond what the adapter outputs.
- It depends on the adapter's CarPlay page loading inside a frame; future Carlinkit or Tesla updates could change that.
- Only tested on a 2021 Tesla Model 3.

## Privacy

The page collects no data and has no analytics. Your settings are stored only in your own browser and in your bookmark link. The CarPlay stream stays on the adapter's local network.

## Safety

Adjust settings only while parked. Don't interact with the settings panel while driving.

## Credits

Inspired by earlier community wrappers for the same issue, including [kniaza/carlinkit-t2c-wrapper](https://github.com/kniaza/carlinkit-t2c-wrapper) and [oleksandrbovchaliuk/carlinkit-t2c-wrapper](https://github.com/oleksandrbovchaliuk/carlinkit-t2c-wrapper).

## Disclaimer

Provided as-is, without warranty of any kind. Use at your own risk. Carlinkit, CarPlay and Tesla are trademarks of their respective owners.
