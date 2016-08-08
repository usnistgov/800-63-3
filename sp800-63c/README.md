# SP 800-63C

This is a working draft of NIST Special Publication 800-63C, *Assertions and Federation*. This document is a sub-document referenced by [SP 800-63-3](../sp800-63-3/README.md) covering the associated topics that had been previously in SP 800-63-2.

SP 800-63C provides guidance on the use of assertions to convey the results of authentication processes to a relying party. Assertions are used in federated identity systems where the authentication is performed a verifier (sometimes called an Identity Provider) and used by a different party, sometimes called a Relying Party. Federation permits a centrally-managed set of credentials to be used at a number if different relying parties.

Keys and other secrets used to maintain state (stored in cookies, local storage, etc.) have been sometimes characterized as local assertions, but have very different requirements and characteristics than assertions conveyed between different parties. Accordingly, such "local assertions" are treated as reauthentication secrets and covered in SP 800-63B.

This document is broken up into sections as follows:

[Front matter](front.md)

[1. Purpose and 2. Introduction](sec1_2_introduction.md)

[3. Definitions and Abbreviations](sec3_definitions.md)

[4. Federation](sec4_federation.md)

[5. Assertion Strength](sec5_strength.md)

[6. Assertion Presentation](sec6_presentation.md)

[7. Federation Assurance Level](sec7_fal.md)

[8. Security](sec8_security.md)

[9. Privacy](sec9_privacy.md)

[10. Usability](sec10_usability.md)

[11. Assertion Examples](sec11_examples.md)

[12. References](references.md)
