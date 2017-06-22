<a name="sec7"></a>

<div class="breaker"></div>

## 7 <a name="toFedorNotToFed"></a> Federation Considerations

_This section is informative._

This guideline and its companion volumes are agnostic to the authentication and identity proofing architecture an agency selects. However, there are scenarios an agency may encounter that make identity federation potentially more efficient and effective than establishing identity services local to the agency or individual applications. The following list details scenarios where, if any apply, the agency may consider federation a viable option. This list does not take into consideration any economic benefits or weaknesses of federation vs. localized identity architectures.

Federate authenticators when:

1. Potential users already have an authenticator at or above required AAL.
2. Multiple credential form factors are required to cover all possible user communities.
3. Agency does not have infrastructure to support authentication management (e.g., account recovery, authenticator issuance, help desk).
4. There is a desire to allow primary authenticators to be added and upgraded over time without changing the RP's implementation.
5. There are different environments to be supported, as federation protocols are network-based and allow for implementation on a wide variety of platforms and languages.
6. Potential users come from multiple communities, each with its own existing identity infrastructure.

Federate attributes when:

1. Pseudonymity is required, necessary, feasible, or important to stakeholders accessing the service.
2. Access to the service only requires a partial attribute list.
3. Access to the service only requires at least one attribute reference.
4. The agency is not the authoritative source or issuing source for required attributes.
5. Attributes are only required temporarily during use (such as to make an access decision), such that agency does not need to locally persist the data.
