# 📝 Exercice3 - Chaîne de raisonnement (Chain of thought) ~ 10 minutes

La technique de « chaîne de raisonnement » (chain of thought) consiste à guider le modèle à produire un plan structuré avant la réponse finale, à comparer des options (self-consistency) et à se relire (réflexion) pour améliorer la qualité. Ici, on l’utilise pour générer de la documentation .NET. Préférez un raisonnement bref et structuré plutôt qu’un long monologue.

## 1️⃣ Cas d'usage 1 : Plan -> Documentation (raisonnement explicite et concis)

Exemple de prompt (remplacez le code par le vôtre) :

```
Voici mon code .NET :
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/clients/{clientId}", (string clientId) =>
{
    return Results.Text("John Doe");
});

app.MapPost("/clients", () =>
{
    return Results.Text("Client updated!");
});

app.Run();
Tâche : 
1) Élabore un plan de documentation en 5 étapes numérotées (bref).
2) Rédige ensuite la documentation finale en Markdown.
Contraintes :
- Le plan doit être concis (une ligne par étape).
- N’inclus pas de code non nécessaire dans la documentation finale.
- Sépare clairement "Plan" et "Documentation finale".
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui force le modèle à produire d’abord un plan numéroté (bref), puis la documentation finale en Markdown, séparées en deux sections.
```

Quelle a été la réponse ?

```markdown
Plan (bref)
1) Objectif de l’API
2) Endpoints et paramètres
3) Exemples de requêtes/réponses
4) Codes d’erreur
5) Notes de sécurité et limites

Documentation finale
## API de gestion des clients
### Objectif
Service minimal pour récupérer et mettre à jour des clients.

### Endpoints
- GET /clients/{clientId}
  - Paramètres: clientId (string)
  - Réponse 200: "John Doe"
- POST /clients
  - Réponse 200: "Client updated!"

### Exemples
- curl http://localhost:5000/clients/123
- curl -X POST http://localhost:5000/clients

### Erreurs
- 400/404 selon la validation d’entrée.

### Sécurité et limites
- Ajouter auth/https en prod; valider inputs; journaliser.
```

## 2️⃣ Cas d'usage 2 : Self-consistency (plusieurs plans -> vote -> sortie OpenAPI)

Exemple de prompt :

```
Voici mon code .NET :
using Microsoft.AspNetCore.Builder;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Http;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

app.MapGet("/clients/{clientId}", (string clientId) =>
{
    return Results.Text("John Doe");
});

app.MapPost("/clients", () =>
{
    return Results.Text("Client updated!");
});

app.Run();
Tâche :
1) Propose 3 plans alternatifs (A, B, C) pour une documentation OpenAPI (brefs).
2) Choisis le meilleur plan via un vote court (une phrase).
3) Génère l’OpenAPI 3.0 final selon le plan retenu.

Contraintes :
- Plans concis (5 puces max chacun).
- Le vote doit citer 1 critère (couverture, clarté, conformité).
- Fournis uniquement le YAML en sortie finale.
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande 3 plans OpenAPI brefs, un vote pour sélectionner le meilleur, puis la génération du YAML final.
```

Quelle a été la réponse ?

```yaml
# Plans candidats (brefs)
# A: Titre/serveurs/schémas/paths/réponses
# B: Titre/paths détaillés/schemes de réponses/examples
# C: Titre/paths/erreurs communes/securitySchemes

# Vote: B couvre mieux les exemples et la clarté des réponses.

openapi: 3.0.0
info:
  title: API de gestion des clients
  version: 1.0.0
paths:
  /clients/{clientId}:
    get:
      summary: Récupérer un client
      parameters:
        - in: path
          name: clientId
          required: true
          schema: { type: string }
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema: { type: string }
              example: John Doe
  /clients:
    post:
      summary: Mettre à jour un client
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema: { type: string }
              example: Client updated!
```

## 3️⃣ Cas d'usage 3 : Réflexion -> Révision (critique structurée puis amélioration)

Exemple de prompt :

```
Voici une première version de documentation (à améliorer) :
## API de gestion des clients

### Introduction

Ce service API permet de gérer les informations des clients via deux endpoints : un pour obtenir des informations sur un
client spécifique et un pour mettre à jour les informations d’un client.

### Endpoints

#### 1. GET /clients/:clientId

- **Description** : Récupère les informations d'un client en fonction de son ID.
- **Paramètre** : `clientId` (string) – l’identifiant du client.
- **Exemple de réponse** : John Doe

#### 2. POST /clients

- **Description** : Met à jour les informations d'un client.
- **Exemple de réponse** : Client updated!

### Utilisation

Pour utiliser ce service API, envoyez des requêtes HTTP aux endpoints spécifiés en utilisant l’URL de base.
**Exemple d’utilisation avec curl :**

# Récupérer les informations d’un client

curl http://localhost:5000/clients/123

# Mettre à jour un client

curl -X POST http://localhost:5000/clients -d "Client updated!"
Tâche :
1) Réflexion (bref) : liste les 5 principales lacunes (puces).
2) Plan de correction (bref) : puces alignées sur les lacunes.
3) Documentation révisée (finale).

Contraintes :
- Réflexion et plan : concis (une ligne par puce).
- Documentation finale : complète mais compacte.
- Sépare clairement les 3 sections.
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande une phase de réflexion (lacunes), un plan de correction, puis une documentation révisée.
```

Quelle a été la réponse ?

```markdown
Réflexion (lacunes)
- Pas de codes d’erreur ni validation.
- Exemples insuffisants.
- Manque de contexte et de limites d’usage.
- Paramètres peu détaillés.
- Sécurité non abordée.

Plan de correction
- Ajouter 400/404 et messages d’erreur.
- Étendre les exemples curl.
- Ajouter objectifs et contraintes.
- Détailler paramètres path/body.
- Ajouter note sur auth/https.

Documentation révisée
## API de gestion des clients
### Contexte
API minimaliste pour lecture et mise à jour.

### Endpoints
- GET /clients/{clientId}
  - Paramètres: clientId (string)
  - 200: "John Doe" | 404: Client introuvable
- POST /clients
  - 200: "Client updated!" | 400: Données invalides

### Exemples
- curl http://localhost:5000/clients/123
- curl -X POST http://localhost:5000/clients

### Sécurité
Utiliser HTTPS; envisager auth et rate limiting.
```

N'hésitez pas à expérimenter d’autres variantes (raisonnement en étapes, checklists, critères de qualité) et à mesurer l’impact sur la clarté et l’exactitude des réponses.