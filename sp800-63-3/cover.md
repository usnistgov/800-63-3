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
Michael E. Garcia  
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

{:/comment}

### Trademark Information

### Requirements Notation and Conventions

The terms “SHALL” and “SHALL NOT” indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.

The terms “SHOULD” and “SHOULD NOT” indicate that among several possibilities one is recommended as particularly suitable, without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.

The terms “MAY” and “NEED NOT” indicate a course of action permissible within the limits of the publication.

The terms “CAN” and “CANNOT” indicate a possibility and capability, whether material, physical or causal.

</div>

<div class="breaker"/>

## Executive Summary

Digital authentication is the process of establishing confidence in user identities digitally presented to an information system. Digital authentication presents a technical challenge when this process involves the authentication of individual people over an open network for the purpose of digital government and commerce.

The suite of SP 800-63-3 documents provides technical guidelines to agencies to allow an individual to authenticate his or her identity to a Federal digital service.  This document may inform but does not restrict or constrain the development or use of standards for application outside of the Federal government, such as e-commerce transactions. These guidelines address only traditional, widely implemented methods for digital authentication, based on secrets. With these methods, the individual to be authenticated proves that he or she knows or possesses a valid authenticator or combination of authenticators.

These technical guidelines supplement OMB guidance, *E-Authentication
Guidance for Federal Agencies* [[OMB M-04-04]](#M-04-04) and
supersede NIST SP 800-63-1 and SP 800-63-2. OMB M-04-04 defines four levels of assurance, Levels 1 to 4, in terms of the consequences of authentication errors and misuse of credentials. Level 1 is the lowest assurance level, and Level 4 is the highest. The OMB guidance defines the required "level of identity assurance", herein referred to as "level of assurance", in terms of the likely consequences of an authentication error. As the consequences of an authentication error become more serious, the required level of assurance increases. The OMB guidance provides agencies with the criteria for determining the level of assurance required for specific applications and transactions, based on the risks and their likelihood of occurrence of each application or transaction.

In addition to the OMB guidance, [Section 4](#sec4) provides additional information that can guide agencies through the selection of the the assurance levels detailed in this guideline.

A new approach for digital authentication solutions is required by these guidelines, separating the individual elements of identity assurance into discrete, component parts. For non-federated systems, agencies will select and combine two individual components, referred to as *Identity Assurance Level (IAL)*  and *Authenticator Assurance Level (AAL)*. For federated systems, a 
third component, *Federation Assurance Level (FAL)*, is required.

* IAL refers to the robustness of the identity proofing process and the binding between an authenticator and the records pertaining to a specific individual.
* AAL refers to the robustness of the authentication process itself.
* FAL refers to the robustness of the assertion protocol utilized by the federation to communicate authentication and attribute information (if applicable) to a relying party.

The separation of these metrics supports applications requiring strong authentication that may be pseudonymous, and the separation of authenticator issuance from the establishment of credentials binding those authenticators to individuals.

Accordingly, with this revision, SP 800-63 has been split into a suite of documents organized as follows:

- SP 800-63-3 *Digital Authentication Guideline* - Provides guidelines on general authentication issues and for using authenticators, credentials, and assertions together in an information system.

- SP 800-63A *Enrollment and Identity Proofing* - Deals with the processes by which a credential, and authenticator(s) associated with that credential, can be bound to a specific individual. This typically happens when that individual is enrolled in an identity system, through the identity proofing process.

- SP 800-63B *Authentication and Lifecycle Management* - provides guidelines on the selection, use, and management of authenticators (formerly called *tokens*) to authenticate a remote subscriber to an identity system at specified authenticator assurance levels.

- SP 800-63C *Federation and Assertions* - Provides guidelines on the use of federated identity and assertions to convey the results of authentication processes to a relying party.

<div class="breaker"/>

## Table of Contents

[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. A New Approach to Levels of Assurance](#sec4)

[5. Digital Authentication Model](#sec5)

[6. References](#references)

 
