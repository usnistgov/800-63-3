<a name="vectors-of-trust-mapping"></a>

<div class="breaker"></div>

## Mapping SP 800-63 to Vectors of Trust
_This section is normative._

Vectors of Trust (VoT) [[VoT]](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07) is a standard for expressing information about an authentication transaction from an IdP to an RP. This information is split into several orthogonal component categories, similar to the way that the assurance levels defined in SP 800-63 are split into different xAL categories.

This document uses terms as defined in [SP 800-63-3 Appendix A](sp800-63-3.html#def-and-acr). Some definitions differ from those in VoT. Notably, the term "authenticator" herein has the same meaning as "credential" in VoT.

### Trustmark

The trustmark URI for these definitions is [[ URI for this document ]].

### VoT Components

This document uses the four components defined in VoT: Identity Proofing (P), Primary Credential Usage (C), Primary Credential Management (M), and Assertion Presentation (A). This document does not define any additional component categories.

The VoT [component P](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07#section-2.1) corresponds to identity proofing requirements and recommendations found in [SP 800-63A](sp800-63a.html). As such, the document maps SP 800-63's Identity Assurance Level (IAL) and identity proofing characteristics into VoT's P.

The VoT [component C](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07#section-2.2) corresponds to authentication requirements and recommendations found in [SP 800-63B](sp800-63b.html). As such, this document maps SP 800-63's Authenticator Assurance Level (AAL), authenticator types, and authentication characteristics into VoT's C.

The VoT [component M](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07#section-2.3) corresponds to authenticator lifecycle management requirements and recommendations found in [SP 800-63B Section 6](sp800-63b.html#sec6). As such, this document maps SP 800-63's authenticator lifecycle management characteristics into VoT's M.

The VoT [component A](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07#section-2.4) corresponds to federation requirements and recommendations found in [SP 800-63C](sp800-63c.html). As such, this document maps SP 800-63's Federation Assurance Level (FAL) and assertion presentation into VoT's A.

**Table: 800-63 General Mapping to VoT Components**

|VoT Component|SP 800-63 xAL|SP 800-63 Requirements and Recommendations|
|:----:|:--:|:--:|
|P|IAL|identity proofing characteristics|
|C|AAL|authenticator types and authentication characteristics|
|M|-|authenticator lifecycle management characteristics|
|A|FAL|assertion presentation|

## Component Values

This document defines new component values in accordance with [VoT Section 2](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07#section-2).

The component values for IAL, AAL, and FAL are expressed with numeric identifiers. Only one numeric identifier SHALL be used for each xAL. The implemented IAL, AAL, and/or FAL SHALL be indicated in the vector. Other digital identity information (i.e., identity proofing characteristics, authenticator type(s) used, authentication characteristics, authenticator lifecycle management characteristics, and assertion presentation values) are expressed with alphabetic identifiers. Multiple alphabetic identifiers MAY be used simultaneously. Some alphabetically-expressed values SHALL be indicated in the vector if implementation matches the uses described in the following sections; otherwise, these values MAY be indicated in the vector.

Identity proofing characteristics, authenticator type(s) used, authentication characteristics, and assertion presentation values SHOULD NOT be indicated when they demonstrate the implementation of approaches required under the xAL indicated in the vector. Such approaches are assumed to be implemented per the xAL's requirements. Approaches, as described in the "Use" sections below, that are required under a specific xAL, and SHOULD NOT be indicated in the vector to avoid redundancy, are noted in the "Implied by xAL" column.

**Example:** C2.Cv could be asserted if implementing AAL2 and an authenticator is used that provides verifier impersonation resistance, since verifier impersonation resistance is not required under AAL2.

> Note: Any discrepancies in the assessed and implemented assurance level SHOULD be documented in a digital identity acceptance statement, per [SP 800-63-3 Section 5.5](sp800-63-3.html#daps).

Any additional component categories SHALL NOT be used.

### Identity Proofing

This section defines a series of P component values dervied from [SP 800-63A](sp800-63a.html).

#### IAL Values

|IAL|Component Value|
|:----:|:--:|
|IAL1 (with no attributes)|P0|
|IAL1|P1|
|IAL2|P2|
|IAL3|P3|

#### Identity Proofing Characteristic Values

|Identity Proofing Characteristic|Component Value|Implied in xAL|
|:----:|:--:|:--:|
|In-person Proofing|Pi|IAL3|
|Unsupervised Remote Proofing|Pr|-|
|Knowledge-based Verification (KBV)|Pk|-|
|Address Confirmation with Postal Address|Pa|-|
|Trusted Referee|Pt|-|

>Note: Any credential service provider performing identity proofing at IAL2 or IAL3 MUST conduct a privacy risk assessment per [SP 800-63A Section 4.2](sp800-63a.html#genProofReqs). Trusted referee policy and procedures MUST be documented per [SP 800-63A Section 5.3.4](sp800-63a.html#trustref).

#### Use of Identity Proofing Values

If KBV is used for identity verification, Pk SHALL be indicated in the vector.

**Example:** P2.Pk would be asserted if implementing IAL2 and using KBV for identity verification.

If using a trusted referee acting on behalf of the applicant in the identity proofing process, Pt SHALL be indicated in the vector.

If the subscriber is identity proofed in-person, Pi SHOULD be indicated in the vector.

If the subscriber is identity proofed using an unsupervised remote process, Pr SHOULD be indicated in the vector.

If confirming an applicant's address by sending an enrollment code to a postal address, Pa SHOULD be indicated in the vector.

### Authentication Events

This section defines a series of C component values dervied from [SP 800-63B](sp800-63b.html).

#### AAL Values

|AAL|Component Value|
|:----:|:--:|
|AAL1|C1|
|AAL2|C2|
|AAL3|C3|

#### Authenticator Type Values

|Authenticator Type|Component Value|Implied in xAL|
|:----:|:--:|:--:|
|Memorized Secret|Cc|-|
|Look-up Secret|Cu|-|
|Out-of-band Device|Co|-|
|Single-factor OTP|Ca|-|
|Multi-factor OTP|Cb|-|
|Single-factor Cryptographic Software|Cd|-|
|Single-factor Cryptographic Device|Ce|-|
|Multi-factor Cryptographic Software|Cf|-|
|Multi-factor Cryptographic Device|Cg|-|
|Restricted Authenticator|Cr|-|

#### Authentication Characteristic Values

|Authentication Characteristic|Component Value|Implied in xAL|
|:----:|:--:|:--:|
|FIPS 140 Validation|Ci|AAL3|
|Verifier Impersonation Resistance|Cv|AAL3|
|Verifier Compromise Resistance|Cs|AAL3|
|Authentication Intent|Cn|AAL3|
|Presentation Attack Detection (PAD)|Ck|-|
|Biometric comparison performed centrally|Ct|-|

**NOTE: Should we add a vector value for FMR?**

>Note: Some authentication approaches described in Table XX are not applicable for all three AALs.

#### Use of Authentication Event Values

The authenticator type(s) used SHALL be indicated in the vector, unless implementing AAL3 and authentication is achieved using one of the following two options.

* Multi-Factor Cryptographic Device; OR
* Single-Factor Cryptographic Device used in conjunction with Memorized Secret

If the user authenticates using a restricted authenticator, Cr and the value representing the authenticator used SHALL be indicated in the vector.

**Example:** Cr.Co would be asserted if the user authenticates using a secret sent via SMS to an out-of-band device.

If implementing AAL1 or AAL2, and:

* the user authenticates with an authenticator that provides verifier impersonation resistance, Cv SHOULD be indicated in the vector.
* the user authenticates with an authenticator that provides verifier compromise resistance, Cs SHOULD be indicated in the vector.
* authentication intent from at least one authenticator is demonstrated, Cn SHOULD be indicated in the vector.
* for non-government agency authenticators and verifiers, authenticator(s) or verifier(s) are validated to meet the requirements of FIPS 140 Level 1, Ci SHOULD be indicated in the vector.

If the user authenticates using a biometric authenticator, and:

* biometric comparison is performed centrally (not locally on the claimant's device), Ct SHALL be indicated in the vector.
* the biometric system implements PAD, Ck SHOULD be indicated in the vector.

### Authenticator Lifecycle Management

This section defines a set of M component values dervied from [SP 800-63B Section 6](sp800-63b.html#sec6). The values in this section differ from others in this document because they pertain to the ongoing policy for the account instead of to a specific authentication event.

#### Authenticator Lifecycle Management Characteristic Values

|Authenticator Lifecycle Management Characteristic|Component Value|Implied in xAL|
|:----:|:--:|:--:|
|Authenticator issued/bound during proofing session|Mp|-|
|Authenticator issued/bound after proofing session (remote)|Mr|-|
|Authenticator issued/bound after proofing session (in-person)|Mi|-|
|Second factor bound to a single-factor account|Ms|-|
|Authentication factors reestablished (account recovery) using abbreviated proofing process|Ma|-|

#### Use of Authenticator Lifecycle Management Values

If the authenticator(s) is/are bound/issued:

* during a single proofing session, Mp SHALL be indicated in the vector.
* remotely after the proofing session, Mr SHALL be indicated in the vector.
* in-person after the proofing session, Mi SHALL be indicated in the vector.

If the subscriber's account had only one authentication factor bound to it at account creation, and an additional authenticator of a different authentication factor is added after account creation, Ms SHALL be indicated in the vector.

If the following conditions are met, Ma SHALL be indicated in the vector.

* The subscriber has been identity proofed at IAL2 or IAL3.
* The subscriber loses all authenticators of a factor necessary to complete multi-factor authentication. 
* The subsriber consequently undergoes an abbreviated identity proofing process to reestablish authentication factors.

### Federation and Assertions

This section defines a series of A component values dervied from [SP 800-63C](sp800-63c.html).

#### FAL Values

|FAL|Component Value|
|:----:|:--:|
|FAL1|A1|
|FAL2|A2|
|FAL3|A3|

#### Assertion Presentation Values

|Assertion Presentation|Component Value|Implied in xAL|
|:----:|:--:|:--:|
|Front channel|Af|-|
|Back channel|Ab|-|

#### Use of Assertion Presentation Values

If a front-channel presentation mechanism is used, Af SHOULD be indicated in the vector.

If a back-channel presentation mechanism is used, Ab SHOULD be indicated in the vector.

### Summary

The table below describes the values that are required to be indicated when implementation matches the uses described in the above "Use" sections to conform to this publication.

|Component Value|Indication in Vector Required*|
|:----:|:--:|
|P0|X|
|P1|X|
|P2|X|
|P3|X|
|Pi|-|
|Pr|-|
|Pk|X|
|Pa|-|
|Pt|X|
|C1|X|
|C2|X|
|C3|X|
|Cc|X|
|Cu|X|
|Co|X|
|Ca|X|
|Cb|X|
|Cd|X|
|Ce|X|
|Cf|X|
|Cg|X|
|Cr|X|
|Ci|-|
|Cv|-|
|Cs|-|
|Cn|-|
|Ck|X|
|Ct|-|
|Mp|X|
|Mr|X|
|Mi|X|
|Ms|X|
|Ma|X|
|A1|X|
|A2|X|
|A3|X|
|Af|-|
|Ab|-|

*This does mean that these values must always be indicated; these values are only required to be indicated when implementation matches the use described in this document's "Use" sections and when the value represents the implemented xAL.

## References

[VoT] Vectors of Trust, December 8, 2018, available at: [https://tools.ietf.org/html/draft-richer-vectors-of-trust-07](https://tools.ietf.org/html/draft-richer-vectors-of-trust-07)