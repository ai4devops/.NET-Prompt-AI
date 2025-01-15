# 📝 Exercise4 - Self-Evaluation ~ 10 minutes

Self-evaluation involves asking the model to assess itself using specific criteria. In this exercise, we apply this
method to .NET scenarios.

## 1️⃣ Use Case 1: Create a Prompt for the Model to List Comprehensive Items to Test a .NET method

Possible example:

```csharp
// Method that validates an email address
using System.Text.RegularExpressions;

public class EmailUtils
{
    public static bool ValidateEmail(string email)
    {
        string emailRegex = @"^[^\s@]+@[^\s@]+\.[^\s@]+$";
        return Regex.IsMatch(email, emailRegex);
    }
}
Create a list of items to test the validateEmail method in .NET

```

Now it's your turn to integrate your prompt below: 👀

```
Create a prompt for the model to list comprehensive items to test a .NET method.
```

What was the response?

```
Here is a list of example strings to test the validateEmail method:
1. "test@example.com" (Valid)
2. "user@domain.co.uk" (Valid)
3. "invalid-email" (Invalid)
4. "test@.com" (Invalid)
5. "name@domain@domain.com" (Invalid)
6. "user@domain.c" (Valid but borderline)
7. "user@sub.domain.com" (Valid)
8. "" (Empty string, invalid)
9. "plainaddress" (Invalid)
10. "user@domain..com" (Invalid)
It is important to cover these cases to check the boundaries and effectiveness of the validateEmail method.
```

## 2️⃣ Use Case 2: Ask the Model if It Can Provide More Possibilities

Possible example:

```
Can you provide other examples of strings to test the validateEmail method?
```

Now it's your turn to integrate your prompt below:  👀

```
Ask the model if it can provide more possibilities.
```

What was the response?

```
Certainly! Here are some additional examples to broaden test coverage:
11. "email@123.123.123.123" (Valid, IP address)
12. "user@[IPv6:2001:db8::1]" (Valid, IPv6)
13. ".user@domain.com" (Invalid, leading dot)
14. "user@domain.web" (Valid, custom domain)
15. "user@domain" (Invalid, incomplete domain)
16. "user@.domain.com" (Invalid, dot after @)
17. "user@domain..com" (Invalid, double dot)
These additional examples allow testing of less common but potentially problematic cases for email validation.
```

## 3️⃣ Use Case 3: Ask the Model to Self-Evaluate and Improve Its Response

Possible example:

```
Is the list of strings sufficient to fully test the validateEmail method? If not, how can it be improved?
```

Now it's your turn to integrate your prompt below: 👀

```
Ask the model to self-evaluate and improve its response.
```

What was the response?

```
The list provided covers many common cases, but it can be improved by adding cases specific to current email standards and considering some rarer configurations. Here are potential improvements:
1. **International Character Cases**: Add emails with Unicode characters to test if the method can handle usernames or domains in other alphabets.
   - Example: "名@例.com" (Valid)
2. **More than 64 Characters Before the @ Symbol**: Email addresses can have up to 64 characters before the @.
   - Example: "longemailaddresslongemailaddresslongemailaddresslongemailaddress@domain.com" (Valid)
3. **Domain Without Extension Case**: Test domains that do not have traditional domain extensions.
   - Example: "user@localhost" (Potentially valid in some environments)
By considering these additional cases, you will achieve more comprehensive validation of the validateEmail method.
```
