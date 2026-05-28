# ET-AutoTech-Hackathon<div align="center">

# 🛰️ SentinelChain

### A Geopolitical Risk-Aware Sourcing Co-Pilot for Resilient Automotive Supply Chains & Smart Manufacturing

**ET AutoTech Hackathon 2026 · Theme 1**
*AI for Resilient Automotive Supply Chains & Smart Manufacturing*

`Predict` Tier-N risk &nbsp;·&nbsp; `Recommend` alternate sourcing &nbsp;·&nbsp; `Optimise` the shop floor

[Problem](#-the-problem) · [Solution](#-the-solution) · [Architecture](#-architecture--intelligence-design) · [Impact](#-business-impact-model) · [Roadmap](#-impact--scalability) · [Demo](#-demo)

</div>

---

## 📌 TL;DR

The disruptions that actually stop an assembly line are the ones nobody can see — they originate two or three tiers below where OEMs have visibility, in single-source sub-components, concentrated mineral geographies, and shared logistics chokepoints.

**SentinelChain** models the entire bill-of-materials as a graph, propagates live geopolitical / commodity / logistics risk through every tier, scores each node with a transparent **Supplier Risk Index**, and uses a GenAI co-pilot to recommend ranked alternate-sourcing and material-substitution playbooks — *with reasoning a human can challenge*. The same engine closes the loop on the shop floor with process-capability, demand, energy and defect intelligence.

Built deliberately for the **cost, connectivity and ERP constraints of India's Tier-1 / Tier-2 supplier base.**

> **Status:** Concept + architecture submission. This repository documents the design, intelligence model, and build plan. A working prototype is scoped for the build phase (see [Build Plan](#-48-hour-build-plan)).

---

## 🔥 The Problem

The automotive supply chain is globally distributed and increasingly fragile — exposed to geopolitical tension, mineral shortages, logistics constraints, and demand volatility. The structural blind spot:

| Insight | Why it matters |
|---|---|
| **~70%+ of disruptions originate at Tier-2/Tier-3** | OEMs map Tier-1 suppliers well, but the failure point is usually a single-source sub-component or raw material deeper in the chain — invisible on any dashboard. |
| **Mineral concentration is a single point of failure** | A handful of geographies dominate supply of rare-earth magnets, cells, and key electronics critical to EV powertrains. |
| **Reaction is measured in weeks** | Most firms learn of a shock *after* the stockout, then scramble to re-source with no pre-qualified alternatives. |
| **Risk signals are scattered & unstructured** | Geopolitical news, commodity prices, port congestion, and supplier health live in silos and unstructured text. |

**Why now:** electrification concentrates dependence on a few mineral geographies, geopolitics increasingly weaponises export controls, and GenAI finally makes unstructured risk signals machine-readable at low cost.

---

## 💡 The Solution

A co-pilot that sees the whole chain — and tells you what to do about it.

1. **Model the BOM as a graph.** Every part, supplier, mineral and route is a node. Risk propagates through tiers, exposing hidden single points of failure.
2. **Score risk transparently.** A glass-box **Supplier Risk Index** decomposed into geopolitical, single-source, financial and logistics sub-scores — never an opaque number.
3. **Recommend & act.** A RAG co-pilot ranks alternate suppliers, geographies, routes and substitute materials, each with explicit cost / lead-time / risk trade-offs and reasoning.
4. **Close the loop on the floor.** The same engine ingests production data for Cp/Cpk monitoring, demand & energy forecasting, and computer-vision defect detection.

---

## 🧠 Architecture & Intelligence Design

Three layers, one explainable decision.

![SentinelChain Architecture](architecture.svg)

### Layer 1 — Signal Ingestion
Pulls structured + unstructured signals and normalises them into node-level features.
- Commodity prices (LME / MCX feeds)
- News & event stream → disruption named-entity recognition
- Port congestion & logistics feeds
- Supplier financial-health proxies

### Layer 2 — Risk Scoring Engine
The reasoning core. Converts signals into an explainable, propagating risk picture.
- **BOM graph** with **Tier-N risk propagation**
- **Composite Supplier Risk Index** (weighted, decomposable)
- Geopolitical-concentration, single-source, financial-fragility & logistics sub-scores
- **Shock simulation** + sensitivity analysis ("what breaks if Region X imposes an export ban?")

### Layer 3 — GenAI Co-Pilot (RAG)
Synthesis and explanation — *not* prediction.
- Retrieval over a supplier / material knowledge base
- Ranked alternate-sourcing playbooks
- Material-substitution candidates with engineering caveats
- Natural-language "why" behind every recommendation

> **Design principle:** the LLM is used for *synthesis and explanation*, never for the risk prediction itself. Risk is computed by a transparent, auditable model so a sourcing manager can challenge any sub-score. Right tool, right job.

### The Supplier Risk Index (glass-box)

| Sub-score | Weight | Captures |
|---|---|---|
| Geopolitical concentration | 35% | Dependence on high-tension / single-region sources |
| Single-source dependency | 30% | Lack of qualified alternates for a node |
| Financial fragility | 20% | Supplier solvency / continuity risk proxies |
| Logistics exposure | 15% | Route, port and lead-time vulnerability |

*Weights are illustrative defaults and are fully tunable per OEM / commodity.*

### How a recommendation is reasoned
```
Detect      live signals shift a node's sub-scores in near-real-time
   ↓
Propagate   graph pushes elevated risk up Tier-2 → Tier-1 → assembly
   ↓
Rank        candidate alternates scored on risk Δ, lead-time, cost, qualification effort
   ↓
Explain     LLM synthesises the trade-off into a decision a human signs off on
```

---

## 🏗️ ERP-Light by Design

Built for the realities of emerging-market suppliers, not just flagship OEMs:
- **CSV / REST connectors** — no SAP required to onboard.
- **Cached risk snapshots** — degrades gracefully under intermittent connectivity.
- **Modest-compute footprint** — runs without a GPU cluster.

---

## 💰 Business Impact Model

Where the value lands for a mid-size auto supplier *(illustrative, indexed)*:

| Value lever | Relative impact | Mechanism |
|---|---|---|
| Avoided disruption loss | ████████████ high | Days-to-weeks of lead time on a shock vs. reacting after the stockout |
| Inventory / buffer reduction | █████ medium | Confidence in visibility lets planners hold less safety stock |
| Quality & scrap savings | ███ medium-low | Cp/Cpk + CV catch process drift before it becomes scrap or recall |
| Energy optimisation | ██ low | Production-linked energy forecasting trims consumption |

**The value logic:** earlier detection → faster re-sourcing via pre-qualified alternates → leaner buffers → fewer defects.

---

## 🚀 Impact & Scalability

A three-horizon path from a single supplier to a national resilience layer.

| Horizon | Scope | What happens |
|---|---|---|
| **H1 — Adopt** | Single supplier / OEM plant | Risk dashboard + alternate-sourcing co-pilot on synthetic + public feeds. Land the wedge. |
| **H2 — Connect** | Multi-tier network | Suppliers share anonymised nodes → network effects sharpen Tier-N visibility for everyone. |
| **H3 — Scale** | Sector / nation | Commodity & geopolitical intelligence as a shared resilience layer for India's auto manufacturing base. |

**Why it scales:**
- 🌱 **Sustainable** — substitution & route optimisation cut embedded carbon and waste.
- 💸 **Frugal** — modest compute, graceful offline degradation.
- 🤝 **Portable** — the same engine generalises to electronics, pharma and FMCG supply chains.

---

## 🛠️ Proposed Tech Stack

| Component | Technology |
|---|---|
| Graph & scoring | NetworkX / igraph · Python · pandas |
| Risk models | Gradient-boosted + rules · scikit-learn / LightGBM |
| Signal NER | Lightweight LLM extraction over news / events |
| Co-pilot | RAG · FAISS vector store · Gemini / open LLM |
| Serving | FastAPI · cached snapshots · CSV / REST connectors |
| UI | Streamlit / React dashboard · shock-injection demo |

---

## 📅 48-Hour Build Plan

**In scope for the prototype**
- [ ] BOM risk-propagation graph on synthetic auto-component data
- [ ] Composite Supplier Risk Index with 3 live-ish signal feeds
- [ ] RAG co-pilot over a curated supplier knowledge base
- [ ] Dashboard with the shock-injection demo flow

**Out of scope (roadmap)**
- [ ] Deep ERP integrations & real telemetry
- [ ] CV defect model trained on real plant data

> The prototype proves the thesis on **synthetic + public data** — no proprietary shop-floor data required.

---

## 🎬 Demo

📹 **Demo video:** _[add Google Drive link here]_

The demo follows one arc: a calm all-green supply graph → inject a rare-earth export ban → watch risk cascade up the tiers → the co-pilot returns a ranked switch playbook with cost / lead-time / risk-Δ trade-offs in seconds.

---

## 👤 Team

| | |
|---|---|
| **Submission** | ET AutoTech Hackathon 2026 — Theme 1 |
| **Team / Author** | _[your name / team name]_ |
| **Contact** | _[email]_ |

---

<div align="center">

### *See the risk before it ships. Re-route before it stops the line.*

</div>
-2026
