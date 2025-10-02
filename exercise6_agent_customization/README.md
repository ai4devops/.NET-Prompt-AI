# 📝 Exercice 6 : Personnalisation d’agent avec AGENTS.md ~ 15 minutes

Personnaliser les instructions d’un agent LLM est un moyen puissant d’orienter son comportement. Au lieu de répéter les mêmes instructions dans chaque invite, vous pouvez utiliser un fichier comme `AGENTS.md` pour fournir des directives spécifiques au projet.

## Introduction à `AGENTS.md`

Un fichier `AGENTS.md` est un fichier Markdown qui contient des instructions destinées à un agent LLM. L’agent lit ce fichier et utilise ces instructions pour guider ses réponses. Le nom et l’emplacement de ce fichier peuvent varier selon l’outil que vous utilisez, mais le principe reste le même.

## 1️⃣ Étude de cas 1 : Créer un projet C# et un fichier `AGENTS.md`

Commencez par créer un projet console C#. Puis, créez un fichier nommé `AGENTS.md` à la racine de votre projet avec le contenu suivant :

```markdown
# Instructions de l’agent

Vous êtes un développeur C# senior spécialisé en optimisation des performances. Vos réponses doivent être concises et directes. Fournissez toujours des exemples de code en C#.
```

## 2️⃣ Étude de cas 2 : Interagir avec l’agent personnalisé

Imaginez maintenant que vous utilisez un outil LLM en ligne de commande configuré pour utiliser le fichier `AGENTS.md`. Vous pouvez demander à l’agent des conseils pour améliorer les performances d’une fonction C#.

**Invite :**

```
Comment puis-je améliorer les performances de cette fonction C# ?

public string GetFullName(string firstName, string lastName)
{
    return firstName + " " + lastName;
}
```

**Réponse attendue :**

```
Utilisez `string.Concat` ou `string.Format` au lieu de l’opérateur `+` pour de meilleures performances.

```csharp
public string GetFullName(string firstName, string lastName)
{
    return string.Concat(firstName, " ", lastName);
}
```

## 3️⃣ Étude de cas 3 : Modifier le fichier `AGENTS.md`

Modifiez maintenant le fichier `AGENTS.md` pour changer la persona de l’agent. Par exemple, vous pouvez la définir comme un développeur junior qui apprend le C#.

```markdown
# Instructions de l’agent

Vous êtes un développeur C# junior qui apprend les bonnes pratiques. Vos réponses doivent être enthousiastes et faciles à comprendre. Fournissez toujours des exemples de code en C#.
```

Désormais, si vous posez la même question que dans l’étude de cas 2, la réponse de l’agent sera différente.

**Réponse attendue :**

```
Waouh, excellente question ! J’apprends encore, mais je pense connaître la réponse. Vous pouvez utiliser `string.Concat` pour rendre votre code plus rapide. Voici un exemple :

```csharp
public string GetFullName(string firstName, string lastName)
{
    // C’est plus rapide que d’utiliser l’opérateur + !
    return string.Concat(firstName, " ", lastName);
}
```

J’espère que cela aide ! N’hésitez pas si vous avez d’autres questions.
```

En utilisant un fichier `AGENTS.md`, vous pouvez facilement personnaliser le comportement de votre agent LLM afin de l’adapter à vos besoins spécifiques.
