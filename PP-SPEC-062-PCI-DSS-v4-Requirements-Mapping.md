# PP-SPEC-062: Proof of Efficacy Mapping to PCI DSS v4.0.1

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | Payment Card Industry Data Security Standard (PCI DSS) v4.0.1, PCI Security Standards Council |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how PCI DSS requirements and their associated assessment context can be bound to Proof Protocol test cases, evidence, and efficacy results.

The Payment Card Industry Data Security Standard (PCI DSS) is published and maintained by the PCI Security Standards Council, LLC (PCI SSC). PCI DSS v4.0.1 was published in June 2024 as a limited revision of v4.0; v4.0 was retired on 31 December 2024, and the future-dated requirements introduced in v4.0 became effective on 31 March 2025. PCI SSC's document library lists PCI DSS v4.0.1 as the current version at the time of writing, and no successor version had been published. This mapping targets **PCI DSS v4.0.1 (June 2024)**.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

PCI DSS supplies external context that can identify what should be examined or tested within an entity's cardholder data environment. It is organized into 12 principal requirements grouped under six headings, with hierarchically numbered requirements (identifier format such as `1.2.1`), defined approach requirements and testing procedures, customized approach objectives, applicability notes, guidance, and appendices including additional requirements (A1, A2, A3), compensating controls (B, C), and the customized approach (D, E). Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Many PCI DSS requirements concern policy, documentation, roles, inventories, training, and process. Those requirements can be referenced by a proof record but are not themselves empirical efficacy claims (see section 4 and rule 9).

Validation of PCI DSS compliance is performed through the assessment and reporting processes defined by PCI SSC and the applicable payment brands, including Qualified Security Assessors (QSAs) where required. Proof Protocol does not replace those processes.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to PCI DSS v4.0.1

Exact upstream identifiers SHOULD be taken from the authoritative version being mapped and recorded in the ProofBundle™. Upstream titles and text SHOULD NOT be copied into the ProofBundle™ unless the upstream terms permit it. This specification does not redefine upstream requirements.

| PCI DSS context | Proof Protocol treatment | Evidence |
|---|---|---|
| Principal requirement (1 to 12) and its heading group | Record the principal requirement number and the PCI DSS version as test context. | Requirement metadata |
| Requirement / sub-requirement (identifier format such as `1.2.1`) | Bind the requirement identifier to one or more test cases where the requirement states a testable security outcome. | Proof record; corpus manifest |
| Defined approach requirement and testing procedure | Reference by identifier only; record that a Proof Protocol test is distinct from the PCI DSS testing procedure performed by an assessor. | Requirement metadata |
| Customized approach objective | Bind the objective identifier to tests that exercise whether the entity's customized control meets the stated objective under adversarial conditions. | Proof records; outcome evidence |
| Targeted risk analysis | Reference as non-empirical context that sets frequency or scope; MUST NOT be scored as efficacy. | Requirement metadata |
| Compensating control (Appendices B and C) | Record the compensating control separately and exercise the original requirement's intended outcome against it. | Control descriptor; proof records |
| Control operation within the cardholder data environment | Exercise the defined condition and capture whether the control operated on in-scope system components. | Execution evidence |
| Segmentation or scope-reduction claim | Exercise connectivity and bypass conditions between in-scope and out-of-scope networks where efficacy of isolation is claimed. | Robustness evidence |
| Detection and logging outcome | Record whether the control identified the exercised condition, separately from whether account data was protected. | Detection result |
| Protected outcome for account data | Establish whether cardholder data or sensitive authentication data reached an unauthorized destination when efficacy is claimed. | Target/outcome evidence |
| System/version context | Bind material system component, policy, configuration, service provider, and environment versions. | Environment descriptor |
| Assessment evidence export | Package evidence and provenance for independent examination by an assessor or acquiring party. | ProofBundle |

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use PCI DSS v4.0.1, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **PCI DSS supplies payment account data security requirements as external context. Proof Protocol supplies the evidence model for independently examining whether a selected control performed as claimed.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by PCI Security Standards Council, LLC is implied.

## 10. Source Framework, Attribution, and License

PCI DSS is external work owned and published by the PCI Security Standards Council, LLC. The standard carries the notice "©2006 - 2024 PCI Security Standards Council, LLC. All Rights Reserved." PCI SSC's website Terms and Conditions reserve all right, title, and interest in its Content, permit viewing, downloading, and printing for personal, non-commercial review, study, and informational purposes, and prohibit publishing, distributing, copying, or preparing derivative works of Content except under a separate written agreement with PCI SSC.

Names, marks, and designations including PCI Security Standards Council, PCI SSC, and PCI DSS remain the property of PCI Security Standards Council, LLC. Use of these names in this specification is nominative and descriptive only.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY-ND 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

Contributors MUST NOT copy PCI DSS requirement text, testing procedures, customized approach objectives, applicability notes, guidance, glossary definitions, or templates into this repository. Reference requirement identifiers and independently authored descriptions only. A Proof Protocol result is not a PCI DSS assessment, Report on Compliance, Attestation of Compliance, or validation of compliance.

### Required attribution

PCI SSC does not publish a specific attribution line for citing PCI DSS identifiers. The standard carries the following copyright notice (quoted verbatim from PCI DSS v4.0.1, June 2024, document library: https://www.pcisecuritystandards.org/document_library/):

> ©2006 - 2024 PCI Security Standards Council, LLC. All Rights Reserved.

PCI SSC website terms (https://www.pcisecuritystandards.org/terms-and-conditions/) reserve all rights in its Content and prohibit copying, distribution, and derivative works without a separate written agreement.

Recommended attribution and citation for this mapping:

> PCI Security Standards Council, "Payment Card Industry Data Security Standard: Requirements and Testing Procedures", v4.0.1, June 2024. ©2006 - 2024 PCI Security Standards Council, LLC. All Rights Reserved. PCI DSS and PCI Security Standards Council are names and marks of PCI Security Standards Council, LLC. https://www.pcisecuritystandards.org/document_library/

**What this specification reproduces:** the standard's name, version, date, and title; requirement identifiers and the identifier format; names of structural elements (principal requirement, defined approach, customized approach, compensating control, targeted risk analysis, appendix designations); and short independently authored factual statements. **What it does not reproduce:** requirement text, testing procedures, customized approach objectives, applicability notes, guidance, glossary entries, worksheets, or templates. Because no PCI SSC Content is copied, distributed, or adapted, the mapping does not fall within the prohibited uses in the PCI SSC Terms and Conditions and does not relicense PCI SSC material.

## 11. Versioning

This mapping is versioned independently of PCI DSS v4.0.1. Material upstream changes SHOULD trigger a mapping review and, where necessary, a new version identifying the upstream revision mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
