# 📝 Exercice1 - Few-Shot Prompting ~ 10 minutes

Le few-shot prompting consiste à fournir au modèle quelques exemples d'entrées et de sorties pour lui indiquer le type
de tâche à effectuer. C'est une méthode simple et intuitive qui peut être utilisée pour diverses tâches de génération de
code ou de vérification de fonctionnalités.

## 1️⃣ Cas d'usage 1 : Créez un prompt qui demande au modèle de générer une fonction .NET

Exemple possible:

```
Créez une fonction qui vérifie si un nombre est pair ou impair.
la fonction isEvenOrOdd appelé avec le paramètre 3, comme ceci isEvenOrOdd(3), doit me retourner "odd"
la fonction isEvenOrOdd appelé avec le paramètre 4, comme ceci isEvenOrOdd(4), doit me retourner "even"
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un prompt qui demande au modèle de générer une fonction .NET
```

Quelle a été la réponse ?

```csharp
public string IsEvenOrOdd(int number)
{
    if (number % 2 == 0)
    {
        return "Even";
    }
    return "Odd";
}
```

## 2️⃣ Cas d'usage 2 : Créez un nouveau prompt qui demande au modèle de générer une fonction .NET avec une structure de réponse spécifique

Exemple possible:

```
Peux-tu créer une fonction .NET qui vérifie si un mot est un palindrome ?
Input: isPalindrome("radar") > Ouput: true
Input: isPalindrome("Bonjour") > Ouput: false
```

A vous de jouer en intégrant votre prompt ci-dessous: 👀

```
Créez un nouveau prompt qui demande au modèle de générer une fonction .NET avec une structure de réponse spécifique
```

Quelle a été la réponse ?

```csharp
public bool IsPalindrome(string word)
{
    char[] charArray = word.ToCharArray();
    Array.Reverse(charArray);
    string reversed = new string(charArray);
    return word == reversed;
}
```

## 3️⃣ Cas d'usage 3 : Comparez vos deux réponses et testez d'autres structures de réponses

N'hésitez pas à expérimenter avec différents prompts pour voir comment le modèle s'adapte et génère des solutions
variées.
