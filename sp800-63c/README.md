# SP 800-63C

This is a working draft of NIST Special Publication 800-63C, *Assertions and Federation*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/README.md) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63C provides guidance on the use of assertions to convey the results of authentication processes to a relying party. Assertions are used in federated identity systems where the authentication is performed a verifier (sometimes called an Identity Provider) and used by a different party, sometimes called a Relying Party. Federation permits a centrally-managed set of credentials to be used at a number if different relying parties.

Keys and other secrets used to maintain state (stored in cookies, local storage, etc.) have been sometimes characterized as local assertions, but have very different requirements and characteristics than assertions conveyed between different parties. Accordingly, such "local assertions" are treated as reauthentication secrets and covered in SP 800-63B.

This document is broken up into sections as follows:

[Front matter](front.md)

[1. Purpose and 2. Introduction](sec1_2_introduction.md)

[3. Definitions and Abbreviations](sec3_definitions.md)

[4. Assertion Strength](sec4_strength.md)

    4.1. Bearer assertions
    4.2. Holder of key assertions

[5. Assertion Models](sec5_models.md)

    5.1 Direct Model
    5.2 Indirect Model

[6. Examples](sec6_examples.md)

    6.1. SAML
    6.2. Kerberos
    6.3. OpenID Connect and OAuth

[7. Assertion Threats](sec7_threats.md)

[8. Privacy Considerations](sec8_privacy.md)

[9. Usability](sec9_usability.md)

[10. References](sec10_references.md)
