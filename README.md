# Health Data Pipeline

## Description

Projet de Data Engineering visant à construire un pipeline complet de traitement et d'analyse de données de santé en France.

L'objectif est de transformer un fichier CSV contenant environ **5,8 millions de lignes** de statistiques de santé en une plateforme analytique structurée, fiable et exploitable.

Le projet met en œuvre une architecture moderne de traitement de données incluant :

* ingestion de données ;
* contrôle qualité ;
* nettoyage et validation ;
* stockage dans PostgreSQL ;
* transformations avec dbt ;
* orchestration avec Apache Airflow ;
* visualisation avec Metabase.

L'objectif principal est de reproduire une architecture proche de celles utilisées dans des environnements professionnels Data Engineering.

---

# Architecture du pipeline

Le pipeline suit une approche en couches inspirée du modèle **Medallion Architecture** :

```
                    Source CSV
                       |
                       v
                  Bronze Layer
              (données brutes)
                       |
                       v
                  Silver Layer
          (données nettoyées et validées)
                       |
                       v
                   Gold Layer
          (modèle analytique / Data Warehouse)
                       |
                       v
          PostgreSQL + Metabase Dashboard
```

---

# Dataset

Le jeu de données contient des statistiques de santé françaises avec les colonnes suivantes :

| Colonne            | Description                    |
| ------------------ | ------------------------------ |
| annee              | année d'observation            |
| patho_niv1         | niveau 1 de pathologie         |
| patho_niv2         | niveau 2 de pathologie         |
| patho_niv3         | niveau 3 de pathologie         |
| top                | indicateur pathologie          |
| cla_age_5          | classe d'âge                   |
| sexe               | sexe                           |
| region             | région                         |
| dept               | département                    |
| Ntop               | nombre de personnes concernées |
| Npop               | population de référence        |
| prev               | prévalence                     |
| Niveau prioritaire | niveau de priorité             |
| libelle_classe_age | libellé âge                    |
| libelle_sexe       | libellé sexe                   |
| tri                | ordre de tri                   |

---

# Technologies utilisées

## Langages

* Python
* SQL

---

## Traitement des données

| Librairie     | Utilité                                                     |
| ------------- | ----------------------------------------------------------- |
| Polars        | traitement performant des fichiers CSV volumineux           |
| DuckDB        | exploration analytique et requêtes SQL rapides sur fichiers |
| SQLAlchemy    | gestion des connexions et interactions avec PostgreSQL      |
| psycopg2      | driver PostgreSQL pour Python                               |
| python-dotenv | gestion des variables d'environnement                       |

---

## Qualité et développement

| Outil  | Utilité                                    |
| ------ | ------------------------------------------ |
| pytest | tests automatisés                          |
| Ruff   | analyse statique et qualité du code Python |
| Black  | formatage automatique du code              |

---

## Data Engineering

| Technologie        | Utilité                              |
| ------------------ | ------------------------------------ |
| PostgreSQL         | stockage analytique                  |
| Apache Airflow     | orchestration des pipelines          |
| dbt                | transformations SQL et modélisation  |
| Great Expectations | validation de la qualité des données |
| Docker             | conteneurisation                     |

---

## Visualisation

| Outil    | Utilité                            |
| -------- | ---------------------------------- |
| Metabase | création de dashboards analytiques |

---

# Structure du projet

```
health-data-pipeline/

├── data/
│   ├── raw/
│   ├── bronze/
│   ├── silver/
│   └── gold/
│
├── src/
│   ├── ingestion/
│   ├── validation/
│   ├── cleaning/
│   ├── loading/
│   ├── utils/
│   └── config/
│
├── airflow/
│   └── dags/
│
├── dbt/
│
├── great_expectations/
│
├── tests/
│
├── docs/
│
├── docker/
│
├── docker-compose.yml
├── requirements.txt
├── README.md
└── .gitignore
```

---

# Objectifs du projet

Ce projet a pour objectifs de mettre en pratique :

* conception d'une architecture Data Engineering ;
* ingestion de données volumineuses ;
* gestion de la qualité des données ;
* approche ETL / ELT ;
* modélisation Data Warehouse ;
* automatisation des pipelines ;
* industrialisation avec Docker ;
* documentation et bonnes pratiques Git.

---

# Installation

## Cloner le projet

```bash
git clone <repository_url>

cd health-data-pipeline
```

## Créer l'environnement Python

```bash
python3 -m venv .venv
```

Activation :

Linux / Mac :

```bash
source .venv/bin/activate
```

Windows :

```bash
.venv\Scripts\activate
```

## Installer les dépendances

```bash
pip install -r requirements.txt
```

---

# Statut du projet

🚧 Projet en cours de développement

Étapes réalisées :

* [x] Initialisation du dépôt Git
* [x] Structure du projet
* [x] Configuration Docker
* [x] Mise en place PostgreSQL
* [ ] Pipeline d'ingestion
* [ ] Contrôles qualité
* [ ] Transformation dbt
* [ ] Orchestration Airflow
* [ ] Dashboard Metabase

---

# Auteur

Houlape Joseph

Objectif : démontrer la conception et l'industrialisation d'un pipeline de données complet.
