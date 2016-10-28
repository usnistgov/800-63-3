<a name="sec1"></a>

## 1. Purpose

This recommendation and its companion documents, [SP 800-63-3](sp800-63-3.html), [SP 800-63A](sp800-63a.html), and [SP 800-63B](sp800-63b.html), provide technical guidelines to credential service providers for the implementation of remote authentication.

This document, SP 800-63C, provides guidelines to credential service providers and relying parties of federated identity systems. Federation allows a given credential service provider to provide authentication and (optionally) subscriber attributes to a number of separately administered relying parties. Similarly, relying parties may use more than one credential service provider.

<a name="sec2"></a>

## 2. Introduction

Federation is a process that allows for the conveyance of authentication and subscriber attribute information across a set of networked systems. In a federation scenario, the verifier and/or CSP is referred to as an identity provider, or IdP. The relying party, or RP, is the party that receives and uses the information provided by the IdP.

To accomplish this task, federated identity systems use assertions. Assertions are statements from an identity provider to a relying party that contain information about a subscriber. They are used when the RP and the IdP are not a single entity or are not under common administration. The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. An assertion typically includes an identifier allowing association of the subscriber with their previous interactions with the RP and may additionally include attributes or claims that further characterize the subscriber and support the authorization decision at the RP.

In a federated identity scenario, the subscriber does not authenticate directly to the RP. Instead, the federation protocol defines a mechanism for an RP to request that an IdP authenticate the subscriber (or depend on a recent authentication of the subscriber  by the IdP) and generate an assertion for the identifier associated with that subscriber. This allows the subscriber to obtain services with multiple RPs without the need to hold or maintain separate credentials at each. This can also be used to support *single sign on*, where subscribers authenticate once to an IdP and subsequently obtain services from multiple RPs.

Assertion mechanisms typically also provide the RP with attributes or attribute claims describing the subscriber. These attributes and claims are often used in determining access privileges for Attribute Based Access Control (ABAC) or may also be used to facilitate a transaction (mailing address, for example).

It is important to note that federation requires relatively complex multiparty protocols that have subtle security requirements requiring careful consideration. When evaluating a particular federation structure, it may be instructive to break it down into its component interactions. Generally speaking, authentication between the subscriber and the IdP will be based on the authentication mechanisms presented in SP 800-63B, while interactions between the IdP and RP will convey attributes established using procedures in SP 800-63A and other self-asserted attributes. Many of the requirements presented in this document, therefore, have some relationship with corresponding requirements in those two documents.
