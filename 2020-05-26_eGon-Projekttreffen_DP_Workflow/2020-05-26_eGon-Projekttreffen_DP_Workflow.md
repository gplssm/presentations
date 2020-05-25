---
author:
- Guido Pleßmann
- Stephan Günther
title: Data Processing Pipeline
subtitle: Definition des Workflows und Datenaustausch mit OEDB \newline \footnotesize 2. Projekttreffen eGo^n^
institute: Reiner Lemoine Institut / Universtität Magdeburg
classoption: aspectratio=169
date: 26.05.2020
theme: egon
---

# Prämissen & Anforderungen

- Versionierung in der OEDB ist für Administration, nicht zum Produktiveinsatz gedacht
- Berechnungen des Data Processings (DP) kann nicht auf OEP ausgeführt werden, lediglich zur Datenverwaltung
- Kommunikation mit der OEP nur über `oedialect`.  
  Empfohlen: SQLAlchemy ORM Klassendefinitionen
- DP soll automatisiert reproduzierbar sein
- Einsatz von Open Source Tools
- DP ist auf beliebigem Rechner ausführbar

# Data Processing Pipeline (Production)

\center
![](img/DP_Workflow.pdf){ width=68% }


# Versionierung & Workflow Management

- Versionierung erfolgt je Datensatz (Tabelle) mit eigenständiger Versionsnummer 
- Versionsnummer in einer Spalte der Tabelle -> mehrere Versionen in einer Tabelle möglich
- Abhängigkeit zwischen Datensätzen (und dem Skript, dass sie verknüpft) muss bekannt sein. Optionen: YAML, JSON, Python `dict()`

![](img/Version_management_script-centric.pdf){ width=85% }

# Versionierung & Workflow Management

:::::: {.columns}
::: {.column  width=50%} 

- Abbildung der Abhängigkeiten und der Versionen mittels Graph (bipartit und/oder DAG)
- Verwaltung des Graphen je nach Workflow Management Tool (Snakemake oder Apache Airflow)
:::

::: {.column  width=50%}
![](img/DP-Workflow_Versioning_bipartite-modeling_rescaled.png){ width=100% }
:::
::::::

# {.plain }

\center
\LARGE Für die Kleingruppe

# Fragen zu Versionierung & Workflow Management

- Wie gehen wir mit Veränderungen der Tabellenstruktur (z.B. Spalte hinzufügen/umbenennen) um? Kann das im Rahmen einer neuen Version erfolgen? Ab welchem Maß an Veränderung sollte ein neuer Datensatz erstellt werden?
- Können Bereiche gültiger Versionen definiert werden à la `>=0.3.2 <0.5.0`?
- DAG / bipartiter Graph?


# Spezifische Anforderungen DP Development

- Datenaustausch von development Daten zwischen Projektpartnern (z.B. über Schema _model_draft_)
- Import von benötigten Daten zu Pipelineschritt X (z.B. SQL-Dump oder Funktion, die Abhängigkeiten auflöst)
- Partielle Ausführung des DP

# Spezifisches zur Preprocessing Pipeline

Einige, der im Preprocessing erstellten Tabellen, existieren bereits. Es muss beachtet werden

- nicht alle Daten müssen neu geschrieben werden
- Ersetzen einer Tabelle würde ggf. andere Menschen beeinflussen
- Änderungen der Tabellenstruktur (z.B. andere Spalten) bricht Workflows anderer Menschen (die wir nicht kennen)

# OEP Schnittstelle

Optionen

- ORM-Klassendefinitionen versioniert in ego.io
- SAIO & OEM2ORM

# Benötigte Tools (helper functions)

- Import von Tabelle in lokale DB
- Constraints, Indizes, Metadaten (Comment), die in lokaler Datenbank erstellt werden, in OEP übernehmen
- Suche von Datensatz in versionierten Schemata, _model_draft_, in lokaler DB
- Metadaten.json Ersteller
- OEM2ORM
- Testdatensatz
