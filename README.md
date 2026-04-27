<p align="center">
  <img src="kryptokat-saif.png" alt="KryptoKat — Hacker Cat at the Terminal" width="420">
</p>

<h1 align="center">🐾 Google SAIF — A KryptoKat Field Guide 🐾</h1>
<h3 align="center"><i>The Secure AI Framework for Securing AI Systems Across Their Lifecycle</i></h3>
<h4 align="center"><i>Six principles. Four components. Fifteen risks. One Agent Risk Map. Currently at SAIF 2.0 (October 2025).</i></h4>

<p align="center">
  <a href="https://saif.google/"><img src="https://img.shields.io/badge/Google-SAIF-4285F4?style=for-the-badge" alt="Google SAIF Badge"></a>
  <a href="https://saif.google/secure-ai-framework"><img src="https://img.shields.io/badge/SAIF-Map-34A853?style=for-the-badge" alt="SAIF Map Badge"></a>
  <img src="https://img.shields.io/badge/Made%20by-KryptoKat-ff1493?style=for-the-badge" alt="Made by KryptoKat">
</p>

---

## 🐈‍⬛ What is this?

A practitioner reference for **Google's Secure AI Framework (SAIF)** — a conceptual framework introduced by Google in June 2023 to secure AI systems throughout their full development and deployment lifecycle, and substantially expanded as **SAIF 2.0** on October 6, 2025 to address the rapidly emerging risks posed by autonomous AI agents.

SAIF distilled Google's decade-plus of internal AI security experience (Vertex AI, Search, Gmail, the AI Red Team) into something anyone can adopt. It pairs **six core elements** (the principles), a **four-component SAIF Map** (Data, Infrastructure, Model, Application), **fifteen specific AI risks** mapped against the controls that mitigate them, and — as of SAIF 2.0 — a dedicated **Agent Risk Map** with three secure-by-design agent principles.

Where OWASP's Top 10 lists *what to worry about* and MITRE ATLAS catalogs *how adversaries operate*, SAIF answers the operational question: *what controls do I put in place across the AI lifecycle, and where do they go?* It is closer in spirit to NIST or ISO frameworks than to a vulnerability list — secure-by-default infrastructure, harmonized platform controls, continuous detection-and-response.

> *"OWASP tells you what's broken. ATLAS tells you who's hunting. SAIF tells you how to lay the fence."*

In 2024, Google contributed SAIF's risk map and self-assessment to the **Coalition for Secure AI (CoSAI)**, formalizing it as community infrastructure rather than a vendor framework. SAIF 2.0 (October 2025) extended that commitment by donating the agent risk map data to the **CoSAI Risk Map initiative**.

---

## 📚 Official Sources (Read These First)

| Resource | Link |
|---|---|
| 🌐 SAIF Home | https://saif.google |
| 🤖 SAIF Focus on Agents (SAIF 2.0) | https://saif.google/focus-on-agents |
| 🗺️ SAIF Map | https://saif.google/secure-ai-framework/saif-map |
| ⚠️ SAIF Risks | https://saif.google/secure-ai-framework/risks |
| 📋 SAIF Risk Self-Assessment | https://saif.google/risk-self-assessment |
| 📘 Secure AI Development Primer | https://saif.google/ai-development-primer |
| 🤝 Coalition for Secure AI (CoSAI) | https://coalitionforsecureai.org |
| ☁️ Google Cloud SAIF Resources | https://cloud.google.com/use-cases/secure-ai-framework |
| 📰 SAIF 2.0 Announcement (Oct 2025) | https://blog.google/technology/safety-security/ai-security-frontier-strategy-tools/ |
| 📰 Original SAIF Announcement (June 2023) | https://blog.google/technology/safety-security/introducing-googles-secure-ai-framework/ |

---

## 🎯 The Six Core Elements

These are the principles that organize every other piece of SAIF. They are **not sequential** — they apply concurrently across the AI lifecycle.

| # | Element | KryptoKat's Translation |
|---|---|---|
| 1 | [Expand strong security foundations to the AI ecosystem](#-1-expand-strong-security-foundations-to-the-ai-ecosystem) | Don't reinvent the litterbox — bring AI inside the one you already built |
| 2 | [Extend detection and response to bring AI into the threat universe](#-2-extend-detection-and-response-to-bring-ai-into-the-threat-universe) | Watch the model the way you watch the network |
| 3 | [Automate defenses to keep pace with existing and new threats](#-3-automate-defenses-to-keep-pace-with-existing-and-new-threats) | Cats are fast. So is the AI defending you. |
| 4 | [Harmonize platform-level controls to ensure consistent security](#-4-harmonize-platform-level-controls-to-ensure-consistent-security) | Same litter, every box |
| 5 | [Adapt controls to adjust mitigations and create faster feedback loops](#-5-adapt-controls-to-adjust-mitigations-and-create-faster-feedback-loops) | The cat learns. So should the controls. |
| 6 | [Contextualize AI system risks in surrounding business processes](#-6-contextualize-ai-system-risks-in-surrounding-business-processes) | The cat in finance is a different cat than the cat in marketing |

---

## 🐱 1. Expand Strong Security Foundations to the AI Ecosystem

> *"Most of the litterbox is already built. Move the AI into it."*

### Description
The first SAIF element argues that organizations should not treat AI security as a greenfield problem. Two decades of secure-by-default infrastructure — IAM, encryption, network segmentation, identity-aware proxying, secrets management, supply-chain controls — already exist and continue to apply to AI workloads. SAIF's first move is to extend and adapt those existing foundations to cover AI-specific risks rather than building parallel infrastructure. The example Google gives is illustrative: SQL injection mitigations (input sanitization, parameter binding, allowlisting) translate directly to early-stage prompt injection defenses. Organizations should also develop AI-specific organizational expertise — security engineers who understand model lifecycles, data scientists who understand threat modeling, and shared vocabulary that lets the two work together.

### Practical Applications
- IAM and zero-trust architectures (BeyondCorp lineage) extended to model serving infrastructure
- Cloud Armor and DDoS protections in front of inference endpoints
- Confidential Computing for training data and model weights at rest
- Software supply chain controls (SLSA levels) applied to model artifacts
- VPC Service Controls creating security perimeters around AI assets

---

## 🐱 2. Extend Detection and Response to Bring AI into the Threat Universe

> *"You already have a SOC. Tell it about the model."*

### Description
The second element addresses a gap most organizations don't realize they have: the existing detection-and-response stack does not see what AI systems are doing. SIEMs, SOAR platforms, and threat intelligence feeds were built for traditional infrastructure and rarely ingest model inputs, outputs, or behavioral telemetry. SAIF's directive is to bring AI into the same detection regime as everything else — monitor prompts, completions, retrieval activity, and tool invocations the way you monitor network traffic and authentication events. Timeliness matters: AI-related incidents (prompt injection, data exfiltration via inference, model extraction campaigns) often present as anomalies in inference patterns long before any traditional indicator fires. This element typically requires collaboration across teams that don't normally share telemetry — security, trust and safety, threat intelligence, counter-abuse, and ML operations.

### Practical Applications
- Connect model I/O streams to SIEM/SOAR pipelines
- Anomaly detection on inference patterns (volume, query distribution, token usage)
- AI-specific threat intelligence feeds and indicators of compromise
- Cross-team incident response runbooks involving ML operations
- Logging that captures both prompts and completions with appropriate redaction

---

## 🐱 3. Automate Defenses to Keep Pace with Existing and New Threats

> *"The attacker is using AI. So should you."*

### Description
The third element acknowledges the asymmetry that adversaries exploit AI to scale their attacks — automated phishing generation, programmatic prompt injection campaigns, AI-assisted vulnerability discovery — and argues that defenders must use AI to stay competitive on speed and scale. Manual response loops cannot match the throughput of automated adversarial pipelines. SAIF specifically calls out using AI for triage, anomaly classification, and automated containment. Crucially, Google warns that humans must remain in the loop for important decisions: AI defense systems can be biased, can produce false positives, and require human judgment to avoid over-blocking legitimate activity. The recommendation is automation in service of human decision-makers, not automation that replaces them.

### Practical Applications
- AI-assisted log analysis and incident triage
- Automated detection-rule generation from observed attack patterns
- Continuous red-teaming and adversarial-test automation
- Machine-speed containment of confirmed attacks (rate limiting, isolation)
- Human-in-the-loop checkpoints for high-impact responses

---

## 🐱 4. Harmonize Platform-Level Controls to Ensure Consistent Security

> *"Same control, every box. Not a different fence in every room."*

### Description
The fourth element addresses a problem that grows with every AI deployment: organizations end up with inconsistent security postures across model platforms (Vertex AI, OpenAI APIs, Anthropic APIs, on-prem inference servers, edge devices), each with different controls, different audit trails, and different blast radii when something goes wrong. SAIF recommends harmonizing controls at the platform level rather than reimplementing them per application — extending secure-by-default protections to AI platforms so that a developer building a new application inherits the right controls automatically. This is the same logic that drives infrastructure-as-code, paved-road security tooling, and zero-trust enforcement: consistency at the platform layer beats heroic effort at the application layer.

### Practical Applications
- Centralized policy enforcement across all model deployment platforms
- Standardized authentication and authorization for inference endpoints (e.g., Identity-Aware Proxy)
- Common logging and audit formats across heterogeneous AI platforms
- Reusable security building blocks (Model Armor, prompt firewalls) integrated platform-side
- Software development lifecycle controls applied uniformly to AI projects

---

## 🐱 5. Adapt Controls to Adjust Mitigations and Create Faster Feedback Loops

> *"The cat learns. The litterbox should learn faster."*

### Description
The fifth element recognizes that AI systems and their threat landscapes change too quickly for static controls to remain effective. Models retrain, data shifts, new attack techniques emerge, and yesterday's threshold becomes today's blind spot. SAIF recommends building controls that adapt — using techniques like reinforcement learning from operational feedback, continuous red-teaming that surfaces new gaps, and policy-as-code that can be updated and redeployed quickly. The faster the feedback loop between detected issues and updated mitigations, the smaller the window of exposure. This element aligns with practices like canary deployments and progressive rollouts: ship a control change to a small population, observe, and expand or roll back based on real-world results.

### Practical Applications
- Continuous red-teaming with automated test generation
- Drift monitoring on both models and the controls protecting them
- Policy-as-code with rapid update and rollback capabilities
- Reinforcement learning loops that tune controls from operational feedback
- Tabletop exercises and incident retrospectives feeding back into control updates

---

## 🐱 6. Contextualize AI System Risks in Surrounding Business Processes

> *"A cat in finance is not the same cat as a cat in marketing."*

### Description
The sixth element argues that AI security cannot be evaluated in isolation from the business context the AI operates in. The same technical vulnerability has dramatically different severity depending on what the model touches: a prompt-injection bug in a customer-service chatbot is recoverable; the same bug in a medical diagnosis assistant is potentially catastrophic. SAIF recommends calibrating controls by decision criticality, data sensitivity, regulatory exposure, and risk appetite. This requires cross-functional involvement — legal, compliance, business owners, responsible-AI ethics review — rather than pure security ownership. In practice, this element is what makes SAIF a *risk management* framework rather than a controls checklist: the same risk gets different mitigations in different business contexts.

### Practical Applications
- Risk assessments that include business impact alongside technical severity
- Regulatory mapping (HIPAA, GLBA, GDPR, EU AI Act) per AI use case
- Business-owner sign-off on AI deployments touching critical decisions
- Tiered controls calibrated to data sensitivity and decision criticality
- Cross-functional governance committees (security, legal, ethics, ML, business)

---

## 🗺️ The SAIF Map: Four Component Areas

The SAIF Map is a conceptual diagram of where in an AI system risks are introduced, exposed, and mitigated. It divides the AI system into **four component areas**, with risks and controls mapped across them. The map exists because most other AI security frameworks focus narrowly on the model itself — SAIF deliberately covers the full lifecycle, including the parts that go wrong long before the model produces a single token.

| Component | What it covers | Example risks introduced here |
|---|---|---|
| **🗂️ Data** | Data sources, processing, storage, and use for training, tuning, and evaluation | Data Poisoning, Unauthorized Training Data, Excessive Data Handling |
| **🏗️ Infrastructure** | Model frameworks, training and serving systems, ML tooling, deployment platforms | Model Source Tampering, Model Deployment Tampering, Model Exfiltration |
| **🧠 Model** | The trained model, its weights, its evaluation, and its behavior | Model Evasion, Sensitive Data Disclosure, Insecure Model Output |
| **🚪 Application** | User-facing applications, plugins, agent layers, and the systems the AI interacts with | Prompt Injection, Rogue Actions, Insecure Integrated Component |

The map has two halves: the **top half** shows the path a model takes to deployment and how a user queries it (most relevant to *Model Consumers* — those building AI-powered products). The **bottom half** shows the path to developing a model (most relevant to *Model Creators* — those training or fine-tuning models for use).

For agentic systems, **SAIF 2.0 introduced a dedicated Agent Risk Map** — a separate, specialized diagram that decomposes agent architectures into Application, Reasoning Core, and Orchestration components, each with their own sub-components and risks. See the next section.

---

## 🤖 The SAIF 2.0 Agent Risk Map

> *"Agents collapse old boundaries. The map had to expand to match."*

### Description
Released October 6, 2025 as part of **SAIF 2.0**, the Agent Risk Map is a dedicated extension of the original SAIF Map purpose-built for agentic systems — those AI systems that take autonomous actions rather than producing single-shot responses. It exists because the original four-component map (Data, Infrastructure, Model, Application) was designed for traditional AI deployments and could not adequately represent the architectural surfaces that agents introduce: reasoning loops, tool orchestration, persistent memory, and the security boundary between trusted operator instructions and untrusted environmental input.

### The Three Agent Architecture Layers

| Layer | Sub-components | Primary security challenge |
|---|---|---|
| **🚪 Application** | System Instructions, User Queries | Reliably distinguishing trusted operator commands from potentially untrusted environmental input |
| **🧠 Reasoning Core** | The LLM(s) doing planning and decision-making | The agent's autonomy level directly governs the severity of any failure — more autonomy means larger blast radius |
| **🔄 Orchestration** | Agent Memory, Tools, Content (RAG) | Coordinating external services and data sources without letting any one of them compromise the whole agent |

### The Three SAIF 2.0 Secure-by-Design Agent Principles

SAIF 2.0 introduced three principles specifically for agent security. Google describes these as the foundation for "secure-by-design" agent architectures:

1. **Agents must have well-defined human controllers.** It must be unambiguous at every step whose authority the agent is operating under, and how that authority was delegated. This rules out anonymous service-account agents acting on no specific person's behalf for any sensitive operation.

2. **Their powers must be carefully limited.** The agent should be granted only the minimum capabilities and permissions required for its intended function. Tool access, scope of authority, and ability to take consequential actions should all be deliberately bounded — not inherited by default.

3. **Their actions and planning must be observable.** A human (or a downstream automated system) should be able to inspect what the agent is doing, why it chose to do it, and what it plans to do next. Black-box agents that produce only outcomes — with no inspectable reasoning or action log — fail this principle.

### Agent-Specific Risk Amplifications

SAIF 2.0 explicitly notes that several existing SAIF risks are *magnified* in agentic contexts:
- **Sensitive Data Disclosure** — exponentially multiplied because agents can access user data flowing through integrated systems (email, files, internal docs) and can leak via any tool that passes information outward
- **Rogue Actions** — graduates from a theoretical concern to the central risk of agentic deployment
- **Insecure Integrated Component** — broader because agents pull in tools, MCP servers, and A2A peers dynamically at runtime
- **Prompt Injection** — more dangerous because injection at one step propagates through the agent's entire multi-step plan

### Practical Implementation Guidance (per Google Cloud)

Google Cloud's January 2026 SAIF guidance distilled three practical rules for implementing SAIF 2.0:

1. **Data should be treated as the new perimeter.** Agents access data far beyond their original task scope; perimeter thinking has to follow the data.
2. **Prompts should be treated as code.** Versioning, testing, code review, and supply-chain controls applied to system prompts.
3. **Secure agentic AI requires identity propagation.** The actual user's identity and permissions should propagate to every backend tool the agent touches — no broad service-account shortcuts.

🔗 Full agent guidance: [saif.google/focus-on-agents](https://saif.google/focus-on-agents)

---

## ⚠️ The 15 SAIF Risks at a Glance

| # | Risk | Primary Component | KryptoKat's Translation |
|---|---|---|---|
| 1 | [Data Poisoning](#-1-data-poisoning) | Data | Spiked kibble in the training bowl |
| 2 | [Unauthorized Training Data](#-2-unauthorized-training-data) | Data | The cat ate things it shouldn't have |
| 3 | [Model Source Tampering](#-3-model-source-tampering) | Infrastructure | Someone edited the cat's DNA |
| 4 | [Excessive Data Handling](#-4-excessive-data-handling) | Data | Cat is hoarding receipts |
| 5 | [Model Exfiltration](#-5-model-exfiltration) | Infrastructure | Cat got cloned |
| 6 | [Model Deployment Tampering](#-6-model-deployment-tampering) | Infrastructure | The cat at production is not the cat you trained |
| 7 | [Denial of ML Service](#-7-denial-of-ml-service) | Application | Cat is too tired to respond |
| 8 | [Model Reverse Engineering](#-8-model-reverse-engineering) | Application | Reconstructing the cat by watching it move |
| 9 | [Insecure Integrated Component](#-9-insecure-integrated-component) | Application | The cat door doesn't lock |
| 10 | [Prompt Injection](#-10-prompt-injection) | Application / Model | Whispering bad ideas to the cat |
| 11 | [Model Evasion](#-11-model-evasion) | Model | Hiding from the cat in plain sight |
| 12 | [Sensitive Data Disclosure](#-12-sensitive-data-disclosure) | Model / Application | Cat told a stranger your secrets |
| 13 | [Inferred Sensitive Data](#-13-inferred-sensitive-data) | Model | Cat figured out something it shouldn't have |
| 14 | [Insecure Model Output](#-14-insecure-model-output) | Application | Cat handed you a wrapped grenade |
| 15 | [Rogue Actions](#-15-rogue-actions) | Application / Agent | Cat did the thing. The thing was bad. |

---

## 🐱 1. Data Poisoning

> *"Spiked kibble in the training bowl."*

### Description
Data Poisoning is introduced when training, tuning, or evaluation data is maliciously or accidentally modified before or during model development. The risk is exposed during training (the model learns the wrong patterns) and during use (the model behaves according to the poisoned learning). Poisoning can be broad (degrading overall model quality) or targeted (introducing a specific backdoor that activates on a chosen trigger). It can originate from external sources — public datasets, scraped web content, third-party data providers — or from internal compromise of data pipelines. Detection is structurally hard because a well-crafted backdoor leaves the model performing normally on standard evaluation sets.

### SAIF Controls
- Training Data Sanitization
- Secure-by-Default ML Tooling
- Model and Data Integrity Management
- Model and Data Access Control

---

## 🐱 2. Unauthorized Training Data

> *"The cat ate things it shouldn't have."*

### Description
Unauthorized Training Data covers the risk of using data for model training, tuning, or evaluation that the organization does not have proper rights to use — copyrighted material without license, PII used outside policy, data from users who didn't consent to ML use, or data that should have been filtered out during ingestion. The risk is introduced early in development (during data ingestion and processing) and exposed both during evaluation (which catches some issues) and at inference time (when the model produces outputs based on data it shouldn't have learned from). This risk has both a security dimension (data leakage in outputs) and a legal/compliance dimension (regulatory and copyright exposure that may follow the model for its entire lifetime).

### SAIF Controls
- Training Data Management
- Training Data Sanitization
- Model and Data Inventory Management

---

## 🐱 3. Model Source Tampering

> *"Someone edited the cat's DNA."*

### Description
Model Source Tampering is introduced when model code, training frameworks, or model weights are not adequately hardened against supply chain attacks. The risk is exposed in the model frameworks and code components (if discovered early) or in the deployed model's modified behavior (if not). The PyTorch dependency confusion attack — where a compromised dependency installed a malicious binary — is the canonical example. Similar risks affect any model artifact pulled from a public or untrusted source: weights, tokenizers, fine-tuning adapters, evaluation harnesses. Mitigation requires the same supply-chain discipline applied to traditional software, with the added wrinkle that model artifacts are larger, less inspectable, and harder to scan than source code.

### SAIF Controls
- Secure-by-Default ML Tooling
- Model and Data Integrity Management
- Model and Data Access Control
- Model and Data Inventory Management

---

## 🐱 4. Excessive Data Handling

> *"Cat is hoarding receipts."*

### Description
Excessive Data Handling is the collection, retention, processing, or sharing of user data beyond what relevant policies allow. The risk lives in both the model and the storage components: the model may have memorized data it should have discarded, and storage systems may retain training inputs, prompts, completions, or telemetry past their permitted lifetime. The exposure happens in two places — during the lifecycle of the data itself (storage policy violations) and during inference (the model surfacing data it shouldn't still have access to). Mitigation requires data-filtering at ingestion, automated archiving and deletion policies, and proactive alerts for models trained on data that has aged past its permitted use window.

### SAIF Controls
- Training Data Management
- Training Data Sanitization
- User Data Management

---

## 🐱 5. Model Exfiltration

> *"Cat got cloned."*

### Description
Model Exfiltration is the unauthorized copying or extraction of model artifacts — weights, code, configurations — typically by attackers exploiting weaknesses in storage or serving infrastructure. The Meta Llama leak (where pre-release weights were redistributed online, bypassing the license-acceptance flow) is the canonical example of how a single infrastructure failure can convert a controlled-release model into an uncontrolled one. The risk is introduced when storage and serving systems are not adequately hardened, and exposed when an attacker accesses model files directly. Mitigation requires hardening storage (encryption at rest, strict access controls, audit logging) and serving infrastructure (authentication, authorization, network isolation) — and treating model artifacts with the same protection level as production source code or cryptographic material.

### SAIF Controls
- Model and Data Inventory Management
- Model and Data Access Control
- Secure-by-Default ML Tooling

---

## 🐱 6. Model Deployment Tampering

> *"The cat at production is not the cat you trained."*

### Description
Model Deployment Tampering is unauthorized modification of the components used to deploy a model, whether by tampering with the source code supply chain or exploiting known vulnerabilities in deployment tooling. Such modifications can change model behavior post-deployment without altering the training process — meaning the model the team validated and the model running in production may diverge. One particularly insidious variant is "candidate model modification," where the attacker manipulates the deployment workflow to swap or alter how a model operates after release. Mitigation focuses on hardening the model serving infrastructure with secure-by-default tooling, model signing and provenance verification, and continuous integrity checks against the deployed artifact.

### SAIF Controls
- Secure-by-Default ML Tooling
- Model and Data Integrity Management

---

## 🐱 7. Denial of ML Service

> *"Cat is too tired to respond."*

### Description
Denial of ML Service is the reduction or complete loss of model availability through queries that consume excessive resources. The risk arises in the application component when the model is exposed to excessive access (insufficient rate limiting, unbounded query complexity), but some types — notably energy-latency attacks and sponge examples — stem from the fundamental functioning of the model itself rather than from infrastructure misconfiguration. The denial can be technical (service is unavailable) or economic (service is technically available but at unsustainable cost — sometimes called Denial of Wallet). Both fall under this risk in the SAIF taxonomy. Mitigation combines classic application-layer controls (rate limiting, quotas, timeouts, queue management) with AI-specific defenses against expensive query patterns.

### SAIF Controls
- Application Access Management

---

## 🐱 8. Model Reverse Engineering

> *"Reconstructing the cat by watching it move."*

### Description
Model Reverse Engineering arises in the application component when excessive query access to the model is granted, allowing attackers to send large numbers of carefully crafted queries and use the responses to reconstruct the model's weights or behavior. The Alpaca 7B project (a model fine-tuned from LLaMA 7B based on 52,000 instruction-following examples generated from a target API) is the canonical demonstration of how cheap and effective this can be — a functional clone built for a few hundred dollars in API costs. Mitigation requires rate limiting at the application or API layer, query-pattern detection to catch systematic extraction campaigns, and limiting the granularity of model output (suppressing logprobs, restricting confidence values) that makes reverse engineering more efficient.

### SAIF Controls
- Application Access Management

---

## 🐱 9. Insecure Integrated Component

> *"The cat door doesn't lock."*

### Description
Insecure Integrated Component is the risk introduced by vulnerabilities in software that interacts with AI models — plugins, libraries, agent tools, application middleware — that attackers can leverage to gain unauthorized model access, insert malicious code, or compromise system operations. As AI systems increasingly assemble from components (LangChain, vLLM, OpenLLM, MCP servers, agent frameworks), the integration boundary becomes a primary attack surface. A single vulnerable plugin in a connected toolchain can compromise the entire AI application. Mitigation requires addressing vulnerabilities directly within the application and agent components, enforcing strict permissions on agents and plugins, and treating the integration surface with the same supply-chain discipline as core dependencies.

### SAIF Controls
- Application Access Management
- Secure-by-Default ML Tooling

---

## 🐱 10. Prompt Injection

> *"Whispering bad ideas to the cat."*

### Description
Prompt Injection is the manipulation of a model's behavior or output through specifically crafted inputs that override or subvert the system's intended instructions. SAIF recognizes both direct injection (malicious user input) and indirect injection (instructions embedded in retrieved content, documents, web pages, or tool outputs that the model processes as if they were authoritative). The risk is exposed in both the application component (where input arrives) and the model component (where instruction-content separation fails). Because LLMs do not reliably distinguish between instructions and content, this is a structural rather than tunable weakness — controls reduce frequency and severity but cannot eliminate the class. Mitigation requires layered defense: input validation and sanitization, adversarial testing during development, output validation, and operational guardrails like Google's Model Armor that screen prompts and responses at runtime.

### SAIF Controls
- Input Validation and Sanitization
- Adversarial Training and Testing
- Output Validation and Sanitization

---

## 🐱 11. Model Evasion

> *"Hiding from the cat in plain sight."*

### Description
Model Evasion is the use of crafted inputs that cause a model to produce incorrect classifications, decisions, or outputs while appearing benign to humans (or while bypassing the model's safety mechanisms). The risk lives in the model itself — even a perfectly deployed, perfectly accessed model can be evaded if its decision surface is not robust to adversarial perturbation. Evasion is especially consequential for ML-based security tooling: malware classifiers, content moderation systems, fraud detection models, and biometric verifiers can all be targeted with adversarial inputs that cause them to misclassify in attacker-controlled directions. The HiddenLayer black-box bypass research demonstrated that effective evasion does not require knowledge of the underlying model architecture. Mitigation focuses on adversarial robustness training, input validation that catches distribution-shifted inputs, and ensemble or diversified detection approaches that don't all share the same failure modes.

### SAIF Controls
- Adversarial Training and Testing
- Input Validation and Sanitization

---

## 🐱 12. Sensitive Data Disclosure

> *"Cat told a stranger your secrets."*

### Description
Sensitive Data Disclosure is the exposure of confidential information — PII, credentials, business secrets, health records, proprietary code — through a model's outputs. The disclosure path can be training-data memorization (the model regurgitates information it learned during training) or runtime context leakage (data passed to the model in one session ends up exposed to a different user). The risk is distributed across the model component (memorization) and the application component (where session boundaries and access controls are enforced). System-prompt-level guidance against disclosing sensitive content is not a security control — it is hint that prompt injection, jailbreaks, or simple confusion can override. Mitigation requires data sanitization before training, output filtering at runtime, scoped access controls on what the model can see in any given session, and explicit policies for what happens to user inputs after a session ends.

### SAIF Controls
- Output Validation and Sanitization
- Application Access Management
- Training Data Sanitization

---

## 🐱 13. Inferred Sensitive Data

> *"Cat figured out something it shouldn't have."*

### Description
Inferred Sensitive Data is a subtler cousin of disclosure: the model produces sensitive information not because it was directly trained on that information, but because it can infer the information from non-sensitive inputs through its learned patterns. A model that was never trained on health records may still infer a person's likely conditions from purchase history, location patterns, or query language. A model that was never given salary data may produce reliable estimates from job title and tenure. The risk is real even when training data is fully sanitized, because inference is an emergent property of capable models trained on enough adjacent data. Mitigation typically requires output filtering for categories of inference the deployment shouldn't produce, careful evaluation against inference-attack benchmarks, and policy decisions about what kinds of inferences the system is permitted to make even when capable.

### SAIF Controls
- Output Validation and Sanitization
- Adversarial Training and Testing

---

## 🐱 14. Insecure Model Output

> *"Cat handed you a wrapped grenade."*

### Description
Insecure Model Output is the risk that LLM-generated content reaches downstream systems without adequate validation, sanitization, or encoding — and triggers the familiar application-security vulnerabilities (XSS, SQL injection, command injection, SSRF, path traversal) when those systems treat model output as trusted input. Because model outputs can be steered by prompt input, accepting model output without scrutiny is functionally equivalent to giving users indirect access to whatever the output flows into. The risk lives in the application component, at the boundary between the model and any downstream system that consumes its output. Mitigation requires treating the model as untrusted: applying the same input-validation and output-encoding pipeline to model output that you would apply to user-submitted form data.

### SAIF Controls
- Output Validation and Sanitization

---

## 🐱 15. Rogue Actions

> *"Cat did the thing. The thing was bad."*

### Description
Rogue Actions is SAIF's name for the risk that an AI agent or AI-integrated application takes actions — sending emails, executing transactions, modifying data, calling external services — that the operator did not intend or authorize. **SAIF 2.0 substantially expanded this risk** as the canonical agent-specific concern: integrating agents into an AI system introduces Rogue Actions by dramatically expanding the model's ability to trigger real-world consequences. The risk is introduced through a failure of the reasoning core to align with user intent, or through poisoning of orchestration components like tools, memory, or retrieved data. The vulnerability is exposed during application usage when the agent inadvertently triggers an unintended action. The mapping to OWASP's Excessive Agency and Agent Goal Hijack is direct.

Mitigation requires a multi-layered defense: filtering and standardizing all inputs before they reach the model, defining tool limitations in the agent's system instructions, hardening the reasoning core with adversarial training to recognize prompt injection, and governing agent capabilities at the orchestration layer with observability, policy engines, and credentialed tool access. SAIF 2.0's three secure-by-design agent principles (well-defined human controllers, carefully limited powers, observable actions and planning) are designed specifically to mitigate this risk.

### SAIF Controls
- Agent Permissions
- Agent User Control
- Agent Observability
- User Transparency and Controls
- Adversarial Training and Testing (for the reasoning core)
- Input Validation and Sanitization

---

## 🛡️ The SAIF Control Categories

SAIF organizes its mitigations into reusable control categories that map across many of the 15 risks:

| Control Category | What it does |
|---|---|
| **Training Data Sanitization** | Removes harmful, unauthorized, or sensitive content before training |
| **Training Data Management** | Lifecycle controls on data sourcing, retention, and use |
| **User Data Management** | Policies and enforcement on user data collection, retention, deletion |
| **Model and Data Inventory Management** | Authoritative inventory of models, datasets, and ML artifacts |
| **Model and Data Access Control** | Identity and authorization controls on AI assets |
| **Model and Data Integrity Management** | Provenance, signing, hashing, tamper detection |
| **Secure-by-Default ML Tooling** | Hardened default configurations across the ML stack |
| **Input Validation and Sanitization** | Filtering and structuring incoming prompts and content |
| **Output Validation and Sanitization** | Filtering and encoding model outputs before downstream use |
| **Adversarial Training and Testing** | Building robustness into models during development |
| **Application Access Management** | Authentication, authorization, rate limiting at the app layer |
| **Agent Permissions** | Least-privilege scoping on agent tools and capabilities |
| **Agent User Control** | Mechanisms for users to constrain or override agent behavior |
| **Agent Observability** | Visibility into what agents are doing and why |
| **User Transparency and Controls** | Communicating AI involvement and risks to users |
| **Red Teaming** | Adversarial testing of deployed systems |
| **Vulnerability Management** | Coordinated disclosure and patching for AI systems |
| **Threat Detection** | Monitoring AI inputs, outputs, and behavior for indicators |
| **Incident Response Management** | Runbooks and processes for AI-specific incidents |

---

## 🆚 SAIF vs. OWASP vs. MITRE ATLAS — How They Fit Together

These three frameworks address overlapping problems from different angles. They are complementary, not redundant.

| Framework | Primary Lens | Best For |
|---|---|---|
| **Google SAIF** | Lifecycle controls and architectural guidance | Building secure-by-default AI infrastructure; harmonizing controls across an organization |
| **OWASP LLM Top 10** | Application-level vulnerability prioritization | Day-to-day developer awareness; AppSec triage for LLM applications |
| **OWASP Agentic Top 10** | Agent-specific vulnerabilities | Threat modeling agentic and multi-agent systems |
| **MITRE ATLAS** | Adversary tactics, techniques, and procedures | Threat intelligence; red-teaming; incident classification |
| **NIST AI RMF** | Risk management governance | Strategic program management; regulatory alignment |
| **CoSAI** | Open-source community standards | Cross-vendor interoperability and shared tooling |

**Practical mapping:**
- **SAIF** answers *"what should our AI security architecture look like?"*
- **OWASP** answers *"what specific bugs and weaknesses should developers know about?"*
- **ATLAS** answers *"how do real adversaries operate, and what should we look for?"*
- **NIST AI RMF** answers *"how do we govern this at the program and business level?"*

Most mature programs use all four together.

---

## 🐾 Defender's Quick-Reference Cheat Sheet

| If you are... | Start with these SAIF elements and risks |
|---|---|
| Building greenfield AI infrastructure | Elements 1, 4 — Risks 3, 5, 6, 9 |
| Adding AI to an existing security program | Elements 2, 3 — Risks 7, 10, 14 |
| Deploying agents or agentic systems | Element 6 — Risks 9, 10, 15 |
| Operating regulated AI (health, finance, gov) | Elements 5, 6 — Risks 2, 4, 12, 13 |
| Running AI red team / pen test | Risks 1, 8, 10, 11 |
| Responding to an active AI incident | Element 2 — Risks 5, 10, 14, 15 |
| Doing AI risk self-assessment | The full [SAIF Risk Self-Assessment](https://saif.google/risk-self-assessment) |

---

## 🤝 Coalition for Secure AI (CoSAI)

In 2024, Google contributed core SAIF assets — the Risk Map, Risk Self-Assessment, and component descriptions — to the **Coalition for Secure AI (CoSAI)**, an open community hosted at the OASIS Open standards body. CoSAI's mission is to develop interoperable, open-source security solutions that any organization can adopt regardless of cloud or vendor. Founding members include Anthropic, Cisco, GenLab, Google, IBM, Intel, Microsoft, NVIDIA, OpenAI, and PayPal, with the membership having since grown to 35+ industry partners.

**SAIF 2.0 (October 2025)** extended this commitment by donating the new Agent Risk Map data to the **CoSAI Risk Map initiative**, ensuring that agent-specific security guidance evolves as community infrastructure rather than a vendor-specific framework.

CoSAI currently runs three technical workstreams:
- **Software Supply Chain Security for AI Systems**
- **Preparing Defenders for a Changing Cybersecurity Landscape**
- **AI Risk Governance** (where the SAIF Risk Self-Assessment lives)

This matters for SAIF practitioners because it commits the framework to community evolution rather than vendor lock-in — and creates a forum where SAIF, OWASP, MITRE ATLAS, NIST AI RMF, and other frameworks are actively being aligned.

🔗 [coalitionforsecureai.org](https://coalitionforsecureai.org)

---

## 🔗 Related Field Guides

- 🐾 [KryptoKat's OWASP LLM Top 10 2025 Reference](https://github.com/cfoudysec/kryptokat-owasp-llm-top10)
- 🐾 [KryptoKat's OWASP Agentic Top 10 2026 Reference](https://github.com/cfoudysec/kryptokat-owasp-agentic-top10)
- 🐾 [KryptoKat's MITRE ATLAS Reference](https://github.com/cfoudysec/kryptokat-mitre-atlas)

---

## 📝 License & Attribution

This reference summarizes content from **Google's Secure AI Framework (SAIF)**, available at [saif.google](https://saif.google). SAIF is a trademark of Google LLC. SAIF documentation is available under Google's standard documentation terms; see the [official SAIF site](https://saif.google) for licensing and terms of use.

This reference is unofficial. KryptoKat is not affiliated with Google or Alphabet.

The hacker cat is just here for moral support. 🐈‍⬛

---

<p align="center">
  <i>Six elements. Four components. Fifteen risks. Defense in depth, end to end.</i><br>
  <b>— ハッカー猫 / KryptoKat</b>
</p>
