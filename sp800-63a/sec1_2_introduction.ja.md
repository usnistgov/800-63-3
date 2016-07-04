<a name="sec1"></a>

# 1. <a name="purpose"></a> Purpose

This document provides requirements for enrollment and identity proofing of subscribers that wish to gain access to online resources for each Identity Assurance Level (IAL).  The requirements detail the acceptability, validation, and verification of identity evidence that will be presented by an individual to support their claim of identity. This document also details the responsibilities of Credential Service Providers (CSPs) with respect to establishing and maintaining enrollment records, and binding of authenticators (either CSP issued or subscriber-provided) to the enrollment record. 

<a name="sec2"></a>

# 2. <a name="intro"></a> Introduction

One of the challenges associated with authenticating people is the association of their online activities with a specific physical person. While there are situations where this is not required or is even undesirable (i.e., use cases where anonymity or pseudonymity are required), there are others where it is important to reliably establish the association with a physical person. Examples include obtaining health care and executing financial transactions. There are also situations where the association is required for regulatory reasons (e.g., Know Your Customer requirements in the financial community) or to establish accountability for high-risk actions (e.g., the release of water from a hydroelectric dam).

There are also instances where it is desirable for a relying party (RP) to know something about a user executing a transaction, but not know the real human identity of the person.  For example, in order to maintain integrity of the service, it may be desirable to know the home ZIP Code of a user for purposes of census taking or petitioning an elected official but where it is not necessary or desirable to know the underlying identity of the person. Identity assurance levels provide a method for expressing the level of assurance associated with attributes established by the credential service provider during the proofing process.

## 2.1. Expected Outcomes of Identity Proofing

The objective of identity proofing is to:  

* Resolve a claimed identity to a single, unique identity within the context of the population of users the CSP serves.
* Validate that all evidence that is supplied is valid (correct) and genuine (not counterfeit or misappropriated).
* Validate that the claimed identity exists in the real world.
* Verify that the claimed identity is associated with the real person supplying the identity evidence.

## 2.2. Identity Assurance Levels

Assurance in a subscriber's identity is described using one of three IALs: 

**Identity Assurance Level 1**:
At this level, there is no requirement for an applicant's identity to be proven.  Any attributes provided in conjunction with the authentication process are self-asserted.

**Identity Assurance Level 2**:
At IAL 2, the claimed identity is proven with evidence that supports the real world existence of the claimed identity and identifies and verifies the person to whom the claimed identity belongs.  IAL 2 introduces the need for either remote or in-person identity proofing.  Attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.

**Identity Assurance Level 3**:
At Identity Assurance Level 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized and trained representative of the CSP. As with IAL 2, attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes. 

At IAL 2 and IAL 3, pseudonymity is enabled by CSP limiting the number of attributes sent, or the way they are presented, to the RP. For example, if an RP needs a valid birthdate but no other personal details, the RP should leverage a CSP to request just the birthdate of the subscriber. It is preferred for the RP to ask the CSP for an attribute claim. For example, if an RP needs to know if a claimant is older than 18 they should request a boolean value, not the entire birthdate for them to evaluate age.

Since the individual will have undergone an identity proofing process at enrollment and likely associated with one or more authenticators, transactions are not pseudonymous with respect to individual interactions with the CSP.

Detailed requirements for each of the IALs is given in [Section 4](#ial-section) and [Section 5](#ipv-section).
