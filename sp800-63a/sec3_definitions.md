<a name="sec3"></a>

# 3. Definitions and Abbreviations

There is a wide variety of terms used in the area of authentication. While the definitions of many terms are consistent with earlier versions of SP 800-63, some have changed in this revision. Since there is no single, consistent definition of many of these terms, careful attention to how the terms are defined here is warranted.

The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document family for additional definitions and abbreviations specific to their content.

#### Address of Record
The validated and verified location (physical or digital) where an individual can receive communications using approved mechanisms.

#### Applicant
A party undergoing the processes of registration and identity proofing.

#### Assurance
In the context of [[OMB M-04-04]](#M-04-04) and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of an individual to whom the credential was issued, and 2) the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued.

#### Asymmetric Keys
Two related keys, consisting of a public key and a private key, that are used to perform complementary operations such as encryption and decryption or signature verification and generation.

#### Attack
An attempt by an unauthorized individual to defeat security controls. For example, to cause a credential service provider to register an impostor as the subscriber.

#### Attacker
A party who acts with malicious intent to compromise an information system.

#### Attribute
A quality or characteristic ascribed to someone or something.

#### Attribute Claim
A statement asserting a property of a subscriber without necessarily containing identity information, independent of format. For example, for the attribute 'birthday', a claim could be 'older than 18' or 'born in December'.

#### Attribute Value
A complete statement asserting a property of a subscriber, independent of format. For example, for the attribute 'birthday', a value could be '12/1/1980' or 'December 1, 1980'.

#### Authentication
The process of establishing confidence in the identity of users or information systems.

#### Authentication Protocol
A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of one or more valid authenticators to establish his/her identity. Secure authentication protocols also demonstrate to the claimant that he or she is communicating with the intended verifier.

#### Authenticator
Something that a claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant’s identity. In previous editions of SP 800-63, this was referred to as a *token*.

#### Authenticity
The property that data originated from its purported source.

#### Authoritative Source
An authority that has access to sufficient information from an issuing source that they are able to confirm the validity of a piece of identity evidence. An issuing source may also be an authoritative source.

#### Biometrics
Automated recognition of individuals based on their behavioral and biological characteristics.

In this document, biometrics may be used to unlock authenticators and prevent repudiation of registration.

#### Claimant
A party whose identity is to be verified using one or more authentication protocols.

#### Claimed Address
The physical location asserted by an individual (e.g. an applicant) where he/she can be reached. It includes the residential street address of an individual and may also include the mailing address of the individual.

For example, a person with a foreign passport, living in the U.S., will need to give an address when going through the identity proofing process. This address would not be an “address of record” but a “claimed address.”

#### Credential
An object or data structure that authoritatively binds an identity (and optionally, additional attributes) to an authenticator possessed and controlled by a subscriber.

While common usage often assumes that the credential is maintained by the subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the subscriber’s authenticator and identity.

#### Credential Service Provider (CSP)
A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. The CSP may encompass verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use.

#### Derived Credential
A credential issued based on proof of possession and control of an authenticator associated with a previously issued credential, so as not to duplicate the identity proofing process.

#### Digital Authentication
The process of establishing confidence in user identities electronically presented to an information system. In previous editions of SP 800-63, this was referred to as *Electronic Authentication*.

#### Digital Signature
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation but not confidentiality protection.

#### Electronic Authentication (E-Authentication)
See *Digital Authentication*.

#### Enrollment
The process through which an applicant applies to become a subscriber of a CSP and an RA validates the identity of the applicant on behalf of the CSP.

#### Identity
A set of attributes that uniquely describe a person within a given context.

#### Identity Proofing
The process by which a CSP collects and verifies information about a person for the purpose of issuing credentials to that person.

#### Issuing Source
An authority that is responsible for the generation of data and/or documents that can be used as identity evidence.

#### Knowledge Based Verification
Identity proofing of an individual based on knowledge of information associated with his or her claimed identity in private databases. This is often referred to as knowledge based authentication (KBA) or knowledge based proofing (KBP).

#### Network
An open communications medium, typically the internet, that is used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (i.e., impersonation, man-in-the-middle, session hijacking) and passive (i.e., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP or RP).

#### Personally Identifiable Information (PII)
As defined by OMB Circular A-130, Personally Identifiable Information means information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual.

#### Practice Statement
A formal statement of the practices followed by the parties to an authentication process (i.e., CSP or verifier). It usually describes the policies and practices of the parties and can become legally binding.

#### Protected Session
A session wherein messages between two participants are encrypted and integrity is protected using a set of shared secrets called session keys.

A participant is said to be *authenticated* if, during the session, he, she or it proves possession of one or more authenticators in addition to the session keys, and if the other party can verify the identity associated with the authenticator(s). If both participants are authenticated, the protected session is said to be *mutually authenticated*.

#### Pseudonym
A name other than a legal name.

#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.

#### Remote
(*As in remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization’s security controls.

Note: Any information exchange across the Internet is considered remote.

#### Subscriber
A party who has had their credential bound to an authenticator by a CSP.

#### Token
See *Authenticator*.

#### Token Authenticator
See *Authenticator Output*.

#### Token Secret
See *Authenticator Secret*.

#### Trust Anchor
A public or symmetric key that is trusted because it is directly built into hardware or software, or securely provisioned via out-of-band means, rather than because it is vouched for by another trusted entity (e.g. in a public key certificate).

#### Valid
In reference to an ID, the quality of not being expired or revoked.

#### Virtual In-Person Proofing
A remote identity person proofing process that employs physical, technical and procedural measures that provide sufficient confidence that the remote session can be considered equivalent to a physical, in-person identity proofing encounter.
