```mermaid
classDiagram
    class Logement {
        +int id
        +String adresse
        +float superficie
        +int nombreChambres
        +float loyerMensuel
        +String typeLogement
        +String description
        +disponibilite bool
    }

    class Appartement {
        +int etage
        +bool ascenseur
    }

    class Studio {
        +bool kitchenette
    }

    class Colocation {
        +int nombreColocataires
        +String reglesColocation
    }

    class Personne {
        +int id
        +String nom
        +String prenom
        +int age
        +String statut
        +rechercherLogement
    }

    class Contrat {
        +int id
        +Date dateDebut
        +Date dateFin
        +float montantLoyer
        +signerContrat
        +annulerContrat
    }

    class Proprietaire {
        +int id
        +String nom
        +String prenom
        +String contact
        +ajouterLogement
        +supprimerLogement
    }

    class ServiceLogement {
        +rechercherParType(typeLogement)
        +filtrerParLoyer(min, max)
        +reserverLogement(idLogement, idPersonne)
        +gererContrat(contrat)
    }

    class Paiement {
        +int id
        +Date datePaiement
        +float montant
        +payerLoyer
    }

    %% Relations
    Personne "1" -- "0..*" Contrat : signe
    Contrat "1" -- "1" Logement : concerne
    Proprietaire "1" -- "0..*" Logement : possède
    Appartement --|> Logement
    Studio --|> Logement
    Colocation --|> Logement
    Contrat "1" -- "0..*" Paiement : génère
    Personne "1" -- "0..*" Paiement : effectue
    ServiceLogement "1" -- "0..*" Logement : gère
    ServiceLogement "1" -- "0..*" Contrat : gère
