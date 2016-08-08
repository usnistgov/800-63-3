<a name="sec6"></a>

# 6. Leveraging Antecedent Proofing Events

Possession of an authenticator, bound to an identity proofed at a given IAL, should allow a claimant to obtain additional authenticators, per CSP policy.  This section details requirements for two specific use cases:

1. A _claimant_ obtains a secondary, or derived authenticator, for use only within the limits and authorizations of the primary authenticator.  For example, this could be a derived PIV credential in federal use cases, or a temporary authenticator when the primary is lost or forgotten. See [Section 6.1](#dc) for more details.
2. An _applicant_ seeks to obtain another primary authenticator from a CSP that did not issue the original authenticator. For example, if an applicant wants to switch CSPs and/or have another authenticator at a new CSP for other uses (e.g. basic browsing vs. financial). See [Section 6.2](#prior) for more details.

## <a name="dc"></a> 6.1. Requirements for Derived Authenticators

This section applies when the secondary authenticator is directly tied to the authorizations of having, and proving possession of, a primary authenticator issued by the same CSP.

### 6.1.1. General Requirements

1. The CSP SHALL verify the original authenticator status.
2. The CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.  
3. The derived authenticator SHALL be valid only as long as the subscriber is authorized to hold the original authenticator.
4. The CSP SHALL record the details of the original authenticator used as the basis for derived authenticator issuance. 
5. The CSP SHOULD set the expiration of the derived authenticator to the expiration of the primary authenticator. There are instances where the derived authenticator need not be directly tied to the expiration of the primary authenticator as the derived authenticator can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
6. A derived authenticator MAY be issued at or below the primary authenticator IAL.


### 6.1.2. IAL 2 Requirements

- The CSP SHOULD check the status of the original authenticator weekly. 


### <a name="dc-ial3"></a>6.1.3. IAL 3 Requirements

1.  The CSP SHOULD perform in-person proofing. This is important if the CSP needs to explicitly provision the authenticator to a trusted device and in-person is the only mechanism to ensure delivery and assurance.
2. The CSP SHOULD check the status of the original authenticator daily.
3. The CSP SHALL obtain and verify a copy of a biometric recorded when the primary authenticator was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured.
4. The CSP SHALL compare a fresh biometric sample obtained in person from the applicant to the reference biometric retained from the original, primary AAL 3 authenticator and determine that they match.
5. The CSP SHALL determine that the authenticator of the original, primary authenticator meets all requirements of an AAL 3 authenticator.

## <a name="prior"></a>6.2 Requirement for Accepting Results of Prior Proofing

Where the applicant already possesses an authenticator from a trusted CSP, the new CSP could choose to "inherit" the successful identity proofing transaction performed in a prior encounter at the original CSP, by verifying possession and control of the authenticator associated the original CSP.  The following details the requirements for the new CSP:

### 6.2.1. General Requirements

Unless otherwise specified, the term "CSP" referenced below pertains to the CSP that depends on a prior proofing transaction.

1.  The CSP SHALL verify that the corresponding authenticator is possessed and controlled by the claimant.
2. The CSP SHOULD verify the original authenticator status prior to issuance.
3. The CSP SHOULD query the authenticator status of the original CSP on a regular basis.
4. The CSP SHALL determine the IAL associated with the original authenticator.
5. The CSP SHOULD determine the proofing process used by the originating CSP.  If the processes are materially different, the CSP SHOULD re-proof the identity.
6. The CSP SHOULD assert the linear distance from the original proofing event.  For example, if the applicant obtains a 3rd authenticator from a 3rd CSP, the 3rd CSP would assert "3" or "twice removed".  The assertion type, attribute name, and corresponding value is not in scope of this document.
7. The CSP MAY check the status of the original authenticator on an interval basis. 
8. A new authenticator MAY be issued at or below the primary authenticator IAL.

### 6.2.2. IAL 2 Requirements

- No additional requirements for IAL 2.

### 6.2.3. IAL 3 Requirements

1. All of the requirements of [Section 6.1.3.](#dc-ial3), in addition;
2. The CSP SHALL collect and record a biometric sample at the time of proofing (e.g., facial image or fingerprints) to ensure that the applicant cannot repudiate application.  See [Section 5.2.3](#biometric_use) of SP 800-63B for more detail on biometric collection.