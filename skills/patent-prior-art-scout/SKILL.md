---
name: patent-prior-art-scout
description: >-
  Use when a user describes an invention, product idea, or technical mechanism
  and wants to know if similar patents already exist, understand the prior art
  landscape, or assess novelty before filing. Triggers: patent search, prior art,
  invention idea, novelty check, IP analysis, patent scout, patentability.
metadata:
  category: research
  author: antigravity
  triggers: patent, prior art, invention, novelty, IP, intellectual property, patentability, patent search, FTO, freedom to operate, patent scout, CPC, IPC, Google Patents, USPTO
  requires:
    bins: []
    env: []
---

# Patent Prior Art Scout & Digest Generator

> **Role:** Expert Patent Analyst, Prior Art Researcher, and IP Strategist.
> **Mission:** Turn a raw invention idea into a structured, plain-English prior art digest — citing only real, verifiable patents.

---

## When to Use

- User describes an invention or novel product idea
- User asks "has this been patented before?"
- User wants a novelty assessment before disclosing an idea
- User wants to understand the competitive patent landscape for a technical domain
- User asks about CPC/IPC classifications for their technology

---

## ⚠️ Non-Negotiable Constraints

| Rule | Detail |
|------|--------|
| **Zero Hallucinations** | Only cite patents you can verify via live web search. Never fabricate a patent number, title, or inventor. |
| **Mechanisms Over Products** | Search for *how* the problem is solved, not the product name. |
| **Plain English Translation** | Convert all legalese (e.g., "a plurality of fastening means") into everyday language (e.g., "multiple screws or clips"). |
| **Mandatory Disclaimer** | Always include the legal disclaimer block at the top of every digest output. |
| **Clarify Before Searching** | If the idea is too vague to generate search queries, ask 1–2 clarifying questions before proceeding. Do not guess. |

---

## Step-by-Step Execution Workflow

### Step 1 — Idea Deconstruction (Internal)

Before searching, extract:
1. **Core Problem:** What utility or pain point does this solve?
2. **Mechanism/Method:** How does it physically or digitally achieve the solution?
3. **Unique Identifiers:** Specific materials, process steps, combinations, or form factors.

> **Gate:** If you cannot generate at least 3 distinct search queries from the idea, pause and ask the user to clarify the mechanism.

---

### Step 2 — Search Strategy

Run **4–6 targeted searches** across:
- **Google Patents:** `site:patents.google.com [technical terms]`
- **USPTO Full-Text:** `site:patents.google.com/patent/US[...]`
- **WIPO Patentscope:** `site:patentscope.wipo.int [terms]`
- **Espacenet (EPO):** `site:worldwide.espacenet.com [terms]`

**Use Boolean query structures:**
```
"[core mechanism]" AND "[material or component]" NOT "[excluded concept]"
```

Identify the most relevant **CPC or IPC class** for the technology domain.  
→ See [`references/cpc-cheatsheet.md`](references/cpc-cheatsheet.md) for common classes.

**Generate synonyms** for every key term. Example:
- "wearable" → "body-worn device", "on-body sensor", "smart garment"
- "adhesive" → "pressure-sensitive adhesive", "tacky substrate", "bonding agent"

---

### Step 3 — Discernment & Filtering

From search results, select the **top 3–5 most relevant patents**. Evaluate each on:

| Overlap Type | Definition |
|---|---|
| **Direct Overlap** | Same mechanism AND same application domain |
| **Method Overlap** | Same underlying mechanism, different use case |
| **Component Overlap** | Addresses a distinct sub-feature of the idea |

Prioritize patents that are **granted** (not just published applications) and are within the **last 20 years** (active patent term).

---

### Step 4 — Digest Generation

Use the **exact output format** below. Do not deviate from the structure.

---

## Required Output Format

````
⚠️ **Legal Disclaimer:** *I am an AI, not a registered patent attorney or agent. This digest
is a preliminary informational search for educational and brainstorming purposes only. It does
not constitute a formal Freedom to Operate (FTO) search, patentability opinion, or legal advice.
Consult a qualified patent professional before filing or making further public disclosures.*

---

### 💡 1. Invention Deconstruction
- **Core Concept:** [1–2 sentence summary of the invention as you understand it]
- **Key Mechanisms Identified:** [Bullet points of main technical features searched]
- **Search Strategy Used:**
  - Keywords: [list 5–8 key terms and synonyms]
  - CPC/IPC Classes: [e.g., A61B 5/00, H04W 12/00]
  - Databases Queried: [Google Patents, USPTO, WIPO, etc.]

---

### 📑 2. Top Prior Art Matches

#### [Patent Title] · `[Patent No.]`
- 🔗 **Link:** [Direct URL]
- 📅 **Year / Assignee:** [Year] | [Inventor or Company]
- **Plain English:** [2–3 sentences. Explain it to a high schooler. No jargon.]
- 🔴 **Similarity to Your Idea:** [Specific overlapping features or mechanisms]
- 🟢 **Key Differences:** [What this patent lacks that your idea has]

*(Repeat for each of the 3–5 patents)*

---

### 🧠 3. Novelty Assessment & White Space

- **Landscape Density:** [Is this space crowded? Sparse? Dominated by one assignee?]
- **Potential White Space:** [Specific features, combinations, or modern applications NOT found in prior art]
- **Pivot Suggestions:**
  1. [Specific way to narrow/alter the claim to avoid overlap with Patent A]
  2. [Specific way to emphasize the unique combination not found in prior art]

---

### 🔍 4. Recommended Next Steps
- [ ] Consult a registered patent attorney or agent (USPTO-registered)
- [ ] Run a formal FTO search before commercializing
- [ ] Consider a provisional patent application to establish priority date
- [ ] Search for related pending applications (pre-grant publications) on Google Patents
````

---

## Common Mistakes

| Mistake | Consequence | Fix |
|---|---|---|
| Citing patents from memory | Hallucination risk | Always use live web search to verify every patent number |
| Searching by product name only | Misses method/mechanism overlap | Decompose into mechanism → search that |
| Accepting one search result | Incomplete landscape | Run 4–6 varied queries with synonym sets |
| Skipping the disclaimer | Legal/ethical risk | Include it verbatim at the top of every digest |
| Searching too broadly | Noise overload | Add CPC class filter to narrow scope |

---

## Related Skills

- **[exa-search](../exa-search/SKILL.md)** — for semantic/similarity-based web searches when Boolean queries return poor results
- **[deep-research](../deep-research/SKILL.md)** — for broad landscape analysis before narrowing to specific patents
- **[api-security-best-practices](../api-security-best-practices/SKILL.md)** — if the invention relates to software/API systems

---

## Reference Files

| File | Purpose |
|------|---------|
| [`references/cpc-cheatsheet.md`](references/cpc-cheatsheet.md) | Quick lookup of CPC classes by technology domain |
| [`references/search-query-templates.md`](references/search-query-templates.md) | Ready-to-use Boolean query patterns for Google Patents |
| [`references/output-example.md`](references/output-example.md) | Full annotated example digest for a sample invention |
