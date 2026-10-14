# Instalacja Do Not Feed AI

**Polski** · [English](INSTALL.en.md)

Trzy kroki: program (companion), wtyczka, sprawdzenie połączenia. Na Windows jeden instalator kładzie program
i wtyczkę naraz. Do samego maskowania tekstu w czacie (poziom Free) wystarczy wtyczka; companion jest potrzebny
do funkcji Pro: pełnego słownika imion i nazwisk, danych technicznych, plików i szyfrowanej sesji na dysku.
Wszystko dzieje się na Twoim komputerze - wtyczka i companion nie łączą się z żadnym serwerem producenta.

## macOS

1. **Pobierz i zainstaluj companion**: `donotfeedai-macos.pkg` →
   dwuklik → instalator poprosi o hasło administratora (instaluje w `/Applications`).
   Instalator sam rejestruje program w przeglądarkach.
   Instalator jest podpisany certyfikatem Developer ID i notaryzowany przez Apple, więc Gatekeeper nie
   powinien się przyczepić. Jeśli się przyczepi, sprawdź podpis: `pkgutil --check-signature donotfeedai-macos.pkg`.

2. **Wtyczka**: rozpakuj `donotfeedai-wtyczka-chrome.zip` (Firefox: `-firefox.zip`) w stałym miejscu
   (np. `~/Documents`), potem:
   - Chrome / Edge / Brave / Chromium: `chrome://extensions` → **Tryb dewelopera** → **Załaduj rozpakowane** →
     wskaż folder `donotfeedai-wtyczka-chrome-<wersja>` (ten z `manifest.json` w środku),
   - Firefox: `about:debugging#/runtime/this-firefox` → **Załaduj tymczasowy dodatek** → wskaż `manifest.json`
     z rozpakowanego folderu. Ładowanie tymczasowe znika po restarcie Firefoksa; wersja stała będzie w AMO.

   **Nie przenoś tego folderu** po załadowaniu - wtyczka ładuje się z niego przy każdym starcie przeglądarki.

3. **Zamknij przeglądarkę całkowicie** (Cmd+Q - samo zamknięcie okna nie wystarczy) i uruchom ponownie.
   Rejestrację companiona przeglądarka czyta przy starcie.

4. **Sprawdź**: kliknij ikonę wtyczki (otworzy się panel boczny). Ma być `Companion: połączony` oraz linia
   `wtyczka X · companion Y`. Chrome pokaże na starcie pasek „wyłącz rozszerzenia w trybie dewelopera” -
   zignoruj go; w wersji ze sklepu tego paska nie ma.

## Windows

Windows 10 i 11 (x64), także Windows 11 na ARM.

1. **Pobierz i uruchom instalator**: `donotfeedai-windows-setup.exe` → dwuklik. Instalator nie potrzebuje
   uprawnień administratora: instaluje program i wtyczkę na Twoim koncie (`%LOCALAPPDATA%\Programs\donotfeedai`)
   i sam rejestruje program w Chrome, Edge, Brave, Chromium i Firefoksie. Na koniec proponuje otwarcie strony
   z ostatnim krokiem: https://donotfeedai.com/start
   Instalator i programy są **podpisane cyfrowo** certyfikatem wydanym przez Microsoft (Artifact Signing):
   wydawca to *Sebastian Obara It&Consulting* (prawy klik na pliku → **Właściwości → Podpisy cyfrowe**, albo w
   PowerShell `Get-AuthenticodeSignature .\donotfeedai-windows-setup.exe`). Wydawca jest nowy, więc przez pierwsze
   tygodnie SmartScreen może jeszcze pokazać „System Windows ochronił ten komputer" - w tym oknie widać już wydawcę;
   kliknij **Więcej informacji → Uruchom mimo to**.

2. **Pokaż wtyczkę przeglądarce** (raz): instalator położył ją w
   `%LOCALAPPDATA%\Programs\donotfeedai\wtyczka-chrome` - nic nie pobierasz ani nie wypakowujesz.
   W `edge://extensions` (Chrome: `chrome://extensions`) włącz **Tryb dewelopera** (w Edge przełącznik na dole
   lewego panelu), kliknij **Załaduj rozpakowane**, w okienku wyboru folderu wklej powyższą ścieżkę w pasek adresu,
   naciśnij Enter i kliknij **Wybierz folder**. Firefox: **Załaduj tymczasowy dodatek** w
   `about:debugging#/runtime/this-firefox` i plik `...\wtyczka-firefox\manifest.json`.
   Restart przeglądarki nie jest potrzebny.

3. **Sprawdź**: kliknij ikonę puzzla, przypnij Do Not Feed AI i kliknij ikonę - panel ma pokazać
   `Companion: połączony`. Kolejne wersje instalatora aktualizują też wtyczkę w tym samym folderze
   (przeglądarka wczyta nową wersję przy następnym uruchomieniu).

**Wdrożenie przez dział IT** (bez okien dialogowych):

```
donotfeedai-windows-setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

Instalacja jest per użytkownik, więc polecenie uruchamia się w kontekście użytkownika (w Intune: *Install
behavior: User*). Log instalacji trafia do `%TEMP%\Setup Log *.txt`.

## Czego potrzebuje companion, a czego nie

| funkcja | bez companiona | z companionem |
|---|---|---|
| maskowanie tekstu w czacie | tak | tak |
| przywracanie odpowiedzi AI | tak | tak |
| pliki xlsx / docx / csv / txt / konfiguracje / logi | nie (plik zatrzymany) | tak |
| dane techniczne: sekrety, hosty, IP, loginy | nie | tak |
| sesja szyfrowana na dysku | nie (tylko pamięć karty) | tak |

## Aktualizacja

**Companion**: pobierz nowy instalator z najnowszego wydania (`donotfeedai-macos.pkg` albo
`donotfeedai-windows-setup.exe`) i zainstaluj - nadpisuje poprzednią wersję (licencja i sesje zostają
w katalogu danych użytkownika).

**Wtyczka** (załadowana jako rozpakowana) nie aktualizuje się sama. Nowa wersja to podmiana plików:

1. Rozpakuj nowy `donotfeedai-wtyczka-chrome-<nowa wersja>.zip`.
2. Jedno z dwóch:
   - skopiuj **zawartość** nowego folderu do starego (tego wskazanego w `chrome://extensions`, nadpisując pliki),
     a potem kliknij ikonę odświeżenia na karcie wtyczki, albo
   - wskaż nowy folder w **Załaduj rozpakowane** - identyfikator wtyczki jest stały, więc Chrome podmieni wersję,
     nie tworząc drugiej kopii.
3. Odśwież karty czatu (Cmd+R / F5). Karta otwarta przed aktualizacją działa jeszcze na starej kopii wtyczki.
4. Sprawdź linię `wtyczka X · companion Y` - obie wersje powinny być równe.

Czego **nie** trzeba robić: nie usuwaj wtyczki (kosz w `chrome://extensions`) - przy podmianie plików nic nie
tracisz, a usuwanie to zbędne ryzyko dla ustawień, licencji i sesji. Ustawienia, licencja i sesja zaszyfrowana
na dysku przechodzą aktualizację bez zmian; ginie tylko sesja w trybie „tylko w pamięci”, bo trzyma się
w pamięci przeglądarki.

## Odinstalowanie

**macOS**:

```
sudo /Applications/donotfeedai/uninstall.sh            # binarki + rejestracja w przeglądarkach
sudo /Applications/donotfeedai/uninstall.sh --purge    # dodatkowo licencja i sesje (pyta o zgodę)
```

**Windows**: **Ustawienia → Aplikacje → Zainstalowane aplikacje** → *Do Not Feed AI companion* → **Odinstaluj**
(usuwa program i rejestrację w przeglądarkach). Licencja i sesje zostają; żeby usunąć i je, skasuj folder
`%LOCALAPPDATA%\donotfeedai`, a w **Menedżerze poświadczeń → Poświadczenia systemu Windows** wpisy z „donotfeedai".

Wtyczkę usuwa się osobno w `chrome://extensions` (Firefox: `about:debugging`).

## Licencja i poziomy

Bez pliku licencji masz **7 dni pełnego Pro** od pierwszego uruchomienia, potem wtyczka przechodzi na Free.
Plik licencji (`.lic`) wczytuje się w popupie wtyczki („Wczytaj plik licencji”). Licencja jest sprawdzana
lokalnie podpisem cyfrowym - nie ma serwera licencji i nie ma połączeń sieciowych.
