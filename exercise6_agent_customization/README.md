# 📝 Exercise 6: Agent customization with AGENTS.md ~ 15 minutes

Customizing an LLM agent’s instructions is a powerful way to steer its behavior. Instead of repeating the same guidance in every prompt, you can use a file like `AGENTS.md` to provide project-specific directives.

## Introduction to `AGENTS.md`

An `AGENTS.md` file is a Markdown file that contains instructions intended for an LLM agent. The agent reads this file and uses these instructions to guide its responses. The name and location of this file may vary depending on the tool you use, but the principle remains the same.

## 1️⃣ Case Study 1: Create a C# project and an `AGENTS.md` file

Start by creating a C# console project. Then, create a file named `AGENTS.md` at the root of your project with the following content:

```markdown
# Agent instructions

You are a senior C# developer specialized in performance optimization. Your answers must be concise and direct. Always provide code examples in C#.
```

## 2️⃣ Case Study 2: Interact with the customized agent

Imagine you’re using a CLI LLM tool configured to use the `AGENTS.md` file. You can ask the agent for advice to improve the performance of a C# function.

**Prompt:**

```text
How can I improve the performance of this C# function?

public string GetFullName(string firstName, string lastName)
{
    return firstName + " " + lastName;
}
```

**Expected answer:**

```markdown
Use `string.Concat` or `string.Format` instead of the `+` operator for better performance.

```csharp
public string GetFullName(string firstName, string lastName)
{
    return string.Concat(firstName, " ", lastName);
}
```
```

## 3️⃣ Case Study 3: Modify the `AGENTS.md` file

Now modify the `AGENTS.md` file to change the agent’s persona. For example, you can define it as a junior developer learning C#.

```markdown
# Agent instructions

You are a junior C# developer learning best practices. Your answers should be enthusiastic and easy to understand. Always provide code examples in C#.
```

From now on, if you ask the same question as in case study 2, the agent’s response will be different.

**Expected answer:**

```markdown
Wow, great question! I’m still learning, but I think I know the answer. You can use `string.Concat` to make your code faster. Here’s an example:

```csharp
public string GetFullName(string firstName, string lastName)
{
    // This is faster than using the + operator!
    return string.Concat(firstName, " ", lastName);
}
```

I hope that helps! Feel free to ask if you have more questions.
```


Using an `AGENTS.md` file, you can easily customize your LLM agent’s behavior to fit your specific needs.


````