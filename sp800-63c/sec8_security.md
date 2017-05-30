<div class="breaker"></div>
<a name="security"></a>

## 8. Security

*This section is informative.*

IdPs, RPs, subscribers, and parties outside of a typical assertion transaction may be malicious or become compromised. An attacker might have an interest in modifying or replacing an assertion to obtain a greater level of access to a resource or service provided by an
RP. They might be interested in obtaining or modifying
assertions and assertion references to impersonate a subscriber or
access unauthorized data or services. Furthermore, it is possible that
two or more entities may be colluding to attack another party. An
attacker may attempt to subvert assertion protocols by directly
compromising the integrity or confidentiality of the assertion data. For the purpose of these types of threats, authorized parties who attempt to exceed their privileges may be considered attackers. This section lists some common attacks against assertion transmission transactions.

-   *Assertion manufacture/modification* - An attacker generates a
    forged assertion or modifies the content of an existing assertion (such as the
    authentication or attribute statements),
    causing the RP to grant inappropriate access to the subscriber. For
    example, an attacker may modify the assertion to extend the validity
    period and keep using an assertion; or a subscriber may modify the assertion to have access to
    information that they should not be able to view.

-   *Assertion disclosure* - Assertions may contain authentication and
    attribute statements that include sensitive subscriber information.
    Disclosure of the assertion contents can make the subscriber
    vulnerable to other types of attacks.

-   *Assertion repudiation by the IdP* - An assertion may be
    repudiated by an IdP if the proper mechanisms are not in place.
    For example, if an IdP does not digitally sign an assertion, the
    IdP can claim that it was not generated through the services of
    the IdP.

-   *Assertion repudiation by the subscriber* - Since it is possible for
    a compromised or malicious IdP to issue assertions to the
    wrong party, a subscriber can repudiate any transaction with the RP
    that was authenticated using only a bearer assertion.

-   *Assertion redirect* - An attacker uses the assertion generated for
    one RP to obtain access to a second RP.

-   *Assertion reuse* - An attacker attempts to use an assertion that
    has already been used once with the intended RP.

In
some cases, the subscriber is
issued some secret information so that they can be recognized by the RP. The knowledge of this information distinguishes the
subscriber from attackers who wish to impersonate them. In the
case of holder-of-key assertions, this secret could already have been
established with the IdP prior to the initiation of the assertion
protocol. In other cases, the IdP will generate a temporary secret
and transmit it to the authenticated subscriber for this purpose. When this secret is used to authenticate to the RP, this temporary secret will be referred to as a secondary
authenticator. Secondary authenticators include assertions in the front-channel
model, session keys in Kerberos, assertion references in the back-channel
model, and cookies used for session management. The threats to the secondary
authenticator are as follows:

-   *Secondary authenticator manufacture* - An attacker may attempt to
    generate a valid secondary authenticator and use it to impersonate
    a subscriber.

-   *Secondary authenticator capture* - An attacker may use a session
    hijacking attack to capture the secondary authenticator when the
    IdP transmits it to the subscriber after the primary
    authentication step, or the attacker may use a man-in-the-middle
    attack to obtain the secondary authenticator as it is being used by
    the subscriber to authenticate to the RP. If, as in the back-channel
    model, the RP needs to send the secondary authenticator back to the
    IdP in order to check its validity or obtain the corresponding
    assertion data, an attacker may similarly subvert the communication
    protocol between the IdP and the RP to capture a
    secondary authenticator. In any of the above scenarios, the
    secondary authenticator can be used to impersonate the subscriber.

Finally, in order for the subscriber's authentication to the RP to be
useful, the binding between the secret used to authenticate to the RP
and the assertion data referring to the subscriber needs to be strong.

-   *Assertion substitution* - A subscriber may attempt to impersonate a
    more privileged subscriber by subverting the communication channel
    between the IdP and RP, for example by reordering the messages,
    to convince the RP that their secondary authenticator
    corresponds to assertion data sent on behalf of the more
    privileged subscriber. 
    

### 8.1. Threat Mitigation Strategies

Mitigation techniques are described below for each of the threats
described in the last subsection.

-   *Assertion manufacture/modification* - To mitigate this threat,
    the following mechanisms are used:

	1.  The assertion is digitally signed by the IdP. The RP 
    checks the digital signature to verify that it was issued by a
    legitimate IdP. The key used is stored in suitably secure storage available to the application 
	(e.g., keychain storage, trusted platform module, secure element) and is communicated to the RP in 
	a secure manner (e.g., through a trusted out-of-band mechanism or delivery over an authenticated protected channel).

	2.  The assertion is sent over an authenticated protected channel such as TLS. In
    order to protect the integrity of assertions from malicious attack,
    the IdP is authenticated.

	3. The assertion contains a non-guessable random identifier. 

-   *Assertion disclosure* - To mitigate this threat, one of the
    following mechanisms are used:

	1.  The assertion is sent over an authenticated protected channel to an
    authenticated RP. Audience restrictions are used to restrict the assertion to the intended RP.  The IdP also signs the assertion.
	The key used is stored in suitably secure storage available to the application 
	(e.g., keychain storage, trusted platform module, secure element) and is communicated to the RP in 
	a secure manner (e.g., through a trusted out-of-band mechanism or delivery over an authenticated protected channel).

	2.  Assertions are signed by the IdP and encrypted for
    a specific RP.  It should be
    noted that this provides all the same guarantees as a mutually
    authenticated protected channel, and may therefore be
    considered equivalent. The general requirement for protecting
    against both assertion disclosure and assertion
    manufacture or modification may therefore be described as a mutually authenticated protected channel or equivalent between the IdP
    and the RP. The keys used are stored in suitably secure storage available to the application 
	(e.g., keychain storage, trusted platform module, secure element), the IdP's key is communicated to the RP in a secure manner
    (e.g., through a trusted out-of-band mechanism or delivery over an authenticated protected channel)
 	and the RP's key is communicated to the IdP in 
	a secure manner (e.g., through a trusted out-of-band mechanism or delivery over an authenticated protected channel).


-   *Assertion repudiation by the IdP* - To mitigate this threat,
    the assertion is digitally signed by the IdP using a key
    that supports non-repudiation. The RP checks the digital
    signature to verify that it was issued by a legitimate IdP.

-   *Assertion repudiation by the subscriber* - To mitigate this threat,
    the IdP issues holder-of-key assertions, rather than bearer assertions.
    The subscriber can then prove possession of the asserted key to
    the RP. If the asserted key matches the subscriber's presented key,
    it will be proof to all parties
    involved that it was the subscriber who authenticated to the RP
    rather than a compromised IdP impersonating the subscriber.

-   *Assertion redirect* - To mitigate this threat, the assertion
    includes the identity of the RP for which it was generated. The RP
    verifies that incoming assertions include its identity as the
    recipient of the assertion. 

-   *Assertion reuse* - To mitigate this threat, the following
    mechanisms are used:

	1.  The assertion includes a timestamp and has a short lifetime
    of validity. The RP checks the timestamp and lifetime values to
    ensure that the assertion is currently valid. 
	2.  The RP keeps track of assertions that were consumed within
    a configurable time window to ensure that an assertion is not
    used more than once within that time window. 

-   *Secondary authenticator manufacture* - To mitigate this threat, one
    of the following mechanisms is used:

	1.  The secondary authenticator may contain sufficient entropy that an
    attacker without direct access to the IdP's random number
    generator cannot guess the value of a valid secondary authenticator.

	2.  The secondary authenticator may contain timely assertion data that
    is signed by the IdP or integrity protected using a key shared
    between the IdP and the RP.



-   *Secondary authenticator capture* - To mitigate this threat,
    adequate protections are in place throughout the lifetime of
    any secondary authenticators used in the assertion protocol.

	1.  In order to protect the secondary authenticator while it is in
    transit between the IdP and the subscriber, the secondary
    authenticator is sent via an authenticated protected channel established
    during the primary authentication of the subscriber. 

	2.  In order to protect the secondary authenticator from capture as it
    is submitted to the RP, the secondary authenticator is used in
    an authentication protocol which protects against eavesdropping and
    man-in-the-middle attacks.

	3.  In order to protect the secondary authenticator after it has been
    used, it is never transmitted over an unprotected channel or to
    an unauthenticated party while it is still valid.
    
-   *Assertion substitution* - To mitigate this threat, one of the
    following mechanisms is used:

	1.  Responses to assertion requests contain the value of the assertion reference used
    in the request or some other nonce that was cryptographically bound
    to the request by the RP.

	2.  Responses to assertion requests are bound to the corresponding
    requests by message order, as in HTTP, provided that assertions and
    requests are protected by a protocol such as TLS that can detect and
    disallow malicious reordering of packets.
