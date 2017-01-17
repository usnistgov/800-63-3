<a name="sec6"></a>

<div class="breaker"></div>

# <a name="resuse_proof"></a> 6. Derived Authenticators

_This section is normative._

It is beneficial to an individual and an organization to re-proof as little as possible.  Wherever possible, verifying that an individual has already been successfully identity proofed SHOULD be performed.

>Note: This guideline supports using digital credentials, in addition to physical credentials, as identity evidence.  See [Section 5.2.](#validate) for more information.

There are two specific use cases to consider when leveraging the proofing associated with an individual:

1. A _claimant_ obtains a secondary, or derived authenticator, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases, or a temporary authenticator. See [Section 6.1](#dc) for more details. *This section covers this use case.*
2. An _applicant_ seeks to obtain another primary authenticator from a CSP that did not issue the original authenticator. For example, if an applicant wants to switch CSPs and/or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). See [Section 6.2](#prior) for more details. *This use case is covered by allowable identity evidence in [Section 5.2](#validate); therefore, this section does not contain any additional requirements.*


**Requirements:**  
1. The IAL of the credential bound to the derived authenticator SHALL be at or below the primary IAL. In most cases the IALs are expected to be the same in order to benefit from the reuse of the original identity proofing event(s).  
2. At IAL3, the CSP SHOULD verify in-person that a claimant possesses, controls and can successfully authenticate using the primary authenticator. 

Details on dervied authenticator lifecycle requirements can be found in SP 800-63B, [Section 6.5](#dc).