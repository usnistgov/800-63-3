<a name="sec4"></a>

## 4. A New Approach to Levels of Assurance

OMB M-04-04 guides agencies to assess the potential impact resultant from an authentication as the method to determine an application or transaction overall level of assurance. In selecting an LOA, the ageny is required to identity proof and issue credentials as the exact same level.  For example, if the impact of an authentication error results in an application assessed at LOA 3, the agency must identity proof and credential at LOA 3.  However, in today's digital services, agencies should look at the impact that could result from an authentication error (the authenticator fails) AND an identity proofing error.  From the perspective of an identity proofing failure, there is really two dimensions:

*  The impact of providing a service to the wrong person (e.g. a fraudster successfully proofs as someone else).
*  The impact of excessive identity proofing (i.e. collecting more information about a person than is required to successfully provide the digital service.

Therefore, this guideline does not view an authentication error as a singleton.  Agencies should assess the risk of authentication and proofing errors separately in determining the appropriate technical solution that should be applied.  

**Need intro language to xALs**  

In selecting the appropriate assurance levels, the agency should assess the risk associated with online transactions, not the entire business process associated with an agency provided benefit or service.  For example, in the case of a census, extremely sensitive information is collected, but it is never made available online to the person after the information is submitted.  In this instance, it is important for the information to be carefully protected in backend systems, but there is no reason to identity proof or even authentication the user providing the information.  The online transaction is submission of the data only, while the entire business process may require a significant amount of data validation without ever needing to know if the correct person submitted the correct information regarding their family. In this scenario, there is no need for any xAL.  

Another example where xAL needs to be applied, but online transaction requirements should not be impacted by the end-to-end business process is a digital service that accepts resumes in order to apply for open positions.  In this use case, the digital service allows an individual to submit their resume and in subsequent visits to the site, query and update their resume.  Since the resume information is being provided in later sessions, and is personal information, the agency must select an appropriate AAL since authentication is required.  In this case, the requirements of EO13681 apply, driving the AAL to be at least level 2.  However, what should be done about identity proofing?  The entire business process of examining a resume and ultimately interviewing a person requires a significant amount of identity proofing.  The agencies needs to be confident that the job applicant/interviewee is in fact the subject of the online submitted resume. Yet this level of proofing is not required to actually submit the resume online.  The actual digital transaction doesn't require any identity proofing.  The resume could be submitted by the applicant, but may also be submitted by a surrogate of some sort.  Identity proofing the submitter would create more risk than required in the online system as excess personal information would be collected.  Therefore, the most appropriate IAL selection would be 1.  There is no need to identity proof the user to successfully complete the online transaction, nor is there any potential negative impact as a result of offering the online transaction if a proofing failure occurred.  Yet, there would be significant impact if the entire business process failed to correctly identity proof the person - a job may be offered to a fraudulent applicant - but that risk should not be applied holistically to the online system.

> In this use case, it is assumed the system allows surrogates.  If the use case is that the only person that can submit is the actual subject of the resume, then identity proofing requirements would be significantly different.  

<a name="63Sec4-Figure1"></a>
<div class="text-center" markdown="1">
![](sp800-63-3/media/IAL_CYOA.png)

**Figure 4-1 - Selecting IAL**
</div>


<a name="63Sec4-Figure2"></a>
<div class="text-center" markdown="1">
![](sp800-63-3/media/AAL_CYOA.png)

**Figure 4-2 - Selecting AAL**
</div>


### 5.5. Assurance Levels

The M-04-04 Level of Assurance (LOA) is determined by combining the discrete assurance level for each of the components of the architecture. [Table 4-1](#63Sec4-Table1) shows strict adherence to M-04-04 Level of Assurance, mapping corresponding Identity, Authenticator, and Federation Assurance Levels. 

<a name="63Sec4-Table1"></a>

<div class="text-center" markdown="1">

**Table 4-1.  Legacy M-04-04 Requirements**

</div>

| M-04-04 Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1| 1
| 2 | 2 | 2 or 3 |2
| 3 | 2 | 2 or 3 |2
| 4 | 3 | 3 |4

However, [Table 4-2](#63ES-Table2) shows the new requirements that are allowable for M-04-04 Level of Assurance, by combining IAL, AAL, and FAL based on agency need. Further details and normative requirements are provided in are provided in [SP 800-63A](sp800-63a.html), [SP 800-63B](sp800-63b.html), and [SP 800-63C](sp800-63c.html) respectively.

<a name="63Sec4-Table2"></a>

<div class="text-center" markdown="1">

**Table 4-2.  Recommended M-04-04 Requirements**

</div>

| M-04-04 Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1, 2 or 3 | 1, 2, 3, or 4
| 2 | 1 or 2 | 2 or 3 |2, 3, or 4
| 3 | 1 or 2 | 2 or 3 |2, 3, or 4
| 4 | 1, 2, or 3 | 3 |3 or 4

This mapping takes advantage of the ability to separate distinct identity elements per assurance level.  This allows an agency adopt multi-factor authentication (MFA) when identification of the individual identity is not required. Conversely, little or no identity proofing can be performed at the higher LOAs. For instance, to achieve M-04-04 LOA 3:

* The enrollment and identity proofing process would, at a minimum, use IAL 1 or 2 processes.
* The authenticator (or combination of authenticators) would have an AAL of 2 or higher.
* Authentication assertions (if used) would have an FAL of 2 or higher.

Agency mission need will assist in determining the acceptable IAL at a given LOA.  Since agencies should limit the collection of personal data in order to provide services and allow for strong pseudonymity, a specific IAL is not explicitly required for each LOA. For example, an agency may establish a "health tracker" application.  In line with the terms of [Executive Order 13681](#EO13681) requiring "...that all agencies making personal data accessible to citizens through digital applications require the use of multiple factors of authentication and an effective identity proofing process, as appropriate.", the agency could select LOA3 such that an AAL2 authenticator is required.  However, in this example, there may be no need for the agency system to know the true identity of the user.  In the past, the LOA3 assessment of data sensitivity would also require the agency to identity proof the user.  This is no longer necessary and the agency is encouraged in this case to not perform any identity proofing and allow the user of the health tracker system to be pseudonymous at IAL1.  The MFA authenticator at AAL2 or AAL3 will not leak any personal information because it is bound to an IAL 1 identity.

In the case of HSPD-12 and those federal employees that are required to obtain a Personal Identity Verification (PIV) smart card, the requirement is that agencies meet LOA4. This use case requires an authenticator at AAL3 **and** identity proofing at IAL 3.   

> Note: An agency can accept a higher assurance level than those required in the table above.  For example, in a federated transaction, an agency can accept an IAL3 identity if their application is assessed at IAL2.  The same holds true for authenticators; stronger authenticators can be used at RP's that have lower authenticator requirements.  However, RPs will ensure that these scenarios only occur in federated scenarios with appropriate privacy protections by the CSP to ensure that only the requested attributes are provided to the RP and that no personal information leaks from the authenticator or the assertion.  See [privacy requirements](./sp800-63c.html#sec9) in SP 800-63C for more details.    


> Note: Agencies are encouraged to consider each distinct element of assurance, therefore the notion of the 'low watermark' to determine LOA no longer applies.  An IAL1/AAL2 application should not be considered any less secure or privacy enhancing than an IAL2/AAL2 application.  The only difference between these applications is the amount of proofing required, which may not impact the security and privacy of each application. That said, if an agency incorrectly determines the xAL, security and privacy could very well be impacted.