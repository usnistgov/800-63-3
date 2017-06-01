<div class="breaker"></div>
<a name="security"></a>

## 8. Security

*This section is informative.*

Since the federated authentication process involves coordination between multiple components, including the CSP which now acts as an IdP, there are additional opportunities for attackers to compromise federated identity transactions. This section summarizes many of the attacks and their mitigations that are applicable when federation is being used.

###8.1. Federation Threats

As in non-federated authentication, the motivation of attackers is typically to gain access (or a greater level of access) to a resource or service provided by an RP. Attackers may also attempt to impersonate a subscriber. Rogue or compromised IdPs, RPs, user agents (e.g., browsers), and parties outside of a typical federation transaction are potential attackers. To accomplish their attack, they might intercept or modify assertions and assertion references. Furthermore, two or more entities may attempt to subvert federation protocols by directly compromising the integrity or confidentiality of the assertion data. For the purpose of these types of threats, any authorized parties who attempt to exceed their privileges are considered attackers.

In some cases, the subscriber is issued some secret information so that they can be recognized by the RP. The knowledge of this information distinguishes the subscriber from attackers who wish to impersonate them. In the case of holder-of-key assertions, this secret could already have been established with the IdP prior to the initiation of the federation protocol. In other cases, the IdP will generate a temporary secret and transmit it to the authenticated subscriber for this purpose. When this secret is used to authenticate to the RP, this temporary secret is referred to as a *secondary authenticator*. Examples of secondary authenticators include assertions in the front-channel model, session keys in Kerberos, assertion references in the back-channel model, and cookies used for session management.

<div class="text-center" markdown="1">

**Table 8-1 Federation Threats**

</div>

| **Federation Threats/Attacks**  | **Description**  | **Examples** |
|---------------------------------|------------------|--------------|
| Assertion manufacture or modification | The attacker generates a false assertion | Compromised IdP asserts identity of a claimant who has not properly authenticated. |
| | The attacker modifies an existing assertion | Compromised proxy that changes AAL of an authentication assertion |
| Assertion disclosure | Assertion visible to third party | Network monitoring reveals subscriber address of record to an outside party |
| Assertion repudiation by the IdP | IdP later claims not to have signed transaction | User engages in fraudulent credit card transaction at RP, IdP claims not to have logged them in |
| Assertion repudiation by the subscriber | Subscriber claims not to have performed transaction | User agreement (e.g., contract) cannot be enforced |
| Assertion redirect | Assertion can be used in unintended context | Compromised user agent passes assertion to attacker who uses it elsewhere |
| Assertion reuse | Assertion can be used more than once with same RP | Intercepted assertion used by attacker to authenticate their own session |
| Secondary authenticator manufacture | Attacker generates a secondary authenticator to impersonate a subscriber | Attacker exploits a cryptographic weakness in generation of secondary authenticators |
| Secondary authenticator capture | Attacker intercepts the secondary authenticator | Attacker uses a session-hijacking attack to capture the secondary authenticator |
| Assertion substitution | Attacker uses an assertion intended for a different subscriber | Session hijacking attack between IdP and RP |

### 8.2. Federation Threat Mitigation Strategies

Mechanisms that assist in mitigating the threats identified above are identified in Table 8-2.

<div class="text-center" markdown="1">

**Table 8-2. Mitigating Authenticator Threats**

</div>

| **Federation Threat/Attack** | **Threat Mitigation Mechanisms** |
|------------------------------|----------------------------------|
| Assertion Manufacture or Modification | Cryptographically sign the assertion at IdP and verify at RP |
| | Send assertion over an authenticated protected channel authenticating the IdP |
| | Include a non-guessable random identifier in the assertion |
| Assertion disclosure | Send assertion over an authenticated protected channel authenticating the RP |
| | Encrypt assertion for a specific RP (may be accomplished by use of a mutually authenticated protected channel) |
| Assertion repudiation by the IdP | Cryptographically sign the assertion at the IdP with a key that supports non-repudiation; verify signature at RP |
| Assertion repudiation by the subscriber | Issue holder-of-key assertions; proof of possession of presented key verifies subscriber's participation |
| Assertion redirect | Include identity of the RP for which the assertion is issued in its signed content; RP verifies that they are intended recipient |
| Assertion reuse | Include a timestamp with short validity period in the signed content of the assertion; RP verifies validity |
| | RP keeps track of assertions consumed within a configurable time window to ensure that a given assertion is not used more than once. |
| Secondary authenticator manufacture | Ensure that secondary authenticator has sufficient entropy to resist manufacture |
| | Include timely assertion data signed by the IdP |
| Secondary authenticator capture | Send secondary authenticator using an authenticated protected channel established between the IdP and subscriber at primary authentication time |
| | Use the secondary authenticator in an authentication protocol that protects against eavesdropping and MitM attacks |
| | Never send a secondary authenticator over an unprotected channel or to an unauthenticated party while still valid |
| Assertion substitution | Ensure that assertion responses contain a reference to the assertion request or some other nonce that was cryptographically bound to the request by the RP |
| | Send assertion responses in the same authentication protected channel as the request, such as in the back-channel model |

