# 📝 Exercise 3 - Chain of Thought ~ 10 minutes

The “chain of thought” technique guides the model to produce a brief, structured plan before the final answer, compare options (self-consistency), and self-review (reflection) to improve quality. Here, we use it to generate .NET documentation. Prefer short, structured reasoning over a long monologue.

## 1️⃣ Use Case 1: Plan -> Documentation (explicit, concise reasoning)

Example prompt (replace the code with yours):

```text
Here is my .NET code:
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
Task:
1) Draft a 5-step numbered documentation plan (brief).
2) Then write the final documentation in Markdown.
Constraints:
- The plan must be concise (one line per step).
- Don’t include unnecessary code in the final documentation.
- Clearly separate "Plan" and "Final documentation".
```

Your turn—add your prompt below: 👀

```text
Create a prompt that forces the model to first produce a brief numbered plan, then the final documentation in Markdown, clearly separated into two sections.
```

What was the response?

```markdown
Plan (brief)
1) API goal
2) Endpoints and parameters
3) Request/response examples
4) Error codes
5) Security notes and limits

Final documentation
## Client Management API
### Goal
Minimal service to retrieve and update clients.

### Endpoints
- GET /clients/{clientId}
  - Parameters: clientId (string)
  - 200: "John Doe"
- POST /clients
  - 200: "Client updated!"

### Examples
- curl http://localhost:5000/clients/123
- curl -X POST http://localhost:5000/clients

### Errors
- 400/404 depending on input validation.

### Security and limits
- Add auth/https in prod; validate inputs; log requests.
```

## 2️⃣ Use Case 2: Self-consistency (multiple plans -> vote -> OpenAPI output)

Example prompt:

```text
Here is my .NET code:
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
Task:
1) Propose 3 alternative plans (A, B, C) for OpenAPI documentation (brief).
2) Choose the best plan via a short vote (one sentence).
3) Generate the final OpenAPI 3.0 according to the selected plan.

Constraints:
- Concise plans (max 5 bullets each).
- The vote must cite 1 criterion (coverage, clarity, conformance).
- Provide only YAML in the final output.
```

Your turn—add your prompt below: 👀

```text
Create a prompt that asks for 3 brief OpenAPI plans, a vote to select the best one, then generation of the final YAML.
```

What was the response?

```yaml
# Candidate plans (brief)
# A: Title/servers/schemas/paths/responses
# B: Title/detailed paths/response schemas/examples
# C: Title/paths/common errors/securitySchemes

# Vote: B better covers examples and response clarity.

openapi: 3.0.0
info:
  title: Client Management API
  version: 1.0.0
paths:
  /clients/{clientId}:
    get:
      summary: Retrieve a client
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
      summary: Update a client
      responses:
        '200':
          description: OK
          content:
            application/json:
              schema: { type: string }
              example: Client updated!
```

## 3️⃣ Use Case 3: Reflection -> Revision (structured critique then improvement)

Example prompt:

```markdown
Here is a first draft of documentation (to improve):
## Client Management API

### Introduction

This API service allows managing client information via two endpoints: one to get information on a specific client and one to update a client's information.

### Endpoints

#### 1. GET /clients/:clientId

- **Description**: Retrieves information about a client based on their ID.
- **Parameter**: `clientId` (string) – the client's identifier.
- **Example response**: John Doe

#### 2. POST /clients

- **Description**: Updates a client's information.
- **Example response**: Client updated!

### Usage

To use this API service, send HTTP requests to the specified endpoints using the base URL.
**Example usage with curl:**

# Retrieve client information

curl http://localhost:5000/clients/123

# Update a client

curl -X POST http://localhost:5000/clients -d "Client updated!"
Task:
1) Reflection (brief): list the top 5 gaps (bullets).
2) Fix plan (brief): bullets aligned to the gaps.
3) Revised documentation (final).

Constraints:
- Reflection and plan: concise (one line per bullet).
- Final documentation: complete yet compact.
- Clearly separate the 3 sections.
```

Your turn—add your prompt below: 👀

```text
Create a prompt that asks for a reflection phase (gaps), a fix plan, then a revised documentation.
```

What was the response?

```markdown
Reflection (gaps)
- No error codes or validation.
- Insufficient examples.
- Lacks context and usage limits.
- Parameters under-specified.
- Security not addressed.

Fix plan
- Add 400/404 and error messages.
- Extend curl examples.
- Add goals and constraints.
- Detail path/body parameters.
- Add note on auth/https.

Revised documentation
## Client Management API
### Context
Minimal API for read and update.

### Endpoints
- GET /clients/{clientId}
  - Parameters: clientId (string)
  - 200: "John Doe" | 404: Client not found
- POST /clients
  - 200: "Client updated!" | 400: Invalid data

### Examples
- curl http://localhost:5000/clients/123
- curl -X POST http://localhost:5000/clients

### Security
Use HTTPS; consider auth and rate limiting.
```

Feel free to experiment with other variants (step-by-step reasoning, checklists, quality criteria) and measure the impact on clarity and accuracy.