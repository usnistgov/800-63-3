<a name="sec7"></a>

<div class="breaker"></div>

## 7. Threats and Security Considerations

_This section is informative._

There are two general categories of threats to the enrollment process: impersonation and compromise or malfeasance of the infrastructure provider. This section addresses impersonation threats. Infrastructure threats are addressed by traditional computer security controls (e.g., intrusion protection, record keeping, independent audits) and are outside the scope of this document. For more information on security controls, see [[SP 800-53]](#SP800-53), *Recommended Security and Privacy Controls for Federal Information Systems and Organizations*.

The threats to the enrollment process include impersonation attacks and threats to the transport mechanisms for identity proofing, authenticator binding, and credential issuance. [Table 7-1](#63aSec7-Table1) lists the threats related to enrollment and identity proofing.

<a name="63aSec7-Table1"></a>

<div class="text-center" markdown="1">

**Table 7-1.  Enrollment and Identity Proofing Threats**

</div>



|**Activity**   |     **Threat/Attack**  | **Example** |
|---------------|------------------------|------------------|
|Enrollment | Falsified identity proofing evidence | An applicant claims an identity by using a forged driver's license.|
| | Fraudulent use of another's identity | An applicant uses a passport associated with a different individual.
| | Repudiation of enrollment | A subscriber denies enrollment, claiming that they did not enroll with the CSP.|
||Social engineering|An attacker manipulates an individual at the CSP who is responsible for performing some or all of the identity proofing in order to be enrolled under a fraudulent or stolen identity.
|Issuance|Disclosure | A key created by the CSP for a subscriber is copied by an attacker as it is transported from the CSP to the subscriber.|
| |Tampering | A new password created by the subscriber is modified by an attacker as it is being submitted to the CSP.
| |Unauthorized issuance | A person claiming to be the subscriber (but in reality is not the subscriber) is issued credentials for that subscriber.
||Social engineering|An attacker manipulates an individual at the CSP who is responsible for issuance in order to obtain a credential bound to another, valid subscriber.


### 7.1. Threat Mitigation Strategies

Enrollment threats can be mitigated by making impersonation more difficult to accomplish or by increasing the likelihood of detection. This section recommends methods for making impersonation more difficult. It also prescribes certain methods and procedures that may help to prove who carried out an impersonation attack. At each level of identity assurance, methods are employed to determine that a person with the claimed identity exists, that the applicant is the person who is entitled to the claimed identity, and that the applicant cannot later repudiate the enrollment. As the level of assurance increases, the methods employed provide increasing resistance to casual, systematic, and
insider impersonation. [Table 7-2](#63aSec7-Table2) lists strategies for mitigating threats
to the enrollment and issuance processes.

<a name="63aSec7-Table2"></a>

<div class="text-center" markdown="1">

**Table 7-2.  Enrollment and Issuance Threat Mitigation Strategies**

</div>


| **Activity** | **Threat/Attack** | **Mitigation Strategy** |
|--------------|-------------------|-------------------------|
| Enrollment | Falsified identity proofing evidence | CSP validates physical security features of presented evidence.
| | | CSP validates personal details in the evidence with the issuer or other authoritative source.
| | Fraudulent use of another's identity | CSP verifies identity data or biometric of applicant against information on evidence or obtained from issuer or other authoritative source.
| | | Verify applicant-provided non-government issued documentation (e.g., electricity bill or a credit card bill) to help achieve a higher level of confidence in the identity of the applicant. |
| | Repudiation of enrollment | Have the applicant sign a form acknowledging participation in the enrollment activity. |
||Social engineering|CSP conducts duplicate records check.
| Issuance | Disclosure | CSP issues the authenticator in person, physically mails it in a tamper-resistant sealed envelope to a secure location, or uses a protected session to send the authenticator electronically.
| | Tampering | CSP issues credentials in person, physically mailing storage media in a tamper-resistant sealed envelope, or through the use of a communication protocol that protects the integrity of the session data.
| | | CSP establishes a procedure that allows the Subscriber to authenticate the CSP as the source of any authenticator and credential data that he or she may receive.
| | Unauthorized issuance/social engineering | CSP establishes procedures to ensure that the individual who receives the authenticator is the same individual who participated in the enrollment process.
| | | CSP implements a dual-control issuance process that ensures two independent individuals cooperate in order to issue an authenticator.
