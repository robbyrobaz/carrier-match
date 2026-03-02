# Carrier-Match: Insurance Underwriting Database

A comprehensive reference database for final expense and term life insurance carriers, built to help agents quickly match applicants with the best carriers based on underwriting criteria.

**Status**: ✅ Production Ready | **Version**: 1.0 | **Last Updated**: March 2, 2026

---

## Overview

This repository contains structured data and reference guides for insurance carrier underwriting requirements, organized for fast lookup and decision-making in the field.

### What This Is
- **Agent reference guide** for final expense and term life insurance underwriting
- **Machine-readable database** (JSON) of underwriting conditions by carrier
- **Comparison grids** for quick carrier selection by medical condition
- **Carrier profiles** with products, underwriting philosophies, and contact info

### What This Is NOT
- A compliance tool (always verify current guidelines with carriers)
- A substitute for carrier underwriting guidelines (refer to official docs)
- A web app (repository data; frontend coming separately)
- Legal or medical advice

---

## Quick Start

### For Agents Evaluating an Applicant

1. **Identify the applicant's key conditions** (e.g., "recent heart attack", "age 72 with diabetes")
2. **Check the applicable grid** (see [Grids](#grids) section):
   - Final Expense → `grids/final-expense-grid.md`
   - Term Life → `grids/term-grid.md`
3. **Look up each condition** and see how carriers handle it
4. **Cross-reference the carrier summary** (`carriers/carrier-summary.md`) for turnaround time and face amounts
5. **Submit to the best-fit carriers**

**Example**:
```
Applicant: 65-year-old female, heart attack 8 months ago

Check final-expense-grid.md for "Heart Attack":
- Accendo: Within 1 year - Guaranteed Issue ✓ (BEST)
- Transamerica: Fast underwriting ✓ (GOOD)
- Senior Choice: Within 2 years - Modified ✓ (OK)
- New Vista: 1-2 years - Standard ✓ (OK)

Decision: Submit to Accendo (best terms), Transamerica (fastest)
```

### For Integration/API Users

The JSON file `data/conditions.json` is machine-readable and ready for:
- Web application backends
- Mobile app integration
- Custom decision-tree logic
- Agent portal development

See [Data Format](#data-format) for schema details.

---

## Repository Structure

```
carrier-match/
├── README.md                          # This file
├── grids/
│   ├── final-expense-grid.md          # Master FE underwriting conditions table
│   └── term-grid.md                   # Term life underwriting conditions table
├── carriers/
│   ├── carrier-summary.md             # Quick-reference summary of all carriers
│   ├── americo.md                     # Americo Eagle Select products & UW
│   ├── aetna-accendo.md               # Accendo (Aetna) final expense details
│   ├── ethos.md                       # Ethos product suite & tiers
│   ├── transamerica.md                # Transamerica FE Express
│   ├── mutual-of-omaha.md             # Mutual/United of Omaha & Living Promise
│   ├── senior-choice.md               # Senior Choice whole life (50-85)
│   ├── other-carriers.md              # Reference for additional carriers
│   └── [PROFILES] detailed carrier breakdowns
└── data/
    └── conditions.json                # Machine-readable condition-carrier mappings
```

---

## Files Guide

### Grids (Decision Tables)

#### `grids/final-expense-grid.md`
**Purpose**: Compare final expense carriers across all medical conditions

**Structure**:
- Alphabetical list of 95+ medical conditions
- 5 primary carriers: Accendo, New Vista, Senior Choice, Plan Right, Living Promise
- Underwriting decision for each condition-carrier combo
- Legend explaining tier abbreviations

**Best For**: "Should I submit to Carrier X for this condition?"

**Example Conditions**: AIDS/HIV, Cancer, Cirrhosis, Heart Attack, Diabetes, COPD, Mental Health conditions, etc.

**Legend Terms**:
- DECLINE = Not eligible
- Guaranteed Issue (GI) = Auto-approve, no health questions
- Graded = 2-year benefit ramp (30-40% → 100%)
- Modified = Similar to graded
- ROP = Return of Premium if death <2yrs
- Standard/Preferred/Basic = Tier classification

---

#### `grids/term-grid.md`
**Purpose**: Compare 5 major term life carriers

**Structure**:
- 5 products: Home Mortgage Series, TruStage Term, Family Freedom, TLE/IULE, Term Made Simple
- Same condition-by-carrier format as FE grid
- Product-specific routing info

**Best For**: "Which term carrier is best for this applicant?"

---

### Carriers (Detailed Profiles)

#### `carriers/carrier-summary.md`
**Quick-reference for all carriers**

| Carrier | Product | Ages | Face Amount | Turnaround | Key Strength |
|---------|---------|------|------------|-----------|--------------|
| Accendo | Level/Modified | 45-85 | $2K-$50K | 5-7 days | Flexible with severe conditions |
| Americo | Eagle Select | 40-85 | $5K-$50K | Instant | Instant decisions |
| ... | ... | ... | ... | ... | ... |

**Tables Included**:
- All carriers at a glance
- Age-based recommendations
- Condition-specific carrier selection
- Face amount limits by age
- Premium turnaround comparison
- Payment method acceptance

---

#### `carriers/americo.md`
- **Products**: Eagle Select 1 (Level), Eagle Select 2 (Level, Smoker), Eagle Select 3 (Graded)
- **Issue Ages**: 40-85 (varies by product)
- **Key Feature**: Instant eApplication decisioning
- **Face Amounts**: $5,000 - $50,000
- **Build Chart**: Height/weight requirements
- **Riders**: Accidental Death, Child/Grandchild Term

---

#### `carriers/aetna-accendo.md`
- **Specialty**: Most flexible with severe conditions (many Guaranteed Issue approvals)
- **Products**: Level Preferred, Standard, Modified
- **Strengths**:
  - AIDS/HIV, COPD, Heart Failure, Dementia, Dialysis — all Guaranteed Issue
  - Cirrhosis, Emphysema, Organ Transplant — Guaranteed Issue
  - Recent cardiac events get Guaranteed Issue option
- **Declinable Drugs**: Extensive medication list for various conditions
- **Best For**: Applicants with serious health impairments

---

#### `carriers/transamerica.md`
- **Specialty**: Instant decisioning (<10 minutes)
- **Products**: FE Express (Immediate benefit), Graded FE Express
- **Face Amounts**: $5K-$100K (ages 18-75), $25K (76-85)
- **Competitive Advantage**:
  - Funeral planning concierge service (included)
  - 100% instant decisions
  - Digital platform, eSignature
- **Best For**: Applicants who want fast underwriting & planning support

---

#### `carriers/ethos.md`
- **Specialty**: Digital platform with tier-based routing
- **Products**:
  - Term Life (Prime/Spectrum/Select)
  - Final Expense
  - TruStage products
  - IUL
- **Key Feature**: Routes applicants to appropriate tier rather than declining
- **Best For**: Ages 18-85 with varying health profiles

---

#### `carriers/senior-choice.md`
- **Specialty**: Ages 50-85 whole life
- **Products**: Immediate, Graded, Return of Premium
- **Underwriting**: Moderate; telephone interview typical
- **Riders**: Accidental Death, Grandchild, Nursing Home WP, Terminal Illness
- **Best For**: Seniors 50-85 seeking whole life protection

---

#### `carriers/mutual-of-omaha.md`
- **Specialty**: Living Promise (final expense) + full product line
- **Key Strength**: Flexible with mild-to-moderate conditions
  - Asthma: Mild okay for Preferred
  - Sleep Apnea: Preferred with CPAP compliance
  - Hypertension/Cholesterol treatment doesn't exclude Preferred
  - Family history doesn't apply after age 60
- **Programs**: Fit Underwriting Credits, Express products
- **Best For**: Applicants with controlled chronic conditions

---

#### `carriers/other-carriers.md`
**Reference guide for secondary carriers** not covered in detail:
- American Amicable (very liberal underwriting)
- Corebridge Financial (formerly AIG)
- Foresters Financial
- Instabrain/Ethos partnership
- National Life Group
- Regional carriers

Includes contact info, products, strengths, and when to use.

---

### Data (Machine-Readable)

#### `data/conditions.json`
**Purpose**: Backend-ready JSON for web apps, mobile, APIs

**Structure**:
```json
{
  "carriers": [
    {
      "id": "accendo",
      "name": "Accendo (Aetna)",
      "issue_ages": {"min": 45, "max": 85},
      "face_amounts": {"min": 2000, "max": 50000},
      ...
    }
  ],
  "conditions": [
    {
      "id": "heart_attack",
      "label": "Heart Attack",
      "category": "cardiac_event",
      "carriers": {
        "accendo": "Within 1 year - Guaranteed Issue",
        "new_vista": "Within 1 year - Modified; 1-2 years - Standard; >2 years - Preferred",
        ...
      }
    }
  ]
}
```

**Categories**: Cardiac, Respiratory, Oncology, Neurological, Mental Health, Infectious Disease, Renal, Hepatic, Hematologic, Gastrointestinal, Rheumatological, Metabolic, Legal, Behavioral, etc.

**Validation**:
```bash
python3 -c "import json; json.load(open('data/conditions.json'))" && echo "✓ Valid JSON"
```

---

## How to Use This Data

### For Agents (PDF/Print)

1. Download or print `grids/final-expense-grid.md` and `grids/term-grid.md`
2. Keep `carriers/carrier-summary.md` on your desk for quick reference
3. Refer to detailed carrier profiles as needed

### For Developers/Integrators

1. Parse `data/conditions.json` into your database
2. Build logic around carrier IDs, issue ages, face amounts
3. Create UI to show applicant → matching carriers based on conditions
4. Use condition categories for search/filter features

### For Underwriting/Operations

1. Use grids to validate agent submissions
2. Compare different carrier terms for the same applicant
3. Build internal carrier preference matrix
4. Train new team members on carrier capabilities

---

## Carrier Selection Guide

### Quick Decision Tree

```
Applicant Profile          → Best Carriers
─────────────────────────    ─────────────
Excellent health, <75     → Ethos Prime, National Life
Good health, 40-75        → Americo, Senior Choice, Accendo
Fair health, 50-85        → Accendo, American Amicable, Ethos FE
Complex/severe condition  → Accendo, American Amicable
Immediate decision needed → Transamerica, Americo, Ethos
Terminal/end-stage        → Accendo (GI available)
Ages 75-85                → American Amicable, Accendo
```

### By Condition Severity

| Severity | Best Carriers |
|----------|---------------|
| **Critical (dialysis, advanced cancer)** | Accendo (GI), American Amicable, Ethos FE |
| **Serious (recent heart attack, stroke)** | Accendo (GI), Transamerica, Senior Choice |
| **Moderate (controlled diabetes, asthma)** | Mutual of Omaha, Americo, Ethos Spectrum |
| **Mild (history, well-controlled)** | Any carrier |

---

## Key Data Points by Carrier

| Carrier | Fastest | Most Liberal | Best for Seniors | Best for Digital |
|---------|---------|--------------|------------------|-----------------|
| Accendo | 5-7 days | ✓✓✓ | ✓✓ | Limited |
| Americo | Instant | ✓✓ | ✓ | ✓✓ |
| Transamerica | <10 min | ✓ | ✓ | ✓✓✓ |
| Senior Choice | 5-7 days | ✓✓ | ✓✓✓ | Limited |
| Ethos | Instant | ✓✓ | ✓ | ✓✓✓ |
| Mutual of Omaha | 7-10 days | ✓✓ | ✓✓ | ✓ |

---

## Important Notes

### Accuracy & Updates
- **Data current as of**: March 2026
- **Source**: Official carrier underwriting guidelines (2025-2026)
- **Always verify** with current carrier documentation before submission
- Underwriting guidelines change; check carrier websites for updates

### Limitations
- **This is reference only** — not binding
- **State variations** not captured (some carriers vary by state)
- **Product availability** changes; verify state licensing
- **Rates and terms** vary and are not included
- **Recent guideline changes** may not be reflected

### Legal Disclaimer
This database is informational only. Agents must:
1. Maintain active producer license
2. Verify current carrier guidelines
3. Comply with state insurance regulations
4. Obtain required disclosures from applicants
5. Follow carrier application procedures

---

## Getting Started

### Step 1: Understand the Grids
Read the legend in `grids/final-expense-grid.md` to understand abbreviations:
- GI = Guaranteed Issue
- Graded = 2-3 year benefit ramp
- Modified = Similar to graded
- ROP = Return of Premium
- Standard/Preferred/Basic = Underwriting tiers

### Step 2: Find Your Applicant's Conditions
Look up each medical condition in the appropriate grid (FE or Term).
Example: "Applicant has diabetes + heart attack (6 months ago)"

### Step 3: See Which Carriers Accept
Read the columns to see each carrier's decision:
- Accendo: "Within 1 year - Guaranteed Issue" ✓ BEST
- Senior Choice: "Within 2 years - Modified" ✓ OK
- New Vista: "Between 1-2 years - Standard" ✓ OK

### Step 4: Check Details & Turnaround
Reference `carriers/carrier-summary.md` for:
- Issue ages (is applicant eligible?)
- Face amount limits (can they get the requested amount?)
- Turnaround time (how fast do you need a decision?)
- Payment methods (does applicant use online-only bank?)

### Step 5: Submit to Best Matches
Use detailed carrier profiles for contact info and submission instructions.

---

## Data Quality

### Validation Checklist
- ✓ All 95+ conditions from master grid included
- ✓ All 5 primary final expense carriers represented
- ✓ Term carriers grid created
- ✓ JSON validated as parseable
- ✓ Carrier summaries cross-checked

### Known Gaps
- Regional carriers (state-specific) not fully detailed
- New products launched after March 2026 may not be included
- Some carriers' recent guideline changes pending
- Medical condition edge cases not exhaustively documented

---

## Contributing

### Suggestions
Found an error or outdated info? Report via GitHub Issues.

### Format
- Markdown for carrier profiles (GitHub-readable)
- JSON for conditions database (machine-parseable)
- Plain tables for quick reference

### Updating Guidelines
When carriers release new guidelines:
1. Update relevant markdown file
2. Update JSON if condition/rating changes
3. Update `carriers/carrier-summary.md`
4. Create new commit with source document reference

---

## Resources & References

### Carrier Websites
- **Americo**: americalife.com | AmericoFinalExpense.com
- **Accendo/Aetna**: aetna.com
- **Transamerica**: transamerica.com
- **Ethos**: ethos.com
- **Senior Choice**: seniorchoiceinsurance.com
- **Mutual of Omaha**: mutualofomaha.com

### Industry Resources
- NAIC (National Association of Insurance Commissioners)
- NAIFA (National Association of Insurance and Financial Advisors)
- StateRate.com (rate and availability info)
- Insure.com (consumer data)

### Regulatory
- State insurance departments (verify licensing)
- NFIP (National Flood Insurance Program)
- MIB Group (Medical Information Bureau)

---

## Version History

| Version | Date | Notes |
|---------|------|-------|
| **1.0** | Mar 2, 2026 | Initial release: 95 conditions, 5 FE carriers, 5 term carriers, full JSON export |

---

## License & Attribution

**Data Source**: Official insurance carrier underwriting guidelines (2025-2026)
**Compiled by**: Claude Code | **For**: Insurance agent reference

**Use**: For licensed insurance agents evaluating applicant eligibility.
**Share**: Permitted for internal agent use; not for public distribution.

---

## Support & Questions

### For Agent Questions
- Contact your carrier's underwriting department directly
- Call carrier support numbers listed in each profile
- Check carrier websites for current guidelines

### For Database/Integration Questions
- Review `data/conditions.json` schema
- Check carrier profiles for contact information
- Refer to GitHub Issues for known limitations

---

## Next Steps

### Planned Enhancements
- [ ] Web app frontend for interactive matching
- [ ] Mobile app for field use
- [ ] Integration with agency management systems
- [ ] Real-time carrier guideline updates
- [ ] Rate comparison module
- [ ] State-specific availability matrix
- [ ] Rider and benefit options database

---

**Last Updated**: March 2, 2026
**Status**: Ready for Production Use
**Questions?** See [Support & Questions](#support--questions) above

---

*This repository is maintained for licensed insurance agents. Always verify current carrier guidelines and state regulations before submission.*
