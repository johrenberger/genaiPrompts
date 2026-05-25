# Cross-Domain Innovation pipeline
## Pipeline Designed for Running on Personal Infrastructure
```text
Run the Cross-Domain Innovation pipeline.

## Inputs (update these two lines only)

TOPIC_DISPLAY="AI/ML Ops"
DOMAINS="Seismology, Air Traffic Control, Military C4ISR, Weather Forecasting, Nuclear Reactor Control, Aviation TCAS, Manufacturing SPC, Telecom SON, Emergency CAD, Pharmaceutical Stability, Hospital ICU, Financial Trading, Power Grid, Spacecraft, Clinical Trials"

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
# Batch 3 Phase 7: 89, Phase 8: 95

## Phase file map

PHASE1_OUT="$BASE_DIR/Batch_1/02_Domain_Discovery/domain_catalog.md"
PHASE2_OUT="$BASE_DIR/Batch_1/03_Domain_Research/domain_research.md"
PHASE3_OUT="$BASE_DIR/Batch_1/05_Translations/software_translations.md"
PHASE4_OUT="$BASE_DIR/Batch_1/06_Candidate_Ideas/candidate_ideas.md"
PHASE5_OUT="$BASE_DIR/Batch_1/07_Critiques/critique_batch1.md"
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
wc -l $PHASE8_OUT  # ≥50

## Spawn sequence (run sequentially, verify each step)

# Batch 1 — Phase 1
# [spawn subagent with Phase 1 prompt + BATCH1_DOMAINS + $BATCH1_PREV]

# ... continue through Phase 8 for Batch 1, then Batch 2, then Batch 3

## Kill Filters (Phase 5)

1. Novelty: genuine translation or rebranding?
2. Feasibility: buildable with current tooling?
3. Ethical: harm/surveillance without opt-in?
4. Domain Match: source mechanism actually maps to problem?

Verdicts: PASS | REVISE (salvage core) | DROP

## Effort Ratings

XS = current sprint | S = team + quarter | M = team + quarter + deps
L = multiple teams + half-year | XL = year+ org-wide

## After all 3 batches complete — upload to Drive

BASE_DIR=".../$TOPIC_KEBAB/$DATE_$TOPIC_KEBAB"
TOPIC_FOLDER_ID="..."

gog drive mkdir Batch_1 --parent $TOPIC_FOLDER_ID
gog drive mkdir Batch_2 --parent $TOPIC_FOLDER_ID
gog drive mkdir Batch_3 --parent $TOPIC_FOLDER_ID

# Upload all files (27 total: 9 per batch × 3 batches)

```
