<a name="sec6"></a>

<div class="breaker"></div>

# <a name="derived-authN"></a> 6. Derived Identity

_This section is normative._

Derived identity (formerly known as derived credentials in previous versions of SP 800-63) is the process of an individual proving to a CSP that they are the rightful subject of an identity record (i.e., a credential) that is bound to one or more authenticators they possess. This process is made available by a CSP that wants individuals to have an opportunity to obtain new authenticators that are bound to the existing, identity proofed record, or credential. Since it is beneficial to the individual and the CSP to minimize the number of times the identity proofing process is repeated, deriving identity is accomplished by proving possession and successful authentication of the primary authenticator that is bound to the original, proofed digital identity.

The definition of derived in this section does *not* infer that an authenticator is cryptographically tied to a primary authenticator, for example deriving a key from another key.

There are two specific use cases for deriving identity:

1. A _claimant_ seeks to obtain a secondary authenticator, bound to a proofed identity record, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases. *This section covers this use case.*
2. An _applicant_ seeks to obtain an authenticator, bound to a proofed identity record, from a CSP that did not proof the individual or issue the original/primary authenticator and credential. For example, if an applicant wants to switch CSPs and/or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). *This use case is covered by allowable identity evidence in [Section 5.2](#validate).*

For the first use case above, the management of authenticators issued by deriving identity is similar to that described in [Section 6.1.2. Post-Enrollment Binding](https://pages.nist.gov/800-63-3/sp800-63b.html#post-enroll-bind); however,  authenticators considered in this section are only issued to a subject that is authorized to have a primary authenticator.  Once the primary authenticator has been revoked, it is possible that all authenticators bound to the identity will also be revoked.

> Note: In some cases, like the PIV smartcard, the authenticator _and_ credential will be revoked.  The individual will typically surrender their authenticator (i.e. the PIV), but since the credential has also been revoked, the PIV is unusable regardless of whether the individual surrenders it or not.  In many consumer use cases, rendering the authenticator unusable is not a desirable outcome. The individual may provide their own authenticator(s), so the CSP will revoke the credential the authenticator is bound to, such that authentication is no longer possible with that CSP; but the authenticator will can be used by the individual at other CSPs.

The following requirements detail how a CSP determines the existence of an enrolled, proofed identity record (i.e. the credential) prior to issuance of a secondary authenticator.  It also lists lifecycle management requirements to keep new authenticators in sync with the primary authenticator.

## 6.1. General Requirements

1. The IAL of the credential bound to the new authenticator SHALL be at or below the primary IAL. In most cases the IALs are expected to be the same in order to benefit from the reuse of the original identity proofing event(s).
1. Before issuance, the CSP SHALL verify the primary authenticator status. The CSP SHALL NOT issue an additional authenticator if status indicates any type of termination, disablement, revocation, or expiration.
2. Before issuance, the CSP SHALL verify that the primary authenticator is possessed and controlled by the claimant.
3. The new authenticator SHALL be valid only as long as the subscriber is authorized to hold the primary authenticator.
4. The CSP SHALL record the details of the primary authenticator used as the basis for derived authenticator issuance.
5. The CSP SHOULD set the expiration of the new authenticator to the expiration, if any, of the primary authenticator. There are instances where the new authenticator need not be directly tied to the expiration of the primary authenticator as the new authenticator can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
6. The new authenticator type MAY be any type allowable at any AAL, regardless of the AAL of the primary authenticator or the IAL of the bound credential.


## 6.2. AAL2 Requirements

- The CSP SHOULD check the status of the primary authenticator weekly in order to keep all authenticators in sync.


## <a name="dc-aal3"></a>6.3. AAL3 Requirements
2. The CSP SHOULD verify in-person that a claimant possesses, controls and can successfully authenticate using the primary authenticator(s).
1.  The CSP SHOULD perform in-person issuance. This is important if the CSP needs to explicitly provision the authenticator to a trusted device and in-person is the only mechanism to ensure delivery and assurance.
2. The CSP SHOULD check the status of the primary authenticator daily in order to keep all authenticators in sync.
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the primary authenticator was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the primary AAL3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured.
4. The CSP SHALL compare a fresh biometric sample from the applicant to the reference biometric retained when the primary AAL3 authenticator was issued.
5. The CSP SHALL determine that the primary authenticator meets all AAL3 requirements.

