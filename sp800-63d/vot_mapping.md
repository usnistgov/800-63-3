<a name="vectors-of-trust-mapping"></a>

<div class="breaker"></div>

## Mapping Assurance Levels to Vectors of Trust
_This section is normative._

Vectors of Trust (VoT) is a standard for expressing information about an authentication transaction from an IdP to an RP. This information is split into several orthogonal component categories, much in the same way that the assurance levels defined in 800-63 are split into different xAL categories.

### Trustmark

The trustmark URI for these definitions is [[ URI for this document ]].

### VoT Components

This document uses the four components defined in VoT: Identity Proofing (P), Primary Credential Usage (C), Primary Credential Management (M), and Assertion Presentation (A).

The VoT components P, C, and A correspond to 800-63's Identity Assurance Level (IAL), Authenticator Assurance Level (AAL), and Federation Assurance Level (FAL), respectively. While M does not correspond directly to an 800-63 assurance level category, this document defines a set of M values derived from requirements and recommendations in 800-63. 

This document uses terms as defined in 800-63-3. Some definitions differ from those in VoT. Notably, the term "authenticator" herein has the same meaning as "credential" in VoT.

This document does not define any additional component categories. Any additional categories SHALL NOT be used.

## Component Values

This document does not use any of the existing values in VoT but instead defines new component values in accordance with Section 8 of VoT.

### Identity Proofing

#### IAL to VoT

IAL maps into the VoT component P using a numeric identifier. The implemented IAL component value SHALL be asserted. Only one numeric identifier SHALL be used. 

|IAL|Component Value|
|:----:|:--:|
|IAL1 (with no attributes)|P0|
|IAL1|P1|
|IAL2|P2|
|IAL3|P3|

#### Identity Proofing Characteristics

In addition, identity proofing characteristics MAY be indicated using an alphabetic identifier. Multiple alphabetic identifiers MAY be used simultaneously. Identity proofing methods or approaches that are required for the asserted IAL SHOULD NOT be asserted.

|Identity Proofing Method or Approach|Component Value|
|:----:|:--:|
|In-person|Pi|
|Remote|Pr|
|Knowledge-based Verification (KBV)|Pk|
|Address Confirmation with Postal Address|Pa|
|Trusted Referee|Pt|
|Implemented IAL differs from assessed IAL|Px|

>Note: Any credential service provider performing identity proofing at IAL2 or IAL3 MUST conduct a privacy risk assessment. Trusted referee policy and procedures MUST be documented per SP 800-63A Section 5.3.4.
If Px is asserted, the component value for the assessed IAL MUST also be asserted (e.g., “P2.Px”). The discrepancy in assessed and implemented assurance level SHOULD be documented in a digital identity acceptance statement, per SP 800-63-3 Section 5.5.

### Authenticator or Credential Usage

#### AAL to VoT

AAL maps into the VoT component C using a numeric identifier. The implemented AAL component value SHALL be asserted. Only one numeric identifier SHALL be used. 

|AAL|Component Value|
|:----:|:--:|
|AAL1|C1|
|AAL2|C2|
|AAL3|C3|

#### Authenticator Types

The authenticator type(s) used MAY be indicated using an alphabetic identifier. Multiple aphabetic identifiers MAY be used simultaneously.

|Authenticator Type|Component Value|
|:----:|:--:|
|Memorized Secret|Cp|
|Look-up Secret|Cu|
|Out-of-band Device|Co|
|Single-factor OTP|Ca|
|Multi-factor OTP|Cb|
|Single-factor Cryptographic Software|Cc|
|Single-factor Cryptographic Device|Cd|
|Multi-factor Cryptographic Software|Ce|
|Multi-factor Cryptographic Device|Cf|
|Restricted Authenticator|Cr|

#### Authentication Characteristics

|Authentication Feature|Component Value|
|:----:|:--:|
|FIPS 140 Validation|Ci|
|Man-in-the-middle Attack Resistance|Cm|
|Verifier Impersonation Resistance|Cv|
|Verifier Compromise Resistance|Cs|
|Authentication Intent|Cn|
|Implemented AAL differs from assessed AAL|Cx|
|Presentation Attack Detection (PAD)|Ck|
|Biometric comparison performed centrally|Ct|

>Note: Some authentication approaches described in Table XX are not applicable for all three AALs.If Cx is asserted, the component value for the assessed AAL MUST also be asserted (e.g., “C2.Cx”). The discrepancy in assessed and implemented assurance level SHOULD be documented in a digital identity acceptance statement, per SP 800-63-3 Section 5.5.


### Assertion Presentation

#### FAL to VoT

FAL maps into the VoT component A using a numeric identifier. Only one numeric identifier SHALL be used. 

|FAL|Component Value|
|:----:|:--:|
|FAL1|A1|
|FAL2|A2|
|FAL3|A3|

#### Assertion Presentation

In addition, the presentation mechanism MAY be indicated using an alphabetic identifier. Multiple aphabetic identifiers MAY be used simultaneously.

|Presentation|Component Value|
|:----:|:--:|
|Front channel|Af|
|Back channel|Ab|
|Implemented FAL differs from assessed FAL|Ax|

If Ax is asserted, the component value for the assessed FAL MUST also be asserted (e.g., “A2.Ax”). The discrepancy in assessed and implemented assurance level SHOULD be documented in a digital identity acceptance statement, per SP 800-63-3 Section 5.5.

### Credential or Authenticator Management to VoT

800-63 authenticator management maps into the VoT component M using an alphabetic identifier. Authenticator management method MAY be indicated using an alphabetic identifier. Multiple alphabetic identifiers MAY be used simultaneously.

|Credential Management Method|Component Value|
|:----:|:--:|
|Credential issued/bound during proofing session|Mp|
|Credential issued/bound after proofing session (remote)|Mr|
|Credential issued/bound after proofing session (in-person)|Mi|
|Second factor bound to a single-factor account|Ms|
|Authentication factors reestablished (account recovery) using full proofing process|Ma|
|Authentication factors reestablished (account recovery) using abbreviated proofing process|Mb|