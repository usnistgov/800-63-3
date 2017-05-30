<a name="sec8"></a>

## 8. Threats and Security Considerations

*This section is informative.*

### 8.1. Authenticator Threats

An attacker who can gain control of an authenticator will often be able to masquerade as the authenticator's owner. Threats to authenticators can be categorized based on attacks on the types of authentication factors that comprise the authenticator:

- *Something you know* may be disclosed to an attacker. The attacker might guess a memorized secret. Where the authenticator is a shared secret, the attacker could gain access to the CSP or verifier and obtain the secret value or perform a dictionary attack on a hash of that value. An attacker may observe the entry of a PIN or passcode, find a written record or journal entry of a PIN or passcode, or may install malicious software (e.g., a keyboard logger) to capture the secret. Additionally, an attacker may determine the secret through offline attacks on a password database maintained by the verifier.

- *Something you have* may be lost, damaged, stolen from the owner, or cloned by an attacker. For example, an attacker who gains access to the owner's computer might copy a software authenticator. A hardware authenticator might be stolen, tampered with, or duplicated. Out-of-band secrets may be intercepted by an attacker and used to authenticate their own session.
    
- *Something you are* may be replicated. For example, an attacker may obtain a copy of the subscriber's fingerprint and construct a replica.

This document assumes that the subscriber is not colluding with the attacker who is attempting to falsely authenticate to the verifier. With this assumption in mind, the threats to the authenticator(s) used for e-authentication are listed in [Table 8-1](#63bSec8-Table1), along with some examples.

<a name="63bSec8-Table1"></a>

<div class="text-center" markdown="1">

**Table 8-1  Authenticator Threats**

</div>


| **Authenticator Threats/Attacks**  | **Description**  | **Examples** |
|------------------------------------|------------------|--------------|
| Theft | A physical authenticator is stolen by an Attacker. | A hardware cryptographic device is stolen. |
| | | An OTP device is stolen. |
| | | A look-up secret authenticator is stolen. |
| | | A cell phone is stolen. |
| Duplication | The subscriber's authenticator has been copied with or without their knowledge. | Passwords written on paper are disclosed.
| | | Passwords stored in an electronic file are copied. |
| | | Software PKI authenticator (private key) copied. |
| | | Look-up secret authenticator copied. |
| | | Counterfeit biometric authenticator manufactured. |
| Eavesdropping | The authenticator secret or authenticator output is revealed to the attacker as the subscriber is authenticating. | Memorized secrets are obtained by watching keyboard entry. |
| | | Memorized secrets or authenticator outputs are intercepted by keystroke logging software. |
| | | A PIN is captured from PIN pad device. |
| | | A hashed password is obtained and used by an attacker for another authentication (*pass-the-hash attack*). |
| | An out of band secret is intercepted by the attacker by compromising the communication channel. | An out of band secret is transmitted via unencrypted wifi and received by the attacker. |
| Offline cracking | The authenticator is exposed using analytical methods outside the authentication mechanism. | A software PKI authenticator is subjected to dictionary attack to identify the correct password to use to decrypt the private key. |
| Side channel attack | The authenticator secret is exposed using physical characteristics of the authenticator. | A key is extracted by differential power analysis on a hardware cryptographic authenticator. |
| | | A cryptographic authenticator secret is extracted by analysis of the response time of the authenticator over a number of attempts. |
| Phishing or pharming | The authenticator output is captured by fooling the subscriber into thinking the attacker is a verifier or RP. | A password is revealed by subscriber to a website impersonating the verifier.
| | | A memorized secret is revealed by a bank subscriber in response to an email inquiry from a phisher pretending to represent the bank. |
| | | A memorized secret is revealed by the subscriber at a bogus verifier website reached through DNS spoofing.
| Social engineering | The attacker establishes a level of trust with a subscriber in order to convince the subscriber to reveal his or her authenticator secret or authenticator output. | A memorized secret is revealed by the subscriber to an officemate asking for the password on behalf of the subscriber's boss. |
| | | A memorized secret is revealed by a subscriber in a telephone inquiry from an attacker masquerading as a system administrator. |
| | | An out of band secret sent via SMS is received by an attacker who has convinced the mobile operator to redirect the victim's mobile phone to the attacker. |
| Online guessing | The attacker connects to the verifier online and attempts to guess a valid authenticator output in the context of that verifier. | Online dictionary attacks are used to guess memorized secrets. |
| | | Online guessing is used to guess authenticator outputs for an OTP device registered to a legitimate claimant. |
| Endpoint compromise | Malicious code on the endpoint proxies remote access to a connected authenticator without user consent. | A cryptographic authenticator connected to the endpoint is used to authenticate remote attackers. |
| | Malicious code on the endpoint causes authentication to other than the intended verifier. | Authentication is performed on behalf of an attacker rather than the subscriber.
| | | A malicious app on the endpoint reads an out of band secret sent via SMS; the attacker uses the secret to authenticate.
| | Malicious code on the endpoint compromises a multi-factor software cryptographic authenticator. | Malicious code proxies authentication or exports authenticator keys from the endpoint.
| Unauthorized binding | Attacker is able to cause an authenticator under their control to be bound to subscriber account. | Attacker intercepts authenticator or provisioning key en route to subscriber.

### 8.2. Threat Mitigation Strategies
Related mechanisms that assist in mitigating the threats identified above are summarized in [Table 8-2](#63bSec8-Table2).

<a name="63bSec8-Table2"></a>

<div class="text-center" markdown="1">

**Table 8-2. Mitigating Authenticator Threats**

</div>


| **Authenticator Threat/Attack** | **Threat Mitigation Mechanisms** |
|---------------------------------|----------------------------------|
| Theft | Use multi-factor authenticators that need to be activated through a memorized secret or biometric.|
| | Use a combination of authenticators that includes a memorized secret or biometric.
| Duplication |  Use authenticators from which it is difficult to extract and duplicate long-term authentication secrets. |
| Eavesdropping | Ensure the security of the endpoint, especially with respect to freedom from malware such as key loggers, prior to use.
| | Maintain situational awareness when entering memorized secrets and OTPs to ensure that they cannot be observed by others.
| | Avoid use of non-trusted wireless networks as unencrypted secondary out-of-band authentication channels.
| | Authenticate over authenticated protected channels (observe lock icon in browser window, for example).
| | Use authentication protocols that are resistant to replay attacks such as *pass-the-hash*.
| | Use authentication endpoints that employ trusted input and trusted display capabilities.
| Offline cracking | Use an authenticator with a high entropy authenticator secret.
| | Store memorized secrets in a salted, hashed form, including a keyed hash.
| Side channel attack | Use authenticator algorithms that are designed to maintain constant power consumption and timing regardless of secret values.
| Phishing or pharming | Use authenticators that provide verifier impersonation resistance.
| | Be alert for unexpected hostnames in URLs.
| | Do not click on links in email messages; instead, enter the URL manually or through a trusted bookmark.
| Social engineering | Do not reveal authentication secrets to others, regardless of their story.
| | Avoid use of authenticators that present a risk of social engineering of third parties such as customer service agents.
| Online guessing | Use authenticators that generate high entropy output.
| | Use an authenticator that locks up after a number of repeated failed activation attempts.
| Endpoint compromise | Use hardware authenticators that require physical action by the subscriber.
| | Provide secure display of identity of verifier and RP.
| | Maintain software-based keys in restricted-access storage.
| Unauthorized binding | Use MitM-resistant protocols for provisioning of authenticators and associated keys.

There are several other strategies that may be applied to mitigate the threats described in [Table 8-1](#63bSec8-Table1):

- *Multiple factors* make successful attacks more difficult to accomplish. If an attacker needs to both steal a cryptographic authenticator and guess a memorized secret, then the work to discover both factors may be too high.

- *Physical security mechanisms* may be employed to protect a stolen authenticator from duplication. Physical security mechanisms can provide tamper evidence, detection, and response.

- *Requiring the use of long memorized secrets* that don't appear in common dictionaries may force attackers to try every possible value.

- *System and network security controls* may be employed to prevent an attacker from gaining access to a system or installing malicious software.

- *Periodic training* may be performed to ensure subscribers understand when and how to report compromise (or suspicion of compromise) or otherwise recognize patterns of behavior that may signify an attacker attempting to compromise the authentication process.

- *Out of band techniques* may be employed to verify proof of possession of registered devices (e.g., cell phones).

### 8.3. Authenticator Recovery

The weak point in many authentication mechanisms is the process followed when a subscriber loses control of one or more authenticators and needs to replace them. In many cases, the options remaining available to authenticate the subscriber are limited, and economic concerns (e.g., cost of maintaining call centers) motivate the use of inexpensive, and often less secure, backup authentication methods. To the extent that authenticator recovery is human-assisted, there is also the risk of social engineering attacks.

In order to maintain the integrity of the authentication factors, it is essential that it not be possible to leverage an authentication involving one factor to obtain an authenticator of a different factor. For example, a memorized secret must not be usable to obtain a new list of look-up secrets.

### 8.4. Session Attacks

The above discussion focuses on threats to the authentication event itself, but hijacking attacks on the session following an authentication event can have similar security impacts. The session management guidelines in [Section 7](#sec7) are essential to maintain session integrity against attacks, such as XSS. In addition, it is important to sanitize all information to be displayed [[OWASP-XSS-prevention]](#OWASP-XSS-prevention) to ensure that it does not contain executable content. These guidelines also recommend that session secrets be made inaccessible to mobile code in order to provide extra protection against exfiltration of session secrets should it be possible to inject malicious mobile code.

Another post-authentication threat, CSRF, takes advantage of users' tendency to have multiple sessions active at the same time. It is important to embed and verify a session identifier into web requests to prevent the ability for a valid URL or request to be unintentionally or maliciously activated.
