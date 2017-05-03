<a name="def-and-acr"/>

## Appendix A: Definitions and Acronyms

*This section is normative.*

### A.1. Definitions

There is a wide variety of terms used in the area of authentication. While the definitions of many terms are consistent with the earlier versions of SP 800-63, some have changed in this revision. Since there is no single, consistent definition for many of these terms, careful attention to how the terms are defined here is warranted.

The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document suite for additional definitions and abbreviations specific to their content.

#### Active Attack
An attack on the authentication protocol where the attacker transmits data to the claimant, Credential Service Provider (CSP), verifier, or Relying Party (RP). Examples of active attacks include man-in-the-middle (MitM), impersonation, and session hijacking.

#### Address of Record
The validated and verified location (physical or digital) where an individual can receive communications using approved mechanisms.

#### Applicant
A subject undergoing the processes of registration and identity proofing.

#### Approved Cryptography
Federal Information Processing Standard (FIPS) approved or NIST recommended. An algorithm or technique that is either 1) specified in a FIPS or NIST Recommendation, or 2) adopted in a FIPS or NIST Recommendation.

#### Assertion
A statement from a verifier to an RP that contains information about a subscriber. Assertions may also contain verified attributes.

#### Assertion Reference
A data object, created in conjunction with an assertion, which identifies the verifier and includes a pointer to the full assertion held by the verifier.

#### Assurance
In the context of OMB M-04-04 and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of a claimant to whom a credential was, or credentials were, issued, and 2) the degree of confidence that the claimant who uses the credential is the same as the subscriber to whom the credential was issued.

#### Asymmetric Keys
Two related keys, consisting of a public key and a private key, that are used to perform complementary operations such as encryption and decryption or signature verification and generation.

#### Attack
An attempt by an unauthorized entity to fool a verifier or an RP into believing that the unauthorized individual in question is the subscriber.

#### Attacker
A party who acts with malicious intent to compromise a system.

#### Attribute
A quality or characteristic ascribed to someone or something.

#### Attribute Bundle
A packaged set of attributes, usually contained within an assertion.  Attribute bundles offer relying parties a simple way to retrieve the most relevant attributes they need from identity providers.  Attribute bundles are synonymous with OpenID Connect scopes. See [OpenID Connect Core 1.0](http://openid.net/specs/openid-connect-core-1_0.html#ScopeClaims).

#### Attribute Claim
A statement asserting a property of a subscriber without necessarily containing identity information, independent of format. For example, for the attribute 'birthday', a claim could be 'older than 18' or 'born in December'.

#### Attribute Value
A complete statement asserting a property of a subscriber, independent of format. For example, for the attribute 'birthday', a value could be '12/1/1980' or 'December 1, 1980'.

#### Authenticated Protected Channel
An encrypted communication channel that uses approved cryptography where the initiator of the connection (client) has authenticated the recipient (server). Authenticated protected channels provide confidentiality and MitM protection and are frequently used in the user authentication process. Transport Layer Security (TLS) BCP 195 is an example of an authenticated protected channel when the certificate presented by the recipient is verified by the initiator. Unless otherwise specified, authenticated protected channels do not require the authentication of the client by the server.

#### Authentication
Verifying the identity of a user, process, or device, often as a prerequisite to allowing access to resources in a system.

#### Authentication Factor
The three types of authentication factors are *something you know*, *something you have*, and *something you are*. Every authenticator has one or more authentication factors.

#### Authentication Intent
The process of confirming the intent of the claimant to authenticate or reauthenticate by including a manual process in the authentication flow. Some authenticators (e.g., OTP devices) establish authentication intent as part of their operation, others require a specific step, such as pressing a button, to establish intent. Authentication intent is a countermeasure against use by malware of the endpoint as a proxy for authenticating an attacker without the subscriber's knowledge.

#### Authentication Protocol
A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of one or more valid authenticators to establish their identity, and, optionally, demonstrates that the claimant is communicating with the intended verifier.

#### Authentication Protocol Run
An exchange of messages between a claimant and a verifier that results in authentication (or authentication failure) between the two parties.

#### Authentication Secret
A generic term for any secret value that could be used by an attacker to impersonate the subscriber in an authentication protocol.

These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The authenticator secret is the canonical example of a long term authentication secret, while the authenticator output, if it is different from the authenticator secret, is usually a short term authentication secret.

#### Authenticator
Something that the claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant's identity. In previous editions of SP 800-63, this was referred to as a *token*.

#### Authenticator Assurance Level (AAL)
A category describing the authentication process proving that the claimant is in control of a given subscriber's authenticator(s).

#### Authenticator Output
The output value generated by an authenticator. The ability to generate valid authenticator outputs on demand proves that the claimant possesses and controls the authenticator. Protocol messages sent to the verifier are dependent upon the authenticator output, but they may or may not explicitly contain it.

#### Authenticator Secret
The secret value contained within an authenticator.

#### Authenticity
The property that data originated from its purported source.

#### Authoritative Source
An entity that has access to, or verified copies of, accurate information from an issuing source such that a CSP can confirm the validity of the identity evidence supplied by an applicant during identity proofing. An issuing source may also be an authoritative source. Often, authoritative sources are determined by a policy decision of the agency or CSP before they can be used in the validation phase of identity proofing.

#### Back-Channel Communication
Communication between two systems that relies on a direct connection (allowing for standard protocol-level proxies), without using redirects through an intermediary such as a browser. This can be accomplished using HTTP requests and responses.

#### Bearer Assertion
An assertion presented by a party as proof of its identity, where possession of the assertion itself is sufficient proof of identity for the bearer of the assertion. 

#### Biometrics
Automated recognition of individuals based on their behavioral and biological characteristics.

In this document, biometrics may be used to unlock authenticators and prevent repudiation of registration.

#### Challenge-Response Protocol
An authentication protocol where the verifier sends the claimant a challenge (usually a random value or a nonce) that the claimant combines with a secret (such as by hashing the challenge and a shared secret together, or by applying a private key operation to the challenge) to generate a response that is sent to the verifier. The verifier can independently verify the response generated by the claimant (such as by re-computing the hash of the challenge and the shared secret and comparing to the response, or performing a public key operation on the response) and establish that the claimant possesses and controls the secret.

#### Claimant
A subject whose identity is to be verified using one or more authentication protocols.

#### Claimed Address
The physical location asserted by a subject at which they can be reached. It includes the residential street address of an individual and may also include the mailing address of the individual.

For example, a person with a foreign passport, living in the U.S., will need to give an address when going through the identity proofing process. This address would not be an "address of record" but a "claimed address."

#### Claimed Identity
A declaration of unvalidated and unverified personal attributes by the applicant.

#### Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA)
An interactive feature added to web-forms to distinguish use of the form by humans as opposed to automated agents. Typically, it requires entering text corresponding to a distorted image or from a sound stream.

#### Credential
An object or data structure that authoritatively binds an identity, via an identifier or identifiers, and, optionally, additional attributes, to at least one authenticator possessed and controlled by a subscriber.

While common usage often assumes that the credential is maintained by the subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the subscriber's authenticator(s) and identity.

#### Credential Service Provider (CSP)
A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. The CSP may encompass Registration Authorities (RAs) and verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use.

#### Cross-site Request Forgery (CSRF)
An attack in which a subscriber who is currently authenticated to an RP and connected through a secure session, browses to an attacker's website which causes the subscriber to unknowingly invoke unwanted actions at the RP.

For example, if a bank website is vulnerable to a CSRF attack, it may be possible for a subscriber to unintentionally authorize a large money transfer, merely by viewing a malicious link in a webmail message while a connection to the bank is open in another browser window.

#### Cross-site Scripting (XSS)
A vulnerability that allows attackers to inject malicious code into an otherwise benign website. These scripts acquire the permissions of scripts generated by the target website and can therefore compromise the confidentiality and integrity of data transfers between the website and client. Websites are vulnerable if they display user supplied data from requests or forms without sanitizing the data so that it is not executable.

#### Cryptographic Authenticator
An authenticator where the secret is a cryptographic key.

#### Cryptographic Key
A value used to control cryptographic operations, such as decryption, encryption, signature generation or signature verification. For the purposes of this document, key requirements shall meet the minimum requirements stated in Table 2 of NIST SP 800-57 Part 1.

See also Asymmetric Keys, Symmetric Key.

#### Cryptographic Module
A set of hardware, software, and/or firmware that implements approved security functions (including cryptographic algorithms and key generation).

#### Data Integrity
The property that data has not been altered by an unauthorized entity.

#### Derived Credential
A credential issued based on proof of possession and control of an authenticator associated with a previously issued credential, so as not to duplicate the identity proofing process.

#### Digital Authentication
The process of establishing confidence in user identities presented digitally to a system. In previous editions of SP 800-63, this was referred to as *Electronic Authentication*.

#### Digital Signature
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation but not confidentiality protection.

#### Eavesdropping Attack
An attack in which an attacker listens passively to the authentication protocol to capture information which can be used in a subsequent active attack to masquerade as the claimant.

#### Electronic Authentication (E-Authentication)
See *Digital Authentication*.

#### Enrollment
The process through which an applicant applies to become a subscriber of a CSP and an RA validates the identity of the applicant on behalf of the CSP.

#### Entropy
A measure of the amount of uncertainty that an attacker faces to determine the value of a secret. Entropy is usually stated in bits. A value having *n* bits of entropy has the same degree of uncertainty as a uniformly-distributed *n*-bit random value.

#### Equal Error Rate (EER)
The value where the false match rate (FMR) and false non-match rate (FNMR) of a sensor are equal. EER is a figure of merit for the sensor; the lower the EER is, the more certain the sensor's decision is likely to be.

#### Federal Information Processing Standard (FIPS)
Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves standards and guidelines that are developed by the National Institute of Standards and Technology (NIST) for Federal computer systems. These standards and guidelines are issued by NIST as Federal Information Processing Standards (FIPS) for use government-wide. NIST develops FIPS when there are compelling Federal government requirements such as for security and interoperability and there are no acceptable industry standards or solutions. See background information for more details.

FIPS documents are available online through the FIPS home page: <http://www.nist.gov/itl/fips.cfm>

#### Federal Information Security Management Act (FISMA)
Title III of the E-Government Act requiring each federal agency to develop, document, and implement an agency-wide program to provide information security for the information and systems that support the operations and assets of the agency, including those provided or managed by another agency, contractor, or other source.

#### Federation
A process that allows for the conveyance of identity and authentication information across a set of networked systems.

#### Federation Assurance Level (FAL)
A category describing the assertion protocol utilized by the federation to communicate authentication and attribute information (if applicable) to an RP.

#### Federation Proxy
A component that acts as a logical RP to a set of IdPs and a logical IdP to a set of RPs, bridging the two systems with a single component. These are sometimes referred to as "brokers".

#### Front-Channel Communication
Communication between two systems that relies on redirects through an intermediary such as a browser. This is normally accomplished by appending HTTP query parameters to URLs hosted by the receiver of the message.

#### Hash Function
A function that maps a bit string of arbitrary length to a fixed length bit string. Approved hash functions satisfy the following properties:

1. One-way - It is computationally infeasible to find any input that maps to any pre-specified output; and

2. Collision resistant - It is computationally infeasible to find any two distinct inputs that map to the same output.

#### Identity
An attribute or set of attributes that uniquely describe a subject within a given context.

#### Identity Assurance Level (IAL)
A category that conveys the degree of confidence that the applicant's claimed identity is their real identity.

#### Identity Proofing
The process by which a CSP and an RA collect and verify information about a person for the purpose of issuing credentials to that person.

#### Identity Provider (IdP)
The party that manages the subscriber’s primary authentication credentials and issues assertions derived from those credentials. This is commonly the CSP as discussed within this document suite.

#### Issuing Source
An authority that is responsible for the generation of data, digital evidence (such as assertions) or physical documents that can be used as identity evidence. 

#### Kerberos
A widely used authentication protocol developed at MIT. In "classic" Kerberos, users share a secret password with a Key Distribution Center (KDC). The user, Alice, who wishes to communicate with another user, Bob, authenticates to the KDC and is furnished a "ticket" by the KDC to use to authenticate with Bob.

When Kerberos authentication is based on passwords, the protocol is known to be vulnerable to offline dictionary attacks by eavesdroppers who capture the initial user-to-KDC exchange. Longer password length and complexity provide some mitigation to this vulnerability, although sufficiently long passwords tend to be cumbersome for users.

#### Knowledge Based Verification (KBV)
Identity verification method based on knowledge of private information associated with the claimed identity. This is often referred to as knowledge based authentication (KBA) or knowledge based proofing (KBP).

#### Man-in-the-Middle Attack (MitM)
An attack on the authentication protocol in which the attacker positions himself or herself in between the claimant and verifier so that he or she can intercept and/or alter data traveling between them.

#### Memorized Secret
A type of authenticator consisting of a character string that is intended to be memorized or memorable by the subscriber, permitting the subscriber to demonstrate *something they know* as part of an authentication process.

#### Message Authentication Code (MAC)
A cryptographic checksum on data that uses a symmetric key to detect both accidental and intentional modifications of the data. MACs provide authenticity and integrity protection, but not non-repudiation protection.

#### Mobile Code
Executable code that is normally transferred from its source to another computer system for execution. This transfer is often through the network (e.g., JavaScript embedded in a web page) but may transfer through physical media as well.

#### Multi-factor
A characteristic of an authentication system or an authenticator that requires more than one authentication factor for successful authentication. MFA can be performed using a single authenticator that provides more than one factor or by a combination of authenticators that provide different factors.

The three authentication factors are something you know, something you have, and something you are.

#### Multi-factor Authentication (MFA)
An authentication system or an authenticator that requires more than one authentication factor for successful authentication. Multi-factor authentication can be performed using a single authenticator that provides more than one factor or by a combination of authenticators that provide different factors.

The three authentication factors are something you know, something you have, and something you are.

#### Network
An open communications medium, typically the Internet, that is used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (e.g., impersonation, man-in-the-middle, session hijacking) and passive (e.g., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP, RP).

#### Nonce
A value used in security protocols that is never repeated with the same key. For example, nonces used as challenges in challenge-response authentication protocols SHALL not be repeated until authentication keys are changed. Otherwise, there is a possibility of a replay attack. Using a nonce as a challenge is a different requirement than a random challenge, because a nonce is not necessarily unpredictable.

#### Offline Attack
An attack where the attacker obtains some data (typically by eavesdropping on an authentication protocol run or by penetrating a system and stealing security files) that he/she is able to analyze in a system of his/her own choosing.

#### Online Attack
An attack against an authentication protocol where the attacker either assumes the role of a claimant with a genuine verifier or actively alters the authentication channel.

#### Online Guessing Attack
An attack in which an attacker performs repeated logon trials by guessing possible values of the authenticator output.

#### Pairwise Pseudonymous Identifier
An opaque unguessable subscriber identifier generated by a CSP for use at a specific individual RP. This identifier is only known to and only used by one CSP-RP pair.

#### Passive Attack
An attack against an authentication protocol where the attacker intercepts data traveling along the network between the claimant and verifier, but does not alter the data (i.e., eavesdropping).

#### Passphrase
A passphrase is a memorized secret consisting of a sequence of words or other text that a claimant uses to authenticate their identity. A passphrase is similar to a password in usage, but is generally longer for added security.

#### Password
See *memorized secret*.

#### Personal Data

See *Personally Identifiable Information*.

#### Personal Information

See *Personally Identifiable Information*.

#### Personal Identification Number (PIN)
A memorized secret typically consisting only of decimal digits.

#### Personally Identifiable Information (PII)
As defined by OMB Circular A-130, Personally Identifiable Information means information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual.

#### Pharming
An attack in which an attacker corrupts an infrastructure service such as DNS (Domain Name Service) causing the subscriber to be misdirected to a forged verifier/RP, which could cause the subscriber to reveal sensitive information, download harmful software or contribute to a fraudulent act.

#### Phishing
An attack in which the subscriber is lured (usually through an email) to interact with a counterfeit verifier/RP and tricked into revealing information that can be used to masquerade as that subscriber to the real verifier/RP.

#### Possession and Control of an Authenticator
The ability to activate and use the authenticator in an authentication protocol.

#### Practice Statement
A formal statement of the practices followed by the parties to an authentication process (e.g., CSP or verifier). It usually describes the policies and practices of the parties and can become legally binding.

#### Private Credentials
Credentials that cannot be disclosed by the CSP because the contents can be used to compromise the authenticator.

#### Private Key
The secret part of an asymmetric key pair that is used to digitally sign or decrypt data.

#### Protected Session
A session wherein messages between two participants are encrypted and integrity is protected using a set of shared secrets called session keys.

A participant is said to be *authenticated* if, during the session, they prove possession of one or more authenticators in addition to the session keys, and if the other party can verify the identity associated with the authenticator(s). If both participants are authenticated, the protected session is said to be *mutually authenticated*.

#### Pseudonym
A name other than a legal name.

#### Pseudonymous Identifier
A meaningless but unique number that does not allow the RP to infer anything regarding the subscriber but which does permit the RP to associate multiple interactions with the subscriber's claimed identity.

#### Public Credentials
Credentials that describe the binding in a way that does not compromise the authenticator.

#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.

#### Public Key Certificate
A digital document issued and digitally signed by the private key of a certificate authority that binds an identifier to a subscriber to a public key. The certificate indicates that the subscriber identified in the certificate has sole control and access to the private key. See also [[RFC 5280]](https://pages.nist.gov/800-63-3/sp800-63b.html#RFC5280).

#### Public Key Infrastructure (PKI)
A set of policies, processes, server platforms, software and workstations used for the purpose of administering certificates and public-private key pairs, including the ability to issue, maintain, and revoke public key certificates.

#### Reauthentication
The process of confirming the subscriber's continued presence and intent to be authenticated during an extended usage session.

#### Registration
The process through which an applicant applies to become a subscriber of a CSP and has their identity validated by the CSP.

#### Relying Party (RP)
An entity that relies upon the subscriber's authenticator(s) and credentials or a verifier's assertion of a claimant's identity, typically to process a transaction or grant access to information or a system.

#### Remote
(*In the context of remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization's security controls.

> Note: Any information exchange across the Internet is considered remote.

#### Replay Attack
An attack in which the attacker is able to replay previously captured messages (between a legitimate claimant and a verifier) to masquerade as that claimant to the verifier or vice versa.

#### Replay Resistance
The property of an authentication process to resist replay attacks, typically by use of an authenticator output that is valid only for a specific authentication.

#### Risk Assessment
The process of identifying, estimating, and prioritizing risks to organizational operations (including mission, functions, image, or reputation), organizational assets, individuals, and other organizations, resulting from the operation of a system. Part of risk management, incorporates threat and vulnerability analyses, and considers mitigations provided by security controls planned or in place. Synonymous with risk analysis.

#### Risk Management
The program and supporting processes to manage information security risk to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, other organizations, and includes: (i) establishing the context for risk-related activities; (ii) assessing risk; (iii) responding to risk once determined; and (iv) monitoring risk over time.

#### Salt
A non-secret value that is used in a cryptographic process, usually to ensure that the results of computations for one instance cannot be reused by an attacker.

#### Secure Sockets Layer (SSL)
See *Transport Layer Security (TLS)*.

#### Session
A persistent interaction between a subscriber and an endpoint, either an RP or a CSP. A session begins with an authentication event and ends with a session termination event. A session is bound by use of a session secret that the subscriber's software (a browser, application, or OS) can present to the RP or CSP in lieu of the subscriber's authentication credentials.

#### Session Hijack Attack
An attack in which the attacker is able to insert himself or herself between a claimant and a verifier subsequent to a successful authentication exchange between the latter two parties. The attacker is able to pose as a subscriber to the verifier or vice versa to control session data exchange. Sessions between the claimant and the RP can also be similarly compromised.

#### Shared Secret
A secret used in authentication that is known to the subscriber and the verifier.

#### Side Channel Attack
An attack enabled by leakage of information from a physical cryptosystem. Timing, power consumption, electromagnetic and acoustic emissions are examples of characteristics that could be exploited in a side-channel attack.

#### Social Engineering
The act of deceiving an individual into revealing sensitive information, obtaining unauthorized access, or committing fraud by associating with the individual to gain confidence and trust.

#### Special Publication (SP)
A type of publication issued by NIST. Specifically, the SP 800-series reports on the Information Technology Laboratory's research, guidelines, and outreach efforts in computer security, and its collaborative activities with industry, government, and academic organizations.

#### Subject  
A person, organization, device, hardware, network, software, or service.

#### Subscriber
A party who has received a credential or authenticator from a CSP.

#### Symmetric Key
A cryptographic key that is used to perform both the cryptographic operation and its inverse, for example to encrypt and decrypt, or create a message authentication code and to verify the code.

#### Token
See *Authenticator*.

#### Token Authenticator
See *Authenticator Output*.

#### Token Secret
See *Authenticator Secret*.

#### Transport Layer Security (TLS)
An authentication and security protocol widely implemented in browsers and web servers. TLS is defined by RFC 5246. TLS is similar to the older SSL protocol, and TLS 1.0 is effectively SSL version 3.1. NIST SP 800-52, *Guidelines for the Selection and Use of Transport Layer Security (TLS) Implementations* specifies how TLS is to be used in government applications.

#### Trust Anchor
A public or symmetric key that is trusted because it is directly built into hardware or software, or securely provisioned via out-of-band means, rather than because it is vouched for by another trusted entity (e.g. in a public key certificate).

#### Usability
Per ISO/IEC 9241-11: Extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use.

#### Valid
In reference to identity evidence, the quality of not being expired or revoked.

#### Verifier
An entity that verifies the claimant's identity by verifying the claimant's possession and control of one or two authenticators using an authentication protocol. To do this, the verifier may also need to validate credentials that link the authenticator(s) to the subscriber's identifier and check their status.

#### Verifier Impersonation
A scenario where the attacker impersonates the verifier in an authentication protocol, usually to capture information that can be used to masquerade as a subscriber to the real verifier. In previous editions of SP 800-63, authentication protocols that are resistant to verifier impersonation have been described as "strongly MitM resistant".

#### Virtual In-Person Proofing
A remote identity proofing process that employs physical, technical and procedural measures that provide sufficient confidence that the remote session can be considered equivalent to a physical, in-person identity proofing process.

#### Weakly Bound Credentials
Credentials that are bound to a subscriber in a manner than can be modified without invalidating the credential.

#### Zeroize
Overwrite a memory location with data consisting entirely of bits with the value zero so that the data is destroyed and not recoverable. This is often contrasted with deletion methods that merely destroy reference to data within a file system rather than the data itself.

#### Zero-knowledge Password Protocol
A password based authentication protocol that allows a claimant to authenticate to a verifier without revealing the password to the verifier. Examples of such protocols are EKE, SPEKE and SRP.

### A.2. Acronyms