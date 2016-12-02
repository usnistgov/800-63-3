<div class="text-right" markdown="1">

# <a name="800-63-3"></a>DRAFT NIST Special Publication 800-63-3

# Digital Authentication Guideline

Paul A. Grassi  
Michael E. Garcia  
James L. Fenton

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

</div>

<div class="breaker text-right" markdown="1">

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

<div class="breaker"/>

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

### Trademark Information

{:/comment}

### <a name="notation"></a> Requirements Notation and Conventions

The terms “SHALL” and “SHALL NOT” indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.

The terms “SHOULD” and “SHOULD NOT” indicate that among several possibilities one is recommended as particularly suitable, without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.

The terms “MAY” and “NEED NOT” indicate a course of action permissible within the limits of the publication.

The terms “CAN” and “CANNOT” indicate a possibility and capability, whether material, physical or causal.

</div>

<div class="breaker"/>

## Executive Summary

Digital authentication is the process of establishing confidence in an identity digitally presented to an information system. Authentication establishes that the individual accessing the digital service is who they claim to be, and that this same individual is in control of the technologies used to authenticate.  It provides reasonable assurances that the person that accessed the service yesterday is the same person accessing the service today, and each subsequent time. Digital authentication presents a technical challenge because this process involves the authentication of individual people over an open network to access digital government services, where multiple opportunities for impersonation and other attacks exist.

These technical guidelines supplement OMB guidance, *E-Authentication Guidance for Federal Agencies* [[OMB M-04-04]](#M-04-04) and supersede NIST SP 800-63-1 and SP 800-63-2. The OMB guidance defines the required "level of identity assurance", herein referred to as "level of assurance", or LOA, best suited to avoid an authentication error. As the consequences of a potential authentication error become more serious, the required level of assurance increases. The OMB guidance provides agencies with possible impacts that could result from the risk of authentication errors for applications and transactions. OMB M-04-04 defines four LOAs, Levels 1 to 4, in terms of the confidence that an agency can attain that an authentication error may or may not occur. Level 1 is the lowest assurance level used primarily for low risk applications, and Level 4 is the highest used for the riskiest of online government digital services.

These guidelines support M-04-04, and the mitigation of possible negative impacts induced by an authentication error, by separating the individual elements of identity assurance into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authenticator Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included. These guidelines do not view LOA in the context of a single ordinal that drive all implementation specific requirements.  Rather, by combining appropriate business and privacy risk management side-by-side with mission need, agencies are encouraged to consider IAL, AAL, and FAL as distinct, not driven by a single LOA selection. [Section 5](#sec5) provides options that can support agency selection of the appropriate IAL, AAL and FAL combinations while adhering to OMB M-04-04 to protect all government digital services.

The components of identity assurance detailed in these guidelines are as follows:

* **IAL** refers to the robustness of the identity proofing process and the binding between one or more authenticators and the records pertaining to a specific individual.
* **AAL** refers to the robustness of the authentication process itself.
* **FAL** refers to the robustness of the assertion protocol utilized by a federation to communicate authentication and attribute information (if applicable) to a relying party.

The separation of these categories provides agencies significant flexibility in the identity solutions they choose and allows for privacy enhancing techniques to be a fundamental element of identity systems at any assurance level.  For example, these guidelines support scenarios that will allow an individual to remain pseudonymous even when strong, multifactor authenticators are used.  In addition, these guidelines encourage minimizing the collection of an individual's information by requiring federated identity providers to support a range of options for querying data, such as if a user is older than a certain age rather than querying the entire date of birth.

The market for identity services is componentized, allowing organizations and agencies to employ standards-based, pluggable identity solutions based on mission need.  No longer are identity solutions a monolith, where all functionality is provided by one system or vendor.  As such, SP 800-63 has been split into a suite of documents that stand alone based on the component service an agency requires. These documents may inform, but does not restrict or constrain, the development or use of standards for application outside of the Federal government, such as e-commerce transactions.  

Each document has adopted verbs that are internationally recognized in standards organizations as normative and requirements-based. For legibility, they are CAPITALIZED throughout the document for ease of identification.  For example, the use of SHALL is used to denote a mandatory requirement, while the use of SHOULD refers to a technique, technology, or process that is recommended but not mandatory.  For more details on the definitions of these terms see the [Requirements Notation and Conventions](#notation) at the beginning of each document.

These guidelines are organized as follows:

**SP 800-63-3 Digital Authentication Guideline**

This document provides an overview of general authentication frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _This document is informative._

[**SP 800-63A Enrollment and Identity Proofing**](#800-63a)

NIST SP 800-63-A deals with how an individual can prove their identity and become enrolled as a valid user within an identity system. It provides guidelines on processes by which an individual can enrolled and identity proofed in both remote and in-person scenarios. _This document contains both normative and informative material._

SP 800-63A sets requirements to achieve a given IAL. The three IALs reflect the options agencies may select based on their risk profile and the potential harm caused by an attacker successfully claiming the identity of another individual.  The IALs are as follows:

**IAL 1**:
At this level, there is no requirement for an applicant's identity to be proven.  Any attributes provided in conjunction with the authentication process are self-asserted.

**IAL 2**:
At IAL 2, the claimed identity is proven with evidence that supports the real-world existence of the claimed identity and identifies and verifies the person to whom the claimed identity belongs.  IAL 2 introduces the need for either remote or in-person identity proofing.  Attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.

**IAL 3**:
At Identity Assurance Level 3, in-person identity proofing is required. Identifying attributes must be verified by an authorized and trained representative of the CSP. As with IAL 2, attributes MAY be asserted by CSPs to RPs in support of pseudonymous identity with verified attributes.


[**SP 800-63B Authentication and Lifecycle Management**](#800-63b)

Digital authentication is the process of establishing confidence in user identities digitally presented to an information system. The robustness of this confidence is described by a categorization known as the AAL. NIST SP 800-63B addresses how an individual can securely authenticate to a Credential Service Provider (CSP) to access a (or set of) digital service.  _This document contains both normative and informative material._

The three AALs reflect the options agencies can select based on their risk profile and the potential harm caused by an attacker taking control of an authenticator and accessing their systems. The AALs are as follows:

**AAL 1** - AAL 1 provides some assurance that the claimant controls the authenticator registered to a subscriber. AAL 1 uses single-factor authentication using a wide range of available authentication technologies. Successful authentication requires that the claimant prove through a secure authentication protocol that he or she possesses and controls the authenticator.

**AAL 2** – AAL 2 provides high confidence that the claimant controls the authenticator registered to a subscriber. Two different authentication factors are required. Approved cryptographic techniques are required at AAL 2 and above.

**AAL 3** – AAL 3 provides very high confidence that the claimant controls the authenticator registered to a subscriber. Authentication at AAL 3 is based on proof of possession of a key through a cryptographic protocol. AAL 3 is like AAL 2 except that a "hard" cryptographic authenticator that also provides impersonation resistance is required.

[**SP 800-63C Federation and Assertions**](#800-63c)

NIST SP 800-63C provides guidelines on the use of federated identity architectures and assertions to convey the results of authentication processes to an agency application. In addition, this guideline offers privacy enhancing techniques to share information about a valid, authenticated user, as well as describing methods that allow for strong multifactor authentication while the individual remains pseudonymous to the digital service. _This document contains both normative and informative material._

The three FALs reflect the options agencies can select based on their risk profile and the potential harm caused by an attacker taking control of federated transactions. The FALs are as follows:

**FAL 1** - FAL 1 allows for the subscriber to enable the relying party (RP) to receive a bearer assertion. The assertion is signed by the IdP using approved cryptography.

**FAL 2** - FAL 2 adds the requirement that the assertion be encrypted using approved cryptography such that the RP is the only party that can decrypt it.

**FAL 3** - FAL 3 requires the subscriber to present proof of possession of a cryptographic key referenced in the assertion in addition to the assertion artifact itself. The assertion is signed by the IdP and encrypted to the RP using approved cryptography.

<div class="breaker"/>

## Table of Contents

[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. Digital Authentication Model](#sec4)

[5. Determining Levels of Assurance](#sec5)

[6. References](#references)

 
