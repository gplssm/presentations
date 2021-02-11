---
author:
- Guido Pleßmann
- Ludwig Hülk
title: An introduction to/update on the Marktstammdatenregister (MaStR) and open-MaStR
institute: Reiner Lemoine Institut
classoption: aspectratio=169
date: 2021-02-22
theme: rli
urlcolor: rlilinkcolor
header-includes:
- |
  \newcommand{\tel}{+49 (0)30 1208 434 72}
  \newcommand{\email}{guido.plessmann@rl-institut.de}
  \newcommand{\twitter}{\href{https://twitter.com/gplssm}{@gplssm}}
  \newcommand{\finalstatement}{Enjoy stating a final statement ;-)}
  \tikzset{
  invisible/.style={opacity=0},
  visible on/.style={alt={#1{}{invisible}}},
  alt/.code args={<#1>#2#3}{%
    \alt<#1>{\pgfkeysalso{#2}}{\pgfkeysalso{#3}} % \pgfkeysalso doesn't change the path
  },
  }
  \usepackage{blindtext}
---

# Outline

# What is the MaStR?

\alert{Goal: being the one and only register for assets in the power and gas sector}

- \alert{Cite relevant paragraphs from MaStRV}
- \alert{Who enters data?}
- \alert{How is data quality assured?}

# What data is available?

# How to access the data?

- \alert{Web portal}
- \alert{Data dumps (Datenauszug) that is irregularly provided by the BNetzA}
- \alert{Webservice}

# Introducing open-MaStR

- \alert{Explain what open-MaStR is intended for}
- \alert{Why downloading the entire dataset is hard}
- \alert{Fundamentals for data download in open-MaStR}
- \alert{MaStRMirror for up-to-date data}

# Data quality and completeness

- Additional data per technology
- Covered capacity compared to reference sources
- Analysis from eGo^n project meeting 12/20
- Status Netzbetreiberprüfung

# Getting latest data

- Amount of recent changes: plot count(DatumLetzeAktualisierung) vs. time

# Cleaning and enriching data

\alert{Describe why a postprocessing is necessary}

\alert{Explain what happens with the data and how is can be used and modified}

# Available analysis tools

\alert{Present existing Jupyter Notebooks and other useful stuff for data analysis}

# Which data can I use now?


# Just for fun


## How to name functions properly?


GetGefilterteAnlagenStromerzeuger()


## Defining column names late at night

```
psql -U open-mastr -d open-mastr -h localhost -p 55443 -c "SELECT count(\"EinheitMastrNummer\") FROM mastr_mirrored.mastr_wind WHERE \"StatistikFlag\" = 'B';"
```

Luckily, postgres has a helpgul hint ;-)

```
ERROR:  column "StatistikFlag" does not exist
ZEILE 1: ...astrNummer") FROM mastr_mirrored.mastr_wind WHERE "Statistik...
                                                              ^
TIP:  Perhaps you meant to reference the column "mastr_wind.StatisikFlag".
```

# Call for collaborators

_You can contribute at various levels!_

- Enhancing documentation
- Add data cleaning enrichment methods
- Fix bugs
- Write tests
- Refactor smaller and larger bits

Open for pull requests!


# Outlook

\alert{What is planned in the next month's?}


# {.plain}

\insertendpagecontent
