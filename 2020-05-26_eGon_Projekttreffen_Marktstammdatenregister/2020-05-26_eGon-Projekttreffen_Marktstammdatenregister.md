---
author:
- Guido Pleßmann
title: Marktstammdatenregister
subtitle: Einblicke ins Marktstammdatenregister und open-MaStR
institute: Reiner Lemoine Institut
classoption: aspectratio=169
date: 26.05.2020
theme: egon
linkcolor: red
---

# MaStR – Das Marktstammdatenregister

:::::: {.columns}
::: {.column  width=50%}

**Ziele**

- Daten für die Energiewende
  - Daten zu Anlagen und Anlagen-Betreibenden
  - Alle neuen und alle bestehenden Anlagen
  - Anlagen zur Erzeugung von erneuerbarer und konventioneller Energie
  - Anlagen zur Erzeugung von Strom und Gas
- Ausschließlich Stammdaten
- Bürokratieabbau
:::

::: {.column  width=50%}
**Konzept**

- [MaStRV](http://www.gesetze-im-internet.de/mastrv/inhalts_bersicht.html) (Verordnung über das zentrale elektronische Verzeichnis energiewirtschaftlicher Daten)
- Konzeptionierung und Aufbau: 09.06.2015 – 31.01.2019 [Historie](https://www.bundesnetzagentur.de/DE/Sachgebiete/ElektrizitaetundGas/Unternehmen_Institutionen/DatenaustauschundMonitoring/Marktstammdatenregister/Historie/historie-node.html)
- Zugang über Website, Excel dumps und SOAP-API
- Lange Verzögerung
- ~~Gute Struktur und~~Interessantes Objektmodell
- [Datenlizenz Deutschland – Namensnennung – Version 2.0](https://www.govdata.de/dl-de/by-2-0)

:::
::::::

# Fristen und Pflichten für Anlagenbetreiber

Jede Anlage muss registriert werden

| Inbetriebnahme | Frist |
|----------------|-------|
| < 1. Juli 2017 | 31. Januar 2021|
| > 1. Juli 2017 | 31. Juli 2019|

Spezielle Fristen für EEG- und KWK-Anlagen

| Inbetriebnahme | Frist |
|----------------|-------|
| < 1. Juli 2017 | 31. Januar 2021 |
| 1. Juli 2017 bis 31.01.2019 | 31. Januar 2021 (Vervollständigung) |
| > 31.01.2019 | 1 Monat nach Inbetriebnahme der Anlage |


# Fristen und Pflichten für Netzbetreiber

Zur Sicherstellung der Datenqualität werden Netzbetreiber aufgefordert Daten registrierter Anlagen in ihrem Gebiet zu prüfen.

| Datum der Prüfungsaufforderung | Frist |
|--------------------------------|-------|
| < 31. Januar 2021 | 6 Monate |
| > 31. Januar 2021 | 1 Monate |

Abweichend EEG und KWK Anlagen im Ausschreibungsverfahren: es gilt direkt die Einmonatsfrist.

Bei nicht Vorlage des Inbetriebnahmeprotkolls verlängert sich die Frist auf max. 6 Monate.

# Objektmodell Stromerzeugungseinheit { .empty }

\centering
![](img/Objektmodell-Fachliche_Ansicht_V1.2.0_Einheit.pdf){ height=80% }

# Objektmodell Marktakteure und Lokationen

:::::: {.columns}
::: {.column  width=60%}
![](img/Objektmodell-Fachliche_Ansicht_V1.2.0_Akteur-Lokation.pdf){ height=80% }
:::

::: {.column  width=40%}
Neben Stammdaten der Anlagen sind weitere Informationen mit einer Anlage verknüft: 

- Netzbetreiber
- Netzanschlusspunkt
- Bilanzierungsgebiet
:::
::::::


# open-MaStR

:::::: {.columns}
::: {.column  width=40%}
Python package zum

- Download
- Cleansing 
- Analyse der MaStR

mit dem Ziel der Datenzugänglichmachung

\vspace{10pt}

Alles relativ kompliziert 

- SOAP API und Tabellen-/Abfragestruktur
- Parallelisierung
- Datenqualität
:::

::: {.column  width=65%}
Im Rahmen von eGo^n^:

Python wrapper für SOAP API

```
from open_mastr.soap_api.sessions import MaStRAPI

mastr_api = MaStRAPI()
wind_units = mastr_api.\
	GetGefilterteListeStromErzeuger(
		energietraeger="Wind",
		limit=1)
```
\vspace{10pt}
Gewinner des Awards für den besten Variablennamen
```
GetEinheitGeoSolarthermieGrubenKlaerschlamm()
```
:::
::::::




# Vollständige Adress-/Geodaten

- Laut Ludwig können für Forschungszwecke ortsscharfe Daten aller Anlagen bezogen werden
- Beantragung bei der BNetzA
- RLI hat bereits "speziellen" Zugang mit erweiterten Downloadberechtigungen

# Geplante Datenprüfungen

- Vollständigkeit der Erzeugungsleistung: vorläufiges Diagramm zeigen
- Vollständigkeit und Qualität der Geolokationen
- Bringen Informationen zu Netzbetreibern etwas für MS-Netzgebietsdefinition?
- Inwieweit ist die Netzbetreiberprüfung bereits abgeschlossen?

# Erzeugungskapazitäten Excel dump vs. SMARD

\centering
![](img/MaStr_Veroeffentlichung_Technologien_Einheitentyp_SMARD-2019_Vergleich.pdf){ height=83% }


