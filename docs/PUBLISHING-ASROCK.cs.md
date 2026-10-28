# Zveřejnění ASRock portu na GitHubu

Připraveno 28. 10. 2026. Zatím nebyl vytvořen veřejný repozitář ani nic nahráno.

## Co zveřejnit

Nejpřehlednější je fork
[impacifist/Windows-GPU-UNLOCK](https://github.com/impacifist/Windows-GPU-UNLOCK),
který zachová historii a původní autorství. Port vychází z commitu
`20c44fecac13cdf601b6a9357a46d8fea29f2678`; není automaticky aktualizovaný na
novější hlavní větev. Případný pull request bude vyžadovat samostatné porovnání
a integraci změn proti tehdejší verzi upstreamu.

Zveřejni zdrojové změny, dokumentaci a vybrané anonymizované výsledky.
Uveď experimentální podporu jediné přesně popsané sestavy. Text pro portfolio
je v [PORTFOLIO.cs.md](PORTFOLIO.cs.md); technický popis v
[ASROCK-B450M-RTX3060.en.md](ASROCK-B450M-RTX3060.en.md).

## Co není v čistém balíčku

- NVIDIA firmware, `PROM.BIN`, `IMG*.BIN` a další binární dumpy.
- Celé DIAG/HLS/AUTO protokoly a soukromé testovací fixtures.
- Sestavené `.EFI` soubory, včetně historického upstream EFI souboru.
- `platform-config.h`, GUID oddílu Windows, cesty k uživatelskému profilu,
  přihlašovací údaje a privátní klíče.
- Stažené překladače, CUDA/PyTorch prostředí, cache, další vložené Git repozitáře
  a metadata `.git`.

Veřejné soubory stále obsahují záměrně publikované modelové a hardwarové údaje:
typ desky, BIOS, PCI/subsystem ID, VBIOS a otisky použitých dat. To nejsou
soubory firmwaru. Souhrn testů je odvozený z lokálních záznamů, není náhradou
za soukromé podklady požadované build gate.

## Licence a původ

Zachovej `LICENSE`, `LICENSES/`, `THIRD_PARTY_NOTICES.md`, původní copyright
hlavičky a původ projektu. Zděděný unlock a Windows port jsou GPL-2.0-only;
jednotlivé závislosti mohou mít vlastní licenci. Neoznačuj celý fork za vlastní
nový algoritmus ani ho nepřelicencovávej na MIT.

Připravený archiv je zdrojový. Nedává oprávnění přibalit NVIDIA firmware.
Úpravy jsou popsány v CHANGES a v seznamu portovaných souborů. Export přidává
do upravených zdrojů datované publikační poznámky; jejich bajtové otisky se proto
liší od původního hardwarově testovaného buildu. Před sestavením z exportu je
nutné znovu provést lokální testy. Starý SOURCE-MANIFEST.json patří původnímu
upstream snapshotu; aktuální seznam exportovaných souborů je v PUBLICATION-MANIFEST.json.

## Doporučený postup pro GitHub

1. Na GitHubu vytvoř fork původního Windows projektu pod svým účtem.
2. V samostatném checkoutu forku vytvoř větev z výše uvedeného základního commitu.
3. Přenes kontrolované zdrojové změny z čistého archivu. Nenahrávej celou pracovní
   složku `gpu-unlock` a nepřidávej v ní bez kontroly vše přes `git add .`.
4. Zkontroluj přidávané soubory a diff; zachovej licence a upstream historii.
5. Udělej commit a push do své větve. GitHub Actions před případným zapnutím projdi;
   soukromé hardware fixtures v repozitáři nejsou a plná reprodukce testů je vyžaduje.
6. V profilu GitHubu připni svůj fork a použij přiměřený popis z portfolia.

Alternativou je nový repozitář ze zdrojového snapshotu s výrazným odkazem na
upstream a jeho základní commit; fork lépe ukazuje, co je tvůj příspěvek.
Příprava archivu nemění Git remote, nevytváří commit a nic nepublikuje.

## Než z toho uděláš veřejný „release“

Tato verze je vhodná jako výzkumný/portfolio projekt. Chybí ověření na dalších
sestavách, dlouhodobá stabilita a obecný postup pro nové uživatele bez tvých
lokálních diagnostických podkladů. Nevydávej cizím lidem EFI binárku sestavenou
pro svůj Windows oddíl a neprezentuj archiv jako univerzální instalátor.
