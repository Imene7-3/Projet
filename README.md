```mermaid
flowchart LR
    %% --- SOURCES ---
    subgraph A["🗂️ Sources de données"]
        INSEE["INSEE – Recensement & revenus"]
        CROUS["CROUS – Logements étudiants"]
        DATAGOUV["Data.gouv.fr – Loyers & offres"]
        DREES["DREES – Conditions de vie des jeunes"]
    end

    %% --- TRAITEMENTS ---
    subgraph B["⚙️ Traitements"]
        CLEAN["Nettoyage et harmonisation des données"]
        MERGE["Croisement des sources"]
        INDIC["Création d’indicateurs logement"]
    end

    %% --- SORTIES ---
    subgraph C["📊 Résultats & diffusion"]
        CARTES["Cartes et graphiques interactifs"]
        RAPPORT["Rapport final & synthèse"]
    end

    %% --- FLUX ---
    INSEE --> CLEAN
    CROUS --> CLEAN
    DATAGOUV --> CLEAN
    DREES --> CLEAN
    CLEAN --> MERGE --> INDIC --> CARTES --> RAPPORT
