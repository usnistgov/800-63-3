<a name="sec7"></a>

# 7. Threats and Security Considerations

There are two general categories of threats to the enrollment process: impersonation and either compromise or malfeasance of the infrastructure (CSPs). This recommendation focuses on addressing impersonation threats. Infrastructure threats are addressed by normal computer security controls (e.g., separation of duties, record keeping, independent audits) and are outside the scope of this document.

The threats to the enrollment process include impersonation attacks and threats to the transport mechanisms for identity proofing, and authenticator binding, and credential issuance. Table 1 lists the threats related to enrollment and identity proofing.

**Table 1 - Enrollment and Identity Proofing Threats**

|**Activity**   |     **Threat/Attack**  | **Example** |
|---------------|------------------------|------------------|
|Enrollment | Falsified identity proofing evidence | An applicant claims an incorrect identity by using a forged driver's license.|
| | Fraudulent use of another's identity | An applicant uses a passport associated with a different individual
| | Repudiation of enrollment | A subscriber denies enrollment, claiming that he or she did not enroll with the CSP.|
|Issuance|Disclosure | A key created by the CSP for a Subscriber is copied by an attacker as it is transported from the CSP to the subscriber during authenticator issuance.|
| |Tampering | A new password created by the subscriber is modified by an attacker as it is being submitted to the CSP during the credential issuance phase.
| |Unauthorized issuance | A person claiming to be the subscriber (but in reality is not the subscriber) is issued credentials for that subscriber.

## 7.1. Threat Mitigation Strategies

Enrollment threats can be deterred by making impersonation more difficult to accomplish or by increasing the likelihood of detection. This recommendation deals primarily with methods for making impersonation more difficult; however, it does prescribe certain methods and procedures that may help to prove who carried out an impersonation. At each level, methods are employed to determine that a person with the claimed identity exists, that the Applicant is the person who is entitled to the claimed identity, and that the Applicant cannot later repudiate the enrollment. As the level of assurance increases, the methods employed provide increasing resistance to casual, systematic and
insider impersonation. Table 2 lists strategies for mitigating threats
to the enrollment and issuance processes.

**Table 2 - Enrollment and Issuance Threat Mitigation Strategies**

| **Activity** | **Threat/Attack** | **Mitigation Strategy** |
|--------------|-------------------|-------------------------|
| Enrollment | Falsified identity proofing evidence | CSP validates physical security features of presented evidence.
| | | CSP validates personal details in the evidence with the issuer or other authoritative source.
| | Fraudulent use of another's identity | CSP verifies identity evidence or biometric of applicant against information on evidence or obtained from issuer or other authoritative source.
| | | Verify Applicant-provided non-government issued documentation (e.g. electricity bills in the name of the Applicant with the current address of the Applicant printed on the bill, or a credit card bill) to help in achieving a higher level of confidence in the identity of the applicant. |
| | Repudiation of enrollment | Have the applicant sign a form acknowledging participation in the enrollment activity. |
| |
| Issuance | Disclosure | Issue the authenticator in person, physically mail it in a sealed envelope to a secure location, or use a protected session to send the authenticator electronically.
| | Tampering | Issue credentials in person, physically mailing storage media in a sealed envelope, or through the use of a communication protocol that protects the integrity of the session data.
| | | Establish a procedure that allows the Subscriber to authenticate the CSP as the source of any authenticator and credential data that he or she may receive.
| | Unauthorized issuance | Establish procedures to ensure that the individual who receives the authenticator is the same individual who participated in the enrollment procedure.
| | | Implement a dual-control issuance process that ensures two independent individuals shall cooperate in order to issue an authenticator.
