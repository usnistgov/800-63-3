<a name="fal"></a>

## 4 Federation Assurance Level (FAL)

*This section is normative.*

This section defines allowable Federation Assurance Levels, or FAL. The FAL describes requirements for how assertions are constructed and secured for a given transaction. These levels can be requested by an RP or required by the configuration of both the RP and the IdP for a given transaction.

All assertions SHALL be used with a federation protocol as described in [Section 4](#federation). All assertions SHALL comply with the detailed requirements in [Section 6](#assertions). All assertions SHALL be presented using one of the methods described in [Section 7](#presentation). While many different federation implementation options are possible, the FAL is intended to provide clear implementation recommendations representing increasingly secure deployment options. Combinations of aspects not found in the FAL table are possible but outside the scope of this volume. See [SP 800-63 Section 6.3](sp800-63-3.html#FAL_CYOA) for details on how to choose the most appropriate FAL.

This table presents different requirements for each FAL. Each successive level subsumes and fulfills all requirements of lower levels. Federations presented through a proxy SHALL be represented by the lowest level used during the proxied transaction.

<a name="63cSec4-Table1"></a>

<div class="text-center" markdown="1">


**Table 4-1 Federation Assertion Levels**

</div>

|FAL|Requirement|
|:--:|----|----|
|1|Bearer assertion, signed by IdP.|
|2|Bearer assertion, signed by IdP and encrypted to RP.|
|3|Holder of key assertion, signed by IdP and encrypted to RP.|

For example, FAL1 maps to the OpenID Connect Basic Client profile or Security Assertion Markup Language (SAML) Web SSO Artifact Binding profile with no additional features. FAL2 additionally requires that the assertion (e.g., the OpenID Connect ID Token or SAML Assertion) be encrypted to a public key representing the RP in question. FAL3 requires the subscriber to cryptographically prove possession of a key bound to the assertion (e.g., the use of a cryptographic authenticator) along with all requirements of FAL2. The additional key presented at FAL3 need not be the same key used by the subscriber to authenticate to the IdP.

Regardless of what the RP requests or what the protocol requires, the RP can easily detect the FAL in use by observing the nature of the assertion as it is presented as part of the federation protocol. Therefore, the RP is responsible for determining which FALs it is willing to accept for a given authentication transaction and ensuring that the transaction meets that FAL's requirements.

If the RP is using a front-channel presentation mechanism, as defined in [Section 7.2](#front-channel) (e.g., the OpenID Connect Implicit Client profile or the SAML Web SSO profile), it SHALL require FAL2 or greater in order to protect the information in the assertion from disclosure to the browser or other parties in the transaction other than the intended RP.

Additionally, the IdP SHALL employ appropriately-tailored security controls (to include control enhancements) from the moderate or high baseline of security controls defined in [SP 800-53](#SP800-53) or equivalent federal (e.g., [FEDRAMP](#FEDRAMP)) or industry standard.

### <a name="key-mgmt"></a>4.1 Key Management

At any FAL, the IdP SHALL ensure that an RP is unable to impersonate the IdP at another RP by protecting the assertion with a signature and key using approved cryptography. If the assertion is protected by a digital signature using an asymmetric key, the IdP MAY use the same public and private key pair to sign assertions to multiple RPs. The IdP MAY publish its public key in a verifiable fashion, such as at an HTTPS-protected URL at a well-known location. If the assertion is protected by a MAC using a shared key, the IdP SHALL use a different shared key for each RP.

Government-operated IdPs asserting authentication at AAL2 and all IdPs asserting authentication at AAL3 SHALL protect keys used for signing or encrypting those assertions with mechanisms validated at [FIPS 140](#FIPS140) Level 1 or higher.

### 4.2 <a name="runtime-decisions"></a>Runtime Decisions

The fact that parties have federated SHALL NOT be interpreted as permission to pass information. The decision of whether an authentication can occur or attributes may be passed can be determined by the use of a whitelist, a blacklist, or a runtime decision by an authorized party.

IdPs MAY establish whitelists of RPs authorized to receive authentication and attributes from the IdP without a runtime decision from the subscriber. All RPs in an IdP's whitelist SHALL abide by the provisions and requirements in the SP 800-63 suite. IdPs SHALL make whitelists available to subscribers as described in [Section 9.2](#notice). IdPs MAY also establish blacklists of RPs not authorized to receive authentication or attributes from the IdP, even when requested by the subscriber. Both whitelists and blacklists identify RPs by their domain or other sufficiently unique identifier, depending on the federation protocol in use. Every RP not on a whitelist or a blacklist SHALL be placed by default in a gray area where runtime authorization decisions will be made by an authorized party, usually the subscriber. The IdP MAY remember a subscriber's decision to authorize a given RP, provided that the IdP SHALL allow the subscriber to revoke such remembered access at a future time.

RPs MAY establish whitelists of IdPs that the RP will accept authentication and attributes from without a runtime decision from the subscriber. All IdPs in an RP's whitelist SHALL abide by the provisions and requirements in the 800-63 suite. RPs MAY also establish blacklists of IdPs that the RP will not accept authentication or attributes from, even when requested by the subscriber. Both whitelists and blacklists identify IdPs by their domain or other sufficiently unique identifier, depending on the federation protocol in use. Every IdP that is not on a whitelist or a blacklist SHALL be placed by default in a gray area where runtime authorization decisions will be made by an authorized party, usually the subscriber. The RP MAY remember a subscriber's decision to authorize a given IdP, provided that the RP SHALL allow the subscriber to revoke such remembered access at a future time.

A subscriber's information SHALL NOT be transmitted between IdP and RP for any purpose other than those described in [Section 5.2](#privacy-reqs), even when those parties are whitelisted.

To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP SHALL, by default, mask sensitive information displayed to the subscriber. The IdP SHALL provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values. The IdP SHALL provide effective mechanisms for redress of applicant complaints or problems (e.g., subscriber identifies an inaccurate attribute value). For more details on masking and redress, please see [Section 10](#usability) on usability considerations.

When the subscriber is involved in a runtime decision, the subscriber SHALL receive explicit notice and be able to provide positive confirmation before any attributes about the subscriber are transmitted to any RP. At a minimum, the notice SHOULD be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Section 9.2](#notice). If the protocol in use allows for optional attributes, the subscriber SHALL be given the option to decide whether to transmit those attributes to the RP. An IdP MAY employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP.
