# askyoda — Claude Code plugin

**Your agent said _done_. AskYoda checks.**

A skill that gives Claude web data it can trust. It runs your goal on a website with
[TinyFish](https://tinyfish.ai), climbing only as far as needed (free fetch → browser agent →
stealth browser + proxy), **verifies every answer** instead of trusting the agent's own
`COMPLETED`, diagnoses what went wrong and at which step, patches the next attempt, and stops with
**needs human escalation** at login walls and CAPTCHAs instead of burning credits.

## Install

```
/plugin install askyoda --marketplace 1sakshm/askyoda-plugin
```

On older Claude Code: `/plugin marketplace add 1sakshm/askyoda-plugin`, then
`/plugin install askyoda@askyoda`.

Then set your TinyFish key (runs bill to your own account):

```sh
export TINYFISH_API_KEY=...        # https://agent.tinyfish.ai/api-keys
export GEMINI_API_KEY=...          # optional: free first-rung extraction
```

## Try it

> Get me the title and price of the first 5 books on https://books.toscrape.com

Claude runs `npx -y askyoda run … --min-items books:5 --json` and answers with a verified table
and its cost (about 2 TinyFish credits in testing).

## What's inside

One skill, [`skills/askyoda/SKILL.md`](skills/askyoda/SKILL.md) — instructions only, no hooks,
servers or bundled programs. It uses the MIT-licensed npm package
[`askyoda`](https://www.npmjs.com/package/askyoda) (zero runtime dependencies).

- Full project, web app and recorded runs with video: https://github.com/1sakshm/AskYoda ·
  https://askyoda.vercel.app

## License

MIT. Based on [agent-failure-autopsy](https://github.com/DevaanshPathak/agent-failure-autopsy) by
DevaanshPathak, used with permission.
