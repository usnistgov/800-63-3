<a name="sec1"></a>

<div class="breaker"></div>

## 1. <a name="purpose"></a>Purpose

*This section is informative.*

This recommendation and its companion documents, SP 800-63A, SP 800-63B, and SP 800-63C, provide technical guidelines to agencies for the implementation of digital authentication.

<a name="sec2"></a>

## 2. <a name="intro"></a>Introduction

*This section is informative.*

Digital identity is the unique representation of a subject engaged in an online transaction. A digital identity is always unique in the context of a digital service, but does not necessarily need to uniquely identify the subject. In other words, accessing a digital service may not mean that the physical representation of the underlying subject is known. Identity proofing establishes that a subject is actually who they claim to be. Digital authentication is the process of determining the validity of one or more authenticators used to claim a digital identity. Authentication establishes a subject attempting to access a digital service is in control of the technologies used to authenticate.  For services in which return visits are applicable, successfully authenticating provides reasonable risk-based assurances that the subject that is accessing the service today is the same as that which accessed the service yesterday. Digital identity presents a technical challenge because this process often involves the proofing of individuals over an open network, and always involves the authentication of individual subjects over an open network to access digital government services. Of which exists multiple opportunities for impersonation and other attacks to fraudelently claim another subjects digital identity.

This recommendation provides technical guidelines
to agencies to allow a subject to remotely authenticate their identity to a Federal system. This recommendation also provides guidelines for credential service providers (CSPs), verifiers, and relying parties (RPs).

This document suite describes identity assurance, authenticator assurance, and federation assurance and as separate ordinal measurements, and provides a mapping between these metrics and the overall level of assurance (LOA). These technical guidelines supplement OMB guidance, *E-Authentication Guidance for Federal Agencies* \[[OMB M-04-04](#M-04-04)\] and supersede NIST SP 800-63-1 and SP 800-63-2. OMB M-04-04 defines four LOAs, Levels 1 to 4, in terms of the consequences of authentication errors and misuse of credentials. Level 1 is the lowest assurance level and Level 4 is the highest. The guidance defines the required LOA in terms of the potential consequences of an authentication error. As the consequences of an authentication error become more severe, the required LOA increases. The OMB guidance provides agencies with criteria for determining the LOA required for specific digital transactions and systems, based on the likelihood of occurrence and potential impact should they occur.

These guidelines support the mitigation of the negative impacts induced by an authentication error by separating the individual elements of identity assurance into discrete, component parts. For non-federated systems, agencies will select two components, referred to as *Identity Assurance Level (IAL)* and *Authenticator Assurance Level (AAL)*. For federated systems, a third component, *Federation Assurance Level (FAL)*, is included. 

These guidelines do not view LOA in the context of a single ordinal that drives all implementation specific requirements.  Rather, by combining appropriate risk management for business, security, and privacy side-by-side with mission need, agencies are encouraged to consider IAL, AAL, and FAL as distinct options; while many systems will have the same numerical level for each of IAL, AAL, and FAL, this not a requirement and agencies should not assume they will be the same in any given system. [Section 5](#sec5) provides options that support agency selection of the appropriate IAL, AAL and FAL combinations while adhering to OMB M-04-04 to protect government digital services. In addition, this section also provides a mapping of IAL, AAL, and FAL to OMB M-04-04 LOAs for digital services that requires the same levels.

The components of identity assurance detailed in these guidelines are as follows:

* **IAL** refers to the identity proofing process and the binding between one or more authenticators and the records pertaining to a specific subscriber.
* **AAL** refers to the authentication process itself.
* **FAL** refers to the assertion protocol utilized in a federated environment to communicate authentication and attribute information (if applicable) to an RP.

As such, SP 800-63 is organized as a suite of documents as follows:

- SP 800-63-3 *Digital Identity Guidelines* - Provides an overview of general identity frameworks, using authenticators, credentials, and assertions together in a digital system, and a risk-based process of selecting assurance levels. _This document contains only informative material._

- SP 800-63A *Enrollment and Identity Proofing* - Addresses how applicants can prove their identities and become enrolled as valid subjects within an identity system. It provides a guideline for processes by which applicants can both proof and enroll at one of three different levels of risk mitigation in both remote and physically-present scenarios. _This document contains both normative and informative material._

- SP 800-63B *Authentication and Lifecycle Management* - Addresses how an individual can securely authenticate to a CSP to access a digital service or set of digital services.  _This document contains both normative and informative material._

- SP 800-63C *Federation and Assertions* - Provides a guideline on the use of federated identity architectures and assertions to convey the results of authentication processes and relevant identity information to an agency application. In addition, this guideline offers privacy enhancing techniques to share information about a valid, authenticated subject, as well as describing methods that allow for strong multi-factor authentication (MFA) while the subject remains pseudonymous to the digital service. _This document contains both normative and informative material._

NIST anticipates that SP 800-63A, SP 800-63B, and SP 800-63C will be revised asynchronously with each other and with this document. At any given time, the most recent revision of each should be used (e.g., if at a time in the future SP 800-63A-1 and SP 800-63B-2 are the most recent revisions of each document, they should be used together even though the revision numbers do not match).

OMB guidance outlines a five-step process by which agencies should meet
their authentication assurance requirements:

1.  *Conduct a risk assessment of the government system* - No specific
    risk assessment methodology is prescribed for this purpose;
    however, NIST Special
    Publication (SP) 800-30 [[SP 800-30]](#SP800-30) offers a general
    process for risk assessment and risk mitigation, and NIST Special Publication (SP) 800-37 Revision 1 [[SP 800-37]](#SP800-37) provides a guideline on the selection and specification of security controls for a system as part of an organization-wide information security program. This guideline supports the identification of risk to the organization or to individuals associated with the operation of a system.

2.  *Map identified risks to the appropriate assurance level* - Section
    2.2 of OMB M-04-04 provides the guidance necessary for agencies to
    perform this mapping.

3.  *Select technology based on digital authentication technical guidance* -
    After the appropriate assurance level has been determined, OMB
    guidance states that agencies should select technologies that meet
    the corresponding technical requirements, as specified by
    this document suite. Some agencies may possess existing
    digital authentication technology. Agencies should verify that any
    existing technology meets the requirements specified in
    this document suite.

4.  *Validate that the implemented system has met the required assurance
    level* - As some implementations may create or compound particular
    risks, agencies should conduct a final validation to confirm that
    the system achieves the required assurance level for the
    user-to-agency process. NIST SP 800-53A [[SP 800-53A]](#SP800-53A)
    provides a guideline for the assessment of the implemented system
    during the validation process. Validation should be performed as
    part of a security authorization process as described in NIST SP
    800-37, Revision 1 [[SP 800-37]](#SP800-37).

5.  *Periodically reassess the system to determine
    technology refresh requirements* - The agency shall periodically
    reassess the system to ensure that the identity
    authentication requirements continue to be satisfied. NIST SP
    800-37, Revision 1 [[SP 800-37]](#SP800-37) provides a guideline on
    the frequency, depth and breadth of periodic reassessments. As with
    the initial validation process, agencies should follow the
    assessment guideline specified in SP 800-53A [[SP
    800-53A]](#SP800-53A) for conducting the security assessment.

This suite of documents provides guidelines for implementing the third step of the
above process. In particular, this document maps the four LOAs defined in OMB M-04-04 into corresponding authenticator assurance and identity assurance levels. Other documents in the suite state specific technical
requirements for identity assurance and authenticator assurance in the following
areas:

-   Identity proofing and registration of applicants (covered in SP 800-63A).

-   Authenticators (covered in SP 800-63B).
    
-	Authenticator lifecycle and management mechanisms (covered in SP 800-63B).

-   Protocols used to support the authentication mechanism between the
    claimant and the verifier (covered in SP 800-63B).

-   Assertion mechanisms used to communicate the results of a remote
    authentication if these results are sent to other parties (covered
    in SP 800-63C).

### 2.1. Considerations, Other Requirements, and Flexibilities
Within a given LOA, agencies may employ other risk mitigation measures and compensating controls not specified herein. Agencies need to ensure that any mitigations and compensating controls do not degrade the intended security and privacy of the selected assurance levels. Agencies may consider partitioning the
functionality of a digital service to allow less
sensitive functions to be available at a lower level of authentication
and identity assurance, while more sensitive functions are available
only at a higher LOA.

Agencies may determine based on their risk
analysis that additional measures are appropriate in certain contexts.
In particular, privacy requirements and legal risks may lead agencies to
determine that additional authentication measures or other process
safeguards are appropriate. When developing digital authentication processes
and systems, agencies should consult *OMB Guidance for Implementing the
Privacy Provisions of the E-Government Act of 2002* [[M-03-22]](#M-03-22). See the *Use of Electronic Signatures in Federal Organization
Transactions* [[ESIG]](#ESIG) for additional information on legal risks, especially those that are related to the need to satisfy legal standards of proof and prevent repudiation.

Additionally, Federal agencies implementing these guidelines should
adhere to the requirements of Title III of the E-Government Act,
entitled the *Federal Information Security Management Act*
\[[FISMA](#FISMA)\], and related NIST standards and guidelines.
FISMA directs Federal agencies to develop, document, and implement
agency-wide programs to provide information security for the information
and systems that support the operations and assets of the
agency. This includes the security authorization of IT systems that support
digital authentication. It is recommended that non-Federal entities
implementing these guidelines follow equivalent standards of security
management, certification and accreditation to ensure the secure
operations of their digital systems.

### 2.2. A Few Limitations

These technical guidelines do not address the
authentication of a person who is physically present, for example, for
access to buildings, even though some authenticators that are used
remotely may also be used for local authentication. These guidelines do not yet address
machine-to-machine (such as router-to-router) authentication, or
establish specific requirements for issuing authenticators to machines and servers when they are used in
authentication protocols with people.

This document suite focuses on authenticators that are difficult to forge because they contain some type of secret information that is not available to unauthorized parties and that is preferably not used in unrelated contexts. Biometric authentication uses human characteristics that, in some cases, may be available to an attacker. Accordingly, the use of biometrics for authentication is limited to activation of a specific physical authenticator to which it is strongly bound, and the number of consecutive activation failures is limited, beyond which another activation factor or authenticator is required. This document suite also supports the use of biometrics to prevent repudiation of registration, and to verify that the same individual participates in all phases of the registration process.

### 2.3. How to Use this Suite of SPs

The business model, marketplace, and the composition of the way identity services are delivered has drastically changed since the first version of SP 800-63 was released.  Notably, CSPs can be componentized and composed of multiple independently operated and owned business entities.  In addition, there is a significant benefit to the use of strong authenticators even if no identity proofing is required.  Therefore, a suite of SPs under the 800-63 moniker has been created to facilitate these new models and make it easy to access the specific requirements for the function an entity may serve under the overall digital authentication model.  Each document stands alone.  However, it is expected that all CSPs, even componentized, will be required to meet the guidelines in [SP 800-63A](sp800-63a.html) and [SP 800-63B](sp800-63b.html).  If the CSP also participates in an identity federation, which is generally preferred over use of an RP acting as its own CSP, meeting the requirements of [SP 800-63C](sp800-63c.html) also applies.

### 2.4. Relationship to Other Standards and Guidelines

This document has been written to satisfy the needs of federal agencies. However, with the expansion of citizen services throughout the world that require identity and authentication assurance, as well as an increasing number of use cases that promote international identity federation and interoperability, these guidelines are intended to achieve alignment to national and international standards that describe levels of identity assurance. [Table 2-1](#63Sec2-Table1) provides a representative snapshot of mappings to various international and national assurance documents. This is not meant to imply that there is direct correlation between the IALs and AALs in this document and the levels in those standards, but that it is seen that this document fulfills the criteria as demonstrated in those standards.

<a name="63Sec2-Table1"></a>

<div class="text-center" markdown="1">

**Table 2-1.  800-63 Informative Mapping to Other Standards and Guidelines**

</div>

SP 800-63|[[eIDAS]](#eIDAS)|[[GPG 45]](#GPG45)|[[RSDOPS]](#RSDOPS)|[[STORK 2.0]](#STORK2.0)|[[ISO 29115]](#ISO29115)|[[ISO 29003]](#ISO29003)|[[Canada]](#Canada)
:---------:|:----:|:----:|:----:|:-------:|:--------:|:-------:|:------------------:
N/A|N/A|N/A|Level 01|N/A|N/A|N/A|N/A
AAL/IAL 1|Low|Level 1|Level 1|QAA Level 1|LoA 1|LoA 1|IAL/CAL 1
AAL/IAL 1|Low|Level 2|Level 2|QAA Level 2|LoA 2|LoA 2|IAL/CAL 2
AAL/IAL 2|Substantial|Level 3|Level 3|QAA Level 3|LoA 3|LoA 3|IAL/CAL 3
AAL/IAL 3|High|Level 4|N/A2|QAA Level 4|LoA 4|LoA 4|IAL/CAL 4

### 2.5. Change History

#### 2.5.1. SP 800-63-1

NIST SP 800-63-1 updated NIST SP 800-63 to reflect current authenticator (then referred to as token)
technologies and restructured to provide a better understanding of the
digital authentication architectural model used here. Additional (minimum)
technical requirements were specified for the CSP, protocols utilized to
transport authentication information, and assertions if implemented
within the digital authentication model. Other changes to NIST SP 800-63
included:

-   Recognition of more types of tokens, including pre-registered
    knowledge token, look-up secret token, out-of-band token, as well
    as some terminology changes for more conventional token types;

-   Detailed requirements for assertion protocols and Kerberos;

-   A new section on token and credential management;

-   Simplification of guidelines for password entropy and throttling;

-   Emphasis that the document is aimed at Federal IT systems;

-   Recognition of different models, including a broader
    digital authentication model (in contrast to the simpler model common
    among Federal IT systems shown in Figure 1) and an additional
    assertion model, the Proxy Model, presented in Figure 6;

-   Clarification of differences between Levels 3 and 4 in Table 12; and

-   New guidelines that permit leveraging existing credentials to issue
    derived credentials.

The subsequent sections of NIST SP 800-63-1 presented a series of
recommendations for the secure implementation of RAs, CSPs, Verifiers,
and RPs. It should be noted that secure implementation of any one of
these can only provide the desired LOA if the others are
also implemented securely. Therefore, the following assumptions were
made in NIST SP 800-63-1:

-   RAs, CSPs, and Verifiers are trusted entities. Agencies implementing
    any of the above trusted entities have some assurance that all other
    trusted entities with which the agency interacts are also
    implemented appropriately for the desired security level.

-   The RP is not considered a trusted entity. However, in some
    authentication systems the Verifier maintains a relationship with
    the RP to facilitate secure communications and may employ security
    controls which only attain their full value when the RP
    acts responsibly. The subscriber also trusts the RP to properly
    perform the requested service and to follow all relevant
    privacy policy.

-   It is assumed that there exists a process of certification through
    which agencies can obtain the above assurance for trusted entities
    which they do not implement themselves.

-   A trusted entity is considered to be implemented appropriately if it
    complies with the recommendations in this document and does not
    behave maliciously.

-   While it is generally assumed that trusted entities will not behave
    maliciously, this document does contain some recommendations to
    reduce and isolate any damage done by a malicious or negligent
    trusted entity.

#### 2.5.2. SP 800-63-2

NIST SP 800-63-2 was a limited update of Special Publication 800-63-1 and
substantive changes were made only in section 5. *Registration and
Issuance Processes*. The substantive changes in the revised draft were
intended to facilitate the use of professional credentials in the
identity proofing process, and to reduce the need to use postal mail to
an address of record to issue credentials for level 3 remote
registration. Other changes to section 5 were minor explanations and
clarifications.


#### 2.5.3. SP 800-63-3

NIST SP 800-63-3 is a substantial update and restructuring of Special Publication 800-63-2. It introduces individual components of digital authentication assurance - authenticator assurance level, identity assurance level, and federation assurance level - to support the growing need for independent treatment of authentication strength and confidence in an individuals claimed identity (for example, in strong pseudonymous authentication). It also moves from a single document describing authentication to a suite of four documents, of which SP 800-63-3 is the top-level document.

Other areas of update to SP 800-63-2 include:

-	Terminology changes, primarily the use of *authenticator* in place of *token* to avoid conflicting use of the word *token* in assertion technologies.
-	Updates to authentication and assertion requirements to reflect advances in both security technology and threats.
-	Requirements on the storage of long-term secrets by verifiers.
-   Restructured identity proofing model.
-	Updated requirements regarding remote identity proofing.
-	Clarification on the use of independent channels and devices as "something you have".
-	Removal of pre-registered knowledge tokens (authenticators), with the recognition that they are special cases of (often very weak) passwords.
-	Requirements regarding account recovery in the event of loss or theft of an authenticator.
-   Expanded discussion of reauthentication and session management.
-   Expanded discussion of identity federation; restructuring of assertions in the context of federation.
