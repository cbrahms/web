# Aircraft Manual Style

A concise, search-friendly writing system for instructions, analysis, plans, and reference material. The goal is low inference, low working-memory load, and fast re-entry after interruption.

## Standard

- Use the fewest words that preserve meaning.
- Let headings carry their share of the meaning. Do not restate a heading in its description.
- Name actors, objects, conditions, and outcomes when a reader could otherwise need to infer them.
- Put prerequisites before actions, actions before expected results, and warnings before risky actions.
- Keep one primary idea per sentence where possible.
- Keep terminology stable. Do not rotate through near-synonyms for the same thing.
- State cause and effect when the relationship matters.
- Separate facts, assumptions, decisions, and next actions.
- Remove sentences that add neither a fact, an instruction, nor a decision criterion.

## Mode format

Every mode uses this format:

```md
**AMS MODE**
#searchable #use-case #tags #go #here
**Uses:** What the mode changes.
**Combos:** Compatible modes.
```

### Hashtag rule

- Put hashtags immediately after the mode name.
- Use at least four hashtags.
- Use at least as many hashtags as applicable use cases or categories.
- Each tag names a real search term for a use case, document type, or task.
- Do not replace the tag line with a prose list.
- Put only the minimum necessary context in **Uses** and **Combos**. The heading and tags already carry context.

## Modes

**AMS LOW-LOAD**
#dense-writing #fatigue #working-memory #long-documents #cognitive-load
**Uses:** Reduces the amount a reader must hold in mind.
**Combos:** AMS low-load + preserve-detail

**AMS EXPLICIT**
#pronouns #ambiguity #actors #causes #relationships
**Uses:** Names actors, objects, causes, and relationships.
**Combos:** AMS explicit + reduce-inference

**AMS STEPWISE**
#procedures #instructions #workflows #troubleshooting #learning #prompting
**Uses:** Separates actions. Preserves execution order.
**Combos:** AMS stepwise + explicit

**AMS SCAN-FRIENDLY**
#dashboards #reference #plans #recurring-use #navigation
**Uses:** Makes information easy to find again.
**Combos:** AMS scan-friendly + terminology

**AMS REDUCE-INFERENCE**
#recommendations #analysis #strategy #technical-reasoning #tradeoffs
**Uses:** States why a conclusion follows from the evidence.
**Combos:** AMS reduce-inference + decision

**AMS FOCUS**
#overload #priorities #immediate-tasks #distractions #next-action
**Uses:** Keeps the active task visible and routes secondary detail out of the way.
**Combos:** AMS focus + scan-friendly

**AMS PRESERVE-DETAIL**
#technical-docs #specifications #compliance #handoffs #completeness
**Uses:** Simplifies language without removing required substance.
**Combos:** AMS preserve-detail + low-load

**AMS COMPRESSION**
#wordiness #repetition #editing #executive-summary #plain-language
**Uses:** Removes words that add no meaning.
**Combos:** AMS compression + explicit

**AMS TERMINOLOGY**
#glossaries #systems #components #agents #consistency
**Uses:** Keeps names stable and prevents synonym drift.
**Combos:** AMS terminology + scan-friendly

**AMS DECISION**
#comparisons #recommendations #criteria #evidence #next-action
**Uses:** Separates facts, criteria, tradeoffs, and the recommended action.
**Combos:** AMS decision + reduce-inference

## Common requests

- `AMS rewrite`
- `AMS low-load rewrite. Preserve technical detail.`
- `Convert this guide to AMS stepwise.`
- `AMS explicit: replace vague references with named actors and objects.`
- `AMS compression: remove repeated or empty phrasing.`
- `AMS decision: show evidence, criteria, tradeoffs, recommendation, and next action.`
- `Keep the content. Apply AMS scan-friendly + terminology.`

## Before and after

### Heading-aware compression

Before:

> For procedures, setup instructions, workflows, troubleshooting, and learning.

After, beneath **AMS STEPWISE**:

> Procedures and troubleshooting.

The heading already identifies the mode. The description adds only information that the heading does not.

### Explicit cause and effect

Before:

> It failed because it was not set up correctly.

After:

> The deployment failed because the release workflow did not receive the required API key.

### Procedural order

Before:

> Configure access, then check the connection. You may need an API key.

After:

1. Add the API key.
2. Configure access.
3. Check the connection.
4. Expected result: the status page shows a successful connection.

## Agent instructions

When asked to apply Aircraft Manual Style:

1. Preserve facts unless the request authorizes factual changes.
2. Identify the document's primary mode or mode combination.
3. Use the relevant mode tags when adding or revising a mode description.
4. Remove repeated meaning before adding explanation.
5. Keep warnings, prerequisites, actions, expected results, and decisions visibly separate when they exist.
6. Return the rewritten artifact, not only a description of the intended changes.
