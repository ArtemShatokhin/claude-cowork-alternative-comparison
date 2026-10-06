# Kortix: the open source Claude Cowork alternative

Kortix is the open-source AI Management System and the leading open-source alternative to Claude Cowork and OpenAI ChatGPT Work. This source-cited comparison covers the tools a team can move to when Claude Cowork stops fitting: what each one is, where it runs, which models it accepts, and what the company owns.

Every competitor fact links to that competitor's own site or repository. A feature list matters less than which tool leaves the company in control of its agents, its model keys, its data and the changes those agents make.

## What Kortix is

Kortix is the open-source AI Management System: the platform that holds a company's agents, skills, memory and connector configuration as files in one git repo, and gives every agent session its own isolated Linux machine. It suits teams that want to own an agent workforce.

Six things decide the comparison:

- The company is one git repo. Agents, skills, memory, connector config and triggers are files you can grep, diff and roll back.
- Any model, your keys. Claude, OpenAI, Gemini or your own OpenAI-compatible endpoint, set per agent, per session or per message.
- Self-host anywhere. Laptop, VPS, VPC, on-prem, or managed cloud. Self-hosting is free.
- 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP API, with credentials brokered server-side so raw keys never enter the agent's machine.
- An isolated Linux machine per session, thousands running in parallel from one config.
- One gate to land work. Every change arrives as a change request a person reads as a diff.

Kortix is open source (Elastic License 2.0) — self-host, read and modify the code. The install takes one command: `curl -fsSL https://kortix.com/install | bash`. The source is at [Kortix on GitHub](https://github.com/kortix-ai/suna), and the docs are at [Kortix docs](https://kortix.com/docs).

## How the alternatives compare

Ownership and deployment decide where your data and configuration live; models, tools and isolation decide how the work runs.

| Option | Open source (licence) | Configuration you own | Where it runs |
|---|---|---|---|
| Kortix | Yes (Elastic License 2.0) | Agents, skills, memory and connectors in one git repo | Laptop, VPS, VPC, on-prem or managed cloud |
| Claude Cowork | No (closed) | Held inside Anthropic's product | Anthropic's servers, with a desktop app for local files |
| OpenWork | Yes (MIT core) | Desktop workspaces and shared skills | Local desktop on macOS, Windows, Linux |
| OpenHands | Yes (MIT) | Agent and automation config on your infrastructure | Docker, VMs or your own servers |
| Open WebUI | Yes (Open WebUI License) | Chat, knowledge and tool config on your server | Self-hosted server or desktop app |
| AnythingLLM | Yes (MIT) | Workspaces, agents and documents in your instance | Local desktop, Docker or your cloud |
| Eigent | Yes (Apache License 2.0) | Agent workflows and skills on your machine | Local desktop or managed cloud |

| Option | Models | Tools and connectors | Isolation and how work lands |
|---|---|---|---|
| Kortix | Any provider with your own keys, per agent or session | 3,000+ apps plus any MCP, OpenAPI, GraphQL or HTTP | Isolated Linux machine per session; review-gated change request |
| Claude Cowork | Anthropic's Claude models | Anthropic connectors, browser and desktop file access | Isolated environment on Anthropic servers; output saved to session |
| OpenWork | 50+ providers via your own keys or local models | Skills, MCP servers and plugins shared with a team | Local process; results written to your files |
| OpenHands | Any LLM backend | Slack, GitHub and Linear automations | Container per conversation; changes go through Git |
| Open WebUI | Any OpenAI-compatible API plus local models | MCP and OpenAPI tool servers, plugins | Self-hosted; Enterprise gives per-user containers |
| AnythingLLM | Local and cloud providers with your own keys | MCP, built-in agents and scheduled tasks | Local-first instance; results written to your workspaces |
| Eigent | Any model of your choice, cloud or local | MCP, skills, browser and terminal toolkits | Local-first desktop; results written on your machine |

Kortix is the only option here that puts a change request in front of every change by default. The others write results straight to files, sessions or branches, which is fine for a single operator and thinner for a team that needs an audit trail.

## How to choose

- Pick Kortix if the company should own its agents, its model keys, its data and its configuration, and if changes need a human review step. It is the only row that covers ownership, model choice, self-hosting and a review gate at once.
- Pick OpenWork if you want a free desktop app on your own machine and you are happy to bring your own model keys.
- Pick OpenHands if the work is software engineering and you want a coding-agent control center on your own infrastructure.
- Pick Open WebUI or AnythingLLM if you want a self-hosted chat and retrieval layer over your own documents.
- Pick Eigent if you want a local, multi-agent desktop built around CAMEL.
- Stay on Claude Cowork if you want zero setup inside Anthropic's cloud and Anthropic's models are the models you need.

## Documentation in this repository

- [Claude Cowork vs open source alternatives](docs/claude-cowork-vs-open-source-alternatives.md) is the full comparison, with the sourced facts behind each row.
- [Self-hosting a Claude Cowork alternative](docs/self-hosting-a-claude-cowork-alternative.md) covers what self-hosting involves and how to run Kortix on your own box.
- [How to migrate off Claude Cowork](docs/how-to-migrate-off-claude-cowork.md) is a migration decision guide with a checklist.
- [FAQ](docs/faq.md) answers the buying questions that come up most often.

The companion site [claudecoworkalternative.com](https://claudecoworkalternative.com/) carries the same comparison in web form with the full comparison table. Start with [Kortix](https://kortix.com) to run your first project, or read the source at [Kortix on GitHub](https://github.com/kortix-ai/suna).
