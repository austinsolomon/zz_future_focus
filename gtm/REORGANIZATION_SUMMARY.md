# GTM Folder Reorganization Summary

**Date**: 2025-12-01
**Change**: Reorganized from tier-based structure to use-case-based structure

---

## ✅ Reorganization Complete

### What Changed

**Old Structure** (Tier-Based):
- tier_examples/tier_0-6/ - Organized by automation complexity
- toolkit/ - Reusable templates
- shelf/ - Production examples

**New Structure** (Use Case-Based):
- **13 GTM Motion Folders** - Organized by business value
- Each folder includes SMB/MM/ENT guidance
- Tier information preserved in file metadata

---

## 📁 New Folder Structure

### 1. **tam_accounts/** - Total Addressable Market Discovery
- icp_account_finder_agent.py (Tier 3)
- multi_agent_fit_scoring.md (Shelf)
- vertical_market_identifier/ (Toolkit)

### 2. **segmentation_targeting/** - Lead Scoring & Segmentation
- autonomous_lead_scoring_agent.py (Tier 6)
- intent_detection_workflow.json (Tier 2)
- lead-scoring-engine/ (Toolkit)

### 3. **find_decision_makers/** - Contact Discovery
- decision_maker_finder_agent.py (Tier 3 Production)
- prospect_finder_toy.py (Tier 3 Teaching)
- decision_maker_orchestrator.json (Tier 1 Orchestration)
- mobile_lead_capture.md (Tier 0 iOS)

### 4. **lead_enrichment/** - Data Augmentation
- lead_research_enrichment.json (Tier 2)
- two_way_crm_sync.md (Shelf)
- clay_prospecting_automation.md (Shelf)
- 6-crm-enrichment/ (Toolkit)

### 5. **lead_routing/** - Intelligent Assignment
- email_routing_classifier.json (Tier 2 Production)
- email_routing_toy.json (Tier 2 Teaching)

### 6. **lead_sequencing/** - Personalized Outreach
- multi_agent_campaign_planner.py (Tier 4)
- personalized_email_generator_toy.py (Tier 4 Teaching)
- website_visitor_outreach.md (Shelf)
- 7-outreach-generator/, 8-linkedin-automator/, 9-followup-manager/ (Toolkits)

### 7. **funnel_health/** - Pipeline Monitoring & RevOps
- autonomous_revops_agent.py (Tier 6)
- daily_metrics_digest.json (Tier 1 Production)
- daily_metrics_toy.json (Tier 1 Teaching)
- 10-pipeline-reporter/ (Toolkit)

### 8. **competitive_intelligence/** - Competitor Monitoring
- competitor_research_agent.py (Tier 3)

### 9. **product_launch/** - Launch Orchestration
- product_launch_orchestrator.py (Tier 5)
- campaign_launch_toy.py (Tier 5 Teaching)

### 10. **customer_success/** - Customer Health
- customer_feedback_analysis.md (Shelf)

### 11. **reputation_management/** - Review Monitoring
- google_review_screenshots.md (Shelf)

### 12. **market_intelligence/** - Trend Monitoring
- 1-startup-signal-detector/ (Toolkit)

### 13. **partnership_marketing/** - Partner/Influencer ID
- 3-influencer-partnership-finder/ (Toolkit)
- 4-mobile-app-need-analyzer/ (Toolkit)

### Utilities (Unchanged)
- **department_workflow_mapper/** - Workflow discovery system
- **shelf/** - Real-world examples and utilities

---

## 🎯 Key Improvements

### Before (Tier-Based)
```
Problem: "I need to find decision-makers"
→ Search across tier_examples/tier_0/, tier_1/, tier_3/
→ Find 3 different approaches
→ Don't know which is right for my company size
```

### After (Use Case-Based)
```
Problem: "I need to find decision-makers"
→ Go to find_decision_makers/
→ See all options with SMB/MM/ENT guidance
→ Choose based on company size and complexity needs
```

### Benefits
1. **Business-First Navigation**: Organized by what you're trying to accomplish
2. **Company Size Guidance**: Each folder has SMB/Mid-Market/Enterprise applications
3. **Complete Context**: All approaches for a use case in one place
4. **Tier Transparency**: Tier info still visible in filenames and docstrings

---

## 📝 File Metadata Updates

All files updated with:
- **USE CASE** header
- **Business Value** statement
- **Company Size Application** (SMB/MM/ENT)
- **Tier** level preserved

Example:
```python
"""
TAM Accounts - ICP-Based Account Finder Agent

USE CASE: Total Addressable Market (TAM) Account Discovery
TIER: 3 (Single Agent with Tools)

Business Value:
- Automatically discover accounts matching your Ideal Customer Profile
- Score and prioritize accounts by fit before sales outreach
- Scale TAM research from manual (5-10 accounts/day) to automated (100s/day)

Company Size Application:
- SMB: Fast discovery with basic scoring (5-10 criteria)
- Mid-Market: Detailed scoring with 10-15 criteria + tech stack analysis
- Enterprise: Deep profiling with competitive intel and stakeholder mapping
"""
```

---

## 🔍 How to Find Examples

### By Business Problem
| I Need To... | Go To Folder |
|-------------|--------------|
| Find target accounts | `tam_accounts/` |
| Score/qualify leads | `segmentation_targeting/` |
| Find decision-makers | `find_decision_makers/` |
| Enrich contact data | `lead_enrichment/` |
| Route leads intelligently | `lead_routing/` |
| Personalize outreach | `lead_sequencing/` |
| Monitor pipeline | `funnel_health/` |
| Track competitors | `competitive_intelligence/` |
| Launch products | `product_launch/` |

### By Company Size
Each folder README includes specific guidance:
- **SMB**: Simple, fast, low-cost (Tier 0-2)
- **Mid-Market**: Balanced automation with ROI (Tier 2-4)
- **Enterprise**: Complex systems (Tier 4-6)

### By Tier Level (Still Available)
All Tier 3 agents across use cases:
- `tam_accounts/icp_account_finder_agent.py`
- `find_decision_makers/decision_maker_finder_agent.py`
- `competitive_intelligence/competitor_research_agent.py`

---

## 📚 Updated Documentation

✅ **gtm/README.md** - Master index with quick start by company size
✅ **CLAUDE.md** - Updated GTM domain architecture section
✅ **13 Folder READMEs** - Use case descriptions and examples
✅ **REORGANIZATION_SUMMARY.md** - This file

---

## ⚠️ Migration Notes

### Backwards Compatibility
- Old `tier_examples/` folder **still exists** (deprecated, not deleted)
- Old `toolkit/` folder **still exists** (deprecated, not deleted)
- All file contents **unchanged** (only metadata updated)
- Import paths need updating if you reference files directly

### What's Deprecated
- ❌ `gtm/tier_examples/` - Use new use-case folders instead
- ❌ `gtm/toolkit/` - Templates moved to relevant use-case folders

### What's Unchanged
- ✅ `gtm/department_workflow_mapper/` - Workflow discovery system
- ✅ `gtm/shelf/` - Real-world examples (some files copied to use-case folders)
- ✅ File contents and logic
- ✅ Tier characteristics and patterns

---

## 🚀 Next Steps

1. **Browse by Use Case**: Explore folders relevant to your GTM motion
2. **Check Company Size**: Each README has SMB/MM/ENT recommendations
3. **Start Simple**: Use toy examples to learn patterns
4. **Scale Up**: Move to production examples when ready
5. **Reference Tiers**: Tier info preserved for learning/comparison

---

**Questions?** See `gtm/README.md` for complete navigation guide.

---

## 🔄 Phase 2 Updates (2025-12-01 - Later)

### Additional Cleanup

✅ **Removed**:
- `tier_examples/` - Old tier-based structure (deprecated)
- `dept_mapping/` - Empty placeholder folder
- `toolkit/recurring/` - Examples moved to use-case folders
- `toolkit/special_task/` - Examples moved to use-case folders

✅ **Renamed**:
- `shelf/` → `production-ready-examples/` (clearer naming)

✅ **Reorganized**:
- `department_workflow_mapper/` → `toolkit/utilities/department_workflow_mapper/`
- Created `toolkit/commands/` (placeholder for future reusable scripts)

### New Structure: toolkit/

**toolkit/utilities/**:
- department_workflow_mapper/ - Workflow discovery system

**toolkit/commands/**:
- Placeholder for reusable commands/scripts
- Future: CLI commands, API templates, data transformers

### Benefits
1. **Cleaner root**: Removed deprecated folders
2. **Organized utilities**: toolkit/ contains cross-cutting tools
3. **Clear naming**: "production-ready-examples" vs "shelf"
4. **Future-ready**: toolkit/commands/ for reusable components

---

## 📁 Final GTM Structure

```
gtm/
├── 13 Use Case Folders (Core GTM Motions)
│   ├── tam_accounts/
│   ├── segmentation_targeting/
│   ├── find_decision_makers/
│   ├── lead_enrichment/
│   ├── lead_routing/
│   ├── lead_sequencing/
│   ├── funnel_health/
│   ├── competitive_intelligence/
│   ├── product_launch/
│   ├── customer_success/
│   ├── reputation_management/
│   ├── market_intelligence/
│   └── partnership_marketing/
│
├── toolkit/                        # Cross-cutting utilities
│   ├── utilities/
│   │   └── department_workflow_mapper/
│   └── commands/                   # (placeholder)
│
└── production-ready-examples/      # Real-world implementations
```

---

## 🎯 All Changes Complete

The GTM folder is now:
- ✅ Organized by business use case (not tier)
- ✅ Clean (no deprecated folders)
- ✅ SMB/MM/ENT guidance in every folder
- ✅ Utilities properly separated
- ✅ Production examples clearly labeled

