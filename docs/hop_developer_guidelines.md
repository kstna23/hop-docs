
# 🛠️ Developer Guidelines für Data Engineers – Apache Hop

Diese Guidelines sollen sicherstellen, dass du mit Apache Hop standardisiert, wartbar und teamkompatibel arbeitest – im Kontext von Data Mesh und produktionsreifen Datenpipelines.

---

## 📦 1. Projektstruktur

- Verwende pro Datenprodukt ein **eigenes Hop-Projekt** (z. B. `customer_profile_project`).
- Gliedere logisch:
  - `pipelines/` für Hauptprozesse
  - `workflows/` für Steuerung, Validierung, Deployment
  - `metadata/` für Verbindungen, Umgebungen, Parameter

---

## 🧭 2. Naming Conventions

| Element         | Konvention                            | Beispiel                         |
|----------------|----------------------------------------|----------------------------------|
| Pipelines       | `p_<modul>_<funktion>`                | `p_orders_enrich_customers`      |
| Workflows       | `wf_<modul>_<zweck>`                  | `wf_orders_full_load`            |
| Transformations | `t_<beschreibung>`                    | `t_join_customer_orders`         |
| Files / Folder  | `lower_snake_case`                    | `metadata/databases/postgres.json` |

---

## ⚙️ 3. Technische Gestaltung

- Verwende **Parameter** statt harter Pfade (`${ENVIRONMENT}`, `${DB_CONNECTION}`)
- Vermeide globale Variablen in Pipelines – nutze übergebbare Werte
- Alle Datenbankverbindungen gehören in `metadata/databases/`
- Gruppiere Transformationsblöcke logisch mit Annotationen

---

## 🔁 4. Modulare Pipelines

- Baue **wiederverwendbare Subpipelines** (z. B. `clean_customer_data.hpl`)
- Trenne **Logik (Transformation)** und **Steuerung (Workflow)** klar
- Ein Workflow = genau **ein Jobziel** (Load, Sync, Export etc.)

---

## 🧪 5. Testing & Validierung

- Verwende **"Assert Rows"** zur Qualitätskontrolle in Pipelines
- Automatisiere Tests über CLI (`hop-run`) oder CI/CD-Tools
- Füge Validierungen am Anfang jeder Pipeline ein (Schema Check, Pflichtfelder)

---

## 📦 6. Deployment & Umgebungen

- Definiere Umgebungen in `metadata/environment/` (`dev`, `test`, `prod`)
- Deployment per CLI (`hop-run`, `hop-server`) oder orchestriert (z. B. Airflow, GitLab CI)
- Halte Umgebungsvariablen konsistent und dokumentiert

---

## 🔒 7. Sicherheit & Datenschutz

- Maskiere sensible Felder direkt in Pipelines (z. B. Hash von E-Mails)
- Keine Passwörter im Klartext – verwende Parameter + Secret Management
- DSGVO-relevante Pipelines klar kennzeichnen (`[PII]` im Namen)

---

## 📈 8. Logging & Monitoring

- Aktiviere detailliertes Logging (`log_level: Basic` oder `Detailed`)
- Leite Logs in zentrale Systeme (z. B. ELK, Grafana via Log-Dateien)
- Verwende eindeutige Run-IDs und schreibe Prozessmetadaten in Audit-Tabellen

---

## 🔗 9. Schnittstellen & Integration

- Eingänge: Datenbank, Flat Files, Kafka, REST, S3
- Ausgänge: Datenbank, S3, REST, Message Queue, Kafka
- Transformationsschritte klar dokumentieren (Schema, Erwartung, Typen) in Notes beschreiben

---

## 📚 10. Dokumentation & Versionierung

- Jede Pipeline & Workflow braucht eine `.md` Beschreibung (Zweck, Input, Output, Besonderheiten)
- Versioniere Pipelines in Git (`.hpl`, `.hwf`, `.json`) – keine Binärdateien!
- Git-Konventionen:
  - Feature-Branches: `feature/<beschreibung>`
  - Commits: `ADD`, `FIX`, `REFACTOR`

---

## 🧠 Tipps

- Nutze `Hop Gui` für visuelles Debugging – aber speichere sauber versionierte Dateien
- Erzeuge `preview`-Schritte für komplexe Transformationsketten
- Vermeide unnötige Lookups – arbeite mit vorbereiteten Joins und Caching

---

## 🔗 Nützliche Links

- [Apache Hop Doku](https://hop.apache.org/manual/latest/)
- [CLI Referenz](https://hop.apache.org/manual/latest/cli/hop-run/)
- [GitHub Best Practices](https://github.com/apache/hop)

---

Diese Richtlinien stellen sicher, dass Apache Hop in einem Data Mesh-Umfeld **skalierbar**, **teamfähig** und **produktionstauglich** eingesetzt wird.
