# Do Not Feed AI - downloads

[Polski](README.md) · **English**

<img src="assets/social-preview.png" alt="Do Not Feed AI: client data stays on your computer. The extension detects names, national IDs, bank accounts, phones and addresses and replaces them with fictional data before your text or file reaches ChatGPT, Claude, Gemini or Copilot.">

Do Not Feed AI detects names, national IDs, phone numbers, addresses and data in files, then replaces them with
realistic fictional data **before the message leaves your computer**. The model's reply comes back with the real values restored. Everything is
done by a program on your machine. Do Not Feed AI works locally: it does not send data to the vendor, collect statistics or track user activity, and it needs no account and no server connection to verify the license.

Do Not Feed AI is a **desktop program** (Windows, macOS) plus a **browser extension**, used together: the program
detects and replaces the data, the extension hands it what you send to the chat. It works with a license; a
trial license is sent on request ([contact@donotfeedai.com](mailto:contact@donotfeedai.com)).

This repository is **distribution only**: the program installer and the browser extension. The source code is
not published here. The software is proprietary, all rights reserved; the terms of use are set out in the license
agreement (OWU) supplied together with the license.

**zero network calls** · **Polish identifiers: PESEL, NIP, REGON, IBAN** · **xlsx, docx, csv, txt**

<p><b>Works in:</b>
<img src="assets/browsers/chrome.svg" width="20" alt="Chrome"> Chrome &nbsp;
<img src="assets/browsers/edge.svg" width="20" alt="Edge"> Edge (Windows) &nbsp;
<img src="assets/browsers/firefox.svg" width="20" alt="Firefox"> Firefox<br>
Windows: Chrome, Edge, Firefox · macOS: Chrome, Firefox</p>

<p><b>Masks in:</b>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/chatgpt-dark.svg"><img src="assets/chats/chatgpt.svg" width="20" alt="ChatGPT"></picture> ChatGPT &nbsp;
<img src="assets/chats/claude.svg" width="20" alt="Claude"> Claude &nbsp;
<img src="assets/chats/gemini.svg" width="20" alt="Gemini"> Gemini &nbsp;
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/copilot-dark.svg"><img src="assets/chats/copilot.svg" width="20" alt="Copilot"></picture> Copilot</p>

<p><b>Systems:</b>
<img src="assets/os/apple.svg" width="20" alt="macOS"> macOS &nbsp;
<img src="assets/os/windows.svg" width="20" alt="Windows"> Windows</p>

Website: [donotfeedai.com](https://donotfeedai.com) · Privacy policy: [donotfeedai.com/polityka-prywatnosci.html](https://donotfeedai.com/polityka-prywatnosci.html) (Polish)

## What to download

The `latest/download/...` links always point to the newest version, so they never need updating.
All releases (with version numbers and changelogs):
[github.com/donotfeedai/download/releases](https://github.com/donotfeedai/download/releases).

| file | for |
|---|---|
| **[donotfeedai-macos.pkg](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-macos.pkg)** | **macOS** - program: signed and notarized installer, Gatekeeper will not complain |
| **[donotfeedai-windows-setup.exe](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-windows-setup.exe)** | **Windows 10/11** - program and extension: per-user installer, no administrator rights. Code-signed (certificate issued by Microsoft), publisher: Sebastian Obara It&Consulting |
| **[donotfeedai-windows.msi](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-windows.msi)** | **Windows 10/11, for IT departments** - the same program and extension as in the installer, for deployment through Group Policy, Intune and SCCM (per-computer or per-user install); details in [INSTALL.en.md](INSTALL.en.md#windows). Code-signed |
| **[donotfeedai-wtyczka-chrome.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-chrome.zip)** | **Chrome** (macOS) - extension, loaded unpacked; on Windows the Chrome and Edge extension comes with the installer |
| **[donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi)** | **Firefox** - extension signed by Mozilla: open the link in Firefox and click **Add**, it stays installed ([same file on GitHub](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-firefox.xpi)) |
| [donotfeedai-wtyczka-firefox.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-firefox.zip) | Firefox - the same extension unsigned, for testing as a temporary add-on |
| **[SHA256SUMS.txt](https://github.com/donotfeedai/download/releases/latest/download/SHA256SUMS.txt)** | checksums for the downloaded files |

**You need both: the program and the extension.** Without the program the extension does not mask anything - it
says so in the bar in the chat and asks before every send whether to send the message unmasked.

## How it works

<img src="assets/how-it-works.svg" width="928" alt="Flow: text and files are masked locally, the AI service receives replacements for the detected data, and the reply is restored on your machine. The map of originals stays on your computer.">

*The AI receives replacements for the detected data, and the map of originals stays on your computer: it lives in the program, separately for each chat tab, and is deleted when the tab is closed.*

- **Chat text**: you type as usual and the extension takes over the send - the program detects the data, the extension substitutes it in the box,
  sends the replacements, and restores the originals in the model's reply. What you see on screen is always real.
- **Files**: you add an xlsx, docx, csv or txt as usual. The extension stops the upload, the program masks the data in
  the file's content on your machine, and the chat receives `plik_anon.xlsx`. From Excel and Word files it is a simplified
  copy with values and text only: formula results instead of formulas, and no formatting, charts, images or macros.
  Your original stays with you, unchanged.
- **Secrets and configs**: passwords, tokens and keys are masked by the program, in `.env` files,
  `docker-compose.yml` and logs too.
- **Clipboard (outside the browser, Pro and Business)**: in a code editor, a terminal or any other program you copy text and press the
  **Anonymize** shortcut (Windows `Ctrl+Win+A`, macOS `Ctrl+Option+A`): the clipboard now holds the text with replacements, which you
  paste into the AI. You copy the reply and press **Restore** (`Ctrl+Win+R`, `Ctrl+Option+R`). The shortcuts are off by default: you
  turn them on in the program's menu icon. This is not an extension inside the editor: the program reads the clipboard only after you
  press a shortcut (or pick the command in the menu). The system clipboard history and clipboard managers may keep the original that
  was copied before you used the shortcut.
- **A file from the program menu (Pro and Business)**: "Anonymize file..." and "Restore file..." in the program's menu icon (the menu
  bar on macOS, the tray on Windows). Next to the original a file with a neutral name ending in `_anon` appears; the map of originals
  is stored encrypted on your computer and deleted after 30 days. A PDF with a text layer becomes a docx or txt (without page layout
  and graphics); from jpg and png images we remove only the metadata (the content of the image is not masked).

## What it detects

| data | how |
|---|---|
| full name | including inflected forms (“dla Magdaleny”, “do Kowalskiego”); the replacement comes back in the same grammatical case; also written in capital letters: “JAN KOWALSKI” |
| PESEL (national ID) | checksum or a plausible date of birth |
| NIP, REGON, IBAN, ID card number | checksum validation, so an order number is not mistaken for a NIP |
| phone and e-mail | e-mail in a person's pattern: `s.obara@` → `s.zalewski@`; 9-digit numbers, with `+48`, dashes and spaces |
| address, postal code and city | “ul. Długa 7” next to other personal data |
| company | Sp. z o.o., S.A., Sp. j., Ltd., GmbH, also in capital letters |
| custom phrases | project, client and product names; in Business also a company dictionary in the license file |
| technical data | secrets, passwords, keys and vendor tokens, hosts, IP addresses, logins, MAC addresses |
| spreadsheet columns | a “Nazwisko” or “PESEL” header sets the type for the whole column |

Replacements are consistent within a conversation: “Jan Kowalski” gets the same replacement in a spreadsheet and
in the chat of the same tab. In another tab the same person gets a different one, so the AI provider cannot link
conversations. Two modes: **fictional data** (default - the text reads like ordinary prose) or
**labels** `[PERSON_1]`, `[PESEL_1]` for code and configs.

## Files

| format | what the chat receives |
|---|---|
| XLSX | Excel sheets: cell values (formula results instead of formulas), no formatting |
| DOCX | paragraphs, tables, headers and footers: text only, no formatting |
| CSV | separator: semicolon, comma or tab |
| TXT | txt, md, log |
| configs and logs | env, yaml, json, toml, ini, conf, properties, tf, sh, ps1, xml, sql, pem, key, Dockerfile, kubeconfig |
| PDF, images | blocked in the chat by default - so nothing slips past; from the program menu: see below |

With the preview enabled you see the detected values with counts before sending - unchecked values stay in the
file unchanged.

**From the program menu** (Pro and Business; macOS: the menu bar, Windows: the tray app): txt, csv, xlsx and docx as in the chat, plus
a **PDF with a text layer** (the result is a docx or txt, without page layout, images, hyperlinks and signatures; scans without text
are rejected) and **jpg and png images** (we remove only the metadata: location, device, author; the content of the image, such as text
in a photo, is not masked). Detection is rule-based, so check the result before sending it to the AI.

## Privacy and security

- **It works locally.** It does not send data to the vendor, collect statistics or track user activity. No telemetry, no user accounts, no online license checks.
  Detection and replacement happen on your device.
- **The only network traffic** is the optional “check for updates”: after you click it, the extension fetches one
  static file, with no parameters, no version number and no identifiers - the comparison happens locally.
  No timers, no background requests.
- **The replacement map** lives in the program's memory, separately for each chat tab, and is deleted when the
  tab is closed. The browser does not store it, so neither the chat site nor another extension can read it. In
  case the connection drops, the program keeps an encrypted copy of an open tab's map (XChaCha20-Poly1305, key in
  Keychain on macOS or Credential Manager on Windows), without passwords or API keys; the copy is deleted with the
  tab, when the browser restarts and after 24 hours at the latest. Incognito tabs never reach the disk.
- **The program keeps no working copies of chat files** - it processes them in memory. A file from the program menu is created next to the
  original, and its map of originals is encrypted with a system key (Keychain, Credential Manager) and disappears after 30 days. The
  clipboard map lives only in the program's memory and disappears after "New session", after 24 hours of inactivity and when the
  program closes.
- **Audit log**: the program keeps a local log of technical events on your computer (numbers and codes, with no messages, detected
  values, names of people and companies, custom phrases or file names), protected against unnoticed changes, kept for 180 days and
  never sent anywhere. It works with every license.
- **The license** is a signed file verified locally by the program; nothing is sent anywhere.
- The extension only has permissions for local storage, talking to the program, and the chat sites it runs on.

## How to install

Short version (full steps: [INSTALL.en.md](INSTALL.en.md)):

1. **Program**: on macOS open `donotfeedai-macos.pkg` and follow the installer (it asks for an administrator
   password because it installs into `/Applications`). On Windows run `donotfeedai-windows-setup.exe` (no
   administrator rights; about signing and SmartScreen see [INSTALL.en.md](INSTALL.en.md#windows)).
2. **Extension**: Firefox (Windows and macOS) - open [donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi) in it and click **Add**.
   Chrome and Edge on Windows - the extension comes with the installer, a page with instructions opens at the end.
   Chrome on macOS - unzip `donotfeedai-wtyczka-chrome.zip`, go to `chrome://extensions`, enable developer
   mode and point it at the unpacked folder. Edge on macOS is not supported.
3. **Quit and restart the browser.** The extension panel should show the program as connected.
4. **License**: on macOS in the Do Not Feed AI icon in the menu bar, next to the clock (**Load license…**), on Windows
   in the extension panel, License section - load the `.lic` file. Without a license protection is off
   (red bar in the chat); we send a trial license on request.

| system | extension | program |
|---|---|---|
| macOS | Chrome: load unpacked (Edge on macOS is not supported); Firefox: signed `.xpi` | `donotfeedai-macos.pkg` |
| Windows | in the installer (Chrome, Edge: load unpacked); Firefox: signed `.xpi` | `donotfeedai-windows-setup.exe` (code-signed) or, for IT departments, `donotfeedai-windows.msi` |

## Tiers

| | Trial | Pro | Business |
|---|---|---|---|
| who | on request, no commitment | per workstation, working with client data | per company, deployed without clicking |
| text, files, technical data, reply restoration | yes | yes | yes |
| clipboard shortcuts and files from the program menu (PDF and images too) | yes | yes | yes |
| audit log (local, no content, 180 days) | yes | yes | yes |
| custom phrases, manual restore mode | yes | yes | yes |
| validity | set when we send it | per agreement | per agreement |
| license | one file per workstation | one file per workstation | one file per company, via MDM or policy |
| shared company dictionary (clients, projects, products) | - | - | yes |

The license is verified locally by the program and needs no network connection. Without a license protection is
off: the extension does not change messages or files, and a red bar in the chat says so.

## Verifying your download

Checksums ship with every release (`SHA256SUMS.txt`) and are also printed in the release notes.
In the folder with the downloaded files:

```
shasum -a 256 -c SHA256SUMS.txt        # macOS
Get-FileHash .\donotfeedai-windows-setup.exe     # Windows (PowerShell), one file at a time
```

The macOS installer is signed with a Developer ID certificate and notarized by Apple; you can check it yourself:

```
pkgutil --check-signature donotfeedai-macos.pkg
spctl -a -vv --type install donotfeedai-macos.pkg
```

The Windows installer and the programs inside it are signed with a certificate issued by Microsoft (Artifact Signing)
for *Sebastian Obara It&Consulting*, with a timestamp. In PowerShell:

```
Get-AuthenticodeSignature .\donotfeedai-windows-setup.exe | Format-List Status, SignerCertificate
```

## Updating

- **Program**: download the new installer from the latest release and install it - it overwrites the previous
  version. The license stays in place. Update the program and the extension together: the extension does not
  work with an older program and says so.
- **Extension** (loaded unpacked): copy the contents of the new folder over the old one (overwriting files), or
  point "Load unpacked" at the new folder, then click the reload icon in `chrome://extensions` and refresh your
  chat tabs. Settings and license survive, because the extension ID is fixed.
  Details: [INSTALL.en.md](INSTALL.en.md#updating).
- The version is shown in the extension panel: the line with the extension and program versions. If the two
  drift apart, the extension says so.

## Frequently asked questions

**Do I have to install the program?**
Yes. Detection, replacements, reply restoration and the license live in the program; the extension only hands it
text and files. Without the program the extension does not mask anything. The part of the program that works with the browser has
no window and runs while the browser is open; the clipboard shortcuts and files from the menu are handled by a separate app (macOS:
the menu bar icon; Windows: the tray icon, started from the Start menu shortcut, with no autostart until you turn it on yourself).

**Does it work in a code editor or a terminal?**
The extension does not, but the program does, through the clipboard shortcuts (Pro and Business, off by default, see "How it works"):
you copy text, the shortcut turns the clipboard into text with replacements, you paste it into the AI, and you restore the reply with
the second shortcut. We do not support editor assistants or API calls.

**What about data the extension does not detect?**
Project, client and product names can be added as custom phrases. The preview before sending lists the detected
values with checkboxes, and the manual restore mode shows exactly what the AI received and replied. Known
limitation: a person mentioned for the first time only in an inflected form (“a letter to Nowak”) is not detected.

**Does it slow down typing or sending?**
The program is rules and checksums, with no language models and no cloud: it checks a few thousand characters in
a few milliseconds, so the “N detected” counter updates as you type. The substitution in the field happens the moment you send.

**What happens when the license expires?**
After the expiry date you still get 14 days of full access (a transition period, with a warning in the panel and
in the bar). Then protection is off: the extension does not change messages or files, and a red bar in the chat
says so. A trial license ends the same way.

## Note on language

The product is made for the Polish market first: the website, the privacy policy, the license terms (OWU) and
the extension UI are Polish (the UI also has English). These English pages cover downloads and installation;
for anything legally binding, the Polish documents are the ones that apply.
