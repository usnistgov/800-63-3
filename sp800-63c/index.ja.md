---
layout: page
title: "SP 800-63C"
description: "SP 800-63C"
---

# SP 800-63C

This is a working draft of NIST Special Publication 800-63C, *Assertions and Federation*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63C provides guidance on the use of assertions to convey the results of authentication processes to a relying party. Assertions are used in federated identity systems where the authentication is performed a verifier (sometimes called an Identity Provider) and used by a different party, sometimes called a Relying Party. Federation permits a centrally-managed set of credentials to be used at a number if different relying parties.

Keys and other secrets used to maintain state (stored in cookies, local storage, etc.) have been sometimes characterized as local assertions, but have very different requirements and characteristics than assertions conveyed between different parties. Accordingly, such "local assertions" are treated as reauthentication secrets and covered in SP 800-63B.

This document is broken up into sections as follows:

[Front matter](front.html)

[1. Purpose and 2. Introduction](sec1_2_introduction.html)

[3. Definitions and Abbreviations](sec3_definitions.html)

[4. Assertion Strength](sec4_strength.html)

    4.1. Bearer assertions
    4.2. Holder of key assertions

[5. Assertion Models](sec5_models.html)

    5.1 Direct Model
    5.2 Indirect Model

[6. Examples](sec6_examples.html)

    6.1. SAML
    6.2. Kerberos
    6.3. OpenID Connect and OAuth

[7. Assertion Threats](sec7_threats.html)

[8. Privacy Considerations](sec8_privacy.html)

[9. Usability](sec9_usability.html)

[10. References](sec10_references.html)
