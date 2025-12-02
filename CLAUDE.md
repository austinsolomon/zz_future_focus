# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## Repository Purpose

This is the **Automation Architecture** repository - a tiered automation framework (Tiers 0-6) spanning from simple iOS Shortcuts to fully autonomous AI agents. It serves as both:
1. **Reference Implementation**: 57 production-ready examples across 3 domains (GTM, UE5, BR2)
2. **Orchestration Hub**: The intended central automation system for the learn_profit workspace

**Core Concept**: Route workflows to appropriate automation tiers based on complexity, from deterministic triggers (Tier 0-1) to AI-enhanced workflows (Tier 2-3) to autonomous multi-agent systems (Tier 4-6).

---

## Quick Start Commands

### Setup and Environment

```bash
# Initial setup (installs Python, Node.js, n8n, LangChain, etc.)
./setup.sh          # macOS/Linux
.\setup.ps1         # Windows PowerShell

# Activate Python environment (required for Tier 3+ examples)
source venv/bin/activate        # macOS/Linux
.\venv\Scripts\Activate.ps1     # Windows

# Start n8n workflow automation (for Tier 1-2 examples)
n8n start
# Access at http://localhost:5678

# Install example-specific dependencies
pip install -r <tier_example_directory>/requirements.txt
```

### Environment Configuration

Create `.env` in project root:

```bash
# Minimum for AI examples (Tier 2+)
ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxx

# For agent examples (Tier 3+)
SERPER_API_KEY=xxxxxxxxxxxxx          # Web search
PROXYCURL_API_KEY=xxxxxxxxxxxxx       # LinkedIn data (optional)
HUBSPOT_API_KEY=xxxxxxxxxxxxx         # CRM integration (optional)

# For BR2 examples
OBSIDIAN_VAULT_PATH=/path/to/vault

# For UE5 examples
UE5_PROJECT_PATH=/path/to/unreal/project
```

### Running Examples

```bash
# Tier 0: iOS Shortcuts (no commands - read markdown instructions)
cat gtm/tier_examples/tier_0/tier_0_toy_ios_shortcuts_gtm_lead_capture.md

# Tier 1: n8n workflows
# 1. Start n8n: n8n start
# 2. Open http://localhost:5678
# 3. Import: gtm/tier_examples/tier_1/tier_1_toy_n8n_gtm_daily_metrics.json

# Tier 2: AI-enhanced n8n
# Same as Tier 1, but requires ANTHROPIC_API_KEY in n8n credentials

# Tier 3+: Python agents
cd gtm/tier_examples/tier_3
python tier_3_toy_langchain_gtm_prospect_finder.py

# Production examples with CLI args
python tier_3_cldchoice_gtm_lead_research.py --company "Acme Corp"
```

### Using the Tier Wizard

```bash
# Interactive tier determination (built-in slash command)
/tier-wizard
```

This wizard asks yes/no questions to determine the correct tier (0-6) for a workflow.

---

## Architecture Overview

### The 7-Tier Hierarchy

The system routes workflows based on complexity:

| Tier | Complexity | Tools | Example |
|------|------------|-------|---------|
| **0** | Simple triggers | iOS Shortcuts, Keyboard Maestro | Voice capture to Obsidian |
| **1** | Deterministic workflows | n8n, Make | Daily sales metrics email |
| **2** | Context-aware (1 LLM call) | n8n + Claude API | Email intent classifier |
| **3** | Single-purpose agents | LangChain + tools | Research agent finds decision-makers |
| **4** | Multi-agent collaboration | LangGraph, CrewAI | Campaign planner (researcher + writer + analyst) |
| **5** | Recursive task decomposition | Claude Code + subagents | Build complete sales enablement system |
| **6** | Autonomous specialists | Full stack + persistent memory | Autonomous RevOps agent |

**Key Decision Points**:
- No AI needed → Tier 0-1
- One AI call for reasoning → Tier 2
- AI needs tools/multi-step → Tier 3
- Multiple specialized AIs → Tier 4+
- Learning from feedback → Tier 6

### Directory Structure

```
automation_architecture/
├── get_started/                    # Start here
│   ├── QUICKSTART.md              # 5min to 1hr getting started paths
│   ├── EXAMPLES_SUMMARY.md        # Complete inventory of 57 examples
│   └── intake_examples/           # Templates for submitting workflows
├── intake_system/                  # Workflow submission & routing
│   ├── README.md                  # Full intake system docs
│   ├── intake_form_template.md    # 7-section intake form
│   ├── submission_guide.md        # How to fill out intake
│   ├── submit_workflow.py         # CLI for submissions
│   └── intake_database_schema.sql # PostgreSQL schema
├── utilities/
│   └── tier_routing_wizard.md     # Tier determination logic
├── tool_stack/                     # Learning materials by tool
│   ├── claude_code/               # Claude Code concepts & patterns
│   ├── n8n/                       # n8n workflow patterns
│   ├── langchain/                 # LangChain agent patterns
│   ├── langgraph/                 # Multi-agent orchestration
│   └── shortcuts/                 # iOS automation patterns
├── gtm/                           # Go-to-Market domain (organized by use case)
│   ├── tam_accounts/              # TAM discovery & ICP-based account finding
│   ├── segmentation_targeting/    # Lead scoring & segmentation
│   ├── find_decision_makers/      # Contact discovery & intelligence
│   ├── lead_enrichment/           # Data augmentation (firmographic/technographic)
│   ├── lead_routing/              # Intelligent lead assignment
│   ├── lead_sequencing/           # Personalized multi-channel outreach
│   ├── funnel_health/             # Pipeline monitoring & RevOps
│   ├── competitive_intelligence/  # Competitor monitoring
│   ├── product_launch/            # Launch orchestration
│   ├── customer_success/          # Customer health & feedback
│   ├── reputation_management/     # Review monitoring
│   ├── market_intelligence/       # Trend monitoring & signals
│   ├── partnership_marketing/     # Partner/influencer identification
│   ├── toolkit/                   # Cross-cutting utilities
│   │   ├── utilities/             # Discovery tools (workflow mapper)
│   │   └── commands/              # Reusable scripts (placeholder)
│   └── production-ready-examples/ # Real-world implementations
├── ue5/                           # Unreal Engine 5 domain
│   └── [same structure as gtm/]
├── br2/                           # Building a Second Brain domain
│   └── [same structure as gtm/]
└── law/                           # Legal automation domain
    └── [same structure as gtm/]
```

### File Naming Conventions

**Pattern**: `tier_X_[type]_[domain]_[name].[ext]`

- `tier_X`: Tier number (0-6)
- `[type]`:
  - `toy_` = Minimal teaching example (~50-100 lines)
  - `cldchoice_` = Production-ready example (Claude Code's personal choice)
  - No prefix = Reference implementation
- `[domain]`: `gtm`, `ue5`, `br2`, `law`
- `[name]`: Descriptive workflow name

**Extensions**:
- `.md` = iOS Shortcut instructions or setup guide
- `.json` = n8n workflow (import to n8n UI)
- `.py` = LangChain/LangGraph agent

**Examples**:
- `tier_0_toy_ios_shortcuts_gtm_lead_capture.md` - Teaching example for Tier 0 GTM
- `tier_3_cldchoice_gtm_lead_research.py` - Production Tier 3 GTM agent
- `tier_2_n8n_claude_email_classifier.json` - n8n workflow with Claude integration

---

## Core Systems

### 1. Intake System (`intake_system/`)

**Purpose**: Structured workflow submission, validation, tier routing, and ROI calculation.

**Key Components**:
- **7-section intake form**: Problem statement → Manual process → Desired automation → Success criteria → Constraints → Complexity signals → Context
- **PostgreSQL schema**: Stores submissions, tracks executions, measures ROI
- **CLI submission tool**: `submit_workflow.py`
- **Tier routing logic**: Maps complexity signals to tiers 0-6

**Workflow**:
1. Export template: `python submit_workflow.py --export-template workflow.yaml`
2. Fill out 7 sections
3. Validate: `python submit_workflow.py --file workflow.yaml --validate-only`
4. Submit: `python submit_workflow.py --file workflow.yaml`
5. Receive submission ID (e.g., `WF-2024-001`)
6. Review → Tier assignment → Approval → Implementation → Deployment

**ROI Formula**:
```
ROI Score = (Weekly Hours × $100/hr × 52 weeks) / (Build Hours × $150/hr)
```

### 2. Department Workflow Discovery (`gtm/department_workflow_mapper/`)

**Purpose**: Systematically discover high-ROI automation candidates for any department.

**Files**:
- `workflow_discovery_prompt.md` - Full framework
- `workflow_discovery_examples.md` - Pre-filled prompts for 6 departments
- `workflow_discovery_quick_start.md` - Fill-in-the-blank template

**Usage**:
1. Copy department prompt from `workflow_discovery_examples.md`
2. Paste into Claude
3. Receive 10 ranked workflow candidates with:
   - Priority score (1-10)
   - Time burden (hours/week)
   - ROI estimate
   - Ready-to-submit intake preview
4. Submit top 3 via intake system

**Supported Departments**: Marketing, Sales, BDR, Customer Success, RevOps, Finance

### 3. Tier Wizard (`/tier-wizard` slash command)

**Purpose**: Interactive yes/no questions to determine correct tier for a workflow.

**Flow**:
1. Domain context (GTM/UE5/BR2/Law)
2. Does it need AI? → No = Tier 0-1, Yes = continue
3. Multi-step logic? → No = Tier 0, Yes = Tier 1
4. Multi-step AI decisions? → No = Tier 2, Yes = continue
5. Multiple specialized agents? → No = Tier 3, Yes = Tier 4+
6. Human approval required? → Factor for Tier 5
7. Learn from feedback? → Tier 6

**Output**: Tier recommendation + tools + implementation time + next steps

---

## Domain Architectures

### GTM (Go-to-Market for B2B SaaS)

**Focus**: Marketing ops, sales ops, customer success, revenue operations

**Organization**: Organized by GTM motion (use case) rather than tier level

**13 GTM Motion Categories**:

1. **tam_accounts/** - Total Addressable Market discovery & ICP-based account finding
2. **segmentation_targeting/** - Lead scoring, intent detection, account segmentation
3. **find_decision_makers/** - Contact discovery and decision-maker intelligence
4. **lead_enrichment/** - Firmographic, technographic, and contact data augmentation
5. **lead_routing/** - Intelligent lead assignment and email classification
6. **lead_sequencing/** - Multi-channel personalized outreach sequences
7. **funnel_health/** - Pipeline monitoring, RevOps, metrics dashboards
8. **competitive_intelligence/** - Competitor monitoring and market positioning
9. **product_launch/** - Launch orchestration and campaign coordination
10. **customer_success/** - Customer health monitoring and feedback analysis
11. **reputation_management/** - Review monitoring and brand perception
12. **market_intelligence/** - Market trends and startup signal detection
13. **partnership_marketing/** - Influencer and partnership identification

**Company Size Guidance**: Each folder includes SMB/Mid-Market/Enterprise applications

**Common Integrations**: HubSpot, Salesforce, Clay, Proxycurl (LinkedIn), Clearbit

**Example Stack** (Decision Maker Research):
```
Tier 1: find_decision_makers/decision_maker_orchestrator.json
    → Daily workflow fetches target accounts from Google Sheets
    ↓
Tier 3: find_decision_makers/decision_maker_finder_agent.py
    → Research agent finds decision-makers, pain points, signals
    ↓
Tier 2: lead_enrichment/lead_research_enrichment.json
    → Generate personalized outreach email
    ↓
Tier 1: lead_sequencing/outreach-generator/
    → Send email, log to CRM, schedule follow-up
```

### UE5 (Unreal Engine 5 Game Development)

**Focus**: Asset creation, C++ assistance, Blueprint automation, procedural generation

**Key Workflows**:
- Texture reference capture
- Asset backup automation
- Asset quality scoring
- Tutorial finding
- Procedural asset generation
- Code quality checking

**Common Integrations**: Unreal Engine Python API, Perforce, GitHub

**Example Stack** (Procedural Pipeline):
```
Tier 4 (LangGraph): Multi-agent pipeline
    → Concept Agent: Design asset
    → Technical Agent: Write Unreal Python
    → Quality Agent: Rate output
        ↓
Tier 2 (n8n + Claude Vision): Quality checker
        ↓
Assets saved to UE5 project
```

### BR2 (Building a Second Brain / PKM)

**Focus**: Note capture, organization (PARA method), knowledge synthesis, retrieval

**Key Workflows**:
- Voice/text/image capture
- Smart categorization (Projects/Areas/Resources/Archives)
- Inbox triage
- Note linking
- Weekly review generation
- Progressive summarization

**Common Integrations**: Obsidian, NotebookLM, Apple Calendar (CalDAV)

**Example Stack** (Multi-Source Capture):
```
Tier 0 (iOS Shortcut): Capture voice/text/screenshot
    ↓
Tier 1 (n8n): Normalize from multiple sources
    ↓
Tier 2 (n8n + Claude): Categorize using PARA method
    ↓
Tier 3 (LangChain): Find semantic connections to existing notes
    ↓
Save to Obsidian vault
```

### Law (Legal Automation)

**Focus**: Contract review, research, compliance, deadline tracking, case management

**Key Workflows**:
- Court filing tracking
- Case note capture
- Contract clause analysis
- Legal research
- Memo generation
- Deadline tracking

**Common Integrations**: Legal research databases, document management systems

---

## State Management Architecture

### Hybrid Postgres + Obsidian

**Why Both?**:
- **PostgreSQL**: Queryable, fast, relationships, runtime operations
- **Obsidian**: Human-reviewable, knowledge graph, planning, context building

**Sync Pattern**: Bidirectional sync maintained by orchestrator

### PostgreSQL Schema (`intake_system/intake_database_schema.sql`)

**Key Tables**:
- `intake.workflow_submissions` - All submitted workflows with intake data
- `intake.tier_routing_log` - Tier assignment decisions + reasoning
- `intake.workflow_executions` - Individual execution metrics
- `intake.success_metrics` - Expected vs. actual performance
- `intake.workflow_feedback` - User ratings and iteration requests

**Key Views**:
- `intake.pending_review` - Submissions needing review (sorted by ROI)
- `intake.roi_ranking` - Top automation candidates
- `intake.workflow_performance` - Performance dashboard

### Obsidian Vault Structure (Planned)

```
/automation-system/
  /inbox/              # Quick capture, unprocessed tasks
  /tasks/              # Active task tracking
  /logs/               # Human-readable execution logs
  /patterns/           # Reusable automation patterns
  /domains/
    /gtm/              # GTM-specific knowledge
    /ue5/              # Game dev knowledge
    /br2/              # PKM system knowledge
  /agents/             # Agent configurations and memories
```

---

## Example Types

### Toy Examples (`tier_X_toy_*`)

**Purpose**: Teach tier concepts through "hello world" style minimal implementations

**Code Characteristics** (using GTM Tier 3 as example):
- **Size**: ~300-400 lines (focused, not comprehensive)
- **Data**: Simulated/mocked responses (no real API calls)
  ```python
  def web_search_tool(query: str) -> str:
      # Toy: Returns hardcoded JSON based on query keywords
      if "ceo" in query.lower():
          return """Sarah Chen is the CEO..."""
  ```
- **Error Handling**: Basic (just checks env vars, no retries)
- **Execution Mode**: Single `main()` function for demonstration
- **Logging**: `print()` statements for educational visibility
- **Documentation**: In-line comments explaining "why this is Tier X"
- **Dependencies**: Minimal (core LangChain/n8n only)

**Setup Guide Characteristics** (~350-400 lines):
- 4-step installation (venv → pip install → .env → run)
- Expected output with agent reasoning steps shown
- "Code Walkthrough" section explaining key patterns
- "Why This Is Tier X" comparison table
- Customization examples for learning
- "Contrast with Other Tiers" educational content

**When to Use**:
- Learning tier boundaries and patterns
- Understanding tool usage in agents
- Prototyping before building production version
- Teaching others about the architecture

**Example**: `tier_3_toy_langchain_gtm_prospect_finder.py` (356 lines)
- Demonstrates agent tool selection with 3 simulated tools
- Shows agent reasoning loop clearly
- No deployment complexity

---

### Production Examples (`tier_X_cldchoice_*`)

**Purpose**: Production-ready implementations that integrate into complete tier stacks

**Code Characteristics** (using GTM Tier 3 as example):
- **Size**: ~600-1000 lines (comprehensive, production-ready)
- **Data**: Real API integration patterns with fallbacks
  ```python
  def web_search_tool(query: str) -> str:
      # Production: Real API call with error handling
      # import requests
      # response = requests.post('https://google.serper.dev/search',
      #     headers={'X-API-KEY': os.getenv('SERPER_API_KEY')},
      #     json={'q': query})
      # return response.json()['organic']

      # Fallback to mock for demo
      return json.dumps([...])
  ```
- **Error Handling**: Try/except blocks, retries, fallback responses
- **Execution Modes**: CLI + API server (FastAPI/Flask)
  ```python
  if args.server:
      uvicorn.run(app, host="0.0.0.0", port=args.port)
  else:
      # CLI mode
      result = research_prospect(...)
  ```
- **Logging**: Structured logging with levels (logger.info, logger.error)
- **Type Safety**: Pydantic models for request/response validation
- **Deployment**: Health checks, CORS, environment-based config
- **Monitoring**: Cost tracking, execution metrics, performance data
- **Integration**: Designed to be called by Tier 1 orchestration

**Additional Components**:
- **API Models**: Request/Response Pydantic schemas
- **Multiple Tools**: 5+ tools with sophisticated logic
  - `pain_point_analyzer` - Heuristic analysis of company data
  - `buying_signal_detector` - Pattern matching for purchase readiness
- **Production Configs**: Timeout, max_iterations, rate limiting
- **CLI Arguments**: `--company`, `--industry`, `--role`, `--server`, `--port`

**Setup Guide Characteristics** (~650-700 lines):
- Complete architecture diagram with data flow
- Prerequisites checklist (services, accounts, keys)
- Multi-step deployment (local, staging, production)
- Integration points documented (how Tier 1 calls this, how this calls Tier 2)
- Environment variables with all options
- Example data flow with actual JSON payloads
- Troubleshooting section (5+ common issues)
- Monitoring & observability section
- Production optimization tips
- Security considerations
- Scaling strategies

**When to Use**:
- Deploying to production environment
- Integrating with other tier workflows
- Building similar production workflows (use as reference)
- Team collaboration (standardized structure)

**Example**: `tier_3_cldchoice_gtm_lead_research.py` (630 lines)
- FastAPI server with `/research` endpoint
- 5 production-grade tools with fallback logic
- Structured logging, health checks, CORS
- Called by `tier_1_cldchoice_gtm_lead_research.json` (orchestrator)
- Returns data to `tier_2_cldchoice_gtm_email_gen.json` (email generation)

---

### Clear Distinction Summary (GTM Context)

| Aspect | Toy Example | Production Example |
|--------|-------------|-------------------|
| **Lines of Code** | 300-400 | 600-1000 |
| **API Calls** | Simulated/mocked | Real integration ready |
| **Error Handling** | Basic (env check only) | Try/except, retries, fallbacks |
| **Logging** | `print()` statements | Structured `logger` with levels |
| **Deployment** | Single script | CLI + Server modes |
| **Type Safety** | Basic types | Pydantic models |
| **Integration** | Standalone | Part of tier stack (called by Tier 1, calls Tier 2) |
| **Setup Guide** | 4 steps, ~350 lines | Multi-env, ~650 lines |
| **Monitoring** | None | Health checks, metrics, cost tracking |
| **Purpose** | Teaching | Production deployment |
| **Data Flow** | Hardcoded → Output | Input → API → CRM → Email Gen |

**Upgrading from Toy to Production**:
1. Replace mocked tools with real API calls (Serper, Proxycurl, Clearbit)
2. Add FastAPI server wrapper for HTTP endpoint
3. Add Pydantic request/response models
4. Implement structured logging (not print)
5. Add error handling and retries
6. Add health check endpoint
7. Document integration points with Tier 1/Tier 2
8. Add CLI argument parsing
9. Add cost/performance tracking
10. Write comprehensive setup guide with troubleshooting

### Shelf Examples (`gtm/shelf/`, etc.)

**Purpose**: Real-world automation implementations from actual businesses

**Examples**:
- Automate website visitor outreach
- Two-way CRM enrichment
- Google review screenshots
- Account fit scoring
- Custom HubSpot integration

**Format**: Markdown documentation with architecture diagrams and implementation notes

---

## Tool Stack Reference

### Claude Code (Tier 5-6 Orchestrator)

**Role**: Top-level orchestration, recursive task decomposition, subagent spawning

**When to Use**:
- Tasks requiring planning + adaptation
- Breaking down complex projects
- Managing long-running autonomous agents

**Resources**: `tool_stack/claude_code/` (concepts, patterns, SDK docs)

### n8n (Tier 1-2 Workflows)

**Role**: Visual workflow automation, scheduling, webhooks, API orchestration

**When to Use**:
- Multi-step deterministic processes
- Scheduled tasks
- Embedding single LLM calls for reasoning

**File Format**: `.json` workflows (import via UI)

**Resources**: `tool_stack/n8n/`

### LangChain (Tier 3 Single Agents)

**Role**: Single-purpose agents with tools (search, database, calculator, etc.)

**When to Use**:
- Autonomous task requires 2-5 tools
- Agent chooses which tool based on context
- RAG (retrieval-augmented generation)

**File Format**: `.py` scripts with LangChain imports

**Resources**: `tool_stack/langchain/`

### LangGraph (Tier 4 Multi-Agent)

**Role**: Multi-agent orchestration with state machines

**When to Use**:
- Multiple specialized agents need to collaborate
- Complex handoffs between agents
- Requires state management across agent boundaries

**File Format**: `.py` scripts defining agent graphs

**Resources**: `tool_stack/langgraph/`

### iOS Shortcuts (Tier 0 Triggers)

**Role**: Mobile capture, quick launchers, one-step automations

**When to Use**:
- Voice/photo/text capture on-the-go
- No logic needed, just save data
- Launching other automations via webhook

**File Format**: `.md` instructions for building shortcut

**Resources**: `tool_stack/shortcuts/`

---

## Working with Examples

### Modifying an Example

1. **Read the setup guide first**: Every example has `*_setup.md`
2. **Check dependencies**: `requirements.txt` for Python, credentials for n8n
3. **Use toy version for experiments**: Modify `toy_*` examples, not production
4. **Test with mock data**: All toy examples include test data
5. **Follow tier boundaries**: Don't add AI to Tier 1, don't add multi-agent to Tier 3

### Creating a New Example

1. **Determine tier**: Use `/tier-wizard` slash command
2. **Choose domain**: GTM, UE5, BR2, or Law
3. **Follow naming convention**: `tier_X_[type]_[domain]_[name].[ext]`
4. **Include setup guide**: `tier_X_[type]_[domain]_[name]_setup.md`
5. **Add to domain's tier_examples folder**: `[domain]/tier_examples/tier_X/`
6. **Document in EXAMPLES_SUMMARY.md**: Add to appropriate section

### Submitting via Intake System

**When to Use Intake vs. Direct Build**:
- **Use intake**: Production workflows, ROI calculation needed, team approval required
- **Direct build**: Personal experiments, learning, one-off tasks

**Process**:
1. Export template: `python submit_workflow.py --export-template my_workflow.yaml`
2. Fill 7 sections (use `intake_system/submission_guide.md`)
3. Validate: `python submit_workflow.py --file my_workflow.yaml --validate-only`
4. Submit: `python submit_workflow.py --file my_workflow.yaml`
5. Track via submission ID

---

## Integration with learn_profit Workspace

This repository is part of the larger `learn_profit` workspace. See workspace-level `CLAUDE.md` for:
- Relationship to `voice_asst` (n8n Docker instance)
- Integration with `open_source/comfyui` (image generation)
- Shared conventions and practices

**Key Points**:
- `automation_architecture` serves as the **planned orchestration hub**
- `voice_asst` is a **running n8n instance** (Docker) for voice assistant workflows
- ComfyUI can be called from Tier 3+ agents for image/video generation
- All projects share same environment variable conventions (`.env` files)

---

## Common Patterns

### Tier Escalation Pattern

Start simple, escalate complexity only when needed:

```
Attempt Tier 1 (deterministic)
    → If logic too complex → Tier 2 (add one LLM call)
    → If needs tools → Tier 3 (single agent)
    → If needs specialization → Tier 4+ (multi-agent)
```

### Human-in-the-Loop Pattern (Tier 5)

```
Agent proposes action
    → Log to Obsidian for review
    → Wait for approval (webhook, email reply, CLI)
    → Execute if approved
    → Store feedback for improvement
```

### Cross-Domain Pattern

Some workflows span multiple domains:

```
GTM (lead research)
    → BR2 (store findings in Obsidian)
    → GTM (generate outreach from notes)
```

Store in primary domain (`gtm/`), document cross-domain links in setup guide.

---

## Critical Concepts

### Tier Boundaries Are Meaningful

**Don't**:
- Add AI to Tier 0-1 (defeats the purpose of deterministic workflows)
- Use multi-agent for Tier 3 (keep it single-purpose)
- Build Tier 6 when Tier 3 would work (start simple)

**Do**:
- Use the tier that matches complexity
- Escalate only when current tier is insufficient
- Document why you chose that tier in setup guide

### ROI Drives Priority

Not all automations are worth building:

```
ROI Score = (Annual Savings) / (Build Cost)

High ROI (>10): Build immediately
Medium ROI (3-10): Prioritize by strategic value
Low ROI (<3): Defer unless strategic importance
```

### Examples Are Documentation

Every example serves dual purpose:
1. **Runnable code**: Can be deployed as-is (production examples)
2. **Living documentation**: Shows pattern for building similar workflows

Treat examples as precious - they're the system's knowledge base.

---

## Anti-Patterns to Avoid

1. **Over-engineering**: Building Tier 4 when Tier 2 would work
2. **Under-engineering**: Trying to make Tier 1 do contextual reasoning (use Tier 2)
3. **Mixing tiers in one file**: Keep tier boundaries clear
4. **Skipping intake for production**: Always document via intake system
5. **No success metrics**: Define before/after metrics upfront
6. **Ignoring ROI**: Time saved must justify build cost

---

## Deployment Considerations

### Tier 0-1 Deployment

- **iOS Shortcuts**: Install on device, no server needed
- **n8n workflows**: Import to n8n instance, configure credentials, activate

### Tier 2-3 Deployment

- **n8n + AI**: Same as Tier 1, plus API key configuration
- **Python agents**: Run as cron jobs, AWS Lambda, or triggered via webhook

### Tier 4+ Deployment

- **Multi-agent systems**: Require orchestration layer (Claude Code, LangGraph server)
- **Monitoring**: Must track costs (LLM tokens), execution time, success rate
- **State management**: PostgreSQL + Obsidian sync service must be running

### Cost Tracking

All examples should log:
- LLM tokens used
- API calls made
- Execution duration
- Success/failure status

Store in `intake.workflow_executions` table.

---

## Getting Help

**Documentation Priority**:
1. Example's `*_setup.md` file
2. `get_started/QUICKSTART.md`
3. Domain-specific toolkit READMEs (`gtm/toolkit/README.md`)
4. `intake_system/README.md`
5. Main `README.md`

**Slash Commands**:
- `/tier-wizard` - Determine correct tier for workflow

**Common Issues**:
- "n8n command not found" → `npm install -g n8n`
- "No module named langchain" → Activate venv: `source venv/bin/activate`
- "Port 5678 in use" → `pkill -f n8n` then restart
- "Invalid API key" → Check `.env` file, restart n8n after adding keys
