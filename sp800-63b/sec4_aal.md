<a name="sec4"></a>

## <a name="AAL_SEC4"></a>4. Authenticator Assurance Levels

_This section is normative._

In order to satisfy the requirements of a given AAL, a claimant SHALL be authenticated with at least a given level of strength to be recognized as a subscriber. The result of an authentication process is an identifier that MAY be pseudonymous and that SHALL be used each time that subscriber authenticates to that relying party. Optionally, other attributes that identify the subscriber as a unique subject may also be provided.

Detailed normative requirements for authenticators and verifiers at each AAL are provided in Section 5.

FIPS 140 requirements are satisfied by [[FIPS 140-2]](#FIPS140-2) or newer revisions.

[Table 4-1](#63bSec4-Table1) lists strict adherence to M-04-04 Level of Assurance, mapping the corresponding Authenticator Assurance Levels.

<a name="63bSec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1.  Legacy M-04-04 AAL Requirements**

</div>


| M-04-04 Level of Assurance (LOA) |  Authenticator Assurance Level (AAL) |
|:------------------:|:-----------------------------:|
| 1 |  1| 
| 2 |  2 or 3 |
| 3 |  2 or 3 |
| 4 |  3 |

However, [Table 4-2](#63bSec4-Table2) shows the expanded set of AALs that are allowable to meet M-04-04 Levels of Assurance. Agencies SHALL select the corresponding AAL based on the impact of an authentication failure. 

<a name="63bSec4-Table2"></a>

<div class="text-center" markdown="1">

**Table 4-2.  Recommended M-04-04 AAL Requirements**

</div>

| M-04-04 Level of Assurance | Authenticator Assurance Level
|:------------------:|:-----------------------------:
| 1, without making personal data available | 1, 2 or 3 
| 1, making personal data available | 2 or 3
| 2 | 2 or 3
| 3 | 2 or 3 
| 4 | 3 

At IAL 1, it is possible that attributes are collected and made available by the digital service.  Any personal data, whether self-asserted or validated, requires multi-factor authentication; therefore agencies SHALL select a minimum of AAL 2 when self-asserted personal data, collected at IAL 1, is made available online.

### 4.1. Authenticator Assurance Level 1

AAL 1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL 1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator through a secure authentication protocol.

#### 4.1.1. Permitted Authenticator Types

AAL 1 permits the use of any of the following authenticator types, which are defined in Section 5:

* Memorized Secret
* Look-up Secret
* Out of Band (Partially deprecated; see [Section 5.1.3](#out-of-band) for more details)
* Single Factor OTP Device
* Multi-Factor OTP Device
* Single Factor Cryptographic Software
* Single Factor Cryptographic Device
* Multi-Factor Cryptographic Software
* Multi-Factor Cryptographic Device

#### 4.1.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL 1 SHALL use approved cryptography. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise of the platform in which they are running (e.g., by malware) and SHOULD decline to operate when such a compromise is detected.

Communication between the claimant and channel (the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks.

Verifiers operated by government agencies at AAL 1 SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1.

#### <a name="aal1reauth"></a>4.1.3. Reauthentication

At AAL 1, reauthentication of the subscriber SHOULD be repeated at least once per 30 days, regardless of user activity.

#### 4.1.4. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the low baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *low* baseline are satisfied.

#### 4.1.5. Records Retention

The CSP shall comply with their respective records retention policies in accordance with applicable laws and regulations. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained.

### 4.2. Authenticator Assurance Level 2

AAL 2 provides high confidence that the claimant controls authenticator(s) registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. Approved cryptographic techniques are required at AAL 2 and above.

#### 4.2.1. Permitted Authenticator Types

At AAL 2, it is required to have either a multi-factor authenticator or a combination of two single-factor authenticators. Authenticator requirements are specified in Section 5.

When a multi-factor authenticator is used, any of the following may be used:

* Multi-Factor OTP Device
* Multi-Factor Cryptographic Software
* Multi-Factor Cryptographic Device

When a combination of two single-factor authenticators is used, it SHALL include a Memorized Secret authenticator and one possession-based ("something you have") authenticator from the following list:

* Look-up Secret
* Out of Band
* Single Factor OTP Device
* Single Factor Cryptographic Software
* Single Factor Cryptographic Device

> Note: The requirement for a memorized secret authenticator above derives from the need for two different types of authentication factors to be used. All biometric authenticators compliant with this specification are multi-factor, so something you know (a memorized secret) is the remaining possibility.

#### 4.2.2. Authenticator and Verifier Requirements

Cryptographic authenticators used at AAL 2 SHALL use approved cryptography. Authenticators procured by government agencies SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1. Software-based authenticators that operate within the context of a general purpose operating system MAY, where practical, attempt to detect compromise of the platform in which they are running (e.g., by malware) and SHOULD decline to operate when such a compromise is detected. At least one authenticator used at AAL 2 SHALL be replay resistant as described in Section [5.2.7](#replay).

Communication between the claimant and verifier (the primary channel in the case of an Out of Band authenticator) SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks.

Verifiers operated by government agencies at AAL 2 SHALL be validated to meet the requirements of [[FIPS 140]](#FIPS140-2) Level 1.

#### <a name="aal2reauth"></a>4.2.3. Reauthentication

At AAL 2, authentication of the subscriber SHALL be repeated at least once per 12 hours, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following no more than 30 minutes of user inactivity. The CSP MAY prompt the user to cause activity just before the inactivity timeout, if desired. Reauthentication MAY use a single authentication factor.

#### 4.2.4. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the moderate baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *moderate* baseline are satisfied.

#### 4.2.5. Records Retention

CSPs shall comply with their respective records retention policies in accordance with whatever laws and regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained.

### 4.3. Authenticator Assurance Level 3

AAL 3 provides very high confidence that the claimant controls authenticator(s) registered to the subscriber. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is like AAL 2 but also requires a "hard" cryptographic authenticator that provides verifier impersonation resistance.

#### 4.3.1. Permitted Authenticator Types

Authentication Assurance Level 3 requires the use of one of two kinds of hardware devices:

* Multi-Factor Cryptographic Device
* Single-Factor Cryptographic Device used in conjunction with Memorized Secret

#### 4.3.2. Authenticator and Verifier Requirements

Communication between the claimant and channel SHALL be via an authenticated protected channel to provide confidentiality of the authenticator output and resistance to man-in-the-middle attacks. All cryptographic device authenticators used at AAL 3 SHALL be verifier impersonation resistant as described in Section [5.2.5](#verifimpers) and SHALL be replay resistant as described in Section [5.2.7](#replay). 

Multi-factor authenticators used at AAL 3 SHALL be hardware cryptographic modules validated at [[FIPS 140]](#FIPS140-2) Level 2 or higher overall with at least [[FIPS 140]](#FIPS140-2) Level 3 physical security. Single-factor cryptographic devices used at AAL 3 SHALL be validated at [[FIPS 140]](#FIPS140-2) Level 1 or higher overall with at least [[FIPS 140]](#FIPS140-2) Level 3 physical security.

Verifiers at AAL 3 SHALL be validated at [[FIPS 140]](#FIPS140-2) Level 1 or higher.

#### <a name="aal3reauth"></a>4.3.3. Reauthentication

At AAL 3, authentication of the subscriber SHALL be repeated at least once per 12 hours, regardless of user activity. Reauthentication of the subscriber SHALL be repeated following a period of no more than 15 minutes of user inactivity. Reauthentication SHALL use both authentication factors. The verifier MAY prompt the user to cause activity just before the inactivity timeout.

#### 4.3.4. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the high baseline of security controls defined in [[SP 800-53]](#SP800-53) or an equivalent industry standard and SHOULD ensure that the minimum assurance requirements associated with the *high* baseline are satisfied.

#### 4.3.5. Records Retention

The CSP SHALL comply with their respective records retention policies in accordance with whatever laws and regulations apply to those entities. If the CSP opts to retain records in the absence of any legal requirements, the CSP SHALL conduct a privacy risk assessment to determine how long records should be retained.

### <a name="aal_privacy"></a>4.4. Privacy Requirements

The CSP SHOULD employ appropriately tailored privacy controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard.

CSPs SHALL NOT use or disclose information about authenticators for any purpose other than conducting authentication or to comply with law or legal process, unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs MAY NOT make consent a condition of the service. Care SHALL be taken to ensure that use of such information is limited to its original purpose for collection. If the use of such information does not fall within uses related to authentication or to comply with law or legal process, the CSP SHALL provide notice and obtain consent from the subscriber.  This notice SHOULD follow the same principles as described in *Notice and Consent* in [SP 800-63A Section 8.2](sp800-63a.html#consent) and SHOULD not be rolled up into a legalistic privacy policy or general terms and conditions. Rather, if there are uses outside the bounds of these explicit purposes, the subscriber SHOULD be provided with a meaningful way to understand the purpose for additional uses, and the opportunity to accept or decline.

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the authentication service:

1. The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of Personally Identifiable Information (PII) to issue or maintain authenticators triggers the requirements of the *Privacy Act of 1974* [[PrivacyAct]](#PrivacyAct). 
* The agency SHALL publish a System of Records Notice to cover such collections, as applicable. 
* The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of PII to issue or maintain authenticators triggers the requirements of the *E-Government Act of 2002* [[E-Gov]](#E-Gov). 
* The agency SHALL publish a Privacy Impact Assessment to cover such collection, as applicable.

### 4.5. Summary of Requirements

*(Non-normative; refer to preceding sections for normative requirements)*

[Table 4-3](#63bSec4-Table3) summarizes the requirements for each of the authenticator assurance levels:

<a name="63bSec4-Table3"></a>

<div class="text-center" markdown="1">

**Table 4-3.  AAL Summary of Requirements**

</div>

Requirement | AAL 1 | AAL 2 | AAL 3
------------|-------|-------|-------
**Permitted authenticator types** | Memorized Secret;<br />Look-up Secret;<br />Out of Band;<br />SF OTP Device;<br />MF OTP Device;<br />SF Crypto Software;<br />SF Crypto Device;<br />MF Crypto Software;<br />MF Crypto Device<br /> | MF OTP Device;<br />MF Crypto Software;<br />MF Crypto Device;<br />or memorized secret plus:<br />&nbsp;&bull;&nbsp;Look-up Secret<br />&nbsp;&bull;&nbsp;Out of Band<br />&nbsp;&bull;&nbsp;SF OTP Device<br />&nbsp;&bull;&nbsp;SF Crypto Software<br />&nbsp;&bull;&nbsp;SF Crypto Device<br /> | MF Crypto Device<br />SF Crypto Device plus &nbsp;&nbsp;Memorized Secret
**FIPS 140 verification** | Level 1 (Government agency verifiers) | Level 1 (Government agency authenticators and verifiers) | Level 2 overall (MF authenticators)<br />Level 1 overall (verifiers and SF Crypto Devices)<br />Level 3 physical security (all authenticators)
**Reauthentication** | 30 days | 12 hours or 30 minutes inactivity; may use one authentication factor | 12 hours or 15 minutes inactivity; shall use both authentication factors
**Security controls**|[[SP 800-53]](#SP800-53) Low Baseline (or equivalent)|[[SP 800-53]](#SP800-53) Moderate Baseline (or equivalent)|[[SP 800-53]](#SP800-53) High Baseline (or equivalent)
**MITM resistance** | Required | Required | Required |
**Replay resistance** | Not required | Required | Required |
**Verifier impersonation resistance** | Not required | Not required | Required |





