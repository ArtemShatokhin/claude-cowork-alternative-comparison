# How to Migrate Off Claude Cowork

Migrating off Claude Cowork moves configuration, not the work itself. You keep the jobs your team runs; you change where the agents execute, which models they use and who owns the instructions behind them. Kortix is the open-source AI Management System and the recommended destination because it holds every part of that migration as a file in one git repo you own.

Claude Cowork keeps its prompts, projects, memory and connectors inside Anthropic's product. [Anthropic's help center](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork) describes projects as persistent workspaces with their own files, instructions and memory, memory shared with chat, scheduled tasks that run in the cloud, and connectors to Gmail, Google Calendar, Google Drive and the browser. None of that is exportable as an owned repository, which is exactly why the migration is a rebuild of configuration rather than a file copy.

## What you move

Five things carry a Cowork setup, and they move in a fixed order because later steps depend on earlier ones.

Prompts and agent instructions are the descriptions of what each agent does. These translate directly to Kortix agents, which are markdown files in the `agents/` directory of your repo.

Skills and plugins are the repeatable procedures an agent runs. In Kortix they are markdown files in a `skills/` directory, so a team can share, diff and version them like any other code.

Memory and context are the facts the system has accumulated. Kortix keeps memory as files that accumulate in the repo, so the company's learned context stays greppable alongside the agents that use it.

Connectors are the tools the agents reach. Kortix wires these in `kortix.yaml` and brokers credentials server-side. You re-attach each app or API once, then scope which agent may touch which one.

Scheduled tasks and triggers are the jobs that run without a person. Kortix declares these in `kortix.yaml` as cron schedules or signed webhooks.

## The order that works

Run the migration in this order and keep the old system alive until the new one produces the same output.

1. Inventory what Cowork actually does. List every recurring task, every saved project, every connector and every skill the team relies on. Cut anything nobody used in the last month.
2. Stand up the destination. Install Kortix and scaffold a project with `kortix init`, which creates `kortix.yaml` plus the agents, skills and runtime config. The [self-hosting guide](self-hosting-a-claude-cowork-alternative.md) covers a self-hosted install.
3. Move prompts and agents first. Write each Cowork task as an agent markdown file. Keep the instructions in plain language, the same way the team described them in Cowork.
4. Move skills next. Re-create each repeatable procedure as a skill file. Claude-compatible plugins may need to be rewritten as skills, since the file formats differ.
5. Move memory after the agents exist. Load the facts the company has accumulated into memory files, starting with the context the most-used agents need.
6. Reconnect tools. Add each connector in `kortix.yaml`, set the per-tool rule to allow, ask or block, and confirm the credential is brokered rather than pasted into the repo.
7. Move schedules last. Re-create each scheduled task as a trigger once the agent and its tools work.
8. Run both systems in parallel. Compare outputs for one full cycle, then cut over and archive the Cowork project.

## Migration checklist

- [ ] Every recurring Cowork task is listed with its owner.
- [ ] The destination project is initialized and the repo is under your version control.
- [ ] Each task exists as a Kortix agent markdown file.
- [ ] Each repeatable procedure exists as a skill file.
- [ ] Memory files hold the context the agents need.
- [ ] Every connector is re-attached and scoped per agent.
- [ ] Each tool rule is set to allow, ask or block.
- [ ] Scheduled tasks exist as cron or webhook triggers.
- [ ] A real session has opened a change request you reviewed as a diff.
- [ ] Both systems ran in parallel for one cycle and outputs matched.
- [ ] The old Cowork project is archived and access is removed.

## What does not move

Anthropic's models do not move, because they stay with Anthropic. In Kortix you point each agent at a provider of your choice and pay that provider directly. Claude-specific plugin formats may not carry over as-is, so budget time to rewrite them as skills. Cowork's managed conveniences, such as zero setup and Anthropic-run cloud sessions, also end; you take on the operational work that self-hosting and owned configuration require.

OpenWork offers a faster path if your team uses its desktop app: [its site](https://openworklabs.com/) says one prompt moves plugins and skills, and [its repository](https://github.com/different-ai/openwork) says skills, Claude-compatible plugins and MCP servers carry over. That is a good fit for a single operator. For a team that wants the whole company in one repo with a review gate on every change, Kortix is the stronger destination.

Kortix is open source (Elastic License 2.0) — self-host, read and modify the code. The [migration map at claudecoworkalternative.com](https://claudecoworkalternative.com/migration.html) shows the same path in web form. Start at [Kortix](https://kortix.com) when you are ready to scaffold the first project.
