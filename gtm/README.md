# GTM (Go-to-Market) Automation Examples

**Purpose**: Automation examples organized by GTM motion and use case, applicable across SMB, Mid-Market, and Enterprise companies.

---

## 📁 Directory Structure (Organized by Use Case)

### Core GTM Motions

#### 1. **tam_accounts/** - Total Addressable Market Discovery
Find and qualify target accounts that match your ICP.
- ICP-based account finder agent
- Multi-agent fit scoring
- Vertical market identification

#### 2. **segmentation_targeting/** - Lead Scoring & Segmentation
Score, qualify, and segment leads/accounts for optimal sales focus.
- Autonomous lead scoring (learns over time)
- Intent detection workflows
- Lead scoring engine toolkit

#### 3. **find_decision_makers/** - Contact Discovery
Identify key decision-makers and influencers at target accounts.
- Decision-maker finder agent (production)
- Prospect finder (teaching example)
- Daily orchestrator workflow
- Mobile lead capture

#### 4. **lead_enrichment/** - Data Augmentation
Enrich lead/account records with firmographic, technographic, and contact data.
- Lead research enrichment workflow
- Two-way CRM sync
- Clay-based prospecting automation
- CRM enrichment toolkit

#### 5. **lead_routing/** - Intelligent Lead Assignment
Route leads to the right person, team, or workflow.
- Email routing classifier (AI-powered intent detection)
- Email routing toy example

#### 6. **lead_sequencing/** - Personalized Outreach
Create and execute personalized multi-channel outbound sequences.
- Multi-agent campaign planner
- Personalized email generator
- Website visitor outreach
- Outreach/LinkedIn/follow-up toolkits

#### 7. **funnel_health/** - Pipeline Management & Optimization
Monitor, analyze, and optimize sales funnel performance.
- Autonomous RevOps agent
- Daily metrics digest
- Pipeline reporter toolkit

### Supporting GTM Functions

#### 8. **competitive_intelligence/** - Market Positioning
Monitor competitors and track market positioning.
- Competitor research agent

#### 9. **product_launch/** - Launch Orchestration
Coordinate complex product launches and marketing campaigns.
- Product launch orchestrator
- Campaign launch examples

#### 10. **customer_success/** - Retention & Expansion
Monitor customer health and analyze feedback.
- Customer feedback analysis

#### 11. **reputation_management/** - Brand Monitoring
Monitor and manage online reputation and reviews.
- Google review screenshots automation

#### 12. **market_intelligence/** - Trend Monitoring
Monitor market trends, signals, and emerging opportunities.
- Startup signal detector

#### 13. **partnership_marketing/** - Partner Development
Identify and qualify partnership opportunities.
- Influencer partnership finder
- Mobile app need analyzer

### Utilities

#### 14. **toolkit/** - Cross-Cutting Tools & Utilities
Reusable components that span multiple GTM use cases.

**utilities/** - Discovery and helper tools:
- **department_workflow_mapper/** - Systematically discover automation opportunities
  - Pre-filled prompts for Marketing, Sales, BDR, CS, RevOps, Finance
  - Fill-in-the-blank templates
  - Generate 10 ranked candidates in 5 minutes

**commands/** - Reusable scripts and templates (placeholder):
- CLI commands
- API call templates
- Data transformation scripts

#### 15. **production-ready-examples/** - Real-World Implementations
Production automation examples from actual businesses.
- HubSpot integration examples
- Tool scorer utility
- Website visitor outreach
- CRM enrichment patterns

---

## 🎯 Quick Start by Company Size

### SMB (Small Business)
**Focus**: Fast time-to-value, low complexity, minimal cost

**Recommended Starting Points**:
1. **find_decision_makers/mobile_lead_capture.md** (Tier 0) - Capture leads on the go
2. **lead_routing/email_routing_toy.json** (Tier 2) - Auto-classify incoming emails
3. **funnel_health/daily_metrics_toy.json** (Tier 1) - Daily sales metrics email

### Mid-Market
**Focus**: Scale operations, multi-channel, automation ROI

**Recommended Starting Points**:
1. **tam_accounts/icp_account_finder_agent.py** (Tier 3) - Automate account discovery
2. **find_decision_makers/decision_maker_orchestrator.json** (Tier 1) - Daily research workflow
3. **lead_sequencing/personalized_email_generator_toy.py** (Tier 4) - AI-powered outreach

### Enterprise
**Focus**: Complex orchestration, learning systems, cross-functional

**Recommended Starting Points**:
1. **segmentation_targeting/autonomous_lead_scoring_agent.py** (Tier 6) - Self-improving scoring
2. **product_launch/product_launch_orchestrator.py** (Tier 5) - Complex launch coordination
3. **funnel_health/autonomous_revops_agent.py** (Tier 6) - Autonomous pipeline management

---

## 🔧 By Tier Level

### Tier 0: Simple Triggers
- find_decision_makers/mobile_lead_capture.md

### Tier 1: Deterministic Workflows
- find_decision_makers/decision_maker_orchestrator.json
- funnel_health/daily_metrics_digest.json

### Tier 2: Context-Aware (Single LLM Call)
- segmentation_targeting/intent_detection_workflow.json
- lead_enrichment/lead_research_enrichment.json
- lead_routing/email_routing_classifier.json

### Tier 3: Single-Purpose Agents
- tam_accounts/icp_account_finder_agent.py
- find_decision_makers/decision_maker_finder_agent.py
- competitive_intelligence/competitor_research_agent.py

### Tier 4: Multi-Agent Collaboration
- lead_sequencing/multi_agent_campaign_planner.py
- lead_sequencing/personalized_email_generator_toy.py

### Tier 5: Recursive Task Decomposition
- product_launch/product_launch_orchestrator.py
- product_launch/campaign_launch_toy.py

### Tier 6: Autonomous Specialists
- segmentation_targeting/autonomous_lead_scoring_agent.py
- funnel_health/autonomous_revops_agent.py

---

## 📊 By GTM Stage

### Top of Funnel (Awareness/Interest)
- tam_accounts/ - Find target accounts
- market_intelligence/ - Monitor trends
- partnership_marketing/ - Influencer outreach

### Middle of Funnel (Consideration)
- find_decision_makers/ - Contact discovery
- lead_enrichment/ - Data augmentation
- competitive_intelligence/ - Battle cards

### Bottom of Funnel (Decision/Purchase)
- segmentation_targeting/ - Prioritize high-fit leads
- lead_sequencing/ - Personalized outreach
- funnel_health/ - Pipeline management

### Post-Sale (Retention/Expansion)
- customer_success/ - Health monitoring
- reputation_management/ - Review management

---

## 🚀 Getting Started

1. **Identify Your Use Case**: Choose from the 13 GTM motions above
2. **Match Company Size**: SMB, Mid-Market, or Enterprise patterns
3. **Select Appropriate Tier**: Start simple (Tier 0-2), scale to complex (Tier 3-6)
4. **Follow Setup Guides**: Each example has detailed setup documentation
5. **Iterate & Optimize**: Start with toy examples, move to production

---

## 📖 Additional Resources

- **Workflow Discovery**: Use `department_workflow_mapper/` to systematically find automation opportunities
- **Tool Scorer**: Use `shelf/gtm_tool_scorer.py` to evaluate tools for your stack
- **Integration Examples**: See `shelf/` for real-world CRM integrations

---

## 🎓 Learning Path

1. **Beginner**: Start with Tier 0-1 examples (mobile capture, daily metrics)
2. **Intermediate**: Move to Tier 2-3 (AI classification, autonomous agents)
3. **Advanced**: Explore Tier 4-5 (multi-agent, orchestration)
4. **Expert**: Build Tier 6 (autonomous, learning systems)

---

**Note**: All examples include company size guidance (SMB/MM/ENT) and clear business value statements.

