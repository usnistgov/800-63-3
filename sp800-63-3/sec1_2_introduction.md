<a name="sec1"></a>

<div class="breaker"></div>

## 1. <a name="purpose"></a>Purpose

*This section is informative.*

This recommendation and its companion documents, Special Publication (SP) 800-63A, SP 800-63B, and SP 800-63C, provide technical guidelines to agencies for the implementation of digital authentication.

<a name="sec2"></a>

## 2. <a name="intro"></a>Introduction

*This section is informative.*

Digital identity is the unique representation of a subject engaged in an online transaction. A digital identity is always unique in the context of a digital service, but does not necessarily need to uniquely identify the subject in all contexts. In other words, accessing a digital service may not mean that the physical representation of the underlying subject is known. Identity proofing establishes that a subject is who they claim to be. Digital authentication is the process of determining the validity of one or more authenticators used to claim a digital identity. Authentication establishes a subject attempting to access a digital service is in control of the technologies used to authenticate. Successful authentication provides reasonable risk-based assurances that the subject accessing the service today is the same as that which accessed the service previously. Digital identity presents a technical challenge because this process often involves  proofing  individuals over an open network, and typically involves the authentication of individual subjects over an open network to access digital government services. There are multiple opportunities for impersonation and other attacks that fraudulently claim another subject's digital identity.

This recommendation provides agencies technical guidelines to allow a subject to remotely authenticate to a federal system. This recommendation also provides guidelines for credential service providers (CSPs), verifiers, and relying parties (RPs).

This document suite describes the risk management processes for selecting appropriate digital identity services, and the details for implementing identity assurance, authenticator assurance, and federation assurance levels based on risk. Risk assessment guidance in this 800-63 suite supplements the *NIST Risk Management Framework* [[NIST RMF]](#NIST-RMF) and its component special publications. This guideline does not establish additional risk management processes for agencies. Rather, requirements contained herein provide specific guidance related to digital identity risk while executing all relevant RMF lifecycle phases.

Digital authentication supports privacy protection by mitigating risks to unauthorized access to individuals' information. At the same time, because identity proofing, authentication, authorization, and federation involve the processing of individuals' information, these functions can also create privacy risks. These guidelines therefore include privacy requirements and considerations to help mitigate potential privacy risks arising from these activities.

These guidelines support the mitigation of the negative impacts induced by an authentication error by separating the individual elements of identity assurance into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authenticator Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included.  [Section 5, Digital Identity Risk Management](#sec5) provides details on the risk assessment process. [Section 6, Selecting Assurance Levels](#sec6) combines the results of the risk assessment with additional context to support agency selection of the appropriate IAL, AAL, and FAL combinations based on risk.

These guidelines do not consider nor result in a composite level of assurance (LOA) in the context of a single ordinal that drives implementation-specific requirements. Rather, by combining appropriate risk management for business, security, and privacy side-by-side with mission need, agencies will select IAL, AAL, and FAL as distinct options. Specifically, this document does not recognize the four LOA model previously used by federal agencies and described in OMB M-04-04, instead requiring agencies to individually select levels corresponding to each function being performed. While many systems will have the same numerical level for each IAL, AAL, and FAL, this is not a requirement, and agencies should not assume they will be the same in any given system or application.

The components of identity assurance detailed in these guidelines are as follows:

* **IAL** refers to the identity proofing process.
* **AAL** refers to the authentication process.
* **FAL** refers to the assertion protocol used in a federated environment to communicate authentication and attribute information (if applicable) to a RP.

As such, SP 800-63 is organized as a suite of documents as follows:

- SP 800-63 *Digital Identity Guidelines* - Provides the risk assessment methodology and an overview of general identity frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _SP 800-63 contains both normative and informative material._

- SP 800-63A *Enrollment and Identity Proofing* - Addresses how applicants can prove their identities and become enrolled as valid subjects within an identity system. It provides requirements for processes by which applicants can both proof and enroll at one of three different levels of risk mitigation in both remote and physically-present scenarios. _SP 800-63A contains both normative and informative material._

- SP 800-63B *Authentication and Lifecycle Management* - Addresses how an individual can securely authenticate to a CSP to access a digital service or set of digital services. This volume also describes the process of binding an authenticator to an identity. _SP 800-63B contains both normative and informative material._

- SP 800-63C *Federation and Assertions* - Provides requirements on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. Furthermore, this guideline offers privacy-enhancing techniques to share information about a valid, authenticated subject, as well as describing methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the digital service. _SP 800-63C contains both normative and informative material._

NIST anticipates that individual documents in this suite will be revised asynchronously. At any time, the most recent revision of each should be used (e.g., if at a time in the future SP 800-63A-1 and SP 800-63B-2 are the most recent revisions of each document, they should be used together even though the revision numbers do not match). To minimize the risk of compatibility errors, a reference to the base document (i.e., SP 800-63 rather than SP 800-63-3) always refers to the current version of the document.

The following table states which sections of this document are normative and which are informative:

|Section Name|Normative/Informative|
|----|:--:|
|1. Purpose|Informative|
|2. Introduction|Informative|
|3. Definitions and Abbreviations|Informative|
|4. Digital Identity Model|Informative|
|5. Digital Identity Risk Management|Normative|
|6. Selecting Assurance Levels|Normative|
|7. Federation Considerations|Informative|
|8. References|Informative|

### 2.1. Applicability

Not all digital services require authentication or identity proofing; however, this guidance applies to all such transactions for which digital identity or authentication are required, regardless of the constituency (e.g. citizens, business partners, government entities).

Transactions not covered by this guidance include those that are associated with national security systems as defined in 44 U.S.C. § 3542(b)(2). Private-sector organizations and state, local, and tribal governments whose digital processes require varying levels of assurance may consider the use of these standards where appropriate.

These guidelines primarily focus on agency services that interact with the non-federal workforce such as citizens accessing benefits or private sector partners accessing information sharing collaboration spaces. However, it also applies to internal agency systems that are accessed by employees and contractors. These users are expected to hold a valid government-issued credential, primarily the Personal Identity Verification (PIV) card or a derived PIV. Therefore 800-63A and 800-63B are secondary to the requirements of FIPS 201 and its corresponding set of special publications and agency-specific instructions. However 800-63C and the risk-based selection of an appropriate FAL applies, regardless of the credential type the internal user holds. FAL selection provides agencies guidance and flexibility in how to PIV-enable their applications based on system risk.

### 2.2. Considerations, Other Requirements, and Flexibilities

Agencies may employ other risk mitigation measures and compensating controls not specified herein. Agencies need to ensure that any mitigations and compensating controls do not degrade the intended security and privacy protections of the selected assurance levels. Agencies may consider partitioning the functionality of a digital service to allow less
sensitive functions to be available at a lower level of authentication
and identity assurance.

Agencies may determine based on their risk
analysis that additional measures are appropriate in certain contexts.
In particular, privacy requirements and legal risks may lead agencies to
determine that additional authentication measures or other process
safeguards are appropriate. When developing digital authentication processes
and systems, agencies should consult *OMB Guidance for Implementing the
Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](#M-03-22). See the *Use of Electronic Signatures in Federal Organization
Transactions* [[ESIG]](#ESIG) for additional information on legal risks, especially those related to the need to 1) satisfy legal standards of proof and 2) prevent repudiation.

Additionally, Federal agencies implementing these guidelines should
adhere to the requirements of Title III of the E-Government Act,
entitled the *Federal Information Security Modernization Act* [[FISMA]](#FISMA), and related NIST standards and guidelines. FISMA directs Federal agencies to develop, document, and implement
agency-wide programs to provide security for the information
and systems that support the agency's operations and assets. This includes the security authorization and accreditation (SA&A) of IT systems that support
digital authentication. NIST recommends that non-Federal entities
implementing these guidelines follow equivalent standards to ensure the secure
operations of their digital systems.


### 2.3. A Few Limitations

These technical guidelines do not address the authentication of a person who is physically present (e.g., for access to buildings), even though some authenticators that are used remotely may be used for physical authentication. In addition, this revision of these guidelines does not explicitly address device identity, often referred to as machine-to-machine (such as router-to-router) authentication or interconnected devices, commonly referred to as the internet of things (IoT). That said, these guidelines are written to reference generic subjects wherever possible to leave open the possiblity for applicability to devices. Also excluded are specific requirements for issuing authenticators to devices when they are used in authentication protocols with people.

### 2.4. How to Use this Suite of SPs

The business model, marketplace, and the composition of the way identity services are delivered has drastically changed since the first version of SP 800-63 was released. Notably, CSPs can be componentized and composed of multiple independently operated and owned business entities. Furthermore, there may be a significant security benefit to using strong authenticators even if no identity proofing is required. Therefore, in this revision, a suite of SPs under the 800-63 moniker has been created to facilitate these new models and make it easy to access the specific requirements for the function an entity may serve under the overall digital identity model.

### 2.5. Relationship to Other Standards and Guidelines

This document has been written to satisfy the needs of federal agencies. However, with the expansion of consituent and customer services throughout the world that require digital identity and authentication assurance, as well as an increasing number of use cases that promote international identity federation and interoperability, these guidelines are intended to achieve alignment to national and international standards that describe levels of identity assurance. [Table 2-1](#63Sec2-Table1) provides a representative snapshot of mappings to various international and national assurance documents. This is not meant to imply that there is direct correlation between the IALs and AALs in this document and the levels in those standards, but that this document fulfills the criteria as demonstrated in those standards.

<a name="63Sec2-Table1"></a>

<div class="text-center" markdown="1">

**Table 2-1.  800-63 Informative Mapping to Other Standards and Guidelines**

</div>

SP 800-63|[[eIDAS]](#eIDAS)|[[GPG 45]](#GPG45)|[[GPG 44]](#GPG44)|[[RSDOPS]](#RSDOPS)|[[STORK 2.0]](#STORK2.0)|[[ISO 29115:2013]](#ISO29115)|[[Canada]](#Canada)
:---------:|:----:|:----:|:----:|:----:|:-------:|:--------:|:-------:|:------------------:
AAL/IAL1|Low|Level 1|Level 1|Level 1|QAA Level 1|LoA 1|IAL/CAL 1
AAL/IAL2|Substantial|Level 3|Level 2|Level 3|QAA Level 3|LoA 3|IAL/CAL 3
AAL/IAL3|High|Level 4|Level 3 (see note)|N/A2|QAA Level 4|LoA 4|IAL/CAL 4

> Note: GPG44 Level 3 allows for software cryptographic modules, which is not allowed at AAL3.

### 2.6. Change History

#### 2.6.1. SP 800-63-1

NIST SP 800-63-1 updated NIST SP 800-63 to reflect current authenticator (then referred to as token) technologies and restructured it to provide a better understanding of the digital identity architectural model used here. Additional (minimum) technical requirements were specified for the CSP, protocols used to transport authentication information, and assertions if implemented within the digital identity model. Other changes to NIST SP 800-63 included:

-   Recognition of more types of tokens, including pre-registered
    knowledge token, look-up secret token, out-of-band token, as well
    as some terminology changes for more conventional token types;

-   Detailed requirements for assertion protocols and Kerberos;

-   A new section on token and credential management;

-   Simplification of guidelines for password entropy and throttling;

-   Emphasis that the document is aimed at Federal IT systems;

-   Recognition of different models, including a broader digital authentication model (in contrast to the simpler model common among Federal IT systems shown in Figure 1) and an additional assertion model, the Proxy Model, presented in Figure 6;

-   Clarification of differences between Levels 3 and 4 in Table 12; and

-   New guidelines that permit leveraging existing credentials to issue derived credentials.

The subsequent sections of NIST SP 800-63-1 presented a series of recommendations for the secure implementation of Registration Authorities (RAs), CSPs, Verifiers,
and RPs. It should be noted that secure implementation of any one of these can only provide the desired LOA if the others are also implemented securely. Therefore, the following assumptions were made in NIST SP 800-63-1:

-   RAs, CSPs, and Verifiers are trusted entities. Agencies implementing any of the above trusted entities have some assurance that all other trusted entities with which the agency interacts are also implemented appropriately for the desired security level.

-   The RP is not considered a trusted entity. However, in some authentication systems the Verifier maintains a relationship with the RP to facilitate secure communications and may employ security controls which only attain their full value when the RP acts responsibly. The subscriber also trusts the RP to properly perform the requested service and to follow all relevant privacy policy.

-   It is assumed that there exists a process of certification through which agencies can obtain the above assurance for trusted entities which they do not implement themselves.

-   A trusted entity is considered to be implemented appropriately if it complies with the recommendations in this document and does not behave maliciously.

-   While it is generally assumed that trusted entities will not behave maliciously, this document does contain some recommendations to
    reduce and isolate any damage done by a malicious or negligent trusted entity.

#### 2.6.2. SP 800-63-2

NIST SP 800-63-2 was a limited update of SP 800-63-1 and substantive changes were made only in Section 5, *Registration and Issuance Processes*. The substantive changes in the revised draft were intended to facilitate the use of professional credentials in the identity proofing process, and to reduce the need to send postal mail to an address of record to issue credentials for level 3 remote registration. Other changes to Section 5 were minor explanations and clarifications.

#### 2.6.3. SP 800-63-3

NIST SP 800-63-3 is a substantial update and restructuring of SP 800-63-2. SP 800-63-3 introduces individual components of digital authentication assurance - AAL, IAL, and FAL - to support the growing need for independent treatment of authentication strength and confidence in an individual's claimed identity (e.g., in strong pseudonymous authentication). A risk assessment methodology and its application to IAL, AAL, and FAL has been included in this guideline. It also moves the whole of digital identity guidance covered under SP 800-63 from a single document describing authentication to a suite of four documents (to separately address the individual components mentioned above) of which SP 800-63-3 is the top-level document.

Other areas updated in 800-63-3 include:

- Renamed to "Digital Identity Guidelines" to properly represent the scope to include identity proofing and federation, as well as support expansion of scope to device identity, or machine-to-machine authentication, in future revisions.
- Terminology changes, including the use of *authenticator* in place of *token* to avoid conflicting use of the word *token* in assertion technologies.
-	Updates to authentication and assertion requirements to reflect advances in both security technology and threats.
-	Requirements on the storage of long-term secrets by verifiers.
-  Restructured identity proofing model.
-	Updated requirements regarding remote identity proofing.
-	Clarification on the use of independent channels and devices as "something you have".
-	Removal of pre-registered knowledge tokens (authenticators), with the recognition that they are special cases of (often very weak) passwords.
-	Requirements regarding account recovery in the event of loss or theft of an authenticator.
-	Removal of email as a valid channel for out-of-band authenticators.
-   Expanded discussion of reauthentication and session management.
-   Expanded discussion of identity federation; restructuring of assertions in the context of federation.
