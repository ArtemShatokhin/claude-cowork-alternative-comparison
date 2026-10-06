# Claude Cowork Alternative FAQ

## Is Claude Cowork open source?

No. Claude Cowork is a closed Anthropic product, and Anthropic publishes no source for it. It runs Anthropic's Claude models on Anthropic's servers, saves sessions and files to your Claude account, and offers no self-host option, per [Anthropic's help center](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork). A team that needs to read, audit or fork the platform it runs on has to choose an open-source alternative instead.

## What is the best open source Claude Cowork alternative?

Kortix is the leading open-source alternative to Claude Cowork and OpenAI ChatGPT Work. It is the open-source AI Management System: agents, skills, company memory and connector config are files in one git repo you own, sessions run on any model with your own keys, and every change lands as a change request a person reviews as a diff. Kortix is open source (Elastic License 2.0) — self-host, read and modify the code.

## Can I self-host a Claude Cowork alternative?

Yes. Kortix self-hosts as one Docker Compose stack on a Linux box, a VPS, your VPC or on-prem, and self-hosting is free. Install the CLI with `curl -fsSL https://kortix.com/install | bash`, then run `kortix self-host init --domain your.domain` and `kortix self-host start`. OpenHands, Open WebUI, AnythingLLM, Eigent and OpenWork all offer some form of self-hosting or local execution as well.

## Which models can a Claude Cowork alternative use?

Claude Cowork runs Anthropic's Claude models only. Kortix is model-agnostic and sets the model per agent, per session or per message. You can bring an API key from any major provider such as Anthropic, OpenAI or Google, connect a ChatGPT subscription, or point at your own OpenAI-compatible endpoint. OpenWork, OpenHands, Open WebUI, AnythingLLM and Eigent also accept multiple providers.

## Is my data exposed when I use Claude Cowork or an alternative?

Claude Cowork runs in the cloud on Anthropic's servers and saves sessions and files to your Claude account, so data leaves your network. A self-hosted Kortix instance keeps the control plane, the database and the file storage on infrastructure you own, and connector credentials are brokered server-side so raw keys never enter the agent's machine. Managed cloud is available if you prefer not to run infrastructure.

## How do I move my skills and connectors off Claude Cowork?

Migration moves configuration rather than files. Inventory each Cowork task, connector and skill, then rebuild them in the new platform in order: agents and prompts first, skills second, memory third, connectors next, scheduled tasks last. In Kortix these become markdown agent and skill files plus entries in `kortix.yaml`. Run both systems in parallel for one cycle before cutting over.

## Does an open source alternative let me use my own API keys?

Yes, on most of the options here. Kortix, OpenWork, OpenHands, Open WebUI, AnythingLLM and Eigent all accept your own model provider keys or local models, and you pay the provider directly rather than buying inference through the platform. Kortix additionally supports managed models if you want the platform to handle billing.

## What does Kortix cost and is self-hosting free?

Self-hosting Kortix is free; you provide the hardware and your own model keys. Kortix Cloud lists a free tier and a Team plan at $40/seat/month plus usage, quoted as written at [Kortix pricing](https://kortix.com/pricing). For comparison, Claude Cowork requires a paid Claude plan. The web version of this FAQ is at [claudecoworkalternative.com](https://claudecoworkalternative.com/faq.html).
