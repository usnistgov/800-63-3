<a name="vectors-of-trust-mapping"></a>

<div class="breaker"></div>

## Mapping Assurance Levels to Vectors of Trust
_This section is normative._

Vectors of Trust (VoT) is a standard for expressing information about an authentication transaction from an IdP to an RP. This information is split into several orthogonal component categories, much in the same way that the assurance levels defined in 800-63 are split into different xAL categories.

### Trustmark

The trustmark URI for these definitions is [[ URI for this document ]].

### VoT Components

This document uses the four components defined in VoT: Identity Proofing (P), Primary Credential Usage (C), Primary Credential Management (M), and Assertion Presentation (A).

The VoT components P, C, and A correspond to 800-63's Identity Assurance Level (IAL), Authenticator Assurance Level (AAL), and Federation Assurance Level (FAL), respectively. While M does not correspond directly to an 800-63 assurance level category, this document defines a set of M values derived from requirements and recommendations in 800-63. This document does not define any additional component categories.

This document uses terms as defined in 800-63-3, Appendix A - Definitions and Abbreviations. Some definitions differ from those in VoT. Notably, the term "authenticator" herein has the same meaning as "credential" in VoT.

## Component Values

This document defines new component values in accordance with Section 8 of VoT.

### Identity Proofing

IAL maps into the VoT component P using a numeric identifier. Identity proofing characteristics map into P using an alphabetic identifier.

#### IAL to VoT

|IAL|Component Value|
|:----:|:--:|
|IAL1 (with no attributes)|P0|
|IAL1|P1|
|IAL2|P2|
|IAL3|P3|

#### Identity Proofing Characteristics

|Identity Proofing Characteristic|Component Value|
|:----:|:--:|
|In-person|Pi|
|Remote|Pr|
|Knowledge-based Verification (KBV)|Pk|
|Address Confirmation with Postal Address|Pa|
|Trusted Referee|Pt|
|Additional features implemented beyond requirements for asserted IAL|Px|
|**NOTE: We don't think Px conveys very much - because which values represent "approaches beyond those required under the asserted IAL"? Suggest removing this value. Does this comment also apply to Ax for federation?**||

>Note: Any credential service provider performing identity proofing at IAL2 or IAL3 MUST conduct a privacy risk assessment. Trusted referee policy and procedures MUST be documented per SP 800-63A Section 5.3.4.

### Authenticator Usage

AAL maps into the VoT component C using a numeric identifier. Authenticator types and characteristics map into C using an alphabetic identifier.

#### AAL to VoT

|AAL|Component Value|
|:----:|:--:|
|AAL1|C1|
|AAL2|C2|
|AAL3|C3|

#### Authenticator Types

|Authenticator Type|Component Value|
|:----:|:--:|
|Memorized Secret|Cc|
|Look-up Secret|Cu|
|Out-of-band Device|Co|
|Single-factor OTP|Ca|
|Multi-factor OTP|Cb|
|Single-factor Cryptographic Software|Cd|
|Single-factor Cryptographic Device|Ce|
|Multi-factor Cryptographic Software|Cf|
|Multi-factor Cryptographic Device|Cg|
|Restricted Authenticator|Cr|

#### Authentication Characteristics

|Authentication Characteristic|Component Value|
|:----:|:--:|
|FIPS 140 Validation|Ci|
|Man-in-the-middle Attack Resistance|Cm|
|Verifier Impersonation Resistance|Cv|
|Verifier Compromise Resistance|Cs|
|Authentication Intent|Cn|
|Additional features implemented beyond requirements for asserted AAL|Cx|
|Presentation Attack Detection (PAD)|Ck|
|Biometric comparison performed centrally|Ct|

>Note: Some authentication approaches described in Table XX are not applicable for all three AALs.

### Authenticator Lifecycle Management to VoT

Authenticator lifecyle management characteristics, per 800-63B Section 6, map into the VoT component M using an alphabetic identifier.

|Authenticator Lifecycle Management Characteristic|Component Value|
|:----:|:--:|
|Authenticator issued/bound during proofing session|Mp|
|Authenticator issued/bound after proofing session (remote)|Mr|
|Authenticator issued/bound after proofing session (in-person)|Mi|
|Second factor bound to a single-factor account|Ms|
|Authentication factors reestablished (account recovery) using abbreviated proofing process|Ma|

### Federation and Assertions

FAL maps into the VoT component A using a numeric identifier. Assertion presentation maps into A using an alphabetic identifier.

#### FAL to VoT

|FAL|Component Value|
|:----:|:--:|
|FAL1|A1|
|FAL2|A2|
|FAL3|A3|

#### Assertion Presentation

|Presentation|Component Value|
|:----:|:--:|
|Front channel|Af|
|Back channel|Ab|
|Additional features implemented beyond requirements for asserted FAL|Ax|

## How to Use the Values in Vectors

The implemented IAL, AAL, and/or FAL component value(s) SHALL be indicated in the vector. Only one numeric identifier SHALL be used for each xAL. Any discrepancies in the assessed and implemented assurance level SHOULD be documented in a digital identity acceptance statement, per SP 800-63-3 Section 5.5.

Identity proofing characteristics, authenticator type(s) used, authentication characteristics, authenticator lifecycle management characteristics, and assertion presentation values MAY be indicated in the vector. Per the requirements in the following sections, some of these values SHALL be indicated in the vector depending on the approaches implemented. Multiple alphabetic identifiers MAY be used simultaneously. 

Identity proofing characteristics, authenticator type(s) used, authentication characteristics, and assertion presentation values SHOULD be indicated only when they demonstrate the implementation of approaches beyond those required by the xAL indicated in the vector. The appropriate value that signifies this (i.e., Px, Cx, and Ax) SHOULD also be indicated. Values SHOULD NOT be indicated that represent approaches already required by the xAL indicated in the vector. These approaches are assumed to be implemented per the xAL's requirements. 

**Example:** C2.Cx.Cv could be asserted if implementing AAL2 and an authenticator is used that provides verifier impersonation resistance, since verifier impersonation resistance is not required under AAL2.

Any additional component categories SHALL NOT be used.

### Identity Proofing Characteristics

If implementing IAL2 and KBV is used for identity verification, Pk SHALL be indicated in the vector (e.g., P2.Pk).

If using a trusted referee acting on behalf of the applicant in the identity proofing process, Pt SHALL be indicated in the vector.

If the subscriber is identity proofed in-person, Pi SHOULD be indicated in the vector.

If the subscriber is identity proofed remotely, Pr SHOULD be indicated in the vector.

If confirming an applicant's address by sending an enrollment code to a postal address, Pa SHOULD be indicated in the vector.

### Authenticator Types

The authenticator type(s) used SHALL be indicated in the vector with the following exceptions.

If implementing AAL3 and authentication is achieved using one of the following two options, the authenticator types used MAY NOT be indicated in the vector.

* Multi-Factor Cryptographic Device; OR
* Single-Factor Cryptographic Device used in conjunction with Memorized Secret

If the user authenticates using a restricted authenticator, Cr and the value representing the authenticator used SHALL be indicated in the vector.

**Example:** Cr.Co would be asserted if the user authenticates using a secret sent via SMS to an out-of-band device.

### Authentication Characteristics

If implementing AAL1 or AAL2, and:

* the user authenticates with an authenticator that provides verifier impersonation resistance, Cv SHOULD be indicated in the vector.
* the user authenticates with an authenticator that provides verifier compromise resistance, Cs SHOULD be indicated in the vector.
* authentication intent from at least one authenticator is demonstrated, Cn SHOULD be indicated in the vector.
* for non-government agency authenticators and verifiers, authenticator(s) or verifier(s) are validated to meet the requirements of FIPS 140 Level 1, Ci SHOULD be indicated in the vector.

If using a biometric for authentication, and:

* biometric comparison is performed centrally (not locally on the claimant's device), Ck SHALL be indicated in the vector.
* the biometric system implements PAD, Ck SHOULD be indicated in the vector.

**NOTE: Should we add a vector value for FMR?**

MitM attack resistance

**NOTE: I'm struggling to find the case where a MitM resistance value is interesting - it seems to be required most of the time and would be redundant with the xAL indicated in the vector.**

### Authenticator Lifecycle Management

If the authenticator(s) is/are bound/issued:

* during a single proofing session, Mp SHALL be indicated in the vector.
* remotely after the proofing session, Mr SHALL be indicated in the vector.
* in-person after the proofing session, Mi SHALL be indicated in the vector.

If the subscriber's account had only one authentication factor bound to it at account creation, and an additional authenticator of a different authentication factor is added after account creation, Ms SHALL be indicated in the vector.

**NOTE: I don't think the phrasing is quite right on adding a second factor yet.**

If a subscriber loses all authentictors of a factor necessary to complete multi-factor authentication, has been identity proofed at IAL2 or IAL3, and consequently undergoes an abbreviated identity proofing process to reestablish authentication factors, Ma SHALL be indicated in the vector.

### Assertion Presentation

If a front-channel presentation mechanism is used, Af SHOULD be indicated in the vector.

If a back-channel presentation mechanism is used, Ab SHOULD be indicated in the vector.

**NOTE: We could build a table to help readers distinguish between values that are required in the vector (SHALLs/depending on implementation) vs. encouraged (SHOULDs/depending on implementation). I can also add in references to A-C as relevant/appropriate so readers can easily find related guidance.**