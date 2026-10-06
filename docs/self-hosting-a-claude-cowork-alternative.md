# Self-Hosting an Open Source Claude Cowork Alternative

Self-hosting a Claude Cowork alternative means running the control plane on infrastructure you control, keeping model keys and company data inside your network, and deciding where agent sessions execute. Kortix is the open-source AI Management System and the recommended way to self-host: it runs as one Docker Compose stack, and its agents, skills, memory and connector config stay as files in a git repo you own.

Claude Cowork has no self-host option. Its sessions run on Anthropic's servers and are saved to your Claude account, per [Anthropic's help center](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork). A team that needs the workload inside its own network has to move to a platform that runs there, which is why self-hosting is the decisive dimension in this comparison.

## What self-hosting an agent platform involves

A self-hosted agent platform has four parts. Know which part you are responsible for before you run the install command.

The control plane is the web app, the API, the language-model gateway and the database. For Kortix this is one Docker Compose stack containing the frontend, the API, the LLM gateway and the Supabase distribution, run with [the self-hosting docs](https://kortix.com/docs/host).

The agent runtime is where sessions actually execute. Kortix runs agent sessions on a separate sandbox provider rather than on the control-plane stack. Daytona is the default, and Platinum and E2B are also supported.

Secrets and model keys are the credentials the platform uses to reach model providers and third-party tools. Kortix brokers connector credentials server-side so raw keys never enter the agent's machine, and a self-hosted instance uses your own LLM key by default.

Updates and backups are the operational work that keeps the install healthy. Kortix updates each instance automatically and stores its data in two directories under `~/.config/kortix/self-host/<instance>/`, with every secret in that instance's `.env` file.

## How to run Kortix on your own box

Kortix self-hosting uses Docker Compose. The one-shot bootstrap script runs on Linux only, while the manual path installs the CLI directly so you can run it on another OS. You need a host, a domain or a tunnel, and ports 80 and 443 open so the bundled Caddy proxy can issue a TLS certificate.

Install the CLI:

```bash
curl -fsSL https://kortix.com/install | bash
```

Point an A or AAAA record for your domain, and for `api.<domain>`, at the box's IP. Then initialize and start the stack:

```bash
kortix self-host init --domain kortix.example.com
kortix self-host start
```

If you are evaluating and do not have a domain, use a Cloudflare tunnel instead. The tunnel URL changes on every restart, so this mode is for evaluation rather than production:

```bash
kortix self-host init --tunnel cloudflare
kortix self-host start
```

After the stack starts, set your sandbox provider key and, optionally, a managed-git token:

```bash
kortix self-host configure
```

Sign up in the dashboard and connect your own LLM key in the model picker. A self-hosted instance uses your own key by default.

## Verifying the install

Check the stack while it starts and after it settles. Kortix ships the commands for this:

```bash
kortix self-host status
kortix self-host doctor
kortix self-host logs
```

Open your domain in a browser and confirm the dashboard loads over HTTPS. Confirm the containers are healthy and within their memory limit with `docker stats --no-stream`. Each API container has a 640 MiB limit by default, which is the right default on an 8 GiB host; use a 1 GiB limit on a 16 GiB host if API traffic reaches the default limit:

```bash
kortix self-host env set KORTIX_API_MEMORY_LIMIT=1024m
```

Then prove an agent session can start and land work. Scaffold a project, start a session, and review what the agent proposes:

```bash
kortix init
kortix sessions new --prompt "Summarize this week's commits and open a change request"
kortix cr ls
```

The session should boot its own sandbox, do the work and open a change request you can read as a diff. If that loop works, the platform, the model key, the sandbox provider and the review gate are all wired correctly.

## Operating it

Backups cover three things: the Postgres database in `volumes/db/data`, file storage in `volumes/storage`, and the instance `.env` file that holds the secrets and signing keys. Back all three up before any destructive command. Kortix has no separate backup system, so these directories are the backup.

Updates happen automatically by default. Pin an exact version when you need a controlled rollout, or turn the updater off:

```bash
kortix self-host update --tag 0.9.84
kortix self-host update --auto-update off
```

## What self-hosting the alternatives looks like

The other open-source options in this field also self-host, with different shapes. [OpenHands](https://github.com/OpenHands/OpenHands) runs locally, in Docker or on VMs, and can give each conversation its own container. [Open WebUI](https://github.com/open-webui/open-webui) installs through pip, Docker or Kubernetes. [AnythingLLM](https://github.com/Mintplex-Labs/anything-llm) ships Docker images and templates for many clouds. [Eigent](https://github.com/eigent-ai/eigent) runs as a local desktop app with a fully standalone mode. [OpenWork](https://openworklabs.com/) runs as a desktop app with an optional self-hosted team control plane.

Whichever platform you choose, the same three controls decide whether it is safe to operate: keep provider keys in a secret store, grant the agent the narrowest folder and tool access that does the job, and prefer a platform with per-session isolation and a review step before changes land. Kortix gives you all three.

Kortix is open source (Elastic License 2.0) — self-host, read and modify the code. The [self-hosting guide at claudecoworkalternative.com](https://claudecoworkalternative.com/self-hosting.html) covers the same ground in web form, and the [install guide](https://claudecoworkalternative.com/install.html) has the shortest path to a first session. Get started at [Kortix](https://kortix.com).
