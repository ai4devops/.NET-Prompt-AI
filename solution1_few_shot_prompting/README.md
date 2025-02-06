# 📝 Exercise1 - Few-Shot Prompting ~ 10 minutes

Few-shot prompting involves providing the model with a few examples of inputs and outputs to indicate the type of task
to perform. It's a simple and intuitive method that can be used for various tasks like code generation or feature
verification.

## 1️⃣ Use Case 1: Create a Prompt for the Model to Generate a .NET method

Possible example:

```
Create a method that checks if a number is even or odd.
The method isEvenOrOdd called with the parameter 3, like this isEvenOrOdd(3), should return "odd"
The method isEvenOrOdd called with the parameter 4, like this isEvenOrOdd(4), should return "even"
```

Now it's your turn to integrate your prompt below: 👀

```
Generate a method in C# that accept a number and return odd if it is odd or even of it is even
```

What was the response?

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

## 2️⃣ Use Case 2: Create a New Prompt for the Model to Generate a .NET method with a Specific Response Structure

Possible example:

```
Can you create a .NET method that checks if a word is a palindrome?
Input: isPalindrome("radar") > Output: true
Input: isPalindrome("Bonjour") > Output: false
```

Now it's your turn to integrate your prompt below: 👀

```
Generate a C# method that take a string in parameter and can be read in both ways like radar or kayak
```

What was the response?

```csharp
public bool IsPalindrome(string word)
{
    char[] charArray = word.ToCharArray();
    Array.Reverse(charArray);
    string reversed = new string(charArray);
    return word == reversed;
}
```

## 3️⃣ Use Case 3: Compare Your Two Responses and Test Other Response Structures

Feel free to experiment with different prompts to see how the model adapts and generates varied structures or solutions.
