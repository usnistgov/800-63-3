<a name="sec6"></a>

<div class="breaker"></div>

# <a name="resuse_proof"></a> 6. Reusing Identity Proofing

_This section is normative._

It is beneficial to an individual and an organization to re-proof as little as possible.  Wherever possible, verifying that an individual has already been successfully identity proofed SHOULD be performed.  The primary method for an individual to verify they have been proofed is through successful possession and authentication of an authenticator that bound via a credential to an identity proofed at a given IAL.  

The IAL of the credential bound to the derived authenticator SHALL be at or below the primary IAL. In most cases the IALs are expected to be the same in order to benefit from the reuse of the original identity proofing events.  

This section details requirements for two specific use cases:

1. A _claimant_ obtains a secondary, or derived authenticator, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases, or a temporary authenticator. See [Section 6.1](#dc) for more details.
2. An _applicant_ seeks to obtain another primary authenticator from a CSP that did not issue the original authenticator. For example, if an applicant wants to switch CSPs and/or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). See [Section 6.2](#prior) for more details.

Details on dervied authenticator lifecycle requirements can be found in SP 800-63B, [Section 6.5](#dc).

## <a name="dc"></a> 6.1. Requirements for a Single CSP 

This section applies when the secondary authenticator is directly tied to the authorizations of having, and proving possession of, a primary authenticator, typically issued by the same CSP.

1.  At IAL3, the CSP SHOULD verify in-person that a claimant possesses, controls and can successfully authenticate using the primary authenticator. 

## <a name="prior"></a>6.2. Requirements for unrelated CSPs

Where the applicant already possesses an authenticator from a trusted CSP, the new CSP could choose to "inherit" the successful identity proofing transaction performed in a prior encounter at the original CSP, by verifying possession and control of the authenticator associated with the original CSP.  The following details the requirements for the new CSP:

1. The CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.
2. The CSP SHALL verify the original authenticator status. The CSP SHALL NOT issue a derived authenticator if status indicates any type of termination, disablement, revocation, or expiration. This requirement is based on the possiblility that the primary CSP may revoke an authenticator because the underlying proofing was fraudulent or successful in error.
3. The CSP SHALL determine the IAL associated with the original authenticator.
4. The CSP SHOULD determine the proofing process used by the originating CSP.  If the processes are materially different, the CSP SHOULD re-proof the identity.
5. The CSP SHOULD assert the linear distance from the original proofing event.  For example, if the applicant obtains a 3rd authenticator from a 3rd CSP, the 3rd CSP would assert "3" or "twice removed".  The assertion type, attribute name, and corresponding value is not in scope of this document.
6. At IAL3, the CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image or fingerprints) to ensure that the applicant cannot repudiate application.  See [Section 5.2.3](#biometric_use) of SP 800-63B for more detail on biometric collection.