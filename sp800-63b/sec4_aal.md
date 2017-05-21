<a name="sec4"></a>

## <a name="AAL_SEC4"></a>4. Authenticator Assurance Levels

_This section is normative._

In order to satisfy the requirements of a given AAL, a claimant SHALL be authenticated with at least a given level of strength to be recognized as a subscriber. The result of an authentication process is an identifier that MAY be pseudonymous and that SHALL be used each time that subscriber authenticates to that RP. Subscriber identifiers SHOULD NOT be reused for a different subject but SHOULD be reused when a previously-enrolled subject is re-enrolled by the CSP. Other attributes that identify the subscriber as a unique subject MAY also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in Section 5.

FIPS 140 requirements are satisfied by [[FIPS 140-2]](#FIPS140-2) or newer revisions.

At IAL1, it is possible that attributes are collected and made available by the digital service. Any PII, whether self-asserted or validated, requires multi-factor authentication; therefore agencies SHALL select a minimum of AAL2 when self-asserted PII is made available online.

### 4.1. Authenticator Assurance Level 1

AAL1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

#### 4.1.1. Permitted Authenticator Types

AAL1 permits the use of any of the following authenticator types, which are defined in Section 5:

* Memorized Secret ([Section 5.1.1](#memsecret))
* Look-up Secret ([Section 5.1.2](#lookupsecrets))
* Out-of-Band Devices ([Section 5.1.3](#out-of-band))
* Single-factor One-Time Password (OTP) Device ([Section 5.1.4](#singlefactorOTP))
* Multi-factor OTP Device ([Section 5.1.5](#multifactorOTP))
* Single-factor Cryptographic Software ([Section 5.1.6](#sfcs))
* Single-factor Cryptographic Device ([Section 5.1.7](#sfcd))
* Multi-factor Cryptographic Software ([Section 5.1.8](#mfcs))
* Multi-factor Cryptographic Device ([Section 5.1.9](#mfcd))

#### 4.1.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL1 SHALL use approved cryptography. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise (e.g., by malware) of the user endpoint in which they are running and SHOULD not complete the operation when such a compromise is detected.

Communication between the claimant and verifier (using the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to MitM attacks.

Verifiers operated by government agencies at AAL1 SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1.

#### <a name="aal1reauth"></a>4.1.3. Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL1, reauthentication of the subscriber SHOULD be repeated at least once per 30 days during an extended usage session, regardless of user activity. The session SHOULD be terminated (logged out) when this time limit is reached.

#### 4.1.4. Security Controls

The CSP SHOULD employ appropriately-tailored security controls from the low baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *low* baseline are satisfied.

#### <a name="aal1records"></a> 4.1.5. Records Retention

The CSP shall comply with their respective records retention policies in accordance with applicable laws and regulations. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### 4.2. Authenticator Assurance Level 2

AAL2 provides high confidence that the claimant controls authenticator(s) registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. In order to authenticate at AAL2, claimants SHALL successfully authenticate using both authentication factors. Approved cryptographic techniques are required at AAL2 and above.

#### 4.2.1. Permitted Authenticator Types

At AAL2, it is required to have either a multi-factor authenticator or a combination of two single-factor authenticators. Authenticator requirements are specified in [Section 5](#sec5).

When a multi-factor authenticator is used, any of the following MAY be used:

* Multi-factor OTP Device ([Section 5.1.5](#multifactorOTP))
* Multi-factor Cryptographic Software ([Section 5.1.8](#mfcs))
* Multi-factor Cryptographic Device ([Section 5.1.9](#mfcd))

When a combination of two single-factor authenticators is used, it SHALL include a Memorized Secret authenticator ([Section 5.1.1](#memsecret)) and one possession-based ("something you have") authenticator from the following list:

* Look-up Secret ([Section 5.1.2](#lookupsecrets))
* Out-of-Band Device ([Section 5.1.3](#out-of-band))
* Single-factor OTP Device ([Section 5.1.4](#singlefactorOTP))
* Single-factor Cryptographic Software ([Section 5.1.6](#sfcs))
* Single-factor Cryptographic Device ([Section 5.1.7](#sfcd))

> Note: When biometric authentication implements the requirements in [Section 5.2.3](#biometric_use), the device SHALL be authenticated; a biometric is not recognized as an authenticator type by itself. Therefore, it is unnecessary to use another factor with biometrics because the associated device is the "something you have", which serves as a valid second factor of the authentication. 

#### 4.2.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL2 SHALL use approved cryptography. Authenticators procured by government agencies SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise of the platform in which they are running (e.g., by malware) and SHOULD not complete the operation when such a compromise is detected. At least one authenticator used at AAL2 SHALL be replay resistant as described in Section [5.2.8](#replay). Authentication at AAL2 SHOULD demonstrate authentication intent from at least one authenticator as discussed in Section [5.2.9](#intent).

Communication between the claimant and verifier (the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to MitM attacks.

Verifiers operated by government agencies at AAL2 SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1.

When a device such a smartphone is used in the authentication process, the unlocking of that device (typically done using a PIN or biometric) SHALL NOT be considered one of the authentication factors. This is because it is generally not possible for verifier to know that the device had been locked, nor whether the unlock process met the requirements for the relevant authenticator type.

When a biometric factor is used in authentication at AAL2, the verifier SHOULD make a determination that the biometric sensor and subsequent processing meet the performance requirements stated in Section [5.2.3](#biometric_use).

#### <a name="aal2reauth"></a>4.2.3. Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL2, authentication of the subscriber SHALL be repeated at least once per 12 hours during an extended usage session, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following any period of no more than 30 minutes of session inactivity. The session SHALL be terminated (logged out) when either of these time limits is reached.

Reauthentication of a session that has not yet reached its time limit MAY require only a memorized secret or a biometric in conjunction with the still-valid session secret. The verifier MAY prompt the user to cause activity just before the inactivity timeout, if desired. 

#### 4.2.4. Security Controls

The CSP SHOULD employ appropriately-tailored security controls from the moderate baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *moderate* baseline are satisfied.

#### <a name="aal2records"></a> 4.2.5. Records Retention

CSPs shall comply with their respective records retention policies in accordance with whatever laws and regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### 4.3. Authenticator Assurance Level 3

AAL3 provides very high confidence that the claimant controls authenticator(s) registered to the subscriber. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication SHALL use a hardware-based cryptographic authenticator and an authenticator that provides verifier impersonation resistance; the same device may fulfill both these requirements. In order to authenticate at AAL3, claimants SHALL successfully authenticate using two different authentication factors. 

#### 4.3.1. Permitted Authenticator Types

Authentication Assurance Level 3 requires the use of one of a combination of authenticators satisfying the requirements in Section 4.3. Possible combinations are:

* Multi-factor Cryptographic Device ([Section 5.1.9](#mfcd))
* Single-factor Cryptographic Device ([Section 5.1.7](#sfcd)) used in conjunction with Memorized Secret ([Section 5.1.1](#memsecret))
* Multi-factor OTP device ([Section 5.1.5](#multifactor OTP)) used in conjunction with a Single-factor Cryptographic Device ([Section 5.1.7](#sfcd))(or Software ([Section 5.1.6](#sfcs)) if OTP is hardware)
* Single-factor OTP device (hardware only) ([Section 5.1.4](#singlefactorOTP)) used in conjunction with a Multi-factor Cryptographic Software authenticator ([Section 5.1.8](#mfcs))
* Single-factor OTP device (hardware only) ([Section 5.1.4](#singlefactorOTP)) used in conjunction with a Single-factor Cryptographic Software authenticator ([Section 5.1.6](#sfcs))  and a Memorized Secret ([Section 5.1.1](#memsecret))

#### 4.3.2. Authenticator and Verifier Requirements

Communication between the claimant and verifier SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to MitM attacks. All cryptographic device authenticators used at AAL3 SHALL be verifier impersonation resistant as described in Section [5.2.5](#verifimpers) and SHALL be replay resistant as described in Section [5.2.8](#replay). All authentication and reauthentication processes at AAL3 SHALL demonstrate authentication intent from at least one authenticator as described in Section [5.2.9](#intent).

Multi-factor authenticators used at AAL3 SHALL be hardware cryptographic modules validated at [FIPS 140](#FIPS140-2) Level 2 or higher overall with at least [FIPS 140](#FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL3 SHALL be validated at [FIPS 140](#FIPS140-2) Level 1 or higher overall with at least [FIPS 140](#FIPS140-2) Level 3 physical security.

Verifiers at AAL3 SHALL be validated at [FIPS 140](#FIPS140-2) Level 1 or higher.

Verifiers at AAL3 SHALL be verifier compromise resistant as described in [Section 5.2.7](#verifier-secrets) with respect to at least one authentication factor.

When a device such a smartphone is used in the authentication process (presuming that the device is able to meet the requirements above), the unlocking of that device (typically done using a PIN or biometric) SHALL NOT be considered to satisfy one of the authentication factors. This is because it is generally not possible for verifier to know that the device had been locked, nor whether the unlock process met the requirements for the relevant authenticator type.

When a biometric factor is used in authentication at AAL3, the verifier SHALL make a determination that the biometric sensor and subsequent processing meet the performance requirements stated in Section [5.2.3](#biometric_use).

#### <a name="aal3reauth"></a>4.3.3. Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL3, authentication of the subscriber SHALL be repeated at least once per 12 hours during an extended usage session, regardless of user activity, as described in [Section 7.2](#sessionreauthn). Reauthentication of the subscriber SHALL be repeated following any period of no more than 15 minutes of session inactivity. Reauthentication SHALL use both authentication factors. The verifier MAY prompt the user to cause activity just before the inactivity timeout. The session SHALL be terminated (logged out) when either of these time limits is reached.

#### 4.3.4. Security Controls

The CSP SHOULD employ appropriately-tailored security controls from the high baseline of security controls defined in [[SP 800-53]](#SP800-53) or an equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *high* baseline are satisfied.

#### <a name="aal3records"></a> 4.3.5. Records Retention

The CSP SHALL comply with their respective records retention policies in accordance with whatever laws and regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### <a name="aal_privacy"></a>4.4. Privacy Requirements

The CSP SHALL employ appropriately-tailored privacy controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard.

CSPs SHALL NOT use or disclose information about subscribers for any purpose other than conducting authentication or to comply with law or legal process, unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs MAY NOT make consent a condition of the service. Care SHALL be taken to ensure that use of such information is limited to its original purpose for collection. If the use of such information does not fall within uses related to authentication or to comply with law or legal process, the CSP SHALL provide notice and obtain consent from the subscriber.  This notice SHOULD follow the same principles as described in *Notice and Consent* in [[SP 800-63A Section 8.2]](sp800-63a.html#consent) and SHOULD not be rolled up into a legalistic privacy policy or general terms and conditions. Rather, if there are uses outside the bounds of these explicit purposes, the subscriber SHOULD be provided with a meaningful way to understand the purpose for additional uses, and the opportunity to accept or decline.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the authentication service:

1. The agency SHALL consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis to determine whether the collection of Personally Identifiable Information (PII) to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[Privacy Act]](#PrivacyAct). 
* The agency SHALL publish a System of Records Notice (SORN) to cover such collections, as applicable. 
* The agency SHALL consult with their SAOP to conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](#E-Gov). 
* The agency SHALL publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

### 4.5. Summary of Requirements

*(Informative; refer to preceding sections for normative requirements)*

[Table 4-1](#63bSec4-Table1) summarizes the requirements for each of the AALs:

<a name="63bSec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1.  AAL Summary of Requirements**

</div>

Requirement | AAL1 | AAL2 | AAL3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret;<br />Look-up Secret;<br />Out of Band;<br />SF OTP Device;<br />MF OTP Device;<br />SF Crypto Software;<br />SF Crypto Device;<br />MF Crypto Software;<br />MF Crypto Device<br /> | MF OTP Device;<br />MF Crypto Software;<br />MF Crypto Device;<br />or Memorized Secret plus:<br />&nbsp;&bull;&nbsp;Look-up Secret<br />&nbsp;&bull;&nbsp;Out of Band<br />&nbsp;&bull;&nbsp;SF OTP Device<br />&nbsp;&bull;&nbsp;SF Crypto Software<br />&nbsp;&bull;&nbsp;SF Crypto Device<br /> | MF Crypto Device;<br />SF Crypto Device plus &nbsp;&nbsp;Memorized Secret;<br />SF OTP Device plus MF Crypto Device or Software;<br />SF OTP Device plus SF Crypto Software plus Memorized Secret
**FIPS 140 verification** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators)<br />Level 1 overall (verifiers and SF Crypto Devices)<br />Level 3 physical security (all authenticators)
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; MAY use one authentication factor | 12 hours or 15 minutes inactivity; SHALL use both authentication factors
**Security controls**|[[SP 800-53]](#SP800-53) Low Baseline (or equivalent)|[[SP 800-53]](#SP800-53) Moderate Baseline (or equivalent)|[[SP 800-53]](#SP800-53) High Baseline (or equivalent)
**MitM resistance** | Required | Required | Required |
**Verifier impersonation resistance** | Not required | Not required | Required |
**Verifier compromise resistance** | Not required | Not required | Required |
**Replay resistance** | Not required | Required | Required |
**Authentication intent** | Not required | Recommended | Required |




