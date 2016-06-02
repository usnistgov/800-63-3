<a name="sec5"></a>

# <a name="ipv-section"></a> 5. Identity Proofing, Validation, and Verification

The following sections list the objectives and steps a CSP SHALL follow to identity proof an individual to meet the security requirements per IAL. The requirements are intended to ensure the claimed identity is the actual identity of the person attempting to enroll with the CSP and that scalable attacks effecting a large population of enrolled individuals are difficult to execute without significant time and cost. 


## <a name="validate"></a>5.2. Identity Evidence Validation

The goal of identity validation is to collect from the applicant the most appropriate identity evidence and determine its authenticity, validity, and accuracy.  Identity validation is made up of two process steps: collecting the appropriate identity evidence and confirming the data is valid and related to an actual, live individual.

### 5.2.1. Identity Evidence Characteristic Requirements

This section provides requirements on the properties and qualities of identity evidence at a given strength.


#### 5.2.1.1. Scoring of Identity Evidence

The following table lists qualities, ranging from weak to superior, of identity evidence that is collected to establish a valid identity. Unless otherwise noted, to achieve a given strength the evidence SHALL, at a minimum, meet all the properties listed.


|Strength|Properties of Identity Evidence|
|:---:|:------------------------------| 
|Unacceptable|The issuing source did not perform identity proofing |
|Weak|- The issuing source of the evidence did not perform identity proofing.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of an individual.<br><br>- The evidence contains at least one reference number that uniquely identifies the person to whom it relates.|
|Adequate|- The issuing source of the evidence confirmed the claimed identity through an identity proofing process.<br><br>- The issuing process for the evidence means that it can reasonably be assumed to have been delivered into the possession of the person to whom it relates.<br><br>- The evidence contains at least one reference number that uniquely identifies the person to whom it relates. <br>**OR**<br> the evidence contains a photograph, image, or biometric of the person to whom it relates.<br><br>- Where the evidence includes digital information, that information is protected using cryptographic and/or proprietary methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed. <br><br>- Where the evidence includes physical security features, it requires proprietary knowledge to be able to reproduce it.<br><br> -The issued evidence is unexpired.|
Strong|- The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to form a reasonable belief that it knows the true identity of the individual. Such procedures shall be subject to recurring oversight by regulatory or publicly accountable institutions. For example, the Customer Identification Program guidelines established in response to the USA PATRIOT Act of 2001 or the [Red Flags Rule](#rfr), under Section 114 of the Fair and Accurate Credit Transaction Act of 2003 (FACT Act)<br><br>- The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.<br><br>  -The issued evidence contains at least one reference number that uniquely identifies the person to whom it relates.<br><br>- The applicants name on the issued evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for last name and at least one first name are not permitted.<br><br>- The issued evidence contains a photograph/image/biometric of the person to whom it relates.<br>**OR**<br>ownership of the evidence can be confirmed through KBV.<br><br>- Where the issued evidence includes digital information, that information is protected using cryptographic and/or proprietary methods and those methods ensure the integrity of the information and enable the authenticity of the claimed issuing source to be confirmed.<br><br>  -Where the issued evidence contains physical security features, it requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|
|Superior|- The issuing source of the evidence confirmed the claimed identity through written procedures designed to enable it to have high confidence it knows the true identity of the individual. Such procedures shall be subject to recurring oversight by regulatory or publicly accountable institutions.<br><br>- The issuing source visually identified the applicant and performed further checks to confirm the existence of that identity.<br><br>- The issuing process for the evidence ensured that it was delivered into the possession of the person to whom it relates.<br><br>- The evidence contains at least one reference number that uniquely identifies person to whom it relates.<br><br>- The applicants name on the evidence must be the name that the identity was officially known at the time of issuance. Pseudonyms, aliases and initials for first and last names are not permitted.<br><br>- The evidence contains a photograph/image of the person to whom it relates.<br><br>- The evidence contains a biometric of the person to whom it relates.<br><br>- The evidence includes digital information, the information is protected using cryptographic and/or proprietary methods and those methods ensure the integrity of the information and enable the authenticity of the issuing source to be confirmed.<br><br>- The evidence includes physical security features that requires proprietary knowledge and proprietary equipment to be able to reproduce it.<br><br>- The evidence is unexpired.|


### 5.2.2. Validating Identity Evidence

Once identity evidence is obtained by the CSP, the accuracy, authenticity, and integrity of the evidence and related information is checked against authoritative sources in order to determine that the presented evidence is:  

* Genuine, authentic, and not a counterfeit, fake, or forgery.
* The information is correct.  
* The information relates to a real individual.  

#### 5.2.2.1. Methods to Perform Identity Evidence Validation

The following table lists qualities, ranging from unacceptable to superior, of identity validation that is performed to validate evidence and the information contained therein. 


|Strength|Method(s)|
|:---:|:------------------------------| 
|Unacceptable|Validation of the evidence failed.|
|Weak|All personal details from the evidence have been confirmed as valid by comparison with information held or published by an authoritative source.|
|Adequate|- All personal and evidence details have been confirmed as valid by comparison with information held/published by the issuing source <br> **OR** <br>- The evidence has been confirmed as genuine by trained personnel and appropriate equipment, confirming the integrity of physical security features <br> **OR** <br>- The issued evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features|
|Strong|- The evidence has been confirmed as genuine by trained personnel and appropriate equipment, confirming the integrity of the physical security features **OR** The evidence has been confirmed as genuine by confirmation of the integrity of cryptographic security features.<br>**AND**<br> - All personal details and evidence details have been confirmed as valid by comparison with information held/published by the issuing source **OR** evidence details have been confirmed as valid by comparison with information held/published by the issuing source|
|Superior|- The evidence has been confirmed as genuine by trained personnel and appropriate equipment including the integrity of any physical and cryptographic security features<br>**AND**<br>- All personal details and evidence details from the evidence have been confirmed as valid by comparison with information held/published by the issuing source|

## 5.3. <a name="verify"></a> Identity Verification

The goal of identity validation is to establish a linkage to the physical, live existence of the claimed identity to the person actually presenting the evidence.

### 5.3.1. Identity Verification Methods

The following table details the verification methods necessary to achieve a given identity verification strength.  

|Strength|Identity Verification Methods|
|:---:|:------------------------------| 
|Unacceptable|Unable to confirm that the applicant is the owner of the claimed identity.|
|Weak|The applicant has been confirmed as having access to the evidence provided to support the claimed identity.|
|Adequate|- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based Verification.  See [Section 5.3.2](#kbv)  for more details.<br>**OR**<br>- The applicant’s ownership of the claimed identity has been confirmed by a physical **OR** biometric comparison of the applicant to the strongest piece of evidence provided.|
|Strong|- The applicant’s ownership of the claimed identity has been confirmed by physical comparison using a photograph/image **OR** Biometric comparison of the Applicant to the strongest piece of evidence provided to support the claimed identity.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based Verification See [Section 5.3.2](#kbv) for more details **OR** a trusted referee confirms the identity of the applicant.|
|Superior|- The applicant’s ownership of the claimed identity has been confirmed by a physical comparison of the applicant using a photograph/image to the strongest pieces of evidence **OR** by a biometric comparison of the applicant to the strongest piece of evidence provided to support the claimed identity.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by Knowledge Based VerificationSee [Section 5.3.2](#kbv) for more details.<br>**AND**<br>- The applicant’s ownership of the claimed identity has been confirmed by an interaction with the applicant via the postal address of record.|



### <a name="kbv"></a>5.3.2. Knowledge Based Verification Requirements

The following requirements apply to the identity verification steps for IAL 2 and 3. There are no restrictions for the use of KBV for identity resolution.

- KBV SHALL NOT be used if the CSP is not, or does not maintain a relationship with, an authoritative source. 
- KBV SHALL NOT be based on data held by the issuing source of an applicants supplied identity evidence.
- The CSP SHALL only use information that is expected to be known only to the applicant, to include any information that in needed to trigger KBV processes. Information accessible freely or for any fee in the public domain SHALL NOT be used.
- The CSP SHALL allow a resolved, validated, or verified identity to opt-out of KBV.

- The CSP SHOULD verify knowledge of recent transactional history that the CSP is a participant to.  For example, verification of amount and confirmation number of a micro-deposit to a claimed and valid bank account.

- The CSP MAY perform KBV by asking questions of the claimed identity to demonstrate they are the owner of the claimed information. 
	- The CSP SHALL require a minimum of four (4) KBV questions each requiring a correct answer to successfully complete the KBV step.
	- The CSP SHOULD require a free form response to a KBV question.  The CSP MAY allow multiple choice answers, however, the CSP SHALL require a minimum of four (4) multiple choice KBV answers per question.
	- The CSP SHOULD allow two (2) attempts for an applicant to complete the KBV.  A CSP MAY allow no more than three (3) attempts to complete the KBV.
	- The CSP MAY use KBV to verify an applicants identity against one (1) piece of validated identity evidence.  
	- The CSP SHALL NOT present diversionary KBV questions.  The CSP SHALL NOT allow answers to KBV questions be 'None of the Above', 'Not Applicable (N/A)', or similar to be regarded as correct.
	- The CSP SHALL NOT ask the same KBV questions in subsequent attempts.
	- The CSP SHALL time out KBV sessions after 2 minutes of inactivity per question.  In cases of session timeout, the CSP SHALL restart the entire KBV process.



### 5.3.3. Trusted Referee Requirements

The CSP MAY determine to utilize trusted referees, such as notaries, legal guardian, or some other form of certified individual that can legally vouch for and/or act on behalf of the individual.  CSP MAY use a trusted referee for both remote and in-person processes.  

In some instances, the CSP MAY allow an individual that has successfully completed identity proofing with the same CSP to act as a trusted referee for another individual.  The CSP SHALL not accept this type of trusted referee verification at IAL3.

### 5.3.4. Considerations for Minors and People with Unique Needs
Enrollment of minors under age 18, unable to meet the evidence requirements of identity proofing SHOULD involve a parent or legal adult guardian as a trusted referee as described in Section 5.3.4. Minors under age 13 require special consideration to ensure compliance with the Children's Online Privacy Protection Act of 1998, 15 USC 6501-6505 and 16 CFR Part 312.

Other individuals may have difficulty completing the identity proofing process based on various circumstances, such as not possessing the complete set of evidence requirements at a given IAL.  In these circumstances, the CSP SHOULD allow the applicant to be enrolled by a conservator or other person with power of attorney.

## 5.4. Binding Requirements

See [800-63B, Section 6.1, Authenticator Binding](sp800-63b.html#binding) for instructions on binding authenticators to subscribers.  


