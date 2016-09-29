<a name="sec4"></a>

## <a name="AAL_SEC4"></a>4. Authenticator Assurance Levels

In order to satisfy the requirements of a given Authenticator Assurance Level (AAL), a claimant SHALL be authenticated with at least a given level of strength to be recognized as a subscriber. The result of an authentication process is an identifier, that MAY be pseudonymous, that SHALL be used each time that subscriber authenticates to that relying party. Optionally, other attributes that identify the subscriber as a unique person may also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in Section 5.

FIPS 140 requirements are satisfied by [[FIPS 140-2]](#FIPS140-2) or newer revisions.

The following table lists strict adherence to M-04-04 Level of Assurance, mapping the corresponding Authenticator Assurance Levels. 


| M-04-04 Level of Assurance (LOA) |  Authenticator Assurance Level (AAL) |
|:------------------:|:-----------------------------:|
| 1 |  1| 
| 2 |  2 or 3 |
| 3 |  2 or 3 |
| 4 |  3 |

However, the table below shows the expanded set of AALs that are allowable to meet M-04-04 Levels of Assurance. Agencies SHALL select the corresponding AAL based on the assessed M-04-04 LOA.


| M-04-04 Level of Assurance | Authenticator Assurance Level
|:------------------:|:-----------------------------:
| 1 | 1, 2 or 3 
| 2 | 2 or 3
| 3 | 2 or 3 
| 4 | 3 


### 4.1. Authenticator Assurance Level 1

AAL 1 provides single factor remote network authentication, giving some assurance that the same Claimant who participated in previous transactions is accessing the protected transaction or data. AAL 1 allows a wide range of available authentication technologies to be employed and requires only a single authentication factor to be used. It also permits the use of any of the authentication methods of higher authenticator assurance levels. Successful authentication requires that the Claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.

#### 4.1.1. Permitted Authenticator Types

Authenticator Assurance Level 1 permits the use of any of the following authenticator types, defined in Section 5:

* Memorized Secret
* Look-up Secret
* Out of Band (Partially deprecated; see [Section 5.1.3](#out-of-band) for more details)
* Single Factor OTP Device
* Multi-Factor OTP Device
* Single Factor Cryptographic Device
* Multi-Factor Software Cryptographic Authenticator
* Multi-Factor Cryptographic Device

#### 4.1.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL 1 SHALL use approved cryptography. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise of the platform in which they are running (e.g., by malware or "jailbreak") and SHOULD decline to operate when such a compromise is detected.

Communication between the claimant and channel (the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks.

Verifiers operated by government agencies at AAL 1 SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1.

#### 4.1.3. Assertion Requirements

In order to be valid at AAL 1, authentication assertions SHALL meet the requirements defined in [SP 800-63C](sp800-63c.html). Bearer assertions MAY be used.

#### <a name="aal1reauth"></a>4.1.4. Reauthentication

At AAL 1, reauthentication of the subscriber SHOULD be repeated at least once per 30 days, regardless of user activity.

#### 4.1.5. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the low baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *low* baseline are satisfied.

#### 4.1.6. Records Retention

The CSP shall comply with their respective records retention policies in accordance with whatever laws and/or regulations apply. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long any records should be retained.

### 4.2. Authenticator Assurance Level 2

AAL 2 provides high confidence that the claimant controls the authenticator registered to a subscriber. At least two different authentication factors are required. Various types of authenticators, including multi-factor software cryptographic authenticators, may be used as described below. AAL 2 also permits any of the authentication methods of AAL 3. AAL 2 authentication requires cryptographic mechanisms that protect the primary authenticator against compromise by the protocol threats for all threats at AAL 1. Approved cryptographic techniques are required at AAL 2 and above.

#### 4.2.1. Permitted Authenticator Types

At AAL 2, it is required to have (a) a multi-factor authenticator, or (b) a combination of two single-factor authenticators. Authenticator requirements are specified in Section 5.

When a multi-factor authenticator is used, any of the following may be used:

* Multi-Factor OTP Device
* Multi-Factor Software Cryptographic Authenticator
* Multi-Factor Cryptographic Device

When a combination of two single-factor authenticators is used, it SHALL include a Memorized Secret authenticator and one possession-based ("something you have") authenticator from the following list:

* Look-up Secret
* Out of Band
* Single Factor OTP Device
* Single Factor Cryptographic Device

> Note: The requirement for a memorized secret authenticator above derives from the need for two different types of authentication factors to be used. All biometric authenticators compliant with this specification are multi-factor, so something you know (a memorized secret) is the remaining possibility.

#### 4.2.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL 2 SHALL use approved cryptography. Authenticators procured by government agencies SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise of the platform in which they are running (e.g., by malware or "jailbreak") and SHOULD decline to operate when such a compromise is detected.

Communication between the claimant and channel (the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks.

Verifiers operated by government agencies at AAL 2 SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1.

#### 4.2.3. Assertion Requirements

In order to be valid at AAL 2, authentication assertions SHALL meet the requirements defined in [SP 800-63C](sp800-63c.html). Bearer assertions MAY be used.

#### <a name="aal2reauth"></a>4.2.4. Reauthentication

At AAL 2, authentication of the subscriber SHALL be repeated at least once per 12 hours, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following no more than 30 minutes of user inactivity. The CSP MAY prompt the user to cause activity just before the inactivity timeout, if desired. Reauthentication MAY use a single authentication factor.

#### 4.2.5. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the moderate baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *moderate* baseline are satisfied.

#### 4.2.6. Records Retention

CSPs shall comply with their respective records retention policies in accordance with whatever laws and/or regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long any records should be retained.

### 4.3. Authenticator Assurance Level 3

AAL 3 provides very high confidence that the claimant controls the authenticator registered to a subscriber. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is similar to AAL 2 except that a “hard” cryptographic authenticator that also provides impersonation resistance SHALL be used.

#### 4.3.1. Permitted Authenticator Types

Authentication Assurance Level 3 requires the use of one of three kinds of hardware devices:

* Multi-Factor Cryptographic Device
* Single-Factor Cryptographic Device used in conjunction with Memorized Secret

All cryptographic device authenticators used at AAL 3 SHALL be verifier impersonation resistant as described in section [5.2.5](#verifimpers).

#### 4.3.2. Authenticator and Verifier Requirements

Communication between the claimant and channel SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks. At least one authenticator used in each AAL 3 authentication SHALL be verifier impersonation resistant as described in Section [5.2.5](#verifimpers). 

Multi-factor authenticators used at AAL 3 SHALL be hardware cryptographic modules validated at [[FIPS 140]](#FIPS140-2) Level 2 or higher overall with at least [[FIPS 140]](#FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL 3 SHALL be validated at [[FIPS 140]](#FIPS140-2) Level 1 or higher overall with at least [[FIPS 140]](#FIPS140-2) Level 3 physical security. These requirements CAN be met by using the PIV authentication key of a [[FIPS 201]](#FIPS201) compliant Personal Identity Verification (PIV) Card.

Verifiers at AAL 3 SHALL be validated at [[FIPS 140]](#FIPS140-2) Level 1 or higher.

#### 4.3.3. Assertion Requirements

In order to be valid at AAL 3, authentication assertions SHALL meet the requirements of proof-of-possession assertions as defined in [SP 800-63C](sp800-63c.html).

#### <a name="aal3reauth"></a>4.3.4. Reauthentication

At AAL 3, authentication of the subscriber SHALL be repeated at least once per 12 hours, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following a period of no more than 15 minutes of user inactivity. Reauthentication SHALL use both authentication factors. The verifier MAY prompt the user to cause activity just before the inactivity timeout.

#### 4.3.5. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the high baseline of security controls defined in [[SP 800-53]](#SP800-53) or an equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *high* baseline are satisfied.

#### 4.3.6. Records Retention

The CSP shall comply with their respective records retention policies in accordance with whatever laws and/or regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long any records should be retained. 

### 4.4. Privacy Requirements

The CSP SHOULD employ appropriately tailored privacy controls defined in [[SP 800-53]](@SP800-53) or equivalent industry standard.

CSPs SHALL NOT use or disclose information about authenticators for any purpose other than conducting authentication or to comply with law or legal process, unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs MAY NOT make consent a condition of the service.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the authentication service:

1. The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the Privacy Act. 
* The agency SHALL publish a System of Records Notice to cover such collections, as applicable. 
* The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the E-Government Act of 2002. 
* The agency SHALL publish a Privacy Impact Assessment to cover such collections, as applicable.

### 4.5. Summary of Requirements

*(Non-normative; refer to preceding sections for normative requirements)*

The following table summarizes the requirements for each of the authenticator assurance levels:

Requirement | AAL 1 | AAL 2 | AAL 3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret<br />Look-up Secret<br />Out of Band<br />SF OTP Device<br />MF OTP Device<br />SF Cryptographic Device<br />MF Software Cryptographic Authenticator<br />MF Cryptographic Device<br /> | MF OTP Device<br />MF Software Cryptographic Authenticator<br />MF Cryptographic Device<br />or memorized secret plus:<br />&nbsp;Look-up Secret<br />&nbsp;Out of Band<br />&nbsp;SF OTP Device<br />&nbsp;SF Cryptographic Device<br /> | MF Cryptographic Device<br />SF Cryptographic Device plus Memorized Secret
**FIPS 140 verification** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators)<br />Level 1 overall (verifiers and SF Crypto Devices)<br />Level 3 physical security (all authenticators)
**Assertions** | Bearer or proof of possession | Bearer or proof of possession | Proof of possession only
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; may use one authentication factor | 12 hours or 15 minutes inactivity; shall use both authentication factors
**Security controls**|[[SP 800-53]](#SP800-53) Low Baseline (or equivalent)|[[SP 800-53]](#SP800-53) Moderate Baseline (or equivalent)|[[SP 800-53]](#SP800-53) High Baseline (or equivalent)
**MITM resistance** | Required | Required | Required |
**Verifier impersonation resistance** | Not required | Not required | Required |





