# Installing Do Not Feed AI

[Polski](INSTALACJA.md) · **English**

Three steps: the program (companion), the extension, then check the connection. On Windows one installer puts
the program and the extension in place at once. The extension alone masks text in the chat (Free); the companion
is needed for Pro features: the full first/last name dictionary, technical data, files and the encrypted session.
Everything happens on your machine - neither the extension nor the companion talks to any vendor server.

## macOS

1. **Download and install the companion**: `donotfeedai-macos.pkg` → double-click → the installer asks for an
   administrator password (it installs into `/Applications`). The installer registers the program with your
   browsers.
   The installer is signed with a Developer ID certificate and notarized by Apple, so Gatekeeper should leave it
   alone. If it does not, check the signature: `pkgutil --check-signature donotfeedai-macos.pkg`.

2. **Extension**: unzip `donotfeedai-wtyczka-chrome.zip` (Firefox: `-firefox.zip`) somewhere permanent
   (e.g. `~/Documents`), then:
   - Chrome / Edge / Brave / Chromium: `chrome://extensions` → **Developer mode** → **Load unpacked** → pick the
     `donotfeedai-wtyczka-chrome-<version>` folder (the one with `manifest.json` inside),
   - Firefox: `about:debugging#/runtime/this-firefox` → **Load Temporary Add-on** → pick `manifest.json` from the
     unpacked folder. Temporary add-ons disappear when Firefox restarts; a permanent version will be on AMO.

   **Do not move that folder** afterwards - the extension loads from it on every browser start.

3. **Quit the browser completely** (Cmd+Q - closing the window is not enough) and start it again. The browser
   reads the companion registration at startup.

4. **Check**: click the extension icon (the side panel opens). You should see the companion as connected and the
   `extension X · companion Y` line. Chrome will show a "disable developer mode extensions" bar - ignore it;
   the store version does not have it.

## Windows

Windows 10 and 11 (x64), including Windows 11 on ARM.

1. **Download and run the installer**: `donotfeedai-windows-setup.exe` → double-click. The installer needs no
   administrator rights: it installs the program and the extension for your account
   (`%LOCALAPPDATA%\Programs\donotfeedai`) and registers the program with Chrome, Edge, Brave, Chromium and Firefox
   by itself. At the end it offers to open the page with the last step: https://donotfeedai.com/start
   The installer and the programs are **code-signed** with a certificate issued by Microsoft (Artifact Signing):
   the publisher is *Sebastian Obara It&Consulting* (right-click the file → **Properties → Digital Signatures**, or in
   PowerShell `Get-AuthenticodeSignature .\donotfeedai-windows-setup.exe`). The publisher is new, so for the first
   weeks SmartScreen may still show "Windows protected your PC" - the dialog already names the publisher; click
   **More info → Run anyway**.

2. **Show the extension to your browser** (once): the installer put it in
   `%LOCALAPPDATA%\Programs\donotfeedai\wtyczka-chrome` - nothing to download or unzip. In `edge://extensions`
   (Chrome: `chrome://extensions`) turn on **Developer mode** (in Edge the switch is at the bottom of the left pane),
   click **Load unpacked**, paste the path above into the address bar of the folder dialog, press Enter and click
   **Select Folder**. Firefox: **Load Temporary Add-on** in `about:debugging#/runtime/this-firefox` and the file
   `...\wtyczka-firefox\manifest.json`. No browser restart is needed.

3. **Check**: click the puzzle icon, pin Do Not Feed AI and click its icon - the panel should show the companion as
   connected. Later installer versions also update the extension in the same folder (the browser loads the new
   version the next time it starts).

**Deployment by IT** (no dialogs):

```
donotfeedai-windows-setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

The install is per user, so run the command in the user's context (in Intune: *Install behavior: User*). The install
log goes to `%TEMP%\Setup Log *.txt`.

## What the companion does and does not do

| feature | without the companion | with the companion |
|---|---|---|
| masking chat text | yes | yes |
| restoring AI replies | yes | yes |
| files xlsx / docx / csv / txt / configs / logs | no (file held back) | yes |
| technical data: secrets, hosts, IPs, logins | no | yes |
| encrypted on-disk session | no (tab memory only) | yes |

## Updating

**Companion**: download the new installer from the latest release (`donotfeedai-macos.pkg` or
`donotfeedai-windows-setup.exe`) and install it - it overwrites the previous version (licence and sessions stay in
the user data folder).

**Extension** (loaded unpacked) does not update itself. Updating means replacing files:

1. Unzip the new `donotfeedai-wtyczka-chrome-<new version>.zip`.
2. Either:
   - copy the **contents** of the new folder into the old one (the folder `chrome://extensions` points at,
     overwriting files), then click the reload icon on the extension card, or
   - point **Load unpacked** at the new folder - the extension ID is fixed, so Chrome swaps the version instead
     of creating a second copy.
3. Refresh your chat tabs (Cmd+R / F5). A tab that was open before the update still runs the old copy of the
   extension.
4. Check the `extension X · companion Y` line - both versions should match.

What you **do not** need to do: do not remove the extension (the trash icon in `chrome://extensions`) -
replacing files loses nothing, while removing is needless risk for your settings, licence and session. Settings,
licence and the encrypted on-disk session survive an update; only a session in "memory only" mode is lost,
because it lives in browser memory.

## Uninstalling

**macOS**:

```
sudo /Applications/donotfeedai/uninstall.sh            # binaries + browser registration
sudo /Applications/donotfeedai/uninstall.sh --purge    # also licence and sessions (asks for confirmation)
```

**Windows**: **Settings → Apps → Installed apps** → *Do Not Feed AI companion* → **Uninstall** (removes the program
and the browser registration). Licence and sessions stay; to remove them too, delete the `%LOCALAPPDATA%\donotfeedai`
folder and, in **Credential Manager → Windows Credentials**, the entries containing "donotfeedai".

The extension is removed separately in `chrome://extensions` (Firefox: `about:debugging`).

## Licence and tiers

Without a licence file you get **7 days of full Pro** from the first launch; after that the extension drops to
Free. A licence file (`.lic`) is loaded in the extension popup ("Load a licence file"). The licence is verified
locally with a digital signature - there is no licence server and no network traffic.
