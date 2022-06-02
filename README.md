# Elections Scraper
Třetí projekt zpracovaný v rámci zadání Engeto Akademie.

## Popis projektu
Tento projekt slouží k extrahování výsledků voleb konaných v roce 2017 do souboru ``.csv``. Odkaz na úvodní stránku výsledků voleb do Poslanecké sněmovny ČR 2017 najdete [zde](https://volby.cz/pls/ps2017nss/ps3?xjazyk=CZ).

## Instalace
- postup je popsán pro OS Windows a prostředí IDE Visual Studio Code

### Instalace virtuálního prostředí
Pro instalaci knihoven doporučuji vytvořit ve složce s projektem virtuální Python prostředí. Prostředí vytvoříme a aktivujeme za pomoci CMD resp. příkazového řádku ve složce projektu následujícími příkazy:

*Absolutní cesta zavisí na vaší konfiguraci (uživatelské jméno, umístění složky,...).*

```
python -m venv C:\Users\pepe\Desktop\projekt\venv       # venv je volitelný název virtuálního prostředí
cd C:\Users\pepe\Desktop\projekt\venv\scripts           # pro aktivaci "venv" se přemístíme do složky scripts
activate                                                # pomoci "activate" aktivujeme virtuální prostředí Pythonu v konzoli
(venv)                                                  # objeví se v konzoli v případě uspěšné aktivace název virtuálního prostředí
cd ..\..                                                # vrátíme se z5 do složky s projektem
```

### Instalace knihoven
Projekt obsahuje soubor `requirements.txt` se seznamem použitých knihoven. V rámci projektu jsou využívány hlavně knihovny **requests** a **beautifulsoup4**. Pro instalaci knihoven ze seznamu do virtuálního prostředí použíjte tyto příkazy:

*Příkazy zadávejte v CMD ve složce projektu. V mém případě v ``C:\Users\pepe\Desktop\projekt``.*

```
pip3 --version                          # ověří verzi manažeru
pip3 install -r requirements.txt        # nainstaluje knihovny
```
Nyní by mělo být vše připraveno ke spuštění projektu 🙂.

## Spuštění projektu
Spuštění souboru ``elections_scraper.py`` v CMD resp. v příkazovém řádku požaduje zadat dva argumenty v následujícím pořadí:
1. URL odkaz vybraného uzemního celku
2. název výsledného souboru s příponou ``.csv``

*Pro ideální vymezení argumentů zadávejte argumenty v uvozovkách.*
```
python elections_scraper.py <"odkaz_uzemniho_celku"> <"vysledny_soubor">
```
Výstupem programu bude soubor se staženými daty ve formátu ``.csv``.

## Ukázka projektu
Výsledky hlasování pro okres Třebíč:
1. argument: https://volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=10&xnumnuts=6104
2. argument: vysledky_trebic.csv
```
python elections_scraper.py "https://volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=10&xnumnuts=6104" "vysledky_trebic.csv"
```
Průběh stahování:
```
Stahuji hlavičku z vybraného URL:
https://volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=10&xnumnuts=6104
Stahuji data z vybraného URL:
https://volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=10&xnumnuts=6104
Ukládám data do vybraného souboru:
vysledky_trebic.csv
+----------------------------------------------+
| Data uložena do souboru: vysledky_trebic.csv |
+----------------------------------------------+
Ukončuji program...
```
Částečný výstup:
```
kód obce,název obce,voliči v seznamu,vydané obálky,platné hlasy,Občanská demokratická strana,...
590274,Babice,167,126,126,9,0,0,11,0,8,9,0,0,3,0,0,16,0,1,40,0,19,0,1,0,0,7,2
590282,Bačice,165,104,104,1,1,0,5,0,6,23,0,1,0,0,0,5,1,2,33,1,7,0,0,0,0,14,4
...
```