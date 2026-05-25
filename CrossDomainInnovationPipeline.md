# Cross-Domain Innovation pipeline
## Pipeline Designed for Running on Personal Infrastructure
```text
Run the Cross-Domain Innovation pipeline.

## Inputs (update these two lines only)

TOPIC_DISPLAY="People analytics and evidence-based HRM"
DOMAINS="Sports Analytics, Aviation Crew Resource Management, Hospital ICU Burnout, Naval Bridge Resource Management, Air Traffic Control, Emergency Medical Triage, Firefighting Crew Dynamics, Financial Trading Desks, Ant Colony Self-Organization, Military C4ISR Command, Power Grid Load Balancing, Wildlife Migration Patterns, Jazz Ensemble Improvisation, Surgery Team Checklists, Wildlife Firefly Synchronization"

## Derived (auto-computed, don't change)

TOPIC_KEBAB=$(echo "$TOPIC_DISPLAY" | sed 's/[^a-zA-Z0-9]/_/g' | sed 's/__*/_/g')
DATE=$(date +%Y-%m-%d)
BASE_DIR="/data/.openclaw/workspace/cross-domain-research/${TOPIC_KEBAB}/${DATE}_${TOPIC_KEBAB}"

BATCH1_DOMAINS=$(echo "$DOMAINS" | cut -d',' -f1-5)
BATCH2_DOMAINS=$(echo "$DOMAINS" | cut -d',' -f6-10)
BATCH3_DOMAINS=$(echo "$DOMAINS" | cut -d',' -f11-15)

BATCH1_PREV=""
BATCH2_PREV=$BATCH1_DOMAINS
BATCH3_PREV="$BATCH1_DOMAINS, $BATCH2_DOMAINS"

## Auto-calculated completion percentages

PHASE1_PCT=11
PHASE2_PCT=22
PHASE3_PCT=33
PHASE4_PCT=44
PHASE5_PCT=56
PHASE6_PCT=67
PHASE7_PCT=78
PHASE8_PCT=89
# Batch 3: Phase 7 = 89, Phase 8 = 95

## Phase file map (filename has NO batch suffix — batch is only in directory path)

PHASE1_OUT="$BASE_DIR/Batch_1/02_Domain_Discovery/domain_catalog.md"
PHASE2_OUT="$BASE_DIR/Batch_1/03_Domain_Research/domain_research.md"
PHASE3_OUT="$BASE_DIR/Batch_1/05_Translations/software_translations.md"
PHASE4_OUT="$BASE_DIR/Batch_1/06_Candidate_Ideas/candidate_ideas.md"
PHASE5_OUT="$BASE_DIR/Batch_1/07_Critiques/critique.md"           # NOT critique_batch1.md
PHASE6_OUT="$BASE_DIR/Batch_1/08_Survivors/surviving_innovations.md"
PHASE7_OUT="$BASE_DIR/Batch_1/09_Evolution/implementation.md"
PHASE8_OUT="$BASE_DIR/Batch_1/10_Final/executive_summary.md"

## Verify after each write

wc -l $PHASE1_OUT  # ≥20
wc -l $PHASE2_OUT  # ≥100
wc -l $PHASE3_OUT  # ≥100
wc -l $PHASE4_OUT  # ≥50
wc -l $PHASE5_OUT  # ≥80
wc -l $PHASE6_OUT  # ≥50
wc -l $PHASE7_OUT  # ≥100
wc -l $PHASE8_OUT  # ≥50 (150 for cross-batch B3 synthesis)

## Kill Filters — Phase 5

| Filter | Question | Gate |
|--------|---------|------|
| Novelty | Genuine translation or rebranding? | Score 1-10; **≥8 = PASS**, 6-7 = REVISE, <6 = DROP |
| Feasibility | Buildable with current tooling? | Reject underestimation |
| Ethical | Harm/surveillance without opt-in/governance? | Safeguards or DROP |
| Domain Match | Does source mechanism actually map? | Forced analogy = DROP |

**Verdicts:** PASS (≥8 novelty) | REVISE (6-7 novelty) | DROP (<6 novelty)

## Effort Ratings

XS = current sprint | S = team + quarter | M = team + quarter + deps
L = multiple teams + half-year | XL = year+ org-wide

## Pre-Flight Input Check (run before EVERY phase)

Before writing anything for any phase, run:
ls {{PREVIOUS_PHASE_FILE}}
If file does NOT exist: write it yourself using your context knowledge first, then proceed.
Log self-completion in recovery_state.json note field.

## Spawn sequence (run sequentially, verify each step)

# Batch 1 — Phase 1 through Phase 8
# Batch 2 — Phase 1 through Phase 8
# Batch 3 — Phase 1 through Phase 8 (cross-batch synthesis)

## After all 3 batches complete — upload to Drive

BASE_DIR=".../$TOPIC_KEBAB/$DATE_$TOPIC_KEBAB"
TOPIC_FOLDER_ID="..."

gog drive mkdir Batch_1 --parent $TOPIC_FOLDER_ID
# ... same for Batch_2 and Batch_3

for batch in 1 2 3; do
  for phase in 1 2 3 4 6 7 8; do
    # [upload each file to respective batch folder]
  done
done

```
