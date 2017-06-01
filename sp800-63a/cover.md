<div class="text-right" markdown="1">

# <a name="800-63a"></a> DRAFT NIST Special Publication 800-63A

![](sp800-63-3/media/div-1.png)  

# Digital Identity Guidelines

### _Enrollment and Identity Proofing Requirements_

![](sp800-63-3/media/div-2.png)  

Paul A. Grassi  
James L. Fenton  

Privacy Authors:  

Naomi B. Lefkovitz    
Jamie M. Danker  

Usability Authors:  

Yee-Yin Choong    
Kristen K. Greene    
Mary F. Theofanos   

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

</div><div class="breaker text-right" markdown="1">

# DRAFT NIST Special Publication 800-63A

# Digital Identity Guidelines

###  Enrollment and Identity Proofing Requirements

Paul A. Grassi  
*Applied Cybersecurity Division  
Information Technology Laboratory*   

James L. Fenton  
*Altmode Networks  
Los Altos, CA*  

Privacy Authors:  

Naomi B. Lefkovitz  
*Applied Cybersecurity Division  
Information Technology Laboratory*    

Jamie M. Danker  
*National Protection and Programs Directorate  
Department of Homeland Security*    


Usability Authors:    

Yee-Yin Choong  
Kristen K. Greene  
Mary F. Theofanos  
*Information Access Division  
Information Technology Laboratory*  

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}


Month TBD 2017

![](sp800-63-3/media/commerce_logo.png)

U.S. Department of Commerce  
*Wilbur L. Ross, Jr., Secretary*  

National Institute of Standards and Technology  
*Kent Rochford, Acting NIST Director and Under Secretary of Commerce for Standards and
Technology*

</div>

<div class="breaker"/>

<div class="text-center" markdown="1">

### Authority

</div>

This publication has been developed by NIST in accordance with its statutory responsibilities under the Federal Information Security Modernization Act (FISMA) of 2014, 44 U.S.C. § 3551 et seq., Public Law  (P.L.) 113-283. NIST is responsible for developing information security standards and guidelines, including minimum requirements for federal information systems, but such standards and guidelines shall not apply to national security systems without the express approval of appropriate federal officials exercising policy authority over such systems. This guideline is consistent with the requirements of the Office of Management and Budget (OMB) Circular A-130.

Nothing in this publication should be taken to contradict the standards and guidelines made mandatory and binding on Federal agencies by the Secretary of Commerce under statutory authority. Nor should these guidelines be interpreted as altering or superseding the existing authorities of the Secretary of Commerce, Director of the OMB, or any other Federal official. This publication may be used by nongovernmental organizations on a voluntary basis and is not subject to copyright in the United States. Attribution would, however, be appreciated by NIST.

<div class="text-center" markdown="1">

National Institute of Standards and Technology Special Publication 800-63-3  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63-3, xxx pages (MonthTBD 2017)  
CODEN: NSPUE2

</div>

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

<div class="text-justify" markdown="1">
>Certain commercial entities, equipment, or materials may be identified in this document in order to describe an experimental procedure or concept adequately. Such identification is not intended to imply recommendation or endorsement by NIST, nor is it intended to imply that the entities, materials, or equipment are necessarily the best available for the purpose.
<br /><br />
>There may be references in this publication to other publications currently under development by NIST in accordance with its assigned statutory responsibilities. The information in this publication, including concepts and methodologies, may be used by federal agencies even before the completion of such companion publications. Thus, until each publication is completed, current requirements, guidelines, and procedures, where they exist, remain operative. For planning and transition purposes, federal agencies may wish to closely follow the development of these new publications by NIST.
<br /><br />
>Organizations are encouraged to review all draft publications during public comment periods and provide feedback to NIST. Many NIST cybersecurity publications, other than the ones noted above, are available at [http://csrc.nist.gov/publications/](http://csrc.nist.gov/publications/).
</div>

<div class="text-center" markdown="1">

**Comments on this publication may be submitted to dig-comments@nist.gov**    
All comments are subject to release under the Freedom of Information Act (FOIA).

National Institute of Standards and Technology  
Attn: Computer Security Division, Information Technology Laboratory  
100 Bureau Drive (Mail Stop 8930) Gaithersburg, MD 20899-8930  
Email: dig-comments@nist.gov
</div>

<div class="text-center" markdown="1">

### Reports on Computer Systems Technology

</div>

The Information Technology Laboratory (ITL) at the National Institute of
Standards and Technology (NIST) promotes the U.S. economy and public
welfare by providing technical leadership for the Nation's measurement
and standards infrastructure. ITL develops tests, test methods,
reference data, proof of concept implementations, and technical analyses
to advance the development and productive use of information technology.
ITL's responsibilities include the development of management,
administrative, technical, and physical standards and guidelines for the
cost-effective security and privacy of other than national
security-related information in Federal information systems. The Special
Publication 800-series reports on ITL's research, guidelines, and
outreach efforts in information system security, and its collaborative
activities with industry, government, and academic organizations.

<div class="text-center" markdown="1">

### Abstract

</div>

These guidelines provide technical requirements for Federal agencies
implementing digital identity services and are not intended to constrain the development or use of standards outside of this purpose. This guideline focuses on the enrollment and verification of an identity for use in digital authentication. Central to this is a process known as *identity proofing* in which an applicant provides evidence to a credential service provider (CSP) reliably identifying themselves, thereby allowing the CSP to assert that identification at a useful identity assurance level. This document defines technical requirements for each of three identity assurance levels. This publication supersedes corresponding sections of NIST SP 800-63-1 and SP 800-63-2.

<div class="text-center" markdown="1">

### Keywords

</div>

authentication; credential service provider; electronic authentication; digital authentication; electronic credentials; digital credentials; identity proofing; federation.

<div class="text-center" markdown="1">

### Acknowledgements

</div>

The authors would like to acknowledge the contributions and guidance of our international peers, including Adam Cooper, Alastair Treharne, and Julian White from the Cabinet Office, United Kingdom, and Tim Bouma from the Treasury Board of Canada Secretariat, Government of Canada. In addition, special thanks to the Federal Privacy Council's Digital Authentication Task Force for the contributions to the development of privacy requirements and considerations.

The authors would also like to acknowledge the thought leadership and innovation of the original authors: Donna F. Dodson, Elaine M. Newton, Ray A. Perlner, W. Timothy Polk, Sarbari Gupta, and Emad A. Nabbus.  Without their tireless efforts, we would not have had the incredible baseline from which to evolve 800-63 to the document it is today.

<div class="text-center" markdown="1">

### Requirements Notation and Conventions

</div>

The terms "SHALL" and "SHALL NOT" indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.

The terms "SHOULD" and "SHOULD NOT" indicate that among several possibilities one is recommended as particularly suitable, without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.

The terms "MAY" and "NEED NOT" indicate a course of action permissible within the limits of the publication.

The terms "CAN" and "CANNOT" indicate a possibility and capability, whether material, physical or causal or, in the negative, the absence of that possibility or capability.

<div class="breaker"/>

<div class="text-center" markdown="1">
## Table of Contents
</div>

[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. Identity Assurance Level Requirements](#sec4)

[5. Identity Resolution, Validation and Verification](#sec5)

[6. Derived Credentials](#sec6)

[7. Threats and Security Considerations](#sec7)

[8. Privacy Considerations](#sec8)

[9. Usability Considerations](#sec9)

[10. References](#references)