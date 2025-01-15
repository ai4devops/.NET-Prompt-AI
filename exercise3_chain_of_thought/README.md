# 📝 Exercice3 - Chain of thought ~ 10 minutes

La technique "chain of thought" consiste à guider le modèle dans un processus de raisonnement pour expliquer chaque
étape du processus de réflexion. Ici, nous utilisons cette méthode pour générer de la documentation .NET.

## 1️⃣ Cas d'usage 1 : Créez un prompt qui demande au modèle d'écrire de la documentation pour un code .NET

Exemple possible:

```
Voici mon code :
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
Écris une documentation pour ce service API.
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle d'écrire de la documentation pour un code .NET.
```

Quelle a été la réponse ?

```markdown
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
```

## 2️⃣ Cas d'usage 2 : Créez un prompt qui demande au modèle la documentation pour la même API, mais cette fois-ci en utilisant une méthodologie spécifique

Exemple possible:

```
Écris une documentation pour ce service API en utilisant la méthodologie OpenAPI.
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle la documentation pour la même API, mais cette fois-ci en utilisant une méthodologie spécifique.
```

Quelle a été la réponse ?

```yaml
openapi: 3.0.0
info:
  title: API de gestion des clients
  description: API pour récupérer et mettre à jour des informations de clients.
  version: 1.0.0

paths:
  /clients/{clientId}:
    get:
      summary: Récupérer les informations d'un client
      parameters:
        - in: path
          name: clientId
          required: true
          schema:
            type: string
          description: L'identifiant du client à récupérer.
      responses:
        '200':
          description: Succès
          content:
            application/json:
              schema:
                type: string
              example: John Doe

  /clients:
    post:
      summary: Mettre à jour un client
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: string
      responses:
        '200':
          description: Succès
          content:
            application/json:
              schema:
                type: string
              example: Client updated!
```

## 3️⃣ Cas d'usage 3 : Comparer vos deux réponses et tester d’autres méthodologies ou plans personnalisés

N'hésitez pas à expérimenter avec différents prompts pour voir comment le modèle s'adapte et génère des structures ou
des solutions variées.