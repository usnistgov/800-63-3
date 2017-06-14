<div class="breaker"></div>
<a name="purpose"></a>

## 1 Purpose

*This section is informative.*

This recommendation and its companion documents, [SP 800-63](sp800-63-3.html), [SP 800-63A](sp800-63a.html), and [SP 800-63B](sp800-63b.html), provide technical guidelines to credential service providers (CSPs) for the implementation of digital authentication.

This document, SP 800-63C, provides requirements to identity providers (IdPs) and relying parties (RPs) of federated identity systems. Federation allows a given IdP to provide authentication and (optionally) subscriber attributes to a number of separately-administered RPs through the use of assertions. Similarly, RPs may use more than one IdP.

<div class="breaker"></div>
<a name="introduction"></a>

## 2 Introduction

*This section is informative.*

Federation is a process that allows for the conveyance of authentication and subscriber attribute information across networked systems. In a federation scenario, the verifier or CSP is referred to as an identity provider, or IdP. The RP is the party that receives and uses the information provided by the IdP.

Federated identity systems use assertions to accomplish this task. Assertions are statements from an IdP to an RP that contain information about a subscriber. Federation technology is generally used when the RP and the IdP are not a single entity or are not under common administration. The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. An assertion typically includes an identifier for the subscriber, allowing association of the subscriber with their previous interactions with the RP. Assertions may additionally include attribute values or attribute references that further characterize the subscriber and support the authorization decision at the RP. Additional attributes may also be available outside of the assertion as part of the larger federation protocol. These attribute values and attribute references are often used in determining access privileges for Attribute Based Access Control (ABAC) or facilitating a transaction (e.g., shipping address).

In a federated identity scenario, the subscriber does not authenticate directly to the RP. Instead, the federation protocol defines a mechanism for an IdP to generate an assertion for the identifier associated with a subscriber, usually in response to a request from the RP. The IdP is responsible for authenticating the subscriber (though it may use session management as described in [SP 800-63B, Section 7](sp800-63b.html#sec7)). This process allows the subscriber to obtain services from multiple RPs without the need to hold or maintain separate credentials at each. This process can also be used to support *single sign on*, where subscribers authenticate once to an IdP and subsequently obtain services from multiple RPs.

Federation requires relatively complex multiparty protocols that have subtle security and privacy requirements and require careful consideration. When evaluating a particular federation structure, it may be instructive to break it down into its component interactions. Generally speaking, authentication between the subscriber and the IdP will be based on the authentication mechanisms presented in SP 800-63B, while interactions between the IdP and RP will convey attributes established using procedures in SP 800-63A and other self-asserted attributes. Many of the requirements presented in this document, therefore, have some relationship with corresponding requirements in those two documents.

The following table states which sections of the document are normative and which are informative:

|Section Name|Normative/Informative|
|----|:--:|
|1. Purpose|Informative|
|2. Introduction|Informative|
|3. Definitions and Abbreviations|Informative|
|4. Federation Assurance Level (FAL)|Normative|
|5. Federation|Normative|
|6. Assertion|Normative|
|7. Assertion Presentation|Normative|
|8. Security|Informative|
|9. Privacy Considerations|Informative|
|10. Usability Considerations|Informative|
|11. Examples|Informative|
|12. References|Informative|
