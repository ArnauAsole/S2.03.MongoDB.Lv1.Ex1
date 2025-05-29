# S2.03.MongoDB.Lv1.Ex1

Òptica “Cul d’Ampolla” – Model No Relacional amb MongoDB
Aquest projecte planteja dues aproximacions de disseny de dades orientades a documents per gestionar les operacions d'una òptica. L'objectiu és modelar les dades segons dues perspectives: la del client i la de les ulleres, utilitzant MongoDB.

### 📚 Project Overview
Aquest projecte es basa en una òptica fictícia anomenada “Cul d’Ampolla”, que necessita informatitzar la seva gestió. El model es construeix amb MongoDB i cobreix els següents aspectes:

Gestió de clients i recomanacions

Gestió de ulleres i les seves característiques

Control de proveïdors associats a ulleres

Registre de vendes amb informació de l’empleat/da i la data/hora

### 📂 Disseny de l’Estructura
🧪 Exercici 1 – Punt de vista del client 👓
Aquest model està centrat en l'experiència i l'activitat del client. Cada document representa un client, i incorpora dades relacionades com les vendes d’ulleres, recomanacions, i detalls de les ulleres comprades.


{
  "nom": "Laura Gómez",
  "adreça": "Carrer Major, 123, 2n 1a, Barcelona, 08001, Espanya",
  "telefon": "612345678",
  "email": "laura@example.com",
  "data_registre": "2023-05-10T00:00:00Z",
  "recomanat_per": "client_id_123",
  "vendes": [
    {
      "data_hora": "2024-01-15T11:23:00Z",
      "empleat": {
        "id": "emp001",
        "nom": "Jordi Mas"
      },
      "ulleres": {
        "marca": "Ray-Ban",
        "graduacio_vidre_esquerre": 1.5,
        "graduacio_vidre_dret": 1.0,
        "tipus_muntura": "metàl·lica",
        "color_muntura": "negre",
        "color_vidre_esquerre": "transparent",
        "color_vidre_dret": "transparent",
        "preu": 129.95,
        "proveidor": {
          "nom": "Visió Global",
          "telefon": "931234567",
          "fax": "931234568",
          "nif": "B12345678",
          "adreça": {
            "carrer": "Av. Diagonal",
            "numero": "456",
            "pis": "3",
            "porta": "2a",
            "ciutat": "Barcelona",
            "codi_postal": "08008",
            "pais": "Espanya"
          }
        }
      }
    }
  ]
}

🔍 Objectius:
Consultes centrades en clients i les seves compres.

Ideal per consultar recomanacions, historial de vendes, i empleats responsables.

### 🧪 Exercici 2 – Punt de vista de les ulleres 🕶️
Aquest model està estructurat al voltant del producte, en aquest cas les ulleres. Cada document representa unes ulleres concretes amb informació del proveïdor, client comprador i venedor.

{
  "marca": "Oakley",
  "graduacio_vidre_esquerre": 2.0,
  "graduacio_vidre_dret": 1.75,
  "tipus_muntura": "pasta",
  "color_muntura": "blau",
  "color_vidre_esquerre": "gris",
  "color_vidre_dret": "gris",
  "preu": 159.99,
  "proveidor": {
    "nom": "Òptics del Vallès",
    "telefon": "938765432",
    "fax": "938765433",
    "nif": "B98765432",
    "adreça": {
      "carrer": "C. Nou",
      "numero": "15",
      "pis": "Baixos",
      "porta": "",
      "ciutat": "Terrassa",
      "codi_postal": "08221",
      "pais": "Espanya"
    }
  },
  "client_comprador": {
    "id": "cli078",
    "nom": "Arnau Pujol"
  },
  "empleat_venda": {
    "id": "emp007",
    "nom": "Sara Martínez"
  },
  "data_venda": "2024-03-01T16:45:00Z"
}
🔍 Objectius:
Consultes centrades en les ulleres com a unitats venudes.

Ideal per fer anàlisi de productes, seguiment de proveïdors i control d’inventari venut.

🔍 Consultes d’exemple (MongoDB)
Tots els clients recomanats per algú:


db.clients.find({ "recomanat_per": { $ne: null } })
Ulleres venudes per un empleat específic:


db.ulleres.find({ "empleat_venda.nom": "Sara Martínez" })
Clients que han comprat ulleres d'una marca específica:


db.clients.find({ "vendes.ulleres.marca": "Ray-Ban" })
### 🛠️ Tools Used
MongoDB per a modelatge NoSQL

MongoDB Compass per visualització i execució de consultes

JSON Schema per definir documents

VS Code / Studio 3T per desenvolupament i proves

### 🔗 GitHub Repository 
📂 https://github.com/ArnauAsole/S2.03.MongoDB.Lv1.Ex1.git
