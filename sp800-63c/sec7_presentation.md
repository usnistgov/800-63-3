<a name="presentation"></a>

## 7 Assertion Presentation

*This section is normative.*

Assertions MAY be presented in either a *back-channel* or *front-channel* manner from the IdP to the RP. There are tradeoffs with each model, but each requires the proper validation of the assertion. Assertions MAY also be proxied to facilitate federation between IdPs and RPs under specific circumstances, as discussed in [Section 5.1.4](#proxied).

The IdP SHALL transmit only those attributes that were explicitly requested by the RP. RPs SHALL conduct a privacy risk assessment when determining which attributes to request. 

### <a name="back-channel"></a> 7.1 Back-Channel Presentation

In the *back-channel* model, the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and SHALL be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP, usually along with authentication of the RP itself, to fetch the assertion.

<a name="63cSec7-Figure1"></a>

<div class="text-center" markdown="1">
<img src="sp800-63c/media/back-channel.png" alt="Back-channel Presentation" style="width:614px;height:600px;;min-width:614px;min-height:600px;"/>

**Figure 7-1 Back Channel Presentation**

</div>

As shown in [Figure 7-1](#63cSec7-Figure1), the back-channel presentation model consists of three steps:

1. The IdP sends an assertion reference to the subscriber through the front channel.
2. The subscriber sends the assertion reference to the RP through the front channel.
3. The RP presents the assertion reference and its RP credentials to the IdP through the back channel. The IdP validates the credentials and returns the assertion.

The assertion reference:

 1. SHALL be limited to use by a single RP.
 2. SHALL be single-use.
 3. SHOULD be time limited with a short lifetime of seconds or minutes.
 4. SHOULD be presented along with authentication of the RP.

In this model, the RP directly requests the assertion from the IdP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).

This method also allows the RP to query the IdP for additional attributes about the subscriber not included in the assertion itself, since back-channel communication can continue to occur after the initial authentication transaction has been completed without sending the user back to the IdP. This query occurs using an authorization credential issued alongside the assertion, as described in [Section 6](#assertions).

More network transactions are required in the back-channel method, but the information is limited to only those parties that need it. Since an RP is expecting to get an assertion only from the IdP directly, the attack surface is reduced. Consequently, it is more difficult to inject assertions directly into the RP.

The RP SHALL protect itself against injection of manufactured or captured assertion references by use of cross-site scripting protection or other accepted techniques.

Elements within the assertion SHALL be validated by the RP, including:

 - *Issuer verification*: ensuring the assertion was issued by the IdP the RP expects it to be from.
 - *Signature validation*: ensuring the signature of the assertion corresponds to the key related to the IdP sending the assertion.
 - *Time validation*: ensuring the expiration and issue times are within acceptable limits of the current timestamp.
 - *Audience restriction*: ensuring this RP is the intended recipient of the assertion.

Conveyance of the assertion reference from the IdP to the subscriber, as well as from the subscriber to the RP, SHALL be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP, as well as the assertion from the IdP to the RP, SHALL be made over an authenticated protected channel.

When assertion references are presented, the IdP SHALL verify that the party presenting the assertion reference is the same party that requested the authentication. The IdP can do this by requiring the RP to authenticate itself when presenting the assertion reference to the IdP or through other similar means (see [RFC 7636](#RFC7636) for one protocol's method of RP identification).

Note that in a federation proxy described in [Section 5.1.4](#proxied), the IdP audience restricts the assertion reference and assertion to the proxy, and the proxy restricts any newly-created assertion references or assertions to the downstream RP.

### <a name="front-channel"></a> 7.2 Front-Channel Presentation

In the *front-channel* model, the IdP creates an assertion and sends it to the subscriber after successful authentication. The assertion is used by the subscriber to authenticate to the RP, often through mechanisms within the subscriber's browser.


<a name="63cSec7-Figure2"></a>

<div class="text-center" markdown="1">
<img src="sp800-63c/media/front-channel.png" alt="Front-channel Presentation" style="width:686px;height:600px;;min-width:686px;min-height:600px;"/>

**Figure 7-2 Front Channel Presentation**

</div>

An assertion is visible to the subscriber in the front-channel method, which could potentially cause leakage of system information included in the assertion. Further, it is more difficult in this model for the RP to query the IdP for additional attributes after the presentation of the assertion.

Since the assertion is under the subscriber's control, the front-channel presentation method also allows the subscriber to submit a single assertion to unintended parties, perhaps by a browser replaying an assertion at multiple RPs. Even if the assertion is audience-restricted and rejected by unintended RPs, its presentation at unintended RPs could lead to leaking information about the subscriber and their online activities. Though it is possible to intentionally create an assertion designed to be presented to multiple RPs, this method can lead to lax audience restriction of the assertion itself, which in turn could lead to privacy and security breaches for the subscriber across these RPs. Such multi-RP use is not recommended. Instead, RPs are encouraged to fetch their own individual assertions.

The RP SHALL protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection or other accepted techniques. 

Elements within the assertion SHALL be validated by the RP including:

 - *Issuer verification*: ensuring the assertion was issued by the expected IdP.
 - *Signature validation*: ensuring the signature of the assertion corresponds to the key related to the IdP making the assertion.
 - *Time validation*: ensuring the expiration and issue times are within acceptable limits of the current timestamp.
 - *Audience restriction*: ensuring this RP is the intended recipient of the assertion.

Conveyance of the assertion from the IdP to the subscriber, as well as from the subscriber to the RP, SHALL be made over an authenticated protected channel.

Note that in a federation proxy described in [Section 5.1.4](#proxied), the IdP audience restricts the assertion to the proxy, and the proxy restricts any newly-created assertions to the downstream RP.

### <a name="protecting-information"></a> 7.3 Protecting Information

Communications between the IdP and the RP SHALL be protected in transit using an authenticated protected channel. Communications between the subscriber and either the IdP or the RP (usually through a browser) SHALL be made using an authenticated protected channel.

Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences described in [Section 9.2](#notice).

Additional attributes about the user MAY be included outside of the assertion itself as part of a separate authorized request from the RP to the IdP. The authorization for access to these attributes MAY be issued alongside the assertion itself. Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.

The RP SHALL, where feasible, request attribute references rather than full attribute values as described in [Section 9.3](#minimization). The IdP SHALL support attribute references.

