# NEXUS-STAFF-ENGINEER-MONITOR-v2.0.0-Monitoring-100-REEL---docker-
# NEXUS STAFF ENGINEER MONITOR v2.0.0 # Monitoring 100% REEL - docker stats, postgres, redis, HTTP endpoints # Zero simulation. Chaque metrique vient d'une source reelle. # Auteur : Aissa Mohammedi (DGK) # Licence : NEXUS-OPEN-2.0
# NEXUS STAFF ENGINEER MONITOR

> **1 file. 0 dependency. 100% REAL metrics. Replaces Grafana + Datadog for local stacks.**

[![Version](https://img.shields.io/badge/version-2.0.0-00ffc8?style=flat-square)](https://github.com)
[![Python](https://img.shields.io/badge/python-3.8%2B-3776ab?style=flat-square)](https://python.org)
[![License](https://img.shields.io/badge/license-NEXUS--OPEN--2.0-00c8ff?style=flat-square)](LICENSE)
[![Size](https://img.shields.io/badge/size-1%20file-ff00c8?style=flat-square)](nexus_staff_monitor.py)

Dashboard temps réel `localhost:8088` qui orchestre et surveille 7 services multi-langages. Chaque métrique vient d'une source réelle, aucune simulation.

**Auteur:** Aissa Mohammedi (DGK) | **Licence:** NEXUS-OPEN-2.0

---

### 🎯 Pourquoi ce projet?

| Grafana + Prometheus + Datadog | NEXUS MONITOR |
| :--- | :--- |
| 5 containers, 2Go RAM, 30min de setup | 1 fichier `.py`, 20Mo RAM, 2sec de setup |
| Besoin de configurer des exporters | Lit direct `/proc`, `docker stats`, `socket` |
| Ne marche pas sur iOS | Marche sur a-Shell iOS, Linux, Mac, Pi |
| 2000 lignes de YAML | 0 dépendance, stdlib pure |

### 📐 Architecture surveillée

Le monitor attend 7 services par défaut (configurable):

| Service | Langage | Port | Rôle | Container |
| :--- | :--- | :--- | :--- | :--- |
| PostgreSQL | SQL | 5432 | Primary Data Store | nexus-postgres |
| Redis | C | 6379 | Cache & Event Queue | nexus-redis |
| Python Orchestrator | Python | 8000 | API Orchestrator | nexus-python |
| Java Task Service | Java | 8080 | Task Service | nexus-java |
| Go Worker | Go | 8001 | Worker Service | nexus-go |
| Rust Validator | Rust | 3000 | Validator Service | nexus-rust |
| TypeScript Frontend | TypeScript | 3001 | Frontend API | nexus-ts |

### 🔬 Sources de données 100% RÉELLES

Aucune métrique n'est inventée. Code vérifiable:

1. **TCP Port:** `socket.connect_ex("127.0.0.1", PORT)` + mesure latence ms
2. **Docker Stats:** `docker stats --no-stream` -> CPU %, RAM Mo, NetIO, BlockIO
3. **Docker Inspect:** `docker inspect` -> Status, Health, RestartCount, Uptime réel
4. **HTTP Health:** `urllib.request GET /health` -> Status + latence HTTP réelle
5. **Prometheus:** Scrape `/metrics` si présent
6. **Système:** Lecture `/proc/stat`, `/proc/meminfo`, `os.statvfs`, `/proc/uptime`, `ps aux`

Si un service est down, il affiche `KO · port fermé`. Il ne ment jamais.

### 🚀 Installation

```bash
# 1. Clone
git clone https://github.com/Aissamohammedi88/NEXUS-STAFF-ENGINEER-MONITOR-v2.0.0-Monitoring-100-REEL---docker-
cd nexus-staff-monitor

# 2. Lance le dashboard (0 dépendance)
python3 nexus_staff_monitor.py

# 3. Ouvre
open http://localhost:8088

 NEXUS STAFF ENGINEER MONITOR

> **1 file. 0 dependency. 100% REAL metrics. Replaces Grafana + Datadog for local stacks.**

[![Version](https://img.shields.io/badge/version-2.0.0-?style=flat-square)](https://github.com)
[![Python](https://img.shields.io/badge/python-3.8%2B-?style=flat-square)](https://python.org)
[![License](https://img.shields.io/badge/license-NEXUS--OPEN--2.0-?style=flat-square)](LICENSE)
[![Size](https://img.shields.io/badge/size-1%20file-?style=flat-square)](nexus_staff_monitor.py)

Dashboard temps réel `localhost:8088` qui orchestre et surveille 7 services multi-langages. Chaque métrique vient d'une source réelle, aucune simulation.

**Auteur:** Aissa Mohammedi (DGK) | **Licence:** NEXUS-OPEN-2.0

---

### 🎯 Pourquoi ce projet?

| Grafana + Prometheus + Datadog | NEXUS MONITOR |
|:--- |:--- |
| 5 containers, 2Go RAM, 30min de setup | 1 fichier `.py`, 20Mo RAM, 2sec de setup |
| Besoin de configurer des exporters | Lit direct `/proc`, `docker stats`, `socket` |
| Ne marche pas sur iOS | Marche sur a-Shell iOS, Linux, Mac, Pi |
| 2000 lignes de YAML | 0 dépendance, stdlib pure |

### 📐 Architecture surveillée

Le monitor attend 7 services par défaut (configurable):

| Service | Langage | Port | Rôle | Container |
|:--- |:--- |:--- |:--- |:--- |
| PostgreSQL | SQL | 5432 | Primary Data Store | nexus-postgres |
| Redis | C | 6379 | Cache & Event Queue | nexus-redis |
| Python Orchestrator | Python | 8000 | API Orchestrator | nexus-python |
| Java Task Service | Java | 8080 | Task Service | nexus-java |
| Go Worker | Go | 8001 | Worker Service | nexus-go |
| Rust Validator | Rust | 3000 | Validator Service | nexus-rust |
| TypeScript Frontend | TypeScript | 3001 | Frontend API | nexus-ts |

### 🔬 Sources de données 100% RÉELLES

Aucune métrique n'est inventée. Code vérifiable:

1. **TCP Port:** `socket.connect_ex("127.0.0.1", PORT)` + mesure latence ms
2. **Docker Stats:** `docker stats --no-stream` -> CPU %, RAM Mo, NetIO, BlockIO
3. **Docker Inspect:** `docker inspect` -> Status, Health, RestartCount, Uptime réel
4. **HTTP Health:** `urllib.request GET /health` -> Status + latence HTTP réelle
5. **Prometheus:** Scrape `/metrics` si présent
6. **Système:** Lecture `/proc/stat`, `/proc/meminfo`, `os.statvfs`, `/proc/uptime`, `ps aux`

Si un service est down, il affiche `KO · port fermé`. Il ne ment jamais.

### 🚀 Installation

```bash
# 1. Clone
git clone https://github.com/ton-pseudo/nexus-staff-monitor.git
cd nexus-staff-monitor

# 2. Lance le dashboard (0 dépendance)
python3 nexus_staff_monitor.py

# 3. Ouvre
open http://localhost:8088

C'est tout.

🐳 Tester avec des vrais services (optionnel)

docker compose up -d
docker compose ps
# Le dashboard passe de 0/7 à 7/7 OK avec vraies métriques

📡 API

Endpoint Description
`GET /` Dashboard HTML
`GET /api/state` Etat complet JSON (toutes les métriques)
`GET /api/health` Health du monitor lui-même
`GET /readme` Documentation texte

📸 Dashboard

> `localhost:8088` - Thème cyberpunk, temps réel 3s, charts SVG, top processus, containers Docker.

📂 Contenu du repo

.
├── nexus_staff_monitor.py # V2.0.0 - 100% REEL (recommandé)
├── nexus_staff_studio.py # V1.0.0 - Simulation déterministe (léger)
├── docker-compose.yml # Stack de test 7 services
├──.gitignore
├── LICENSE
└── README.md

📄 Licence

NEXUS-OPEN-2.0 - Copyright (c) 2026 Aissa Mohammedi (DGK)
Libre d'utilisation, modification, commercial. Voir `LICENSE`.

---
*Built with frustration against bloated observability stacks.*


### 2. `.gitignore` - pro


Python
*pycache*/
_.py
_$py.class
_.so
_.egg-info/
dist/
build/
.venv/
venv/
env/[cod]

Nexus
Documents/nexus_staff__/
_.log
logs/
exports/

OS
.DS_Store
http://Thumbs.db
.idea/
.vscode/

Docker
.docker/


### 3. `LICENSE` - NEXUS-OPEN-2.0


NEXUS-OPEN-2.0 LICENSE
Copyright (c) 2026 Aissa Mohammedi (DGK)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

1. Attribution required: Keep original author name Aissa Mohammedi (DGK)
2. No warranty: Software is provided as-is.
3. No liability.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.


### 4. Description GitHub (quand tu crées le repo)

**Description courte:** `1-file Python monitoring that replaces Grafana + Datadog. 0 deps, 100% real metrics from docker stats, /proc, and TCP checks.`

**Topics:** `monitoring` `grafana-alternative` `datadog-alternative` `docker` `python` `observability` `staff-engineer` `stdlib`


### 4. Description GitHub (quand tu crées le repo)

**Description courte:** `1-file Python monitoring that replaces Grafana + Datadog. 0 deps, 100% real metrics from docker stats, /proc, and TCP checks.`

**Topics:** `monitoring` `grafana-alternative` `datadog-alternative` `docker` `python` `observability` `staff-engineer` `stdlib`


