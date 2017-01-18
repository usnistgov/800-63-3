<a name="sec6"></a>

## 6. Authenticator Lifecycle Management

During the lifecycle of an authenticator bound to a subscriber's identity, a number of events can occur that affect the use of that authenticator. These events include binding, loss, theft, unauthorized duplication, expiration, and revocation. This section describes the actions that SHALL be taken in response to those events.

### <a name="binding"></a>6.1. Authenticator binding

Authenticators MAY be issued (provided) by a CSP as part of a process such as enrollment; in other cases, the subscriber MAY provide their own, such as software or hardware cryptographic modules. For this reason, this guideline refers to the *binding* of an authenticator rather than the issuance, but this does not exclude the possibility that an authenticator is issued as well.

Throughout the online identity lifecycle, CSPs SHALL maintain a record of all authenticators that are or have been associated with the identity. The CSP or verifier SHALL also maintain the information required for throttling authentication attempts when required, as described in section 5.2.2.

The record created by the CSP SHALL contain the date and time the authenticator was bound to the account and SHOULD include information about the binding, such as the IP address or other device identifier associated with the enrollment. If available, the record SHOULD also contain information about unsuccessful authentications attempted with the authenticator.

#### 6.1.1. Enrollment

The following requirements apply when an authenticator is bound to an identity as a result of a successful identity proofing transaction, as described in [SP 800-63A](sp800-63a.html).

At IAL 2, the CSP SHALL bind at least one, and SHOULD bind at least two, authenticators to the subscriber's online identity. Binding of multiple authenticators is preferred in order to recover from loss or theft of their primary authenticator. While at IAL 1 all identifying information is self-asserted, creation of online material or an online reputation makes it undesirable to lose control of an account as result of the loss of an authenticator. The second authenticator makes it possible to securely recover from that situation.

At IAL 2 and above, identifying information is associated with the online identity and the subscriber has undergone an identity proofing process as described in SP 800-63A. As a result, authenticators at the same AAL as the desired IAL SHALL be bound to the account. For example, if the subscriber has successfully completed proofing at IAL 2, AAL 2 or 3 authenticators are appropriate to bind to the IAL 2 identity.  As above, the availability of additional authenticators provides backup methods of authentication if an authenticator is damaged, lost, or stolen.

Enrollment and binding MAY be broken up into a number of separate physical encounters or electronic transactions. (Two electronic transactions are considered to be separate if they are not part of the same protected session.) In these cases, the following methods SHALL be used to ensure that the same party acts as Applicant throughout the processes:

1. For remote transactions:
	2. The applicant SHALL identify himself/herself in each new transaction by presenting a temporary secret which was established during a prior transaction or encounter, or sent to the Applicant’s phone number, email address, or postal address of record.
	3. Long-term authenticator secrets SHALL only be issued to the Applicant within a protected session.
2. For physical transactions:
	3. The applicant SHALL identify himself/herself in person by either using a secret as described above, or through the use of a biometric that was recorded during a prior encounter.
	4. Temporary secrets SHALL not be reused.
	5. If the CSP issues long-term authenticator secrets during a physical transaction, then they SHALL be loaded locally onto a physical device that is issued in person to the applicant or delivered in a manner that confirms the address of record.


#### <a name="post-enroll-bind">/<a> 6.1.2. Post-Enrollment Binding

##### 6.1.2.1. Binding of additional authenticator at existing AAL

Subscribers SHOULD be encouraged to maintain at least two valid authenticators of each factor they will be using. For example, a subscriber that usually uses a one-time OTP device as a physical authenticator MAY also be issued a number of look-up secret authenticators, or register a device for out-of-band authentication, in case the physical authenticator is lost, stolen, or damaged.

Accordingly, CSPs SHOULD permit the binding of additional authenticators to a subscriber's account. Before adding the new authenticator, the CSP SHALL first require the subscriber to authenticate at the AAL (or a higher AAL) at which the new authenticator will be used. When an authenticator is added, the CSP SHOULD send a notification to the subscriber. The CSP MAY limit the number of authenticators that may be bound in this manner.

##### 6.1.2.2. Adding an additional factor to a one-factor account

If the subscriber's account has only one authentication factor bound to it (at IAL 1/AAL 1), and an additional authenticator of a different authentication factor is to be added, the subscriber MAY request that the account be upgraded to AAL 2 (but still at IAL 1). Once this has been done, the CSP SHALL no longer permit the subscriber to use single-factor authentication.

Prior to binding the new authenticator, the CSP SHALL first require the subscriber to authenticate at AAL 1. The CSP SHOULD send a notification of the event to the subscriber.

##### 6.1.2.3. Replacement of lost authentication factor

As a last resort, if a subscriber loses all authenticators of a factor necessary to complete multi-factor authentication and has been identity proofed at IAL 2 or 3, that subscriber SHALL repeat the identity proofing process. An abbreviated proofing process, confirming the binding of the claimant to previously-supplied evidence MAY be used if the CSP has retained the evidence from the original proofing process pursuant to a privacy risk assessment as described in [SP 800-63A](sp800-63a.html) section 4.2. The CSP SHALL require the claimant to authenticate using an authenticator of the remaining factor (if any) to confirm binding to the existing identity. Reestablishment of authentication factors at IAL 3 SHALL be done in person and SHALL verify the biometric collected during the proofing process.

The CSP SHOULD send a notification of the event to the subscriber; this MAY be the same notice as is required as part of the proofing process.

#### 6.1.3. Binding to a subscriber-provided authenticator

A subscriber MAY already possess authenticators suitable for authentication at a particular AAL. For example, he or she MAY have a two-factor authenticator from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at a relying party that requires IAL2.

CSPs SHOULD, where practical, accommodate the use of subscriber-provided authenticators in order to relieve the burden to the subscriber of managing a large number of authenticators. Binding of these authenticators SHALL be done as described in section 6.1.2.1.

#### 6.1.4. Renewal

The CSP SHOULD bind an updated authenticator an appropriate amount of time in advance of an existing authenticator's expiration. The process for this SHOULD conform closely to the initial authenticator issuance process (e.g., confirming address of record, etc.). Following successful use of the new authenticator, the CSP MAY revoke the authenticator that it is replacing.

### 6.2. Loss, Theft, Damage, and Unauthorized Duplication

Loss, theft, damage to and unauthorized duplication of an authenticator are handled similarly, because in most cases one must assume that a lost authenticator has potentially been stolen or recovered by someone that is not the legitimate claimant of the authenticator. Damaged or malfunctioning authenticators SHALL be treated in a similar manner to protect against any possibility of extraction of the authenticator secret. One notable exception is when a memorized secret is forgotten without other indication of having been compromised (duplicated by an attacker). 

To facilitate secure reporting of loss or theft of or damage to an authenticator, the CSP SHOULD provide the subscriber a method to authenticate to the CSP using a backup authenticator; either a memorized secret or a physical authenticator MAY be used for this purpose (only one authentication factor is required for this purpose). Alternatively, the subscriber MAY establish an authenticated protected channel to the CSP and verify information collected during the proofing process. Alternatively, the CSP MAY verify an address of record (email, telephone, or postal) and suspend authenticator(s) reported to have been compromised. The suspension SHALL be reversible if the subscriber successfully authenticates to the CSP and requests reactivation of an authenticator suspended in this manner.

### 6.3. Expiration

CSPs MAY issue authenticators that expire. If and when an authenticator expires, it SHALL NOT be usable for authentication. When an authentication is attempted using an expired authenticator, the CSP SHOULD give an indication to the subscriber that the authentication failure is due to expiration rather than some other cause.

The CSP SHALL require subscribers to surrender or prove destruction of any physical authenticator containing attribute certificates signed by the CSP as soon as practical after expiration or receipt of a renewed authenticator.

### 6.4. Revocation and Termination

Revocation of an authenticator (sometimes referred to as termination, especially in the context of PIV credentials) refers to removal of the binding between an authenticator and a credential the CSP maintains. 
CSPs SHALL revoke the binding of authenticators promptly when an online identity ceases to exist (e.g., subscriber's death, discovery of a fraudulent subscriber), when requested by the subscriber, or when the CSP determines that the subscriber no longer meets its eligibility requirements.

The CSP SHALL require subscribers to surrender or prove destruction of any physical authenticator containing certified attributes signed by the CSP as soon as practical after revocation or termination takes place.

Further requirements on the termination of PIV credentials are found in [[FIPS 201]](#FIPS201).

### 6.5. Derived Authenticators

The expression of IAL and AAL as separate ordinals allows organizations to issue any type or number of authenticators they want regardless of how or if a subject is identity proofed.  This is one of the benefits of the separation - an organization can issue authenticators suitable for use by subscribers having a credential at IAL 2 or 3.  However, it may be beneficial for organizations to issue additional authenticators bound to a credential asscoiated with a primary authenticator.  This is covered in detail in [Section 6.1.2. Post-Enrollment Binding](#post-enroll-bind). 

The management of derived authenticators is similar to that described in [Section 6.1.2. Post-Enrollment Binding](#post-enroll-bind); however, derived authenticators are issued only to a subject that is authorized to have a primary authenticator.  Once the primary authenticator has been revoked, all derived authenticators, or their credentials, should be revoked.

> Note: In some cases, like the PIV smartcard, the authenticator and credential will be revoked.  The individual will typically surrender their authenticator (the PIV) even though the credential has been revoked, rendering the PIV unusable.  However, in many consumer use cases where an individual may provide their own authenticator(s), the CSP will revoke the credential the authenticator is bound to, such that authentication is no longer possible with that CSP; yet the individual can enroll the authenticator(s) with other CSPs. 

The definition of derived in this case is _not_ that an authenticator is tied to a primary authenticator, for example deriving a key from another key.  Rather, the derived authenticator is issued and bound to an identity that has already been identity proofed.  To prove that identity proofing has occurred, the individual demonstrates possession and authentication of an authenticator bound to the original proofed identity record (i.e the credential). 

The following requirements detail how a CSP should validate the authenticator and credential prior to issuance of a derived authenticator.  It also lists lifecycle management requirements to keep derived authenticators in sync with the primary authenticator and credential.

#### 6.5.1. General Requirements

1. Before issuance, the CSP SHALL verify the original authenticator status. The CSP SHALL NOT issue a derived authenticator if status indicates any type of termination, disablement, revocation, or expiration.
2. Before issuance, the CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.  
3. The derived authenticator SHALL be valid only as long as the subscriber is authorized to hold the original authenticator.
4. The CSP SHOULD record the details of the original authenticator used as the basis for derived authenticator issuance. 
5. The CSP SHOULD set the expiration of the derived authenticator to the expiration, if any, of the primary authenticator. There are instances where the derived authenticator need not be directly tied to the expiration of the primary authenticator as the derived authenticator can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
6. The derived authenticator type MAY be any AAL, regardless of the AAL of the primary authenticator or the IAL of the bound credential.  


#### 6.5.2. AAL 2 Requirements

- The CSP SHOULD check the status of the original authenticator weekly. 


#### <a name="dc-ial3"></a>6.5.3. AAL 3 Requirements

1.  The CSP SHOULD perform in-person issuance. This is important if the CSP needs to explicitly provision the authenticator to a trusted device and in-person is the only mechanism to ensure delivery and assurance.
2. The CSP SHOULD check the status of the original authenticator daily.
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the primary authenticator was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured.
4. The CSP SHALL compare a fresh biometric sample obtained in person from the applicant to the reference biometric retained when the primary AAL3 authenticator was issued.
5. The CSP SHALL determine that the original, primary authenticator the meets all AAL3 requirements.

