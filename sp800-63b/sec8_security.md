<a name="sec8"></a>

## 8. Threats and Security Considerations

*This section is non-normative.*

### 8.1. Authenticator Threats

An attacker who can gain control of an authenticator will often be able to masquerade as the authenticator's owner. Threats to authenticators can be categorized based on attacks on the types of authentication factors that comprise the authenticator:

- *Something you have* may be lost, damaged, stolen from the owner or cloned by an attacker. For example, an attacker who gains access to the owner’s computer might copy a software authenticator. A hardware authenticator might be stolen, tampered with, or duplicated.

- *Something you know* may be disclosed to an attacker. The attacker might guess a memorized secret. Where the authenticator is a shared secret, the attacker could gain access to the CSP or verifier and obtain the secret value or perform a dictionary attack on a hash of that value. An attacker may observe the entry of a PIN or passcode, find a written record or journal entry of a PIN or passcode, or may install malicious software (e.g., a keyboard logger) to capture the secret. Additionally, an attacker may determine the secret through offline attacks on a hashed password database maintained by the verifier.
    
- *Something you are* may be replicated. An attacker may obtain a copy of the subscriber’s fingerprint and construct a replica - assuming that the biometric system(s) employed do not block such attacks by employing robust liveness detection techniques.

This document assumes that the subscriber is not colluding with the attacker who is attempting to falsely authenticate to the verifier. With this assumption in mind, the threats to the authenticator(s) used for e-authentication are listed in Table 4, along with some examples.

**Table 4 – Authenticator Threats**

| **Authenticator Threats/Attacks**  | **Description**  | **Examples** |
|------------------------------------|------------------|--------------|
| Theft | A physical authenticator is stolen by an Attacker. | A hardware cryptographic device is stolen. |
| | | A One-Time Password device is stolen. |
| | | A look-up secret authenticator is stolen. |
| | | A cell phone is stolen. |
| Duplication | The Subscriber’s authenticator has been copied with or without their knowledge. | Passwords written on paper are disclosed.
| | | Passwords stored in an electronic file are copied. |
| | | Software PKI authenticator (private key) copied. |
| | | Look-up secret authenticator copied. |
| Eavesdropping | The authenticator secret or authenticator output is revealed to the attacker as the subscriber is authenticating. | Memorized secrets are obtained by watching keyboard entry. |
| | | Memorized secrets or authenticator outputs are intercepted by keystroke logging software. |
| | | A PIN is captured from PIN pad device. |
| Offline cracking | The authenticator is exposed using analytical methods outside the authentication mechanism. | A software PKI authenticator is subjected to dictionary attack to identify the correct password to use to decrypt the private key. |
| Side channel attack | The authenticator secret is exposed using physical characteristics of the authenticator | A key is extracted by differential power analysis on a hardware cryptographic authenticator. |
| | | A cryptographic authenticator secret is extracted by analysis of the response time of the authenticator over a number of attempts. |
| Phishing or pharming | The authenticator output is captured by fooling the subscriber into thinking the attacker is a Verifier or RP. | A password is revealed by subscriber to a website impersonating the verifier.
| | | A memorized secret is revealed by a bank subscriber in response to an email inquiry from a phisher pretending to represent the bank. |
| | | A memorized secret is revealed by the subscriber at a bogus verifier website reached through DNS spoofing.
| Social engineering | The attacker establishes a level of trust with a Subscriber in order to convince the Subscriber to reveal his or her authenticator secret or authenticator output. | A memorized secret is revealed by the Subscriber to an officemate asking for the password on behalf of the subscriber’s boss. |
| | | A memorized secret is revealed by a subscriber in a telephone inquiry from an attacker masquerading as a system administrator. |
| Online guessing | The attacker connects to the verifier online and attempts to guess a valid authenticator output in the context of that verifier. | Online dictionary attacks are used to guess memorized secrets. |
| | | Online guessing is used to guess authenticator outputs for a one-time password device registered to a legitimate claimant. |


### 8.2. Threat Mitigation Strategies
Related mechanisms that assist in mitigating the threats identified above are summarized in Table 5.

**Table 5 - Mitigating Authenticator Threats**

| **Authenticator Threat/Attack** | **Threat Mitigation Mechanisms** |
|---------------------------------|----------------------------------|
| Theft | Use multi-factor authenticators which need to be activated through a PIN or biometric.|
| Duplication |  Use authenticators that are difficult to duplicate, such as hardware cryptographic authenticators. |
| Discovery | Use methods in which the responses to prompts cannot be easily discovered.
| Eavesdropping | Use authenticators with dynamic outputs where knowledge of one authenticator does not assist in deriving a subsequent authenticator.
| | Use authenticators that generate authenticators based on an authenticator input value or challenge.
| | Establish authenticators through a separate channel.
| Offline cracking | Use an authenticator with a high entropy authenticator secret.
| | Use an authenticator that locks up after a number of repeated failed activation attempts.
| | Store memorized secrets in a salted, hashed form to raise the cost of dictionary attacks; use a keyed hash.
| Side channel attack | Use authenticator algorithms that are designed to maintain constant power consumption and timing regardless of secret values
| Phishing or pharming | Use authenticators with dynamic outputs where knowledge of one output does not assist in deriving a subsequent output.
| Social engineering | Use authenticators with dynamic outputs where knowledge of one output does not assist in deriving a subsequent output.
| Online guessing | Use authenticators that generate high entropy output.


There are several other strategies that may be applied to mitigate the threats described in Table 5:

- *Multiple factors* make successful attacks more difficult to accomplish. If an attacker needs to both steal a cryptographic authenticator and guess a memorized secret, then the work to discover both factors may be too high.

- *Physical security mechanisms* may be employed to protect a stolen authenticator from duplication. Physical security mechanisms can provide tamper evidence, detection, and response.

- *Requiring the use of long memorized secrets* that don’t appear in common dictionaries may force attackers to try every possible value.

- *System and network security controls* may be employed to prevent an attacker from gaining access to a system or installing malicious software.

- *Periodic training* may be performed to ensure subscribers understand when and how to report compromise (or suspicion of compromise) or otherwise recognize patterns of behavior that may signify an attacker attempting to compromise the authentication process.

- *Out of band techniques* may be employed to verify proof of possession of registered devices (e.g., cell phones).

### 8.3. Authenticator Recovery

The weak point in many authentication mechanisms is the process followed when a subscriber loses control of one or more authenticators and needs to replace them. In many cases, the options remaining available to authenticate the subscriber are limited, and economic concerns (cost of maintaining call centers, etc.) motivate the use of inexpensive, and frequently less secure, backup authentication methods. To the extent that authenticator recovery is human-assisted, there is also the risk of social engineering attacks.

In order to maintain the integrity of the authentication factors, it is essential that it not be possible to leverage an authentication involving one factor to obtain an authenticator of a different factor. For example, a memorized secret must not be usable to obtain a new list of look-up secrets.

Subscribers should be encouraged to maintain at least two valid authenticators of each factor they will be using. For example, a subscriber that usually uses a one-time OTP device as a physical authenticator should also be issued a number of look-up secret authenticators, or should register a device for out-of-band authentication, in case the physical authenticator is lost, stolen, or damaged.
