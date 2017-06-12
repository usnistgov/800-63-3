<a name="sec7"></a>

<div class="breaker"></div>

## 7 Threats and Security Considerations

_This section is informative._

There are two general categories of threats to the enrollment process: impersonation, and either compromise or malfeasance of the infrastructure provider. This section focuses on impersonation threats, as infrastructure threats are addressed by traditional computer security controls (e.g., intrusion protection, record keeping, independent audits) and are outside the scope of this document. For more information on security controls, see [SP 800-53](#SP800-53), *Recommended Security and Privacy Controls for Federal Information Systems and Organizations*.

Threats to the enrollment process include impersonation attacks and threats to the transport mechanisms for identity proofing, authenticator binding, and credential issuance. [Table 7-1](#63aSec7-Table1) lists the threats related to enrollment and identity proofing.

<a name="63aSec7-Table1"></a>

<div class="text-center" markdown="1">

**Table 7-1 Enrollment and Identity Proofing Threats**

</div>



|**Activity**   |     **Threat/Attack**  | **Example** |
|---------------|------------------------|------------------|
|Enrollment | Falsified identity proofing evidence | An applicant claims an incorrect identity by using a forged driver's license.|
| | Fraudulent use of another's identity | An applicant uses a passport associated with a different individual.
| | Enrollment repudiation | A subscriber denies enrollment, claiming that they did not enroll with the CSP.|


### 7.1 Threat Mitigation Strategies

Enrollment threats can be deterred by making impersonation more difficult to accomplish or by increasing the likelihood of detection. This recommendation deals primarily with methods for making impersonation more difficult; however, it does prescribe certain methods and procedures that may help prove who perpetrated an impersonation. At each level, methods are employed to determine that a person with the claimed identity exists, that the applicant is the person entitled to the claimed identity, and that the applicant cannot later repudiate the enrollment. As the level of assurance increases, the methods employed provide increasing resistance to casual, systematic, and insider impersonation. [Table 7-2](#63aSec7-Table2) lists strategies for mitigating threats to the enrollment and issuance processes.

<a name="63aSec7-Table2"></a>

<div class="text-center" markdown="1">

**Table 7-2 Enrollment and Issuance Threat Mitigation Strategies**

</div>


| **Activity** | **Threat/Attack** | **Mitigation Strategy** |**Normative Reference(s)**|
|--------------|-------------------|-------------------------|------------------------|
| Enrollment | Falsified identity proofing evidence | CSP validates physical security features of presented evidence.|[4.4.1.3](#4-4-1-3), [4.5.3](#4-5-3), [5.2.2](#evidence_validation)|
| | | CSP validates personal details in the evidence with the issuer or other authoritative source.|[4.4.1.3](#4-4-1-3), [4.5.3](#4-5-3), [4.5.6](#4-5-6) [5.2.2](#evidence_validation)|
| | Fraudulent use of another's identity | CSP verifies identity evidence and biometric of applicant against information obtained from issuer or other authoritative source.|[4.4.1.7](#4-4-1-7), [4.5.7](#4-5-7), [5.3](#verify)|
| | |Verify applicant-provided non-government-issued documentation (e.g., electricity bills in the name of the applicant with the current address of the applicant printed on the bill, or a credit card bill) to help achieve a higher level of confidence in the applicant's identity.|[4.4.1.7](#4-4-1-7), [4.5.7](#4-5-7), [5.3](#verify)|
| | Enrollment repudiation | CSP saves a subscriber's biometric. |[4.4.1.7](#4-4-1-7), [4.5.7](#4-5-7)
