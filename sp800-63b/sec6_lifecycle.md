<a name="sec6"></a>

## 6. Authenticator Lifecycle Management

*This section is normative.*

During the lifecycle of an authenticator bound to a subscriber's identity, a number of events can occur that affect the use of that authenticator. These events include binding, loss, theft, unauthorized duplication, expiration, and revocation. This section describes the actions that SHALL be taken in response to those events.

### <a name="binding"></a>6.1. Authenticator Binding

*Authenticator binding* refers to the establishment of an association between a specific authenticator and a subscriber's account, enabling the authenticator to be used, possibly in conjunction with others, to authenticate for that account.

Authenticators SHALL be bound to subscriber accounts by either:

- issuance by the CSP as part of enrollment, binding, or other processes, or
- an authenticator acceptable to the CSP being provided by the subscriber.

This guideline refers to the *binding* rather than the issuance of an authenticator in order to accommodate both these options.

Throughout the online identity lifecycle, CSPs SHALL maintain a record of all authenticators that are or have been associated with each identity. The CSP or verifier SHALL also maintain the information required for throttling authentication attempts when required, as described in section 5.2.2. The CSP SHALL also verify the type of user-provided authenticator (e.g., single-factor cryptographic device vs. multi-factor cryptographic device) so that verifiers can determine compliance with requirements at at each AAL.

The record created by the CSP SHALL contain the date and time the authenticator was bound to the account and SHOULD include information about the binding, such as the IP address and any device identifier associated with the enrollment. If available, the record SHOULD also contain information about unsuccessful authentications attempted with the authenticator.

#### 6.1.1. Enrollment

The following requirements apply when an authenticator is bound to an identity as a result of a successful identity proofing transaction, as described in [[SP 800-63A]](sp800-63a.html).

The CSP SHALL bind at least one, and SHOULD bind at least two, physical ("something you have") authenticators to the subscriber's online identity in addition to a memorized secret and/or one or more biometrics. Binding of multiple authenticators is preferred in order to recover from the loss or theft of the subscriber's primary authenticator.

While at IAL1 all identifying information is self-asserted, creation of online material or an online reputation makes it undesirable to lose control of an account due to the loss of an authenticator. The second authenticator makes it possible to securely recover from the loss of an authenticator. For this reason, a CSP SHOULD bind at least two physical authenticators to the subscriber's credential at IAL1 as well.

At IAL2 and above, identifying information is associated with the online identity and the subscriber has undergone an identity proofing process as described in SP 800-63A. As a result, authenticators at the same AAL as the desired IAL SHALL be bound to the account. For example, if the subscriber has successfully completed proofing at IAL2, AAL2 or AAL3 authenticators are appropriate to bind to the IAL2 identity. While a CSP MAY bind an AAL1 authenticator to an IAL2 identity, if the subscriber is authenticated at AAL1, the CSP SHALL NOT expose personal information, even if self-asserted, to the subscriber. As stated in the previous paragraph, the availability of additional authenticators provides backup methods of authentication if an authenticator is damaged, lost, or stolen.

Enrollment and binding MAY be broken up into a number of separate physical encounters or electronic transactions. Two electronic transactions are considered to be separate if they are not part of the same protected session. In these cases, the following methods SHALL be used to ensure that the same party acts as the applicant throughout the processes:

1. For remote transactions -

  a) The applicant SHALL identify themselves in each new transaction by presenting a temporary secret which was established during a prior transaction or encounter, or sent to the applicant's phone number, email address, or postal address of record.	

  b) Long-term authenticator secrets SHALL only be issued to the applicant within a protected session.

2. For physical transactions -

  a) The applicant SHALL identify themselves in person by either using a secret as described above, or through the use of a biometric that was recorded during a prior encounter.	

  b) Temporary secrets SHALL not be reused.

  c) If the CSP issues long-term authenticator secrets during a physical transaction, then they SHALL be loaded locally onto a physical device that is issued in person to the applicant or delivered in a manner that confirms the address of record.


#### <a name="post-enroll-bind"></a> 6.1.2. Post-Enrollment Binding

#### 6.1.2.1. Binding of Additional Authenticator at Existing AAL

CSPs and verifiers SHOULD encourage subscribers to maintain at least two valid authenticators of each factor that they will be using, with the exception of memorized secrets. For example, a subscriber that usually uses an OTP device as a physical authenticator MAY also be issued a number of look-up secret authenticators, or register a device for out-of-band authentication, in case the physical authenticator is lost, stolen, or damaged.

Accordingly, CSPs SHOULD permit the binding of additional authenticators to a subscriber's account. Before adding the new authenticator, the CSP SHALL first require the subscriber to authenticate at the AAL (or a higher AAL) at which the new authenticator will be used. When an authenticator is added, the CSP SHOULD send a notification to the subscriber. The CSP MAY limit the number of authenticators that may be bound in this manner.

#### 6.1.2.2. Adding an Additional Factor to a One-factor Account

If the subscriber's account has only one authentication factor bound to it (at IAL1/AAL1), and an additional authenticator of a different authentication factor is to be added, the subscriber MAY request that the account be upgraded to AAL2 (but still at IAL1). Once this has been done, the CSP SHALL no longer permit the subscriber to use single-factor authentication.

Prior to binding the new authenticator, the CSP SHALL first require the subscriber to authenticate at AAL1. The CSP SHOULD send a notification of the event to the subscriber.

#### 6.1.2.3. Replacement of Lost Authentication Factor

If a subscriber loses all authenticators of a factor necessary to complete multi-factor authentication and has been identity proofed at IAL2 or IAL3, that subscriber SHALL repeat the identity proofing process. An abbreviated proofing process, confirming the binding of the claimant to previously-supplied evidence MAY be used if the CSP has retained the evidence from the original proofing process pursuant to a privacy risk assessment as described in [[SP 800-63A, Section 4.2]](sp800-63a.html#genProofReqs). The CSP SHALL require the claimant to authenticate using an authenticator of the remaining factor, if any, to confirm binding to the existing identity. Reestablishment of authentication factors at IAL3 SHALL be done in person or through a supervised remote process as described in [SP 800-63A Section 5.3.3.2](sp800-63a.html#supervised) and SHALL verify the biometric collected during the proofing process.

The CSP SHOULD send a notification of the event to the subscriber; this MAY be the same notice as is required as part of the proofing process.

#### 6.1.3. Binding to a Subscriber-provided Authenticator

A subscriber MAY already possess authenticators suitable for authentication at a particular AAL. For example, he or she MAY have a two-factor authenticator from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at an RP that requires IAL2.

CSPs SHOULD, where practical, accommodate the use of subscriber-provided authenticators in order to relieve the burden to the subscriber of managing a large number of authenticators. Binding of these authenticators SHALL be done as described in [Section 6.1.2.1](#post-enroll-bind). In situations where the authenticator strength is not self-evident (e.g., between single-factor and multi-factor authenticators of a given type), the CSP SHOULD assume the use of the weaker authenticator unless it is able to establish that the stronger authenticator is in fact being used (e.g., by verification with the issuer or manufacturer of the authenticator).

#### 6.1.4. Renewal

The CSP SHOULD bind an updated authenticator an appropriate amount of time in advance of an existing authenticator's expiration. The process for this SHOULD conform closely to the initial authenticator issuance process (e.g., confirming address of record). Following successful use of the new authenticator, the CSP MAY revoke the authenticator that it is replacing.

### 6.2. Loss, Theft, Damage, and Unauthorized Duplication

Loss, theft, damage to, and unauthorized duplication of an authenticator are handled similarly, because in most cases one must assume that a lost authenticator has potentially been stolen or compromised by someone that is not the legitimate claimant of the authenticator. Damaged or malfunctioning authenticators SHALL be treated in a similar manner to protect against any possibility of extraction of the authenticator secret. One notable exception is when a memorized secret is forgotten without other indication of having been compromised, such as being duplicated by an attacker.

Suspense, revocation, or destruction of compromised authenticators SHOULD occur as promptly as practical following detection. Agencies MAY establish time limits for this process.

To facilitate secure reporting of the loss, theft, or damage to an authenticator, the CSP SHOULD provide the subscriber a method to authenticate to the CSP using a backup or alternate authenticator. This backup authenticator could be a memorized secret or a physical authenticator MAY be used for this purpose and either MAY be used for this purpose with only one authentication factor required. Alternatively, the subscriber MAY establish an authenticated protected channel to the CSP and verify information collected during the proofing process. As an option, the CSP MAY choose to verify an address of record (i.e., email, telephone, postal) and suspend authenticator(s) reported to have been compromised. The suspension SHALL be reversible if the subscriber successfully authenticates to the CSP and requests reactivation of an authenticator suspended in this manner.

### 6.3. Expiration

CSPs MAY issue authenticators that expire. If and when an authenticator expires, it SHALL NOT be usable for authentication. When an authentication is attempted using an expired authenticator, the CSP SHOULD give an indication to the subscriber that the authentication failure is due to expiration rather than some other cause.

The CSP SHALL require subscribers to surrender or prove destruction of any physical authenticator containing attribute certificates signed by the CSP as soon as practical after expiration or receipt of a renewed authenticator.

### 6.4. Revocation and Termination

Revocation of an authenticator (sometimes referred to as termination, especially in the context of PIV credentials) refers to removal of the binding between an authenticator and a credential the CSP maintains. 
CSPs SHALL revoke the binding of authenticators promptly when an online identity ceases to exist (e.g., subscriber's death, discovery of a fraudulent subscriber), when requested by the subscriber, or when the CSP determines that the subscriber no longer meets its eligibility requirements.

The CSP SHALL require subscribers to surrender or certify destruction of any physical authenticator containing certified attributes signed by the CSP as soon as practical after revocation or termination takes place.

Further requirements on the termination of PIV credentials are found in [[FIPS 201]](#FIPS201).
