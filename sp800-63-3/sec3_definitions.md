<a name="sec3"></a>

## 3. Definitions and Abbreviations

There is a wide variety of terms used in the area of authentication. While the definitions of many terms are consistent with the earlier versions of SP 800-63, some have changed in this revision. Since there is no single, consistent definition of many of these terms, careful attention to how the terms are defined here is warranted.

The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document family for additional definitions and abbreviations specific to their content.

#### Applicant
A party undergoing the processes of registration and identity proofing.

#### Assertion
A statement from a verifier to a relying party (RP) that contains identity information about a subscriber. Assertions may also contain verified attributes.


#### Assurance
In the context of [[OMB M-04-04]](#M-04-04) and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of an individual to whom the credential was issued, and 2) the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued.

#### Asymmetric Keys
Two related keys, a public key and a private key that are used to perform complementary operations, such as encryption and decryption or signature generation and signature verification.

#### Attack
An attempt by an unauthorized individual to fool a verifier or a relying party into believing that the unauthorized individual in question is the subscriber.

#### Attacker
A party who acts with malicious intent to compromise an information system.

#### Attribute
A claim of a named quality or characteristic inherent in or ascribed to someone or something. (See term in [\[ICAM\]](#ICAM) for more information.)

#### Authentication
The process of establishing confidence in the identity of users or information systems.

#### Authentication Protocol
A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of a valid authenticator to establish his/her identity, and optionally, demonstrates to the claimant that he or she is communicating with the intended verifier.

#### Authentication Secret
A generic term for any secret value that could be used by an attacker to impersonate the subscriber in an authentication protocol.

These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The authenticator secret is the canonical example of a long term authentication secret, while the authenticator output, if it is different from the authenticator secret, is usually a short term authentication secret.

#### Authenticator
Something that the claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant’s identity. In previous versions of this guideline, this was referred to as a *token*.

#### Authenticator Assurance Level (AAL)
A metric describing robustness of the authentication process proving that the claimant is in control of a given subscriber's authenticator(s).

#### Authenticator Secret
The secret value contained within an authenticator.

#### Authenticity
The property that data originated from its purported source.

#### Biometrics
Automated recognition of individuals based on their behavioral and biological characteristics.

In this document, biometrics may be used to unlock authenticators and prevent repudiation of registration.

#### Claimant
A party whose identity is to be verified using an authentication protocol.

#### Claimed Identity
A declaration by the applicant of their current Personal Name, date of birth and address. [[GPG45]](#gpg45)

#### Credential
An object or data structure that authoritatively binds an identity (and optionally, additional attributes) to an authenticator possessed and controlled by a subscriber.

While common usage often assumes that the credential is maintained by the subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the subscriber’s authenticator(s) and identity.

#### Credential Service Provider (CSP)
A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. The CSP may encompass Registration Authorities (RAs) and verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use.

#### Cryptographic Key
A value used to control cryptographic operations, such as decryption, encryption, signature generation or signature verification. For the purposes of this document, key requirements shall meet the minimum requirements stated in Table 2 of NIST SP 800-57 Part 1.

See also Asymmetric keys, Symmetric key.

#### Cryptographic Authenticator
An authenticator where the secret is a cryptographic key.

#### Digital Authentication

The process of establishing confidence in user identities digitally presented to an information system.

#### Digital Signature
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation.


#### Federal Information Security Management Act (FISMA)
Title III of the E-Government Act requiring each federal agency to develop, document, and implement an agency-wide program to provide information security for the information and information systems that support the operations and assets of the agency, including those provided or managed by another agency, contractor, or other source.

#### Federal Information Processing Standard (FIPS)
Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves standards and guidelines that are developed by the National Institute of Standards and Technology (NIST) for Federal computer systems. These standards and guidelines are issued by NIST as Federal Information Processing Standards (FIPS) for use government-wide. NIST develops FIPS when there are compelling Federal government requirements such as for security and interoperability and there are no acceptable industry standards or solutions. See background information for more details.

FIPS documents are available online through the FIPS home page: <http://www.nist.gov/itl/fips.cfm>

#### Federation
A process that allows for the conveyance of identity and authentication information across a set of networked systems.

#### Identity
A set of attributes that uniquely describe a person within a given context.

#### Identity Assurance Level (IAL)
A metric describing degree of confidence that the applicant’s claimed identity is their real identity.

#### Identity Proofing
The process by which a CSP and a Registration Authority (RA) collect and verify information about a person for the purpose of issuing credentials to that person.

#### Multi-Factor
A characteristic of an authentication system or an authenticator that uses more than one authentication factor.

The three types of authentication factors are something you know, something you have, and something you are.

#### Network
An open communications medium, typically the Internet, that is used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (i.e., impersonation, man-in-the-middle, session hijacking) and passive (i.e., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP or RP).

#### Password
A secret that a claimant memorizes and uses to authenticate his or her identity. Passwords are typically character strings.

#### Personal Identification Number (PIN)
A password consisting only of decimal digits.

#### Personally Identifiable Information (PII)
As defined by OMB Circular A-130, Personally Identifiable Information means information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual.

#### Private Key
The secret part of an asymmetric key pair that is used to digitally sign or decrypt data.

#### Pseudonymous Identifer
A meaningless, but unique number that does not allow the RP to infer the subscriber but which does permit the RP to associate multiple interactions with the subscriber’s claimed identity.

#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.

#### Public Key Certificate
A digital document issued and digitally signed by the private key of a Certificate authority that binds the name of a subscriber to a public key. The certificate indicates that the subscriber identified in the certificate has sole control and access to the private key. See also [[RFC 5280]](#RFC5280).

#### Public Key Infrastructure (PKI)
A set of policies, processes, server platforms, software and workstations used for the purpose of administering certificates and public-private key pairs, including the ability to issue, maintain, and revoke public key certificates.

#### Registration
The process through which an applicant applies to become a subscriber of a CSP and an RA validates the identity of the applicant on behalf of the CSP.

#### Registration Authority (RA)
A trusted entity that establishes and vouches for the identity or attributes of a subscriber to a CSP. The RA may be an integral part of a CSP, or it may be independent of a CSP, but it has a relationship to the CSP(s).

#### Relying Party (RP)
An entity that relies upon the subscriber's authenticator(s) and credentials or a verifier's assertion of a claimant’s identity, typically to process a transaction or grant access to information or a system.

#### Remote
(*As in remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization’s security controls.

Note: Any information exchange across the Internet is considered remote.

#### Risk Assessment
The process of identifying the risks to system security and determining the probability of occurrence, the resulting impact, and additional safeguards that would mitigate this impact. Part of Risk Management and synonymous with Risk Analysis.

#### Shared Secret
A secret used in authentication that is known to the claimant and the verifier.

#### Special Publication (SP)
A type of publication issued by NIST. Specifically, the Special Publication 800-series reports on the Information Technology Laboratory's research, guidelines, and outreach efforts in computer security, and its collaborative activities with industry, government, and academic organizations.

#### Subscriber
A party who has received a credential or authenticator from a CSP.

#### Symmetric Key
A cryptographic key that is used to perform both the cryptographic operation and its inverse, for example to encrypt and decrypt, or create a message authentication code and to verify the code.

#### Token
See *Authenticator*.

#### Unverified Name
A subscriber name that is not verified as meaningful by identity proofing.

#### Valid
In reference to an ID, the quality of not being expired or revoked.

#### Verified Name
A subscriber name that has been verified by identity proofing.

#### Verifier
An entity that verifies the claimant’s identity by verifying the claimant’s possession and control of one or two authenticators using an authentication protocol. To do this, the verifier may also need to validate credentials that link the authenticator(s) and identity and check their status.

