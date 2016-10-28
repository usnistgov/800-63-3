<a name="sec4"></a>

## 4. A New Approach to Levels of Assurance

OMB M-04-04 guides agencies to assess the potential impact of an **authentication error** as the method to determine an application or transactions overall level of assurance (LOA). Per M-04-04, in selecting an LOA, the agency is required to identity proof and issue credentials as the exact same level.  In this context, assurance is defined as:

1.  The degree of confidence in the vetting process used to establish the identity of the individual to whom the authenticator was issued, and
2. the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued.

For example, if the impact of an authentication error results in an application assessed at LOA 3, the agency must identity proof and provide authenticators that meet the requirements for LOA 3.  However, in today's digital services, combining proofing and authenticator requirements into a single bundle sometimes creates unintended consequences. Agencies should look at the impact that could result from a true authentication error (the wrong individual can use someone elses credential) AND an identity proofing error.  From the perspective of an identity proofing failure, there is two dimensions of failure:

*  The impact of providing a service to the wrong person (e.g. a fraudster successfully proofs as someone else).
*  The impact of excessive identity proofing (i.e. collecting more information about a person than is required to successfully provide the digital service.)

Therefore, this guideline does not view an authentication error as a singleton.  Rather, agencies should assess the risk of authentication and proofing errors separately in determining the appropriate technical solutions that should be applied.  

### 4.1. Categories of Assurance Levels

In order to appropriately determine the process and system requirements to reduce the risk of an authentication or identity proofing failure, this guideline introduces distinct categories of assurance which drive the technical solutions an agency may implement.  They are:

* Identity Assurance Level (IAL) - the robustness of the identity proofing process to confidently determine the identity of an individual  
* Authenticator Assurance Level (AAL) - the robustness of the authentication process itself, and the binding between an authenticator and the identifier of a specific individual.
* Federation Assurnace Level (FAL) - the robustness of the assertion protocol utilized by the federation to communicate authentication and attribute information (if applicable) to a relying party. FAL is optional as not all digital systems will leverage federated identity architectures.

A summary of each of the identity, authenticator, and federation assurance levels is provided below.


|Identity Assurance Level|
|:----------------------:|
|**IAL 1** – At this level, attributes provided in conjunction with the authentication process, if any, are self-asserted.|
|**IAL2** – IAL 2 introduces the need for either remote or in-person identity proofing. IAL 2 requires identifying attributes to have been verified in person or remotely using, at a minimum, the procedures given in [SP 800-63A](sp800-63a.html).|
|**IAL3** – At IAL 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized representative of the CSP through examination of physical documentation as described in [SP 800-63A](sp800-63a.html).|

|Authenticator Assurance Level|
|:----------------------:|
|**AAL1** - AAL 1 provides some assurance that the claimant controls the authenticator registered to a subscriber. AAL 1 uses single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.|
| **AAL2** – AAL 2 provides high confidence that the claimant controls the authenticator registered to a subscriber. Two different authentication factors are required. Approved cryptographic techniques are required at AAL 2 and above.|
|**AAL3** – AAL 3 provides very high confidence that the claimant controls the authenticator registered to a subscriber. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is similar to AAL 2 except that a "hard" cryptographic authenticator that also provides impersonation resistance is required.|

|Federation Assurance Level|
|:----------------------:|
|**FAL1** - FAL 1 allows for the subscriber to retrieve and present a bearer assertion directly to the relying party (RP) in the front channel. The assertion must be signed with using approved cryptography.|
|**FAL2** - FAL 2 requires the subscriber to retrieve an assertion artifact to present to the RP, which the RP then presents to the CSP to fetch the bearer assertion in the back channel. The assertion must be signed using approved cryptography. Alternatively, if the assertion is presented in the front channel, the assertion is required to be encrypted such that the RP is the only party that can decrypt it.|
|**FAL3** - FAL 3 builds on FAL 2 and adds the requirement that the assertion be encrypted using approved cryptography such that the RP is the only party that can decrypt it.|
|**FAL4** - FAL 4 requires the subscriber to present proof of possession of a cryptographic key referenced in the assertion in addition to the assertion artifact itself. The assertion must be signed using approved cryptography and encrypted to the RP using approved cryptography.|

When described generically or bundled, this guideline will refer to the combination of IAL, AAL, and FAL as **_xAL_**.

### 4.2. Mapping xAL to M-04-04 Levels of Assurance 

This guideline introduces a model where individual xAL's can be selected and not be at the same level in order to access a digital service, as opposed to applying a single LOA where all xAL's are equal.  In addition, since the possible number of levels available to choose from for each xAL differs from OMB M-04-04 4 LOA's, [Table 4-1](#63sec4-Table1) shows strict adherence to M-04-04 by mapping the corresponding Identity, Authenticator, and Federation Assurance Levels to LOA.

<a name="63sec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1.  Mapping xAL to Legacy M-04-04 Requirements**

</div>

| M-04-04 Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1| 1
| 2 | 2 | 2 or 3 |2
| 3 | 2 | 2 or 3 |2
| 4 | 3 | 3 |4

However, [Table 4-2](#63sec4-Table2) represents new, allowable combinations of xAL's per each M-04-04 LOA, by combining IAL, AAL, and FAL based on agency need. Further details and normative requirements to achieve each xAL are provided in [SP 800-63A](sp800-63a.html), [SP 800-63B](sp800-63b.html), and [SP 800-63C](sp800-63c.html) respectively.

<a name="63sec4-Table2"></a>

<div class="text-center" markdown="1">

**Table 4-2.  Recommended xAL to M-04-04 Requirements**

</div>

| M-04-04 Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1, 2 or 3 | 1, 2, 3, or 4
| 2 | 1 or 2 | 2 or 3 |2, 3, or 4
| 3 | 1 or 2 | 2 or 3 |2, 3, or 4
| 4 | 1, 2, or 3 | 3 |3 or 4

The mapping in [Table 4-2](#63sec4-Table2) takes advantage of the ability to separate each assurance level based on use case.  For example, an agency is allowed to adopt multi-factor authentication (MFA) at LOA1. Conversely, little or no identity proofing can be performed at the higher LOAs.  In fact, in most cases it is no longer recommended to think in terms of a single LOA per M-04-04.  Rather, a risk assessment to determine each xAL is recommended.  [Section 4.3.](#CYOA) provides details on how agencies may going about making xAL selections.

It will often be the case that IAL can be lower than AAL, not the reverse. Agency mission and risk tolerance should drive the most advantageous selection to minimize risk.  Since agencies should limit the collection of personal data in order to provide services and allow for strong pseudonymity, a specific IAL is not explicitly required for each LOA. For example, an agency may establish a "health tracker" application.  In line with the terms of [Executive Order 13681](#EO13681) requiring "...that all agencies making personal data accessible to citizens through digital applications require the use of multiple factors of authentication and an effective identity proofing process, as appropriate.", the agency could select LOA3 such that an AAL2 authenticator is required.  However, in this example, there may be no need for the agency system to know the true identity of the user.  In the past, the LOA3 assessment would also require the agency to identity proof the user at IAL2.  This is no longer necessary and the agency is encouraged to not perform any identity proofing and allow the user of the health tracker system to be pseudonymous at IAL1.  The MFA authenticator at AAL2 or AAL3 will not leak any personal information because it is bound to an IAL 1 identity.

For traditional M-04-04 LOA use cases, such as HSPD-12 requiring federal employees to obtain a Personal Identity Verification (PIV) smart card, the requirement is that agencies meet LOA4. This use case requires an authenticator at AAL3 **and** identity proofing at IAL 3.   

> Note: An agency can accept a higher assurance level than those required in the table above.  For example, in a federated transaction, an agency can accept an IAL3 identity if their application is assessed at IAL2.  The same holds true for authenticators; stronger authenticators can be used at RP's that have lower authenticator requirements.  However, RPs will ensure that these scenarios only occur in federated scenarios with appropriate privacy protections by the CSP to ensure that only the requested attributes are provided to the RP and that excessive personal information does not leak from the authenticator or the assertion.  See [privacy requirements](./sp800-63c.html#sec9) in SP 800-63C for more details.    

<!---->

> Note: Agencies are encouraged to consider each distinct element of assurance, therefore the notion of the 'low watermark' to determine LOA no longer applies.  An IAL1/AAL2 application should not be considered any less secure or privacy enhancing than an IAL2/AAL2 application.  The only difference between these applications is the amount of proofing required, which may not impact the security and privacy of each application. That said, if an agency incorrectly determines the xAL, security and privacy could very well be impacted.

 
### 4.3. <a name="CYOA"></a>Selecting the Appropriate xAL
In selecting the appropriate assurance levels, the agency should assess the risk associated with the online transactions they offering via the digital service, not the entire business process (some of which may be manual or processed by other systems) associated with an agency provided benefit or service.  For example, in the case of the census, extremely sensitive information is collected, but it is never made available online to the person after the information is submitted.  In this instance, it is important for the information to be carefully protected in backend systems, but there is no reason to identity proof or even authenticate the user providing the information.  The online transaction is submission of the data only, while the entire business process may require a significant amount of data validation, without ever needing to know if the correct person submitted the correct information regarding their family. In this scenario, there is no need for any xAL.  

Another example xALs would be different if the agency assessed risk of the entire business process rather than the online transaction requirements, is a digital service that accepts resumes in order to apply for open job postings.  In this use case, the digital service allows any individual to submit a resume, and in subsequent visits to the site, query and update the resume.  Since the resume information is being provided in later sessions, and is considered personal information, the agency must select an appropriate AAL since authentication, specifically MFA, is required.  In this case, the requirements of EO13681 apply, driving the AAL to be at least level 2.  However, what should be done about identity proofing?  The entire business process of examining a resume and ultimately interviewing a person requires a significant amount of identity proofing.  The agency needs a high level of confidence that the job applicant/interviewee is in fact the subject of the resume submitted online. Yet this level of proofing is not required to actually submit the resume online.  Identity proofing is not required to complete the digital transaction successfully.  The resume could be submitted by the applicant, but may also be submitted by a surrogate.  Identity proofing the submitter would create more risk than required in the online system as excess personal information would be collected, such as from the surrogate, when no such information is needed.  Therefore, the most appropriate IAL selection would be 1.  There is no need to identity proof the user to successfully complete the online transaction, nor is there any potential negative impact as a result of offering the online transaction if a proofing failure occurred.  Yet, there would be significant impact if the entire business process failed to correctly identity proof the person - a job may be offered to a fraudulent applicant - but that risk should not be applied holistically to the online system via a higher IAL.

> In this use case, it is assumed the system allows surrogates.  If the use case is that the only person that can submit is the actual subject of the resume, then identity proofing requirements would be significantly different.  
 
#### <a name="AAL_CYOA"></a> 4.3.1 Selecting Authenticator Assurance Level

The AAL decision tree in [Figure 4-1](#63Sec4-Figure1) offers agencies a possible path to determine the most appropriate authentication requirements for their digital service offering. This analysis is not intended to be complete nor replace M-04-04 risk assessments or any other risk management process in use by the agency. Descriptions follow for specific steps that fall outside the risk management process documented in M-04-04.

The AAL selection does not mean the digital service provider will need to issue authenticators themselves. More information of whether the agency can federate or not is provided in [Section 4.4](#toFedorNotToFed). 

<a name="63Sec4-Figure1"></a>
<div class="text-center" markdown="1">
![](sp800-63-3/media/AAL_CYOA.png)

**Figure 4-1 - Selecting AAL**
</div>

<div class="text-left" markdown="1">
<table style="width:100%">
  <tr>
    <td><img src="sp800-63/media/aal-step1.png"/></td>
  </tr>
  <tr>
   <td>Step 1 asks agencies to look at the potential impacts of an authentication failure.  In other words, what would occur if an unauthorized user accessed one or more valid user accounts. Risk should be considered from the perspective of the organization and to a valid user, since one may not be negatively impacted while the other could be significantly harmed. The risk assessment process of M-04-04 and any agency specific risk management process should commence from this step.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/aal-step2.png"/></td>
  </tr>
  <tr>
   <td>[EO 13681](#EO13681) requires MFA when any personal information is made available online. Since the other paths in this decision tree already drive the agency to an AAL that requires MFA, the question regarding personal information is only raised at this point.  That said, personal information release at all AALs should be considered when performing the risk assessment.  An important point at this step, the collection of personal information, if made available online, does not need to be validated or verified to require an AAL of 2 or higher.  Even self-asserted personal information requires account protection via MFA. Even though self-asserted information can be falsified, most users will provide accurrate information to benefit from the digital service.  As such, self-asserted data must be protected appropriately.</td> 
  </tr>
  
  </table>
</div>


#### <a name="IAL_CYOA"></a> 4.3.2 Selecting Identity Assurance Level

The IAL decision tree in [Figure 4-2](#63Sec4-Figure2) offers agencies a possible path to determine the most appropriate identity proofing requirements for their digital service offering. This analysis is not intended to be complete nor replace M-04-04 risk assessments or any other risk management process in use by the agency. Descriptions follow for specific steps that fall outside the required risk management process documented in M-04-04.

The IAL selection does not mean the digital service provider will need to perform the proofing themselves. More information of whether the agency can federate or not is provided in [Section 4.4](#toFedorNotToFed). 

<a name="63Sec4-Figure2"></a>
<div class="text-center" markdown="1">
![](sp800-63-3/media/IAL_CYOA.png)

**Figure 4-2 - Selecting IAL**
</div>


<div class="text-left" markdown="1">
<table style="width:100%">
  <tr>
    <td><img src="sp800-63/media/ial-step1.png"/></td>
  </tr>
  <tr>
   <td>The risk assessment and selection of IAL can be short circuited by answering this question first. If the service does not require any personal information in order to execute any digital transactions, the IAL of the system can be set to 1.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/ial-step2.png"/></td>
  </tr>
  <tr>
   <td>If personal information is needed, the relying party needs to determine if validated and verified attributes are required, or if self-asserted attributes are acceptable. If even a single validated and verified attribute is needed, then the provider will need to accept attributes that have been IAL2 or 3 proofed. Again, the selection of IAL can be short circuited to IAL1 if the agency can deliver the digital service with self-asserted attributes only.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/ial-step3.png"/></td>
  </tr>
  <tr>
   <td>At this point, the agency understands that some level of proofing is required. Step 3 is intended to look at the potential impacts of an identity proofing failure in order to determine if IAL2 or IAL3 is the most appropriate selection.  The primary identity proofing failure an agency may encounter is accepting a falsified identity as true, therefore providing a service or benefit to the wrong or inelligible person. In addition, proofing, when not required, or collecting more information than needed, is a risk in and of itself. Hence, obtaining verified attribute information when not needed is also considered an identity proofing failure. This step should identify if the agency answered Step 1 and 2 incorrectly, realizing they actually don't need personal information to deliver the service. Risk should be considered from the perspective of the organization and to the user, since one may not be negatively impacted while the other could be significantly harmed. The risk assessment process of M-04-04 and any agency specific risk management process should commence from this step.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/ial-step4.png"/></td>
  </tr>
  <tr>
   <td>Step 4 is intended to determine if the personal information required by the agency will ultimately resolve to a unique identity.  In other words, the agency needs to know the full identity of the individual accessing the digital service, and pseudonymous access, even with a few validated and verified attributes, is not possible. If the agency needs to uniquely identify the individual, the process can end.  However, the agency should consider if Step 5 is of value to them, as the acceptance of claims will reduce exposure to the risk of overcollecting and storing more personal information than is necessary.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/ial-step5.png"/></td>
  </tr>
  <tr>
   <td>Step 5 focuses on whether or not the digital service can be provided without having access to full attribute values.  This does not mean all attributes must be delivered as claims, but this step does ask the agency to look at each personal attribute they have determined they need, and identify which ones can suffice as claims and which ones need to be complete values. A federated environment is best suited for receiving claims, as the digital service provider is not in control of the attribute information to start with. If the application also performs all required identity proofing, claims may not make sense since full values are already under control of the digital service provider.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63/media/ial-step6.png"/></td>
  </tr>
  <tr>
   <td>If the agency has reached Step 6, claims should be used.  This step identifies the digital service as an excellent candidate for accepting federated attribute claims from a CSP (or multiple CSP's), since it has been determined that complete attribute values are not needed to deliver the digital service.</td> 
  </tr>
  </table>
</div>



#### <a name="FAL_CYOA"></a> 4.3.3 Selecting Federation Assurance Level

### <a name="toFedorNotToFed"></a> 4.4 Federation Consideratons

### 4.5. Acceptable IAL and AAL Combinations

[Table 3](#63ES-Table3) details valid combinations of IAL and AAL that may be established during the enrollment process:

<a name="63ES-Table3"></a>

<div class="text-center" markdown="1">

**Table 3.  Acceptable combinations of IAL and AAL**

</div>

| | IAL 1 | IAL 2 | IAL 3 |
|:-:|:-:|:-:|:-:|
| **AAL 1** | Allowed | **NO** | **NO** |
| **AAL 2** | Allowed | Allowed | See Note |
| **AAL 3** | Allowed | Allowed | Allowed |

> Note: AAL 2 capable authenticators SHALL be bound to credentials at IAL 2 enrollment since management (and often use) of those credentials is a release of personal data requiring multi-factor authentication. AAL 3 authenticators SHOULD be bound to IAL 3 credentials since they are frequently required for the high-sensitivity applications that require in-person identity proofing.
