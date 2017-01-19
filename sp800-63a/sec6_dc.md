<a name="sec6"></a>

<div class="breaker"></div>

# <a name="derived-authN"></a> 6. Derived Authenticators

_This section is normative._

The expression of IAL and AAL as separate ordinals allows organizations to issue any type or number of authenticators they want regardless of how or if a subject is identity proofed.  This is one of the benefits of the separation - an organization can issue authenticators suitable for use by subscribers regardless of the required IAL to access the service.  However, there are instances when a CSP will want to bind a new authenticator to an existing, identity proofed record, or credential. Since it is beneficial to the subject and CSP to minimize the number of times the identity proofing process needs to be repeated, this can be accomplished by proving possession and successful authentication of an existing authenticator that is already bound to a proofed digital identity. Authenticators issued and bound to existing identity proofed records are considered to be *derived authenticators*.

The definition of derived in this section does *not* infer that an authenticator is cryptographically tied to a primary authenticator, for example deriving a key from another key.  Rather, the derived authenticator is issued and bound to an identity that has already been identity proofed.  To prove that identity proofing has occurred, the individual demonstrates possession and authentication of an authenticator bound to the original proofed identity record (i.e the credential). 

There are two specific use cases to consider leveraging past proofing of an individual:

1. A _claimant_ obtains a secondary, or derived authenticator, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases, or a temporary authenticator. *This section covers this use case.*
2. An _applicant_ seeks to obtain an authenticator, bound to a proofed identity, from a CSP that did not proof the individual or issue the original authenticator. For example, if an applicant wants to switch CSPs and/or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). *This use case is covered by allowable identity evidence in [Section 5.2](#validate).*

For the first use case above, the management of derived authenticators is similar to that described in [Section 6.1.2. Post-Enrollment Binding](https://pages.nist.gov/800-63-3/sp800-63b.html#post-enroll-bind); however, derived authenticators considered in this section are only issued to a subject that is authorized to have a primary authenticator.  Once the primary authenticator has been revoked, it is reasonable that all derived will also be revoked.

> Note: In some cases, like the PIV smartcard, the authenticator _and_ credential will be revoked.  The individual will typically surrender their authenticator (i.e. the PIV), but since the credential has been revoked the PIV is unusable regardless of whether the individual surrenders it or not.  In many consumer use cases, rendering the authenticator unusable is not a desirable outcome. The individual may provide their own authenticator(s), so the CSP will revoke the credential the authenticator is bound to, such that authentication is no longer possible with that CSP; yet the authenticator is still valid to be used by the individual at other CSPs. 

The following requirements detail how a CSP should validate the existence of a past proofing event (i.e. the credential) prior to issuance of a derived authenticator.  It also lists lifecycle management requirements to keep derived authenticators in sync with the primary authenticator.


## 6.2. General Requirements


1. The IAL of the credential bound to the derived authenticator SHALL be at or below the primary IAL. In most cases the IALs are expected to be the same in order to benefit from the reuse of the original identity proofing event(s). 
1. Before issuance, the CSP SHALL verify the original authenticator status. The CSP SHALL NOT issue a derived authenticator if status indicates any type of termination, disablement, revocation, or expiration.
2. Before issuance, the CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.  
3. The derived authenticator SHALL be valid only as long as the subscriber is authorized to hold the original authenticator.
4. The CSP SHALL record the details of the original authenticator used as the basis for derived authenticator issuance. 
5. The CSP SHOULD set the expiration of the derived authenticator to the expiration, if any, of the primary authenticator. There are instances where the derived authenticator need not be directly tied to the expiration of the primary authenticator as the derived authenticator can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
6. The derived authenticator type MAY be any AAL, regardless of the AAL of the primary authenticator or the IAL of the bound credential.  


## 6.3. AAL 2 Requirements

- The CSP SHOULD check the status of the original authenticator weekly. 


## <a name="dc-ial3"></a>6.4. AAL 3 Requirements
2. At IAL3, the CSP SHOULD verify in-person that a claimant possesses, controls and can successfully authenticate using the primary authenticator(s). 
1.  The CSP SHOULD perform in-person issuance. This is important if the CSP needs to explicitly provision the authenticator to a trusted device and in-person is the only mechanism to ensure delivery and assurance.
2. The CSP SHOULD check the status of the original authenticator daily.
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the primary authenticator was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured.
4. The CSP SHALL compare a fresh biometric sample obtained in person from the applicant to the reference biometric retained when the primary AAL3 authenticator was issued.
5. The CSP SHALL determine that the original, primary authenticator meets all AAL3 requirements.

