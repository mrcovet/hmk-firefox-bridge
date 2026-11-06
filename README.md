HMK Kèthîra ↔ Roll20 VTT Bridge
Connect the HMK Kèthîra Workshop and DM Toolkit to Roll20 in Firefox or Chrome.

The HMK Kèthîra VTT Bridge is a browser extension that connects the standalone HMK character and game-management tools to a Roll20 tabletop session. It carries supported game rolls, reports, and character-owner messages between HMK and Roll20, reducing the need to copy results into chat or coordinate everything manually.

It is designed for groups playing HârnMaster Kèthîra with the companion HMK Workshop and, where applicable, the DM Toolkit.
Project status (November 6, 2026): Firefox v0.3.2 and Chrome v0.3.2 are both live-tested and permanently installable. Both have passed a real v0.3.1 → v0.3.2 automatic-update test. Firefox updates are distributed through a Mozilla-signed, self-hosted release; Chrome updates are distributed by the Chrome Web Store.

Install the bridge
Browser	Current verified version	Installation	Updates
Firefox	v0.3.2	Install the signed Firefox extension	Automatic, using the hosted update manifest
Chrome	v0.3.2	Install from the Chrome Web Store	Automatic, through the Chrome Web Store


The Chrome listing is Unlisted: use the direct installation link above. Neither browser requires Developer Mode or a temporary/unpacked extension for ordinary installation.
Firefox setup
1. Open the signed Firefox installation link in Firefox and install the add-on.
2. Open about:addons → HMK Kèthîra VTT Bridge → Permissions & Data. Enable Access local files on your computer. This is essential when opening the Workshop or DM Toolkit as a local .html file.
3. Open your HMK Workshop (or DM Toolkit) and your Roll20 game in Firefox.
4. Click the HMK VTT Bridge toolbar icon and confirm that the HMK tool and Roll20 are detected.
5. In the Roll20 game tab, select Use current Roll20 game tab in the bridge popup. Enable Automatically send HMK events to Roll20 if desired.
6. Make a test roll in the HMK tool and check that it reaches Roll20.
Firefox download and update information
Chrome setup
1. Open the HMK Kèthîra VTT Bridge listing in the Chrome Web Store in Chrome and select Add to Chrome.
2. Open chrome://extensions → HMK Kèthîra VTT Bridge → Details. Enable Allow access to file URLs. This is essential when opening the Workshop or DM Toolkit as a local .html file.
3. Open your HMK Workshop (or DM Toolkit) and your Roll20 game in Chrome.
4. Click the HMK VTT Bridge toolbar icon and confirm that the HMK tool and Roll20 are detected.
5. In the Roll20 game tab, select Use current Roll20 game tab in the bridge popup. Enable Automatically send HMK events to Roll20 if desired.
6. Make a test roll in the HMK tool and check that it reaches Roll20.
For either browser: The GM should ensure the compatible HMK Roll20 Mod is installed and configured in the Roll20 game for supported Roll20-side commands, displays, and automation. The browser extension alone does not install the Mod.
What it does
- Sends supported HMK rolls and game events to Roll20, where the companion Roll20 Mod can process and display them.
- Relays supported two-way game messages between connected HMK Workshop/DM Toolkit sessions, including owner-authoritative character interactions.
- Lets you choose the Roll20 game tab to receive HMK events and turn automatic forwarding on or off.
- Shows connection and delivery status in the browser extension popup, including the latest HMK event.
- Offers optional local character backups, with a manual JSON download and an automatic backup option when the Toolkit tab closes.
The bridge is a connection layer, not a replacement for the HMK Workshop, the DM Toolkit, the Roll20 game, or the companion Roll20 Mod. Available automation depends on the HMK tools and Roll20 Mod versions in use.
Troubleshooting
Symptom	What to check
Workshop not detected	Enable the browser's local-file access permission for the bridge; reload the HMK .html page.
Roll20 not detected	Open the actual Roll20 game editor, not just the Roll20 homepage, and check the selected game tab in the popup.
Rolls do not appear	Check Automatically send HMK events to Roll20, the selected target tab, the popup's delivery status, and the companion Roll20 Mod in the game.
Duplicate output	Disable or remove older temporary/unpacked copies of the extension so only the signed Firefox or store-installed Chrome version is active in that browser.
Browser updated but connection stopped	Recheck local-file access and reload both HMK and Roll20 tabs.


Privacy and data handling
The bridge processes HMK game information—including character and player display names, roll results, selected game messages, and optional character backup snapshots—to deliver its stated functionality. Relevant messages are relayed to the Roll20 game you select. Some settings, delivery metadata, and optional backups are retained in browser-local extension storage or saved as user-requested downloads.

The bridge is not an analytics service and does not send HMK game data to the extension developer. It does not require a separate HMK cloud account. Keep in mind that information posted to Roll20 may be visible to participants according to your game settings.

Read the Firefox privacy information or Chrome privacy information for details.
Releases and updates
- Firefox — v0.3.2 (live accepted): Mozilla-signed releases are hosted by this project. The update manifest identifies the published packages. The v0.3.1 → v0.3.2 automatic update was tested successfully, including connection, roll delivery, permissions and browser restart.
- Chrome — v0.3.2 (live accepted): Install from the Chrome Web Store. Google distributes published updates. The v0.3.1 → v0.3.2 automatic update was tested successfully, including connection, roll delivery, permissions and browser restart.
For existing installations, the normal browser update process is the supported path; routine updates do not require re-installing an unpacked extension. The Firefox and Chrome extensions share the HMK message formats hmk-vtt/1 and hmk-link/1.
Project scope
This repository hosts Firefox browser-bridge releases, update files and supporting documentation for both supported browsers. The Chrome extension is published through the Chrome Web Store, not installed from a GitHub ZIP. The HMK Workshop, DM Toolkit, and Roll20 Mod are companion components maintained and tested separately.

This is an independent companion project. It is not an official Roll20 product and is not affiliated with or endorsed by Roll20.
