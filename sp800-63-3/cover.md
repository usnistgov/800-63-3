<div class="text-right" markdown="1">

# <a name="800-63-3"></a>DRAFT NIST Special Publication 800-63-3

# Digital Authentication Guideline

Paul A. Grassi  
James L. Fenton

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

# DRAFT NIST Special Publication 800-63-3

# Digital Authentication Guideline

Paul A. Grassi  
*Applied Cybersecurity Division  
Information Technology Laboratory*

James L. Fenton  
*Altmode Networks  
Los Altos, CA*

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}


Month TBD 2016

![](sp800-63-3/media/commerce_logo.png)

U.S. Department of Commerce  
*Penny Pritzker, Secretary*

National Institute of Standards and Technology  
*Willie E. May, Under Secretary of Commerce for Standards and
Technology and Director*

</div>

<div class="text-center" markdown="1">

### Authority

This publication has been developed by NIST in accordance with its statutory responsibilities under the Federal Information Security Modernization Act (FISMA) of 2014, 44 U.S.C. § 3541 et seq., Public Law  (P.L.) 113-283. NIST is responsible for developing information security standards and guidelines, including minimum requirements for federal information systems, but such standards and guidelines shall not apply to national security systems without the express approval of appropriate federal officials exercising policy authority over such systems. This guideline is consistent with the requirements of the Office of Management and Budget (OMB) Circular A-130.

Nothing in this publication should be taken to contradict the standards and guidelines made mandatory and binding on Federal agencies by the Secretary of Commerce under statutory authority. Nor should these guidelines be interpreted as altering or superseding the existing authorities of the Secretary of Commerce, Director of the OMB, or any other Federal official. This publication may be used by nongovernmental organizations on a voluntary basis and is not subject to copyright in the United States. Attribution would, however, be appreciated by NIST.


National Institute of Standards and Technology Special Publication 800-63-3  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63-3, xxx pages (MonthTBD 2016)  
CODEN: NSPUE2


{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}


>Certain commercial entities, equipment, or materials may be identified in this document in order to describe an experimental procedure or concept adequately. Such identification is not intended to imply recommendation or endorsement by NIST, nor is it intended to imply that the entities, materials, or equipment are necessarily the best available for the purpose.
There may be references in this publication to other publications currently under development by NIST in accordance with its assigned statutory responsibilities. The information in this publication, including concepts and methodologies, may be used by federal agencies even before the completion of such companion publications. Thus, until each publication is completed, current requirements, guidelines, and procedures, where they exist, remain operative. For planning and transition purposes, federal agencies may wish to closely follow the development of these new publications by NIST.
Organizations are encouraged to review all draft publications during public comment periods and provide feedback to NIST. Many NIST cybersecurity publications, other than the ones noted above, are available at [http://csrc.nist.gov/publications](http://csrc.nist.gov/publications).  

{::comment}

**Comments on this publication may be submitted to eauth-comments@nist.gov  
Public comment period: Month Day, YYYY through Month Day, YYYY**  
All comments are subject to release under the Freedom of Information Act (FOIA).

National Institute of Standards and Technology  
Attn: Computer Security Division, Information Technology Laboratory  
100 Bureau Drive (Mail Stop 8930) Gaithersburg, MD 20899-8930  
Email: <eauth-comments@nist.gov>

{:/comment}

### Reports on Computer Systems Technology

The Information Technology Laboratory (ITL) at the National Institute of
Standards and Technology (NIST) promotes the U.S. economy and public
welfare by providing technical leadership for the Nation’s measurement
and standards infrastructure. ITL develops tests, test methods,
reference data, proof of concept implementations, and technical analyses
to advance the development and productive use of information technology.
ITL’s responsibilities include the development of management,
administrative, technical, and physical standards and guidelines for the
cost-effective security and privacy of other than national
security-related information in Federal information systems. The Special
Publication 800-series reports on ITL’s research, guidelines, and
outreach efforts in information system security, and its collaborative
activities with industry, government, and academic organizations.

### Abstract

This recommendation, along with accompanying recommendations in the SP 800-63 document set, provide technical guidelines for Federal agencies
implementing digital authentication and is not intended to constrain
the development or use of standards outside of this purpose. The
recommendation covers remote authentication of users (such as employees,
contractors, or private individuals) interacting with government IT
systems over open networks. It defines technical requirements for each
of four levels of assurance in the areas of identity proofing,
registration, authenticators, management processes, authentication protocols and
related assertions. This publication supersedes NIST SP 800-63-1 and SP 800-63-2.

### Keywords

authentication; authentication assurance; authenticator; assertions; credential service provider;
digital authentication; digital credentials; identity proofing;
passwords; PKI.

### Acknowledgements

The authors would like to acknowledge the thought leadership and innovation of the original authors: Donna F. Dodson, Elaine M. Newton, Ray A. Perlner, W. Timothy Polk, Sarbari Gupta, and Emad A. Nabbus.  Without their tireless efforts, we would not have had the incredible baseline from which to evolve 800-63 to the document it is today. 

### Audience

### Compliance with NIST Standards and Guidelines

### Conformance Testing

{::comment}

### Note to Reviewers

### Note to Readers

{:/comment}

### Trademark Information

### Requirements Notation and Conventions

The terms “SHALL” and “SHALL NOT” indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.

The terms “SHOULD” and “SHOULD NOT” indicate that among several possibilities one is recommended as particularly suitable, without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.

The terms “MAY” and “NEED NOT” indicate a course of action permissible within the limits of the publication.

The terms “CAN” and “CANNOT” indicate a possibility and capability, whether material, physical or causal.

</div>

## Executive Summary

Digital authentication is the process of establishing confidence in user identities digitally presented to an information system. Digital authentication presents a technical challenge when this process involves the authentication of individual people over an open network for the purpose of digital government and commerce. 

The suite of SP 800-63-3 documents provides technical guidelines to agencies to allow an individual to authenticate his or her identity to a Federal digital service.  This document may inform but does not restrict or constrain the development or use of standards for application outside of the Federal government, such as e-commerce transactions. These guidelines address only traditional, widely implemented methods for digital authentication, based on secrets. With these methods, the individual to be authenticated proves that he or she knows or possesses a valid authenticator or combination of authenticators.

These technical guidelines supplement OMB guidance, *E-Authentication
Guidance for Federal Agencies* [[OMB M-04-04]](#M-04-04) and
supersede NIST SP 800-63-1 and SP 800-63-2. OMB M-04-04 defines four levels of assurance, Levels 1 to 4, in terms of the consequences of authentication errors and misuse of credentials. Level 1 is the lowest assurance level, and Level 4 is the highest. The OMB guidance defines the required level of identity assurance in terms of the likely consequences of an authentication error. As the consequences of an authentication error become more serious, the required level of assurance increases. The OMB guidance provides agencies with the criteria for determining the level of identity assurance required for specific applications and transactions, based on the risks and their likelihood of occurrence of each application or transaction.

OMB guidance outlines a five-step process by which agencies should meet their digital authentication assurance requirements:

1.  Conduct a risk assessment of the government system.

2.  Map identified risks to the appropriate assurance level.

3.  Select technology based on digital authentication technical guidance.

4.  Validate that the implemented system has met the required
    assurance level.

5.  Periodically reassess the information system to determine technology refresh requirements.

This document suite provides guidelines for implementing the third step of the above process.  A new approach for digital authentication solutions is required by these guidelines, separating the individual elements of identity assurance into discrete, component parts. For non-federated systems, agencies will select and combine two (2) individual components, referred to as *Identity Assurance Level (IAL)* and *Authenticator Assurance Level (AAL)*. For federated systems, a 
third component, *Federation Assurance Level (FAL)*, is required. 

* IAL refers to the robustness of the identity proofing process and the binding between an authenticator and the records pertaining to a specific individual. 
* AAL refers to the robustness of the authentication process itself.
* FAL refers to the robustness of the assertion protocol utilized by the federation to communicate authentication and attribute information (if applicable) to a relying party.

The separation of these metrics supports applications requiring strong authentication that may be pseudonymous, and the separation of authenticator issuance from the establishment of credentials binding those authenticators to individuals.

Accordingly, with this revision, SP 800-63 has been split into a family of documents organized as follows:

- SP 800-63-3 *Digital Authentication Guideline* - Provides guidance on general authentication issues and for using authenticators, credentials, and assertions together in an information system.

- SP 800-63A *Enrollment and Identity Proofing* - Deals with the processes by which a credential, and authenticator(s) associated with that credential, can be bound to a specific individual. This typically happens when that individual is enrolled in an identity system, through the identity proofing process.

- SP 800-63B *Authentication and Lifecycle Management* - provides guidance on the selection, use, and management of authenticators (formerly called *tokens*) to authenticate a remote subscriber to an identity system at specified authenticator assurance levels.

- SP 800-63C *Federation and Assertions* - Provides guidance on the use of federated identity and assertions to convey the results of authentication processes to a relying party.


### IAL and AAL Summary

A summary of each of the identity and authenticator assurance levels is provided below.

**Identity Assurance Level 1** – At this level, attributes provided in conjunction with the authentication process, if any, are self-asserted.

**Identity Assurance Level 2** – IAL 2 introduces the need for either remote or in-person identity proofing. IAL 2 requires identifying attributes to have been verified in person or remotely using, at a minimum, the procedures given in [SP 800-63A](sp800-63a.html).

**Identity Assurance Level 3** – At IAL 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized representative of the CSP through examination of physical documentation as described in [SP 800-63A](sp800-63a.html).

**Authenticator Assurance Level 1** - AAL 1 provides single factor digital authentication, giving some assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. AAL 1 allows a wide range of available authentication technologies to be employed and requires only a single authentication factor to be used. It also permits the use of any of the authentication methods of higher authenticator assurance levels. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.

**Authenticator Assurance Level 2** – AAL 2 provides higher assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data. Two different authentication factors are required. Various types of authenticators, including multi-factor Software Cryptographic Authenticators, may be used as described in [SP 800-63B](sp800-63b.html). AAL 2 also permits any of the authentication methods of AAL 3. AAL 2 authentication requires cryptographic mechanisms that protect the primary authenticator against compromise by the protocol threats for all threats at AAL 1 as well as verifier impersonation attacks. Approved cryptographic techniques are required for all assertion protocols used at AAL 2 and above.

**Authenticator Assurance Level 3** – AAL 3 is intended to provide the highest practical digital authentication assurance. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is similar to AAL 2 except that only “hard” cryptographic authenticators are allowed. The authenticator is required to be a hardware cryptographic module validated at Federal Information Processing Standard (FIPS) 140 Level 2 or higher overall with at least FIPS 140 Level 3 physical security. AAL 3 authenticator requirements can be met by using the PIV authentication key of a FIPS 201 compliant Personal Identity Verification (PIV) Card.

### M-04-04 Levels of Assurance Requirements


The following table shows strict adherence to M-04-04 Level of Assurance, mapping corresponding Identity, Authenticator, and Federation Assurance Levels. 


| Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1| TBD
| 2 | 2 | 2 or 3 |TBD
| 3 | 2 | 2 or 3 |TBD
| 4 | 3 | 3 |TBD

However, the table below shows the new requirements that are allowable for M-04-04 Level of Assurance, by combining IAL, AAL, and FAL based on agency need. Further details and normative requirements are provided in are provided in [SP 800-63A](../sp800-63a.md), [SP 800-63B](../sp800-63b.md), and [SP 800-63C](../sp800-63c.md) respectively.


| Level of Assurance (LOA) | Identity Assurance Level (IAL)| Authenticator Assurance Level (AAL) | Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:|:------------------------:|:------------------------:|
| 1 | 1 | 1, 2 or 3 | TBD
| 2 | 1 or 2 | 2 or 3 |TBD
| 3 | 1 or 2 | 2 or 3 |TBD
| 4 | 1, 2 or 3 | 3 |TBD

This mapping takes advantage of the ability to separate distinct identity elements per assurance level.  For example, an agency is allowed to adopt multi-factor authentication (MFA) at LOA1. Conversely, little or no identity proofing can be performed at the higher LOAs.  

Agency mission need will assist in determining the acceptable IAL at a given LOA.  Since agencies should limit the collection of personal data in order to provide services and allow for strong pseudonymity, a specific IAL is not explicitly required for each LOA. For example, an agency may establish a "health tracker" application.  In line with the terms of [Executive Order 13681](#EO13681) requiring "...that all agencies making personal data accessible to citizens through digital applications require the use of multiple factors of authentication and an effective identity proofing process, as appropriate.", the agency could select LOA3 such that an AAL2 authenticator is required.  However, in this example, there may be no need for the agency system to know the true identity of the user.  In the past, the LOA3 assessment of data sensitivity would also require the agency to identity proof the user.  This is no longer necessary and the agency is encouraged in this case to not perform any identity proofing and allow the user of the health tracker system to be pseudonymous at IAL1.  The MFA authenticator at AAL2 or AAL3 will not leak any personal information because it is bound to an IAL 1 identity.

In the case of federal employees, bound by HSPD-12 and required to obtain a Personal Identity Verification (PIV) smart card, the requirement is that agencies meet LOA4. The HSPD-12 use case requires an authenticator at AAL3 **and** identity proofing at IAL 3.   

>Important Note: An agency can accept a higher assurance level than those required in the table above.  For example, in a federated transaction, an agency can accept an IAL3 identity if their application is assessed at IAL2.  The same holds true for authenticators; stronger authenticators can be used at RP's that have lower authenticator requirements.  However, RPs will ensure that these scenarios only occur in federated scenarios with appropriate privacy protections by the CSP to ensure that only the requested attributes are provided to the RP and that no personal information leaks from the authenticator or the assertion.  See [privacy requirements](../sp800-63c/sec8_privacy.md) in SP 800-63C for more details.   
 
### Acceptable IAL and AAL Combinations

The following table details valid combinations of IAL and AAL that may be established during the enrollment process:

| | IAL 1 | IAL 2 | IAL 3 |
|:-:|:-:|:-:|:-:|
| **AAL 1** | Allowed | **NO** | **NO** |
| **AAL 2** | Allowed | Allowed | See Note |
| **AAL 3** | Allowed | Allowed | Allowed |

Note: AAL 2 capable authenticators MUST be bound to credentials at IAL 2 enrollment since management (and often use) of those credentials is a release of personal data requiring multi-factor authentication. AAL 3 authenticators SHOULD be bound to IAL 3 credentials since they are frequently required for the high-sensitivity applications that require in-person identity proofing.

In limited situations, a given transaction requiring IAL 2 MAY be able to authenticate at AAL 1 when personal data is not made accessible to the subscriber (per Executive Order 13681) and the other risk and sensitivity requirements of M-04-04 are satisfied.

## Table of Contents

[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. Digital Authentication Model](#sec4)

[5. References](#references)

 
