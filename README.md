# Run My Ads: Claude Code plugin

The Run My Ads plugin for Claude Code. Installing it adds the Run My Ads connector **and** a
skill that teaches Claude how to work with Ados, the Run My Ads AI, so the work lands in your
account the right way: drafts in your Library, prices shown before anything is paid for, and
you approving in the app.

## Install

```
/plugin marketplace add sakredapp/runmyads-plugin
/plugin install runmyads@runmyads
```

The first time Claude uses a Run My Ads tool, it asks you to sign in with your Run My Ads
account and press Allow. There is no key to paste. You need a Run My Ads account.

Then try:

> Brief me on my ads.

## Other assistants

The connector address is `https://app.runmyads.com/mcp/rma`. Add it as a custom connector in
Claude or ChatGPT and sign in. For a connection that can only read, use
`https://app.runmyads.com/mcp/rma/read`. Help: https://runmyads.com/docs/connect-ai-agent

## What is here

```
.claude-plugin/marketplace.json      marketplace catalog
plugins/runmyads/
├── .claude-plugin/plugin.json       manifest (adds the connector)
├── skills/runmyads/SKILL.md         how to work with Ados
└── README.md
```

The plugin only points at the hosted connector. It holds no account data and no keys.
