---
layout: post
author: Xinyu Zhang
tags: [Tech, AI, Agents]
---

# ADK: When You Need Multi-Agent Orchestration

I've spent the last few weeks working with Google's Agent Development Kit. My initial attempt was a disaster. Then I used it for a real project at work and everything made sense.

## The Mistake: Wrapping Simple Conversations

My first experiment was embarrassing. I took a basic conversational agent and wrapped it in ADK's framework. Just put the whole thing in an agent shell and called it a day.

The result? Slower responses. Higher token usage. Zero benefit.

I turned a straightforward API call into a multi-layer abstraction for no reason. The framework added latency at every step. Setup tokens, agent initialization, context marshaling. All overhead, no value.

```python
# What I should have done
response = client.generate_content(prompt)

# What I actually did
# [pages of ADK boilerplate for the same result]
```

I wasted tokens and time trying to justify using a tool I didn't need. Sometimes the simplest approach is the right one, and I learned that the hard way.

## The Breakthrough: Routing Complex Workflows

Everything changed when I applied ADK to a work project. We had a system handling multiple types of user requests, each needing different processing logic. The monolithic agent was getting messy and slow.

I redesigned it with a routing agent at the top. It analyzes incoming requests and routes them to specialized subagents. Each subagent is small, focused, and good at one thing.

```
User Request
    ↓
Routing Agent (classifies intent)
    ↓
├─ Data Query Agent
├─ Report Generation Agent
├─ Analysis Agent
└─ General Q&A Agent
```

The routing agent is fast because it only classifies. The subagents are efficient because they handle narrow domains. Total token usage dropped because we stopped sending every request through a massive context window.

ADK made this architecture practical. It handles:
- State passing between routing and execution
- Parallel execution when multiple subagents are needed
- Error handling when a subagent fails
- Logging so we can debug routing decisions

Building this from scratch would have taken weeks. ADK gave us the infrastructure, and we focused on making each agent better at its job.

### Why This Works

The key insight is separation of concerns. The routing agent doesn't need to know how to generate reports. The report agent doesn't need to understand all possible user intents. Each agent has one responsibility.

When something breaks, we know exactly where to look. When we need to improve performance, we optimize specific agents instead of the entire system. This is where ADK's architecture pays off.

For simple tasks, this is overkill. For complex workflows with multiple decision points, it's the right tool.

## Production Features I Now Appreciate

When I started, I ignored the monitoring and logging features. They looked like enterprise bloat. Then we deployed to production and needed to debug why certain requests were failing.

ADK logs every routing decision and agent execution. When users reported unexpected outputs, we traced the exact path through the system. We found the routing agent was occasionally misclassifying edge cases, sending requests to the wrong subagent.

The metrics dashboard showed us which subagents were bottlenecks. We optimized the slow ones and left the fast ones alone. Version control for agent configs meant we could roll back when an update broke something, without redeploying the entire service.

These tools saved us time we would have spent building them ourselves. I'm glad we didn't have to reinvent logging infrastructure and monitoring dashboards.

## The Pattern: Google Catching Up

Comparing ADK to OpenAI's Agent Kit reminded me of something that happened in 2024.

Back then, I was using GPT for everything. It was the obvious choice. Everyone used it, the API was solid, the documentation was good. Then Google offered free Gemini credits for students.

I tried Gemini expecting it to be worse. It wasn't. The quality was comparable, sometimes better. The integration with Google Drive and Docs meant less glue code. The free credits made the choice obvious.

I switched and never looked back.

Now I'm seeing the same pattern with agent frameworks. OpenAI had the early lead with GPT Agent Kit. Google came later with ADK. And ADK is better for production systems. Better orchestration, better monitoring, better tooling for complex workflows.

This keeps happening. Google enters late, uses its resources to build something competitive, and leverages its ecosystem to pull ahead.

### Why Big Companies Win

OpenAI is an AI company. Google is a tech giant with unlimited resources and an existing ecosystem.

When you use Gemini, you get:
- Free integration with Drive, Docs, Sheets
- Built-in auth with Google accounts
- Infrastructure that scales to billions of users
- Tools built on decades of engineering experience

OpenAI has to build all of this from scratch while also competing on model quality, scaling ChatGPT, and managing partnerships.

The same applies to agent frameworks. ADK benefits from Google's production infrastructure, monitoring systems, and enterprise tooling. OpenAI's Agent Kit feels like a side project because it probably is.

### The Hard Reality for AI Startups

AI companies face an impossible challenge. They need to compete with tech giants that have:
- Decades of infrastructure
- Existing user ecosystems
- Unlimited capital
- Teams building adjacent tools

OpenAI had a head start because they moved fast when others were slow. But Google caught up on models. Amazon and Microsoft caught up on infrastructure. Meta released open-source alternatives.

The window for AI startups to build moats is closing. Big companies are catching up, and they have advantages that startups can't match.

I don't know if OpenAI can maintain its lead. Maybe they will by staying focused on what they do best. But watching Google release better tooling while offering free credits to students makes me wonder how long that lead will last.

## OpenAI's Agent Kit vs ADK

While evaluating frameworks, I looked at OpenAI's GPT Agent Kit. It's clean and simple. Great for tutorials. Perfect for learning agent concepts.

But it doesn't have what I need for production:
- No built-in routing mechanisms
- No support for parallel subagent execution
- No monitoring or logging infrastructure
- No version control for agent configurations

It feels like a teaching tool, not a production framework.

Google built ADK for real systems from the start. The learning curve is steeper, but the features are there when you need them. If you're building something users rely on daily, you need those features.

### The Bigger Picture

I think OpenAI is fighting too many battles at once. They're scaling ChatGPT, iterating on models, managing Microsoft partnerships, and competing with open-source alternatives. Agent tooling for developers gets deprioritized.

I understand why. When everything is urgent, some things get less attention. But the result is that Google and Anthropic are building better tools for engineers who ship production systems.

OpenAI had a big lead. That lead is shrinking.

## When To Use ADK

I've learned to ask: do I need multiple agents coordinating?

If the answer is no, skip ADK. Call the API directly. Keep it simple.

If the answer is yes, ADK probably makes sense. You get routing, orchestration, monitoring, and logging without building them yourself.

Use ADK when you're building:
- Multi-agent systems with routing logic
- Applications where different requests need different processing
- Production systems where debugging and monitoring matter
- Tools that integrate with multiple services

Skip ADK when you're building:
- Simple conversational agents
- Single-purpose tools with one clear task
- Prototypes where speed matters more than architecture

## What I Learned

ADK solves specific problems well. For simple tasks, it adds complexity you don't need. For multi-agent systems with routing and coordination, it saves weeks of infrastructure work.

Gemini's integration with Google services matters more than small differences in model quality. When the ecosystem fits your workflow, the choice is obvious.

OpenAI built incredible models and tools. But they can't focus on everything at once, and other companies are catching up in areas OpenAI isn't prioritizing.

The best tool is the one that solves your specific problem without creating new ones. For my work project, that was ADK with Gemini. Your situation might be different, and that's fine.

---

Resources:
- Google ADK Documentation: https://cloud.google.com/products/agent-builder
- Gemini API Docs: https://ai.google.dev/
- OpenAI Agent Kit (for comparison): https://github.com/openai/agent-kit
