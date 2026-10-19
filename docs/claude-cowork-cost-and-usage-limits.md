# Claude Cowork cost at ten people, and what open source changes

Claude Cowork has no price of its own. Every Cowork task draws from the same plan usage pool as an ordinary chat, so the seat line on the invoice is arithmetic and the usage line is the variable. This page prices ten people on every Claude plan, shows where the pool becomes the bill, and compares that shape with Kortix, the open-source alternative that prices credits instead of seats.

## What the September 16 merge changed

Anthropic's [release notes](https://support.claude.com/en/articles/12138966-release-notes) date the change to September 16, 2026: the new experience "makes everything Claude Cowork does available from any conversation." Chats, Cowork tasks, projects, connectors and skills carry over, with no mode to pick. The rollout began with Pro and Max on web, desktop and mobile. More plans follow; Enterprise admins hear from Anthropic 30 days before anything changes.

The [merge help article](https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude) states the billing consequence. "Everything you do with Claude counts toward your plan's usage limits." Longer agentic tasks that search the web, run code or create files "generally use more than a quick question." Once an account moves, it cannot switch back to separate Chat and Cowork options. Cowork is still not a line item on any invoice.

## Which plans include Cowork, at printed prices

| Plan | Price as printed (Oct 19, 2026) | Cowork status | Usage |
|---|---|---|---|
| Free | $0 | Not in the current rollout | Everyday use, limits apply |
| Pro | $20/month, or $17/month with $200 billed annually | Included in the rollout | Shared pool, 5-hour and weekly limits |
| Max | From $100/month | Included in the rollout | 5x or 20x Pro usage |
| Team Standard | $25/seat/month, or $20 billed annually | Rollout pending; lists all Claude features | Organization pool, extra usage at API rates |
| Team Premium | $125/seat/month, or $100 billed annually | Lists Claude Code and Claude Cowork | 5x Standard seat usage |
| Enterprise | $20/seat/month billed annually, 20-seat minimum | More plans to follow, 30 days' notice | Usage billed at API rates |

All six rows come from [Anthropic's pricing page](https://claude.com/pricing), read on October 19, 2026. Prices exclude tax.

### What the table leaves out

Max offers 5x or 20x Pro usage, and the page prints no separate 20x price. The monthly API credits for Max and Team, $100 to $200 and up to $500 pooled, pay for the Claude Platform, not Cowork.

## Where the shared pool bites

Anthropic's pricing FAQ gives the mechanism. Limits reset on a rolling five-hour window, paid plans add weekly limits, and "your activity across Claude on web, desktop, mobile, and Claude Code all draws from the same pool." There is "no fixed message count," since consumption depends on conversation length, model and features.

### Cloud sessions run unattended

Since [July 7, 2026](https://support.claude.com/en/articles/12138966-release-notes), Cowork sessions can run remotely, save to the Claude account, keep working after the laptop closes, and run scheduled tasks with no device online. A ten-person team can consume usage overnight and at weekends. Teams that let sessions reach company files should check what the [safety settings cover](https://claudecoworkalternative.com/is-claude-cowork-safe).

### Agentic work costs more than chat

Searching the web, running code and creating files "generally use more than a quick question," in the merge article's wording. The deck a task produces costs more pool than the question that asked for it, and the total appears in Settings > Usage.

### Overage adds a metered line

When a paid plan reaches its limit, Anthropic lets the account turn on usage credits and keep working at standard API rates. That is a second invoice line, priced per model call rather than per seat. Anthropic publishes no pool size in tasks, tokens or Cowork runs; any page quoting a cost per task is estimating.

## What ten people cost on each plan

| Plan, ten people | Price used | Monthly total | Yearly total |
|---|---|---|---|
| Kortix, credits entry | $50 tier, 5,000 credits; members free | $50 | $600 |
| Kortix, self-hosted (platform only) | No platform fee; your infrastructure | $0 | $0 |
| Pro, monthly | $20 per person | $200 | $2,400 |
| Pro, annual | $200 up front per person | $167 equivalent | $2,000 up front |
| Team Standard, monthly | $25 per seat | $250 | $3,000 |
| Team Standard, annual | $20 per seat | $200 | $2,400 |
| Team Premium, annual | $100 per seat | $1,000 | $12,000 |
| Enterprise, annual | $20 per seat, 20-seat minimum | $400 minimum | $4,800 minimum |

### Reading the totals

Claude totals multiply printed prices by ten; the Kortix rows show the entry credits tier and the self-hosted platform fee, with model usage outside both. Enterprise is the exception: the 20-seat minimum means a ten-person team buys twenty seats. Pro annual is $200 up front per person, shown as a monthly equivalent, and the yearly column assumes twelve months. Max starts at $1,000 a month for ten; Team Premium monthly is $1,250, or $15,000 held for a year. None of the rows includes usage credits, tax or model calls. At $2,400 a year for ten, Team Standard annual is the cheapest per-seat Claude team plan.

## What an owned system changes about the cost shape

Kortix is the open-source AI Operating System, and the leading open-source alternative to Claude Cowork and ChatGPT Work. Its [pricing page](https://kortix.com/pricing), read the same day, prices the agent computer, not the person. Agents, skills, company memory and connector configuration live as files in one git repo the company owns.

### The platform line

Free is $0 with 500 credits a month and one project. Credits plans run from $50 a month for 5,000 credits to $50,000 a month for 5,000,000, and members are free on one shared pool. At ten people the seat multiplication disappears: the team picks a credit tier and adds members without changing the invoice.

A credit is $0.01 and buys about five minutes of the default 2 vCPU / 4 GB / 20 GB agent computer, which uses about 11 credits an hour. The $200 example tier buys 20,000 credits, about 1,830 hours.

### The model line

Model spend follows the key. With your own API keys, model usage goes to your provider, and Kortix charges nothing on the first $1,000 a month, then 5% from credits. A connected ChatGPT subscription uses no credits; Kortix-managed models cost the provider's base price plus 5.5%.

The unknown is different. Credits are prepaid and visible, so the platform budget is a number the team sets, while the model bill depends on the provider and model each agent uses. On Claude plans the seat line is fixed and the usage line is unknown.

### The work you keep

Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free. Any model provider with your own keys. An owned system also has to be operated, and the [comparison](https://claudecoworkalternative.com/comparison) sets that work against the zero-setup option. The free tiers are compared on the [free-plan page](https://claudecoworkalternative.com/is-claude-cowork-free).

## Questions teams ask about Claude Cowork pricing

### How much does Cowork Claude cost?

Cowork has no separate price; it is sold inside Claude plans. On October 19, 2026 Anthropic printed Free at $0, Pro at $20 a month or $17 with $200 billed annually, Max from $100 a month, Team Standard at $25 or $20 billed annually, Team Premium at $125 or $100 billed annually, and Enterprise at $20 a seat a month billed annually plus usage at API rates.

### How much does Cowork cost?

One person pays $20 a month on Pro, or $17 a month paid annually. Ten people pay $200 a month on Pro monthly, $250 on Team Standard monthly, $1,250 on Team Premium monthly, and at least $400 on Enterprise because of the 20-seat minimum. Usage credits above the pool are extra, and Anthropic publishes no task allowance.

### Is Claude Cowork worth paying for?

It is worth the plan price when the work is occasional and runs inside Anthropic's cloud on Anthropic's models, because the seat price is then the whole price. At ten people running agentic work daily, seats commit $2,400 to $15,000 a year before overage. The pool has no published task allowance, so cost per finished task cannot be calculated in advance.

### What subscription do I need for Claude Cowork?

A paid Claude plan. The rollout started with Pro and Max, and Anthropic's pricing page says more plans follow; Free is not in the current rollout. Team Premium lists Claude Code and Claude Cowork, Team Standard lists all Claude features, Enterprise admins get 30 days' notice, and there is no standalone Cowork subscription.

## Where to start

Ten people cost $2,000 to $15,000 a year in Claude seats at the printed prices, and the pool that decides the rest has no published size. A team that needs a prepaid number can price Kortix credits instead. Start with [Kortix](https://kortix.com), read [Kortix docs](https://kortix.com/docs), or read the source at [Kortix on GitHub](https://github.com/kortix-ai/suna).

## Sources and dates

All sources were read on October 19, 2026: [release notes](https://support.claude.com/en/articles/12138966-release-notes), [merge article](https://support.claude.com/en/articles/16761823-claude-cowork-and-chat-are-one-claude), [Claude pricing](https://claude.com/pricing) and [Kortix pricing](https://kortix.com/pricing). See also the [README](../README.md) and [comparison](claude-cowork-vs-open-source-alternatives.md).
