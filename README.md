# Carlinkit T2C Ultimate Wrapper

Fixes the cropped or stretched CarPlay picture of the **Carlinkit T2C** adapter in the Tesla browser.

Other wrappers make the full screen visible by squashing it, so icons look stretched and the picture loses sharpness. This one keeps the original proportions, and at the default setting it shrinks the picture rather than enlarging it, so it stays sharp.

![Before and after](screenshots/00-before-after.jpg)

## How to use

1. Connect the Tesla to the T2C's Wi-Fi (`AutoKit-xxxx`) and start CarPlay as usual.
2. In the Tesla browser, open:

   **https://blbrln.github.io/t2c/**

3. Bookmark it.

## Settings

Tap **⚙︎** in the top-left corner (while parked):

- **Size**: makes everything bigger or smaller without distortion. Lower it if the right side is cut off.
- **Width**: corrects squeeze. Square icons mean it's right.
- **Reconnect**: reloads the CarPlay stream.

Defaults (70% / 100%) are tested on a 2021 Model 3. Your settings are saved in the link, so bookmark the page after adjusting.

![Settings panel](screenshots/03-settings.jpg)

## Troubleshooting

- **Black screen:** make sure CarPlay is running, then open ⚙︎, try another adapter address and press **Reconnect**.
- **Page doesn't load:** the car needs internet (via your phone's hotspot or the T2C's SIM) to load the page. The CarPlay stream itself stays local.

## Notes

- Display workaround only. It doesn't change the adapter's firmware. Raising Size above 100% enlarges the picture and can soften it.
- No data is collected.
- Unofficial. Not affiliated with Carlinkit, Apple or Tesla. Use at your own risk.
