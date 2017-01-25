<div class="breaker"></div>
<a name="fal"></a>

## 7. Federation Assurance Level (FAL)

*This section is normative.*

This section defines allowable Federation Assurance Levels, or FAL. The FAL describes aspects of the assertion and federation protocol used in a given transaction. These levels can be requested by an RP or required by configuration of both RP and IdP for a given transaction. 

The FAL combines aspects of [assertion protection](#sec5) and [assertion presentation](#sec6) into an ordinal measurement scale applicable across different [federation models](#sec4). All assertions SHALL comply with the requirements in [Section 5](#sec5). While many other combinations of factors are possible, this list is intended to provide clear implementation recommendations representing increasingly secure deployment choices. Combinations of aspects not found in the FAL table are possible but outside the scope of this document.

This table presents different requirements depending on whether the assertion is presented through either the front channel or the back channel (via an assertion reference). Each successive level subsumes and fulfills all requirements of lower levels. Federations presented through a proxy SHALL be represented by the lowest level used during the proxied transaction.

<a name="63cSec7-Table1"></a>

<div class="text-center" markdown="1">


**Table 7-1: Federation Assertion Levels**

</div>

|FAL|Requirement|
|:--:|----|----|
|1|Bearer assertion, signed by IdP.|
|2|Bearer assertion, signed by IdP and encrypted to RP.|
|3|Holder of key assertion, signed by IdP and encrypted to RP.|

For example, FAL1 maps to the OpenID Connect Basic Client profile or SAML (Security Assertion Markup Language) Web SSO Artifact Binding profile, with no additional features. FAL2 additionally requires that the OpenID Connect ID Token or SAML Assertion be encrypted to a public key representing the RP in question. FAL3 requires the presentation of an additional key bound to the assertion (e.g., the use of a cryptographic authenticator) along with all requirements of FAL2. Note that the additional key presented at FAL3 need not be the same key used by the subscriber to authenticate to the IdP.

Regardless of what is requested or required by the protocol, the FAL in use is easily detected by the RP by observing the nature of the assertion as it is presented as part of the federation protocol. Therefore, the RP is responsible for determining which FALs it is willing to accept for a given authentication transaction and ensuring that the transaction meets the requirements of that FAL.

If the RP is using a front-channel presentation mechanism (e.g., the OpenID Connect Implicit Client profile or the SAML Web SSO profile), it SHOULD require FAL2 or greater in order to protect the information in the assertion from the browser or other parties in the transaction.

[Table 7-2](#63cSec7-Table2) lists strict adherence to M-04-04 Level of Assurance, mapping the corresponding FALs.

<a name="63cSec7-Table2"></a>

<div class="text-center" markdown="1">

**Table 7-2: Legacy M-04-04 FAL Requirements**

</div>


| M-04-04 Level of Assurance (LOA) |  Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:
| 1 | 1
| 2 | 2
| 3 | 2
| 4 | 3

However, [Table 7-3](#63cSec7-Table3) shows the expanded set of FAL's that are allowable to meet M-04-04 Level of Assurance. Agencies SHALL select the corresponding FAL based on the assessed M-04-04 LOA.

<a name="63cSec7-Table3"></a>

<div class="text-center" markdown="1">

**Table 7-3: Recommended M-04-04 FAL Requirements**

</div>

| M-04-04 Level of Assurance | Federation Assurance Level
|:------------------:|:-----------------------------:
| 1 | 1, 2, or 3
| 2 | 2, or 3
| 3 | 2, or 3
| 4 | 3

### 7.1. Key Management

At any FAL, the IdP SHALL ensure that an RP is unable to impersonate the IdP at another RP by protecting the assertion with a signature and key using approved cryptography. If the assertion is protected by a digital signature using an asymmetric key, the IdP MAY use the same public and private key pair to sign assertions to multiple RPs. The IdP MAY publish its public key in a verifiable fashion, such as at an HTTPS-protected URL at a well-known location. If the assertion is protected by a MAC using a shared key, the IdP SHALL use a different shared key for each RP.
