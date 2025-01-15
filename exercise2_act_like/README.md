# 📝 Exercise2 - Act Like ~ 10 minutes

"Act like" involves asking the model to behave as a specific person or role. In this case, we use it to get advice on
developing features in .NET.

## 1️⃣ Use Case 1: Create a Prompt for the Model to Provide Steps for Developing a .NET Project and Highlight Key Points

Possible example:

```
Act like an experienced .NET developer. What should not be forgotten when developing a secure API in .NET?
```

Now it's your turn to integrate your prompt below: 👀

```
Create a prompt for the model to provide steps for developing a .NET project and highlight key points.
```

What was the response?

```markdown
As an experienced .NET developer, here’s what should not be forgotten when developing a secure API:

1. **Input Validation**: Use libraries like `FluentValidation` to validate incoming data and prevent SQL injection or
   other input-based attacks.
2. **Error Handling**: Implement consistent error handling so the API returns appropriate error messages without
   exposing sensitive information.
3. **Authentication and Authorization**: Implement authentication via JWT with `System.IdentityModel.Tokens.Jwt` and
   ensure users have appropriate permissions to access routes.
4. **Encryption of Sensitive Data**: Use libraries like `System.Security.Cryptography` to secure sensitive data,
   especially passwords, before storage.
5. **Security Testing**: Write unit and integration tests with tools like `xUnit` to ensure your API is secure and
   functions as expected.
```

## 2️⃣ Use Case 2: Create a Prompt for the Model to Assist by Acting as a Specialized Expert

Possible example:

```
Act like a web application security expert. What needs to be integrated into a .NET API to ensure compliance with OWASP standards?
```

Now it's your turn to integrate your prompt below: 👀

```
Create a prompt for the model to assist by acting as a specialized expert.
```

What was the response?

```markdown
As a web application security expert, here’s what should be integrated into a .NET API for OWASP compliance:

1. **Injection Prevention**: Use ORMs like `Entity Framework` to interact with your database and prevent SQL injection.
2. **Session Management Security**: Ensure JWT tokens are well-signed using `System.IdentityModel.Tokens.Jwt` and have a
   limited lifespan to prevent exploitation.
3. **Encryption of Sensitive Data**: All sensitive data such as passwords or personal information must be encrypted
   before storage using `System.Security.Cryptography`.
4. **Error Management Without Information Leakage**: Never return full errors to end users. Use middleware such as
   `ExceptionHandlerMiddleware` to return generic messages.
5. **Protect Against CSRF and XSS Attacks**: Use `AntiForgery` tokens and validate user input to prevent XSS attacks.

By following these recommendations, you’ll ensure compliance with OWASP’s best security practices.
```

## 3️⃣ Use Case 3: Compare Your Two Responses and Test Other Response Structures

Possible example:

```
Act like a Lead Dev .NET in a development team. What are the design principles to never forget when creating a new service in .NET?
```

Now it's your turn to integrate your prompt below: 👀

```
Compare your two responses and test other response structures.
```

What was the response?

```markdown
As a Lead Dev .NET, here are the design principles to never forget:

1. **SOLID Principles**: Ensure each module and function follows SOLID principles for maintainable and scalable code.
2. **Strict Types and Advanced Typing**: Use .NET's advanced typing features such as generics and union types to ensure
   code robustness.
3. **Testability**: Focus on writing modular and testable code. Each service should have unit and integration tests.
4. **Design Patterns**: Use suitable design patterns like the "Repository" pattern for database communication
   management.
5. **Clear Documentation**: Document each function and class to facilitate other developers’ work and ensure team
   consistency.
```

