# GDPR Compliance Checklist for Chatbots & AI Assistants

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![GDPR](https://img.shields.io/badge/GDPR-Compliant-green.svg)](https://gdpr.eu/)
[![AI Act 2024/1689](https://img.shields.io/badge/AI%20Act-2024%2F1689-purple.svg)](https://eur-lex.europa.eu/eli/reg/2024/1689/oj)
[![Last Updated](https://img.shields.io/badge/Last%20Updated-April%202026-orange.svg)](#)

A practical, actionable checklist for organizations deploying chatbots and AI assistants in the EU. Covers GDPR obligations and EU AI Act transparency requirements.

---

## Why This Checklist?

Chatbots and AI assistants process personal data by design. Every conversation can contain names, email addresses, phone numbers, preferences, and sometimes sensitive information like health data. **GDPR applies to all of this.**

The EU AI Act (Regulation 2024/1689) adds another layer: AI systems that interact directly with people must clearly disclose they are not human. Transparency is no longer optional.

Most chatbot platform providers (OpenAI, Anthropic, Meta, Google) **leave compliance to the deployer**. Their terms of service explicitly state that you, the organization deploying the chatbot, are the data controller. You are responsible for:

- Informing users they are talking to AI
- Obtaining valid consent where required
- Honoring data subject rights (access, deletion, portability)
- Ensuring data processing agreements are in place
- Documenting your processing activities

This checklist helps you cover every requirement systematically.

---

## Quick Assessment

```
Does your chatbot collect or process personal data?
│
├── YES → GDPR applies. Complete this checklist.
│   │
│   ├── Does it process health data? → Art. 9 applies (explicit consent required)
│   ├── Does it interact with children? → Age verification + parental consent
│   ├── Does data leave the EU? → Art. 44-49 (transfer mechanisms required)
│   └── Is it customer-facing? → AI Act Art. 50 (AI disclosure mandatory)
│
└── NO → Are you sure? Check if conversation logs, IP addresses,
         or analytics cookies count as personal data (they usually do).
```

---

## Checklist

### 1. Legal Basis (Art. 6 GDPR)

- [ ] Identify the legal basis for each processing activity (consent, legitimate interest, contract performance, legal obligation)
- [ ] Document the legal basis in your Record of Processing Activities (ROPA)
- [ ] If relying on **consent**: implement a clear opt-in mechanism before processing begins
- [ ] If relying on **legitimate interest**: conduct and document a Legitimate Interest Assessment (LIA)
- [ ] Ensure the legal basis is specific to each purpose (no blanket consent)

### 2. Transparency (Art. 13-14 GDPR + Art. 50 AI Act)

- [ ] **AI disclosure**: clearly inform users they are interacting with an AI system, not a human (AI Act Art. 50)
- [ ] Display the AI disclosure **before or at the start** of the conversation
- [ ] Make a privacy notice accessible directly from the chatbot interface (link or expandable section)
- [ ] Explain **what data** is collected (messages, metadata, device info, IP)
- [ ] Explain **why** data is collected (each specific purpose)
- [ ] Identify the **data controller** (company name, contact details)
- [ ] Provide **DPO contact** information if a DPO is appointed
- [ ] State **retention periods** for conversation data
- [ ] Explain any **automated decision-making** or profiling (Art. 22)

### 3. Data Minimization (Art. 5 GDPR)

- [ ] Collect only data strictly necessary for the chatbot's purpose
- [ ] Do not store full conversation logs if summaries or aggregates suffice
- [ ] Pseudonymize PII before using conversation data for training or analytics
- [ ] Anonymize analytics data where possible
- [ ] Implement automatic deletion of conversation data after the retention period
- [ ] Avoid collecting data "just in case" for future use
- [ ] Strip unnecessary metadata from stored conversations

### 4. Data Subject Rights (Art. 15-22 GDPR)

- [ ] **Right of access** (Art. 15): users can request a copy of their conversation data
- [ ] **Right to rectification** (Art. 16): users can correct inaccurate data
- [ ] **Right to erasure** (Art. 17): users can request deletion of their data
- [ ] **Right to restriction** (Art. 18): users can request processing be limited
- [ ] **Right to data portability** (Art. 20): export data in a machine-readable format (JSON, CSV)
- [ ] **Right to object** (Art. 21): users can opt out of profiling or marketing
- [ ] Provide a clear mechanism to exercise rights (email, in-chat command, self-service portal)
- [ ] Respond to requests within **30 days**
- [ ] Document all data subject requests and responses

### 5. Data Processing Agreements (Art. 28 GDPR)

- [ ] DPA in place with the **chatbot platform provider**
- [ ] DPA in place with the **AI model provider** (OpenAI, Anthropic, Google, etc.)
- [ ] DPA in place with the **hosting/cloud provider** (AWS, Azure, GCP)
- [ ] DPA in place with any **analytics provider** processing conversation data
- [ ] Verify and document the **sub-processors list** for each provider
- [ ] Ensure DPAs include: subject matter, duration, nature of processing, categories of data, obligations of the processor
- [ ] Review DPAs annually or when providers update their terms

### 6. Security (Art. 32 GDPR)

- [ ] Encrypt data **in transit** (TLS 1.2+)
- [ ] Encrypt data **at rest** (AES-256 or equivalent)
- [ ] Implement access controls and role-based authentication for conversation data
- [ ] Enable audit logging for data access
- [ ] Conduct regular security assessments and penetration testing
- [ ] Establish an **incident response plan** specific to chatbot data breaches
- [ ] Notify the supervisory authority within **72 hours** of a breach (Art. 33)
- [ ] Test backup and recovery procedures for conversation data

### 7. International Transfers (Art. 44-49 GDPR)

- [ ] Map where conversation data is processed and stored (country/region)
- [ ] If data is processed **outside the EU/EEA**: verify an adequacy decision exists for the country
- [ ] If no adequacy decision: implement **Standard Contractual Clauses (SCCs)**
- [ ] Conduct a **Transfer Impact Assessment (TIA)** for each transfer
- [ ] Document the transfer mechanism used for each data flow
- [ ] Monitor changes in adequacy decisions (e.g., EU-US Data Privacy Framework status)

### 8. Special Categories of Data (Art. 9 GDPR)

- [ ] **Health data** (medical/wellness chatbots): obtain **explicit consent** before processing
- [ ] **Children's data**: implement age verification mechanisms
- [ ] **Children's data**: obtain verifiable **parental consent** for users under 16 (or lower age per member state)
- [ ] **Biometric data** (voice assistants): explicit consent and DPIA required
- [ ] Conduct a **Data Protection Impact Assessment (DPIA)** when processing special categories at scale

---

## Common Mistakes

| Mistake | Why It's a Problem | Fix |
|---------|-------------------|-----|
| **"We use OpenAI, so they handle GDPR"** | You are the data controller. The API provider is a processor. Compliance is your responsibility. | Sign a DPA with the provider and implement all controls yourself. |
| **Storing conversations indefinitely** | Violates data minimization (Art. 5) and purpose limitation. | Set retention periods (e.g., 90 days) and auto-delete. |
| **No AI disclosure** | Violates AI Act Art. 50. Fines up to 1.5% of global turnover. | Add a clear message at conversation start. |
| **Cookie-wall style consent** | Consent must be freely given. Blocking the service unless users agree is not valid consent. | Offer a non-personalized fallback or use legitimate interest where appropriate. |
| **Ignoring conversation metadata** | IP addresses, timestamps, device fingerprints, and session IDs are personal data too. | Include metadata in your ROPA and privacy notice. |
| **No process for data subject requests** | Failing to respond within 30 days can trigger complaints and fines. | Set up an intake process with tracking and SLA monitoring. |

---

## Implementation Examples

### AI Disclosure Message

```
// Display at the start of every conversation
const AI_DISCLOSURE = `👋 Hi! I'm an AI assistant powered by [Company Name].
I'm not a human. Your messages may be processed to provide this service.
See our [Privacy Policy](https://example.com/privacy) for details.`;
```

### Consent Collection (Before Processing)

```html
<div class="chatbot-consent">
  <p>Before we start, please review how we handle your data:</p>
  <ul>
    <li>Your messages are processed by an AI system</li>
    <li>Conversations are stored for 90 days</li>
    <li>Data is processed in the EU</li>
  </ul>
  <label>
    <input type="checkbox" id="chatbot-consent" />
    I understand and agree to the <a href="/privacy">Privacy Policy</a>
  </label>
  <button id="start-chat" disabled>Start Chat</button>
</div>
```

### Data Export Endpoint

```python
@app.route("/api/data-export/<user_id>", methods=["GET"])
def export_user_data(user_id):
    """GDPR Art. 20 — Data portability in machine-readable format."""
    conversations = db.get_conversations(user_id)
    return jsonify({
        "user_id": user_id,
        "export_date": datetime.utcnow().isoformat(),
        "conversations": [
            {
                "id": c.id,
                "started_at": c.created_at.isoformat(),
                "messages": c.messages,
                "metadata": c.metadata,
            }
            for c in conversations
        ],
    })
```

### Automatic Data Retention

```sql
-- Delete conversations older than 90 days
DELETE FROM conversations
WHERE created_at < NOW() - INTERVAL '90 days';

-- Anonymize analytics after 12 months
UPDATE analytics
SET user_id = NULL, ip_address = NULL
WHERE created_at < NOW() - INTERVAL '12 months';
```

---

## Related Resources

- [GDPR guide for chatbot developers](https://synaptica-solution.com/guida-chatbot-ai-privacy-gdpr/) — In-depth privacy guide (Italian)
- [What is Human-in-the-Loop?](https://synaptica-solution.com/knowledge/cos-e-human-in-the-loop/) — Why human oversight matters for GDPR
- [AI Act compliance checklist](https://github.com/SynapticaSolution/ai-act-compliance-checklist) — Companion checklist for EU AI Act
- [SideMindBot](https://synaptica-solution.com/sidemind/) — GDPR-compliant chatbot with pseudonymization of 12 PII types
- [AI Act guide for Italian companies](https://synaptica-solution.com/knowledge/guida-ai-act-aziende/) — Practical AI Act implementation
- [Best AI chatbots for Italian companies 2026](https://synaptica-solution.com/knowledge/migliori-chatbot-ai-aziende/) — Comparison with compliance focus
- [Synaptica DPA template](https://synaptica-solution.com/dpa/) — Our Data Processing Agreement

---

## Contributing

Found a gap in the checklist? Regulations change frequently. Open an issue or submit a pull request. Please cite the specific article or recital for any addition.

---

## License

This checklist is released under the [MIT License](LICENSE). Use it freely in your compliance documentation.

---

Made by [Synaptica Solution](https://synaptica-solution.com) — AI Governance & Process Automation for Italian SMEs
