<a name="sec5"></a>

<div class="breaker"></div>

## 5. Digital Identity Risk Management

_This section is normative._

This section, and the corresponding risk assessment guidance, supplements the [NIST Risk Management Framework (RMF)](#NIST-RMF) and its component special publications. This guideline does not establish additional risk management processes for agencies.  Rather, requirements contained herein provide specific guidance related to digital identity risk that agencies SHALL apply while executing all relevant RMF lifecycle phases.

### <a name="5-1-overview"></a> 5.1. Overview

In today's digital services, combining proofing, authenticator, and federation requirements into a single bundle sometimes has unintended consequences and can put unnecessary implementation burden upon the implementing organization. It is quite possible that an agency can deliver the most effective set of identity services by assessing the risk and impacts of failures for each individual component of digital authentication, rather than as a single, all-encompassing LOA. To this end, the 800-63 suite recognizes that an authentication error is not a singleton that drives all requirements. 

This guideline details requirements to assist agencies in avoiding (1) authentication errors (i.e., a false claimant using a credential that is not rightfully theirs), (2) identity proofing errors (i.e., a false claimant claiming an identity that is not rightfully theirs), and (3) federation errors (an identity assertion is compromised). From the perspective of an identity proofing failure, there are two dimensions of potential failure:

*  The impact of providing a service to the wrong subject (e.g., an attacker successfully proofs as someone else).
*  The impact of excessive identity proofing (i.e., collecting and securely storing more information about a person than is required to successfully provide the digital service).

As such, agencies SHALL assess the risk of proofing, authentication, and federation errors separately to determine the required assurance level for each transaction. 

[Section 5.3](#section5-3) provides impact categories specific to digital identity to assist in the overall application of the RMF.

Risk assessments determine the extent to which risk must be mitigated by the identity proofing, authentiation, and federation processes. These determinations drive the relevant choices of applicable technologies and mitigation strategies, rather than the desire for any given technology driving risk determinations. Once an agency has completed the overall risk assessment; selected individual assurance levels for identity proofing, authentication, and federation (if applicable); and determined the processes and technologies they will will employ to meet each assurance level, agencies SHALL develop a "Digital Identity Acceptance Statement", in accordance with NIST 800-53r5 IA-1 a.1. See [Section 5.5.](#daps) for more detail on the necessary content of the Digital Identity Acceptance Statement.

### 5.2. <a name="5-2"></a> Assurance Levels

The individual assurance levels that will be selected based on risk are as as follows:

* IAL - The robustness of the identity proofing process to confidently determine the identity of an individual. IAL is selected to mitigate potential identity proofing errors.
* AAL - The robustness of the authentication process itself, and the binding between an authenticator and the identifier of a specific individual. AAL is selected to to mitigate potential authentication errors (i.e., a false claimant using a credential that is not rightfully theirs). 
* FAL - The robustness of the assertion protocol utilized by the federation to communicate authentication and attribute information (if applicable) to an RP. FAL is optional as not all digital systems will leverage federated identity architectures. FAL is selected to mitigate potential federation errors (an identity assertion is compromised). 

A summary of each of the identity, authenticator, and federation assurance levels is provided below.


| Identity Assurance Level |
|:----------------------|
| **IAL1** - At IAL1, attributes, if any, are self-asserted or should be treated as self-asserted.|
| **IAL2** - IAL2 introduces the need for either remote or in-person identity proofing. IAL2 requires identifying attributes to have been verified in person or remotely using, at a minimum, the procedures given in [[SP 800-63A]](sp800-63a.html).|
| **IAL3** - At IAL3, in-person identity proofing is required. Identifying attributes must be verified by an authorized representative of the CSP through examination of physical documentation as described in [[SP 800-63A]](sp800-63a.html).|

|Authenticator Assurance Level|
|:----------------------|
|**AAL1** - AAL1 provides some assurance that the claimant controls an authenticator registered to the subscriber. AAL1 requires single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove possession and control of the authenticator(s) through a secure authentication protocol.|
| **AAL2** - AAL2 provides high confidence that the claimant controls authenticator(s) registered to the subscriber. Proof of possession and control of two different authentication factors is required through a secure authentication protocol. Approved cryptographic techniques are required at AAL2 and above.|
|**AAL3** - AAL3 provides very high confidence that the claimant controls authenticator(s) registered to the subscriber. Authentication at AAL3 is based on proof of possession of a key through a cryptographic protocol. AAL3 is like AAL2 but also requires a "hard" cryptographic authenticator that provides verifier impersonation resistance.|

|Federation Assurance Level|
|:----------------------|
|**FAL1** - FAL1 permits the RP to receive a bearer assertion from an identity provider (IdP). The assertion must be signed by the IdP using approved cryptography.|
|**FAL2** - FAL2 adds the requirement that the assertion be encrypted using approved cryptography such that the RP is the only party that can decrypt it.|
|**FAL3** - FAL3 requires the subscriber to present proof of possession of a cryptographic key referenced in the assertion in addition to the assertion artifact itself. The assertion must be signed using approved cryptography and encrypted to the RP using approved cryptography.|

When described generically or bundled, this guideline will refer to the combination of IAL, AAL, and FAL as **_xAL_**.

### <a name="section5-3"></a> 5.3. Risk and Impacts

This section provides details on the impact categories that SHALL be assessed to determine IAL, AAL, and FAL. 

Potential Impact Categories: To determine the appropriate level of assurance in the user’s asserted identity, agencies SHALL assess the potential risks, and identify measures to minimize their impact. 

Authentication, proofing, and federation errors with potentially worse consequences require higher levels of assurance. Business process, policy, and technology may help reduce risk.

Categories of harm and impact include:  

- Inconvenience, distress, or damage to standing or reputation
- Financial loss or agency liability
- Harm to agency programs or public interests
- Unauthorized release of sensitive information
- Personal safety
- Civil or criminal violations

Required assurance levels for digital transactions are determined by assessing the potential impact of each of the above categories using the potential impact values described in Federal Information Processing Standard (FIPS) 199, “Standards for Security Categorization of Federal Information and Information Systems.” 

The three potential impact values are:

- Low impact
- Moderate impact
- High impact

#### 5.3.1. Business Process vs. Online Transaction

The assurance level determination is only based on transactions that are part of a digital system. An online transaction may not be equivalent to a complete business process that requires offline processing, or online processing in a completely segmented system. In selecting the appropriate assurance levels, the agency should assess the risk associated with online transactions they are offering via the digital service, not the entire business process associated with the provided benefit or service. For example, in an online survey, sensitive PII may be collected, but it is never made available online to the person after the information is submitted. In this instance, it is important for the information to be carefully protected in backend systems, but there is no reason to identity proof or even authenticate the user providing the information for the purposes of their own access to the system or its associated benefits. The online transaction is solely a submission of the data. The entire business process may require a significant amount of data validation, without ever needing to know if the correct person submitted the information. In this scenario, there is no need for any identity proofing nor authentication.

Another example where the assessed risk could differ if the agency evaluated the entire business process rather than the online transaction requirements is a digital service that accepts resumes to apply for open job postings. In this use case, the digital service allows--or at least does not restrict--an individual to submit a resume on behalf of anyone else, and in subsequent visits to the site, access the resume for various purposes. Since the resume information is available to the user in later sessions, and is likely to contain PII, the agency must select an AAL that requires MFA, even though the user self-asserted the PII. In this case, the requirements of [EO 13681](#eo13681) apply and the application must provide at least AAL2. However, the identity proofing requirements remain unclear. The entire business process of examining a resume and ultimately hiring and onboarding a person requires a significant amount of identity proofing. The agency needs a high level of confidence that the job applicant is in fact the subject of the resume submitted online if a decision to hire is made. Yet this level of proofing is not required to submit the resume online. Identity proofing is not required to complete the digital portion of the transaction successfully. Identity proofing the submitter would create more risk than required in the online system as excess personal information would be collected when no such information is needed for the portion of the hiring process served by the digital job application portal and may reduce usability. Therefore, the most appropriate IAL selection would be 1. There is no need to identity proof the user to successfully complete the online transaction. This decision for the online portal itself is independent of a seemlingly obvious identiy proofing requirement for the entire business process, lest a job be offered to a fraudulent applicant.

#### 5.3.2. Impacts per Category

This section defines the potential impacts for each category of harm. Each assurance level, IAL, AAL, and FAL (if accepting or asserting a federated identity) SHALL be evaluated separately. 

> Note: If an error in the identity system causes no measurable consequences for a category, there is no impact.

_Potential impact of inconvenience, distress, or damage to standing or reputation:_    

- Low—at worst, limited, short-term inconvenience, distress, or embarrassment to any party.
- Moderate—at worst, serious short-term or limited long-term inconvenience, distress, or damage to the standing or reputation of any party.
- High—severe or serious long-term inconvenience, distress, or damage to the standing or reputation of any party. This is ordinarily reserved for situations with particularly severe effects or which potentially affect many individuals.

_Potential impact of financial loss:_

- Low—at worst, an insignificant or inconsequential financial loss to any party, or at worst, an insignificant or inconsequential agency liability.
- Moderate—at worst, a serious financial loss to any party, or a serious agency liability.
- High—severe or catastrophic financial loss to any party, or severe or catastrophic agency liability.

_Potential impact of harm to agency programs or public interests:_

- Low—at worst, a limited adverse effect on organizational operations or assets, or public interests. Examples of limited adverse effects are: (i) mission capability degradation to the extent and duration that the organization is able to perform its primary functions with noticeably reduced effectiveness, or (ii) minor damage to organizational assets or public interests.
- Moderate—at worst, a serious adverse effect on organizational operations or assets, or public interests. Examples of serious adverse effects are: (i) significant mission capability degradation to the extent and duration that the organization is able to perform its primary functions with significantly reduced effectiveness; or (ii) significant damage to organizational assets or public interests.
- High—a severe or catastrophic adverse effect on organizational operations or assets, or public interests. Examples of severe or catastrophic effects are: (i) severe mission capability degradation or loss of to the extent and duration that the organization is unable to perform one or more of its primary functions; or (ii) major damage to organizational assets or public interests.

_Potential impact of unauthorized release of sensitive information:_

- Low—at worst, a limited release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in a loss of confidentiality with a low impact as defined in FIPS PUB 199.
- Moderate—at worst, a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a moderate impact as defined in FIPS PUB 199.
- High—a release of personal, U.S. government sensitive, or commercially sensitive information to unauthorized parties resulting in loss of confidentiality with a high impact as defined in FIPS PUB 199.

_Potential impact to personal safety:_

- Low—at worst, minor injury not requiring medical treatment.
- Moderate—at worst, moderate risk of minor injury or limited risk of injury requiring medical treatment.
- High—a risk of serious injury or death.

_The potential impact of civil or criminal violations is:_

- Low—at worst, a risk of civil or criminal violations of a nature that would not ordinarily be subject to enforcement efforts.
- Moderate—at worst, a risk of civil or criminal violations that may be subject to enforcement efforts.
- High—a risk of civil or criminal violations that are of special importance to enforcement programs.

### 5.4. Risk Acceptance and Compensating Controls

The 800-63 suite specifies baseline requirements for digital identity services based on assurance level.  Agencies SHOULD implement identity services per the requirements in these guidelines and are encouraged to consider additional techniques and technologies to further secure and privacy-enhance their services.  

Agencies MAY determine to partially implement the NIST recommended guidance based on their mission risk tolerance, existing business processes, special considerations for certain populations, availablity of data that provides similar mitigations to those described in this suite, or due to other capabilities that are unique to the agency.  Agencies SHALL demonstrate comparability of compensating controls when the complete set of applicable 800-63 requirements are not implemented. That said, agencies SHALL NOT alter the assessed value based on agency capabilities. Rather, the agency MAY adjust implementation of solutions based the agency's ability to mitigate risk via means not explicitly addressed by 800-63 requirements. The agency SHALL implement prodecures to document both the justification for any departure from normative requirements and detail the compensating control employed.

This guidance addresses only those risks associated with authentication and identity proofing errors. [NIST Special Publication 800-30, “Risk Management Guide for Information Technology Systems”](#SP800-30) recommends a general methodology for managing risk in federal systems. 

### <a name="daps"></a> 5.5. Digital Identity Acceptance Statement

Shall include at a minimum:

1. Assessed xAL.
2. Implemented xAL.
3. Rationale (if 1/2 different).
4. Comparability of compensating controls when the complete set of applicable 800-63 requirements are not implemented.
5. If not accepting federated identities, rationale.

