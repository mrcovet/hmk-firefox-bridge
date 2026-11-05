# hmk-firefox-bridge
Automatic updates for the HârnMaster Kèthîra Firefox VTT Bridge.

# HMK Kèthîra ↔ Roll20 VTT Bridge

**Connect the HMK Kèthîra Workshop and DM Toolkit to Roll20.**

The **HMK Kèthîra VTT Bridge** is a browser extension that connects the standalone HMK character and game-management tools to a Roll20 tabletop session. It carries supported game rolls, reports, and character-owner messages between HMK and Roll20, reducing the need to copy results into chat or coordinate everything manually.

It is designed for groups playing **HârnMaster Kèthîra** with the companion HMK Workshop and, where applicable, the DM Toolkit.

> **Project status:** The Firefox extension is live-tested, permanently installable, and verified to update automatically. The Chrome extension has been submitted to the Chrome Web Store and is awaiting review.

## What it does

- **Sends supported HMK rolls and game events to Roll20**, where the companion Roll20 Mod can process and display them.
- **Relays supported two-way game messages** between connected HMK Workshop/DM Toolkit sessions, including owner-authoritative character interactions.
- **Lets you choose the Roll20 game tab** to receive HMK events and turn automatic forwarding on or off.
- **Shows connection and delivery status** in the browser extension popup, including the latest HMK event.
- **Offers optional local character backups**, with a manual JSON download and an automatic backup option when the Toolkit tab closes.

The bridge is a **connection layer**, not a replacement for the HMK Workshop, the DM Toolkit, the Roll20 game, or the companion Roll20 Mod. Available automation depends on the HMK tools and Roll20 Mod versions in use.

## Install and get connected

### Firefox — available now

1. [Install the signed Firefox extension](https://mrcovet.github.io/hmk-firefox-bridge/releases/HMK_Firefox_VTT_Bridge_v0.3.2_signed.xpi) using Firefox. The signed extension receives future updates through this project's hosted update manifest.
2. Open `about:addons` → **HMK Kèthîra VTT Bridge** → **Permissions & Data** and enable **Access local files on your computer**. This is required when using the local `.html` Workshop or DM Toolkit files.
3. Open your HMK Workshop (or DM Toolkit) and your Roll20 game in Firefox.
4. Click the **HMK VTT Bridge** toolbar icon. Confirm that the HMK tool and Roll20 are detected.
5. In the Roll20 game tab, use **Use current Roll20 game tab** in the bridge popup to select that game. Enable **Automatically send HMK events to Roll20** if desired.
6. Make a test roll in HMK and check that the result reaches Roll20.

### Chrome — awaiting Web Store review

The Chrome version uses the **Chrome Web Store** for installation and updates. Its listing will be linked here after approval. Chrome users will also need to open `chrome://extensions` → **HMK Kèthîra VTT Bridge** → **Details** and enable **Allow access to file URLs** for locally opened HMK HTML files.

**For either browser:** The GM should ensure the compatible **HMK Roll20 Mod** is installed and configured in the Roll20 game for the supported Roll20-side commands, displays, and automation. The browser extension alone does not install the Mod.

## Troubleshooting

| Symptom | What to check |
| --- | --- |
| Workshop not detected | Enable local-file access for the extension; reload the HMK HTML page. |
| Roll20 not detected | Open the actual Roll20 **game editor**, not just the Roll20 homepage, and check the selected game tab. |
| Rolls do not appear | Check **Automatically send HMK events to Roll20**, the selected target tab, the popup's delivery status, and the companion Roll20 Mod in the game. |
| Duplicate output | Disable or remove any older temporary/unpacked copy of the bridge running alongside the signed/store version. |
| Browser updated but connection stopped | Recheck local-file access and reload both HMK and Roll20 tabs. |

## Privacy and data handling

The bridge processes HMK game information—including character and player display names, roll results, selected game messages, and optional character backup snapshots—to deliver its stated functionality. Relevant messages are relayed to the **Roll20 game you select**. Some settings, delivery metadata, and optional backups are retained in browser-local extension storage or saved as user-requested downloads.

The bridge is **not an analytics service** and does not send HMK game data to the extension developer. It does not require a separate HMK cloud account. Keep in mind that information posted to Roll20 may be visible to participants according to your game settings.

Read the [Firefox privacy information](https://mrcovet.github.io/hmk-firefox-bridge/privacy.html) or [Chrome privacy information](https://mrcovet.github.io/hmk-firefox-bridge/chrome-privacy.html) for details.

## Releases and updates

- **Firefox:** Current verified version **0.3.2**. The v0.3.1 → v0.3.2 update was successfully delivered through Firefox's automatic-update mechanism using this project's [update manifest](https://mrcovet.github.io/hmk-firefox-bridge/updates.json). Each Firefox release is signed by Mozilla before publication.
- **Chrome:** Version **0.3.1** has been submitted for Chrome Web Store review. Once approved and installed from the store, Chrome updates will be distributed by Google.

The Firefox and Chrome extensions share the same HMK message formats: `hmk-vtt/1` and `hmk-link/1`.

## Project scope

This repository hosts browser-bridge releases, update files, and supporting documentation for the HMK Kèthîra ↔ Roll20 integration. The HMK Workshop, DM Toolkit, and Roll20 Mod are companion components maintained and tested separately.

This is an independent companion project. It is not an official Roll20 product and is not affiliated with or endorsed by Roll20.
