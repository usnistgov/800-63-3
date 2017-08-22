<a name="sec4"></a>

## <a name="AAL_SEC4"></a>4 Authenticator Assurance Levels

_This section contains both normative and informative material._

To satisfy the requirements of a given AAL, a claimant SHALL be authenticated with at least a given level of strength to be recognized as a subscriber. The result of an authentication process is an identifier that SHALL be used each time that subscriber authenticates to that RP. The identifier MAY be pseudonymous. Subscriber identifiers SHOULD NOT be reused for a different subject but SHOULD be reused when a previously-enrolled subject is re-enrolled by the CSP. Other attributes that identify the subscriber as a unique subject MAY also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in Section 5.

See [SP 800-63](sp800-63-3.html) Section 6.2 for details on how to choose the most appropriate AAL.

FIPS 140 requirements are satisfied by [FIPS 140-2](#FIPS140-2) or newer revisions.

At IAL1, it is possible that attributes are collected and made available by the digital identity service. Any PII or other personal information — whether self-asserted or validated — requires multi-factor authentication. Therefore, agencies SHALL select a minimum of AAL2 when self-asserted PII or other personal information is made available online.

### 4.1 Authenticator Assurance Level 1

*This section is normative.*

AAL1 provides some assurance that the claimant controls an authenticator bound to the subscriber's account. AAL1 requires either single-factor or multi-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

#### 4.1.1 Permitted Authenticator Types

AAL1 authentication SHALL occur by the use of any of the following authenticator types, which are defined in [Section 5](#sec5):

* Memorized Secret ([Section 5.1.1](#memsecret))
* Look-Up Secret ([Section 5.1.2](#lookupsecrets))
* Out-of-Band Devices ([Section 5.1.3](#out-of-band))
* Single-Factor One-Time Password (OTP) Device ([Section 5.1.4](#singlefactorOTP))
* Multi-Factor OTP Device ([Section 5.1.5](#multifactorOTP))
* Single-Factor Cryptographic Software ([Section 5.1.6](#sfcs))
* Single-Factor Cryptographic Device ([Section 5.1.7](#sfcd))
* Multi-Factor Cryptographic Software ([Section 5.1.8](#mfcs))
* Multi-Factor Cryptographic Device ([Section 5.1.9](#mfcd))

#### <a name="aal1req"></a>4.1.2 Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL1 SHALL use approved cryptography. Software-based authenticators that operate within the context of an operating system MAY, where applicable, attempt to detect compromise (e.g., by malware) of the user endpoint in which they are running and SHOULD NOT complete the operation when such a compromise is detected.

Communication between the claimant and verifier (using the primary channel in the case of an out-of-band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle (MitM) attacks.

Verifiers operated by government agencies at AAL1 SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1.

#### <a name="aal1reauth"></a>4.1.3 Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL1, reauthentication of the subscriber SHOULD be repeated at least once per 30 days during an extended usage session, regardless of user activity. The session SHOULD be terminated (i.e., logged out) when this time limit is reached.

#### 4.1.4 Security Controls

The CSP SHALL employ appropriately-tailored security controls from the *low* baseline of security controls defined in [SP 800-53](#SP800-53) or equivalent federal (e.g. [FEDRAMP](#FEDRAMP)) or industry standard. The CSP SHALL ensure that the minimum assurance-related controls for *low-impact* systems, or equivalent, are satisfied.

#### <a name="aal1records"></a> 4.1.5 Records Retention Policy

The CSP shall comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any National Archives and Records Administration (NARA) records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP SHALL conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### 4.2 Authenticator Assurance Level 2

*This section is normative.*

AAL2 provides high confidence that the claimant controls authenticator(s) bound to the subscriber's account. Proof of possession and control of two distinct authentication factors is required through secure authentication protocol(s). Approved cryptographic techniques are required at AAL2 and above.

#### <a name="aal2types"></a>4.2.1 Permitted Authenticator Types

At AAL2, authentication SHALL occur by the use of either a multi-factor authenticator or a combination of two single-factor authenticators. A multi-factor authenticator requires two factors to execute a single authentication event, such as a cryptographically-secure device with an integrated biometric sensor that is required to activate the device. Authenticator requirements are specified in [Section 5](#sec5).

When a multi-factor authenticator is used, any of the following MAY be used:

* Multi-Factor OTP Device ([Section 5.1.5](#multifactorOTP))
* Multi-Factor Cryptographic Software ([Section 5.1.8](#mfcs))
* Multi-Factor Cryptographic Device ([Section 5.1.9](#mfcd))

When a combination of two single-factor authenticators is used, it SHALL include a Memorized Secret authenticator ([Section 5.1.1](#memsecret)) and one possession-based (i.e., "something you have") authenticator from the following list:

* Look-Up Secret ([Section 5.1.2](#lookupsecrets))
* Out-of-Band Device ([Section 5.1.3](#out-of-band))
* Single-Factor OTP Device ([Section 5.1.4](#singlefactorOTP))
* Single-Factor Cryptographic Software ([Section 5.1.6](#sfcs))
* Single-Factor Cryptographic Device ([Section 5.1.7](#sfcd))

> Note: When biometric authentication meets the requirements in [Section 5.2.3](#biometric_use), the device has to be authenticated in addition to the biometric &mdash; a biometric is recognized as a factor, but not recognized as an authenticator by itself. Therefore, when conducting authentication with a biometric, it is unnecessary to use two authenticators because the associated device serves as "something you have," while the biometric serves as "something you are."

#### <a name="aal2req"></a>4.2.2 Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL2 SHALL use approved cryptography. Authenticators procured by government agencies SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1. Software-based authenticators that operate within the context of an operating system MAY, where applicable, attempt to detect compromise of the platform in which they are running (e.g., by malware) and SHOULD NOT complete the operation when such a compromise is detected. At least one authenticator used at AAL2 SHALL be replay resistant as described in [Section 5.2.8](#replay). Authentication at AAL2 SHOULD demonstrate authentication intent from at least one authenticator as discussed in [Section 5.2.9](#intent).

Communication between the claimant and verifier (the primary channel in the case of an out-of-band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to MitM attacks.

Verifiers operated by government agencies at AAL2 SHALL be validated to meet the requirements of [FIPS 140](#FIPS140-2) Level 1.

When a device such a smartphone is used in the authentication process, the unlocking of that device (typically done using a PIN or biometric) SHALL NOT be considered one of the authentication factors. Generally, it is not possible for a verifier to know that the device had been locked or if the unlock process met the requirements for the relevant authenticator type.

When a biometric factor is used in authentication at AAL2, the performance requirements stated in [Section 5.2.3](#biometric_use) SHALL be met, and the verifier SHOULD make a determination that the biometric sensor and subsequent processing meet these requirements.

#### <a name="aal2reauth"></a>4.2.3 Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL2, authentication of the subscriber SHALL be repeated at least once per 12 hours during an extended usage session, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following any period of inactivity lasting 30 minutes or longer. The session SHALL be terminated (i.e., logged out) when either of these time limits is reached.

Reauthentication of a session that has not yet reached its time limit MAY require only a memorized secret or a biometric in conjunction with the still-valid session secret. The verifier MAY prompt the user to cause activity just before the inactivity timeout.

#### 4.2.4 Security Controls

The CSP SHALL employ appropriately-tailored security controls from the *moderate* baseline of security controls defined in [SP 800-53](#SP800-53) or equivalent federal (e.g., [FEDRAMP](#FEDRAMP)) or industry standard. The CSP SHALL ensure that the minimum assurance-related controls for *moderate-impact* systems or equivalent are satisfied.

#### <a name="aal2records"></a> 4.2.5 Records Retention Policy

The CSP shall comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP SHALL conduct a risk management process, including assessments of privacy and security risks to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### 4.3 Authenticator Assurance Level 3

*This section is normative.*

AAL3 provides very high confidence that the claimant controls authenticator(s) bound to the subscriber's account. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 authentication SHALL use a hardware-based authenticator and an authenticator that provides verifier impersonation resistance — the same device MAY fulfill both these requirements. In order to authenticate at AAL3, claimants SHALL prove possession and control of two distinct authentication factors through secure authentication protocol(s). Approved cryptographic techniques are required.

#### <a name="aal3types"></a>4.3.1 Permitted Authenticator Types

AAL3 authentication SHALL occur by the use of one of a combination of authenticators satisfying the requirements in Section 4.3. Possible combinations are:

* Multi-Factor Cryptographic Device ([Section 5.1.9](#mfcd))
* Single-Factor Cryptographic Device ([Section 5.1.7](#sfcd)) used in conjunction with Memorized Secret ([Section 5.1.1](#memsecret))
* Multi-Factor OTP device (software or hardware) ([Section 5.1.5](#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Device ([Section 5.1.7](#sfcd))
* Multi-Factor OTP device (hardware only) ([Section 5.1.5](#multifactorOTP)) used in conjunction with a Single-Factor Cryptographic Software ([Section 5.1.6](#sfcs))
* Single-Factor OTP device (hardware only) ([Section 5.1.4](#singlefactorOTP)) used in conjunction with a Multi-Factor Cryptographic Software Authenticator ([Section 5.1.8](#mfcs))
* Single-Factor OTP device (hardware only) ([Section 5.1.4](#singlefactorOTP)) used in conjunction with a Single-Factor Cryptographic Software Authenticator ([Section 5.1.6](#sfcs)) and a Memorized Secret ([Section 5.1.1](#memsecret))

#### <a name="aal3req"></a>4.3.2 Authenticator and Verifier Requirements

Communication between the claimant and verifier SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to MitM attacks. All cryptographic device authenticators used at AAL3 SHALL be verifier impersonation resistant as described in Section [5.2.5](#verifimpers) and SHALL be replay resistant as described in Section [5.2.8](#replay). All authentication and reauthentication processes at AAL3 SHALL demonstrate authentication intent from at least one authenticator as described in [Section 5.2.9](#intent).

Multi-factor authenticators used at AAL3 SHALL be hardware cryptographic modules validated at [FIPS 140](#FIPS140-2) Level 2 or higher overall with at least [FIPS 140](#FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL3 SHALL be validated at [FIPS 140](#FIPS140-2) Level 1 or higher overall with at least [FIPS 140](#FIPS140-2) Level 3 physical security.

Verifiers at AAL3 SHALL be validated at [FIPS 140](#FIPS140-2) Level 1 or higher.

Verifiers at AAL3 SHALL be verifier compromise resistant as described in [Section 5.2.7](#verifier-secrets) with respect to at least one authentication factor.

Hardware-based authenticators and verifiers at AAL3 SHOULD resist relevant side-channel (e.g., timing and power-consumption analysis) attacks. Relevant side-channel attacks SHALL be determined by a risk assessment performed by the CSP.

When a device such a smartphone is used in the authentication process — presuming that the device is able to meet the requirements above — the unlocking of that device SHALL NOT be considered to satisfy one of the authentication factors. This is because it is generally not possible for verifier to know that the device had been locked nor whether the unlock process met the requirements for the relevant authenticator type.

When a biometric factor is used in authentication at AAL3, the verifier SHALL make a determination that the biometric sensor and subsequent processing meet the performance requirements stated in [Section 5.2.3](#biometric_use).

#### <a name="aal3reauth"></a>4.3.3 Reauthentication

Periodic reauthentication of subscriber sessions SHALL be performed as described in [Section 7.2](#sessionreauthn). At AAL3, authentication of the subscriber SHALL be repeated at least once per 12 hours during an extended usage session, regardless of user activity, as described in [Section 7.2](#sessionreauthn). Reauthentication of the subscriber SHALL be repeated following any period of inactivity lasting 15 minutes or longer. Reauthentication SHALL use both authentication factors. The session SHALL be terminated (i.e., logged out) when either of these time limits is reached. The verifier MAY prompt the user to cause activity just before the inactivity timeout.

#### 4.3.4 Security Controls

The CSP SHALL employ appropriately-tailored security controls from the *high* baseline of security controls defined in [SP 800-53](#SP800-53) or an equivalent federal (e.g., [FEDRAMP](#FEDRAMP)) or industry standard. The CSP SHALL ensure that the minimum assurance-related controls for *high-impact* systems or equivalent are satisfied.

#### <a name="aal3records"></a> 4.3.5 Records Retention Policy

The CSP shall comply with its respective records retention policies in accordance with applicable laws, regulations, and policies, including any NARA records retention schedules that may apply. If the CSP opts to retain records in the absence of any mandatory requirements, the CSP SHALL conduct a risk management process, including assessments of privacy and security risks, to determine how long records should be retained and SHALL inform the subscriber of that retention policy.

### <a name="aal_privacy"></a>4.4 Privacy Requirements

The CSP SHALL employ appropriately-tailored privacy controls defined in [SP 800-53](#SP800-53) or equivalent industry standard.

CSPs SHALL NOT use or disclose information about subscribers for any purpose other than conducting authentication, related fraud mitigation, or to comply with law or legal process, unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs SHALL NOT make consent a condition of the service. Care SHALL be taken to ensure that use of such information is limited to its original purpose for collection. If the use of such information does not fall within uses related to authentication or to comply with law or legal process, the CSP SHALL provide notice and obtain consent from the subscriber. This notice SHOULD follow the same principles as described in *Notice and Consent* in [SP 800-63A](sp800-63a.html) Section 8.2 and SHOULD NOT be rolled up into a legalistic privacy policy or general terms and conditions. Rather, if there are uses outside the bounds of these explicit purposes, the subscriber SHOULD be provided with a meaningful way to understand the purpose for additional uses, and the opportunity to accept or decline.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to an agency offering or using the authentication service:

1. The agency SHALL consult with their Senior Agency Official for Privacy (SAOP) and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[Privacy Act]](#PrivacyAct) (see [Section 9.4](#agency-privacy)).
* The agency SHALL publish a System of Records Notice (SORN) to cover such collections, as applicable.
* The agency SHALL consult with their SAOP and conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](#E-Gov).
* The agency SHALL publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

### 4.5 Summary of Requirements

*This section is informative.*

[Table 4-1](#63bSec4-Table1) summarizes the requirements for each of the AALs:

<a name="63bSec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1 AAL Summary of Requirements**

</div>

Requirement | AAL1 | AAL2 | AAL3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret;<br />Look-up Secret;<br />Out-of-Band;<br />SF OTP Device;<br />MF OTP Device;<br />SF Crypto Software;<br />SF Crypto Device;<br />MF Crypto Software;<br />MF Crypto Device<br /> | MF OTP Device;<br />MF Crypto Software;<br />MF Crypto Device;<br />or Memorized Secret plus:<br />&nbsp;&bull;&nbsp;Look-up Secret<br />&nbsp;&bull;&nbsp;Out-of-Band<br />&nbsp;&bull;&nbsp;SF OTP Device<br />&nbsp;&bull;&nbsp;SF Crypto Software<br />&nbsp;&bull;&nbsp;SF Crypto Device<br /> | MF Crypto Device;<br />SF Crypto Device plus &nbsp;&nbsp;Memorized Secret;<br />SF OTP Device plus MF Crypto Device or Software;<br />SF OTP Device plus SF Crypto Software plus Memorized Secret
**FIPS 140 verification** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators)<br />Level 1 overall (verifiers and SF Crypto Devices)<br />Level 3 physical security (all authenticators)
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; MAY use one authentication factor | 12 hours or 15 minutes inactivity; SHALL use both authentication factors
**Security controls**|[SP 800-53](#SP800-53) Low Baseline (or equivalent)|[SP 800-53](#SP800-53) Moderate Baseline (or equivalent)|[SP 800-53](#SP800-53) High Baseline (or equivalent)
**MitM resistance** | Required | Required | Required |
**Verifier-impersonation resistance** | Not required | Not required | Required |
**Verifier-compromise resistance** | Not required | Not required | Required |
**Replay resistance** | Not required | Required | Required |
**Authentication intent** | Not required | Recommended | Required |
**Records Retention Policy** | Required | Required | Required |
**Privacy Controls** | Required | Required | Required |
