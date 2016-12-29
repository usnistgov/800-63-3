<a name="sec1"></a>

## 1. Purpose

_This section is informative._

This document and its companion documents, [SP 800-63-3](sp800-63-3.html), [SP 800-63A](sp800-63a.html), and [SP 800-63C](sp800-63c.html), provide technical guidelines to credential service providers for the implementation of digital authentication.

<a name="sec2"></a>

## 2. Introduction

>**MG: first paragraph to be updated by Paul to align with other volumes.**

_This section is informative_

Digital authentication is the process of establishing confidence in user identities electronically presented to an information system. E-authentication presents a technical challenge when this process involves the digital authentication of individual people over a network. 

The ongoing authentication of subscribers is central to this process. Subscriber authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in earlier editions of SP 800-63) associated with a given subscriber. A successful authentication results in the assertion of an identifier, either pseudonymous or non-pseudonymous, and optionally other identity information, to the relying party (RP).

This document provides guidelines on types of authentication processes, including choices of authenticators, that may be used at various *Authenticator Assurance Levels* (AALs). It also provides guidelines on the lifecycle of authenticators, including revocation in the event of loss or theft.

These technical guidelines apply to digital authentication of users systems over a network. They do not primarily address the authentication of a person who is physically present, for example, for access to buildings, although some credentials that are used remotely may also be used in local authentication. These technical guidelines also establish requirements that Federal systems and service providers participating in authentication protocols be authenticated to subscribers.

>**MG: Hopefully removing this last sentence doesn't break anything. Let's leave the door open to repurposing for stronger IoT uses. You'll likely see other adjustments elsewhere for that, such as replacing individual or person with subject.**

The strength of an authentication transaction is characterized by an ordinal measurement known as the AAL. Stronger authentication (a higher AAL) requires a higher level of capabilities or resources on the part of an attacker in order to successfully authenticate, effectively reducing the risk of an authentication error.  A high-level summary of the technical requirements for each of the authenticator assurance levels is provided below; see [Section 4](#sec4) and [5](#sec5) of this document for specific normative requirements.

**Authenticator Assurance Level 1** - AAL 1 provides some assurance that the claimant controls the authenticator registered to a subscriber. AAL 1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.

>**MG: adjust all of these to match -3 changes.**

**Authenticator Assurance Level 2** – AAL 2 provides high confidence that the claimant controls the authenticator registered to a subscriber. Two different authentication factors are required. Approved cryptographic techniques are required at AAL 2 and above.

**Authenticator Assurance Level 3** – AAL 3 provides very high confidence that the claimant controls the authenticator registered to a subscriber. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is similar to AAL 2 except that a "hard" cryptographic authenticator that also provides impersonation resistance is required.
