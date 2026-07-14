---
name: course-notes
description: >-
  Transform raw, messy course/lecture/workshop notes (usually a .txt file, but
  also pasted text) into a clean, well-structured Markdown file. Reorganizes
  the material into a logical top-to-bottom flow so prerequisite concepts
  appear before the concepts that depend on them, cleans up formatting
  (headers, bullets, code blocks, bold key terms), and corrects mistakes it
  finds in the notes, fixing them directly in the file while clearly flagging
  every fix back to the user in chat. Stays strictly within the scope of what
  the notes already cover, with no padding from outside material, no invented
  examples, no generic textbook filler. Use this whenever the user mentions
  raw notes, class/course/lecture/workshop notes, a messy .txt of notes, wants
  notes "cleaned up," "organized," "turned into markdown," "made into a proper
  .md," or asks to reorganize/fix a notes file into a real document, even if
  they don't say the word "skill" or name the file type explicitly.
---

# Course Notes → Markdown

Raw notes taken live during a course are captured in whatever order the instructor happened to say things, not the order that's best for understanding them later. They also inherit whatever slipped or got misheard in the moment. The job here is two things at once: reorder for comprehension, and tighten up accuracy and formatting — without turning the notes into something generic or padding them with material that wasn't there. The notes are the user's own learning record. Keep them recognizably theirs.

## Step 1: Read the whole thing before touching anything

Read the entire notes file first. Reordering decisions require seeing the whole picture — you can't know a term needs to move earlier until you've seen where it gets used later.

## Step 2: Map concepts and their dependencies

Informally note, for each concept or term in the notes, what other concepts it assumes the reader already has. Use that to decide the top-to-bottom order: foundational concepts before the things built on them.

Don't force reordering that isn't needed. If the notes already flow logically, leave that order alone — reorder only when it actually helps comprehension (e.g. a term is used early but not defined until much later).

## Step 3: Rewrite into clean, richly-formatted Markdown

Base formatting:
- Title as H1, major topics as H2, sub-points as H3.
- Bold key terms on first mention, italics for secondary emphasis.
- Code, commands, or technical syntax in backticks or code blocks.
- Bullet lists for enumerations, numbered lists for sequences/steps.
- `---` horizontal rules between major sections for breathing room.
- Match the density of the original — don't inflate short fragments into long paragraphs, and don't compress fuller notes down into bare fragments. Reformat, don't rewrite the substance.

On top of that, here's a repertoire of formatting devices worth drawing from — treat them as options to reach for when they genuinely fit what the notes cover, not a checklist to complete on every note:

- **Opening hook.** If the notes trace a progression or answer a "why" (an evolution, a cause-and-effect chain, a "how did we get here"), open with a one-line question or statement in a blockquote that frames the arc before section 1 starts.
- **Callout blockquotes.** Use a blockquote with a leading emoji + bold label for asides that are useful but would clutter the main flow — history, the key turning point, a memory aid, a caveat, why something matters. E.g. `> 🔑 **Why it matters:** ...` or `> ⚠️ **Easy to get wrong:** ...`. Use a handful of the clearest ones rather than wrapping every paragraph in one — they work because they're rare.
- **Tables for comparisons.** Any time the notes set two or more things side by side (X vs. Y, types of something, a timeline, before/after), a table reads faster than prose describing the same thing.
- **"The Problem" pattern.** When the notes describe a limitation that motivated whatever came next, give it its own short subheader (e.g. `### The Problem`) so the reader feels the gap before the fix arrives.
- **Worked examples.** If the notes include a concrete example, label it clearly (`Case 1:`, `Worked example:`) so it reads as illustration, distinct from the definition above it.
- **Closing recap.** End with a short "Key Takeaways" or "Recap" section when it'd genuinely help. Let the shape of the material decide the format — a table if it's genuinely comparison-shaped, a few bullets if it's a flat set of concepts, a short paragraph if that says it just as well. Don't default to a table out of habit.

## Step 4: Stay within scope

Don't add:
- Examples that weren't in the original notes.
- Background or context the source material didn't cover.
- Generic textbook framing around a concept just because you know more about it.

It's fine to:
- Add a one-line bridging sentence when reordering leaves a gap in flow — but mark it distinctly (e.g. *italicized, "added for flow"*) so the user always knows what's original versus added.
- Raise a question in chat instead of filling a gap yourself, when a concept is referenced but genuinely never explained in the notes.

## Step 5: Corrections — fix inline, flag in chat

This is the step that needs the most judgment.

When something in the notes is actually wrong — not just differently phrased than you'd put it — fix it directly in the Markdown file. The point is to hand back notes the user can trust, not a document cluttered with "[sic]" and bracketed caveats.

Then, in your chat reply (never inside the .md file itself), list what you changed: what the note said, what you changed it to, and why, in one line each. This is the user's chance to catch you being wrong, not just take your word for it.

Be conservative about what counts as "wrong":
- Fix things you're confident are factual errors, swapped/confused terminology, or internal contradictions (the notes define something one way early on and a conflicting way later).
- Don't "fix" things that are just stylistic, a matter of emphasis, or a legitimate paraphrase of what the instructor said — that's the user's own understanding, not a bug.
- If you're genuinely unsure whether something is wrong (could be shorthand, could be a paraphrase that lost some nuance), don't silently rewrite it. Leave the original phrasing in the file and raise it as a question in chat instead. Confidently "fixing" something you're not sure about is worse than asking.

If there were no corrections to make, don't manufacture one to have something to report — just skip that part of the reply.

## A note on explaining concepts

When rewriting an explanation — not just reformatting it — keep it grounded and concrete: say why a concept matters or exists before getting into how it works mechanically. Don't blend two related concepts into one explanation just because the source notes kept them distinct and it would read more smoothly merged — precision is the whole point of notes like these. Only use examples the notes themselves introduced; never attribute an example to the notes that you invented to illustrate a point more cleanly.

## Example

**Before (raw notes, in the order they were jotted down):**
```
RAG = retrieval augmented generation, uses cosine similarity on embeddings usually
embeddings = vectors that represent meaning, made by an embedding model
vault = the folder of markdown files, agent reads/writes here
```

**After (reorganized, cleaned, house style applied):**
```markdown
## Vault
The **vault** is the folder of Markdown files the agent reads and writes to.

## Embeddings
**Embeddings** are vectors that represent meaning, produced by an embedding model.

## RAG (Retrieval-Augmented Generation)
**RAG** retrieves relevant chunks — usually by cosine similarity between embeddings —
before generating a response.

> 🔑 **Why order matters:** RAG's definition leans on knowing what an embedding is,
> so embeddings come first even though the notes mentioned RAG first.
```
Embeddings moved ahead of RAG, since RAG's definition depends on knowing what an embedding is. Nothing was added beyond what the three original lines already said — the callout just narrates the reordering, it doesn't introduce new content.

## Output

Produce one Markdown file per notes file. If given several files, transform each into its own corresponding .md file rather than merging them, unless the user explicitly asks for a combined document.
