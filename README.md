# Einar

Know who to ask at work. Einar keeps track of who knows what at work: what colleagues can be asked about, what they are learning, what they are passionate about, and which places and communities they know people in. Ask him in Claude, and he names the colleague who can help, with a question to start from.

This plugin connects Claude to [einar.ai](https://einar.ai) and teaches Claude when and how to use Einar.

## What it contains

- **The einar.ai connector** (`.mcp.json`): Einar's remote MCP server at `https://einar.ai/api/mcp`. You sign in to einar.ai with your work email (OAuth); there is no password.
- **The `einar` skill** (`skills/einar/SKILL.md`): when to ask Einar, how to present who he finds, and which actions wait for your yes.

The plugin runs nothing on your machine. Everything it does goes through the einar.ai connector, which reads and writes only what you ask Claude to look up, save or send, never your conversations.

## Examples

- «Who knows OKR?»
- «Add that I know Terraform»
- «Note that Kari is great at running workshops» (private, only you see it)
- «Ask Kari how they set up the OKR process» (shown to you before it is sent)
- «Invite a colleague who knows Kubernetes»

## Who it is for

Einar is built for workplaces. Your network is where you work: colleagues at your company's email domain who have joined. Your contacts are people you have worked with or know personally, whom you invite yourself. With a private email address you see only your contacts.

## Your data

Your profile is seen by your network: colleagues at your company's email domain who have joined. Your notes are seen only by you. Joining a network, sending a question and deleting your account each take a preview and your confirmation. Read the [privacy policy](https://einar.ai/privacy/en) and the [documentation](https://einar.ai/docs).

## Support

Email andreashafsaas@gmail.com. Einar is made by Andreas Hafsaas, Hafsaas Foundry, Norway.
