---
name: polish-transcripts
description: Polish raw interview transcripts into searchable, well-structured markdown with metadata, dynamic headers, and full fidelity to technical content. Designed for Ray Peat interview podcasts and similar shows where technical accuracy is paramount.
---

# Polish Transcripts Skill

Transform raw transcripts into discoverable, navigable documents where an LLM agent can find specific information without reading the entire transcript. This skill maintains 100% fidelity to technical and medical content while improving readability.

## Workflow: Three Sequential Steps

### STEP 1: Setup & Metadata

1. **Read first 500 lines** of raw transcript to understand:
   - Speakers (hosts, guests, callers)
   - Major topics
   - Show format

2. **Create new markdown file** named: `[filename]_polished.md` (replace `_raw` with `_polished`)

3. **Add YAML Front Matter at very top:**

```yaml
---
title: "[Descriptive Topic] - [Show Name] [Date]"
show_name: "[Exact show name]"
date: "YYYY-MM-DD"
speakers:
  - "[Full Name]"
  - "[Full Name]"
---
```

---

### STEP 2: Polish Content with Dynamic Headers

**DO NOT create Table of Contents yet.** Go straight to polishing the actual transcript content.

**REMOVE technical/audio sections first:**
- Cut out opening radio mechanics (station IDs, underwriter announcements, fundraising pitches)
- Remove audio troubleshooting: "Can you hear me?", "Sound went down", "Engineer's voice was clear", etc.
- These interruptions break the flow and will be reconstructed as narrative when relevant

**Process:**
1. Polish transcript section by section following the rules below
2. When topic substantially changes, insert a header: `## [Topic Title]`
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

### STEP 3: Generate Table of Contents (VERY END - AFTER ENTIRE POLISHING IS DONE)

**ONLY after the entire transcript is fully polished**, create a Table of Contents and insert it right after the YAML metadata.

**Format:**

```markdown
## Table of Contents

Line X - [[#Chapter Header 1|Chapter Header 1]]
Line Y - [[#Chapter Header 2|Chapter Header 2]]
Line Z - [[#Chapter Header 3|Chapter Header 3]]
```

**Rules:**
- Use "Line X" format (no numbering like "1.", "2.")
- List all major section headers in order
- Get actual line numbers from the polished file
- Insert this TOC section as the first content block after YAML front matter
- Do NOT include key takeaways or descriptions—just the links and line numbers
```

Match TOC entries to headers created during Step 2.

---

## Content Polishing Standards

### Core Principle
**100% FIDELITY to meaning + MAXIMUM READABILITY**

**CRITICAL:** When raw text is awkward, garbled, or unclear, PRESERVE the awkwardness rather than reinterpreting. Use light grammar fixes only. If text is incomprehensible, flag it with [unclear] or [sic] rather than paraphrasing.

### What to ALWAYS Remove:

**REMOVE THESE COMPLETELY - DO NOT INCLUDE IN POLISHED VERSION:**
- **ALL call-in numbers** (707-923-3911, 1-800-XXX-XXXX, etc.) - NEVER include phone numbers
- **ALL station IDs and frequencies** (KMUD 91.1 FM, KMUE Eureka, etc.) - remove repeated announcements
- **ALL technical difficulties** ("Can you hear me?", "Is that better?", "You sound tinny", audio troubleshooting, microphone issues)
- **ALL logistical/scheduling info** ("You're invited to call in from 7:30 to 8:00", "the show runs every third Friday", time announcements)
- **ALL fundraising/pledge drive appeals** (donation requests, membership drives, support appeals)
- **Repeated invitations** to call in or participate in live show format
- **Generic filler** that impedes reading: Excessive "um, uh, you know, like"
- **Incomplete fragments** that don't complete a thought: "So I was going to— well actually—"
- **Redundant acknowledgments** when repeated: "Yeah, yeah, okay, yeah"
- **Show opening/closing mechanics** unless they contain substantive introductions

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

[Continue same speaker's next paragraph without repeating name]

[Another paragraph from same speaker - still no name label]

**[Different Speaker]:** [Their response]
```

**CRITICAL RULES:**
- Use actual names, not "[Speaker A]"
- **NEVER have consecutive same-speaker labels** - if the same person speaks multiple times in a row, merge into ONE speaker block with paragraph breaks between their statements
- Add paragraph breaks WITHIN a speaker's segment when they shift topics or take a breath
- Long monologues (5+ sentences) should be broken into multiple paragraphs for readability
- Only add speaker name when speaker actually changes
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

### Example 3: Long Monologue with Paragraph Breaks

**BEFORE:**
```
[Speaker B]: Yeah. And in the process of getting the ketogenic effect, basically it's starvation and stress that turns on the so called ketone production. But actually the so called ketone bodies, one of the major ketone bodies is actually not a ketone, but an alcohol hydroxyl group as a potential ketone. But in the hydroxyl state which is formed during the ketogenic diet, this becomes a reductant having effect similar to lactic acid, which is a trigger to shift oxidation towards the fermentation or the lactic acid metabolism typical of cancer. And once anything interferes with your ability to oxidize glucose fully, that liberates any stored fatty acids you have in your tissues. And everyone has an abundance of fat mixed right into their functioning tissues.
```

**AFTER:**
```markdown
**Dr. Raymond Peat:** Yeah. In the process of getting the ketogenic effect, basically it's starvation and stress that turns on so-called ketone production. But actually, one of the major ketone bodies is not a ketone, but an alcohol with a hydroxyl group as a potential ketone. In the hydroxyl state which is formed during the ketogenic diet, this becomes a reductant having an effect similar to lactic acid, which is a trigger to shift oxidation towards fermentation or the lactic acid metabolism typical of cancer.

And once anything interferes with your ability to oxidize glucose fully, that liberates any stored fatty acids you have in your tissues. Everyone has an abundance of fat mixed right into their functioning tissues.
```

**What Changed:**
- Light punctuation fixes ("so called" → "so-called")
- **Added paragraph break when topic shifts from ketone bodies to glucose oxidation**
- Broke long monologue into readable chunks

**What Stayed:** Complete technical explanation, Ray's teaching style, 100% content fidelity

### Example 4: NEVER Consecutive Same-Speaker Labels

**BEFORE:**
```
[Speaker C]: I wanted to question you about the lymphatics. I know in breast cancer, lymph nodes become congested. They pick up cancer cells.
[Speaker B]: For.
[Speaker C]: But I wanted to get to the point of the interstitium. What do you understand about this ground substance?
```

**AFTER:**
```markdown
**Andrew Murray:** I wanted to question you about the lymphatics. I know in breast cancer, lymph nodes become congested. They pick up cancer cells.

But I wanted to get to the point of the interstitium. What do you understand about this ground substance?
```

**What Changed:**
- **Merged two Andrew Murray segments into ONE speaker block with paragraph break**
- Removed "[Speaker B]: For." (meaningless audio artifact)
- NO consecutive same-speaker labels

**What Stayed:** Complete question flow, natural paragraph break

### Example 5: Call-In Segment with Removals

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

**What Removed:** "Okay, we're good, let's hold that there" (logistical coordination)
**What Kept:** Call-in interaction, engineer relay, actual question

---

## Processing Notes

Processing happens in chunks with pause points. After every 1,500-2,000 lines of polished content, the process pauses for fidelity review. This ensures technical accuracy is maintained and the approach can be adjusted if needed.

The skill improves iteratively as it's used—feedback from checkpoint reviews informs updates to these guidelines.
