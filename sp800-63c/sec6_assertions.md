<div class="breaker"></div>
<a name="assertions"></a>

## 6 Assertions

*This section is normative.*

An assertion used for authentication is a packaged set of attribute values or attribute references about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including: assertion metadata, attribute values and attribute references about the subscriber, and other information that the RP can leverage (such as restrictions and expiration time). While the assertion's primary function is to authenticate the user to an RP, the information conveyed in the assertion can be used by the RP for a number of use cases &mdash; for example, authorization or personalization of a website. These guidelines do not restrict RP use cases nor the type of protocol or data payload used to federate an identity, provided the chosen solution meets all mandatory requirements contained herein.

Assertions MAY represent only an authentication event, or MAY also represent attribute values and attribute references regarding the subscriber.

All assertions SHALL include the following assertion metadata:

1. Subject: An identifier for the party that the assertion is about (i.e., the subscriber).
2. Issuer: An identifier for the IdP that issued the assertion.
3. Audience: An identifier for the party intended to consume the assertion (i.e., the RP).
4. Issuance: A timestamp indicating when the IdP issued the assertion.
5. Expiration: A timestamp indicating when the assertion expires and SHALL no longer be accepted as valid by the RP (i.e., the expiration of the assertion and not the expiration of the session at the RP).
6. Identifier: A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
7. Signature: Digital signature or message authentication code (MAC), including key identifier or public key associated with the IdP, for the entire assertion.
8. Authentication Time: A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event (if available).

Assertions MAY also include the following information:

1. Key binding: Public key or key identifier of subscriber-held key to demonstrate their binding with the assertion described in [Section 6.1.2](#holderofkey).
2. Attribute values and attribute references: Information about the subscriber.
3. Attribute metadata: Additional information about one or more subscriber attributes, such as that described in NIST Internal Report 8112 [[NISTIR 8112]](#nistir8112).

Assertions SHOULD specify the AAL when an authentication event is being asserted and IAL when identity proofed attributes (or references based thereon) are being asserted. If not specified, the RP SHALL NOT assign any specific IAL or AAL to the assertion.

An RP SHALL treat subject identifiers as not inherently globally unique. Instead, the value of the assertion's subject identifier is usually in a namespace under the assertion issuer's control. This allows an RP to talk to multiple IdPs without incorrectly conflating subjects from different IdPs.

Assertions MAY include additional attributes. [Section 7](#presentation) contains privacy requirements for presenting attributes in assertions. The RP MAY fetch additional identity attributes from the IdP in one or more separate transactions using an authorization credential issued alongside the original assertion. The ability to successfully fetch such additional attributes SHALL NOT be treated as equivalent to processing the assertion.

Although details vary based on the exact federation protocol in use, an assertion SHOULD be used only to represent a single login event at the RP. After the RP consumes the assertion, session management by the RP comes into play (see [SP 800-63B Section 7](sp800-63b.html#sec7)); an assertion SHALL NOT be used past the expiration time contained therein. However, the expiration of the session at the RP MAY occur prior to the assertion's expiration. See [Section 5.3](#federation-session) for more information.

The assertion's lifetime is the time between its issuance and its expiration. This lifetime needs to be long enough to allow the RP to process the assertion and create a local application session for the subscriber, but should not be longer than necessary for such establishment. Long-lived assertions have a greater risk of being stolen or replayed; a short assertion lifetime mitigates this risk. Assertion lifetimes SHALL NOT be used to limit the session at the RP. See [Section 5.3](#federation-session) for more information.

### 6.1 Assertion Binding <a name="assertion-binding"></a>

Assertion binding can be classified based on whether presentation by a claimant of an assertion, or an assertion reference, is sufficient for binding to the subscriber, or if the RP requires additional proof that the assertion is bound to the subscriber.

#### 6.1.1 Bearer Assertions <a name="bearer"></a>

A bearer assertion can be presented by any party as proof of the bearer's identity. If an attacker can capture or manufacture a valid assertion or assertion reference representing a subscriber and can successfully present that assertion or reference to the RP, then the attacker could be able to impersonate the subscriber at that RP.

Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Section 7.1](#back-channel)), additional controls MAY be placed on the transaction (such as identification of the RP and assertion injection protections) that help further protect the RP from fraudulent activity.

#### 6.1.2 <a name="holderofkey"></a>Holder-of-Key Assertions
A holder-of-key assertion contains a reference to a key possessed by and representing the subscriber. The key referenced in a holder-of-key represents the subscriber, not any other party in the system including the browser, IdP, or RP. Note that the reference to the key is asserted (and signed) by the issuer of the assertion.

When the RP receives the holder-of-key assertion, the subscriber proves possession of the key referenced in the assertion directly to the RP. While the subscriber could also have used a key-based means of authenticating to the IdP, the primary authentication at the IdP and the federated authentication at the RP are considered separately and are not assumed to use the same keys or related sessions.

In proving possession of the subscriber's key to the RP, the claimant also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen holder-of-key assertion issued to a subscriber, since the attacker would need to steal the referenced key material as well.

The following requirements apply to all holder-of-key assertions:

1. The subscriber SHALL prove possession of that key to the RP, in addition to presentation of the assertion itself.
2. An assertion containing a reference to a key held by the subscriber for which key possession has not been proven SHALL be considered a [bearer assertion](#bearer) by the RP.
3. Reference to a given key SHALL be trusted at the same level as all other information within the assertion.
4. The assertion SHALL NOT include an unencrypted private or symmetric key to be used with holder-of-key presentation.
5. The key MAY be distinct from any key used by the subscriber to authenticate to the IdP.
6. The key MAY be a symmetric key or a public key that corresponds to a private key.
7. The RP MAY verify the claimant's possession of the key in conjunction with the IdP, for example, by requesting that the IdP verify a signature or MAC calculated by the claimant in response to a cryptographic challenge.


### 6.2 Assertion Protection

Independent of the binding mechanism (discussed in [Section 6.1](#assertion-binding)) or the federation model used to obtain them (described in [Section 5.1](#federation-model)), assertions SHALL include a set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs. The protections required are dependent on the details of the use case being considered, and recommended protections are listed here.

#### <a name="assertion-id"></a>6.2.1 Assertion Identifier

Assertions SHALL be sufficiently unique to permit unique identification by the target RP. Assertions MAY accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques.

#### 6.2.2 <a name="signed-assertion"></a>Signed Assertion

Assertions SHALL be cryptographically signed by the issuer (IdP). The RP SHALL validate the digital signature or MAC of each such assertion based on the issuer's key. This signature SHALL cover the entire assertion, including its identifier, issuer, audience, subject, and expiration.

The assertion signature SHALL either be a digital signature using asymmetric keys or a MAC using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP SHALL be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verifying digital signatures MAY be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography SHALL be used.

#### 6.2.3 <a name="encrypted-assertion"></a>Encrypted Assertion

When encrypting assertions, the IdP SHALL encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP SHALL be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption MAY be fetched by the IdP in a secure fashion at runtime, such as through an HTTPS URL hosted by the RP.

All encryption of assertions SHALL use approved cryptography.

When assertions are passed through third parties, such as a browser, the actual assertion SHALL be encrypted. For example, a SAML assertion can be encrypted using XML-Encryption, or an OpenID Connect ID Token can be encrypted using JSON Web Encryption (JWE). For assertions that are passed directly between IdP and RP, the actual assertion MAY be encrypted. If it is not, the assertion SHALL be sent over an authenticated protected channel.

> Note: Assertion encryption is required at FAL2 and FAL3.

#### 6.2.4 Audience Restriction

Assertions SHALL use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs SHALL check that the audience of an assertion contains an identifier for their RP to prevent the injection and replay of an assertion generated for one RP at another RP.

#### <a name="ppi"></a>6.3 Pairwise Pseudonymous Identifiers

In some circumstances, it is desirable to prevent the subscriber's account at the IdP from being easily linked at multiple RPs through use of a common identifier.

#### 6.3.1 General Requirements

When using pairwise pseudonymous subject identifiers within the assertions generated by the IdP for the RP, the IdP SHALL generate a different identifier for each RP as described in [Section 6.3.2](#ppi-gen) below.

When pairwise pseudonymous identifiers are used with RPs alongside attributes, it may still be possible for multiple colluding RPs to re-identify a subscriber by correlation across systems using these identity attributes. For example, if two independent RPs each see the same subscriber identified with different pairwise pseudonymous identifiers, they could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier in the respective assertions. Privacy policies SHOULD prohibit such correlation, and pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation.

Note that in a proxied federation model, the initial IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is generally established between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs. The proxy SHALL NOT disclose the mapping between the pairwise pseudonymous identifier and any other identifiers to a third party or use the information for any purpose other than federated authentication, related fraud mitigation, to comply with law or legal process, or in the case of a specific user request for the information.

#### 6.3.2 <a name="ppi-gen"></a>Pairwise Pseudonymous Identifier Generation

Pairwise pseudonymous identifiers SHALL contain no identifying information about the subscriber. They SHALL also be unguessable by a party having access to some information identifying the subscriber. Pairwise pseudonymous identifiers MAY be generated randomly and assigned to subscribers by the IdP or MAY be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key). Normally, the identifiers SHALL only be known by and used by one pair of endpoints (e.g., IdP-RP). However, an IdP MAY generate the same identifier for a subscriber at multiple RPs at the request of those RPs, provided:

* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
* All RPs sharing an identifier consent to being correlated in such a manner.

The RPs SHALL conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. See [Section 9.2](#notice) for further privacy considerations.

The IdP SHALL ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a set of correlated RPs by fraudulently posing as part of that set.
