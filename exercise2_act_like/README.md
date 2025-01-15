# 📝 Exercice2 - Act Like ~ 10 minutes

L'act like consiste à demander au modèle de se comporter comme une personne ou un rôle spécifique.
Dans ce cas, nous l'utilisons pour obtenir des conseils dans le développement de fonctionnalités en .NET.

## 1️⃣ Cas d'usage 1 : Créez un prompt qui demande au modèle de vous donner les étapes du développement d'un projet .NET et de souligner les points d'attention.

Exemple possible:

```
Agis comme un développeur .NET expérimenté. Que ne faut-il pas oublier pour développer une API sécurisée en .NET ?
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle de vous donner les étapes du développement d'un projet .NET et de souligner les points d'attention.
```

Quelle a été la réponse ?

```markdown
En tant que développeur .NET expérimenté, voici ce qu'il ne faut pas oublier pour développer une API sécurisée :

1. **Validation des entrées** : Utilisez des bibliothèques comme `FluentValidation` pour valider les données entrantes
   et empêcher les injections SQL ou autres attaques basées sur les entrées utilisateur.
2. **Gestion des erreurs** : Implémentez une gestion d'erreurs cohérente pour que l'API renvoie des messages d'erreur
   appropriés sans exposer d'informations sensibles.
3. **Authentification et autorisation** : Mettez en place une authentification via JWT avec
   `System.IdentityModel.Tokens.Jwt` et vérifiez que les utilisateurs disposent des autorisations appropriées pour
   accéder aux routes.
4. **Chiffrement des données sensibles** : Utilisez des bibliothèques comme `System.Security.Cryptography` pour
   sécuriser les données sensibles, notamment les mots de passe, avant de les stocker.
5. **Tests de sécurité** : Écrivez des tests unitaires et des tests d'intégration avec des outils comme `xUnit` pour
   vous assurer que votre API est sécurisée et fonctionne comme prévu.

```

## 2️⃣ Cas d'usage 2 : Créez un prompt qui demande au modèle de vous aider en agissant en tant qu’expert spécialisé.

Exemple possible:

```
Agis comme un expert en sécurité des applications web. Que faut-il absolument intégrer dans une API .NET pour qu'elle soit conforme aux standards OWASP ?
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle de vous aider en agissant en tant qu’expert spécialisé.
```

Quelle a été la réponse ?

```markdown
En tant qu'expert en sécurité des applications web, voici ce qu'il faut intégrer dans une API .NET pour être conforme
aux standards OWASP :

1. **Prévention des injections** : Utilisez des ORM comme `Entity Framework` pour interagir avec votre base de données
   et éviter les injections SQL.
2. **Sécurisation de la gestion des sessions** : Assurez-vous que les tokens JWT sont bien signés et que leur durée de
   vie est limitée pour éviter leur exploitation.
3. **Chiffrement des données sensibles** : Toutes les données sensibles comme les mots de passe ou les informations
   personnelles doivent être chiffrées avant stockage.
4. **Gestion des erreurs sans fuite d'informations** : Ne retournez jamais les erreurs complètes aux utilisateurs
   finaux. Utilisez un middleware de gestion d'erreurs tel que `ExceptionHandlerMiddleware` pour renvoyer des messages
   génériques.
5. **Protégez contre les attaques CSRF et XSS** : Utilisez des tokens `AntiForgery` et vérifiez les entrées utilisateur
   pour prévenir les attaques XSS.

En suivant ces recommandations, vous assurerez une conformité aux meilleures pratiques de sécurité selon OWASP.
```

## 3️⃣ Cas d'usage 3 : Comparez vos deux réponses et testez d'autres structures de réponses

Exemple possible:

```
Agis comme un Lead Dev .NET dans une équipe de développement. Quels sont les principes de conception à ne jamais oublier lors de la création d'un nouveau service en .NET ?
```

A vous de jouer en intégrant votre prompt ci-dessous:

```
Comparez vos deux réponses et testez d'autres structures de réponses
```

Quelle a été la réponse ?

```markdown
En tant que Lead Dev .NET, voici les principes de conception à ne jamais oublier :

1. **Principes SOLID** : Assurez-vous que chaque module et fonction suive les principes SOLID pour un code maintenable
   et évolutif.
2. **Types stricts et typage avancé** : Utilisez les fonctionnalités de typage avancées de .NET comme les types
   génériques et les unions de types pour assurer la robustesse du code.
3. **Testabilité** : Concentrez-vous sur l'écriture de code modulaire et testable. Chaque service devrait avoir des
   tests unitaires et d'intégration.
4. **Modèles de conception** : Utilisez des modèles de conception adaptés tels que le pattern "Repository" pour gérer la
   communication avec la base de données.
5. **Documentation claire** : Documentez chaque fonction et chaque classe pour faciliter le travail des autres
   développeurs et assurer la cohérence dans l'équipe.
```

