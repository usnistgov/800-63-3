<a name="sec1"></a>

## 1. Purpose

This recommendation and its companion documents, [SP 800-63-3](sp800-63-3.html), [SP 800-63A](sp800-63a.html), and [SP 800-63C](sp800-63c.html), provide technical guidelines to credential service providers for the implementation of digital authentication.

<a name="sec2"></a>

## 2. Introduction

Digital authentication is the process of establishing confidence in user identities electronically presented to an information system. E-authentication presents a technical challenge when this process involves the digital authentication of individual people over a network. 

The ongoing authentication of subscribers is central to this process. Subscriber authentication is performed by verifying that the claimant controls one or more *authenticators* (called *tokens* in earlier editions of SP 800-63) associated with a given subscriber. A successful authentication results in the assertion of an identifier, either pseudonymous or non-pseudonymous, and optionally other identity information, to the relying party (RP).

This document provides guidelines on types of authentication processes, including choices of authenticators, that may be used at various *Authenticator Assurance Levels* (AAL). It also provides guidelines on the lifecycle of authenticators, including revocation in the event of loss or theft.

These technical guidelines apply to digital authentication of human users to IT systems over a network. They do not primarily address the authentication of a person who is physically present, for example, for access to buildings, although some credentials that are used remotely may also be used in local authentication. These technical guidelines also establish requirements that Federal IT systems and service providers participating in authentication protocols be authenticated to subscribers. However, these guidelines do not specifically address machine-to-machine (such as router-to-router) authentication, or establish specific requirements for issuing authentication credentials to machines and servers when they are used in e-authentication protocols with people.

The strength of an authentication transaction is characterized by a categorization known as the AAL. Stronger authentication (a higher AAL) requires a higher level of capabilities and/or resources on the part of an attacker in order to successfully authenticate.  A high-level summary of the technical requirements for each of the authenticator assurance levels is provided below; see [Section 4](#sec4) and [5](#sec5) of this document for specific normative requirements.

**Authenticator Assurance Level 1** - AAL 1 provides single factor authentication, giving some assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. AAL 1 allows a wide range of available authentication technologies to be employed. It also permits the use of any of the authentication methods of higher authenticator assurance levels, therefore allowing CSPs to allow users to use a higher AAL authenticator to be at AAL 1. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.

**Authenticator Assurance Level 2** – AAL 2 provides higher assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. At least two different authentication factors SHALL be used. AAL 2 also permits any of the authentication methods of AAL 3. AAL 2 authentication requires cryptographic mechanisms that protect the primary authenticator against compromise by the protocol threats for all threats at AAL 1. Approved cryptographic techniques SHALL be used at AAL 2 and above.

**Authentication Assurance Level 3** – AAL 3 is intended to provide the highest practical digital authentication assurance. Authentication at AAL 3 is based on proof of possession of a key in a physical authenticator through a cryptographic protocol. AAL 3 is similar to AAL 2 except that only hardware cryptographic authenticators are allowed (in conjunction with a memorized secret if a single-factor cryptographic device is used) and that the authenticator SHALL be resistant to verifier impersonation attacks. The authenticator SHALL be a hardware cryptographic module validated at Federal Information Processing Standard (FIPS) 140 Level 2 or higher overall (Level 1 for single-factor authenticators) with at least FIPS 140 Level 3 physical security. AAL 3 authenticator requirements can be met by using the PIV authentication private key of a FIPS 201 compliant Personal Identity Verification (PIV) Card.

