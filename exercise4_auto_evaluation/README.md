# 📝 Exercice4 - Auto-évaluation ~ 10 minutes

L'auto-évaluation consiste à demander au modèle de s'évaluer lui-même en utilisant des critères spécifiques. Dans cet
exercice, nous appliquons cette méthode à des scénarios en .NET.

## 1️⃣ Cas d'usage 1 : Créez un prompt qui demande au modèle de dresser une liste d’éléments exhaustifs pour tester un composant .NET

Exemple possible:

```.NET
// Fonction qui valide le format d'une adresse e-mail
using System.Text.RegularExpressions;

public class EmailUtils
{
    public static bool ValidateEmail(string email)
    {
        string emailRegex = @"^[^\s@]+@[^\s@]+\.[^\s@]+$";
        return Regex.IsMatch(email, emailRegex);
    }
}

Dresse une liste d'éléments pour tester la fonction validateEmail en .NET.
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle de dresser une liste d’éléments exhaustifs pour tester une fonction .NET.
```

Quelle a été la réponse ?

```
Voici une liste d'exemples de chaînes de texte pour tester la fonction validateEmail :

1. "test@example.com" (Valide)
2. "user@domain.co.uk" (Valide)
3. "invalid-email" (Non valide)
4. "test@.com" (Non valide)
5. "name@domain@domain.com" (Non valide)
6. "user@domain.c" (Valide mais limite)
7. "user@sub.domain.com" (Valide)
8. "" (Chaîne vide, non valide)
9. "plainaddress" (Non valide)
10. "user@domain..com" (Non valide)

Il est important de couvrir ces cas pour vérifier les limites et l'efficacité de la fonction validateEmail.
```

## 2️⃣ Cas d'usage 2 : Demandez au modèle s’il peut donner plus de possibilités

Exemple possible:

```
Peux-tu fournir d'autres exemples de chaînes à tester pour la fonction validateEmail ?
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Demandez au modèle s’il peut donner plus de possibilités.
```

Quelle a été la réponse ?

```
Bien sûr ! Voici quelques autres exemples pour élargir la couverture des tests :

11. "email@123.123.123.123" (Valide, adresse IP)
12. "user@[IPv6:2001:db8::1]" (Valide, IPv6)
13. ".user@domain.com" (Non valide, point au début)
14. "user@domain.web" (Valide, domaine personnalisé)
15. "user@domain" (Non valide, domaine incomplet)
16. "user@.domain.com" (Non valide, point après le @)
17. "user@domain..com" (Non valide, double point)

Ces exemples supplémentaires permettent de tester des cas moins courants mais potentiellement problématiques pour la validation des e-mails.
```

## 3️⃣ Cas d'usage 3 : Demandez au modèle de s'auto-évaluer et d'améliorer sa réponse

Exemple possible:

```
La liste de chaînes est-elle suffisante pour tester entièrement la fonction validateEmail ? Sinon, comment peut-elle être améliorée ?
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Demandez au modèle de s'auto-évaluer et d'améliorer sa réponse.
```

Quelle a été la réponse ?

```
La liste fournie couvre de nombreux cas courants, mais elle peut être améliorée en ajoutant des cas spécifiques aux normes actuelles des e-mails et en prenant en compte certaines configurations plus rares. Voici des points d'amélioration potentiels :

1. **Cas de caractères internationaux** : Ajouter des e-mails avec des caractères Unicode pour tester si la fonction peut gérer des noms d'utilisateur ou des domaines dans d'autres alphabets.
    - Exemple : "名@例.com" (Valide)
2. **Cas de plus de 64 caractères avant le symbole @** : Les adresses e-mail peuvent avoir un maximum de 64 caractères avant le @.
    - Exemple : "longemailaddresslongemailaddresslongemailaddresslongemailaddress@domain.com" (Valide)
3. **Cas de domaine sans extension** : Tester des domaines qui n'ont pas d'extensions de domaine traditionnelles.
    - Exemple : "user@localhost" (Potentiellement valide dans certains environnements)
En prenant en compte ces cas supplémentaires, vous obtiendrez une validation plus complète de la fonction validateEmail.
```
