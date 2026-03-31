<p align="center">
  <img width="409" height="420" alt="Yaneli’s Music Awards logo" src="https://github.com/user-attachments/assets/ae4c943b-9199-44e0-b55b-d242ec02caaa" />
</p>

# Yaneli’s Music Awards (2010–2024) — SQL para Reporting y KPIs (MySQL)

![MySQL](https://img.shields.io/badge/DB-MySQL-4479A1?logo=mysql&logoColor=white)
![SQL](https://img.shields.io/badge/Query-SQL-2F74C0)
![Python](https://img.shields.io/badge/Python-pandas%2Fnumpy-3776AB?logo=python&logoColor=white)
![KPI](https://img.shields.io/badge/Enfoque-KPIs%20%26%20Reporting-20c997)
![Team](https://img.shields.io/badge/Trabajo-Team%20Project-6f42c1)

Proyecto de análisis musical que convierte datos de **Spotify** y **Last.fm** en una gala de premios ficticia: los **Yaneli’s Awards**.  
Más allá del storytelling, el proyecto está diseñado como un caso de **modelado relacional + SQL orientado a métricas (KPIs) y reporting**.

---

## Resumen ejecutivo (para qué sirve)

**Objetivo:** construir una base de datos relacional en **MySQL** y crear consultas SQL para generar **métricas, rankings y KPIs** reproducibles.  
**Qué demuestra:** modelado, relaciones (FK), normalización, joins, agregaciones y queries orientadas a decisión.  
**Aplicación (innovación social / empleabilidad):** la misma lógica sirve para centralizar datos, automatizar reporting y dar trazabilidad a indicadores de proceso/resultado (participación, avance por hitos, resultados).

---

## Acceso rápido

- 🗃️ **Dump MySQL:** `musica_db_dump.sql`  
- 🧠 **Consultas / KPIs (“premios”):** `premiosmusicales.sql`  
- 🧩 **Diagrama relacional:** `relacion_entre_tablas.png`  
- 📊 **Presentación final (PDF):** `Proyecto_promo_59_modulo_2_equipo_3_ QUERY QUEENS PRESENTS Y´S AWARDS version comprimida.pdf`  
- 📒 **Notebooks (limpieza/transformación):** carpeta `ARCHIVOS .IPYNB/`  
- 📁 **CSVs de entrada:** carpeta `archivos.CSV/`

---

## Objetivo del proyecto

- Construir una base de datos relacional en **MySQL** con información de canciones, artistas, álbumes y géneros.
- Integrar datos procedentes de múltiples CSV (Spotify + Last.fm) y normalizarlos en un modelo.
- Diseñar una gala de premios basada en métricas objetivas (popularidad, playcount, oyentes, etc.).
- Practicar un flujo real de trabajo con Python (pandas) + SQL + VS Code + Git/GitHub.

> Dataset: ~2500 canciones (aprox.) de géneros como Reggaeton, Pop Latino, Funk, Rock Indie y Jazz (2010–2024).

---

## Arquitectura de datos (modelo relacional)

La base de datos `musica_db` contiene 4 tablas principales:

### `artistas`
- `Artista` (PK)
- `Playcount_LastFM` (BIGINT)
- `Listeners_LastFM` (BIGINT)
- `Biografia_Resumen` (TEXT)

### `albumes`
- `ID_Album` (PK)
- `Nombre_Album`
- `Año_Lanzamiento_Album`
- `Artista` (FK → `artistas`)

### `generos`
- `genero_id` (PK)
- `nombre_genero`

### `canciones`
- `ID_Spotify` (PK)
- `Nombre`
- `Año_lanzamiento`
- `ID_Album` (FK → `albumes`)
- `Artista` (FK → `artistas`)
- `genero_id` (FK → `generos`)
- `Popularidad` (INT)

### Diagrama de relaciones

<p align="center">
  <img src="relacion_entre_tablas.png" width="850" alt="Modelo relacional">
</p>

Este modelo permite responder preguntas como:
- ¿Qué artista domina cada género entre 2010 y 2024?
- ¿Qué álbum es el más consistente en popularidad?
- ¿Qué canciones son las más escuchadas según Last.fm?

---

## KPIs / Premios calculados (SQL orientado a decisión)

Las queries de `premiosmusicales.sql` están presentadas como “premios”, pero representan **métricas y rankings**. Ejemplos:

- 🏆 **Álbum atemporal (2010–2024):** álbum con popularidad sostenida a lo largo del periodo.
- 🔥 **Top Hits (2010–2024):** artista con mayor suma de popularidad / playcount.
- 💎 **Álbum más sólido:** álbum con mayor popularidad media de sus canciones.
- 🎭 **Álbum más variado:** mayor diversidad de géneros o colaboraciones.
- 🎼 **Género del año:** género con mayor popularidad media en cada año.

---

## Notebooks y datos (lo que hay en el repo)

### Notebooks (`ARCHIVOS .IPYNB/`)
- `reggaeton_codigo.ipynb`
- `latin_codigo.ipynb`
- `funk_codigo.ipynb`
- `Rock_Indie_codigo.ipynb`
- `jazz_codigo.ipynb`
- `fase2.ipynb`

### CSVs (`archivos.CSV/`)
- `reggaeton_data_2010_2024.csv`
- `latin_data_2010_2024.csv`
- `funk_data_2010_2024.csv`
- `indie_data_2010_2024.csv`
- `jazz_data_2010_2024.csv`

---

## Tecnologías utilizadas

- **Python** — limpieza/transformación (notebooks)
- **pandas, numpy** — consolidación y preparación de datos
- **MySQL** — creación de `musica_db`, normalización y consultas SQL
- **VS Code** — entorno de desarrollo
- **Git & GitHub** — control de versiones y colaboración entre 5 miembros

---

## Cómo reproducir el proyecto (paso a paso)

## 1) Clonar el repositorio

```bash
git clone https://github.com/Ruthpsegovia/da-project-promo-59-modulo-2-team-3.git
cd da-project-promo-59-modulo-2-team-3
```

## 2) Crear la base de datos

```sql
CREATE DATABASE musica_db;
```

## 3) Importar el dump (desde la raíz del repositorio)

```bash
mysql -u root -p musica_db < musica_db_dump.sql
```

## 4) Ejecutar las consultas (KPIs / “premios”)

1. Abre el archivo `premiosmusicales.sql`.
2. Ejecútalo sobre la base de datos `musica_db`.
3. Obtendrás rankings / ganadores por categoría y tablas de apoyo.

## 5) (Opcional) Revisar limpieza y preparación en notebooks

Abre los archivos `.ipynb` ubicados en la carpeta `ARCHIVOS .IPYNB/` y revisa/ejecuta la preparación previa a la carga en MySQL (según el flujo del proyecto).

## Estructura del repositorio

```text
.
├── ARCHIVOS .IPYNB/
│   ├── Rock_Indie_codigo.ipynb
│   ├── fase2.ipynb
│   ├── funk_codigo.ipynb
│   ├── jazz_codigo.ipynb
│   ├── latin_codigo.ipynb
│   └── reggaeton_codigo.ipynb
├── archivos.CSV/
│   ├── funk_data_2010_2024.csv
│   ├── indie_data_2010_2024.csv
│   ├── jazz_data_2010_2024.csv
│   ├── latin_data_2010_2024.csv
│   └── reggaeton_data_2010_2024.csv
├── Proyecto_promo_59_modulo_2_equipo_3_ QUERY QUEENS PRESENTS Y´S AWARDS version comprimida.pdf
├── README.md
├── musica_db_dump.sql
├── premiosmusicales.sql
└── relacion_entre_tablas.png
```

## Contribución (trabajo en equipo)

Proyecto realizado por el equipo **QUERY QUEENS** (5 miembros):

<p align="center">
  <img width="158" height="320" alt="Hannia" src="https://github.com/user-attachments/assets/8e90d244-b514-4cbb-b409-ebec8cd8903c" />
  <img width="222" height="215" alt="Cristina" src="https://github.com/user-attachments/assets/cf788289-0291-4fdd-8d3c-4ef41c3317f2" />
  <img width="220" height="300" alt="Ruth Pérez Segovia" src="https://github.com/user-attachments/assets/34d5480b-2beb-4600-a70d-d3fd1d66b055" />
  <img width="136" height="348" alt="Ruth Cuevas" src="https://github.com/user-attachments/assets/69797b64-f0ad-4b6a-8b43-d8ab68ddfe95" />
  <img width="212" height="218" alt="Rocío" src="https://github.com/user-attachments/assets/8e18da99-bcbe-4074-a8fe-9bc6dde5ec88" />
</p>

- **HANNIA CORENA** (Scrum Master) — coordinación, Git & documentación  
- **CRISTINA ARAGON** — extracción de datos y consolidación  
- **RUTH PÉREZ SEGOVIA** — modelado relacional y SQL  
- **RUTH CUEVAS** — limpieza avanzada & calidad de datos  
- **ROCIO SANCHEZ** — análisis de premios y storytelling  

## Limitaciones y mejoras futuras

- Las métricas dependen de la calidad y cobertura de los datos de Spotify/Last.fm.  
- Mejorable con carga incremental (ETL) y validación de calidad de datos.  
- Evolución natural: construir un dashboard de KPIs (Power BI/Tableau) consumiendo la BBDD o una tabla agregada.

<p align="center">
  <sub>Proyecto académico de bootcamp con foco en SQL para reporting, modelado relacional y storytelling basado en datos.</sub>
</p>
