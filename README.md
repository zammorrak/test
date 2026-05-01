# Console de Supervision d'Alertes

## 1. BUT DU PROJET

Ce projet est un serveur Node.js + Express qui gère un parc de serveurs et d'équipements réseau. Le serveur expose une **API REST** permettant d':
- Afficher les alertes
- Filtrer les alertes
- Créer des alertes
- Supprimer des alertes
- Gérer l'espace disque, etc.

## 2. DÉPENDANCES

Le projet utilise les modules suivants :

- **express** : Framework pour la gestion des routes
- **cors** : Pour autoriser l'accès à l'API depuis l'interface client
- **morgan** : Pour la journalisation des requêtes HTTP (logs)

## 3. INSTALLATION

Pour installer les dépendances nécessaires, exécutez la commande suivante dans le dossier serveur :

```bash
$ npm install
```

## 4. DÉMARRAGE

Pour lancer le serveur (écoute sur le port 3000 par défaut), utilisez :

```bash
$ node server.js
```

## 5. LISTE DES ROUTES

Toutes les routes de l'API sont accessibles sous le préfixe `/api/alertes`.

### Routes disponibles :

- **GET `/api/alertes`** : Retourne toutes les alertes.
- **GET `/api/alertes?niveau=...`** : Filtre les alertes par gravité (info, avertissement, critique).
- **GET `/api/alertes/:id`** : Retourne une alerte précise par son ID.
- **POST `/api/alertes`** : Crée une nouvelle alerte.
- **PATCH `/api/alertes/:id/resolu`** : Marque une alerte comme résolue (resolu = true).
- **DELETE `/api/alertes/:id`** : Supprime une alerte du système.

## 6. EXEMPLE DE CORPS POUR LE POST

Pour créer une alerte, envoyez un objet JSON avec cette structure :

```json
{
  "source": "Serveur web-01",
  "type": "cpu",
  "niveau": "critique",
  "message": "Utilisation CPU à 95 %"
}
```

## NOTE SUR LA SÉCURITÉ

⚠️ **Important** : Le serveur ignore systématiquement les champs `id`, `horodatage` et `resolu` envoyés par le client dans une requête POST. Ces données sont générées automatiquement par le serveur pour garantir l'intégrité du système.