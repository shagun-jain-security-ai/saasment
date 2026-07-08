# SaaSment — AI-Powered SaaS Security Posture Management

Assesses security configuration of SaaS applications\tools, maps findings to compliance controls, scores posture per app, and surfaces AI-driven remediation — from a single extensible Python pipeline.

---

## Problem

As organizations adopt more SaaS applications, security teams face several challenges:

* 🔍 Hundreds of security settings spread across multiple SaaS platforms
* 📈 Difficulty understanding the overall security posture
* ⚠️ Thousands of configuration findings with little prioritization
* 📚 Manual compliance mapping across different frameworks
* 🤖 Static rule engines that lack contextual reasoning
* ⏱️ Time-consuming remediation and validation processes

Traditional SSPM solutions often identify misconfigurations but provide limited context about why they matter or how security teams should prioritize remediation.

---

## Solution

SaaSment combines deterministic security analysis with AI-assisted reasoning to provide a richer understanding of SaaS security posture.

Rather than replacing deterministic security checks, AI is used to enhance them with context, prioritization, and explanation.

Instead of buying a commercial SSPM tool (AppOmni, Obsidian, etc — $100K+/yr), this knows your specific environment, integrates with your existing infrastructure, and uses AI to find issues that static rules alone would miss.

---


## Key Features

The project is designed around several principles:

* ✅ Provider-independent architecture
* ✅ Rule-based security assessment
* ✅ AI-assisted contextual analysis, scoring and reporting
* ✅ Compliance-aware posture evaluation
* ✅ Scalable for multiple SaaS platforms
* ✅ Actionable remediation guidance
* ✅ Normalization is fundamental to accurate cross-platform security analysis.

---


## Architecture - High Level

```
  SaaS Connectors          one extractor per app 
        │
        ▼
  Normalization            every extractor produces the same snapshot
        │
        |
        ▼
    Analysis
        ├──── RULES mode   static rules only      
        ├──── HYBRID mode  static rules + AI analysis  (default)
        └──── AI mode      AI analysis only
        │
        ▼
  Static Rules Engine      rule per tool: id │ severity │ compliance │ check prompt
        │
        |
        ▼
  AI Engine                Phase 1: evaluate each static rule against snapshot
        |                  Phase 2: AI scan — finds what static rules miss
        |                  Phase 3: merge + deduplicate
        │
        ▼
  Posture Scoring          100 − deductions (Critical −20, High −10, Medium −5, Low −2)
  Compliance Mapping       SOC2 │ ISO27001 │ NIST CSF │ CIS
        │
        ▼
     Output                  
        │
        ├──── Report     Finding and AI Remediation Assistant   finding and remediation 
        ├──── [Planned]  Security Copilot                       conversational posture interface
        └──── [Planned]  Recheck & Close                        auto-close resolved findings
```

---


## Source Code

🚫 ***The implementation(source code) is not included in this repository.*** 

The project was developed as part of my professional work and the source code is therefore not publicly available.

This repository exists to document the project's vision, engineering approach, architectural concepts, and the technical challenges involved in building an AI-powered SaaS Security Posture Management solution. 

---

## Security Considerations


* Never commit .env — credentials stay local only
* Read-only access — all extractors use read-only API permissions. No write operations are performed on any tool
* Data handling — snapshot files contain security configuration data - snapshots/ and reports/ should be gitignored.
* Use approved/known AI model/solution 
