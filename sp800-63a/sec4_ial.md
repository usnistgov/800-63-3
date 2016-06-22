<a name="sec4"></a>

# <a name="ial-section"></a> 4. Identity Assurance Level Requirements

The paradigm of this document is that individuals (referred to as applicants at this stage) undergo an identity proofing and enrollment process, in which their identity evidence and attributes are collected, uniquely resolved to a single identity record, then validated and verified. These attributes are then bound to an authenticator (described in [SP 800-63B](#800-63b).

The only outcome of identity proofing is to ensure that the applicant is who he/she claims to be. This includes presentation, validation and verification of the minimum attributes necessary to accomplish identity proofing.  Such core attributes, to the extent they are the minimum necessary, could include:  

1. Full name
2. Date of birth
3. Home address

It is possible that additional information could be collected in the process of identity proofing an individual, provided validation and verification follow the requirements contained herein, and the individual explicitly consents to the CSP collecting and storing the attributes.  

## 4.1. Process Flow

The following diagram outlines the basic flow for Identity Proofing and Enrollment, to include the corresponding sections with normative requirements.

<a name="figure1"></a>

<div class="text-center" markdown="1">

![](sp800-63a/media/ProofingProcess.png)

**Figure 1.  The Identity Proofing Process**

</div>

## 4.2. General Requirements

The following table shows the required IAL per M-04-04 Level of Assurance.  Agencies SHALL select the corresponding IAL based on the assessed M-04-04 LOA.

| Level of Assurance | Identity Assurance Level
|:------------------:|:-----------------------------:
| 1 | 1 
| 2 | 1 or 2 
| 3 | 1 or 2 
| 4 | 1, 2 or 3 


The following requirements apply to any CSP performing identity proofing at IAL 2 or 3. 

1. Identity proofing SHALL NOT be performed to determine suitability/entitlement to gain access to services or benefits.
2. Collection of personally identifiable information (PII) SHALL be limited to the minimum necessary to validate the existence of the claimed identity and associate the claimed identity to the person providing identity evidence based on best available practices for appropriate identity resolution, validation, and verification. 
3. The CSP SHALL provide explicit notice at the time of collection to the applicant regarding the purpose for collecting and maintaining a record of the attributes necessary for identity proofing, including whether the such attributes are voluntary or mandatory in order to complete the identity proofing transactions and the consequences for not providing the attributes. 
5.	 The CSP SHALL NOT use attributes collected and maintained in the identity proofing process for any purpose other than identity proofing, authentication, authorization or attribute assertions, or to comply with law or legal process unless the CSP provides clear notice and obtains consent from the subscriber for additional uses.  
6.	The CSP SHALL provide effective mechanisms for redress of applicant complaints or problems arising from the identity proofing. These mechanisms SHALL be easy for applicants to find and access. 
3. The CSP SHALL maintain a record of all steps taken to verify the identity of the applicant, to include steps that are additive to mandatory requirements specified herein.
4. The CSP SHALL conduct a privacy risk assessment to determine what PII is necessary to maintain a record of identity proofing, however the CSP SHALL record the types of identity evidence presented in the proofing process, including any identification and reference number.  The CSP SHALL maintain such records in accordance with National Archives and Records Administration (NARA) records retention schedules or agency specific schedules as appropriate.
5. The CSP The CSP SHALL NOT record an image, scan, or other copy of the identity evidence, unless explicitly required for a specify IAL.
4. The identity proofing and enrollment processes SHALL be performed according to an applicable written policy or *practice statement* that specifies the particular steps taken to verify identities.
6. All personally identifiable information (PII) collected as part of the enrollment process SHALL be protected to ensure confidentiality, integrity, and attribution of the information source.
13. The entire proofing transaction, including transactions that involve a third party, SHALL occur over an Authenticated Protected Channel.
13. <a name="gr14"></a>The CSP MAY obtain additional confidence in remote identity proofing using risk mitigation measures such as geolocation, device characteristics, and behavioral characteristics, so long as additional mitigations do not substitute for requirements contained herein. 

Regardless of whether the CSP is an agency or private sector provider, the following requirements apply to the agency offering or using the proofing service:

1. If the CSP employs risk mitigation measures described in General Requirement [#14](#gr14) above, the agency SHALL conduct a privacy risk assessment of these mitigation measures. Such assessments should include any privacy risk mitigations (e.g., limited retention, strict use limitations, notice, etc.) or other technological mitigations (e.g.,cryptography). The CSP SHALL NOT apply additional risk mitigation approaches without providing explicit notice of such approaches. 
2. The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the Privacy Act.
3.	The agency SHALL publish a System of Records Notice to cover such collections, as applicable.
4.	The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the collection of PII to conduct identity proofing triggers the requirements of the E-Government Act of 2002.
5.	The agency SHALL publish a Privacy Impact Assessment to cover such collections, as applicable.

## 4.4. Identity Assurance Level 1

The CSP SHALL NOT proof any applicants.  Applicants MAY self-assert 0 or more attributes to the CSP.

## 4.5. Identity Assurance Level 2

IAL 2 allows for remote or in-person identity proofing.  IAL supports a wide range of acceptable identity evidence and validation techniques in order to increase user adoption, decrease false negatives (legitimate applicants that cannot successfully complete identity proofing), and detect to the best extent possible the presentation of fraudulent identities by a malicious applicant. A CSP MAY exceed these requirements.

### 4.5.1. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity record.  See [Section 5.2](#resolve) for general resolution requirements.

### 4.5.2. Evidence Requirements

See [Section 5.3, Identity Evidence Validation](#validate) for more information on acceptable identity evidence.

- Two (2) pieces of STRONG evidence; **OR**
- One (1) piece of STRONG evidence plus two (2) pieces of ADEQUATE evidence.

### 4.5.3. Validation Requirements

See [Section 5.3, Identity Evidence Validation](#validate) for more information on acceptable identity evidence.

- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.
- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.

### 4.5.4. Verification Requirements

See [Section 5.4, Identity Verification](#verify) for more information on acceptable identity evidence.

At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.

### 4.5.5. Presence Requirements

The CSP SHOULD perform identity proofing in-person. The CSP MAY perform remote identity proofing. The CSP SHOULD offer both in-person and remote proofing.

### 4.5.6. Address Confirmation

- A CSP SHALL send an enrollment code to an address of record of the applicant.
- The applicant SHALL present a valid enrollment code to complete the identity proofing process.
- Self-asserted address data that has not been confirmed in records SHALL NOT be used for confirmation.
- The CSP MAY send the enrollment code to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address that has been verified in records
- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.
- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days but MAY be made valid up to 21 days via an exception process to accommodate addresses outside the direct reach of the U.S. postal service.  
- A notification of proofing SHALL be sent to different address of record than the destination of the enrollment code. The address of record MAY include the postal address obtained from validated identity evidence.  For example, if the CSP sends an enrollment code to a mobile phone of record, a notification of proofing will be sent to the postal address in records or obtained from validated evidence, like a drivers license.

### 4.5.7. Biometric Collection

The CSP SHALL NOT collect biometrics for any reason.

## <a name="ial3-requirements"/> 4.6. Identity Assurance Level 3

IAL 3 adds additional rigor to the steps required at IAL 2, to include providing further evidence of superior strength, and is subjected to additional and specific processes, including the use of biometrics, to further protect the identity and RP from impersonation, fraud, or other significantly harmful damages.  In addition, identity proofing at IAL 3 is either performed in-person or via a valid virtual in-person proofing process. See [Section 5.4.3](#vip) for more details. A CSP MAY exceed these requirements.

### 4.6.2. Resolution Requirements

Collection of PII SHALL be limited to the minimum necessary to resolve to a unique identity record.  See [Section 5.2](#resolve) for general resolution requirements.


### 4.6.2. Evidence Requirements

See [Section 5.3, Identity Evidence Validation](#validate) for more information on acceptable identity evidence.

- One (1) piece of SUPERIOR evidence plus one (1) piece of STRONG evidence; **OR**
- Two (2) pieces of STRONG evidence plus one (1) piece of ADEQUATE evidence

### 4.6.3. Validation Requirements  

See [Section 5.3, Identity Evidence Validation](#validate) for more information on acceptable identity evidence.

- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.
- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.

### 4.6.4. Verification Requirements

See [Section 5.4, Identity Verification](#verify) for more information on acceptable identity evidence.

- At a minimum, the applicant must be verified by a process that is able to achieve a strength of SUPERIOR.

### 4.6.5. Presence Requirements

All identity proofing steps SHOULD be performed in person. 

Virtual in-person identity proofing MAY be employed by a CSP as an equivalent process to in-person identity proofing provided all requirements specified in [Section 5.4.3](#vip) are met.

Remote proofing SHALL NOT be allowed. 

### 4.6.6 Address Confirmation

- The CSP SHALL confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence.
- Self-asserted address data SHALL NOT be used for confirmation.
- A notification of proofing SHALL be sent to the confirmed address of record. 

### 4.6.7. Biometric Collection

The CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image or fingerprints) to ensure that the applicant cannot repudiate application.  See [Section 5.2.3](#biometric_use) of SP 800-63B for more detail on biometric collection. 

## 4.7. Enrollment Code
An enrollment code allows the CSP to confirm that the applicant controls an address of record, as well as offers the applicant the ability to reestablish binding to their enrollment record.  Binding is not always completed in the same session as the original identity proofing transaction.  

An enrollment code SHALL be comprised of one of the following:

* Minimually, a random six (6) character alphanumeric. 
* A machine readable optical label, such as a QR Code, that contains data of similar or higher entropy as a random six (6) character alphanumeric.


## 4.8. Summary of Requirements
*(Non-normative; refer to preceding sections for normative requirements)*

The following table summarizes the requirements for each of the authenticator assurance levels:

Requirement | IAL 1 | IAL 2 | IAL 3
------------|-------|-------|-------
Presence|No requirements|In-person and remote|In-person or virtual in-person
Resolution|No requirements|The minimum attributes necessary to accomplish identity resolution. KBV may be used for added confidence.||
Evidence|Identity evidence is not required|Two (2) pieces of STRONG evidence<br>**OR**<br>One (1) piece of STRONG evidence plus two (2) pieces of ADEQUATE evidence|One (1) piece of SUPERIOR evidence plus one (1) piece of STRONG evidence<br>**OR**<br>Two (2) pieces of STRONG evidence plus one (1) piece of ADEQUATE evidence
Validation|No validation of evidence is required|- Each piece of evidence must be validated with a process that is able to achieve the same strength as the evidence presented; For example, if two forms of STRONG identity evidence are presented, each evidence will be validated at a strength of STRONG.<br><br>- Validation against a third party data service SHALL only be used for one piece of presented identity evidence.|Same as IAL 2.
Verification| No verification of identity is required |- At a minimum, the applicant must be verified by a process that is able to achieve a strength of STRONG.|- At a minimum, the applicant must be verified by a process that is able to achieve a strength of SUPERIOR.<br>
Address Confirmation|No requirements for address confirmation|- Self-asserted address data SHALL NOT be used for confirmation.<br>- An enrollment code consisting of at least 6 random digits SHALL be included in address confirmation.<br>- May be sent to a mobile telephone (SMS or voice), landline telephone, email, or physical mailing address obtained from records.<br>- If the enrollment code is also intended to be an authentication factor, it SHALL be reset upon first use.<br>- Enrollment codes sent by means other than physical mail SHALL be valid for a maximum of 10 minutes; those sent to a postal address of record SHALL be valid for a maximum of 7 days but MAY be made valid up to 21 days via an exception process to accommodate addresses outside the direct reach of the U.S. postal service.  <br> - A notification of proofing SHALL be sent via a different address of record than the destination of the enrollment code|- The CSP SHALL confirm address of record through validation of the address contained on any supplied, valid piece of identity evidence. - Self-asserted address data SHALL NOT be used for confirmation. - A notification of proofing SHALL be sent to the confirmed address of record.
Biometric Collection|No|No|Yes|


