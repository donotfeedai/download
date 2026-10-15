# Instalacja Do Not Feed AI

**Polski** · [English](INSTALL.en.md)

Kroki: program, wtyczka, sprawdzenie połączenia, licencja. Na Windows jeden instalator kładzie program i wtyczkę
naraz. Potrzebne są oba: program wykrywa i podmienia dane, wtyczka przekazuje mu to, co wysyłasz do czatu - bez
programu wtyczka nie maskuje danych. Wszystko dzieje się na Twoim komputerze - wtyczka i program nie łączą się
z żadnym serwerem producenta.

## macOS

1. **Pobierz i zainstaluj program**: `donotfeedai-macos.pkg` →
   dwuklik → instalator poprosi o hasło administratora (instaluje w `/Applications`).
   Instalator sam rejestruje program w przeglądarkach.
   Instalator jest podpisany certyfikatem Developer ID i notaryzowany przez Apple, więc Gatekeeper nie
   powinien się przyczepić. Jeśli się przyczepi, sprawdź podpis: `pkgutil --check-signature donotfeedai-macos.pkg`.

2. **Wtyczka**:
   - Firefox: otwórz w Firefoksie [donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi), kliknij
     **Kontynuuj instalację** i **Dodaj**. Wtyczka jest podpisana przez Mozillę i zostaje na stałe, bez trybu
     dewelopera. Ten sam plik jest w wydaniu jako `donotfeedai-wtyczka-firefox.xpi`.
   - Chrome / Edge / Brave / Chromium: rozpakuj `donotfeedai-wtyczka-chrome.zip` w stałym miejscu
     (np. `~/Documents`), potem `chrome://extensions` → **Tryb dewelopera** → **Załaduj rozpakowane** →
     wskaż folder `donotfeedai-wtyczka-chrome-<wersja>` (ten z `manifest.json` w środku).

   **Nie przenoś tego folderu** po załadowaniu - wtyczka ładuje się z niego przy każdym starcie przeglądarki.

3. **Zamknij przeglądarkę całkowicie** (Cmd+Q - samo zamknięcie okna nie wystarczy) i uruchom ponownie.
   Rejestrację programu przeglądarka czyta przy starcie.

4. **Sprawdź**: kliknij ikonę wtyczki (otworzy się panel boczny). Ma być `Program: połączony` oraz linia
   z wersją wtyczki i programu. Chrome pokaże na starcie pasek „wyłącz rozszerzenia w trybie dewelopera” -
   zignoruj go; w wersji ze sklepu tego paska nie ma.

5. **Wczytaj licencję** (patrz [Licencja](#licencja)).

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
   naciśnij Enter i kliknij **Wybierz folder**. Firefox: otwórz
   [donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi) i kliknij **Kontynuuj instalację** → **Dodaj**
   (wtyczka podpisana przez Mozillę, zostaje na stałe).
   Restart przeglądarki nie jest potrzebny.

3. **Sprawdź**: kliknij ikonę puzzla, przypnij Do Not Feed AI i kliknij ikonę - panel ma pokazać
   `Program: połączony`. Kolejne wersje instalatora aktualizują też wtyczkę w tym samym folderze
   (przeglądarka wczyta nową wersję przy następnym uruchomieniu).

4. **Wczytaj licencję** (patrz [Licencja](#licencja)).

**Wdrożenie przez dział IT** (bez okien dialogowych):

```
donotfeedai-windows-setup.exe /VERYSILENT /SUPPRESSMSGBOXES /NORESTART
```

Instalacja jest per użytkownik, więc polecenie uruchamia się w kontekście użytkownika (w Intune: *Install
behavior: User*). Log instalacji trafia do `%TEMP%\Setup Log *.txt`. Domyślny folder to
`%LOCALAPPDATA%\Programs\donotfeedai`; inny można podać parametrem `/DIR="D:\Programy\donotfeedai"` (instalator nie
pyta o folder w oknie, a instrukcja dla użytkowników zakłada folder domyślny).

## Gdy programu nie ma albo nie odpowiada

Wtyczka nie ma własnego silnika, więc bez programu nie maskuje danych i mówi to wprost:

| sytuacja | pasek w czacie | wysłanie wiadomości | pliki |
|---|---|---|---|
| programu nie ma | „Zainstaluj program Do Not Feed AI” | po pytaniu „Wyślij bez maskowania” | zatrzymane |
| program nie odpowiada | „Ochrona niedostępna” | po pytaniu „Wyślij bez maskowania” | zatrzymane |
| program starszy niż wtyczka | „Program za stary” | po pytaniu „Wyślij bez maskowania” | zatrzymane |
| brak licencji | „Ochrona wyłączona: brak licencji” (czerwony) | bez zmian, bez maskowania | bez zmian |

Program nie odpowiada: zamknij przeglądarkę całkowicie i uruchom ponownie; jeśli to nie pomoże, zainstaluj
program jeszcze raz.

## Aktualizacja

**Program**: pobierz nowy instalator z najnowszego wydania (`donotfeedai-macos.pkg` albo
`donotfeedai-windows-setup.exe`) i zainstaluj - nadpisuje poprzednią wersję (licencja zostaje w katalogu danych
użytkownika). Program i wtyczkę aktualizuj razem: wtyczka nie współpracuje ze starszym programem.

**Wtyczka** (załadowana jako rozpakowana) nie aktualizuje się sama. Nowa wersja to podmiana plików:

1. Rozpakuj nowy `donotfeedai-wtyczka-chrome-<nowa wersja>.zip`.
2. Jedno z dwóch:
   - skopiuj **zawartość** nowego folderu do starego (tego wskazanego w `chrome://extensions`, nadpisując pliki),
     a potem kliknij ikonę odświeżenia na karcie wtyczki, albo
   - wskaż nowy folder w **Załaduj rozpakowane** - identyfikator wtyczki jest stały, więc Chrome podmieni wersję,
     nie tworząc drugiej kopii.
3. Odśwież karty czatu (Cmd+R / F5). Karta otwarta przed aktualizacją działa jeszcze na starej kopii wtyczki.
4. Sprawdź w panelu linię z wersją wtyczki i programu - obie wersje powinny być równe.

Czego **nie** trzeba robić: nie usuwaj wtyczki (kosz w `chrome://extensions`) - przy podmianie plików nic nie
tracisz, a usuwanie to zbędne ryzyko dla ustawień. Ustawienia i licencja przechodzą aktualizację bez zmian.
Mapy zamienników otwartych kart program wczytuje po ponownym połączeniu; po restarcie przeglądarki zaczynają się
od nowa.

## Odinstalowanie

**macOS**:

```
sudo /Applications/donotfeedai/uninstall.sh            # binarki, ikona w pasku menu + rejestracja w przeglądarkach
sudo /Applications/donotfeedai/uninstall.sh --purge    # dodatkowo licencja i kopie map kart (pyta o zgodę)
```

**Windows**: **Ustawienia → Aplikacje → Zainstalowane aplikacje** → *Do Not Feed AI companion* → **Odinstaluj**
(usuwa program i rejestrację w przeglądarkach). Licencja zostaje; żeby usunąć i ją, skasuj folder
`%LOCALAPPDATA%\donotfeedai`, a w **Menedżerze poświadczeń → Poświadczenia systemu Windows** wpisy z „donotfeedai".

Wtyczkę usuwa się osobno w `chrome://extensions` (Firefox: `about:addons` → Do Not Feed AI → **Usuń**).

## Licencja

Program działa z licencją Pro albo Business. Okres próbny to licencja z krótką datą ważności - wyślemy ją na
prośbę: [kontakt@donotfeedai.pl](mailto:kontakt@donotfeedai.pl). Bez licencji ochrona jest wyłączona.
Plik licencji (`.lic`) wczytuje się na macOS w ikonie Do Not Feed AI w pasku menu, obok zegara („Wczytaj licencję…”
albo „Wklej licencję ze schowka”), a na Windows w panelu wtyczki („Wczytaj plik licencji”). Zawsze działa też
`dnf license install plik.lic`; w firmie plik może położyć w katalogu danych MDM. Licencja jest sprawdzana
lokalnie przez program podpisem cyfrowym - nie ma serwera licencji i nie ma połączeń sieciowych.
