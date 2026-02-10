---
layout: post
author: Xinyu Zhang
tags: [Tech, AI, Engineering, Productivity]
---

# Claude Code in My Real Daily Workflow: A 27-Day Engineering Retrospective

### What Your Shoe Sole Reveals About How You Walk

I wanted this write-up to be a technical blog, not a motivational post.

For 27 days, I used Claude Code during normal work hours while building backend features at an AI startup. I work closely with frontend, and my daily engineering reality is a multi-service environment: **2 frontend services + 6 backend services**. My core stack during this period was **ADK + Django**, and in the last week I started shifting toward **Flutter + A2A + A2UI** because I wanted more accurate behavior and more stable cross-platform UI presentation.

I care about efficiency, but not in the abstract. In this setup, efficiency means how quickly I can move from architecture context to shippable backend functionality while keeping frontend collaboration smooth.

---

## Why this retrospective matters to me

In startup work, delivery speed is not only about typing code fast. It is heavily constrained by system context, dependency order, authentication flow, and how cleanly backend capabilities are communicated to frontend.

I also feel daily summaries matter more than they seem. Habit is easy to ignore when you are inside it. Looking back at usage traces is like checking the wear pattern on a shoe sole: you can see posture, gait, and pressure points that were invisible in the moment. This report gave me that kind of visibility into my engineering behavior.

That is exactly where I used Claude the most:

- reading docs and extracting what matters
- summarizing architecture quickly
- consolidating API surface and backend capabilities
- accelerating implementation decisions in the middle of feature work

So this article is really a short-term engineering report on that workflow.

---

## Data snapshot from `report.html` (embedded)

Below is a compact HTML panel with the key numbers from the Claude usage report. I’m embedding this directly because the report itself is HTML-first and I want the blog to preserve that flavor.

<div style="border:1px solid #e5e7eb; border-radius:12px; padding:16px; margin:16px 0; background:#fafafa;">
  <h3 style="margin-top:0;">Claude Code Usage Window</h3>
  <p style="margin:6px 0 12px 0; color:#4b5563;"><strong>2025-12-22 → 2026-02-10</strong> (27 active days)</p>

  <table style="width:100%; border-collapse:collapse; font-size:14px;">
    <tr>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Messages</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">5,447</td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Sessions</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">680</td>
    </tr>
    <tr>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Messages / Day</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">201.7</td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Files Touched</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">1,944</td>
    </tr>
    <tr>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Code Diff</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">+328,364 / -102,053 lines</td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;"><strong>Median Response</strong></td>
      <td style="padding:8px; border-bottom:1px solid #e5e7eb;">111.8s</td>
    </tr>
    <tr>
      <td style="padding:8px;"><strong>Average Response</strong></td>
      <td style="padding:8px;">268.6s</td>
      <td style="padding:8px;"><strong>Parallel Session Share</strong></td>
      <td style="padding:8px;">~1% messages</td>
    </tr>
  </table>
</div>

The tool profile was even more telling:

<div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; margin:12px 0;">
  <div style="border:1px solid #e5e7eb; border-radius:10px; padding:12px;">
    <h4 style="margin:0 0 8px 0;">Top Tools</h4>
    <ul style="margin:0; padding-left:20px; line-height:1.7;">
      <li><strong>Bash</strong>: 15,568</li>
      <li><strong>Read</strong>: 7,650</li>
      <li><strong>Edit</strong>: 6,333</li>
      <li><strong>Grep</strong>: 2,071</li>
      <li><strong>Glob</strong>: 659</li>
    </ul>
  </div>
  <div style="border:1px solid #e5e7eb; border-radius:10px; padding:12px;">
    <h4 style="margin:0 0 8px 0;">Language Surface</h4>
    <ul style="margin:0; padding-left:20px; line-height:1.7;">
      <li><strong>Python</strong>: 7,965</li>
      <li><strong>TypeScript</strong>: 3,043</li>
      <li><strong>Markdown</strong>: 894</li>
      <li><strong>HTML</strong>: 399</li>
      <li><strong>YAML</strong>: 229</li>
      <li><strong>JSON</strong>: 153</li>
    </ul>
  </div>
</div>

---

## What these numbers revealed about my workflow

The numbers confirmed something I felt but never quantified: I use Claude as a **system-level execution partner**.

I am not opening one clean project and writing one isolated function. I am running a connected system where backend implementation depends on architecture clarity, and frontend collaboration depends on stable backend capability communication. In that setup, the biggest productivity wins come from reducing context loading time and reducing switching friction.

From my perspective, this is what “top-down engineering” means in real work:

1. start from service map and dependency awareness,
2. clarify backend capability boundaries,
3. implement a complete functional slice,
4. hand off capability language that frontend can use immediately.

That loop sounds simple, but in multi-service projects it is where most delivery quality is decided.

---

## Personal operating pattern: where Claude saved the most time

The report aligns with my daily feeling about high-impact moments. I got the most leverage when I asked Claude to do context-heavy work fast.

### A) Document compression under delivery pressure
When requirements or setup details were spread across docs and code, Claude gave me the shortest path to an actionable summary. That reduced dead time between “I know what the feature is” and “I know exactly what to implement.”

### B) Architecture scanning before implementation
Before building, I often needed a full-project orientation fast. Claude was useful for turning repository complexity into a practical map I could execute against.

### C) API capability consolidation for frontend collaboration
My collaboration pattern with frontend is direct: I finish backend functionality, then I communicate what capabilities are available. Claude helped consolidate those capability summaries quickly and consistently.

### D) Command-heavy execution continuity
The Bash volume in the report is high for a reason. Multi-service development introduces startup/order/authentication coordination cost. Even when boot time is not huge, the cognitive overhead is real. Claude reduced that overhead by centralizing command context and execution logic.

---

## Why commit count is not a useful standalone metric here

One report detail that can be misread is low commit count relative to interaction volume. In my own workflow, I commit when a feature slice is actually complete, and I generally do not delegate commit operations. So the effort distribution in this period sits heavily in architecture comprehension, feature shaping, service coordination, and integration-ready communication.

In other words, delivery work happened continuously; commit events were intentionally coarse-grained.

---

## From “Existing CC Features to Try” onward: what the report actually suggested

I was very curious about this section too, especially all the “paste into Claude Code” content. I reviewed it as engineering guidance rather than generic tips.

The report proposed a practical evolution path:

- add startup hygiene rules into CLAUDE.md (pre-start stale-process and port cleanup)
- standardize config backup before restart/reinstall tasks
- enforce checklist-first execution for long setup flows so sessions are resumable
- package repeated operations into custom skills
- add hooks for pre-task cleanup automation
- use headless mode for repeatable non-interactive command workflows
- generate an explicit service dependency map with startup order

It also included ambitious future patterns:

- autonomous health monitoring and recovery loops
- migration pipelines with test validation loops
- spec-to-delivery parallel agent workflows

My personal takeaway is that these suggestions are strong when interpreted as a maturity ladder. Immediate gains come from structure and repeatability. Advanced autonomy becomes useful after operational discipline is already in place.

## How the `/insights` report likely works under the hood

I also read a [deep-dive article](https://www.zolkos.com/2026/02/04/deep-dive-how-claude-codes-insights-command-works.html) about how `/insights` is implemented, and it helped explain why the output feels both quantitative and narrative. The pipeline appears to be designed as a staged analytics + LLM system rather than one single prompt.

At a high level, it first scans session logs, filters out low-value or internal sessions, and extracts structured metadata such as tool counts, token usage, duration, lines changed, language signals, error categories, and feature usage markers. For very long transcripts, it summarizes chunks before deeper analysis, which keeps later inference bounded and consistent.

Then it runs facet extraction per session using a strict JSON schema. The interesting part is that this schema forces separation between explicit user intent and Claude’s autonomous behavior. That design decision matters because it reduces false attribution in goal tracking. The same schema also enforces standardized labels for outcomes, satisfaction, friction, session type, and primary success mode. Once these per-session facets are produced, they are cached, which makes reruns incrementally cheaper and faster.

After that, the system aggregates all sessions and runs multiple specialized prompts: project-area clustering, interaction-style narrative, success pattern extraction, friction diagnosis, and feature recommendations. This explains why the final HTML can combine dashboard-like metrics with “you-style” qualitative coaching language. In practice, it is doing both descriptive analytics and guided interpretation.

From an engineering perspective, this architecture is useful because it makes habit patterns visible in a stable taxonomy. It turns daily interaction traces into operational signals: where time goes, what repeatedly causes drag, and which standardization opportunities are worth implementing first. That is exactly why this report felt actionable for my own workflow.

---

## A technical reading of efficiency in this workflow

I now describe this workflow using three connected dimensions:

### 1) Efficiency as context speed
Not just “faster coding,” but faster transition from unknown context to executable decisions.

### 2) System thinking as delivery quality
In a 2-frontend + 6-backend topology, dependency awareness and interface clarity have direct impact on integration quality.

### 3) Top-down execution as stability
Starting with system framing and ending with capability handoff creates fewer coordination surprises.

This is the combination I want to keep improving.

---

## What changed in practice after this 27-day period

I became much more intentional about treating AI usage as part of engineering process design. Instead of seeing Claude as a convenience tool, I now treat it as a workflow component with measurable effect on context management and execution continuity.

That shift matters for startup work. Speed is important, but sustained delivery speed comes from reducing invisible friction in how information moves through the system and through the team.

For me, this retrospective validates one direction clearly: pairing top-down system thinking with disciplined AI-assisted execution is a practical path to higher backend delivery efficiency.

---

## Reference

- Deep Dive: How Claude Code's /insights Command Works  
  https://www.zolkos.com/2026/02/04/deep-dive-how-claude-codes-insights-command-works.html
