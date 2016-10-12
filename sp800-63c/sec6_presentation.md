<a name="sec6"></a>

## 6. Assertion Presentation

Assertions MAY be presented in either a *back-channel* or *front-channel* manner from the IdP to the RP. Each model has its benefits and drawbacks, but both require the proper validation of the assertion. Assertions MAY also be proxied to facilitate federation between IdPs and RPs under specific circumstances, as discussed in section 4.1.4.

The IdP SHALL transmit only those attributes that were explicitly requested by the RP. RPs SHALL conduct a privacy risk assessment when determining which attributes to request. 

The subscriber SHALL be able to view the attribute values to be transmitted, although masking mechanisms SHALL be employed, as necessary, to mitigate the risk of unauthorized exposure of sensitive information (e.g. shoulder surfing). The subscriber SHALL receive explicit notice and be able to provide positive confirmation before any attributes about the subscriber are transmitted to any RP. At a minimum, the notice SHOULD be provided by the party in the position to provide the most effective notice and obtain confirmation. See section 9.2 for considerations on determining which party should provide the notice and obtain confirmation. If the protocol in use allows for optional attributes, the subscriber SHALL be given the option to decide whether to transmit those attributes to the RP. A IdP MAY employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP. 

### 6.1. Back-channel presentation

In the *back-channel* model, the subscriber is given an assertion reference to present to the RP, generally through the front channel. The assertion reference itself contains no information about the subscriber and SHALL be resistant to tampering and fabrication by an attacker. The RP presents the assertion reference to the IdP, usually along with authentication of the RP itself, to fetch the assertion.


<a name="63cSec6-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 1: Back-channel presentation](sp800-63c/media/indirect.png)

**Figure 6-1: Back-channel presentation**

</div>




In this model, the assertion itself is requested directly from the IdP to the RP, minimizing chances of interception and manipulation by a third party (including the subscriber themselves).

This method also allows the RP to query the CSP for additional attributes about the subscriber not included in the assertion itself, since back-channel communication can continue to occur after the initial authentication transaction has completed.

In the back-channel method, there are more network transactions required, but the information is limited to the parties that need it. Since an RP is expecting to get an assertion only from the IdP directly, the attack surface is reduced it is more difficult to inject assertions directly into the RP.

The assertion reference:

 - SHALL be limited to use by a single RP
 - SHALL be single-use
 - SHOULD be time limited with a short lifetime of seconds or minutes
 - SHOULD be presented along with authentication of the RP

The RP SHALL protect itself against injection of manufactured or captured assertion references by use of cross-site scripting protection or other accepted techniques. 

Claims within the assertion SHALL be validated including issuer verification, signature validation, and audience restriction.

Conveyance of the assertion reference from the IdP to the subscriber as well as from the subscriber to the RP SHALL be made over an authenticated protected channel. Conveyance of the assertion reference from the RP to the IdP as well as the assertion from the IdP to the RP SHALL be made over an authenticated protected channel.

Presentation of the assertion reference at the IdP SHOULD require authentication of the RP before an assertion is issued.

### 6.2. Front-channel Presentation

In the *front-channel* model, the IdP creates an assertion and sends it to the subscriber after successful authentication. The assertion is used by the subscriber to authenticate to the RP. This is often handled by mechanisms within the subscriber’s browser.) 


<a name="63cSec6-Figure2"></a>

<div class="text-center" markdown="1">
![Figure 2: Front-channel presentation](sp800-63c/media/direct.png)


**Figure 6-2: Front-channel presentation**

</div>




In the front-channel method, an assertion is visible to the subscriber, which could potentially cause leakage of system information included in the assertion. 

Since the assertion is under the control of the subscriber, the front-channel presentation method also allows the subscriber to submit a single assertion to unintended parties, perhaps by a browser replaying an assertion at multiple RPs. Even if the assertion is audience restricted and rejected by RPs, its presentation at unintended RPs could lead to leaking information about the subscriber and their online activities. Though it is possible to intentionally create an assertion designed to be presented to multiple RPs, this method can lead to lax audience restriction of the assertion itself, which in turn could lead to privacy and security breaches for the subscriber across these RPs. Such multi-RP use is not recommended. Instead, RPs are encouraged to fetch their own individual assertions.

The RP SHALL protect itself against injection of manufactured or captured assertions by use of cross-site scripting protection or other accepted techniques. 

Claims within the assertion SHALL be validated including issuer verification, signature validation, and audience restriction.

Conveyance of the assertion from the IdP to the subscriber as well as from the subscriber to the RP SHALL be made over an authenticated protected channel.

### 6.3. Assertion proxying

In some implementations, a proxy takes in an assertion from the IdP and creates a derived assertion when interacting directly with the RP, acting as an intermediary between the subscriber, the IdP, and the RP. From the perspective of the true IdP, the proxy is a single RP. From the perspective of the true RPs, the proxy is a single IdP. (See section 4.1.4.) 

There are several common reasons for such proxies:

- Portals that provide users access to multiple RPs that require user authentication

- Web caching mechanisms that are required to satisfy the RP’s access control policies, especially when mutually-authenticated TLS with the subscriber is used

- Network monitoring and/or filtering mechanisms that terminate TLS in order to inspect and manipulate the traffic

Conveyance of all information SHALL be made over authenticated protected channels.

### 6.4. Protecting Information

Communications between the IdP and the RP SHALL be protected in transit using an authenticated protected channel.

Note that the IdP may have access to information that may be useful to the RP in enforcing security policies, such as device identity, location, system health checks, and configuration management. If so, it may be a good idea to pass this information along to the RP within the bounds of the subscriber's privacy preferences.

Additional attributes about the user MAY be included outside of the assertion itself as part of a separate authorized request from the RP to the IdP. The authorization for access to these attributes MAY be issued alongside the assertion itself. Splitting user information in this manner can aid in protecting user privacy and allow for limited disclosure of identifying attributes on top of the essential information in the authentication assertion itself.

The RP SHALL, where feasible, request attribute claims rather than full attribute values. The IdP SHALL support attribute claims.  

