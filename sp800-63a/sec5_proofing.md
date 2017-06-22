<a name="sec5"></a>

<div class="breaker"></div>

## <a name="ipv-section"></a> 5 Identity Resolution, Validation, and Verification

_This section is normative._

This section lists the requirements to resolve, validate, and verify an identity and any supplied identity evidence. The requirements are intended to ensure the claimed identity is the actual identity of the subject attempting to enroll with the CSP and that scalable attacks affecting a large population of enrolled individuals require greater time and cost than the value of the resources the system is protecting.

### <a name="resolve"></a>5.1 Identity Resolution

The goal of identity resolution is to uniquely distinguish an individual within a given population or context. Effective identity resolution uses the smallest set of attributes necessary to resolve to a unique individual. It provides the CSP an important starting point in the overall identity proofing process, to include the initial detection of potential fraud, but in no way represents a complete and successful identity proofing transaction.

1.  Exact matches of information used in the proofing process can be difficult to achieve. The CSP MAY employ appropriate matching algorithms to account for differences in personal information and other relevant proofing data across multiple forms of identity evidence, issuing sources, and authoritative sources. Matching algorithms and rules used SHOULD be available publicly or, at minimum, to the relevant community of interest. For example, they may be included as part of the written policy or _practice statement_ referred to in [Section 4.2](#genProofReqs).
2.  KBV (sometimes referred to as knowledge-based authentication) has historically been used to verify a claimed identity by testing the knowledge of the applicant against information obtained from public databases. The CSP MAY use KBV to resolve to a unique, claimed identity.

### <a name="validate"></a>5.2 Identity Evidence Collection and Validation

The goal of identity validation is to collect the most appropriate identity evidence (e.g., a passport or driver's license) from the applicant and determine its authenticity, validity, and accuracy. Identity validation is made up of three process steps: collecting the appropriate identity evidence, confirming the evidence is genuine and authentic, and confirming the data contained on the identity evidence is valid, current, and related to a real-life subject.

#### <a name="evidence-quality"></a> 5.2.1 Identity Evidence Quality Requirements

This section provides quality requirements for identity evidence collected during identity proofing.

[Table 5-1](#63aSec5-Table1) lists strengths, ranging from unacceptable to superior, of identity evidence that is collected to establish a valid identity. Unless otherwise noted, to achieve a given strength the evidence SHALL, at a minimum, meet all the qualities listed.

<a name="63aSec5-Table1"></a>

<div class="text-center" markdown="1">

**Table 5-1 Strengths of Identity Evidence**

</div>

|Strength|Qualities of Identity Evidence|
|:---:|:------------------------------|
|Unacceptable|- No acceptable identity evidence provided. |
|Weak|- The issuing source of the evidence did not perform identity proofing.<br><br> - The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the applicant.<br><br> - The evidence contains:<br>&nbsp;&nbsp;&nbsp;&nbsp;- At least one reference number that uniquely identifies itself or the person to whom it relates.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- The issued identity evidence contains a photograph or biometric template (of any modality) of the person to whom it relates.|
|Fair| - The issuing source of the evidence confirmed the claimed identity through an identity proofing process.<br><br> - The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates.<br><br>- The evidence:<br>&nbsp;&nbsp;&nbsp;&nbsp;- contains at least one reference number that uniquely identifies the person to whom it relates. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- contains a photograph or biometric template (any modality) of the person to whom it relates.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- can have ownership confirmed through KBV.<br><br> - Where the evidence includes digital information, that information is protected using cryptographic or proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed. <br><br> - Where the evidence includes physical security features, it requires proprietary knowledge to be able to reproduce it.<br><br> - The issued evidence is unexpired.|
|Strong|- The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the real-life identity of the person. Such procedures shall be subject to recurring oversight by regulatory or publicly-accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [Red Flags Rule](#rfr), under Section 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act).<br><br> - The issuing process for the evidence ensured that it was delivered into the possession of the subject to whom it relates.<br><br> - The issued evidence contains at least one reference number that uniquely identifies the person to whom it relates.<br><br> - The full name on the issued evidence must be the name that the person was officially known by at the time of issuance. Not permitted are pseudonyms, aliases, an initial for surname, or initials for all given names<br><br>- The:<br> &nbsp;&nbsp;&nbsp;&nbsp;- Issued evidence contains a photograph or biometric template (of any modality) of the person to whom it relates.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- Applicant proves possession of an AAL2 authenticator bound to an IAL2 identity, at a minimum.<br><br> - Where the issued evidence includes digital information, that information is protected using cryptographic or proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed.<br><br> - Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary technologies to be able to reproduce it.<br><br> - The evidence is unexpired.|
|Superior|- The issuing source of the evidence confirmed the claimed identity by following written procedures designed to enable it to have high confidence that the source knows the real-life identity of the subject. Such procedures shall be subject to recurring oversight by regulatory or publicly accountable institutions.<br><br> - The issuing source visually identified the applicant and performed further checks to confirm the existence of that person. <br><br> - The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.<br><br> - The evidence contains at least one reference number that uniquely identifies the person to whom it relates.<br><br> - The full name on the evidence must be the name that the person was officially known by at the time of issuance. Not permitted are pseudonyms, aliases, an initial for surname, or initials for all given names.<br><br> - The evidence contains a photograph of the person to whom it relates.<br><br> - The evidence contains a biometric template (of any modality) of the person to whom it relates.<br><br> - The evidence includes digital information, the information is protected using cryptographic or proprietary methods, or both, and those methods ensure the integrity of the information and enable the authenticity of the issuing source to be confirmed.<br><br> - The evidence includes physical security features that require proprietary knowledge and proprietary technologies to be able to reproduce it.<br><br> - The evidence is unexpired.|


#### <a name="evidence_validation"></a> 5.2.2 Validating Identity Evidence

Once the CSP obtains the identity evidence, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence:  

* Is genuine, authentic, and not a counterfeit, fake, or forgery;
* Contains information that is correct; and
* Contains information that relates to a real-life subject.  

[Table 5-2](#63aSec5-Table2) lists strengths, ranging from unacceptable to superior, of identity validation performed by the CSP to validate the evidence presented for the current proofing session and the information contained therein.

<a name="63aSec5-Table2"></a>

<div class="text-center" markdown="1">

**Table 5-2 Validating Identity Evidence**

</div>

|Strength|Method(s) performed by the CSP|
|:---:|:------------------------------|
|Unacceptable|- Evidence validation was not performed, or validation of the evidence failed.|
|Weak|- All personal details from the evidence have been confirmed as valid by comparison with information held or published by an authoritative source.|
|Fair| - The evidence:<br>&nbsp;&nbsp;&nbsp;&nbsp;- details have been confirmed as valid by comparison with information held or published by the issuing source or authoritative source(s).<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- has been confirmed as genuine using appropriate technologies, confirming the integrity of physical security features and that the evidence is not fraudulent or inappropriately modified.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR** <br>&nbsp;&nbsp;&nbsp;&nbsp;- The evidence has been confirmed as genuine by trained personnel. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR** <br>&nbsp;&nbsp;&nbsp;&nbsp;- The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features.|
|Strong| - The evidence has been confirmed as genuine:<br>&nbsp;&nbsp;&nbsp;&nbsp;- using appropriate technologies, confirming the integrity of physical security features and that the evidence is not fraudulent or inappropriately modified. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- by trained personnel and appropriate technologies, confirming the integrity of the physical security features and that the evidence is not fraudulent or inappropriately modified.<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- by confirmation of the integrity of cryptographic security features.<br><br> - All personal details and evidence details have been confirmed as valid by comparison with information held or published by the issuing source or authoritative source(s).|
|Superior| - The evidence has been confirmed as genuine by trained personnel and appropriate technologies including the integrity of any physical and cryptographic security features.<br><br> - All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held or published by the issuing source or authoritative source(s).|

Training requirements for personnel validating evidence SHALL be based on the policies, guidelines, or requirements of the CSP or RP. 

### 5.3 <a name="verify"></a> Identity Verification

The goal of identity verification is to confirm and establish a linkage between the claimed identity and the real-life existence of the subject presenting the evidence.

#### 5.3.1 Identity Verification Methods

[Table 5-3](#63aSec5-Table3) details the verification methods necessary to achieve a given identity verification strength. The CSP SHALL adhere to the requirements in [Section 5.3.2](#kbv) if KBV is used to verify an identity.


<a name="63aSec5-Table3"></a>

<div class="text-center" markdown="1">

**Table 5-3 Verifying Identity Evidence**

</div>

|Strength|Identity Verification Methods|
|:---:|:------------------------------|
|Unacceptable|- Evidence verification was not performed or verification of the evidence failed. Unable to confirm that the applicant is the owner of the claimed identity.|
|Weak|- The applicant has been confirmed as having access to the evidence provided to support the claimed identity.|
|Fair| - The applicant's ownership of the claimed identity has been confirmed by:<br>&nbsp;&nbsp;&nbsp;&nbsp;- KBV. See [Section 5.3.2.](#kbv) for more details. <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- a physical comparison of the applicant to the strongest piece of identity evidence provided to support the claimed identity. Physical comparison performed remotely SHALL adhere to all requirements as specified in [[SP 800-63B, Section 5.2.3.]](sp800-63b.html#biometric_use). <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- biometric comparison of the applicant to the identity evidence. Biometric comparison performed remotely SHALL adhere to all requirements as specified in [[SP 800-63B, Section 5.2.3.]](sp800-63b.html#biometric_use). |
|Strong| - The applicant's ownership of the claimed identity has been confirmed by: <br>&nbsp;&nbsp;&nbsp;&nbsp;- physical comparison, using appropriate technologies, to a photograph, to the strongest piece of identity evidence provided to support the claimed identity. Physical comparison performed remotely SHALL adhere to all requirements as specified in [[SP 800-63B, Section 5.2.3.]](sp800-63b.html#biometric_use). <br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**OR**<br>&nbsp;&nbsp;&nbsp;&nbsp;- biometric comparison, using appropriate technologies, of the applicant to the strongest piece of identity evidence provided to support the claimed identity. Biometric comparison performed remotely SHALL adhere to all requirements as specified in [[SP 800-63B, Section 5.2.3.]](sp800-63b.html#biometric_use).|
|Superior| - The applicant's ownership of the claimed identity has been confirmed by biometric comparison of the applicant to the strongest piece of identity evidence provided to support the claimed identity, using appropriate technologies. Biometric comparison performed remotely SHALL adhere to all requirements as specified in [[SP 800-63B, Section 5.2.3.]](sp800-63b.html#biometric_use).|


#### <a name="kbv"></a>5.3.2 Knowledge-Based Verification Requirements

The following requirements apply to the identity verification steps for IAL2 and IAL3. There are no restrictions for the use of KBV for identity resolution.

<div class="text-left" markdown="0">
	<ol type="1" start="1">
		<li>The CSP SHALL NOT use KBV to verify an applicant's identity against more than one piece of validated identity evidence.</li>
		<li>The CSP SHALL only use information that is expected to be known only to the applicant and the authoritative source, to include any information needed to begin the KBV process. Information accessible freely, for a fee in the public domain, or via the black market SHALL NOT be used.</li>
		<li>The CSP SHALL allow a resolved and validated identity to opt out of KBV and leverage another process for verification.</li>
		<li>The CSP SHOULD perform KBV by verifying knowledge of recent transactional history in which the CSP is a participant. The CSP SHALL ensure that transaction information has at least 20 bits of entropy. For example, to reach minimum entropy requirements, the CSP could ask the applicant for verification of the amount(s) and transaction numbers(s) of a micro-deposit(s) to a valid bank account, so long as the total number of digits is seven or greater.</li>
		<li>The CSP MAY perform KBV by asking the applicant questions to demonstrate they are the owner of the claimed information. However, the following requirements apply:</li>
			<ol type="a" start="a">
				<li>KBV SHOULD be based on multiple authoritative sources.</li>  
		  		<li>The CSP SHALL require a minimum of four KBV questions with each requiring a correct answer to successfully complete the KBV step.</li>
		  		<li>The CSP SHOULD require free-form response KBV questions. The CSP MAY allow multiple choice questions, however, if multiple choice questions are provided, the CSP SHALL require a minimum of four answer options per question.</li>
		  		<li>The CSP SHOULD allow two attempts for an applicant to complete the KBV. A CSP SHALL NOT allow more than three attempts to complete the KBV.</li>
		  		<li>The CSP SHALL time out KBV sessions after two minutes of inactivity per question. In cases of session timeout, the CSP SHALL restart the entire KBV process and consider this a failed attempt.</li>
		  		<li>The CSP SHALL NOT present a majority of diversionary KBV questions (i.e., those where "none of the above" is the correct answer).</li>
		  		<li>The CSP SHOULD NOT ask the same KBV questions in subsequent attempts.</li>
		  		<li>The CSP SHALL NOT ask a KBV question that provides information that could assist in answering any future KBV question in a single session or a subsequent session after a failed attempt.</li>
		  		<li>The CSP SHALL NOT use KBV questions for which the answers do not change (e.g., "What was your first car?").</li>
		  		<li>The CSP SHALL ensure that any KBV question does not reveal PII that the applicant has not already provided, nor personal information that, when combined with other information in a KBV session, could result in unique identification.</li>
	  		</ol>
	</ol>	
</div>	


#### <a name="vip"></a>5.3.3 In-person Proofing Requirements

In-person proofing can be satisfied in two ways:

- A physical interaction with the applicant, supervised by an operator.
- An remote interaction with the applicant, supervised by an operator, based on the specific requirements in [Section 5.3.3.2](#supervised).

#### 5.3.3.1 General Requirements

1. The CSP SHALL have the operator view the biometric source (e.g., fingers, face) for presence of non-natural materials and perform such inspections as part of the proofing process.
2. The CSP SHALL collect biometrics in such a way that ensures that the biometric is collected from the applicant, and not another subject. All biometric performance requirements in [SP 800-63B, Section 5.2.3](sp800-63b.html#biometric_use) apply.

#### <a name="supervised"></a> 5.3.3.2 Requirements for Supervised Remote In-person Proofing

CSPs can employ remote proofing processes to achieve comparable levels of confidence and security to in-person events. The following requirements establish comparability between in-person transactions where the applicant is in the same physical location as the CSP to those where the applicant is remote.

Supervised remote identity proofing and enrollment transactions SHALL meet the following requirements, in addition to the IAL3 validation and verification requirements specified in [Section 4.6](#ial3-requirements):

1. The CSP SHALL monitor the entire identity proofing session, from which the applicant SHALL NOT depart — for example, by a continuous high-resolution video transmission of the applicant.
2. The CSP SHALL have a live operator participate remotely with the applicant for the entirety of the identity proofing session.
3. The CSP SHALL require all actions taken by the applicant during the identity proofing session to be clearly visible to the remote operator. 
4. The CSP SHALL require that all digital verification of evidence (e.g., via chip or wireless technologies) be performed by integrated scanners and sensors.
5. The CSP SHALL require operators to have undergone a training program to detect potential fraud and to properly perform a virtual in-process proofing session.
6. The CSP SHALL employ physical tamper detection and resistance features appropriate for the environment in which it is located. For example, a kiosk located in a restricted area or one where it is monitored by a trusted individual requires less tamper detection than one that is located in a semi-public area such as a shopping mall concourse.
7. The CSP SHALL ensure that all communications occur over a mutually authenticated protected channel.

#### <a name="trustref"></a> 5.3.4 Trusted Referee Requirements

1. The CSP MAY use trusted referees &mdash; such as notaries, legal guardians, medical professionals, conservators, persons with power of attorney, or some other form of trained and approved or certified individuals &mdash; that can vouch for or act on behalf of the applicant in accordance with applicable laws, regulations, or agency policy. The CSP MAY use a trusted referee for both remote and in-person processes.
2. The CSP SHALL establish written policy and procedures as to how a trusted referee is determined and the lifecycle by which the trusted referee retains their status as a valid referee, to include any restrictions, as well as any revocation and suspension requirements.
3. The CSP SHALL proof the trusted referee at the same IAL as the applicant proofing. In addition, the CSP SHALL determine the minimum evidence required to bind the relationship between the trusted referee and the applicant.
4. The CSP SHOULD perform re-proofing of the subscriber at regular intervals defined in the written policy specified in item 1 above, with the goal of satisfying the requirements of [Section 4.4.1](#normal).

#### Considerations for Minors

1. The CSP SHALL give special consideration to the legal restrictions of interacting with minors unable to meet the evidence requirements of identity proofing to ensure compliance with the [Children's Online Privacy Protection Act of 1998](#COPPA), and other laws, as applicable.
2. Minors under age 13 require additional special considerations under COPPA, and other laws, to which the CSP SHALL ensure compliance, as applicable.
3. The CSP SHOULD involve a parent or legal adult guardian as a trusted referee for an applicant that is a minor, as described elsewhere in this section.

### 5.4 Binding Requirements

[800-63B](sp800-63b.html) Section 6.1 Authenticator Binding for instructions on binding authenticators to subscribers.
