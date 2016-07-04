<a name="sec5"></a>

## 5. Assertion Strength

An assertion contains a set of claims or statements about an authenticated subscriber. Assertions can be categorized along multiple orthogonal dimensions, including the characteristics of using the assertion or the protections on the assertion itself.

The core set of claims inside an assertion SHOULD include (but is not limited to):

 - Issuer: an identifier for the party that issued the assertion (the CSP)
 - Subject: an identifier for the party that the assertion is about (the subscriber), usually within the namespace control of the issuer (the CSP)
 - Audience: an identifier for the party intended to consume the assertion (the RP)
 - Issuance: a timestamp indicating when the assertion was issued by the CSP
 - Expiration: a timestamp indicating when the assertion expires and SHALL no longer be accepted as valid by the RP
 - Authentication Time: a timestamp indicating when the CSP last verified the presence of the subscriber at the CSP through a primary authentication event
 - Identifier: a random value uniquely identifying this assertion, used to prevent attackers from manufacturing malicious assertions which would pass other validity checks

These core claims, particularly the issuance and expiration claims, apply to the assertion about the authentication event itself, and not to any additional identity attributes associated with the subscriber, even when those claims are included within the assertion. A subscriber's attributes MAY expire or be otherwise invalidated independently of the expiration or invalidation of the assertion.

Assertions MAY include other additional identity attributes, but where possible the information contained in the assertion SHOULD be limited to the information required to process the authentication transaction. The RP MAY fetch additional identity attributes from the CSP in a separate transaction using an authorization credential issued along side the assertion. 

Although details vary based on the exact federation protocol in use, an assertion SHOULD be used only to represent a single log-in event at the RP. After the RP consumes the assertion, [session management](sp800-63b.html#sec7) at the RP comes into play and the assertion is no longer used directly. 

### 5.1. Assertion possession category

An assertion can be classified based on whether possession of the assertion itself is sufficient for representing  the subject of the assertion, or if additional proof is necessary along side the assertion.

#### 5.1.1. Holder-of-Key Assertions

A holder-of-key assertion contains a reference to a symmetric key or a public key (corresponding to a private key) possessed by and representing the subscriber. The RP may require the subscriber to prove possession of the key that is referenced in the assertion in parallel with presentation of the assertion itself. 

In proving possession of the subscriber’s secret, the subscriber also proves with a certain degree of assurance that they are the rightful subject of the assertion. It is more difficult for an attacker to use a stolen holder-of-key assertion issued to a subscriber, since the attacker would need to steal the referenced key material as well. 

Note that the reference to the key material in question is asserted by the issuer of the assertion as are any other claims therein, and reference to a given key SHALL be trusted at the same level as all other claims within the assertion itself.

#### 5.1.2. Bearer Assertions

A bearer assertion can be presented by any party as proof of the bearer's identity, without reference to external materials. If an attacker is able to capture or manufacture a valid assertion representing a subscriber, and that attacker is able to successfully present that assertion to the RP, then the attacker will be able to impersonate the subscriber at that RP. 

Note that mere possession of a bearer assertion is not always enough to impersonate a subscriber. For example, if an assertion is presented in the indirect federation model (Section 6.1), additional controls MAY be placed on the transaction (such as identification of the RP and assertion injection protections) that help to further protect the RP from fraudulent activity.

### 5.2. Assertion protection category

Regardless of the possession mechanism (discussed above) or the federation model used to obtain them (described in section 4), assertions need to include an appropriate set of protections to the assertion data itself to prevent attackers from manufacturing valid assertions or re-using captured assertions at disparate RPs.

#### 5.2.1. Shared Secret

Assertions SHALL contain sufficient entropy to prevent an attacker from manufacturing a valid assertion and using it with a target RP. A 128-bit random symmetric key or equivalent strength asymmetric key SHALL be used for this purpose. Assertions MAY accomplish this by use of an embedded nonce, timestamp, assertion identifier, or a combination of these or other techniques.

In the absence of additional cryptographic protections, this source of randomness SHALL function as a shared secret between the CSP and the RP to uniquely identify the assertion in question.

#### 5.2.2. Signed Assertion

Assertions MAY be cryptographically signed by the CSP, and the RP SHALL validate the signature of each such assertion based on the CSP's key. This signature SHALL cover all vital fields of the assertion, including its issuer, audience, subject, expiration, and any unique identifiers.

The signature MAY be asymmetric based on the published public key of the CSP. In such cases, the RP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the CSP), or the key MAY be provisioned out of band at the RP.

The signature MAY be symmetric based on a key shared out of band between the CSP and the RP. In such circumstances, the CSP SHALL use a different shared key for each RP.

All signatures SHALL use approved signing methods.

#### 5.2.3. Encrypted Assertion

Assertions MAY be encrypted in such a fashion as to allow only the intended audience to decrypt the claims therein. The CSP SHALL encrypt the payload of the assertion using the RP's public key. The CSP MAY fetch this public key in a secure fashion at runtime (such as through an HTTPS URL hosted by the RP), or the key MAY be provisioned out of band at the CSP (during registration of the RP).

All encrypted objects SHALL use approved encryption methods.

#### 5.2.4. Audience Restriction

All assertions SHOULD use audience restriction techniques to allow an RP to recognize whether or not it is the intended target of an issued assertion. All RPs SHALL check the audience of an assertion, if provided, to prevent the injection and replay of an assertion generated for one RP at another RP. 

#### 5.2.5. Pseudonymous Identifiers

To prevent the subscriber's account at the CSP from being linked through one or more RPs through use of a common identifier, pseudonymous subject identifiers SHALL be used within the assertions generated by the CSP for the RP. The CSP SHALL generate a different identifier for each RP.

