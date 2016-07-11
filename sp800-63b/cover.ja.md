<div class="text-right" markdown="1">

# <a name="800-63b"></a> DRAFT NIST Special Publication 800-63B

# Digital Authentication Guideline (翻訳版)

### Authentication and Lifecycle Management

Paul A. Grassi  
Elaine M. Newton  
Ray A. Perlner  
Andrew R. Regenscheid  
William E. Burr  
James L. Fenton  
Justin P. Richer

{::comment}

This publication is available free of charge from:
http://dx.doi.org/10.6028/NIST.SP.XXX  

{:/comment}

![](sp800-63-3/media/csd.png)  
![](sp800-63-3/media/nist_logo.png)

# DRAFT NIST Special Publication 800-63B

# Digital Authentication Guideline (翻訳版)

### Authentication and Lifecycle Management

Paul A. Grassi  
*Applied Cybersecurity Division  
Information Technology Laboratory*

Elaine M. Newton  
*Office of the Director  
Information Technology Laboratory*

Ray A. Perlner  
*Computer Security Division  
Information Technology Laboratory*

Andrew R. Regenscheid  
*Computer Security Division  
Information Technology Laboratory*

William E. Burr  
*Dakota Consulting, Inc.  
Silver Spring, MD*

James L. Fenton  
*Altmode Networks  
Los Altos, CA*

Justin P. Richer  
*Bespoke Engineering  
Billerica, MA*

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


National Institute of Standards and Technology Special Publication 800-63B  
Natl. Inst. Stand. Technol. Spec. Publ. 800-63B, xxx pages (MonthTBD 2016)  
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
Email: <eauth-comment@nist.gov>


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

<!--### Abstract-->

### 概要

<!--This document and its companion documents, SP 800-63-3, SP 800-63A, and SP 800-63C, provide technical and procedural guidelines to agencies implementing electronic authentication to choose and implement effective authentication processes based on risk. The recommendation covers remote authentication of users (such as employees, contractors, or private individuals) interacting with government IT systems over open networks. It defines technical requirements for each
of the three authenticator assurance levels. This publication supersedes corresponding sections of NIST SP 800-63-1 and SP 800-63-2.-->

本書及び付随文書であるSP 800-63-3、SP 800-63A、SP 800-63Cは、電子的な認証を実装する機関が、リスクに基づいて効果的な認証プロセスを選択、実装する際の技術的及び手続き上の指針を提供する。


<!--### Keywords-->

### キーワード

<!--authentication; credential service provider; digital authentication; digital credentials; electronic authentication; electronic credentials.-->

認証; クレデンシャルサービスプロバイダ; デジタル認証; デジタルクレデンシャル; 電子的認証; 電子的クレデンシャル

<!--### Acknowledgements-->

### 謝辞

The authors would like to acknowledge the thought leadership and innovation of the original authors: Donna F. Dodson, W. Timothy Polk, Sarbari Gupta, and Emad A. Nabbus.  Without their tireless efforts, we would not have had the incredible baseline from which to evolve 800-63 to the document it is today.

### Audience

### Compliance with NIST Standards and Guidelines

### Conformance Testing

{::comment}

### Note to Reviewers

### Note to Readers

{:/comment}

### Trademark Information

<!--### Requirements Notation and Conventions-->

### 要求記法および規則

<--The terms “SHALL” and “SHALL NOT” indicate requirements to be followed strictly in order to conform to the publication and from which no deviation is permitted.-->
「SHALL(するものとする)」及び「SHALL NOT(しないものとする)」というキーワードは、刊行物に厳密に従うことを要求しており、内容と異なってはならない。


<!--The terms “SHOULD” and “SHOULD NOT” indicate that among several possibilities one is recommended as particularly suitable, without mentioning or excluding others, or that a certain course of action is preferred but not necessarily required, or that (in the negative form) a certain possibility or course of action is discouraged but not prohibited.-->

キーワード「SHOULD(すべきである)」及び「SHOULD NOT(すべきではない)」は、いくつかある選択肢の中で特定の推奨があることを示しており、他の選択肢については言及も除外もしない。ある行動指針を推奨するが、必須であることまでは要求しない。(否定の意味では)ある選択肢または行動指針を非推奨するが、禁止はしない。



<!--The terms “MAY” and “NEED NOT” indicate a course of action permissible within the limits of the publication.-->

キーワード「MAY(してもよい)」及び「NEED NOT(しなくてよい)」は、刊行物の範囲において、行動指針が許容できることを示す。


<!--The terms “CAN” and “CANNOT” indicate a possibility and capability, whether material, physical or causal.-->

キーワード「CAN(できる)」及び「CANNOT(できない)」は、可能性や、能力があることを示す。その対象が物理的か一時的かにはかかわらない。

</div>

<!--## Executive Summary-->

## 全体概要

<!--Digital authentication is the process of establishing confidence that a given claimant is the same as a subscriber that has previously authenticated. The robustness of this confidence is described by categorization known as the Authenticator Assurance Level (AAL). The separation of AAL from Identity Assurance Level (IAL), described in SP 800-63A, better supports applications requiring strong authentication that may be pseudonymous. The separation of authenticator issuance from the establishment of credentials binding those authenticators to individuals provides additional flexibility in the enrollment and identity proofing process.-->

デジタル認証は、与えられた要求者と以前認証を行った加入者とが同一である、という確からしさを証明するためのプロセスである。この確からしさの堅牢性については、認証器信頼レベル(Authenticator Assurance Level、以下AAL)<!--TODO-->として知られている分類を用いて表される。AALはsp 800-63Aにおいてアイデンティティ信頼レベル(Identity Assurance Level、以下IAL)<!--TODO-->と区別される。これはより高いAALをサポートするようなアプリケーションでは、仮名を用いた高度な認証を要求するようなことがあるかもしれないためである。

<!--This guideline addresses how an individual, known as a claimant, can securely authenticate to a Credential Service Provider to establish the context for a remote digital interaction.-->

本ガイドラインは、要求者としての個人がどのようにクレデンシャル・サービス・プロバイダ(Crendential Service Provider)に対してセキュアな認証を行い、遠隔で行われるデジタルな対話のためのコンテキストを確立するか、という点に取り組むものである。

<!--The three AALs reflect the options agencies will select based on their risk profile and the potential harm caused by an invalid or fraudulent user accessing their systems. The AALs are as follows:-->

3つのAALは、システムに対する不正・詐欺的なユーザアクセスによって生じるリスクや損害に基づいて、各機関が選びうる選択肢を示している。各AALは次の通り：

<!--
**AAL 1**: AAL 1 requires single factor authentication, giving some assurance that the same claimant who participated in previous transactions is accessing the protected transaction or data.
-->
**AAL 1**: ALL 1は、単一要素の認証を必要とする。これは、保護された取引/データへアクセスしようとする要求者が以前の取引に関わった人と同一であるという、ある程度の信頼性を持つ。

<!--
**AAL 2**: AAL 2 requires two different authentication factors, providing higher assurance that the same claimaint who participated in previous transactions is accessing the protected transaction or data.
-->
**AAL 2**: AAL 2は、2つの異なる要素の認証を必要とする。これは、保護された取引/データへアクセスしようとする要求者が以前の取引に関わった人と同一であるという、より高い信頼性を提供する。

<!--
**AAL 3**: AAL 3 provides the highest practical remote digital authentication assurance. It requires proof of possession of a key in a physical multifactor authenticator through a cryptographic protocol.-->
**AAL 3**: AAL 3は、遠隔で行われるデジタル認証のうち最も実用的な信頼性を提供する。これは、暗号理論に基づくプロトコルを介して、物理的な多要素認証器内部にある鍵の所有者であることを証明することを必要とする。


<!-- ## Table of Contents -->
## 目次

[1. 目的](#sec1)

[2. はじめに](#sec2)

[3. 定義及び略語](#sec3)

[4. 認証器信頼レベル(Authenticator Assurance Levels)](#sec4)

[5. 認証器(Authenticator)及び検証器(Verifier)の要件](#sec5)

[6. 認証器ライフサイクルの要件](#sec6)

[7. セッション管理](#sec7)

[8. 脅威とセキュリティに関する考慮事項](#sec8)

[9. プライバシに関する考慮事項](#sec9)

[10. ユーザビリティに関する考慮事項](#sec10)

[11. 参照](#references)

[付録A. 記憶シークレットの強度](#appA)

<!--
[1. Purpose](#sec1)

[2. Introduction](#sec2)

[3. Definitions and Abbreviations](#sec3)

[4. Authenticator Assurance Levels](#sec4)

[5. Authenticator and Verifier Requirements](#sec5)

[6. Authenticator Lifecycle Requirements](#sec6)

[7. Session Management](#sec7)

[8. Threats and Security Considerations](#sec8)

[9. Privacy Considerations](#sec9)

[10. Usability Considerations](#sec10)

[11. References](#references)

[Appendix A. Strength of Memorized Secrets](#appA)
-->
