<div class="text-right" markdown="1">

# <a name="800-63c"></a> NIST Special Publication 800-63C

![](sp800-63-3/media/div-1.png)  

# Digital Identity Guidelines  

### _Federation and Assertions_

![](sp800-63-3/media/div-2.png)  

Paul A. Grassi  
Justin P. Richer  
Sarah K. Squire  
James L. Fenton  
Ellen M. Nadeau  

**Privacy Authors:**  
Naomi B. Lefkovitz    
Jamie M. Danker  

**Usability Authors:**  
Yee-Yin Choong      
Kristen K. Greene      
Mary F. Theofanos

This publication is available free of charge from:  
https://doi.org/10.6028/NIST.SP.800-63c  

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

</div><div class="breaker text-right" markdown="1">

# NIST Special Publication 800-63C

# Digital Identity Guidelines

### Federation and Assertions

<table class="authors">
  <tr>
    <td>Paul A. Grassi<br>Ellen M. Nadeau<br><i>Applied Cybersecurity Division</i><br><i>Information Technology Laboratory</i></td>
    <td>James L. Fenton<br><i>Altmode Networks</i><br><i>Los Altos, Calif.</i></td>    
  </tr>
  <tr>
  <td/>
      <td>Justin P. Richer<br>Sarah K. Squire<br><i>Bespoke Engineering</i><br><i>Billerica, Mass.</i></td>
      <td>&nbsp;</td>
  </tr>
  <tr>
    <td><strong>Privacy Authors:</strong><br>Naomi B. Lefkovitz<br><i>Applied Cybersecurity Division</i><br><i>Information Technology Laboratory</i><br><br>Jamie M. Danker<br><i>National Protection and Programs Directorate</i><br><i>Department of Homeland Security</i></td>
    <td><strong>Usability Authors:</strong><br>Yee-Yin Choong<br>Kristen K. Greene<br><i>Information Access Division</i><br><i>Information Technology Laboratory</i><br><br>Mary F. Theofanos<br><i>Office of Data and Informatics</i><br><i>Material Measurement Laboratory</i></td>
  </tr>
</table>

This publication is available free of charge from:  
https://doi.org/10.6028/NIST.SP.800-63c  


June 2017

![](sp800-63-3/media/commerce_logo.png)

U.S. Department of Commerce  
*Wilbur L. Ross, Jr., Secretary*  

National Institute of Standards and Technology  
*Kent Rochford, Acting NIST Director and Under Secretary of Commerce for Standards and
Technology*

</div>

<div class="text-center" markdown="1">

### Authority

</div>

This publication has been developed by NIST in accordance with its statutory responsibilities under the Federal Information Security Modernization Act (FISMA) of 2014, 44 U.S.C. § 3551 et seq., Public Law  (P.L.) 113-283. NIST is responsible for developing information security standards and guidelines, including minimum requirements for federal information systems, but such standards and guidelines shall not apply to national security systems without the express approval of appropriate federal officials exercising policy authority over such systems. This guideline is consistent with the requirements of the Office of Management and Budget (OMB) Circular A-130.

Nothing in this publication should be taken to contradict the standards and guidelines made mandatory and binding on federal agencies by the Secretary of Commerce under statutory authority. Nor should these guidelines be interpreted as altering or superseding the existing authorities of the Secretary of Commerce, Director of the OMB, or any other federal official. This publication may be used by nongovernmental organizations on a voluntary basis and is not subject to copyright in the United States. Attribution would, however, be appreciated by NIST.

<div class="text-center" markdown="1">

National Institute of Standards and Technology Special Publication 800-63C  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63C, 48 pages (June 2017)  
CODEN: NSPUE2



This publication is available free of charge from:  
https://doi.org/10.6028/NIST.SP.800-63c  

</div>

<div class="text-justify" markdown="1">
>Certain commercial entities, equipment, or materials may be identified in this document in order to describe an experimental procedure or concept adequately. Such identification is not intended to imply recommendation or endorsement by NIST, nor is it intended to imply that the entities, materials, or equipment are necessarily the best available for the purpose.
<br /><br />
>There may be references in this publication to other publications currently under development by NIST in accordance with its assigned statutory responsibilities. The information in this publication, including concepts and methodologies, may be used by federal agencies even before the completion of such companion publications. Thus, until each publication is completed, current requirements, guidelines, and procedures, where they exist, remain operative. For planning and transition purposes, federal agencies may wish to closely follow the development of these new publications by NIST.
<br /><br />
>Organizations are encouraged to review all draft publications during public comment periods and provide feedback to NIST. Many NIST cybersecurity publications, other than the ones noted above, are available at [http://csrc.nist.gov/publications/](http://csrc.nist.gov/publications/).
</div>

<div class="text-center" markdown="1">
**Comments on this publication may be submitted to:**    

National Institute of Standards and Technology  
Attn: Applied Cybersecurity Division, Information Technology Laboratory  
100 Bureau Drive (Mail Stop 2000) Gaithersburg, MD 20899-2000  
Email: <dig-comments@nist.gov>

All comments are subject to release under the Freedom of Information Act (FOIA).

</div>

<div class="text-center" markdown="1">

### Reports on Computer Systems Technology

</div>

The Information Technology Laboratory (ITL) at the National Institute of Standards and Technology (NIST) promotes the U.S. economy and public welfare by providing technical leadership for the Nation's measurement and standards infrastructure. ITL develops tests, test methods, reference data, proof of concept implementations, and technical analyses to advance the development and productive use of information technology. ITL's responsibilities include the development of management, administrative, technical, and physical standards and guidelines for the cost-effective security and privacy of other than national security-related information in federal information systems. The Special Publication 800-series reports on ITL's research, guidelines, and outreach efforts in information system security, and its collaborative activities with industry, government, and academic organizations.

<div class="text-center" markdown="1">

### Abstract

</div>

This document and its companion documents, SP 800-63, SP 800-63A, and SP 800-63B, provide technical and procedural guidelines to agencies for the implementation of federated identity systems and for assertions used by federations. This publication supersedes corresponding sections of SP 800-63-2.

These guidelines provide technical requirements for federal agencies implementing digital identity services and are not intended to constrain the development or use of standards outside of this purpose. This guideline focuses on the use of federated identity and the use of assertions to implement identity federations. Federation allows a given credential service provider to provide authentication and (optionally) subscriber attributes to a number of separately-administered relying parties. Similarly, relying parties may use more than one credential service provider.

<div class="text-center" markdown="1">

### Keywords

</div>

assertions; authentication; credential service provider;
digital authentication; electronic authentication; electronic credentials; federations.

<div class="text-center" markdown="1">

### Acknowledgements

</div>

The authors gretefully acknowledge Kaitlin Boeckl for her artistic graphics contributions to all vulumed in the SP 800-63 suite and the contributions of our many reviewers, including Joni Brennan from the Digital ID & Authentication Council of Canada (DIACC), Kat Megas and Ben Piccarreta from NIST, and Christine Abruzzi and Danna Gabel O'Rourke from Deloitte & Touche LLP.

The authors would also like to acknowledge the thought leadership and innovation of the original authors: Donna F. Dodson, Elaine M. Newton, Ray A. Perlner, W. Timothy Polk, Sarbari Gupta, and Emad A. Nabbus. Without their tireless efforts, we would not have had the incredible baseline from which to evolve 800-63 to the document it is today. In addition, special thanks to the Federal Privacy Council's Digital Authentication Task Force for the contributions to the development of privacy requirements and considerations.

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

[1. Purpose](#purpose)

[2. Introduction](#introduction)

[3. Definitions and Abbreviations](#definitions)

[4. Federation Assurance Levels](#fal)

[5. Federation](#federation)

[6. Assertions](#assertions)

[7. Assertion Presentation](#presentation)

[8. Security](#security)

[9. Privacy Requirements and Considerations](#privacy)

[10. Usability Considerations](#usability)

[11. Assertion Examples](#examples)

[12. References](#references)
