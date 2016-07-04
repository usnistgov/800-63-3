<a name="sec6"></a>

## 6. Authenticator Lifecycle Management

During the lifecycle of an authenticator bound to a subscriber's identity, a number of events may occur that affect the use of that authenticator. These events include binding, loss, theft, unauthorized duplication, expiration, and revocation. This section describes the actions that SHALL be taken in response to those events.

### <a name="binding"></a>6.1. Authenticator binding

Authenticators may be provided by a CSP as part of a process such as enrollment; in other cases, the subscriber may provide their own, such as software or hardware cryptographic modules. For this reason, we refer to the *binding* of an authenticator rather than the issuance, but this does not exclude the possibility that an authenticator is issued as well.

Throughout the online identity lifecycle, CSPs SHALL maintain a record of all authenticators that are or have been associated with the identity. It SHALL also maintain the information required for throttling authentication attempts when required, as described in section 5.2.2.

The record created by the CSP SHALL contain the date and time the authenticator was bound to the account and SHOULD include information about the binding, such as the IP address or other device identifier associated with the enrollment. It SHOULD also contain information about unsuccessful authentications attempted with the authenticator.

#### 6.1.1. Enrollment

The following requirements apply when an authenticator is bound to an identity as a result of a successful identity proofing transaction, as described in 800-63-A.

At IAL 2, the CSP SHALL bind at least one, and SHOULD bind at least two, authenticators to the subscriber's online identity. Binding of multiple authenticators is preferred in order to recover from loss or theft of their primary authenticator. While at IAL 1 all identifying information is self-asserted, creation of online material or an online reputation makes it undesirable to lose control of an account as result of the loss of an authenticator. The second authenticator makes it possible to securely recover from that situation.

At IAL 2 and above, identifying information is associated with the online identity and the subscriber has undergone an identity proofing process as described in SP 800-63A. As a result, authenticators at the same AAL as the desired IAL SHALL be bound to the account. For example, if the subscriber has successfully completed proofing at IAL 2, AAL 2 or 3 authenticators are appropriate to bind to the IAL 2 identity.  As above, the availability of additional authenticators provides backup methods of authentication if an authenticator is lost or stolen.

Enrollment and binding MAY be broken up into a number of separate physical encounters or electronic transactions. (Two electronic transactions are considered to be separate if they are not part of the same protected session.) In these cases, the following methods SHALL be used to ensure that the same party acts as Applicant throughout the processes:

1. For remote transactions:
	2. The applicant SHALL identify himself/herself in each new transaction by presenting a temporary secret which was established during a prior transaction or encounter, or sent to the Applicant’s phone number, email address, or postal address of record.
	3. Permanent secrets shall only be issued to the Applicant within a protected session.
2. For physical transactions:
	3. The applicant SHALL identify himself/herself in person by either using a secret as described above, or through the use of a biometric that was recorded during a prior encounter.
	4. Temporary secrets SHALL not be reused.
	5. If the CSP issues permanent secrets during a physical transaction, then they SHALL be loaded locally onto a physical device that is issued in person to the applicant or delivered in a manner that confirms the address of record.


#### 6.1.2. Post-Enrollment Binding

Following enrollment, binding an additional authenticator to an account requires the use of an existing authenticator of the same type (or types). For example, binding a new single-factor OTP device requires the subscriber to authenticate with another *something you have* authentication factor. If the account has only one authentication factor bound to it (which is possible only at IAL 1/AAL 1), an additional authenticator of the same factor may be bound to it.

Binding an additional authenticator SHALL require the use of two different authentication factors, except as provided below.

If the subscriber has only one of the two authentication factors, they SHALL repeat the identity proofing process, using the remaining authentication and SHOULD verify knowledge of some information collected during the proofing process to bind to the existing identity. In order to reestablish authentication factors at IAL 3, they SHALL verify the biometric collected during the proofing process.

***Consider what proofing information the CSP is allowed to maintain. Privacy impact here?***


#### 6.1.3. Binding Identity to a Subscriber Provided Authenticator
In some instances, a claimant may already possess authenticators at a suitable AAL without having been proofed at the equivalent IAL. For example, a user may have a two-factor authenticator from a social network provider, considered AAL2 and IAL1, and would like to use those credentials at a relying party that requires IAL2.

**I think we are making this too hard.  And not sure this is correct if we even want this as increasing IAL should still require address confirmation.  I'm thinking we require address confirmation and then let the binding of an existing authenticator to occur, so the OR below turns into an AND.**

The following requirements apply when a claimant choses to increase IAL in order to bind to a suitable authenticator they already have.

1. The CSP MAY accept an existing authenticator at or above the desired IAL
2. The CSP SHALL require the user to authenticate using their existing authenticator
3. The CSP SHALL execute all required identity proofing processes for the desired IAL
4. If the user successfully completes identity proofing, the CSP MAY issue an enrollment code (temporary secret) that confirms address of record as per [800-63-A, Section 5.3.1, Address Confirmation Requirements](sp800-63a.html#address_confirmation), **OR** MAY request the claimant to register their own authenticator by proving proof of possession (for example, activating a private key by physically touching the token)

#### 6.1.4. Renewal

The CSP SHOULD bind an updated authenticator an appropriate amount of time in advance of an existing authenticator's expiration. The process for this SHOULD conform closely to the initial authenticator issuance process (e.g., confirming address of record, etc.). Following successful use of the new authenticator, the CSP MAY revoke the authenticator that it is replacing.

### 6.2. Loss, Theft, and Unauthorized Duplication

Loss, theft, and unauthorized duplication of an authenticator are handled similarly, because in most cases one must assume that a lost authenticator has potentially been stolen or recovered by someone that is not the legitimate claimant of the authenticator. One notable exception is when a memorized secret is forgotten without other indication of having been compromised (duplicated by an attacker).

To facilitate secure reporting of loss or theft of an authenticator, the CSP SHOULD provide the subscriber a method to authenticate to the CSP using a backup authenticator; either a memorized secret or a physical authenticator MAY be used for this purpose (only one authentication factor is required for this purpose). Alternatively, the subscriber MAY establish an authenticated protected channel to the CSP and verify information collected during the proofing process. Alternatively, the CSP MAY verify an address of record (email, telephone, or postal) and suspend authenticator(s) reported to have been compromised. The suspension SHALL be reversible if the subscriber successfully authenticates to the CSP and requests reactivation of an authenticator suspended in this manner.

### 6.3. Expiration

CSP's SHOULD issue authenticators that expire. When an authenticator expires, it SHALL NOT be usable for authentication. When an authentication is attempted, the CSP SHOULD give an indication to the subscriber that the authentication failure is due to expiration rather than some other cause.

The CSP SHALL require subscribers to surrender any physical authenticator containing trustable attributes as soon as practical after expiration or after receipt of a renewed authenticator.

### 6.4. Revocation

CSPs SHALL revoke the binding of authenticators promptly when an online identity ceases to exist or when requested by the subscriber.

