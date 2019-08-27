<a name="security"></a>

## 8 Security

*This section is informative.*

Since the federated authentication process involves coordination between multiple components, including the CSP which now acts as an IdP, there are additional opportunities for attackers to compromise federated identity transactions. This section summarizes many of the attacks and mitigations applicable to federation.

### 8.1 Federation Threats

As in non-federated authentication, attackers' motivations is typically to gain access (or a greater level of access) to a resource or service provided by an RP. Attackers may also attempt to impersonate a subscriber. Rogue or compromised IdPs, RPs, user agents (e.g., browsers), and parties outside of a typical federation transaction are potential attackers. To accomplish their attack, they might intercept or modify assertions and assertion references. Further, two or more entities may attempt to subvert federation protocols by directly compromising the integrity or confidentiality of the assertion data. For the purpose of these types of threats, any authorized parties who attempt to exceed their privileges are considered attackers.

In some cases, the subscriber is issued some secret information so they can be recognized by the RP. Knowledge of this information distinguishes the subscriber from attackers who wish to impersonate them. In the case of holder-of-key assertions, this secret could have been established with the IdP prior to the initiation of the federation protocol.

<div class="text-center" markdown="1">

**Table 8-1 Federation Threats**

</div>

| **Federation Threats/Attacks**  | **Description**  | **Examples** |
|---------------------------------|------------------|--------------|
| Assertion Manufacture or Modification | The attacker generates a false assertion | Compromised IdP asserts identity of a claimant who has not properly authenticated |
| | The attacker modifies an existing assertion | Compromised proxy that changes AAL of an authentication assertion |
| Assertion Disclosure | Assertion visible to third party | Network monitoring reveals subscriber address of record to an outside party |
| Assertion Repudiation by the IdP | IdP later claims not to have signed transaction | User engages in fraudulent credit card transaction at RP, IdP claims not to have logged them in |
| Assertion Repudiation by the Subscriber | Subscriber claims not to have performed transaction | User agreement (e.g., contract) cannot be enforced |
| Assertion Redirect | Assertion can be used in unintended context | Compromised user agent passes assertion to attacker who uses it elsewhere |
| Assertion Reuse | Assertion can be used more than once with same RP | Intercepted assertion used by attacker to authenticate their own session |
| Assertion Substitution | Attacker uses an assertion intended for a different subscriber | Session hijacking attack between IdP and RP |

### 8.2 Federation Threat Mitigation Strategies

Mechanisms that assist in mitigating the above threats are identified in Table 8-2.

<div class="text-center" markdown="1">

**Table 8-2 Mitigating Federation Threats**

</div>

| **Federation Threat/Attack** | **Threat Mitigation Mechanisms** | **Normative Reference(s)** |
|------------------------------|----------------------------------|---|
| Assertion Manufacture or Modification | Cryptographically sign the assertion at IdP and verify at RP | [4.1](#key-mgmt), [6](#assertions) |
| | Send assertion over an authenticated protected channel authenticating the IdP | [7.1](#back-channel), [7.2](#front-channel) |
| | Include a non-guessable random identifier in the assertion | [6.2.1](#assertion-id) |
| Assertion Disclosure | Send assertion over an authenticated protected channel authenticating the RP | [7.1](#back-channel), [7.2](#front-channel) |
| | Encrypt assertion for a specific RP (may be accomplished by use of a mutually authenticated protected channel) | [6.2.3](#encrypted-assertion) |
| Assertion Repudiation by the IdP | Cryptographically sign the assertion at the IdP with a key that supports non-repudiation; verify signature at RP | [6.2.2](#signed-assertion) |
| Assertion Repudiation by the Subscriber | Issue holder-of-key assertions; proof of possession of presented key verifies subscriber's participation | [6.1.2](#holderofkey) |
| Assertion Redirect | Include identity of the RP ("audience") for which the assertion is issued in its signed content; RP verifies that they are intended recipient | [6](#assertions), [7.1](#back-channel), [7.2](#front-channel) |
| Assertion Reuse | Include an issuance timestamp with short validity period in the signed content of the assertion; RP verifies validity | [6](#assertions), [7.1](#back-channel), [7.2](#front-channel) |
| | RP keeps track of assertions consumed within a configurable time window to ensure that a given assertion is not used more than once. | [6.2.1](#assertion-id) |
| Assertion Substitution | Ensure that assertions contain a reference to the assertion request or some other nonce that was cryptographically bound to the request by the RP | [6](#assertions) |
| | Send assertions in the same authenticated protected channel as the request, such as in the back-channel model |[7.1](#back-channel)|

