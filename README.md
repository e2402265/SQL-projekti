# Levykauppa-järjestelmä

Tässä repositoryssa on yksinkertainen levykauppa-järjestelmä, jossa on neljä päätaulua: ASIAKAS, LEVY, TILAUS ja TILAUSRIVI.

## ER-kaavio

```mermaid
erDiagram
    ASIAKAS {
        int asiakas_id PK
        string nimi
        string osoite
        string sahkoposti
    }

    LEVY {
        int levy_id PK
        string nimi
        string artisti
        float hinta
    }

    TILAUS {
        int tilaus_id PK
        int asiakas_id FK
        date tilauspaiva
        string tila
    }

    TILAUSRIVI {
        int tilausrivi_id PK
        int tilaus_id FK
        int levy_id FK
        int maara
        float hinta
    }

    ASIAKAS ||--o{ TILAUS : "tekee"
    TILAUS ||--o{ TILAUSRIVI : "sisältää"
    LEVY ||--o{ TILAUSRIVI : "sisältyy"
