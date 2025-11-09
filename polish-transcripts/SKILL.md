---
name: polish-transcripts
description: Polish raw interview transcripts into searchable, well-structured markdown with metadata, dynamic headers, and full fidelity to technical content. Designed for Ray Peat interview podcasts and similar shows where technical accuracy is paramount.
---

# Polish Transcripts Skill

Transform raw transcripts into discoverable, navigable documents where an LLM agent can find specific information without reading the entire transcript. This skill maintains 100% fidelity to technical and medical content while improving readability.

## Workflow: Four Sequential Steps

### STEP 1: Read & Understand (Build Contextual Glossary)

**CRITICAL: Do this FIRST before any polishing begins.**

1. **Read the entire raw transcript** (skim if necessary, but read fully)
   - Don't start polishing yet
   - Goal: Understand the content deeply

2. **Build a contextual glossary as you read:**
   - Names: Who are all the speakers? Get full, correct names. Cross-check against context.
   - Key people referenced: Who is mentioned? (Reiner Fuellmich, not "Fyolnir"; Raymond Peat, not "Pete")
   - Organizations: What companies, institutions, agencies are discussed?
   - Key terms: What specialized vocabulary is used? (PUFA, KMUD, etc.)
   - References: What studies, websites, or resources are cited?
   - Technical content: What are the main medical/technical claims being made?
   - Recurring themes: What topics appear multiple times?

3. **Read between the lines:**
   - What is the speaker actually saying when they're being unclear?
   - What context helps clarify garbled or mumbled sections?
   - What assumptions or background knowledge is the speaker operating from?
   - Where might transcription errors have occurred?

4. **Draft Table of Contents structure (topics only, no line numbers yet):**
   - Identify the major topics/sections as you read
   - List them in order as:
     ```
     ## [Topic Title]
     ## [Topic Title]
     ## [Topic Title]
     ```
   - This is just the structure—no actual line numbers yet

5. **Document any uncertainties:**
   - Flag unclear passages: [unclear about X]
   - Flag names you're unsure about: [verify name: sounds like "Fyolnir"]
   - Flag technical terms that need context: [need to understand what PUFA means in context]

---

### STEP 2: Setup & Metadata

1. **Create new markdown file** named: `[filename]_polished.md` (replace `_raw` with `_polished`)

2. **Add YAML Front Matter at very top** (use verified names from STEP 1 glossary):

```yaml
---
title: "[Descriptive Topic] - [Show Name] [Date]"
show_name: "[Exact show name]"
date: "YYYY-MM-DD"
speakers:
  - "[Full Name - VERIFIED from STEP 1]"
  - "[Full Name - VERIFIED from STEP 1]"
---
```

---

### STEP 3: Polish Content with Dynamic Headers

**Using the TOC structure from STEP 1, now polish the actual transcript content.**

**REMOVE technical/audio sections first:**
- Cut out opening radio mechanics (station IDs, underwriter announcements, fundraising pitches)
- Remove audio troubleshooting: "Can you hear me?", "Sound went down", "Engineer's voice was clear", etc.
- These interruptions break the flow and will be reconstructed as narrative when relevant

**Process:**
1. Polish transcript section by section following the rules below
2. When topic substantially changes, insert a header: `## [Topic Title]` (from STEP 1 structure)
3. After each header, add tags (see format below)
4. **Always end each pause point with a new header and the opening dialogue of the next section** to ensure continuity and allow for review of header placement
5. Continue polishing the next section
6. **PAUSE after every 1,500-2,000 lines of polished content** for fidelity review

**Header Format (insert when topic shifts):**

```markdown
## [Specific, Clear Chapter Title]
tags: [[tag1]] [[tag2]] [[tag3]] [[tag4]]

[Opening dialogue of this section]
```

**Rules for Headers:**
- Only insert headers when topic substantially changes
- 3-5 tags, lowercase-hyphenated, in Obsidian wiki-link format
- Always include the first paragraph or question of the new section after the header
- Keep natural flow of conversation

---

### STEP 4: Generate Table of Contents with Line Numbers (FINAL STEP)

**ONLY after the entire transcript is fully polished**, add line numbers to the TOC structure from STEP 1.

**Process:**
1. Get actual line numbers from the polished file (use `grep -n "^## " polished.md`)
2. Insert the formatted TOC right after YAML metadata with actual line numbers

**Format:**

```markdown
## Table of Contents

Line X - [[#Chapter Header 1|Chapter Header 1]]
Line Y - [[#Chapter Header 2|Chapter Header 2]]
Line Z - [[#Chapter Header 3|Chapter Header 3]]
```

**Rules:**
- Use "Line X" format (no numbering like "1.", "2.")
- List all major section headers in order of appearance
- Use actual line numbers from the polished file
- Insert this TOC section as the first content block after YAML front matter
- Do NOT include key takeaways or descriptions—just the links and line numbers

Match TOC entries to headers created during Step 3.

---

## Content Polishing Standards

### Core Principle
**100% FIDELITY to meaning + MAXIMUM READABILITY**

**CRITICAL:** When raw text is awkward, garbled, or unclear, PRESERVE the awkwardness rather than reinterpreting. Use light grammar fixes only. If text is incomprehensible, flag it with [unclear] or [sic] rather than paraphrasing.

### What to ALWAYS Remove:
- Pure radio mechanics: Call-in numbers, station IDs, frequency announcements (repeated)
- Scheduling/logistical info: "You're invited to call in from 7:30 to 8:00 PM", air times, "the number is 707-923-3911"
- Repeated invitations to call in or participate in live show format
- Audio troubleshooting: "Can you hear me? Is that better?" (unless affects content)
- Generic filler: Excessive "um, uh, you know, like" that impedes reading
- Incomplete fragments: "So I was going to— well actually—" that don't complete a thought
- Redundant acknowledgments: "Yeah, yeah, okay, yeah" when repeated

### What to ALWAYS Keep:
- ALL medical/technical information (100% fidelity to every fact, figure, mechanism)
- Speaker personality (casual phrasing, hesitations, stammers like "I knew, I know")
- Substantive asides (references, anecdotes, explanatory details like "Guangdong virus of 1996" or MLK quotes)
- Relationship dynamics ("As we discussed before", credibility signals)
- Thinking process (even if not perfectly polished, shows how ideas develop)
- Call-in interactions (questions from callers, backgrounds when relevant)
- Credibility markers (experience, track record, "I've followed this for 40 years")
- Emotional tone (emphasis, frustration, humor, passion)
- Awkward or unusual phrasing that reveals speaker's authentic voice ("the classical thing is", "very likely through science")

### Light Touch Edits Only:
- Fix obvious transcription errors ("fat fish in diet" → "fat-free diet")
- Add missing punctuation that impedes reading (not speech punctuation)
- Fix clear misspeaks where context reveals intent
- Normalize speaker labels and format (not content)
- Clean up "um, uh" stuttering at phrase starts only

### DO NOT:
- Rephrase in your own words or reinterpret unclear passages
- Reinterpret garbled or confusing passages—preserve them faithfully
- Change vocabulary or technical terminology
- Over-formalize natural speech
- Remove personality markers or hesitations
- Remove substantive details (names, references, explanatory asides)

### Speaker Formatting:
```markdown
**[Full Name]:** [What they said]
```
- Use actual names, not "[Speaker A]"
- Don't repeat name if same speaker continues next paragraph
- Use "Caller" or "Engineer" if name unknown

---

## Examples

### Example 1: Opening Segment

**BEFORE:**
```
[Speaker A]: 53 degrees outside 7pm Kmud Garberville, Kmue, Eureka K L A I Laytonville. Where the views and opinions expressed throughout the broadcast day are those of the speaker and not necessarily the station staff, underwriters or volunteers.
[Speaker B]: Sam Sa. Sam Sa.
[Speaker A]: And I believe I have the herb doctor here.
[Speaker C]: Hey, good evening.
[Speaker A]: Good evening. And we have Dr. Pete. Take it away.
[Speaker C]: Welcome to this month's ask your herb doctor. The see here, November 19th edition, 2021. My name is Andrew Murray.
```

**AFTER:**
```markdown
## Introduction
#intro #welcome #overview

**Andrew Murray:** Welcome to this month's Ask Your Herb Doctor, the November 19th, 2021 edition. My name is Andrew Murray.
```

### Example 2: Technical Medical Content

**BEFORE:**
```
[Speaker B]: A couple of the abstracts you're referring to I think mentioned that on a high fish oil diet, the Metastasis was about 1,000 times worse than on a low fat diet. Just a huge difference from supplementing fish oil versus not having fat. And we can make all of the unsaturated and saturated fats that we need from carbohydrates.
```

**AFTER:**
```markdown
**Dr. Raymond Peat:** A couple of the abstracts you're referring to mentioned that on a high fish oil diet, metastasis was about 1,000 times worse than on a low fat diet. Just a huge difference from supplementing fish oil versus not having fat. We can make all of the unsaturated and saturated fats that we need from carbohydrates.
```

**What Changed:** Speaker label, fixed capitalization
**What Stayed:** Every fact, Ray's casual style

### Example 3: Complex Biochemistry

**BEFORE:**
```
[Speaker B]: Yeah. And in the process of getting the ketogenic effect, basically it's starvation and stress that turns on the so called ketone production. But actually the so called ketone bodies, one of the major ketone bodies is actually not a ketone, but an alcohol hydroxyl group as a potential ketone.
```

**AFTER:**
```markdown
**Dr. Raymond Peat:** Yeah. In the process of getting the ketogenic effect, basically it's starvation and stress that turns on so-called ketone production. But actually, one of the major ketone bodies is not a ketone, but an alcohol with a hydroxyl group as a potential ketone.
```

**What Changed:** Light punctuation fixes ("so called" → "so-called")
**What Stayed:** Complete technical explanation, Ray's teaching style

### Example 4: Call-In Segment

**BEFORE:**
```
[Speaker A]: And we have a couple callers.
[Speaker C]: Okay, we're good, let's hold that there. Caller, you're on the air. Where are you from and what's your question?
[Speaker A]: It was a local person who was a very bad connection. But they wanted to know what you thought of flax oil and avocados.
```

**AFTER:**
```markdown
**Andrew Murray:** We have a caller. Where are you from and what's your question?

**Michael (Engineer):** It was a local person with a bad connection, but they wanted to know what you thought of flax oil and avocados.
```

**What Removed:** "Okay, we're good, let's hold that there" (logistical)
**What Kept:** Call-in interaction, engineer relay, question

---

## Processing Notes

**STEP 1 is non-negotiable:** Read and understand the entire transcript before touching anything. This prevents name errors, context misses, and ensures the TOC structure is sound from the start.

**STEP 3 (Polishing) happens in chunks** with pause points. After every 1,500-2,000 lines of polished content, pause for fidelity review. This ensures technical accuracy is maintained and the approach can be adjusted if needed.

**STEP 4 (TOC with line numbers) is purely mechanical:** Only after all content is polished, grep for headers and add line numbers. Don't change anything else.

The skill improves iteratively as it's used—feedback from checkpoint reviews informs updates to these guidelines.
