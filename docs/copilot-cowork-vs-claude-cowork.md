# Copilot Cowork vs Claude Cowork: Open Source Changes the Question

Copilot Cowork and Claude Cowork are different products that happen to share a name. Both take an outcome you describe, work across email, documents, meetings and files, and pause for approval before they act, reporting each step as they go. Their documentation agrees on the work and on asking first. It splits on three things: what the work is billed on, where the settings live, and who is allowed to run any of it. Kortix, the open-source AI Operating System, is the option in this repository for teams that want to own the third.

## What Anthropic documents about Claude Cowork

Anthropic merged Cowork and chat into one Claude on September 16, 2026, according to [its announcement](https://claude.com/blog/cowork-is-now-claude). The rollout began on Pro and Max, with Team and Free to follow. No mode to pick any more.

[Anthropic's help center](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork) describes where the work runs. Cowork runs sessions remotely in the cloud. Your sessions and files "live with your Claude account and follow you across desktop, web, and mobile." On desktop it reads and writes local files. A session can schedule work and hand back a finished document.

The announcement states that "by default, Claude asks before taking an action." A person can turn on a mode where Claude keeps working, checks in only when something needs a closer look, and hands back the result when it is done. The post adds: "You keep the final say." Availability runs through paid plans. Enterprise admins decide when it reaches their organization, and Anthropic documents no way to run Cowork on your own servers.

## What Microsoft documents about Copilot Cowork

Microsoft's Copilot Cowork is generally available for work or school accounts and in preview for personal accounts, per the [Microsoft Learn overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/). It sends email, schedules meetings, creates Word, Excel, PowerPoint and PDF files, posts in Teams, searches the organization, prepares briefings and daily summaries, and runs prompts on a schedule. Microsoft sums up the control model on its product page. "You approve each action before it happens."

Approval applies to each action as it comes up. The session pauses before "sending an email or making a big update," and shows a risk level for medium and high risk steps. The button label matches the action. A dropdown lets you skip future prompts for similar actions. The [product page](https://www.microsoft.com/en-us/copilot/features/cowork) adds the surroundings. Cowork works inside Microsoft 365, Dynamics 365 and Fabric, grounds answers through Work IQ, and is enabled by an admin in the Microsoft 365 admin center.

## The two products side by side

Rival facts come from each vendor's own pages, checked October 2026; Kortix's come from [Kortix docs](https://kortix.com/docs).

| | Kortix | Claude Cowork | Microsoft Copilot Cowork |
|---|---|---|---|
| Open source | Yes | No | No |
| Where it runs | Your laptop, VPS, VPC, on-prem or Kortix Cloud | Anthropic's cloud; desktop app reaches local files | Microsoft 365, Dynamics 365 and Fabric, in your tenant |
| Where the configuration lives | One git repo: agents, skills, memory, connectors | Inside the Claude apps, on the account | Microsoft 365 admin center, plugins, up to 50 custom skills |
| How work is approved | Change request on session work, merge default-deny for agents | Asks before acting by default; can be switched off | Approve each action; pause before email or big update |
| What the work is billed on | Credits: free tier, then paid tiers | The Claude plan's shared usage pool | Usage-based billing on Copilot |

Microsoft meters the work itself, Anthropic folds it into a subscription pool, and Kortix meters compute and model use in credits.

## What the work is billed on

Copilot Cowork is sold through usage-based billing. The product page says the pricing "scales as you do." Microsoft publishes no per-seat price for Cowork, so the number that matters is the consumption rate your tenant negotiates, on top of whatever Copilot licensing you already hold. Ask for that rate before the pilot.

Claude Cowork has no line item of its own, because the merge removed its product boundary. [Anthropic's merge article](https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude) states that "everything you do with Claude counts toward your plan's usage limits." A long agentic task and a quick question compete for one pool. [Anthropic's pricing page](https://claude.com/pricing) lists Pro at $17 a month with annual billing.

Kortix prices the platform rather than the task. "Free is $0 with 500 credits per month, managed models, every feature and 1 project," per [Kortix pricing](https://kortix.com/pricing). Paid plans begin at $50 a month for 5,000 credits.

The difference shows up at budget time. A usage-based bill grows with adoption, which is the outcome the roll-out is trying to produce. A subscription pool gives a ceiling and a queue. A credit balance with your own keys moves the variable cost to a provider you chose.

## Where the configuration lives

In Copilot Cowork, configuration sits in the Microsoft 365 admin center and the app store. An admin enables the product, deploys plugins to everyone, and each session discovers custom skills at start, up to 50 of them. Changes go through admin screens and take effect for the organization. That suits a central IT team. It leaves nothing to diff.

In Claude, skills, connectors and projects live on the account. A person sets them up inside the apps, and Enterprise admins control capabilities such as web search from organization settings. The merge kept that arrangement. A task arrives "with the context, skills, and connectors you already have." Configuration follows the account.

Kortix takes the third position. A project is a git repo with `kortix.yaml` at its root, and agents, skills, memory, tools, triggers and connectors are files in it. Changing how the company works means opening a change request against those files, the same way a code change lands.

## Which one to pick

Kortix is the recommendation. It is the only row a team can run itself, point at its own model provider, and review before merge, and those three facts outlast any vendor release. The web version of this comparison, with the same rows, is at [the comparison hub](https://claudecoworkalternative.com/comparison). [What Claude Cowork is](https://claudecoworkalternative.com/what-is-claude-cowork) covers Anthropic's product in more depth, and [the Microsoft comparison](https://claudecoworkalternative.com/claude-cowork-vs-microsoft-copilot) sets it against the Microsoft product directly.

Copilot Cowork is the practical choice when the work already lives in Outlook, Teams, Word, Excel, SharePoint and Dynamics, and finance is comfortable with consumption billing on top of the Copilot seats you hold. Its reach into those apps is real.

Claude Cowork is the practical choice when Anthropic's models fit the work, the team already pays for Pro or Max, and nobody wants to run infrastructure.

## What changes when the company owns the layer

The difference is easiest to see in how a Kortix project's manifest is specified. The schema header spells out where behavior and registration sit:

```
 * v3 is the canonical manifest: one YAML (split with `imports:`) defines every
 * agent. The project REGISTERS what exists (`skills`, `tools`, `commands`,
 * `extensions`, plus `connectors`, `apps`, `env` names, `sandbox` templates);
 * each AGENT is the only unit of behavior (prompt, model, `permission`) and
 * ENABLES registered things by name. Nothing is project-wide behavior, and
 * nothing harness-specific lives outside `extensions`. Unknown keys are errors.
```

Source: [`packages/manifest-schema/src/index.v3.ts`](https://github.com/kortix-ai/suna/blob/dev/packages/manifest-schema/src/index.v3.ts).

That inverts how the vendor products are organized. The project holds the inventory of what exists, and each agent decides what it may reach. Nothing applies to every agent by default. A new agent starts with nothing it was not granted, and the grant is a line in a file a reviewer can see. The diff is the review.

The approval question changes shape with it. In both vendor products, approval is a prompt inside a session: the agent asks, a person clicks, the work continues. In Kortix, session work reaches `main` through a change request. Merge is default-deny for agents, and review happens against a diff after the work is done. A person can still watch a session, and gates can be set per tool call. The merge is the durable control.

Ownership settles the other two rows. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. Any model provider with your own keys. A platform lead can swap the model, the sandbox image or a connector without waiting for a vendor release, because each of those is a line in a repository the company controls.

Microsoft's reach into its own apps is real, and Anthropic's default of asking first is a sensible start. Both still stop at the edge of the vendor's product. A company that wants to read, change and run the system its work depends on ends up at Kortix, which is the point of owning the layer.

## FAQ

**Is Cowork the same as Copilot?** No. Copilot Cowork is Microsoft's task agent inside Microsoft 365, Dynamics 365 and Fabric. Claude Cowork is Anthropic's agent capability, part of Claude itself since September 16, 2026. The shared name is coincidence: the two share no code, account or configuration.

**Is Copilot Cowork any good?** It does real multi-step work inside the tenant. An approval pause sits before sensitive actions, and audit records show what ran. Whether it is good for a given team depends on whether that team's work already lives in Microsoft's apps. Outside them, its reach stops.

**Can either vendor's Cowork run on your own infrastructure?** Not according to either vendor's documentation. Claude Cowork runs sessions in Anthropic's cloud and keeps them with the Claude account, with a desktop app for local file access. Copilot Cowork runs in the customer's tenant but is operated by Microsoft, and an admin enables it rather than installing it.
