<a name="sec6"></a>

# 6. Requirements for Derived Credentials

Where the applicant already possesses recognized authentication credentials from a trusted CSP, the additional CSP may choose to identity proof the claimant by verifying possession and control of the token associated with the credentials and issue a new derived credential.  The following details the proofing requirements for the CSP issuing a derived credential.

#### 6.5.1. General Requirements

- Before issuing any derived credential the CSP SHALL verify the original credential status and SHALL verify that the corresponding credential is possessed and controlled by the claimant.  
- The CSP SHALL record the details of the original credential used as the basis for derived credential issuance. 
- The CSP SHOULD set the expiration of the new credential to the expiration of the original credential. There are instances where the derived credential need not be directly tied to the expiration of the primary credential as the derived credential can provide authentication services in its place, for example, while the expiring primary credential is being replaced.
- The CSP that issued the derived credential SHOULD notify the issuer of the original, primary credential if the derived credential is revoked.

#### 6.5.2. IAL 2 Requirements

- The CSP SHOULD check the expiration/revocation/termination status of the original credential weekly. 


#### 6.5.3. IAL 3 Requirements
- The CSP SHALL perform in-person proofing only.
- The CSP SHOULD check the expiration/revocation/termination status of the original credential daily.
- The CSP SHALL obtain and verify a copy of a biometric recorded when the original credential was issued. An example of such a biometric is the signed biometric data object, however if the biometric reference is not available from the original AAL 3 authenticator, it may be obtained elsewhere, as long as its authenticity is assured.
- The CSP SHALL compare a fresh biometric sample obtained in person from the applicant to the reference biometric retained from the original, primary AAL 3 authenticator and determine that they match.
- The CSP SHALL determine that the authenticator of the original, primary credential meets all requirements of an AAL 3 authenticator.
