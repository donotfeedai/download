# Do Not Feed AI — downloads

[Polski](README.md) · **English**

<img src="assets/social-preview.png" alt="Do Not Feed AI: client data stays on your computer. The extension replaces names, national IDs, bank accounts, phones and addresses with fictional data before your text or file reaches ChatGPT, Claude or Gemini.">

Do Not Feed AI replaces names, national IDs, phone numbers, addresses and files with realistic fictional data
**before they leave your browser**. The model's reply comes back with the real values restored. Everything
happens on your machine, with no connection to a vendor server — there is no such server.

This repository is **distribution only**: the companion installer and the browser extension. The source code is
not published here. The software is proprietary, all rights reserved; the terms of use are set out in the licence
agreement (OWU) supplied together with the licence.

**zero network calls** · **Polish identifiers: PESEL, NIP, REGON, IBAN** · **xlsx, docx, csv, txt**

<p><b>Works in:</b>
<img src="assets/browsers/chrome.svg" width="20" alt="Chrome"> Chrome &nbsp;
<img src="assets/browsers/edge.svg" width="20" alt="Edge"> Edge &nbsp;
<img src="assets/browsers/brave.svg" width="20" alt="Brave"> Brave &nbsp;
<img src="assets/browsers/chromium.svg" width="20" alt="Chromium"> Chromium and derivatives &nbsp;
<img src="assets/browsers/firefox.svg" width="20" alt="Firefox"> Firefox <code>in preparation</code></p>

<p><b>Masks in:</b>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/chatgpt-dark.svg"><img src="assets/chats/chatgpt.svg" width="20" alt="ChatGPT"></picture> ChatGPT &nbsp;
<img src="assets/chats/claude.svg" width="20" alt="Claude"> Claude &nbsp;
<img src="assets/chats/gemini.svg" width="20" alt="Gemini"> Gemini &nbsp;
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/copilot-dark.svg"><img src="assets/chats/copilot.svg" width="20" alt="Copilot"></picture> Copilot</p>

<p><b>Systems:</b>
<img src="assets/os/apple.svg" width="20" alt="macOS"> macOS (with the companion) &nbsp;
<img src="assets/os/windows.svg" width="20" alt="Windows"> Windows (with the companion) &nbsp;
<img src="assets/os/tux.svg" width="20" alt="Linux"> Linux <code>companion from source</code></p>

Website: [donotfeedai.com](https://donotfeedai.com) · Privacy policy: [donotfeedai.com/polityka-prywatnosci.html](https://donotfeedai.com/polityka-prywatnosci.html) (Polish)

## What to download

The `latest/download/...` links always point to the newest version, so they never need updating.
All releases (with version numbers and changelogs):
[github.com/donotfeedai/download/releases](https://github.com/donotfeedai/download/releases).

| file | for |
|---|---|
| **[donotfeedai-macos.pkg](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-macos.pkg)** | **macOS** — companion: signed and notarized installer, Gatekeeper will not complain |
| **[donotfeedai-windows-setup.exe](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-windows-setup.exe)** | **Windows 10/11** - companion: per-user installer, no administrator rights. Code-signed (certificate issued by Microsoft), publisher: Sebastian Obara It&Consulting |
| **[donotfeedai-wtyczka-chrome.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-chrome.zip)** | **Chrome, Edge, Brave, Chromium** — extension, loaded unpacked |
| **[donotfeedai-wtyczka-firefox.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-firefox.zip)** | **Firefox** — the same extension, different manifest |
| **[SHA256SUMS.txt](https://github.com/donotfeedai/download/releases/latest/download/SHA256SUMS.txt)** | checksums for the downloaded files |

The extension works on chat text right away. **The companion is only needed for files** (xlsx, docx, csv, txt,
configs, logs) and for the encrypted on-disk session.

## How it works

<img src="assets/how-it-works.svg" width="928" alt="Flow: text and files are masked locally, the AI service receives replacements, and the reply is restored on your machine. Originals never cross the boundary of your computer.">

*Original values never cross the boundary of your computer. The replacement map is encrypted with a key from the system keychain and expires after the time you set.*

- **Chat text**: you type as usual and the extension takes over the send — it substitutes values in the box,
  sends the replacements, and restores the originals in the model's reply. What you see on screen is always real.
- **Files**: you add an xlsx, docx, csv or txt as usual. The extension stops the upload, the companion masks the
  file on your machine, and the chat receives `plik_anon.xlsx`. Formulas, styles and formatting stay untouched.
- **Secrets and configs** (Pro): passwords, tokens and keys are masked by the companion, in `.env` files,
  `docker-compose.yml` and logs too.

## What it detects

| data | how |
|---|---|
| full name | including inflected forms (“dla Magdaleny”, “do Kowalskiego”); the replacement comes back in the same grammatical case |
| PESEL (national ID) | checksum or a plausible date of birth |
| NIP, REGON, IBAN, ID card number | checksum validation, so an order number is not mistaken for a NIP |
| phone and e-mail | e-mail in a person's pattern: `s.obara@` → `s.zalewski@`; 9-digit numbers, with `+48`, dashes and spaces |
| address, postal code and city | “ul. Długa 7” next to other personal data |
| company | Sp. z o.o., S.A., Sp. j., Ltd., GmbH |
| custom phrases | project, client and product names (Pro) |
| technical data (Pro) | secrets, passwords, keys and vendor tokens, hosts, IP addresses, logins, MAC addresses — computed in the companion only |
| spreadsheet columns | a “Nazwisko” or “PESEL” header sets the type for the whole column |

Replacements are deterministic: “Jan Kowalski” gets the same replacement in a spreadsheet and in the chat,
for the whole session. Two modes: **fictional data** (default — the text reads like ordinary prose) or
**labels** `[PERSON_1]`, `[PESEL_1]` for code and configs.

## Files

| format | what is preserved |
|---|---|
| XLSX | Excel sheets, formulas |
| DOCX | paragraphs, tables, headers and footers |
| CSV | separator: semicolon, comma or tab |
| TXT | txt, md, log |
| configs and logs | env, yaml, json, toml, ini, conf, properties, tf, sh, ps1, xml, sql, pem, key, Dockerfile, kubeconfig |
| file from the AI reply | restore with one command: `dnf restore plik_anon.xlsx --vault browser` |
| PDF, images | blocked by default — so nothing slips past |

With the preview enabled you see the detected values with counts before sending — unchecked values stay in the
file unchanged.

## Privacy and security

- **There is no vendor server.** No telemetry, no usage statistics, no user accounts, no online licence checks.
  Detection and replacement happen on your device.
- **The only network traffic** is the optional “check for updates”: after you click it, the extension fetches one
  static file, with no parameters, no version number and no identifiers — the comparison happens locally.
  No timers, no background requests.
- **The replacement map (session)** lives in browser memory or — if you choose so and have the companion —
  on disk, encrypted (AES-256-GCM), with the key held by the system keychain (Keychain on macOS, Credential
  Manager on Windows). It expires 1, 7 or 30 days after it starts (your choice), even if you do not use the extension, and you can delete it anytime.
- **Secrets in tab memory only** (on by default): passwords and keys never reach the saved session.
- **The companion keeps no working copies of files** — it processes them in memory.
- **The licence** is a signed file verified locally; nothing is sent anywhere.
- The extension only has permissions for local storage, talking to the companion, and the chat sites it runs on.

## How to install

Short version (full steps: [INSTALL.en.md](INSTALL.en.md)):

1. **Companion**: on macOS open `donotfeedai-macos.pkg` and follow the installer (it asks for an administrator
   password because it installs into `/Applications`). On Windows run `donotfeedai-windows-setup.exe` (no
   administrator rights; about signing and SmartScreen see [INSTALL.en.md](INSTALL.en.md#windows)).
2. **Extension**: unzip `donotfeedai-wtyczka-chrome.zip` (or `-firefox.zip`), go to `chrome://extensions`
   (Firefox: `about:debugging#/runtime/this-firefox`), enable developer mode and point it at the unpacked folder.
3. **Quit and restart the browser.** The extension panel should show the companion as connected.

| system | extension | companion |
|---|---|---|
| macOS | Chrome/Edge/Brave/Firefox + load unpacked | `donotfeedai-macos.pkg` |
| Windows | Chrome/Edge/Brave/Firefox + load unpacked | `donotfeedai-windows-setup.exe` (code-signed) |
| Linux | Chromium/Firefox + load unpacked | build from source (`cargo build --release`); distribution to be considered |

Without a licence file you get **7 days of full Pro** from the first launch; after that the extension drops to
Free (chat text keeps working without limits, files are held back).

## Tiers

| | Free | Pro | Business |
|---|---|---|---|
| who | one person, chat text | per workstation, working with client data | per company, deployed without clicking |
| text and reply restoration | yes | yes | yes |
| files and configs | — | yes | yes |
| technical data, custom phrases, manual restore mode | — | yes | yes |
| encrypted on-disk session | — | yes | yes |
| licence | no file needed | one file per workstation | one file per company, via MDM or policy |
| shared company dictionary (clients, projects, products) | — | — | yes |

The licence is verified locally and needs no network connection: a single signed file per workstation.

## Verifying your download

Checksums ship with every release (`SHA256SUMS.txt`) and are also printed in the release notes.
In the folder with the downloaded files:

```
shasum -a 256 -c SHA256SUMS.txt        # macOS, Linux
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

- **Companion**: download the new `.pkg` from the latest release and install it — it overwrites the previous
  version. Licence and sessions stay in place.
- **Extension** (loaded unpacked): copy the contents of the new folder over the old one (overwriting files), or
  point "Load unpacked" at the new folder, then click the reload icon in `chrome://extensions` and refresh your
  chat tabs. Settings, licence and the encrypted session survive, because the extension ID is fixed.
  Details: [INSTALL.en.md](INSTALL.en.md#updating).
- The version is shown in the extension panel: the `extension X · companion Y` line. If the two drift apart,
  the extension says so.

## Frequently asked questions

**Do I have to install the companion?**
No — for chat text the extension alone is enough. The companion is needed for files and for the encrypted
on-disk session. Without it the replacement map lives only in memory until the browser closes, and files are
held back.

**What about data the extension does not detect?**
Project, client and product names can be added as custom phrases. The preview before sending lists the detected
values with checkboxes, and the manual restore mode shows exactly what the AI received and replied. Known
limitation: a person mentioned for the first time only in an inflected form (“a letter to Nowak”) is not detected.

**Does it slow down typing or sending?**
The engine is rules and checksums, with no language models and no cloud, so the “N detected” counter updates as
you type. The substitution in the field happens the moment you send.

**What happens when the licence expires?**
After the expiry date you still get 14 days of full access (a transition period, with a warning in the panel),
then the extension drops to Free. The session is not deleted, it just stops being written to disk. Chat text
keeps working without limits.

## Note on language

The product is made for the Polish market first: the website, the privacy policy, the licence terms (OWU) and
the extension UI are Polish (the UI also has English). These English pages cover downloads and installation;
for anything legally binding, the Polish documents are the ones that apply.
