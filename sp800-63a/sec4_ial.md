<a name="sec4"></a>

<div class="breaker"></div>

## <a name="ial-section"></a> 4. Identity Assurance Level Requirements

_This section is normative._

This document describes the common pattern in which a subject (referred to as an applicant at this stage) undergoes an identity proofing and enrollment process in which their identity evidence and attributes are collected, uniquely resolved to a single identity within a given population or context, then validated and verified. A CSP may then bind these attributes to an authenticator (described in [[SP 800-63B]](sp800-63b.html)).

The only outcome of identity proofing is to ensure that the applicant is who they claim to be. This includes presentation, validation, and verification of the minimum attributes necessary to accomplish identity proofing.  As an example, such core attributes, to the extent they are the minimum necessary, could include:  

1. Full name
2. Date of birth
3. Home address

It is permissible for the CSP to collect additional information in the process of identity proofing an applicant, provided validation and verification follow the requirements contained herein, and the applicant explicitly consents to the CSP collecting and storing the attributes.  

### 4.1. Process Flow

[Figure 4-1](#63aSec4-Figure1) outlines the basic flow for Identity Proofing and Enrollment, to include the corresponding sections with normative requirements.

<a name="63aSec4-Figure1"></a>

<div class="text-center" markdown="1">

![](sp800-63a/media/ProofingProcess.png)

**Figure 4-1. The Identity Proofing Process**

</div>

### <a name="genProofReqs"></a> 4.2. General Requirements


The following requirements apply to any CSP performing identity proofing at IAL2 or 3.

1. Identity proofing SHALL NOT be performed to determine suitability/entitlement to gain access to services or benefits.

2. The CSP SHOULD NOT collect the SSN unless it is necessary for performing identity resolution and cannot be accomplished by collection of another attribute or combination of attributes.

3. Collection of PII SHALL be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the applicant providing identity evidence based on best available practices for appropriate identity resolution, validation, and verification.

4. The CSP SHALL provide explicit notice at the time of collection to the applicant regarding the purpose for collecting and maintaining a record of the attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory in order to complete the identity proofing transactions and the consequences for not providing the attributes.

5. The CSP SHALL NOT use attributes collected and maintained in the identity proofing process for any purpose other than identity proofing, authentication, authorization or attribute assertions, or to comply with law or legal process unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs SHALL NOT make consent a condition of the service.

6. The CSP SHALL provide effective mechanisms for redress of applicant complaints or problems arising from the identity proofing. These mechanisms SHALL be easy for applicants to find and access.

7. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.

8. The CSP SHALL maintain a record of all steps taken to verify the identity of the applicant and SHALL record the types of identity evidence presented in the proofing process. The CSP SHALL conduct a privacy risk assessment to determine:

	a) Any steps that it will take to verify the identity of the applicant beyond any mandatory requirements specified herein;  
	b) The PII, including any biometrics, images, scans, or other copies of the identity evidence that the CSP will maintain as a record of identity proofing. Note: Specific federal requirements may apply; and  
	c) The schedule of retention for these records. Note: Specific National Archives and Records Administration (NARA) records retention schedules may apply.  

9. All PII collected as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source.

10. The entire proofing transaction, including transactions that involve a third party, SHALL occur over an Authenticated Protected Channel.

11. <a name="gr13"></a>The CSP SHOULD obtain additional confidence in unsupervised remote identity proofing using fraud mitigation measures, for example inspecting geolocation, examining the device characteristics of the applicant, evaluating behavioral characteristics, or checking vital statistic repositories such as the [Death Master File](https://www.ssdmf.com/Library/InfoManage/Guide.asp?FolderID=1), so long as any additional mitigations do not substitute for the mandatory requirements contained herein and the CSP SHALL conduct a privacy risk assessment of these mitigation measures. Such assessments SHOULD include any privacy risk mitigations (e.g., limited retention, use limitations, notice, etc.) or other technological mitigations (e.g. cryptography).

12. In the event a CSP ceases to conduct identity proofing and enrollment processes, the CSP SHALL be responsible for fully disposing of or destroying any sensitive data including PII, or its protection from unauthorized access for the duration of retention.

13. Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the proofing service:  

	a) The agency SHALL consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the Privacy Act.  
	b) The agency SHALL publish a System of Records Notice (SORN) to cover such collection, as applicable.  
	c) The agency SHALL consult with their SAOP to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the E-Government Act of 2002.  
	d) The agency SHALL publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

### 4.3. Identity Assurance Level 1

The CSP SHALL NOT proof applicants.  Applicants MAY self-assert zero or more attributes to the CSP.

### 4.4. Identity Assurance Level 2

IAL2 allows for **unsupervised remote** or **in-person** identity proofing.  IAL2 supports a wide range of acceptable identity proofing techniques in order to increase user adoption, decrease false negatives (legitimate applicants that cannot successfully complete identity proofing), and detect to the best extent possible the presentation of fraudulent identities by a malicious applicant. A CSP MAY exceed these requirements.

A CSP SHOULD implement identity proofing in accordance with [Section 4.4.1](#normal). Depending on the population the CSP serves, the CSP MAY implement identity proofing in accordance with [Section 4.4.2](#referee).

#### <a name="normal"></a>4.4.1. IAL2 Conventional Proofing Requirements

#### 4.4.1.1. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity in a given context.  See [Section 5.1](#resolve) for general resolution requirements.

#### 4.4.1.2. Evidence Collection Requirements

See [Section 5.2.1. Identity Evidence Quality Requirements](#evidence-quality) for more information on acceptable identity evidence.

- One (1) piece of SUPERIOR or STRONG evidence **if** the issuing source of the evidence, during its identity proofing event, confirmed the claimed identity by collecting two (2) or more forms of SUPERIOR or STRONG evidence **AND** the CSP validates the evidence directly with the issuing source; **OR**
- Two (2) pieces of STRONG evidence; **OR**
- One (1) piece of STRONG evidence plus two (2) pieces of FAIR evidence.

#### 4.4.1.3. Validation Requirements

See [Section 5.2.2. Validating Identity Evidence](#evidence_validation") for more information on validating identity evidence.

- Each piece of evidence SHALL be validated with a process that is able to achieve the same strength as the evidence presented. For example, if two forms of STRONG identity evidence are presented, each piece of evidence will be validated at a strength of STRONG.
- Validation against a third party data service SHALL NOT be used for more than one piece of presented identity evidence.

#### 4.4.1.4. Verification Requirements

See [Section 5.3, Identity Verification](#verify) for more information on acceptable identity evidence.

At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.

#### 4.4.1.5. Presence Requirements

In-person and unsupervised remote identity proofing are allowed. The CSP SHOULD offer both in-person and unsupervised remote proofing.

#### <a name="4-4-1-6"></a> 4.4.1.6. Address Confirmation

- The CSP SHALL confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence.


- Self-asserted address data that has not been confirmed in records SHALL NOT be used for confirmation.

- **If CSP performed in-person proofing (physical or supervised remote):**  

	- The CSP SHOULD send a notification of proofing to the address of record.
	- The CSP MAY provide an enrollment code directly to the subscriber if binding to an authenticator will occur at a later time.
	- The enrollment code SHALL be valid for a maximum of 7 days

- **If the CSP performed remote proofing (unsupervised):**  
  
	- The CSP SHALL send an enrollment code to an address of record of the applicant.
	- The applicant SHALL present a valid enrollment code to complete the identity proofing process.
	- The CSP SHOULD send the enrollment code to the physical mailing address that has been verified in records.  The CSP MAY send the enrollment code to a mobile telephone (SMS or voice), landline telephone, or email that has been verified in records.
	- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.
	- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days but MAY be made valid up to 21 days via an exception process to accommodate addresses outside the direct reach of the U.S. Postal Service.  
	- The CSP SHALL ensure the enrollment code and notification of proofing are sent by  different means. For example, if the CSP sends an enrollment code to a mobile phone of record, a notification of proofing will be sent to the physical address in records or obtained from validated and verified evidence, such as a driver’s license.

#### 4.4.1.7. Biometric Collection

The CSP MAY collect biometrics for the purposes of non-repudiation and re-proofing. See [[Section 5.2.3 of SP 800-63B]](sp800-63b.html#biometric_use) for more detail on biometric collection.

#### 4.4.1.8. Security Controls

The CSP SHOULD employ appropriately tailored security controls from the moderate baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent industry standard and SHOULD ensure that the minimum requirements associated with the *moderate* baseline are satisfied.

#### <a name="referee"></a>4.4.2. IAL2 Trusted Referee Proofing Requirements

In instances where an individual cannot meet the identity evidence requirements specified in [Section 4.4.1.](#normal), the agency MAY use a trusted referee to assist in identity proofing the enrollee.  See [Section 5.3.4.](#trustref) for more details.

### <a name="ial3-requirements"></a> 4.5. Identity Assurance Level 3

IAL3 adds additional rigor to the steps required at IAL2, to include providing further evidence of superior strength, and is subjected to additional and specific processes, including the use of biometrics, to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages.  In addition, identity proofing at IAL3 is performed in-person. See [Section 5.3.3](#vip) for more details. A CSP MAY exceed these requirements.

#### 4.5.1. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity record.  See [Section 5.1](#resolve) for general resolution requirements.


#### 4.5.2. Evidence Collection Requirements

See [Section 5.2.1. Identity Evidence Quality Requirements](#evidence-quality) for more information on acceptable identity evidence.

- Two (2) or more pieces of SUPERIOR evidence; **OR**
- One (1) piece of SUPERIOR evidence and one (1) piece of STRONG evidence **if** the issuing source of the evidence, during its identity proofing event, confirmed the claimed identity by collecting two (2) or more forms of SUPERIOR or STRONG evidence **AND** the CSP validates the evidence directly with the issuing source; **OR**
- Two (2) pieces of STRONG evidence plus one (1) piece of FAIR evidence.

#### 4.5.3. Validation Requirements  

See [Section 5.2.2. Validating Identity Evidence](#evidence_validation") for more information on validating identity evidence

- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented. For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.
- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.

#### 4.5.4. Verification Requirements

See [Section 5.3, Identity Verification](#verify) for more information on acceptable identity evidence.

- At a minimum, the applicant must be verified by a process that is able to achieve a strength of SUPERIOR.

#### 4.5.5. Presence Requirements

All identity proofing steps SHALL be performed in person. See [Section 5.3.3](#vip) for more details.

Unsupervised remote proofing SHALL NOT be allowed.

#### 4.5.6. Address Confirmation

- The CSP SHALL confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence.
- Self-asserted address data SHALL NOT be used for confirmation.
- A notification of proofing SHALL be sent to the confirmed address of record.
- The CSP MAY provide an enrollment code directly to the subscriber if binding to an authenticator will occur at a later time. The enrollment code SHALL be valid for a maximum of 7 days.

#### 4.5.7. Biometric Collection

The CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image, fingerprints) the purposes of non-repudiation and re-proofing.  See [[Section 5.2.3 of SP 800-63B]](sp800-63b.html#biometric_use) for more detail on biometric collection.

#### 4.5.8. Security  Controls

The CSP SHOULD employ appropriately tailored security controls from the High baseline of security controls defined in [[SP 800-53]](#SP800-53) or an equivalent industry standard and SHOULD ensure that the minimum requirements associated with the *high* baseline are satisfied.

### <a name="enrollmentcode"></a> 4.6. Enrollment Code

An enrollment code allows the CSP to confirm that the applicant controls an address of record, as well as offers the applicant the ability to reestablish binding to their enrollment record.  Binding is not always completed in the same session as the original identity proofing transaction.  

An enrollment code SHALL be comprised of one of the following:

* Minimally, a random six character alphanumeric. For example, a code generated using a secure random cryptographic algorithm or a serial number for a physical hardware authenticator.
* A machine readable optical label, such as a QR Code, that contains data of similar or higher entropy as a random six character alphanumeric.


### 4.7. Summary of Requirements

_This section is informative._

[Table 4-1](#63aSec4-Table1) summarizes the requirements for each of the authenticator assurance levels:

<a name="63aSec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1. IAL Requirements Summary**

</div>

Requirement | IAL1 | IAL2 | IAL3
------------|-------|-------|-------
Presence|No requirements|In-person and remote|In-person
Resolution|No requirements|The minimum attributes necessary to accomplish identity resolution. KBV may be used for added confidence.||
Evidence|Identity evidence is not required|Two (2) pieces of STRONG evidence<br>**OR**<br>One (1) piece of STRONG evidence plus two (2) pieces of FAIR evidence|One (1) piece of SUPERIOR evidence plus one (1) piece of STRONG evidence<br>**OR**<br>Two (2) pieces of STRONG evidence plus one (1) piece of FAIR evidence
Validation|No validation of evidence is required|- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.<br><br>- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.|Same as IAL2.
Verification| No verification of identity is required |- At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.|- At a minimum, the applicant must be verified by a process that is able to achieve a strength of SUPERIOR.<br>
Address Confirmation|No requirements for address confirmation|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.<br>- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address obtained from records.<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days but MAY be made valid up to 21 days via an exception process to accommodate addresses outside the direct reach of the U.S. postal service.  <br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|- The CSP SHALL confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence. - Self-asserted address data SHALL NOT be used for confirmation. - A notification of proofing SHALL be sent to the confirmed address of record.
Biometric Collection|No|Yes|Yes|
Security Controls|N/A|[[SP 800-53]](#SP800-53) Moderate Baseline (or equivalent)|[[SP 800-53]](#SP800-53) High Baseline (or equivalent)
