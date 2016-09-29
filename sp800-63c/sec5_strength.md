<a name="sec5"></a>

## 5. Assertions

An assertion contains a set of claims or statements about an authenticated subscriber. Assertions can be categorized along multiple orthogonal dimensions, including the characteristics of using the assertion or the protections on the assertion itself.

The core set of claims inside an assertion SHOULD include (but is not limited to):

 - Issuer: an identifier for the party that issued the assertion (the IdP)
 - Subject: an identifier for the party that the assertion is about (the subscriber), usually within the namespace control of the issuer (the IdP)
 - Audience: an identifier for the party intended to consume the assertion (the RP)
 - Issuance: a timestamp indicating when the assertion was issued by the IdP
 - Expiration: a timestamp indicating when the assertion expires and SHALL no longer be accepted as valid by the RP (note that this is not the expiration of the session at the RP)
 - Authentication Time: a timestamp indicating when the IdP last verified the presence of the subscriber at the IdP through a primary authentication event
 - Identifier: a random value uniquely identifying this assertion, used to prevent attackers from manufacturing malicious assertions which would pass other validity checks

These core claims, particularly the issuance and expiration claims, apply to the assertion about the authentication event itself, and not to any additional identity attributes associated with the subscriber, even when those claims are included within the assertion. A subscriber's attributes MAY expire or be otherwise invalidated independently of the expiration or invalidation of the assertion.

Assertions MAY include other additional identity attributes. See sec. 6 for privacy requirements on presenting attributes in assertions. The RP MAY fetch additional identity attributes from the IdP in a separate transaction using an authorization credential issued along side the assertion. 

Although details vary based on the exact federation protocol in use, an assertion SHOULD be used only to represent a single log-in event at the RP. After the RP consumes the assertion, [session management](sp800-63b.html#sec7) at the RP comes into play and the assertion is no longer used directly. The expiration of the assertion SHALL NOT represent the expiration of the session at the RP.

### 5.1. Assertion possession category

An assertion can be classified based on whether possession of the assertion itself is sufficient for representing  the subject of the assertion, or if additional proof is necessary along side the assertion.

#### 5.1.1. Holder-of-Key Assertions

A holder-of-key assertion contains a reference to a symmetric key or a public key (corresponding to a private key) possessed by and representing the subscriber. An RP MAY decide when to require the subscriber to prove possession of the key, depending on the policy of the RP. However, the RP SHALL require the subscriber to prove possession of the key that is referenced in the assertion in parallel with presentation of the assertion itself in order for the assertion to be considered holder-of-key. Otherwise, an assertion containing reference to a key which the user has not proved possession of will be considered a bearer assertion (5.1.2).

The key referenced in a holder-of-key represents the subscriber, not the client. This key MAY be distinct from any key used by the subscriber to authenticate to the IdP.

In proving possession of the subscriber’s secret, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen holder-of-key assertion issued to a subscriber, since the attacker would need to steal the referenced key material as well. 

Note that the reference to the key material in question is asserted by the issuer of the assertion as are any other claims therein, and reference to a given key SHALL be trusted at the same level as all other claims within the assertion itself.

The assertion SHALL NOT include an unencrypted private or symmetric key to be used with holder-of-key presentation.

#### 5.1.2. Bearer Assertions

A bearer assertion can be presented by any party as proof of the bearer's identity, without reference to external materials. If an attacker is able to capture or manufacture a valid assertion representing a subscriber, and that attacker is able to successfully present that assertion to the RP, then the attacker will be able to impersonate the subscriber at that RP. 

Note that mere possession of a bearer assertion is not always enough to impersonate a subscriber. For example, if an assertion is presented in the indirect federation model (Section 6.1), additional controls MAY be placed on the transaction (such as identification of the RP and assertion injection protections) that help to further protect the RP from fraudulent activity.

### 5.2. Assertion protection category

Regardless of the possession mechanism (discussed above) or the federation model used to obtain them (described in section 4), assertions need to include an appropriate set of protections to the assertion data itself to prevent attackers from manufacturing valid assertions or re-using captured assertions at disparate RPs.

#### 5.2.1. Assertion Identifier

Assertions SHALL contain sufficient entropy to prevent an attacker from manufacturing a valid assertion and using it with a target RP. Assertions MAY accomplish this by use of an embedded nonce, timestamp, assertion identifier, or a combination of these or other techniques. 

In the absence of additional cryptographic protections, this source of randomness SHALL function as a shared secret between the IdP and the RP to uniquely identify the assertion in question. 

#### 5.2.2. Signed Assertion

Assertions MAY be cryptographically signed by the IdP, and the RP SHALL validate the signature of each such assertion based on the IdP's key. This signature SHALL cover all vital fields of the assertion, including its issuer, audience, subject, expiration, and any unique identifiers.

The signature MAY be asymmetric based on the published public key of the IdP. In such cases, the RP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the IdP), or the key MAY be provisioned out of band at the RP (during configuration of the RP).

The signature MAY be symmetric based on a key shared out of band between the IdP and the RP. In such circumstances, the IdP SHALL use a different shared key for each RP.

All signatures SHALL use approved signing methods.

#### 5.2.3. Encrypted Assertion

Assertions MAY be encrypted in such a fashion as to allow only the intended audience to decrypt the claims therein. The IdP SHALL encrypt the payload of the assertion using the RP's public key. The IdP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the RP), or the key MAY be provisioned out of band at the IdP (during registration of the RP).

All encrypted objects SHALL use approved encryption methods.

#### 5.2.4. Audience Restriction

All assertions SHOULD use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs SHALL check the audience of an assertion, if provided, to prevent the injection and replay of an assertion generated for one RP at another RP. 

#### 5.2.5. Pairwise Pseudonymous Identifiers

In some circumstances, it is desirable to prevent the subscriber's account at the IdP from being linked through one or more RPs through use of a common identifier. In these circumstances, pairwise pseudonymous subject identifiers SHALL be used within the assertions generated by the IdP for the RP, and the IdP SHALL generate a different identifier for each RP. (See [Pairwise Pseudonymous Identifier Generation](#ppi-gen) for more information.)

When unique pseudonymous identifiers are used with RPs along side of identity attribute bundles, it may still be possible for multiple colluding RPs to fully identify and correlate a subscriber across systems using these attributes. For example, given that two independent RPs will each see the same subscriber identified with a different pairwise pseudonymous identifier, the RPs could still determine that the subscriber is the same person by comparing their name, email address, physical address, or other identifying attributes carried alongside the pairwise pseudonymous identifier. Privacy policies may prohibit such correlation, but pairwise pseudonymous identifiers can increase effectiveness of these policies by increasing the administrative effort in managing the attribute correlation. 

Note that in a proxied federation model, ultimate IdP may be unable to generate a pairwise pseudonymous identifier for the ultimate RP, since the proxy could blind the IdP from knowing which RP is being accessed by the subscriber. In such situations, the pairwise pseudonymous identifier is usually between the IdP and the federation proxy itself. The proxy, acting as an IdP, can itself provide pairwise pseudonymous identifiers to downstream RPs. Depending on the protocol, the federation proxy may need to map the pairwise pseudonymous identifiers back to the associated identifiers from upstream IdPs in order to allow the identity protocol to function. In such cases, the proxy will be able to track and determine which pairwise pseudonymous identifiers represent the same subscriber at different RPs.

#### 5.2.6. <a name="ppi-gen"></a>Pairwise Pseudonymous Identifier Generation

Pairwise pseudonymous identifiers SHALL be opaque and unguessable, containing no identifying information about the subscriber. Additionally, the identifiers SHALL only be known by and used by one IdP-RP pair. 

An IdP MAY generate the same identifier for a subscriber at multiple RPs at the request of those RPs, but only if:

* Those RPs have a demonstrable relationship that justifies an operational need for the correlation, such as a shared security domain or shared legal ownership, and
* All RPs sharing an identifier consent to being correlated in such a manner.

The RPs SHALL conduct a privacy risk assessment to consider the privacy risks associated with requesting a common identifier. The IdP SHALL ensure that only intended RPs are correlated; otherwise, a rogue RP could learn of the pseudonymous identifier for a correlation by fraudulently posing as part of that correlation.