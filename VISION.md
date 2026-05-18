# aint CLI vision

Like many developers, I am firm in my resistance to LLM providers' efforts to "lock-in" developers to their models and harnesses.

## My agents are not their harness or model.
They persist beyond the harness lifecycle (thanks to [Hizal](https://github.com/parkerscobey/hizal)).

I can run my agent in Claude Code, OpenCode, Codex, OpenClaw, Pi - anywhere tool calling is supported.
*They just need to be able to reach their _semantic memory layer_.*

That last bit is key... Each agent has an API key or set of keys that gives them access to critical context - who they are and how they work.

## Keeping it simple
This could be done with VMs or clever scripting, but I want something easier than that.
I need an easy to use tool that spawns the agent I specify in the harness of my choosing.

Critically, the tool must:
- provide associated keys and environment info to the agent
- list busy and free agents

## Why track active agents?
Because I let my agents act like human workers. With guardrails, of course.
They have:
- a single focus at any given time (see Hizal's `register_focus` and `session_lifecycles`)
- a "linear" memory
They remember every task they work on, and automatically remember what they worked on last

## Why this tool
This tool is build to support the orchestration of Hizal-backed agents, but the tool doesn't know anything about Hizal.
I imagine other devs are using things like Mem0 to give their agents some persistance and they may have multiple agents with separate memories/contexts.
Maybe you always have multiple Claude Code instances running trying to one-shot many features at once and you just want to list them out.

I don't know what other crazy people are trying, but for my bassackwards setup, apparantly I need one more layer of tooling.

