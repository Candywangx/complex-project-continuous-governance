# Complex Model Discovery External Mapping 2026-07-02

Purpose: explain which external ideas Complex borrows for model-discovery work, what they help with, and where their boundaries are. This note is a method map, not a new runtime dependency and not a verifier-required field.

## Why This Was Added

Complex already works well for many evidence-fill and audit-heavy tasks: the model or table is known, then the agent collects sources, checks gaps, routes tools, validates claims, and delivers. The weakness exposed in real use was different: when the research frame, explanation model, metric structure, or story is not settled, the protocol can converge too early. It may choose the easiest evidence gap, the first tool path, or the smallest loop, then keep improving that local route while the bigger question remains under-defined.

The new layer fixes that by adding a project-nature router and anti-premature-convergence gates. It does not replace evidence discipline. It decides when evidence discipline should wait until the question and candidate frameworks are mature enough.

## External Method Mapping

| External idea | Useful transfer into Complex | Non-transfer boundary |
| --- | --- | --- |
| Cynefin / domain sensemaking | Use `project_nature_router` to distinguish ordered evidence-fill work from model-discovery and mixed work. Complex should not treat every task as a known-form evidence audit. | Cynefin is not a scoring formula and does not by itself tell the agent which answer is correct. |
| Double Diamond | Use a visible rhythm of divergence then convergence: open candidate frames first, then select and execute. | It is not a fixed four-stage template that must be forced onto every task. |
| Tree of Thoughts | Use a candidate path pool for open problems, with branch, evaluate, keep, drop, or backtrack operations. | Do not expose hidden chain-of-thought. Record only user-safe summaries: candidate paths, assumptions, probes, and decisions. |
| Graph of Thoughts | Allow paths to merge, recombine, or be transformed instead of staying as isolated branches. | It does not require a graph database or a new tool dependency. |
| IBIS | Add `issue / position / pro / con / unresolved question` before evidence filling for open-ended research. | It does not replace evidence matrices; it clarifies what the evidence is supposed to decide. |
| LangGraph / agent frameworks | Borrow state, routing, and multi-agent engineering ideas for persistence and topology control. | These frameworks do not solve divergent research thinking by themselves; they are engineering substrates, not creativity guarantees. |

Sources used for mapping:

- Design Council, Double Diamond: https://www.designcouncil.org.uk/our-resources/framework-for-innovation/
- Tree of Thoughts: https://arxiv.org/abs/2305.10601
- Graph of Thoughts: https://arxiv.org/abs/2308.09687
- Snowden and Boone, Cynefin in HBR: https://hbr.org/2007/11/a-leaders-framework-for-decision-making
- IBIS overview: https://en.wikipedia.org/wiki/Issue-based_information_system

## Complex Mapping

### project_nature_router

At entry, classify the task as:

- `evidence_fill`: model, table, formula, metric, or framework is already stable.
- `model_discovery`: problem definition, research frame, explanation path, variables, or story is still unsettled.
- `mixed`: discovery first, evidence filling later.
- `execution_delivery`: solution is defined; main work is implementation, verification, or delivery.

This prevents the agent from using one workflow for all complex tasks.

### anti_premature_convergence_gate

For `model_discovery` and pre-convergence `mixed` tasks, the agent must preserve 3-5 candidate frameworks unless the problem is already narrow. Each candidate needs:

- core assumption;
- what it explains;
- what it cannot explain;
- support and objection;
- discriminating evidence;
- minimum probe;
- keep/drop condition.

Before this exists, a local evidence gap cannot become the main goal.

### ibis_argument_map_gate

For open questions, the agent records:

- issue;
- positions;
- pros;
- cons;
- unresolved questions;
- evidence needed to distinguish positions.

This handles "what is the right question?" before "what source fills the table?"

### thought_search_gate

The highest-leverage next step should come from a candidate path pool, not the first easy route. Paths can be:

- kept for exploration;
- merged with another path;
- dropped with reason;
- backtracked when evidence breaks the route;
- transformed into a discriminating probe.

This is the anti-greedy part of the update.

### event_triggered_capability_refresh

Capability refresh now uses event triggers first and a 3-round fallback cap second. The protocol should reconsider tools, subagents, and external paths when:

- project nature changes;
- main direction changes;
- evidence path changes;
- the same type of block repeats;
- material type changes;
- external write/account boundary appears;
- a subagent responsibility no longer matches;
- delivery audience changes.

If none of these happen, the agent records `lightweight_keep` and stays on task.

## What This Changes In Practice

For evidence-fill tasks, Complex should stay efficient. It can skip heavy divergence with a short `divergence_noop_reason` and focus on sources, validation, and delivery.

For model-discovery tasks, Complex must delay convergence. It should make the problem shape visible, compare candidate frameworks, test what distinguishes them, and only then switch into evidence filling.

For mixed tasks, Complex starts in discovery mode and changes weight only when convergence conditions are explicit.

For execution-delivery tasks, Complex keeps the workflow lean: acceptance criteria, implementation, verification, side-effect boundary, and handoff.

## Guardrails

- This is not a new table burden for every task.
- This is not permission to make unsupported claims in the name of creativity.
- This does not add verifier-required fields.
- This does not require installing LangGraph, agent frameworks, graph databases, or external libraries.
- This should reduce attention scattering by asking the right first question: "Are we filling a known model, or are we still discovering the model?"
