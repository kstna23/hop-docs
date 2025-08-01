
# 📦 Datenproduktbeschreibung: `your_data_product_name`

## 🧭 1. Fachliche Domäne
- **Domäne:** `z. B. Customer Management / Produktion / Vertrieb`
- **Produktverantwortliches Team:** `Teamname oder Abteilung`
- **Kontakt:** `team@example.com`

---

## 🎯 2. Zweck & Mehrwert
> Beschreibe in 2–4 Sätzen, warum es dieses Datenprodukt gibt und welchen geschäftlichen oder analytischen Nutzen es bringt.

**Beispiel:**  
Dieses Datenprodukt liefert einen konsolidierten Blick auf alle Kundenprofile, inklusive Kaufverhalten, Loyalty-Status und Lifetime Value. Es unterstützt Kampagnen, Segmentierungen und personalisierte Empfehlungen.

---

## 👤 3. Zielgruppen & Konsumenten
- Fachabteilungen: `z. B. Marketing, Vertrieb, Service`
- Datenrollen: `z. B. Analyst*innen, Data Scientists, ML Engineers`
- Systeme: `z. B. Recommendation Engine, Dashboards`

---

## 📄 4. Hauptinhalte des Datenprodukts

| Attribut               | Beschreibung                                           |
|------------------------|--------------------------------------------------------|
| `customer_id`          | Eindeutige Kundenkennung                               |
| `loyalty_status`       | Aktueller Status im Treueprogramm                      |
| `lifetime_value`       | Berechneter Gesamtwert eines Kunden                    |
| `first_purchase_date`  | Zeitpunkt der ersten Bestellung                        |
| `region`               | Zuordnung zum geografischen Markt                      |

---

## 🔒 5. Datenschutz & Sicherheit
- **Personenbezogene Daten enthalten?** `Ja / Nein`
- **DSGVO-Relevant?** `Ja / Nein`
- **Sichtbar für:** `Nur autorisierte Rollen / Nur anonymisiert / Offen intern`
- **Spezielle Zugriffsrichtlinien:** `z. B. PII-Maskierung, Löschpflichten`

---

## 📈 6. Aktualität & Qualität
- **Aktualisierungsfrequenz:** `z. B. täglich, stündlich, in Echtzeit`
- **Datenerfassungszeitraum:** `z. B. ab 2020 bis heute`
- **Datenqualität:** `z. B. > 99% Felder vollständig, automatisierte Checks`
- **Letzter erfolgreicher Lauf:** `YYYY-MM-DD HH:MM`

---

## ⚙️ 7. Technische Details

- **Quellsysteme:** `z. B. SAP CRM, Kafka Events, Web-Tracking`
- **ETL/ELT-Werkzeug:** `z. B. dbt, Airflow, Talend, Azure Data Factory`
- **Datenbank/Ziellager:** `z. B. Snowflake, BigQuery, Delta Lake`
- **Verarbeitungstechnologie:** `z. B. Spark, SQL, dbt`
- **Transformationstyp:** `Batch / Streaming / Micro-Batch`
- **Wichtige Join-Operationen:**  
  - `JOIN customer_events USING (customer_id)`
  - `LEFT JOIN region_mapping ON zip_code = region_zip`
- **Businesslogik/Filter:**  
  - Nur aktive Kunden (Status = 'ACTIVE')  
  - Umsatz > 0 innerhalb der letzten 12 Monate

---

## 📂 8. Speicherstruktur
- **Physische Ablage / Pfad:** `z. B. s3://data/products/customer_profile/`
- **Tabellenname (Warehouse):** `z. B. prod.customer_profile_v1`
- **Schema-Versionierung:** `v1, v2 …`
- **Datenretention:** `z. B. 180 Tage (Query-fähig), Archiv 2 Jahre`

---

## 📎 9. Technische Dokumentation & Zugang

- [Schema-Dokumentation](https://yourcompany.com/schema/customer_profile)
- [ETL-Pipeline-Definition](https://git.example.com/your_team/etl_jobs/customer_profile_dag.py)
- [Transformation in dbt](https://git.example.com/your_team/dbt/models/customer_profile.sql)
- [Data Catalog-Eintrag](https://datahub.example.com/your_data_product_name)
- [Monitoring Dashboard (z. B. Grafana)](https://grafana.example.com/d/xyz/customer-profile)
- Ansprechpartner: `tech-lead@example.com`

---

## 🗺️ 10. Herkunft & Lineage
- **Quellen:** `CRM-Events, E-Commerce-Orders, Loyalty-Service`
- **ETL-Fluss:** `CRM → Raw Layer → Staging → Aggregation → Produkt`
- **Lineage-Tool:** `OpenLineage, Marquez, DataHub`
- **Change Impact:** dokumentiert im GitHub Repo (Contract-Tests)

---

## 🧪 11. Tests & Qualitätssicherung
- **Datenqualitätsregeln:** `z. B. NULL-Anteil < 1 %, IDs eindeutig`
- **Validierungsframework:** `Great Expectations, SodaSQL, dbt tests`
- **Monitoring:** z. B. Alerts bei Datenvolumenabweichung > 20%
