<div class="breaker"></div>
<a name="sec5"></a>

## 5. Assertions

An assertion is a packaged set of attribute values or attribute claims about or associated with an authenticated subscriber that is passed from the IdP to the RP in a federated identity system. Assertions contain a variety of information, including assertion metadata, attribute values and attribute claims about the subscriber, and other information that the RP can leverage, such as restrictions, and expiration time.

Assertions MAY represent only an authentication event, or MAY also represent attribute values and attribute claims regarding the subscriber. 

All assertions SHALL include the following assertion metadata:

- Subject - An identifier for the party that the assertion is about (the subscriber), usually within the namespace control of the issuer (the IdP).
- Issuer - An identifier for the IdP that issued the assertion.
- Audience - An identifier for the party intended to consume the assertion (the RP).
- Issuance - A timestamp indicating when the assertion was issued by the IdP.
- Expiration - A timestamp indicating when the assertion expires and SHALL no longer be accepted as valid by the RP (note that this is the expiration of the assertion and not the expiration of the session at the RP).
- Identifier - A value uniquely identifying this assertion, used to prevent attackers from replaying prior assertions.
- Signature - Digital signature or message authentication code (MAC), including key identifier or public key associated with the IdP, for the entire assertion.
- Authentication Time - A timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event (if available).

Assertions MAY also include the following information:

- Key binding - Public key or key identifier of a key held by the subscriber to demonstrate their binding with the assertion.
- Attribute values and attribute claims - Information about the subscriber.
- Attribute metadata - Additional information about one or more subscriber attributes, such as that described in [[NISTIR 8112]](#nistir8112).

Assertions SHOULD specify the AAL when an authentication event is being asserted and IAL when identity proofed attributes or claims based thereon are being asserted. The IAL and AAL MAY be specified in an alternate form, such as a composite level of assurance. If not specified, the RP SHALL NOT assign any specific IAL or AAL to the assertion.

Assertions MAY include additional attributes. Refer to [Section 6](#sec6) for privacy requirements on presenting attributes in assertions. The RP MAY fetch additional identity attributes from the IdP in one or more separate transactions using an authorization credential issued alongside the original assertion. The ability to successfully fetch such additional attributes SHALL NOT be treated as equivalent to processing of the assertion.

Although details vary based on the exact federation protocol in use, an assertion SHOULD be used only to represent a single login event at the RP. After the RP consumes the assertion, [session management](sp800-63b.html#sec7) by the RP comes into play; the assertion SHALL NOT be used past the expiration time contained therein. However, the expiration of the session at the RP MAY occur prior to the expiration of the assertion. See [section 4.3](#federation-session) for more information.

### 5.1. Assertion Binding

An assertion can be classified based on whether presentation by a claimant of an assertion reference or the assertion itself is sufficient for establishing the binding between the subscriber and the assertion, or if a stronger binding is required.

#### 5.1.1. Bearer Assertions

A bearer assertion can be presented by any party as proof of the bearer's identity. If an attacker is able to capture or manufacture a valid assertion or assertion reference representing a subscriber, and that attacker is able to successfully present that assertion or reference to the RP, then the attacker MAY be able to impersonate the subscriber at that RP. 

Note that mere possession of a bearer assertion or reference is not always enough to impersonate a subscriber. For example, if an assertion is presented in the back-channel federation model (described in [Section 6.1](#sec6-1)), additional controls MAY be placed on the transaction (such as identification of the RP and assertion injection protections) that help to further protect the RP from fraudulent activity.

#### 5.1.2. Holder-of-Key Assertions

A holder-of-key assertion contains a reference to a key possessed by and representing the subscriber, and the subscriber SHALL prove possession of that key in addition to presentation of the assertion itself. The key MAY be a symmetric key or a public key that corresponds to a private key. An assertion containing a reference to a key held by the subscriber for which key possession has not been proven SHALL be considered a bearer assertion by the RP.

The key referenced in a holder-of-key represents the subscriber, not any other party in the system including the browser, IdP, or RP. This key MAY be distinct from any key used by the subscriber to authenticate to the IdP.

In proving possession of the subscriber's secret, the claimant also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen holder-of-key assertion issued to a subscriber, since the attacker would need to steal the referenced key material as well. 

Note that the reference to the key is asserted (and signed) by the issuer of the assertion; reference to a given key SHALL be trusted at the same level as all other information within the assertion.

The assertion SHALL NOT include an unencrypted private or symmetric key to be used with holder-of-key presentation. The RP MAY verify the claimant's possession of the key in conjunction with the IdP, for example, by requesting that the IdP verify a signature or MAC calculated by the claimant in response to a cryptographic challenge.

### 5.2. Assertion Protection

Independent of the binding mechanism (discussed above) or the federation model used to obtain them (described in Section 4), assertions SHALL include an appropriate set of protections to prevent attackers from manufacturing valid assertions or reusing captured assertions at disparate RPs.

#### 5.2.1. Assertion Identifier

Assertions SHALL be sufficiently unique to permit unique identification by the target RP. Assertions MAY accomplish this by use of an embedded nonce, issuance timestamp, assertion identifier, or a combination of these or other techniques. 

#### 5.2.2. Signed Assertion

Assertions SHALL be cryptographically signed by the issuer (IdP). The RP SHALL validate the digital signature or MAC of each such assertion based on the issuer's key. This signature SHALL cover all vital fields of the assertion, including its identifier, issuer, audience, subject, and expiration.

The assertion signature SHALL either be a digital signature using asymmetric keys or a message authentication code (MAC) using a symmetric key shared between the RP and issuer. Shared symmetric keys used for this purpose by the IdP SHALL be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for verification of digital signatures MAY be fetched by the RP in a secure fashion at runtime, such as through an HTTPS URL hosted by the IdP. Approved cryptography SHALL be used.

#### 5.2.3. Encrypted Assertion

Assertions MAY be encrypted so as to allow only the intended audience to decrypt the contents. The IdP SHALL encrypt the contents of the assertion using either the RP's public key or a shared symmetric key. Shared symmetric keys used for this purpose by the IdP SHALL be independent for each RP to which they send assertions, and are normally established during registration of the RP. Public keys for encryption MAY be fetched by the IdP in a secure fashion at runtime, such as through an HTTPS URL hosted by the RP. 

All encryption of assertions SHALL use approved cryptography.

#### 5.2.4. Audience Restriction

Assertions SHALL use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs SHALL check the audience of an assertion, if provided, to prevent the injection and replay of an assertion generated for one RP at another RP. 

#### <a name="ppi"></a> 5.2.5. Pairwise Pseudonymous Identifiers

In some circumstances, it is desirable to prevent the subscriber's account at the IdP from being easily linked at multiple RPs through use of a common identifier. When using pairwise pseudonymous subject identifiers within the assertions generated by the IdP for the RP, the IdP SHALL generate a different identifier for each RP as described in [Section 5.2.6](#ppi-gen) below.

When pairwise pseudonymous identifiers are used with RPs alongside attributes, it may still be possible for multiple colluding RPs to reidentify a subscriber by correlation across systems using these identity attributes. For example, if two independent RPs each see the same subscriber identified with different pairwise pseudonymous identifiers, they could still determine that the subscriber is the same person by comparing the name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier in the respective assertions. Privacy policies MAY prohibit such correlation, and pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation. 

Note that in a proxied federation model, the initial IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is generally established between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs. The proxy SHALL NOT disclose the mapping between the pairwise pseudonymous identifier and any other identifiers to a third party or use the information for any purpose other than federated authentication, to comply with law or legal process, or in the case of a specific user request for the information.

#### 5.2.6. <a name="ppi-gen"></a>Pairwise Pseudonymous Identifier Generation

Pairwise pseudonymous identifiers SHALL be opaque, containing no identifying information about the subscriber. They SHALL also be unguessable by a party having access to some information identifying the subscriber. Pairwise pseudonymous identifiers MAY be generated randomly and assigned to subscribers by the IdP or MAY be derived from other subscriber information if the derivation is done in an irreversible, unguessable manner (e.g., using a keyed hash function with a secret key). Normally, the identifiers SHALL only be known by and used by one pair of endpoints (e.g., IdP-RP). However, an IdP MAY generate the same identifier for a subscriber at multiple RPs at the request of those RPs, provided:

* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership; and
* All RPs sharing an identifier consent to being correlated in such a manner.

The RPs SHALL conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. The IdP SHALL ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a correlation by fraudulently posing as part of that correlation.
