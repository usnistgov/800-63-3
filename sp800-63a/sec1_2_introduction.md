<a name="sec1"></a>

<div class="breaker"></div>

## 1. <a name="purpose"></a> Purpose

_This section is informative._

This document provides requirements for enrollment and identity proofing of applicants that wish to gain access to resources at each Identity Assurance Level (IAL).  The requirements detail the acceptability, validation, and verification of identity evidence that will be presented by a subscriber to support their claim of identity. This document also details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining enrollment records and binding authenticators (either CSP-issued or subscriber-provided) to the enrollment record.

<a name="sec2"></a>

## 2. <a name="intro"></a> Introduction

_This section is informative._

One of the challenges associated with digital identity is the association of a set of online activities with a single, specific subject. While there are situations where this is not required or is even undesirable (e.g., use cases where anonymity or pseudonymity are required), there are others where it is important to reliably establish an association with a real-life subject (e.g., obtaining health care and executing financial transactions). There are also situations where the association is required for regulatory reasons (e.g., 'Know Your Customer' requirements, established in response to the USA PATRIOT Act of 2001, in the financial community) or to establish accountability for high-risk actions (e.g., changing the release rate of water from a dam).

There are also instances where it is desirable for a relying party (RP) to know something about a user executing a transaction, but not know the real-life identity of the user.  For example, in order to maintain integrity of the service, it may be desirable to know the home ZIP Code of a user for purposes of census taking or petitioning an elected official but where it is not necessary or desirable to know the underlying identity of the person. IALs provide a method for expressing the level of assurance (LOA) associated with attributes established by the CSP during the proofing process.

The following table states which sections of this document are normative and which are informative:

|Section Name|Normative/Informative|
|----|:--:|
|1. Purpose|Informative|
|2. Introduction|Informative|
|3. Definitions and Abbreviations|Informative|
|4. Identity Assurance Level Requirements|Normative|
|5. Identity Resolution, Validation, and Verification|Normative|
|6. Derived Credentials|Normative|
|7. Threats and Security Considerations|Informative|
|8. Privacy Considerations|Informative|
|9. Usability Considerations|Informative|
|10. References|Informative|

## 2.1. The Steps in Identity Proofing

When a subject is identity proofed, the expected steps are:  

1. Resolve a claimed identity to a single, unique identity within the context of the population of users the CSP serves.
2. Validate that all supplied evidence is correct and genuine (e.g., not counterfeit or misappropriated).
3. Validate that the claimed identity exists in the real world.
4. Verify that the claimed identity is associated with the real-life person supplying the identity evidence.

## 2.2. Identity Assurance Levels

Assurance in a subscriber's identity is described using one of three IALs:

**IAL1** - There is no requirement to link the applicant to a specific real-life identity. Any attributes provided in conjunction with the authentication process are self-asserted or should be treated as self-asserted (including attributes a CSP asserts to an RP). Self-asserted attributes are neither validated nor verified.

**IAL2** - Evidence supports the real-life existence of the claimed identity and verifies that the applicant is appropriately associated with this real-life identity. IAL2 introduces the need for either remote or physically-present identity proofing. Attributes could be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes. A CSP that supports IAL2 can support IAL1 transactions if the user consents.

**IAL3** - Physical presence is required for identity proofing. Identifying attributes must be verified by an authorized and trained representative of the CSP. As with IAL2, attributes could be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.  A CSP that supports IAL3 can support IAL1 and IAL2 identity attributes if the user consents.

At IAL2 and IAL3, pseudonymity in federated environments is enabled by limiting the number of attributes sent from the CSP to the RP, or the way they are presented. For example, if an RP needs a valid birthdate but no other personal details, the RP should leverage a CSP to request just the birthdate of the subscriber. It is preferred for the RP to ask the CSP for an attribute reference. For example, if a RP needs to know if a subscriber is older than 18 they should request a boolean value, not the entire birthdate in order to evaluate age. Users who maintain and IAL3 identity should be able to use their CSP for lower-level and pseudonymous transactions, giving them the added benefit of being able to assert already-verified attributes as part of these transactions. Since the individual will have undergone an identity proofing process at enrollment, interactions with the CSP may not necessarily be pseudonymous.

Detailed requirements for each of the IALs are given in [Section 4](#ial-section) and [Section 5](#ipv-section).
