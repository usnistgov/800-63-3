<a name="sec1"></a>

## 1. Purpose

This recommendation and its companion documents, SP 800-63-3, SP 800-63A, and SP 800-63B, provide technical guidelines to credential service providers for the implementation of remote authentication.

<a name="sec2"></a>

## 2. Introduction

Assertions are statements from a identity provider (IdP) to a relying party (RP) that contain information about a subscriber. Assertions are used when the RP and the verifier are not co-located (i.e., they are connected through a shared network or the internet). The RP uses the information in the assertion to identify the subscriber and make authorization decisions about their access to resources controlled by the RP. An assertion may include identification and authentication statements regarding the subscriber and may additionally include attribute statements that further characterize the subscriber and support the authorization decision at the RP.

Assertions are presented over a network through the use of an identity federation protocol. In a federation protocol, the subscriber does not authenticate directly to the RP using credentials as described in this document suite. Instead, the federation protocol defines a mechanism for an RP to request that an IdP generate an assertion for the currently-present subscriber, by way of having the subscriber authenticate to the IdP. This supports the process of Single Sign On, allowing subscribers to authenticate once to an IdP and subsequently obtain services from multiple RPs, all without requiring the subscriber to hold or maintain separate credentials at each RP. Note that within this document, the use of "RP" refers specifically to the RP of the federation protocol and not the RP of any primary credential.

Assertion mechanisms can also facilitate authentication schemes that are based on the attributes or characteristics of the subscriber. Attributes are often used in determining access privileges for Attribute Based Access Control (ABAC) or Role Based Access Control (RBAC).

It is important to note that assertion schemes are fairly complex multiparty protocols, and therefore have fairly subtle security requirements which must be satisfied. When evaluating a particular assertion scheme, it may be instructive to break it down into its component interactions. Generally speaking, interactions between the subscriber and the IdP and between the subscriber and RP are similar to the authentication mechanisms presented SP 800-63B, while interactions between the IdP and RP convey attributes such as those established using procedures in SP 800-63A. Many of the requirements presented in this document will, therefore, have some relationship with corresponding requirements in those two documents.
