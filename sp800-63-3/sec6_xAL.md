<a name="sec6"></a>

<div class="breaker"></div>

## 6. <a name="toFedorNotToFed"></a> Federation Considerations

*This section is informative.*

The technical guidelines detailed in NIST SP 800-63-3 and its companion volumes are agnostic to the authentication and identity proofing architecture an agency selects. However, there are scenarios an agency may encounter which make identity federation potentially more attractive than establishing identity services local to the agency or individual applications. The following list details the scenarios where an agency may consider federation as a viable option. This list does not factor in any economic benefits or weaknesses of federation vs. localized identity architectures.

**Federate authenticators when:**

* Potential users already have an authenticator at or above required AAL.
* Multiple credential form factors are required to cover all possible user communities.
* Agency does not have infrastructure to support authentication management (e.g., account recovery, authenticator issuance, help desk).
* Desire to allow the primary authentication to be modified and upgraded over time without changing the RP's implementation.
* There are different environments to be supported, as federation protocols are network-based and allow for implementation on a wide variety of platforms and languages.
* Potential users come from multiple communities, each with its own existing identity infrastructure.

**Federate attributes when:**  

* Pseudonymity is required, necessary, feasible, or important to stakeholders accessing the service.
* Access to the service only requires a partial attribute list.
* Access to the service only requires at least one attribute claim.
* Agency is not the authoritative source or issuing source for required attributes.  
* Attributes are only required temporarily during use (such as to make an access decision), such that agency does not need to locally persist the data.



