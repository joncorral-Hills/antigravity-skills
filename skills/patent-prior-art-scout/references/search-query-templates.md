# Search Query Templates — Patent Prior Art Scout

Ready-to-use Boolean query patterns for Google Patents and other databases.
Replace `[TERM]` placeholders with your invention's specific terminology.

---

## Google Patents — Boolean Query Patterns

### Pattern 1: Core Mechanism + Component
```
site:patents.google.com "[core mechanism]" "[key component]"
```
**Example:**
```
site:patents.google.com "conductive thread" "pressure sensing" wearable
```

### Pattern 2: Method Claim Search
```
site:patents.google.com "method for [action]" "[material or medium]"
```
**Example:**
```
site:patents.google.com "method for detecting" "skin contact" "flexible sensor"
```

### Pattern 3: CPC Class + Keyword
```
site:patents.google.com CPC:[class] "[keyword1]" "[keyword2]"
```
**Example:**
```
site:patents.google.com CPC:A61B5/00 "continuous glucose" "non-invasive"
```

### Pattern 4: Assignee-Scoped Search (when a competitor is suspected)
```
site:patents.google.com assignee:"[Company Name]" "[mechanism]"
```
**Example:**
```
site:patents.google.com assignee:"Apple Inc" "blood oxygen" wearable
```

### Pattern 5: Synonym Sweep
Run this pattern multiple times with synonyms to catch what the first search misses:
```
site:patents.google.com ("[term1]" OR "[synonym1]" OR "[synonym2]") "[anchor concept]"
```
**Example:**
```
site:patents.google.com ("smart garment" OR "electronic textile" OR "e-textile") "heart rate"
```

---

## USPTO Full-Text Search (patents.google.com/patent/US...)

Use Google Patents to surface US patents, then verify on:
- [https://ppubs.uspto.gov/pubwebapp/](https://ppubs.uspto.gov/pubwebapp/) — Full-text search
- [https://patft.uspto.gov/](https://patft.uspto.gov/) — Granted patents
- [https://appft.uspto.gov/](https://appft.uspto.gov/) — Published applications

**USPTO Boolean Syntax:**
```
ABST/"[abstract keyword]" AND ACLM/"[claim keyword]"
```
**Example:**
```
ABST/"flexible sensor" AND ACLM/"strain gauge" AND ACLM/"wearable"
```

---

## WIPO Patentscope

URL: [https://patentscope.wipo.int/search/en/search.jsf](https://patentscope.wipo.int/search/en/search.jsf)

**Basic Query:**
```
EN_TI:([mechanism keyword]) AND EN_AB:([component keyword])
```
**Example:**
```
EN_TI:(non-invasive glucose) AND EN_AB:(near infrared spectroscopy)
```

---

## Espacenet (EPO)

URL: [https://worldwide.espacenet.com](https://worldwide.espacenet.com)

**Smart Search Syntax:**
```
ti = "[title keyword]" AND ab = "[abstract keyword]" AND cl = [CPC class]
```
**Example:**
```
ti = "flexible display" AND ab = "foldable substrate" AND cl = G09G
```

---

## Synonym Generation Guide

Before running searches, always generate synonyms for each key term:

| Original Term | Synonyms to Try |
|---|---|
| "wearable device" | "body-worn device", "on-body sensor", "smart garment", "e-textile" |
| "adhesive" | "pressure-sensitive adhesive", "tacky layer", "bonding agent", "self-adhesive" |
| "machine learning" | "neural network", "deep learning", "artificial intelligence", "trained model" |
| "detect" | "sense", "measure", "monitor", "identify", "recognize" |
| "transmit" | "send", "communicate", "broadcast", "relay", "transfer" |
| "flexible" | "conformable", "bendable", "stretchable", "deformable" |

---

## Recommended Search Sequence

Run searches in this order to maximize coverage:

1. **Broad sweep** — Core mechanism only (see Pattern 1)
2. **Synonym sweep** — Same mechanism with synonym set (see Pattern 5)
3. **CPC-filtered** — Narrow by class (see Pattern 3)
4. **Method-specific** — Search claim language directly (see Pattern 2)
5. **Competitor sweep** — Check known players in the space (see Pattern 4)
6. **WIPO sweep** — Catch international filings not indexed by Google Patents
