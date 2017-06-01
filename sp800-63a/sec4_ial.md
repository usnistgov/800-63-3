<a name="sec4"></a>

<div class="breaker"></div>

## <a name="ial-section"></a> 4. Identity Assurance Level Requirements

_This section is normative._

This document describes the common pattern in which an applicant undergoes an identity proofing and enrollment process in which their identity evidence and attributes are collected, uniquely resolved to a single identity within a given population or context, then validated and verified. A CSP may then bind these attributes to an authenticator (described in [SP 800-63B](sp800-63b.html)).

The only outcome of identity proofing is to ensure that the applicant is who they claim to be to a stated level of certitude. This includes presentation, validation, and verification of the minimum attributes necessary to accomplish identity proofing.  There may be many different set that suffice as the minimum, so CSPs should choose this set to balance privacy and usability needs of the user, as well as the likely attributes needed in future uses of the digital identity. As an example, such attributes, to the extent they are the minimum necessary, could include:  

1. Full name
2. Date of birth
3. Home address

This document also provides requirements for CSPs that will collect additional information used for purposes other than identity proofing.

### 4.1. Process Flow

[Figure 4-1](#63aSec4-Figure1) outlines the basic flow for Identity Proofing and Enrollment, to include the corresponding sections with normative requirements.

<a name="63aSec4-Figure1"></a>

<div class="text-center" markdown="1">
<img src="sp800-63a/media/ProofingProcess.png" alt="Identity Proofing Process" style="width:1074px;height:496px;;min-width: 1074px;min-height: 496px;"/>

**Figure 4-1. The Identity Proofing User Journey**
</div>

The following provides a sample of how a CSP and an applicant interact during the identity proofing process:

1. Resolution

	a. The CSP collects PII from the user, such as name, address, date of birth, email, and phone number.  
	b. The CSP also collects two forms of identity evidence, such as a driver license and a passport. For example, using the camera of a laptop, the CSP can capture a photo of both sides of both pieces of identity evidence.  
	c. The CSP asks the applicant for a photo of themselves to match to the license and passport.

2. Validation

	a. The CSP validates the information supplied in 1.a. by checking an authoritative source they maintain. The CSP determines the information supplied by the applicant matches their records.  
	b. The CSP checks the images of the license and the passport, determines there are no alterations, the data encoded in the QR codes  matches the plain-text information, and that the identification numbers follow standard formats.  
	c. The CSP queries the issuing sources for the license and passport and validates the information matches.

3. Verification

	a. The CSP matches the pictures on the license and the passport to the applicant picture and determines they match.    
	b. The CSP sends an enrollment code to the validated phone number of the applicant, the user provides the enrollment code to the CSP, and the CSP confirms they match, verifying the user is in possession and control of the validated phone number.  
	c. The applicant has been successfully proofed.


### <a name="genProofReqs"></a> 4.2. General Requirements


The following requirements apply to any CSP performing identity proofing at IAL2 or IAL3.

1. Identity proofing SHALL NOT be performed to determine suitability or entitlement to gain access to services or benefits.

<a name="4.2-r2"></a> 2. Collection of PII SHALL be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the applicant providing identity evidence for appropriate identity resolution, validation, and verification. This MAY include attributes that correlate identity evidence to authoritative sources and to provide RPs with attributes used to make authorization decisions.

<a name="4.2-r3"></a> 3. The CSP SHALL provide explicit notice at the time of collection to the applicant regarding the purpose for collecting and maintaining a record of the attributes necessary for identity proofing, including whether such attributes are voluntary or mandatory to complete the identity proofing process, and the consequences for not providing the attributes.

<a name="4.2-r4"></a> 4. The CSP SHALL NOT use attributes collected and maintained in the identity proofing process for any purpose other than identity proofing, authentication, or attribute assertions, or to comply with law or legal process unless the CSP provides clear notice and obtains consent from the subscriber for additional uses. CSPs SHALL NOT make consent with these additional purposes a condition of the service.

<a name="4.2-r5"></a> 5. The CSP SHALL provide mechanisms for redress of applicant complaints or problems arising from the identity proofing. These mechanisms SHALL be easy for applicants to find and use. The CSP SHALL assess the mechanisms for their efficacy in achieving resolution of complaints or problems.

<a name="4.2-r6"></a> 6. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities. The *practice statement* SHALL include control information that details how the CSP handles proofing errors that result in an applicant not being successfully enrolled.  For example, the number of retries allowed, proofing alternatives (e.g., in-person if remote fails), or fraud counter-measures when anomolies are detected.

<a name="4.2-r7"></a> 7. The CSP SHALL maintain a record, to include audit logs, of all steps taken to verify the identity of the applicant and SHALL record the types of identity evidence presented in the proofing process. The CSP SHALL conduct a risk management process, including asessements of privacy and security risks to determine:

	a) Any steps that it will take to verify the identity of the applicant beyond any mandatory requirements specified herein;  
	b) The PII, including any biometrics, images, scans, or other copies of the identity evidence that the CSP will maintain as a record of identity proofing (Note: Specific federal requirements may apply.); and  
	c) The schedule of retention for these records (Note: CSPs may be subject to specific retention policies in accordance with applicable laws, regulations, or policies, including any National Archives and Records Administration (NARA) records retention schedules that may apply.).  

<a name="4.2-r8"></a> 8. All PII collected as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source.

<a name="4.2-r9"></a> 9. The entire proofing transaction, including transactions that involve a third party, SHALL occur over an authenticated protected channel.

<a name="4.2-r10"></a> 10. The CSP SHOULD obtain additional confidence in identity proofing using fraud mitigation measures (e.g., inspecting geolocation, examining the device characteristics of the applicant, evaluating behavioral characteristics, checking vital statistic repositories such as the [Death Master File](https://www.ssdmf.com/Library/InfoManage/Guide.asp?FolderID=1)), so long as any additional mitigations do not substitute for the mandatory requirements contained herein. In the event the CSP uses fraud mitigation measures, the CSP SHALL conduct a privacy risk assessment for these mitigation measures. Such assessments SHOULD include any privacy risk mitigations (e.g., limited retention, use limitations, notice) or other technological mitigations (e.g., cryptography), and be documented per requirement 4.2(7) above.

<a name="4.2-r11"></a> 11. In the event a CSP ceases to conduct identity proofing and enrollment processes, the CSP SHALL be responsible for fully disposing of or destroying any sensitive data including PII, or its protection from unauthorized access for the duration of retention.

<a name="4.2-r12"></a> 12. Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the proofing service:  

	a. The agency SHALL consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the Privacy Act.  
	b. The agency SHALL publish a System of Records Notice (SORN) to cover such collection, as applicable.  
	c. The agency SHALL consult with their SAOP to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the E-Government Act of 2002.  
	d. The agency SHALL publish a Privacy Impact Assessment (PIA) to cover such collection, as applicable.

<a name="4.2-r13"></a> 
13. The CSP SHOULD NOT collect the SSN unless it is necessary for performing identity resolution and cannot be accomplished by collection of another attribute or combination of attributes.

### 4.3. Identity Assurance Level 1

1. A CSP that supports only IAL1 CSP SHALL NOT validate and verify attributes.
2. The CSP MAY request zero or more self-asserted attributes from the applicant to support their service offering.
3. An IAL2 or IAL3 CSP SHOULD support RPs that only require IAL1, if the user consents.

### 4.4. Identity Assurance Level 2

IAL2 allows for **remote** or **in-person** identity proofing.  IAL2 supports a wide range of acceptable identity proofing techniques in order to increase user adoption, decrease false negatives (legitimate applicants that cannot successfully complete identity proofing), and detect to the best extent possible the presentation of fraudulent identities by a malicious applicant.

A CSP SHALL proof according to the requirements in [Section 4.4.1](#normal) or [Section 4.4.2](#referee). A CSP SHOULD implement identity proofing in accordance with [Section 4.4.1](#normal). Depending on the population the CSP serves, the CSP MAY implement identity proofing in accordance with [Section 4.4.2](#referee).

#### <a name="normal"></a>4.4.1. IAL2 Conventional Proofing Requirements

#### 4.4.1.1. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity in a given context.  This MAY include the collection of attributes that assist in data queries. See [Section 5.1](#resolve) for general resolution requirements.

#### 4.4.1.2. Evidence Collection Requirements

The CSP SHALL collect the following from the applicant:

1. One piece of SUPERIOR or STRONG evidence **if** the issuing source of the evidence, during its identity proofing event, confirmed the claimed identity by collecting two or more forms of SUPERIOR or STRONG evidence **and** the CSP validates the evidence directly with the issuing source; **OR**
2. Two pieces of STRONG evidence; **OR**
3. One piece of STRONG evidence plus two pieces of FAIR evidence.

See [Section 5.2.1. Identity Evidence Quality Requirements](#evidence-quality) for more information on acceptable identity evidence.

#### 4.4.1.3. Validation Requirements

The CSP SHALL validate identity evidence as follows:

Each piece of evidence SHALL be validated with a process that is able to achieve the same strength as the evidence presented. For example, if two forms of STRONG identity evidence are presented, each piece of evidence will be validated at a strength of STRONG.

See [Section 5.2.2. Validating Identity Evidence](#evidence_validation) for more information on validating identity evidence.

#### 4.4.1.4. Verification Requirements

The CSP SHALL verify identity evidence as follows:

1. At IAL2, at least one piece of STRONG (or SUPERIOR) identity evidence is required. At a minimum, the applicant's binding to the STRONG (or SUPERIOR) identity evidence must be verified by a process that is able to achieve a strength of STRONG.
2. KBV SHALL NOT be used for in-person (physical or supervised remote) identity verification.

See [Section 5.3. Identity Verification](#verify) for more information on acceptable identity evidence.

#### 4.4.1.5. Presence Requirements

The CSP SHALL support in-person or remote identity proofing. The CSP SHOULD offer both in-person and remote proofing.

#### <a name="4-4-1-6"></a> 4.4.1.6. Address Confirmation

1. Valid records to confirm address SHALL be issuing source(s) or authoritative source(s).
2. The CSP SHALL confirm address of record. The CSP SHOULD confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence. The CSP MAY confirm address of record by validating information supplied by the applicant that is not contained on any supplied piece of identity evidence.
3. Self-asserted address data that has not been confirmed in records SHALL NOT be used for confirmation.
4. **If CSP performs in-person proofing (physical or supervised remote):**  

	a. The CSP SHOULD send a notification of proofing to a confirmed address of record.  
	b. The CSP MAY provide an enrollment code directly to the subscriber if binding to an authenticator will occur at a later time.  
	c. The enrollment code SHALL be valid for a maximum of 7 days.  

5. **If the CSP performs remote proofing (unsupervised):**  

	a. The CSP SHALL send an enrollment code to a confirmed address of record for the applicant.  
	b. The applicant SHALL present a valid enrollment code to complete the identity proofing process.  
	c. The CSP SHOULD send the enrollment code to the postal address that has been validated in records.  The CSP MAY send the enrollment code to a mobile telephone (SMS or voice), landline telephone, or email if it has been validated in records.  
	d. If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.  
	e. Enrollment codes sent to a postal address of record SHALL be valid for a maximum of 10 days but MAY be made valid up to 30 days via an exception process to accommodate addresses outside the contiguous United States. Enrollment codes sent by telephone SHALL be valid for a maximum of 10 minutes. Enrollment codes sent via email SHALL be valid for a maximum of 24 hours.  
	f. The CSP SHALL ensure the enrollment code and notification of proofing are sent to different addresses of record. For example, if the CSP sends an enrollment code to a phone number validated in records, a notification of proofing will be sent to the postal address validated in records or obtained from validated and verified evidence, such as a driver license.  

> Note: Postal address is the preferred method of sending any communications, to include enrollment code and notifications, with the applicant. However, this guideline supports any confirmed address of record, whether physical or digital.

#### 4.4.1.7. Biometric Collection

The CSP MAY collect biometrics for the purposes of non-repudiation and re-proofing. See [Section 5.2.3. of SP 800-63B](sp800-63b.html#biometric_use) for more detail on biometric collection.

#### 4.4.1.8. Security Controls

The CSP SHALL employ appropriately tailored security controls, to include control enhancements, from the moderate or high baseline of security controls defined in [[SP 800-53]](#SP800-53) or equivalent federal (e.g., [FEDRAMP](#FEDRAMP))  or industry standard.

#### <a name="referee"></a>4.4.2. IAL2 Trusted Referee Proofing Requirements

In instances where an individual cannot meet the identity evidence requirements specified in [Section 4.4.1.](#normal), the agency MAY use a trusted referee to assist in identity proofing the applicant.  See [Section 5.3.4.](#trustref) for more details.

### <a name="ial3-requirements"></a> 4.5. Identity Assurance Level 3

IAL3 adds additional rigor to the steps required at IAL2, to include providing further evidence of superior strength, and is subjected to additional and specific processes, including the use of biometrics, to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages. Biometrics are used to detect fraudulent enrollments, duplicate enrollments, and as a mechanism to re-establish binding to a credential.  In addition, identity proofing at IAL3 is performed in-person. See [Section 5.3.3.](#vip) for more details.

#### 4.5.1. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity record.  This MAY include the collection of attributes that assist in data queries. See [Section 5.1.](#resolve) for general resolution requirements.


#### 4.5.2. Evidence Collection Requirements

The CSP SHALL collect the following from the applicant:

1. Two pieces of SUPERIOR evidence; **OR**
2. One piece of SUPERIOR evidence and one piece of STRONG evidence **if** the issuing source of the STRONG evidence, during its identity proofing event, confirmed the claimed identity by collecting two or more forms of SUPERIOR or STRONG evidence **and** the CSP validates the evidence directly with the issuing source; **OR**
3. Two pieces of STRONG evidence plus one piece of FAIR evidence.

See [Section 5.2.1. Identity Evidence Quality Requirements](#evidence-quality) for more information on acceptable identity evidence.

#### 4.5.3. Validation Requirements  

The CSP SHALL validate identity evidence as follows:

Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented. For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.

See [Section 5.2.2. Validating Identity Evidence](#evidence_validation) for more information on validating identity evidence

#### 4.5.4. Verification Requirements

The CSP SHALL verify identity evidence as follows:

1. At IAL3, when SUPERIOR identity evidence is collected, the applicant's binding to the SUPERIOR identity evidence must be verified by a process that is able to achieve a strength of SUPERIOR. If the CSP only collects two pieces of STRONG identity evidence, the applicant's binding to *both* pieces of STRONG identity evidence must be verified by a process that is able to achieve a strength of STRONG.
2. KBV SHALL NOT be used for in-person (physical or supervised remote) identity verification.

See [Section 5.3. Identity Verification](#verify) for more information on acceptable identity evidence.

#### 4.5.5. Presence Requirements

The CSP SHALL perform all identity proofing steps with the applicant in-person. See [Section 5.3.3.](#vip) for more details.


#### 4.5.6. Address Confirmation

1. The CSP SHALL confirm address of record. The CSP SHOULD confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence. The CSP MAY confirm address of record by validating information supplied by the applicant, not contained on any supplied, valid piece of identity evidence.
2. Self-asserted address data SHALL NOT be used for confirmation.
3. A notification of proofing SHALL be sent to the confirmed address of record.
4. The CSP MAY provide an enrollment code directly to the subscriber if binding to an authenticator will occur at a later time. The enrollment code SHALL be valid for a maximum of 7 days.

#### 4.5.7. Biometric Collection

The CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image, fingerprints) for the purposes of non-repudiation and re-proofing.  See [Section 5.2.3. of SP 800-63B](sp800-63b.html#biometric_use) for more detail on biometric collection.

#### 4.5.8. Security  Controls

The CSP SHALL employ appropriately tailored security controls, to include control enhancements, from the High baseline of security controls defined in [SP 800-53](#SP800-53) or an equivalent federal (e.g., [FEDRAMP](#FEDRAMP)) or industry standard.

### <a name="enrollmentcode"></a> 4.6. Enrollment Code

An enrollment code allows the CSP to confirm that the applicant controls an address of record, as well as offering the applicant the ability to reestablish binding to their enrollment record.  Binding NEED NOT be completed in the same session as the original identity proofing transaction.  

An enrollment code SHALL be comprised of one of the following:

1. Minimally, a random six character alphanumeric or equivalent entropy. For example, a code generated using an approved random number generator or a serial number for a physical hardware authenticator.
2. A machine readable optical label, such as a QR Code, that contains data of similar or higher entropy as a random six character alphanumeric.


### 4.7. Summary of Requirements

_This section is informative._

[Table 4-1](#63aSec4-Table1) summarizes the requirements for each of the authenticator assurance levels:

<a name="63aSec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1. IAL Requirements Summary**

</div>

Requirement | IAL1 | IAL2 | IAL3
------------|-------|-------|-------
Presence|No requirements|In-person and unsupervised remote|In-person and supervised remote
Resolution|No requirements|The minimum attributes necessary to accomplish identity resolution<br><br>KBV may be used for added confidence| Same as IAL2
Evidence|No identity evidence is collected| - One piece of SUPERIOR or STRONG evidence depending on strength of original proof and validation occurs with issuing source; or<br><br>- Two pieces of STRONG evidence, or <br><br> - One piece of STRONG evidence plus two pieces of FAIR evidence|- Two pieces of SUPERIOR evidence, or<br><br> - One piece of SUPERIOR evidence and one piece of STRONG evidence depending on strength of original proof and validation occurs with issuing source, or<br><br> - Two pieces of STRONG evidence plus one piece of FAIR evidence
Validation|No validation|Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented|Same as IAL2
Verification| No verification |Verified by a process that is able to achieve a strength of STRONG.|Verified by a process that is able to achieve a strength of SUPERIOR.<br>
Address Confirmation|No requirements for address confirmation|Required. Enrollment code sent to any address of record.  Notification sent by means different from enrollment code.|Required. Notification of proofing to postal address.
Biometric Collection|No|Optional|Mandatory
Security Controls|N/A|[SP 800-53](#SP800-53) Moderate Baseline (or equivalent federal or industry standard)|[SP 800-53](#SP800-53) High Baseline (or equivalent federal or industry standard)