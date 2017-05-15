<div class="breaker"></div>
<a name="sec4"></a>

## 4. Federation

*This section is normative.*

In a federation protocol, a three-party relationship is formed between the subscriber, the IdP, and the RP as shown in [Figure 4-1](#63cSec4-Figure1). Depending on the specifics of the protocol, different information passes among the participants at different times. The subscriber communicates with both the IdP and the RP, usually through a browser. The RP and the IdP communicate with each other in two ways:

 - The *front channel*, through redirects involving the subscriber; or
 - The *back channel*, through a direct connection between the RP and IdP, not involving the subscriber.

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 1: Federation](sp800-63c/media/federation.png)

**Figure 4-1. Federation**

</div>

The subscriber authenticates to the IdP as described in [[SP 800-63B]](sp800-63b.html), and then the result of that authentication event is asserted to the RP across the network. The IdP can also make attribute statements about the subscriber as part of this process. These attributes and authentication event information are carried to the RP through the use of an assertion, described in [Section 5](#sec5).

### <a name="federation-model"></a> 4.1. Federation Models

IdPs that provide authentication services and RPs that consume those services are known as members of a federation. From an IdP's perspective, the federation consists of the RPs that it services. From an RP's perspective, the federation consists of the IdPs that it uses. This section provides an overview of and requirements for common identity federation models currently in use. In each model, relationships are established between members of the federation.

#### <a name="manual-registration"></a> 4.1.1. Manual Registration

In the manual registration model, the IdP and RP manually provision configuration information about parties with which they expect to interoperate. IdPs MAY configure RPs using an explicit whitelist, allowing these RPs to receive authentication and attribute information as part of the authentication transaction. In such cases where an RP is not whitelisted, the IdP SHALL require runtime decisions (see [Section 4.1.5](#runtime-decisions)) to be made by an authorized party, such as the subscriber, before releasing user information.

IdPs and RPs MAY act as their own authorities of who to federate with or MAY externalize those authority decisions to an external party as in [Section 4.1.3](#authorities).

Protocols requiring the transfer of keying information SHALL use a secure method to exchange keying information needed to operate the federated relationship during the registration process, including any shared secrets or public keys. Any symmetric keys used in this relationship SHALL be unique to a pair of federation participants.

Federation relationships SHALL establish parameters regarding expected and acceptable IALs and AALs in connection with the federated relationship.

#### <a name="dynamic-registration"></a> 4.1.2. Dynamic Registration

In the dynamic registration model of federation, it is possible for relationships between members of the federation to be negotiated at the time of a transaction. This process allows IdPs and RPs to be connected together without manually establishing a connection between them using manual registration (See [Section 4.1.1](#manual-registration)). IdPs that support dynamic registration SHALL make their configuration information (such as dynamic registration endpoints) available in such a way as to minimize system administrator involvement.

Protocols requiring the transfer of keying information SHALL use a secure method to establish such keying information needed to operate the federated relationship during the registration process, including any shared secrets or public keys. Any symmetric keys used in this relationship SHALL be unique to a pair of federation participants.

IdPs SHALL require runtime decisions (see [Section 4.1.5](#runtime-decisions)) to be made by an authorized party, such as the subscriber, before releasing user information. An IdP accepting dynamically registered RPs MAY limit the types of attributes and other information made available to such RPs. An RP capable of dynamically registering MAY limit which IdPs it is willing to accept identity information from.

Frequently, parties in a dynamic registration model do not know each other ahead of time. Where possible, this SHOULD be augmented by *software statements*, which allow federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes describing the RP software, cryptographically signed by an authority (either the IdP itself, a federation authority as in [Section 4.1.3](#authorities), or another trusted party). This cryptographically verifiable statement allows the connection to be established or elevated between the federating parties without relying solely on self-asserted attributes. (See [[RFC 7591]](#RFC7591) Section 2.3 for more information on one protocol's implementation of software statements.)

#### <a name="authorities"></a> 4.1.3. Federation Authorities

Some federated parties defer to an authority known as a *federation authority* to assist in making federation decisions and to establish the working relationship between parties. In this model, the federation authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards, but the level of vetting, if it occurs at all, is unique to the use cases and models employed within the federation.

Federation authorities SHALL establish parameters regarding expected and acceptable IALs and AALs in connection with the federated relationships they enable. Federation authorities SHALL individually vet each participant in the federation to determine that they adhere to their expected security, identity, and privacy standards. Vetting of IdPs and RPs SHALL establish, as a minimum, that:

* Assertions generated by IdPs adhere to the requirements in [Section 5](#sec5).
* RPs adhere to IdP requirements for the handling of subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.

Federation authorities MAY assist the technical connection and configuration process between members, such as by publishing configuration data for IdPs or issuing software statements for RPs.

Most federations managed through authorities have a simple membership model: either parties are in the federation or they are not. However, more sophisticated federations MAY have multiple tiers of membership which can be used by federated parties to tell whether other parties in the federation have been more thoroughly vetted. IdPs MAY decide that certain subscriber information is only releasable to RPs in higher tiers, and RPs MAY decide to accept certain information only from IdPs in higher tiers.

#### <a name="proxied"></a> 4.1.4. Proxied Federation

In a proxied federation, communication between the IdP and the RP is intermediated in a way that prevents direct communication between the two parties. There are multiple methods to achieve this effect; common configurations include:

* A third party that acts as a federation proxy (or *broker*)
* A network of nodes that distributes the communications

Where proxies are used, they function as an IdP on one side and an RP on the other side. Therefore, all normative requirements that apply to IdPs and RPs SHALL apply to proxies in their respective roles.

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 2: Federation Proxy](sp800-63c/media/broker.png)

**Figure 4-2. Federation Proxy**
</div>

A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks of federation described in [Section 4.2](#privacy-reqs) below.

See [Section 9.5](#blinding) for further information on blinding techniques, their uses, and limitations.

#### 4.1.5. <a name="runtime-decisions"></a>Runtime Decisions

The fact that parties have federated SHALL NOT be interpreted as permission to pass information. The decision of whether an authentication can occur or attributes are passed can be determined by the use of a whitelist, a blacklist, or a runtime decision by an authorized party.

IdPs MAY establish whitelists of RPs that are authorized to receive authentication and attributes from the IdP, without runtime decision from the subscriber. IdPs MAY also establish blacklists of RPs who are not authorized to receive authentication or attributes from the IdP, even when requested by the subscriber. Both whitelists and blacklists identify RPs by their domain or other sufficiently unique identifier, depending on the federation protocol in use. Every RP that is not on a whitelist or a blacklist SHALL be placed by default in a gray area where runtime authorization decisions will be made by an authorized party, usually the subscriber.

RPs MAY establish whitelists of IdPs that are authorized to send authentication and attributes to the RP, without runtime decision from the subscriber. RPs MAY also establish blacklists of IdPs who are not authorized to send authentication or attributes to the RP, even when requested by the subscriber. Both whitelists and blacklists identify IdPs by their domain or other sufficiently unique identifier, depending on the federation protocol in use. Every IdP that is not on a whitelist or a blacklist SHALL be placed by default in a gray area where runtime authorization decisions will be made by an authorized party, usually the subscriber.

To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP SHALL, by default, mask sensitive information displayed to the subscriber.  The IdP SHALL provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values. The IdP SHALL provide effective mechanisms for redress of applicant complaints or problems (e.g., subscriber identifies an inaccurate attribute value). For more details on masking and redress, please see [Section 10](#sec10) on usability considerations.

The subscriber SHALL receive explicit notice and be able to provide positive confirmation before any attributes about the subscriber are transmitted to any RP. At a minimum, the notice SHOULD be provided by the party in the position to provide the most effective notice and obtain confirmation, consistent with [Section 9.2](#notice). If the protocol in use allows for optional attributes, the subscriber SHALL be given the option to decide whether to transmit those attributes to the RP. An IdP MAY employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP.

### <a name="privacy-reqs"></a> 4.2. Privacy Requirements

Federation involves the transfer of personal attributes from a third party, the IdP, that is not otherwise involved in a transaction. Federation also potentially gives the IdP broad visibility into subscriber activities. Accordingly, there are specific privacy requirements associated with federation.

Communication between the RP and the IdP could reveal to the IdP where the subscriber is conducting a transaction. Communication with multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed without federation. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not always align with the privacy interests of subscribers.

The IdP SHALL NOT disclose information on subscriber activities at an RP to any party, nor use the information for any purpose other than federated authentication, to comply with law or legal process, or in the case of a specific user request for the information. The IdP SHOULD employ technical measures, such as the use of pairwise pseudonymous identifiers described in [Section 5.2.5](#ppi) or privacy-enhancing cryptographic protocols, to provide unlinkability and discourage subscriber activity tracking and profiling.

An IdP MAY disclose information on subscriber activities to other RPs within the federation for security purposes such as communication of compromised subscriber accounts.

The following requirements apply specifically to agencies:

1. The agency SHALL consult with their Senior Agency Official for Privacy (SAOP) to conduct an analysis to determine whether the agency that is acting as either an IdP or an RP in an identity federation triggers the requirements of the Privacy Act.

2. The agency SHALL publish or identify coverage by a System of Records Notice (SORN) as applicable.

3. The agency SHALL consult with their SAOP to conduct an analysis to determine whether the agency that is acting as either an IdP or an RP in an identity federation triggers the requirements of the E-Government Act.

4. The agency SHALL publish or identify coverage by a Privacy Impact Assessment (PIA) as applicable.

### 4.3. <a name="federation-session"></a> Reauthentication and Session Requirements in Federated Environments

In a federated environment, the RP manages its sessions separately from any sessions at the IdP. The session at the RP starts when the RP processes the federation protocol from the IdP. At the time of a federated login, the subscriber MAY have an existing session at the IdP which MAY be used as part of the authentication process to the RP. The IdP SHALL communicate any information it has regarding the time of the latest authentication event at the IdP, and the RP MAY use this information in determining its access policies. Depending on the capabilities of the federation protocol in use, the IdP SHOULD allow the RP to request that the subscriber re-authenticate at the IdP as part of a federation request.

Due to the distributed nature of a federated system, the subscriber is capable of terminating sessions with the IdP and RP independently of one another. The RP SHALL NOT assume that the subscriber has an active session at the IdP past the establishment of the federated log in. The IdP SHALL NOT assume that termination of the subscriber's session at the IdP will propagate to any sessions that subscriber would have at downstream RPs.

See [SP 800-63B Section 7](sp800-63b.html#sec7) for more information about session management requirements.
