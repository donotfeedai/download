# Installing Do Not Feed AI

[Polski](INSTALACJA.md) · **English**

Steps: the program, the extension, a connection check, the licence. On Windows one installer puts the program and
the extension in place at once. You need both: the program detects and replaces the data, the extension hands it
what you send to the chat - without the program the extension does not mask anything. Everything happens on your
machine - neither the extension nor the program talks to any vendor server.

Supported browsers: Chrome, Edge and Firefox on Windows; Chrome and Firefox on macOS. Edge on macOS is not
supported.

## macOS

1. **Download and install the program**: `donotfeedai-macos.pkg` → double-click → the installer asks for an
   administrator password (it installs into `/Applications`). The installer registers the program with your
   browsers.
   The installer is signed with a Developer ID certificate and notarized by Apple, so Gatekeeper should leave it
   alone. If it does not, check the signature: `pkgutil --check-signature donotfeedai-macos.pkg`.

2. **Extension**:
   - Firefox: open [donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi) in Firefox, click
     **Continue to Installation** and **Add**. The extension is signed by Mozilla and stays installed, no developer
     mode needed. The same file is in the release as `donotfeedai-wtyczka-firefox.xpi`.
   - Chrome (Edge is not supported on macOS): unzip `donotfeedai-wtyczka-chrome.zip` somewhere permanent
     (e.g. `~/Documents`), then `chrome://extensions` → **Developer mode** → **Load unpacked** → pick the
     `donotfeedai-wtyczka-chrome-<version>` folder (the one with `manifest.json` inside).

   **Do not move that folder** afterwards - the extension loads from it on every browser start.

3. **Quit the browser completely** (Cmd+Q - closing the window is not enough) and start it again. The browser
   reads the program registration at startup.

4. **Check**: click the extension icon (the side panel opens). You should see the program as connected and the
   line with the extension and program versions. Chrome will show a "disable developer mode extensions" bar -
   ignore it; the store version does not have it.

5. **Load the licence** (see [Licence](#licence)).

## Windows

Windows 10 and 11 (x64), including Windows 11 on ARM.

1. **Download and run the installer**: `donotfeedai-windows-setup.exe` → double-click. The installer needs no
   administrator rights: it installs the program and the extension for your account
   (`%LOCALAPPDATA%\Programs\donotfeedai`) and registers the program with Chrome, Edge and Firefox
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
   **Select Folder**. Firefox: open [donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi) and click
   **Continue to Installation** → **Add** (signed by Mozilla, stays installed). No browser restart is needed.

3. **Check**: click the puzzle icon, pin Do Not Feed AI and click its icon - the panel should show the program as
   connected. Later installer versions also update the extension in the same folder (the browser loads the new
   version the next time it starts).

4. **Load the licence** (see [Licence](#licence)).

**Deployment by IT** (no dialogs):

```
donotfeedai-windows-setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

The install is per user, so run the command in the user's context (in Intune: *Install behavior: User*). The install
log goes to `%TEMP%\Setup Log *.txt`. The default folder is `%LOCALAPPDATA%\Programs\donotfeedai`; another one can be
set with `/DIR="D:\Programs\donotfeedai"` (the installer does not ask for a folder, and the end-user guide assumes the
default one).

## When the program is missing or not responding

The extension has no engine of its own, so without the program it does not mask anything and says so:

| situation | bar in the chat | sending a message | files |
|---|---|---|---|
| no program | "Install the Do Not Feed AI program" | after the "Send without masking" question | held back |
| program not responding | "Protection unavailable" | after the "Send without masking" question | held back |
| program older than the extension | "The program is too old" | after the "Send without masking" question | held back |
| no licence | "Protection off: no license" (red) | unchanged, unmasked | unchanged |

Program not responding: quit the browser completely and start it again; if that does not help, reinstall the
program.

## Updating

**Program**: download the new installer from the latest release (`donotfeedai-macos.pkg` or
`donotfeedai-windows-setup.exe`) and install it - it overwrites the previous version (the licence stays in the user
data folder). Update the program and the extension together: the extension does not work with an older program.

**Extension** (loaded unpacked) does not update itself. Updating means replacing files:

1. Unzip the new `donotfeedai-wtyczka-chrome-<new version>.zip`.
2. Either:
   - copy the **contents** of the new folder into the old one (the folder `chrome://extensions` points at,
     overwriting files), then click the reload icon on the extension card, or
   - point **Load unpacked** at the new folder - the extension ID is fixed, so Chrome swaps the version instead
     of creating a second copy.
3. Refresh your chat tabs (Cmd+R / F5). A tab that was open before the update still runs the old copy of the
   extension.
4. Check the line with the extension and program versions in the panel - both versions should match.

What you **do not** need to do: do not remove the extension (the trash icon in `chrome://extensions`) -
replacing files loses nothing, while removing is needless risk for your settings. Settings and licence survive an
update. The program reloads the replacement maps of open tabs after reconnecting; after a browser restart they
start from scratch.

## Uninstalling

**macOS**:

```
sudo /Applications/donotfeedai/uninstall.sh            # binaries, menu bar icon + browser registration
sudo /Applications/donotfeedai/uninstall.sh --purge    # also licence and tab map copies (asks for confirmation)
```

**Windows**: **Settings → Apps → Installed apps** → *Do Not Feed AI companion* → **Uninstall** (removes the program
and the browser registration). The licence stays; to remove it too, delete the `%LOCALAPPDATA%\donotfeedai`
folder and, in **Credential Manager → Windows Credentials**, the entries containing "donotfeedai".

The extension is removed separately in `chrome://extensions` (Firefox: `about:addons` → Do Not Feed AI → **Remove**).

## Licence

The program works with a Pro or Business licence. The trial is a licence with a short expiry date - we send it on
request: [kontakt@donotfeedai.pl](mailto:kontakt@donotfeedai.pl). Without a licence protection is off.
A licence file (`.lic`) is loaded on macOS in the Do Not Feed AI icon in the menu bar, next to the clock ("Load
license…" or "Paste license from clipboard"), and on Windows in the extension panel ("Load a licence file").
`dnf license install file.lic` always works too; in a company, MDM can place it in the data folder. The licence is verified locally
by the program with a digital signature - there is no licence server and no network traffic.
