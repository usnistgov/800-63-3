<div class="text-right" markdown="1">

# <a name="800-63c"></a> DRAFT NIST Special Publication 800-63C

# Digital Authentication Guideline (翻訳版)

### Federation and Assertions

Paul A. Grassi  
James L. Fenton  
Justin P. Richer  
Sarah K. Squire

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

# DRAFT NIST Special Publication 800-63C

# Digital Authentication Guideline

### Federation and Assertions

Paul A. Grassi  
*Applied Cybersecurity Division  
Information Technology Laboratory*

James L. Fenton  
*Altmode Networks  
Los Altos, CA*

Justin P. Richer  
*Bespoke Engineering  
Billerica, MA*

Sarah K. Squire  
*Engage Identity  
Seattle, WA*

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

National Institute of Standards and Technology Special Publication 800-63C  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63C, xxx pages (MonthTBD 2016)  
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

The Information Technology Laboratory (ITL) at the National Institute of Standards and Technology (NIST) promotes the U.S. economy and public welfare by providing technical leadership for the Nation’s measurement and standards infrastructure. ITL develops tests, test methods, reference data, proof of concept implementations, and technical analyses to advance the development and productive use of information technology. ITL’s responsibilities include the development of management, administrative, technical, and physical standards and guidelines for the cost-effective security and privacy of other than national security-related information in Federal information systems. The Special Publication 800-series reports on ITL’s research, guidelines, and outreach efforts in information system security, and its collaborative activities with industry, government, and academic organizations.

### Abstract

This document and its companion documents, SP 800-63-3, SP 800-63A, and SP 800-63B, provide technical and procedural guidelines to agencies for the implementation of federated identity systems and for assertions used by federations. This publication supersedes corresponding sections of NIST SP 800-63-1 and SP 800-63-2.

### Keywords

assertions; authentication; credential service provider;
digital authentication; electronic authentication; electronic credentials; federations.

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

### Executive Summary

> Under Construction  

## Table of Contents  

[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. Federation](#sec4)

[5. Assertion Strength](#sec5)

[6. Assertion Presentation](#sec6)

[7. Federation Assurance Levels](#fal)

[8. Security](#sec8)

[9. Privacy Requirements and Considerations](#sec9)

[10. Usability](#sec10)

[11. Assertion Examples](#sec11)

[12. References](#references)
