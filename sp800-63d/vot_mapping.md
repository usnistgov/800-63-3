<a name="vectors-of-trust-mapping"></a>

<div class="breaker"></div>

## Mapping Assurance Levels to Vectors of Trust
_This section is normative._

Vectors of Trust (VoT) is a standard for expressing information about an authentication transaction from an IdP to an RP. This information is split into several orthogonal component categories, much in the same way that the assurances defined in 800-63 are split into different xAL categories.

### Trustmark

The trustmark URI for these definitions is [[ URI for this document ]].

### xAL to VoT Components

This document uses three categories defined in VoT: Identity Proofing (P), Primary Credential Usage (C), and Assertion Presentation (A). These categories correspond to the Identity Assurance Level (IAL), Authenticator Assurance Level (AAL), and Federation Assurance Level (FAL), respectively.

This document does not use the Primary Credential Management (M) category defined in VoT.

This document does not define any additional component categories. Any additional categories SHALL NOT be used.

## Component Values

This document does not use any of the existing values in VoT but instead defines new component values here in accordance with Section 8 of VoT.

### IAL to VOT Component Values

IAL maps into the VoT component P using a numeric identifier. Only one numeric identifier SHALL be used.

|IAL|Component Value|
|:----:|:--:|
|IAL1 (with no attributes)|P0|
|IAL1|P1|
|IAL2|P2|
|IAL3|P3|

In addition, the type of proofing used MAY be indicated using an alphabetic identifier. Multiple alphabetic identifiers MAY be used simultaneously.

|Proofing method|Component Value|
|In-person|Pp|
|Remote|Pr|

### AAL to VOT Component Values

AAL maps into the VoT component C using a numeric identifier. Only one numeric identifier SHALL be used.

|AAL|Component Value|
|:----:|:--:|
|AAL1|C1|
|AAL2|C2|
|AAL3|C3|

In addition, the type of authenticator used SHALL be indicated using an alphabetic identifier. Multiple alphabetic identifiers MAY be used simultaneously.

|Authenticator|Component Value|
|Memorized Secret|Cp|
|Look-up Secret|Cu|
|Out-of-band Device|Co|
|Out-of-band over SMS|Cs|
|Single-factor OTP|Ca|
|Multi-factor OTP|Cb|
|Single-factor Cryptographic Software|Cc|
|Single-factor Cryptographic Device|Cd|
|Multi-factor Cryptographic Software|Ce|
|Multi-factor Cryptographic Device|Cf|


### FAL to VOT Component Values

FAL maps into the VoT component A using a numeric identifier. Only one numeric identifier SHALL be used.

|FAL|Component Value|
|:----:|:--:|
|FAL1|A1|
|FAL2|A2|
|FAL3|A3|

In addition, the presentation mechanism MAP be indicated using an alphabetic identifier. Only one alphabetic identifier SHALL be used.

|Presentation|Component Value|
|Front channel|Af|
|Back channel|Ab|
