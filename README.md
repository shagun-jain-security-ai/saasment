# SaaSment — AI-Powered SaaS Security Posture Management

Assesses security configuration of SaaS applications\tools, maps findings to compliance controls, scores posture per app, and surfaces AI-driven remediation — from a single extensible Python pipeline.

---

## Flow

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
