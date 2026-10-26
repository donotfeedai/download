# Do Not Feed AI - pobieranie

**Polski** · [English](README.en.md)

<img src="assets/social-preview.png" alt="Do Not Feed AI: dane klientów zostają na Twoim komputerze. Wtyczka wykrywa imiona, PESEL, NIP, IBAN, telefony i adresy i podmienia je na dane fikcyjne, zanim tekst albo plik trafi do ChatGPT, Claude, Gemini lub Copilota.">

Do Not Feed AI wykrywa imiona, PESEL-e, numery telefonów, adresy i dane w plikach, a potem podmienia je na
realistyczne dane fikcyjne, **zanim wiadomość opuści Twój komputer**. Odpowiedź modelu wraca już z prawdziwymi wartościami. Wszystko robi program
na Twoim komputerze. Do Not Feed AI działa lokalnie: nie przesyła danych do producenta, nie zbiera statystyk ani nie śledzi aktywności użytkowników i nie wymaga konta ani połączenia z serwerem w celu weryfikacji licencji.

Do Not Feed AI to **program na komputer** (Windows, macOS) i **wtyczka do przeglądarki**, potrzebne razem:
program wykrywa i podmienia dane, wtyczka przekazuje mu to, co wysyłasz do czatu. Działa z licencją; licencję próbną
wysyłamy na prośbę ([kontakt@donotfeedai.pl](mailto:kontakt@donotfeedai.pl)).

To repozytorium służy **tylko do dystrybucji**: instalator programu i wtyczka do przeglądarki.
Kod źródłowy nie jest tu publikowany. Oprogramowanie jest własnościowe, wszelkie prawa zastrzeżone;
warunki korzystania określa umowa licencyjna (OWU) przekazywana razem z licencją.

**zero połączeń sieciowych** · **polskie identyfikatory: PESEL, NIP, REGON, IBAN** · **xlsx, docx, csv, txt**

<p><b>Działa w:</b>
<img src="assets/browsers/chrome.svg" width="20" alt="Chrome"> Chrome &nbsp;
<img src="assets/browsers/edge.svg" width="20" alt="Edge"> Edge (Windows) &nbsp;
<img src="assets/browsers/firefox.svg" width="20" alt="Firefox"> Firefox<br>
Windows: Chrome, Edge, Firefox · macOS: Chrome, Firefox</p>

<p><b>Maskuje w:</b>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/chatgpt-dark.svg"><img src="assets/chats/chatgpt.svg" width="20" alt="ChatGPT"></picture> ChatGPT &nbsp;
<img src="assets/chats/claude.svg" width="20" alt="Claude"> Claude &nbsp;
<img src="assets/chats/gemini.svg" width="20" alt="Gemini"> Gemini &nbsp;
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/chats/copilot-dark.svg"><img src="assets/chats/copilot.svg" width="20" alt="Copilot"></picture> Copilot</p>

<p><b>Systemy:</b>
<img src="assets/os/apple.svg" width="20" alt="macOS"> macOS &nbsp;
<img src="assets/os/windows.svg" width="20" alt="Windows"> Windows</p>

Strona: [donotfeedai.com](https://donotfeedai.com) · Polityka prywatności: [donotfeedai.com/polityka-prywatnosci.html](https://donotfeedai.com/polityka-prywatnosci.html)

## Co pobrać

Linki `latest/download/...` zawsze prowadzą do najnowszej wersji - nie trzeba ich zmieniać.
Wszystkie wydania (z numerami wersji i opisem zmian):
[github.com/donotfeedai/download/releases](https://github.com/donotfeedai/download/releases).

| plik | dla kogo |
|---|---|
| **[donotfeedai-macos.pkg](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-macos.pkg)** | **macOS** - program: instalator podpisany i notaryzowany, Gatekeeper nie będzie ostrzegał |
| **[donotfeedai-windows-setup.exe](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-windows-setup.exe)** | **Windows 10/11** - program i wtyczka: instalator na koncie użytkownika, bez uprawnień administratora. Podpisany cyfrowo (certyfikat wydany przez Microsoft), wydawca: Sebastian Obara It&Consulting |
| **[donotfeedai-windows.msi](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-windows.msi)** | **Windows 10/11, dla działów IT** - ten sam program i wtyczka co w instalatorze, do wdrożeń przez zasady grupy, Intune i SCCM (instalacja na komputer lub na użytkownika); szczegóły w [INSTALACJA.md](INSTALACJA.md#windows). Podpisany cyfrowo |
| **[donotfeedai-wtyczka-chrome.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-chrome.zip)** | **Chrome** (macOS) - wtyczka do załadowania jako rozpakowana; na Windows wtyczka do Chrome i Edge jest w instalatorze |
| **[donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi)** | **Firefox** - wtyczka podpisana przez Mozillę: otwórz link w Firefoksie i kliknij **Dodaj**, zostaje na stałe ([ten sam plik na GitHubie](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-firefox.xpi)) |
| [donotfeedai-wtyczka-firefox.zip](https://github.com/donotfeedai/download/releases/latest/download/donotfeedai-wtyczka-firefox.zip) | Firefox - ta sama wtyczka bez podpisu, do testów jako dodatek tymczasowy |
| **[SHA256SUMS.txt](https://github.com/donotfeedai/download/releases/latest/download/SHA256SUMS.txt)** | sumy kontrolne pobranych plików |

**Potrzebne są oba: program i wtyczka.** Bez programu wtyczka nie maskuje danych - mówi to na pasku w czacie
i przed każdym wysłaniem pyta, czy wysłać wiadomość bez maskowania.

## Jak to działa

<img src="assets/jak-to-dziala.svg" width="928" alt="Przepływ: tekst i pliki są maskowane lokalnie, do usługi AI trafiają zamienniki wykrytych danych, odpowiedź wraca i jest przywracana na komputerze. Mapa oryginałów zostaje na komputerze.">

*Do AI trafiają zamienniki wykrytych danych, a mapa oryginałów zostaje na Twoim komputerze: w programie, osobno dla każdej karty czatu, i znika z jej zamknięciem.*

- **Tekst w czacie**: piszesz normalnie, a wysyłkę przejmuje wtyczka - program wykrywa dane, wtyczka podmienia je w polu, wysyła zamienniki,
  a w odpowiedzi modelu przywraca oryginały. Z ekranu nie znikasz: dane, które widzisz, są prawdziwe.
- **Plik**: dodajesz xlsx, docx, csv albo txt jak zwykle. Wtyczka zatrzymuje wysyłkę, program maskuje dane w treści
  pliku na Twoim komputerze i do czatu trafia wersja `plik_anon.xlsx`. Z plików Excel i Word jest to uproszczona kopia
  z samymi wartościami i tekstem: wyniki formuł zamiast formuł, bez formatowania, wykresów, obrazów i makr.
  Oryginał zostaje u Ciebie bez zmian.
- **Sekrety i konfiguracje**: hasła, tokeny i klucze podmienia program, także w plikach `.env`,
  `docker-compose.yml` i logach.
- **Schowek (poza przeglądarką, Pro i Business)**: w edytorze, terminalu albo dowolnym programie kopiujesz tekst i naciskasz
  skrót **Anonimizuj** (Windows `Ctrl+Win+A`, macOS `Ctrl+Option+A`): w schowku zostaje tekst z zamiennikami, który wklejasz do AI.
  Odpowiedź kopiujesz i naciskasz **Przywróć** (`Ctrl+Win+R`, `Ctrl+Option+R`). Skróty są domyślnie wyłączone: włączasz je w menu
  ikony programu. To nie jest wtyczka w edytorze: program czyta schowek tylko po naciśnięciu skrótu (albo wybraniu polecenia w menu).
  Historia schowka systemu i menedżery schowka mogą zachować oryginał skopiowany przed użyciem skrótu.
- **Plik z menu programu (Pro i Business)**: „Zanonimizuj plik…” i „Przywróć plik…” w menu ikony programu (pasek menu na macOS,
  zasobnik na Windows). Obok oryginału powstaje plik z neutralną nazwą i końcówką `_anon`; mapa oryginałów leży zaszyfrowana na
  Twoim komputerze i po 30 dniach jest usuwana. PDF z warstwą tekstową zamieniamy na docx albo txt (bez układu strony i grafiki);
  z obrazów jpg i png usuwamy tylko metadane (treść obrazu nie jest maskowana).

## Co wykrywa

| dana | jak |
|---|---|
| imię i nazwisko | także w przypadkach zależnych: „dla Magdaleny”, „do Kowalskiego”; zamiennik wraca w tym samym przypadku; także zapisane WIELKIMI literami: „JAN KOWALSKI” |
| PESEL | suma kontrolna albo wiarygodna data urodzenia |
| NIP, REGON, IBAN, nr dowodu | z walidacją sum kontrolnych, więc numer zamówienia nie jest NIP-em |
| telefon i e-mail | e-mail we wzorcu osoby: `s.obara@` → `s.zalewski@`; numery 9-cyfrowe, z `+48`, myślnikami i spacjami |
| adres, kod i miasto | „ul. Długa 7” obok innych danych osobowych |
| firma | Sp. z o.o., S.A., Sp. j., Ltd., GmbH, także wielkimi literami |
| własne frazy | nazwy projektów, klientów, produktów; w Business także słownik firmowy w pliku licencji |
| dane techniczne | sekrety, hasła, klucze i tokeny dostawców, hosty, adresy IP, loginy, adresy MAC |
| kolumny w arkuszach | nagłówek „Nazwisko” czy „PESEL” ustala typ całej kolumny |

Zamienniki są spójne w rozmowie: „Jan Kowalski” w arkuszu i w czacie tej samej karty dostaje ten sam zamiennik.
W innej karcie ta sama osoba dostaje inny zamiennik, więc dostawca AI nie powiąże rozmów.
Dwa tryby do wyboru: **dane fikcyjne** (domyślnie - tekst czyta się jak zwykłe pismo) albo **etykiety**
`[PERSON_1]`, `[PESEL_1]` do kodu i konfiguracji.

## Pliki

| format | co trafia do czatu |
|---|---|
| XLSX | arkusze Excel: wartości komórek (wyniki formuł zamiast formuł), bez formatowania |
| DOCX | akapity, tabele, nagłówki i stopki: sam tekst, bez formatowania |
| CSV | separator: średnik, przecinek albo tabulator |
| TXT | txt, md, log |
| konfiguracje i logi | env, yaml, json, toml, ini, conf, properties, tf, sh, ps1, xml, sql, pem, key, Dockerfile, kubeconfig |
| PDF, obrazy | w czacie blokowane domyślnie - nic nie prześlizgnie się obok; z menu programu: patrz niżej |

Z włączonym podglądem zobaczysz listę wykrytych wartości z licznikami - odznaczone zostają w pliku bez zmian.

**Z menu programu** (Pro i Business; macOS: pasek menu, Windows: aplikacja w zasobniku): txt, csv, xlsx i docx jak w czacie, a ponadto
**PDF z warstwą tekstową** (wynik: docx albo txt, bez układu strony, obrazów, hiperłączy i podpisów; skany bez tekstu są odrzucane)
oraz **obrazy jpg i png** (usuwamy tylko metadane: lokalizację, urządzenie, autora; treść obrazu, np. tekst na zdjęciu, nie jest
maskowana). Wykrywanie działa na regułach, więc sprawdź wynik przed wysłaniem do AI.

## Prywatność i bezpieczeństwo

- **Działa lokalnie.** Nie przesyła danych do producenta, nie zbiera statystyk ani nie śledzi aktywności
  użytkowników. Żadnej telemetrii, kont użytkowników ani sprawdzania licencji online. Wykrywanie i podmiana
  danych odbywają się na Twoim urządzeniu.
- **Jedyny ruch sieciowy** to opcjonalne „sprawdź aktualizacje”: po kliknięciu wtyczka pobiera jeden statyczny
  plik, bez parametrów, bez numeru wersji i bez identyfikatorów - porównanie wersji robi lokalnie.
  Żadnych żądań sieciowych w tle ani cyklicznie.
- **Mapa zamienników** jest w pamięci programu, osobno dla każdej karty czatu, i znika z jej zamknięciem.
  Przeglądarka jej nie przechowuje, więc ani strona czatu, ani inna wtyczka jej nie odczyta. Na wypadek zerwania
  połączenia program trzyma zaszyfrowaną kopię mapy otwartej karty (XChaCha20-Poly1305, klucz w Keychain na macOS
  albo w Credential Manager na Windows), bez haseł i kluczy API; kopia znika z zamknięciem karty, przy ponownym
  uruchomieniu przeglądarki i najpóźniej po 24 godzinach. Karty incognito nigdy nie trafiają na dysk.
- **Program nie zapisuje kopii roboczych plików z czatu** - przetwarza je w pamięci. Plik z menu programu powstaje obok oryginału, a jego
  mapa oryginałów jest zaszyfrowana kluczem systemu (Keychain, Credential Manager) i znika po 30 dniach. Mapa schowka jest tylko
  w pamięci programu i znika po „Nowej sesji”, po 24 godzinach bezczynności i po zamknięciu programu.
- **Dziennik audytu**: program zapisuje na Twoim komputerze lokalny dziennik zdarzeń technicznych (liczby i kody, bez wiadomości,
  wykrytych wartości, nazw osób i firm, fraz własnych ani nazw plików), zabezpieczony przed niezauważoną zmianą, przechowywany
  180 dni i nigdzie nie jest wysyłany. Działa przy każdej licencji.
- **Licencja** to podpisany plik sprawdzany lokalnie przez program; nic nie jest wysyłane.
- Wtyczka ma uprawnienia tylko do pamięci lokalnej, komunikacji z programem i stron czatów, na których działa.

## Jak zainstalować

Skrót (pełna wersja: [INSTALACJA.md](INSTALACJA.md)):

1. **Program**: na macOS otwórz `donotfeedai-macos.pkg` i przejdź instalator (poprosi o hasło administratora,
   bo instaluje program w `/Applications`). Na Windows uruchom `donotfeedai-windows-setup.exe` (bez uprawnień
   administratora; o podpisie i SmartScreen - patrz [INSTALACJA.md](INSTALACJA.md#windows)).
2. **Wtyczka**: Firefox (Windows i macOS) - otwórz w nim [donotfeedai-wtyczka-firefox.xpi](https://donotfeedai.com/pobierz/donotfeedai-wtyczka-firefox.xpi) i kliknij **Dodaj**.
   Chrome i Edge na Windows - wtyczka jest już w instalatorze, na koniec otworzy się strona z instrukcją.
   Chrome na macOS - rozpakuj `donotfeedai-wtyczka-chrome.zip`, wejdź w `chrome://extensions`, włącz tryb
   dewelopera i wskaż rozpakowany folder. Edge na macOS nie jest obsługiwany.
3. **Zamknij i uruchom przeglądarkę ponownie.** W panelu wtyczki ma być `Program: połączony`.
4. **Licencja**: na macOS w ikonie Do Not Feed AI w pasku menu, obok zegara (**Wczytaj licencję…**), a na Windows
   w panelu wtyczki, w sekcji Licencja, wczytaj plik `.lic`. Bez licencji ochrona jest wyłączona
   (czerwony pasek w czacie); licencję próbną wyślemy na prośbę.

| system | wtyczka | program |
|---|---|---|
| macOS | Chrome: load unpacked (Edge na macOS nie jest obsługiwany); Firefox: podpisany `.xpi` | `donotfeedai-macos.pkg` |
| Windows | w instalatorze (Chrome, Edge: load unpacked); Firefox: podpisany `.xpi` | `donotfeedai-windows-setup.exe` (podpisany cyfrowo) albo, dla działów IT, `donotfeedai-windows.msi` |

## Poziomy

| | Okres próbny | Pro | Business |
|---|---|---|---|
| kto | na prośbę, bez zobowiązań | na stanowisko, praca na danych klientów | na firmę, wdrożenie bez klikania |
| tekst, pliki, dane techniczne, przywracanie odpowiedzi | tak | tak | tak |
| skróty schowka i pliki z menu programu (także PDF i obrazy) | tak | tak | tak |
| dziennik audytu (lokalny, bez treści, 180 dni) | tak | tak | tak |
| własne frazy, tryb ręczny | tak | tak | tak |
| ważność | ustalana przy wysyłce | według umowy | według umowy |
| licencja | plik na stanowisko | plik na stanowisko | jeden plik na firmę, przez MDM lub politykę |
| wspólny słownik firmowy (klienci, projekty, produkty) | - | - | tak |

Licencja jest sprawdzana lokalnie przez program i nie wymaga połączenia z siecią. Bez licencji ochrona jest
wyłączona: wtyczka nie zmienia wiadomości ani plików, a czerwony pasek w czacie mówi to wprost.

## Weryfikacja pobrania

Sumy kontrolne są w każdym wydaniu (`SHA256SUMS.txt`), a te same wartości są wypisane w opisie wydania.
W rozpakowanym katalogu z pobranymi plikami:

```
shasum -a 256 -c SHA256SUMS.txt        # macOS
Get-FileHash .\donotfeedai-windows-setup.exe     # Windows (PowerShell), pojedynczo
```

Instalator macOS jest podpisany certyfikatem Developer ID i notaryzowany przez Apple; możesz to sprawdzić sam:

```
pkgutil --check-signature donotfeedai-macos.pkg
spctl -a -vv --type install donotfeedai-macos.pkg
```

Instalator Windows i programy w nim są podpisane certyfikatem wydanym przez Microsoft (Artifact Signing) dla
*Sebastian Obara It&Consulting*, ze znacznikiem czasu. W PowerShell:

```
Get-AuthenticodeSignature .\donotfeedai-windows-setup.exe | Format-List Status, SignerCertificate
```

## Aktualizacja

- **Program**: pobierz nowy instalator z najnowszego wydania i zainstaluj - nadpisuje poprzednią wersję.
  Program i wtyczkę aktualizuj razem: wtyczka nie współpracuje ze starszym programem i mówi to wprost.
- **Wtyczka** (załadowana jako rozpakowana): skopiuj zawartość nowego folderu do starego (nadpisując pliki)
  albo wskaż nowy folder w „Załaduj rozpakowane”, a potem kliknij odświeżenie w `chrome://extensions`
  i odśwież karty czatu. Ustawienia i licencja zostają - identyfikator wtyczki jest stały.
  Szczegóły: [INSTALACJA.md](INSTALACJA.md#aktualizacja).
- Wersję widać w panelu wtyczki: linia z wersją wtyczki i programu. Gdy wersje się rozjadą, wtyczka to zgłosi.

## Pytania, które padają najczęściej

**Czy muszę instalować program?**
Tak. Wykrywanie, zamienniki, przywracanie odpowiedzi i licencja są w programie, a wtyczka tylko przekazuje mu
tekst i pliki. Bez programu wtyczka nie maskuje danych. Część programu współpracująca z przeglądarką nie ma okna i działa, gdy
przeglądarka jest otwarta; skróty schowka i pliki z menu obsługuje osobna aplikacja (macOS: ikona w pasku menu, Windows: ikona
w zasobniku, uruchamiana ze skrótu w menu Start, bez autostartu, dopóki sam go nie włączysz).

**Czy działa w edytorze kodu albo terminalu?**
Wtyczka nie, ale program tak, przez skróty schowka (Pro i Business, domyślnie wyłączone, patrz „Jak to działa”): kopiujesz tekst,
skrót zamienia schowek na tekst z zamiennikami, wklejasz do AI, a odpowiedź przywracasz drugim skrótem. Asystentów w edytorze
i wywołań API nie obsługujemy.

**Co z danymi, których wtyczka nie wykryje?**
Nazwy projektów, klientów czy produktów dodajesz jako własne frazy. Podgląd przed wysłaniem pokazuje listę
wykrytych wartości z checkboxami, a tryb ręcznego przywracania pokazuje dokładnie to, co dostało i odpowiedziało
AI. Znane ograniczenie: nieznana wcześniej osoba wspomniana wyłącznie w przypadku zależnym („list do Nowaka”)
nie jest wykrywana.

**Czy wtyczka spowalnia pisanie albo wysyłanie?**
Program to reguły i sumy kontrolne, bez modeli językowych i bez chmury: kilka tysięcy znaków sprawdza w kilka
milisekund, więc licznik „N wykrytych” odświeża się
na bieżąco podczas pisania. Podmiana w polu następuje w chwili wysłania.

**Co się dzieje po wygaśnięciu licencji?**
Po dacie wygaśnięcia masz jeszcze 14 dni pełnego dostępu (okres przejściowy, z ostrzeżeniem w panelu i na pasku).
Potem ochrona jest wyłączona: wtyczka nie zmienia wiadomości ani plików, a czerwony pasek w czacie mówi to wprost.
Tak samo kończy się licencja próbna.
