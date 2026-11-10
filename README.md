# PhishSense Pro — SOC-Style Phishing Investigation Lab

**CodeAlpha Cyber Security Internship · Task 2: Phishing Awareness Training**

PhishSense Pro is a browser-based cybersecurity awareness application with a SOC-inspired interface. It provides fictional email investigations, transparent rule-based risk scoring, local URL heuristics, an explainable rule sandbox, and a knowledge quiz.

## Features

### 1. Training overview
- Session-level investigation metrics
- Detection accuracy based on the built-in scenario labels
- Recent activity and training-module shortcuts

### 2. Email investigation lab
- Six fictional email samples: phishing and likely legitimate
- Sender, reply-to, return-path, recipient, timestamp, and message inspection
- Simulated raw email headers (including illustrative SPF/DKIM/DMARC outcomes)
- Rule-based findings with explanations
- Manual trainee verdict for each message

### 3. URL inspector
- Local checks for HTTP vs HTTPS, IP-address hosts, punycode, excessive subdomains, suspicious hostname wording, URL shorteners, unusual ports, percent encoding, and user-info URL structure
- Does not open URLs, resolve DNS, or contact external reputation services

### 4. Threat analyzer
- Interactive indicator sandbox
- Documented weights and live score calculation
- Risk bands: Low, Medium, High
- Explainable findings

### 5. Knowledge center
- Social-engineering, sender/domain, link-safety, and incident-response guidance
- Five-question knowledge check with immediate score

## Run locally

1. Download and extract the project ZIP.
2. Open `simulator/index.html` in a modern browser.
3. No installation, server, database, or internet connection is required.

## Project structure

```text
PhishSense_Pro/
├── simulator/
│   └── index.html
└── README.md
```

## Risk-scoring model

The email training rules use the following illustrative weights:

| Indicator | Weight |
|---|---:|
| Sender/domain mismatch | 25 |
| Credential or sensitive-data request | 25 |
| Suspicious or unverified URL | 20 |
| Urgency, threat, or pressure | 15 |
| Unexpected attachment | 10 |
| Impersonation or secrecy tactic | 15 |

Selected weights are summed and capped at 100.

- **Low:** 0–29
- **Medium:** 30–64
- **High:** 65–100

These are educational heuristic weights, not probabilities, calibrated detections, or a substitute for a production email security gateway. The built-in examples have fixed training indicators so learners can compare their judgement with the expected explanation.

## Safety and privacy

- All messages, identities, domains, and header results are fictional training examples.
- The `.example`, `.test`, and reserved example-style domains are used to avoid directing learners to real organizations.
- No messages are sent or received.
- No credentials or personal data are collected.
- No URL is opened, fetched, resolved, or checked against a live reputation feed.
- All logic runs locally in the browser; no analytics or external JavaScript libraries are used.

## Limitations

This is a training simulator, not a forensic mail gateway. It does not validate real SPF/DKIM/DMARC signatures, detonate attachments, inspect actual MIME payloads, perform DNS lookups, or query threat-intelligence databases. The URL inspector uses string-based heuristics and can produce false positives or false negatives. A low score must never be interpreted as proof that a site is safe.

## Suggested demonstration

1. Open the Overview and explain the training-only metrics.
2. Investigate M-001 and run the rule engine.
3. Inspect the simulated raw headers.
4. Compare with the legitimate library reminder M-004.
5. Use the URL Inspector with the provided suspicious example.
6. Demonstrate the Threat Analyzer sandbox and explain the weights.
7. Complete the Knowledge Center quiz.

## Author

Created as an educational cybersecurity awareness project for the CodeAlpha internship.
