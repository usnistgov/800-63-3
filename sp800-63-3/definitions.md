<a name="def-and-acr"></a>

<div class="breaker"></div>

## Appendix A&mdash;Definitions and Abbreviations

*This section is normative.*

### A.1 Definitions

A wide variety of terms is used in the realm of authentication. While many terms' definitions are consistent with earlier versions of SP 800-63, some have changed in this revision. Many of these terms lack a single, consistent definition, warranting careful attention to how the terms are defined here.

#### <a name="access"></a> Access
To make contact with one or more discrete functions of an online, digital service.

#### Active Attack
An attack on the authentication protocol where the attacker transmits data to the claimant, Credential Service Provider (CSP), verifier, or Relying Party (RP). Examples of active attacks include man-in-the-middle (MitM), impersonation, and session hijacking.

#### Address of Record
The validated and verified location (physical or digital) where an individual can receive communications using approved mechanisms.

#### Applicant
A subject undergoing the processes of enrollment and identity proofing.

#### <a name="approved"></a> Approved Cryptography
Federal Information Processing Standard (FIPS)-approved or NIST recommended. An algorithm or technique that is either 1) specified in a FIPS or NIST Recommendation, or 2) adopted in a FIPS or NIST Recommendation.

#### Assertion
A statement from a verifier to an RP that contains information about a subscriber. Assertions may also contain verified attributes.

#### Assertion Reference
A data object, created in conjunction with an assertion, that identifies the verifier and includes a pointer to the full assertion held by the verifier.

#### Asymmetric Keys
Two related keys, comprised of a public key and a private key, that are used to perform complementary operations such as encryption and decryption or signature verification and generation.

#### Attack
An unauthorized entity's attempt to fool a verifier or RP into believing that the unauthorized individual in question is the subscriber.

#### Attacker
A party, including an insider, who acts with malicious intent to compromise a system.

#### Attribute
A quality or characteristic ascribed to someone or something.

#### Attribute Bundle
A packaged set of attributes, usually contained within an assertion. Attribute bundles offer RPs a simple way to retrieve the most relevant attributes they need from IdPs. Attribute bundles are synonymous with OpenID Connect scopes [[OpenID Connect Core 1.0]](#OpenIDConnectCore).

#### Attribute Reference
A statement asserting a property of a subscriber without necessarily containing identity information, independent of format. For example, for the attribute "birthday," a reference could be "older than 18" or "born in December."

#### Attribute Value
A complete statement asserting a property of a subscriber, independent of format. For example, for the attribute "birthday," a value could be "12/1/1980" or "December 1, 1980."

#### Authenticate
See [Authentication](#authentication).

#### Authenticated Protected Channel
An encrypted communication channel that uses approved cryptography where the connection initiator (client) has authenticated the recipient (server). Authenticated protected channels provide confidentiality and MitM protection and are frequently used in the user authentication process. Transport Layer Security (TLS) [[BCP 195]](#bcp195) is an example of an authenticated protected channel where the certificate presented by the recipient is verified by the initiator. Unless otherwise specified, authenticated protected channels do not require the server to authenticate the client. Authentication of the server is often accomplished through a certificate chain leading to a trusted root rather than individually with each server.

#### <a name="authentication"></a> Authentication
Verifying the identity of a user, process, or device, often as a prerequisite to allowing access to a system's resources.

#### <a name="af"></a> Authentication Factor
The three types of authentication factors are *something you know*, *something you have*, and *something you are*. Every authenticator has one or more authentication factors.

#### Authentication Intent
The process of confirming the claimant's intent to authenticate or reauthenticate by including a process requiring user intervention in the authentication flow. Some authenticators (e.g., OTP devices) establish authentication intent as part of their operation, others require a specific step, such as pressing a button, to establish intent. Authentication intent is a countermeasure against use by malware of the endpoint as a proxy for authenticating an attacker without the subscriber's knowledge.

#### Authentication Protocol
A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of one or more valid authenticators to establish their identity, and, optionally, demonstrates that the claimant is communicating with the intended verifier.

#### Authentication Protocol Run
An exchange of messages between a claimant and a verifier that results in authentication (or authentication failure) between the two parties.

#### Authentication Secret
A generic term for any secret value that an attacker could use to impersonate the subscriber in an authentication protocol.

These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The authenticator secret is the canonical example of a long-term authentication secret, while the authenticator output, if it is different from the authenticator secret, is usually a short-term authentication secret.

#### <a name="authenticator"></a> Authenticator
Something the claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant's identity. In previous editions of SP 800-63, this was referred to as a *token*.

#### Authenticator Assurance Level (AAL)
A category describing the strength of the authentication process.

#### <a name="authenticatoroutput"></a> Authenticator Output
The output value generated by an authenticator. The ability to generate valid authenticator outputs on demand proves that the claimant possesses and controls the authenticator. Protocol messages sent to the verifier are dependent upon the authenticator output, but they may or may not explicitly contain it.

#### <a name="authenticatorsecret"></a> Authenticator Secret
The secret value contained within an authenticator.

#### Authenticator Type
A category of authenticators with common characteristics. Some authenticator types provide one authentication factor, others provide two.

#### Authenticity
The property that data originated from its purported source.

#### Authoritative Source
An entity that has access to, or verified copies of, accurate information from an issuing source such that a CSP can confirm the validity of the identity evidence supplied by an applicant during identity proofing. An issuing source may also be an authoritative source. Often, authoritative sources are determined by a policy decision of the agency or CSP before they can be used in the identity proofing validation phase.

#### Authorize
A decision to grant [access](#access), typically automated by evaluating a subject's attributes.

#### Back-Channel Communication
Communication between two systems that relies on a direct connection (allowing for standard protocol-level proxies), without using redirects through an intermediary such as a browser. This can be accomplished using HTTP requests and responses.

#### Bearer Assertion
The assertion a party presents as proof of identity, where possession of the assertion itself is sufficient proof of identity for the assertion bearer.

#### Binding
An association between a subscriber identity and an authenticator or given subscriber session.

#### Biometrics
Automated recognition of individuals based on their biological and behavioral characteristics.

#### Challenge-Response Protocol
An authentication protocol where the verifier sends the claimant a challenge (usually a random value or nonce) that the claimant combines with a secret (such as by hashing the challenge and a shared secret together, or by applying a private key operation to the challenge) to generate a response that is sent to the verifier. The verifier can independently verify the response generated by the claimant (such as by re-computing the hash of the challenge and the shared secret and comparing to the response, or performing a public key operation on the response) and establish that the claimant possesses and controls the secret.

#### Claimant
A subject whose identity is to be verified using one or more authentication protocols.

#### Claimed Address
The physical location asserted by a subject where they can be reached. It includes the individual's residential street address and may also include their mailing address.

For example, a person with a foreign passport living in the U.S. will need to give an address when going through the identity proofing process. This address would not be an "address of record" but a "claimed address."

#### Claimed Identity
An applicant's declaration of unvalidated and unverified personal attributes.

#### Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA)
An interactive feature added to web forms to distinguish whether a human or automated agent is using the form. Typically, it requires entering text corresponding to a distorted image or a sound stream.

#### Credential
An object or data structure that authoritatively binds an identity - via an identifier or identifiers - and (optionally) additional attributes, to at least one authenticator possessed and controlled by a subscriber.

While common usage often assumes that the subscriber maintains the credential, these guidelines also use the term to refer to electronic records maintained by the CSP that establish binding between the subscriber's authenticator(s) and identity.

#### Credential Service Provider (CSP)
A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. A CSP may be an independent third party or issue credentials for its own use.

#### Cross-site Request Forgery (CSRF)
An attack in which a subscriber currently authenticated to an RP and connected through a secure session browses to an attacker's website, causing the subscriber to unknowingly invoke unwanted actions at the RP.

For example, if a bank website is vulnerable to a CSRF attack, it may be possible for a subscriber to unintentionally authorize a large money transfer, merely by viewing a malicious link in a webmail message while a connection to the bank is open in another browser window.

#### Cross-site Scripting (XSS)
A vulnerability that allows attackers to inject malicious code into an otherwise benign website. These scripts acquire the permissions of scripts generated by the target website and can therefore compromise the confidentiality and integrity of data transfers between the website and client. Websites are vulnerable if they display user-supplied data from requests or forms without sanitizing the data so that it is not executable.

#### Cryptographic Authenticator
An authenticator where the secret is a cryptographic key.

#### Cryptographic Key
A value used to control cryptographic operations, such as decryption, encryption, signature generation, or signature verification. For the purposes of these guidelines, key requirements shall meet the minimum requirements stated in Table 2 of NIST SP 800-57 Part 1.

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
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation, but not confidentiality protection.  

#### Diversionary
In regards to KBV, a multiple-choice question for which all answers provided are incorrect, requiring the applicant to select an option similar to "none of the above."

#### Eavesdropping Attack
An attack in which an attacker listens passively to the authentication protocol to capture information that can be used in a subsequent active attack to masquerade as the claimant.

#### Electronic Authentication (E-Authentication)
See *Digital Authentication*.

#### <a name="enroll"></a> Enrollment
The process through which an applicant applies to become a subscriber of a CSP and the CSP validates the applicant's identity.

#### Entropy
A measure of the amount of uncertainty an attacker faces to determine the value of a secret. Entropy is usually stated in bits. A value having *n* bits of entropy has the same degree of uncertainty as a uniformly distributed *n*-bit random value.

#### Federal Information Processing Standard (FIPS)
Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves the standards and guidelines that the National Institute of Standards and Technology (NIST) develops for federal computer systems. NIST issues these standards and guidelines as Federal Information Processing Standards (FIPS) for government-wide use. NIST develops FIPS when there are compelling federal government requirements, such as for security and interoperability, and there are no acceptable industry standards or solutions. See background information for more details.

FIPS documents are available online on the FIPS home page: <http://www.nist.gov/itl/fips.cfm>

#### Federation
A process that allows the conveyance of identity and authentication information across a set of networked systems.

#### Federation Assurance Level (FAL)
A category describing the assertion protocol used by the federation to communicate authentication and attribute information (if applicable) to an RP.

#### Federation Proxy
A component that acts as a logical RP to a set of IdPs and a logical IdP to a set of RPs, bridging the two systems with a single component. These are sometimes referred to as "brokers".

#### Front-Channel Communication
Communication between two systems that relies on redirects through an intermediary such as a browser. This is normally accomplished by appending HTTP query parameters to URLs hosted by the receiver of the message.

#### Hash Function
A function that maps a bit string of arbitrary length to a fixed-length bit string. Approved hash functions satisfy the following properties:

1. One-way - It is computationally infeasible to find any input that maps to any pre-specified output; and

2. Collision resistant - It is computationally infeasible to find any two distinct inputs that map to the same output.

#### Identity
An attribute or set of attributes that uniquely describe a subject within a given context.

#### Identity Assurance Level (IAL)
A category that conveys the degree of confidence that the applicant's claimed identity is their real identity.

#### Identity Evidence
Information or documentation provided by the applicant to support the claimed identity. Identity evidence may be physical (e.g. a driver license) or digital (e.g. an assertion generated and issued by a CSP based on the applicant successfully authenticating to the CSP).

#### Identity Proofing
The process by which a CSP collects, validates, and verifies information about a person.

#### Identity Provider (IdP)
The party that manages the subscriber’s primary authentication credentials and issues assertions derived from those credentials. This is commonly the CSP as discussed within this document suite.

#### Issuing Source
An authority responsible for the generation of data, digital evidence (such as assertions), or physical documents that can be used as identity evidence.

#### Kerberos
A widely used authentication protocol developed at MIT. In "classic" Kerberos, users share a secret password with a Key Distribution Center (KDC). The user (Alice) who wishes to communicate with another user (Bob) authenticates to the KDC and the KDC furnishes a "ticket" to use to authenticate with Bob.

See [SP 800-63C](sp800-63c.html) Section 11.2 for more information.

#### Knowledge-Based Verification (KBV)
Identity verification method based on knowledge of private information associated with the claimed identity. This is often referred to as knowledge-based authentication (KBA) or knowledge-based proofing (KBP).

#### Man-in-the-Middle Attack (MitM)
An attack in which an attacker is positioned between two communicating parties in order to intercept and/or alter data traveling between them. In the context of authentication, the attacker would be positioned between claimant and verifier, between registrant and CSP during enrollment, or between subscriber and CSP during authenticator binding.

#### Memorized Secret
A type of authenticator comprised of a character string intended to be memorized or memorable by the subscriber, permitting the subscriber to demonstrate *something they know* as part of an authentication process.

#### Message Authentication Code (MAC)
A cryptographic checksum on data that uses a symmetric key to detect both accidental and intentional modifications of the data. MACs provide authenticity and integrity protection, but not non-repudiation protection.

#### Mobile Code
Executable code that is normally transferred from its source to another computer system for execution. This transfer is often through the network (e.g., JavaScript embedded in a web page) but may transfer through physical media as well.

#### Multi-Factor
A characteristic of an authentication system or an authenticator that requires more than one distinct [authentication factor](#af) for successful authentication. MFA can be performed using a single authenticator that provides more than one factor or by a combination of authenticators that provide different factors.

The three authentication factors are something you know, something you have, and something you are.

#### <a name="mfa-definition"></a>Multi-Factor Authentication (MFA)
An authentication system that requires more than one distinct [authentication factor](#af) for successful authentication. Multi-factor authentication can be performed using a multi-factor authenticator or by a combination of authenticators that provide different factors.

The three authentication factors are *something you know*, *something you have*, and *something you are*.

#### Multi-Factor Authenticator
An authenticator that provides more than one distinct authentication factor, such as a cryptographic authentication device with an integrated biometric sensor that is required to activate the device.

#### Network
An open communications medium, typically the Internet, used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the network's security; it is assumed to be open and subject to active (e.g., impersonation, man-in-the-middle, session hijacking) and passive (e.g., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP, RP).

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

#### Personal Identification Number (PIN)
A memorized secret typically consisting of only decimal digits.

#### Personal Information

See *Personally Identifiable Information*.

#### Personally Identifiable Information (PII)
As defined by [OMB Circular A-130](#A-130), Personally Identifiable Information is information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual.

#### Pharming
An attack in which an attacker corrupts an infrastructure service such as DNS (Domain Name System) causing the subscriber to be misdirected to a forged verifier/RP, which could cause the subscriber to reveal sensitive information, download harmful software, or contribute to a fraudulent act.

#### Phishing
An attack in which the subscriber is lured (usually through an email) to interact with a counterfeit verifier/RP and tricked into revealing information that can be used to masquerade as that subscriber to the real verifier/RP.

#### Possession and Control of an Authenticator
The ability to activate and use the authenticator in an authentication protocol.

#### Practice Statement
A formal statement of the practices followed by the parties to an authentication process (e.g., CSP or verifier). It usually describes the parties' policies and practices and can become legally binding.

#### Private Credentials
Credentials that cannot be disclosed by the CSP because the contents can be used to compromise the authenticator.

#### Private Key
The secret part of an asymmetric key pair that is used to digitally sign or decrypt data.

#### Presentation Attack
Presentation to the biometric data capture subsystem with the goal of interfering with the operation of the biometric system.

#### Presentation Attack Detection (PAD)
Automated determination of a presentation attack. A subset of presentation attack determination methods, referred to as *liveness detection*, involve measurement and analysis of anatomical characteristics or involuntary or voluntary reactions, in order to determine if a biometric sample is being captured from a living subject present at the point of capture.

#### Protected Session
A session wherein messages between two participants are encrypted and integrity is protected using a set of shared secrets called session keys.

A participant is said to be *authenticated* if, during the session, they prove possession of one or more authenticators in addition to the session keys, and if the other party can verify the identity associated with the authenticator(s). If both participants are authenticated, the protected session is said to be *mutually authenticated*.

#### Protected Session
A session established on an authenticated protected channel.

#### Pseudonym
A name other than a legal name.

#### Pseudonymity
The use of a pseudonym to identify a subject.

#### Pseudonymous Identifier
A meaningless but unique number that does not allow the RP to infer anything regarding the subscriber but which does permit the RP to associate multiple interactions with the subscriber's claimed identity.

#### Public Credentials
Credentials that describe the binding in a way that does not compromise the authenticator.

#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.

#### Public Key Certificate
A digital document issued and digitally signed by the private key of a certificate authority that binds an identifier to a subscriber to a public key. The certificate indicates that the subscriber identified in the certificate has sole control and access to the private key. See also [[RFC 5280]](sp800-63b.html#RFC5280).

#### Public Key Infrastructure (PKI)
A set of policies, processes, server platforms, software, and workstations used for the purpose of administering certificates and public-private key pairs, including the ability to issue, maintain, and revoke public key certificates.

#### Reauthentication
The process of confirming the subscriber's continued presence and intent to be authenticated during an extended usage session.

#### Registration
See [Enrollment](#enroll).

#### Relying Party (RP)
An entity that relies upon the subscriber's authenticator(s) and credentials or a verifier's assertion of a claimant's identity, typically to process a transaction or grant access to information or a system.

#### Remote
(*In the context of remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization's security controls.

#### Replay Attack
An attack in which the attacker is able to replay previously captured messages (between a legitimate claimant and a verifier) to masquerade as that claimant to the verifier or vice versa.

#### Replay Resistance
The property of an authentication process to resist replay attacks, typically by use of an authenticator output that is valid only for a specific authentication.

#### Restricted
An authenticator type, class, or instantiation having additional risk of false acceptance associated with its use that is therefore subject to additional requirements.

#### Risk Assessment
The process of identifying, estimating, and prioritizing risks to organizational operations (including mission, functions, image, or reputation), organizational assets, individuals, and other organizations, resulting from the operation of a system. It is part of risk management, incorporates threat and vulnerability analyses, and considers mitigations provided by security controls planned or in place. Synonymous with risk analysis.

#### Risk Management
The program and supporting processes to manage information security risk to organizational operations (including mission, functions, image, reputation), organizational assets, individuals, other organizations, and includes: (i) establishing the context for risk-related activities; (ii) assessing risk; (iii) responding to risk once determined; and (iv) monitoring risk over time.

#### Salt
A non-secret value used in a cryptographic process, usually to ensure that the results of computations for one instance cannot be reused by an attacker.

#### Secure Sockets Layer (SSL)
See *Transport Layer Security (TLS)*.

#### Session
A persistent interaction between a subscriber and an endpoint, either an RP or a CSP. A session begins with an authentication event and ends with a session termination event. A session is bound by use of a session secret that the subscriber's software (a browser, application, or OS) can present to the RP or CSP in lieu of the subscriber's authentication credentials.

#### Session Hijack Attack
An attack in which the attacker is able to insert himself or herself between a claimant and a verifier subsequent to a successful authentication exchange between the latter two parties. The attacker is able to pose as a subscriber to the verifier or vice versa to control session data exchange. Sessions between the claimant and the RP can be similarly compromised.

#### Shared Secret
A secret used in authentication that is known to the subscriber and the verifier.

#### Side-Channel Attack
An attack enabled by leakage of information from a physical cryptosystem. Characteristics that could be exploited in a side-channel attack include timing, power consumption, and electromagnetic and acoustic emissions.

#### <a name="sf"></a> Single-Factor
A characteristic of an authentication system or an authenticator that requires only one authentication factor (something you know, something you have, or something you are) for successful authentication.

#### Social Engineering
The act of deceiving an individual into revealing sensitive information, obtaining unauthorized access, or committing fraud by associating with the individual to gain confidence and trust.

#### Special Publication (SP)
A type of publication issued by NIST. Specifically, the SP 800-series reports on the Information Technology Laboratory's research, guidelines, and outreach efforts in computer security, and its collaborative activities with industry, government, and academic organizations.

#### Subject
A person, organization, device, hardware, network, software, or service.

#### Subscriber
A party who has received a credential or authenticator from a CSP.

#### Symmetric Key
A cryptographic key used to perform both the cryptographic operation and its inverse. For example, to encrypt and decrypt or create a message authentication code and to verify the code.

#### Token
See [Authenticator](#authenticator).

#### Token Authenticator
See [Authenticator Output](#authenticatoroutput).

#### Token Secret
See [Authenticator Secret](#authenticatorsecret).

#### Transaction

A discrete event between a user and a system that supports a business or programmatic purpose. A government digital system may have multiple categories or types of transactions, which may require separate analysis within the overall digital identity risk assessment.

#### Transport Layer Security (TLS)
An authentication and security protocol widely implemented in browsers and web servers. TLS is defined by RFC 5246. TLS is similar to the older SSL protocol, and TLS 1.0 is effectively SSL version 3.1. NIST SP 800-52, Guidelines for the Selection and Use of Transport Layer Security (TLS) Implementations [[SP 800-52]](#SP800-52), specifies how TLS is to be used in government applications.

#### Trust Anchor
A public or symmetric key that is trusted because it is directly built into hardware or software, or securely provisioned via out-of-band means, rather than because it is vouched for by another trusted entity (e.g. in a public key certificate). A trust anchor may have name or policy constraints limiting its scope.

#### Usability
Per [ISO/IEC 9241-11](#ISO9241): Extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency, and satisfaction in a specified context of use.

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

#### Zero-Knowledge Password Protocol
A password-based authentication protocol that allows a claimant to authenticate to a verifier without revealing the password to the verifier. Examples of such protocols are EKE, SPEKE and SRP.

### A.2 Abbreviations

Selected abbreviations in these guidelines are defined below.

|Abbreviation|Term|
|:-----|:---------|
|ABAC|Attribute Based Access Control|
|AAL|Authenticator Assurance Level|
|AS|Authentication Server|
|CAPTCHA|Completely Automated Public Turing test to tell Computer and Humans Apart|
|CSP|Credential Service Provider|
|CSRF|Cross-site Request Forgery|
|XSS|Cross-site Scripting|
|DNS|Domain Name System|
|EO|Executive Order|
|FACT Act|Fair and Accurate Credit Transaction Act of 2003|
|FAL|Federation Assurance Level|
|FEDRAMP|Federal Risk and Authorization Management Program|
|FMR|False Match Rate|
|FNMR|False Non-Match Rate|
|FIPS|Federal Information Processing Standard|
|FISMA|Federal Information Security Modernization Act|
|IAL|Identity Assurance Level|
|IM|Identity Manager|
|IdP|Identity Provider|
|IoT|Internet of Things|
|ISO/IEC|International Organization for Standardization/International Electrotechnical Commission|
|JOSE|JSON Object Signing and Encryption|
|JSON|JavaScript Object Notation |
|JWT|JSON Web Token|
|KBA|Knowledge-Based Authentication|
|KBV|Knowledge-Based Verification|
|KDC|Key Distribution Center|
|LOA|Level of Assurance|
|MAC|Message Authentication Code|
|MitM|Man-in-the-Middle|
|MitMA|Man-in-the-Middle Attack|
|MFA|Multi-Factor Authentication|
|N/A|Not Applicable|
|NARA|National Archives and Records Administration|
|OMB|Office of Management and Budget|
|OTP|One-Time Password|
|PAD|Presentation Attack Detection|
|PHI|Personal Health Information|
|PIA|Privacy Impact Assessment |
|PII|Personally Identifiable Information|
|PIN|Personal Identification Number|
|PKI|Public Key Infrastructure |
|PL|Public Law|
|PSTN|Public Switched Telephone Network|
|RA|Registration Authority|
|RMF|Risk Management Framework|
|RP|Relying Party|
|SA&A|Security Authorization & Accreditation|
|SAML|Security Assertion Markup Language|
|SAOP|Senior Agency Official for Privacy|
|SSL|Secure Sockets Layer|
|SMS|Short Message Service|
|SP|Special Publication|
|SORN|System of Records Notice|
|TEE|Trusted Execution Environment|
|TGS|Ticket Granting Server|
|TGT|Ticket Granting Ticket|
|TLS|Transport Layer Security|
|TPM|Trusted Platform Module|
|VOIP|Voice-over-IP|
