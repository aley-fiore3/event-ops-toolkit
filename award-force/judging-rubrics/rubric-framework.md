# Judging Rubric Framework for Award Force

A reusable framework for building scoring rubrics that produce consistent, calibrated results across judges.

## The Problem with Most Rubrics

Most rubrics produce inflated scores where 80% of entries land between 4 and 5 on a 5-point scale. This makes differentiation impossible and leads to arbitrary tiebreakers. This framework prevents that.

## Rubric Structure

### Step 1: Define Criteria (3-6 criteria recommended)

Each criterion should be:
- **Independent** — scoring one shouldn't influence another
- **Observable** — judges can point to specific evidence in the submission
- **Weighted** — not all criteria matter equally (weights must total 100%)

### Step 2: Write Score Descriptors

For each criterion, write a descriptor for every score level. The descriptors are the most important part — they're what prevent score inflation.

**Template (5-point scale):**

| Score | Label | Descriptor Template |
|-------|-------|-------------------|
| 1 | Inadequate | {{CRITERION}} is missing, incorrect, or fundamentally flawed. |
| 2 | Below Expectations | {{CRITERION}} is present but has significant gaps or errors. |
| 3 | Meets Expectations | {{CRITERION}} is competent and adequate. This is where an average, acceptable submission should land. |
| 4 | Exceeds Expectations | {{CRITERION}} is strong, thorough, and demonstrates clear quality above the average. |
| 5 | Exceptional | {{CRITERION}} is outstanding and would be a model example. Reserve this for the top 10% of submissions. |

**Key calibration rule:** A score of 3 = "this is fine." Most entries should cluster around 3. If your judges are averaging 4.2 across all entries, the rubric isn't calibrated.

### Step 3: Add Anchor Examples

For each criterion, provide one concrete example of a 2, 3, and 5. Judges calibrate much better with examples than with descriptions alone.

## Example Rubric: Academic Case Competition

| Criterion | Weight | What It Measures |
|-----------|--------|-----------------|
| Ethical Reasoning | 30% | Depth and rigor of ethical analysis; identification of relevant frameworks |
| Analysis Quality | 25% | Logical structure, use of evidence, consideration of alternatives |
| Practical Application | 20% | Feasibility and realism of proposed solutions |
| Communication Clarity | 15% | Organization, clarity of writing/presentation, persuasiveness |
| Creativity of Solution | 10% | Originality and innovation in approach |

### Sample Descriptor: Ethical Reasoning (30%)

| Score | Descriptor |
|-------|-----------|
| 1 | No ethical framework identified. Analysis is purely practical or opinion-based. |
| 2 | An ethical framework is mentioned but not applied meaningfully to the case. |
| 3 | One or more ethical frameworks are identified and applied to the case with adequate reasoning. |
| 4 | Multiple frameworks are applied with nuance, including tensions between them. Shows depth beyond surface analysis. |
| 5 | Sophisticated multi-framework analysis that reveals insights a competent professional might miss. Handles moral ambiguity with clarity. Top 10% quality. |

## Award Force Configuration

In Award Force, map this rubric to:
- **Judging Mode:** Scoring with weighted criteria
- **Score Set:** Create one score set with all criteria
- **Weights:** Enter percentages per criterion
- **Scale:** 1-5 (or 1-10 if you need more granularity)
- **Score Descriptors:** Enter the text from your descriptor table into each criterion's help text

## Judge Calibration Process

1. Before judging opens, send all judges the rubric with anchor examples
2. Have each judge score the SAME sample entry independently
3. Compare scores — if variance is high, discuss the criteria that diverged
4. Adjust descriptors if the language is ambiguous
5. Re-score the sample to verify alignment

## Common Rubric Mistakes

| Mistake | Fix |
|---------|-----|
| All criteria weighted equally | Weight them by actual importance to outcomes |
| No descriptor for "3" / middle score | Write the 3 first — it anchors everything else |
| Criteria overlap (e.g., "quality" and "thoroughness") | Merge or differentiate with clearer definitions |
| "5" descriptor is vague ("excellent") | Describe what "excellent" looks like concretely |
| No anchor examples | Add at least one per criterion |
| Rubric is longer than 2 pages | Judges won't read it — simplify |
