<a name="sec4"></a>

## 4. Federation

In a federation protocol, a three-party relationship is formed between the subscriber, the identity provider (IdP), and the relying party (RP) as shown in [Figure 4-1](#63cSec4-Figure1). Depending on the specifics of the protocol, different information passes among the participants at different times. The subscriber communicates with both the IdP and the RP, usually through a web browser. The RP and the IdP communicate with each other in two ways:

 - The *front channel*, through redirects involving the subscriber,
 - or the *back channel*, through a direct connection between the RP and IdP, not involving the subscriber.

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 1: Federation](sp800-63c/media/federation.png)

**Figure 4-1: Federation**

</div>

The subscriber authenticates to the IdP as described in [SP 800-63B](sp800-63b.html), and then the result of that authentication event is asserted to the RP across the network. The IdP can also make attribute statements about the subscriber as part of this process. These attributes and authentication event information are carried to the RP through the use of an assertion, described in [Section 5](#sec5).

### 4.1. Federation Models

This section provides an overview of and requirements for common identity federation models currently in use. In each model, relationships are established between members of the federation in several different ways.

#### <a name="manual-registration"></a> 4.1.1. Manual Registration

In the manual registration model, the IdP and RP manually provision configuration information about parties with which they expect to interoperate. IdPs MAY configure RPs using an explicit whitelist, allowing services to transfer information as part of the authentication transaction. In such cases where an RP is not whitelisted, the IdP SHALL require appropriate [runtime decisions](#runtime-decisions) to be made by an authorized party, such as the subscriber, before releasing user information.

Protocols requiring the transfer of keying information SHALL use a secure method to establish such keying information needed to operate the federated relationship, including any shared secrets or public keys. Any symmetric keys used in this relationship SHALL be unique to a pair of federation participants.

Federation relationships SHALL establish parameters regarding expected and acceptable identity assurance level (IAL) and authentication assurance level (AAL) in connection with the federated relationship. For example, a given RP may only accept IAL 2 identity proofing from a given IdP that has been vetted at that level.

#### <a name="dynamic-registration"></a> 4.1.2. Dynamic Registration

In the dynamic registration model of federation, it is possible for relationships between members of the federation to be negotiated at the time of a transaction. This process allows components to be connected together without manually establishing a connection between components. IdPs that support dynamic registration SHALL make their configuration information (such as dynamic registration endpoints) available in such a way as to minimize system adminsitrator involvement. 

IdPs SHALL require appropriate [runtime decisions](#runtime-decisions) to be made by an authorized party, such as the subscriber, before releasing user information. An IdP accepting dynamically registered RPs MAY limit the types of attributes and other information made available to such RPs. An RP capable of dynamically registering MAY limit which IdPs it is willing to accept identity information from.

Frequently, parties in a dynamic registration model do not know each other ahead of time. Where possible, this SHOULD be augmented by *software statements*, which allow federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes describing the RP software, cryptographically signed by an authority (either the IdP itself, a federation authority as in [section 4.1.3](#authorities), or another trusted party). This cryptographically verifiable statement allows the connection to be established or elevated between the federating parties without relying solely on self-asserted attributes. (See [[RFC 7591]](#RFC7591) section 2.3 for more information on one protocol's implementation of software statements.)

#### <a name="authorities"></a> 4.1.3. Federation Authorities

Some federated parties defer to an authority known as a *federation authority* to assist in making federation decisions and to establish the working relationship between parties. In this model, the federation authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards.

Federation authorities SHALL establish parameters regarding expected and acceptable identity assurance level (IAL) and authentication assurance level (AAL) in connection with the federated relationships they enable. Federation authorities SHALL individually vet each participant in the federation to determine that they adhere to their expected security, identity, and privacy standards. Vetting of IdPs and RPs SHALL establish, as a minimum, that:

* Assertions generated by IdPs adhere to the requirements in [Section 5](#sec5).
* RPs will adhere to IdP requirements for the handling of subscriber attribute data, such as retention, aggregation, and disclosure to third parties.
* RP and IdP systems use approved profiles of federation protocols.

Federation authorities MAY assist the technical connection and configuration process between members, such as by publishing configuration data for IdPs or issuing software statements for RPs.

Most federations managed through authorities have a simple membership model: either parties are in the federation or they are not. However, more sophisticated federations MAY have multiple tiers of membership which can be used by federated parties to tell whether other parties in the federation have been more thoroughly vetted. IdPs MAY decide that certain subscriber information is only releasable to RPs in higher tiers, and RPs MAY decide to accept certain information only from IdPs in higher tiers. The nature and structure of such a multi-tiered system is outside the scope of this document.

#### 4.1.4. Proxied Federation

In a proxied federation, communication between the IdP and the RP is intermediated in a way that prevents direct communication between the two parties. There are multiple methods to achieve this effect; common configurations include:
* A third party that acts as a federation proxy (or *broker*)
* A network of nodes that distributes the communications

Where proxies are used, they function as an IdP on one side and an RP on the other side. Therefore, all normative requirements that apply to IdPs and RPs SHALL apply to proxies in their respective roles.

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 2: Federation Proxy](sp800-63c/media/broker.png)

**Figure 4-2: Federation Proxy**
</div>

A proxied federation model can provide several benefits. Federation proxies can simplify technical integration between the RP and IdP by providing a common interface for integration. Additionally, to the extent a proxy effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that want to guard their subscriber lists from each other. Proxies can also mitigate some of the privacy risks of federation described in Section 4.2 below. 

See [section 4.2.1](#blinding) for further information on blinding techniques, their uses, and limitations.
 
#### 4.1.5. <a name="runtime-decisions"></a>Runtime Decisions

The fact that parties have federated SHALL NOT be interpreted as permission to pass information. Federated parties MAY establish whitelists of other federated parties who may authenticate subscribers or pass information about them without runtime authorization from the subscriber. Federated parties MAY also establish blacklists of other federated parties who may not be allowed to pass information about subscribers at all. Every party that is not on a whitelist or a blacklist SHALL be placed by default in a gray area where runtime authorization decisions will be made by an authorized party, often the subscriber.

### 4.2. Privacy Requirements

Federation involves the transfer of personal attributes from a third party, the IdP, that is not otherwise involved in a transaction. Federation also potentially gives the IdP broad visibility into subscriber activities. Accordingly, there are specific privacy requirements associated with federation. 

Communication between the RP and the IdP could reveal to the IdP where the subscriber is conducting a transaction. Communication with multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed without federation. This aggregation could enable new opportunities for subscriber tracking and use of profile information that do not always align with the privacy interests of subscribers. 

The IdP SHALL NOT disclose information on subscriber activities at an RP to any party, nor use the information for any purpose other than federated authentication, to comply with law or legal process, or in the case of a specific user request for the information. The IdP SHOULD employ technical measures, such as the use of pairwise pseudonymous identifiers described in Section 5.2.5, to provide unlinkability and discourage subscriber activity tracking and profiling.

An IdP MAY disclose information on subscriber activities to other RPs within the federation for security purposes such as communication of compromised subscriber accounts.

The following requirements apply specifically to agencies:

1. The agency SHALL consult with their Senior Agency Official for Privacy to conduct and analysis to determine whether the agency that is acting as either an IdP or an RP in an identity federation triggers the requirements of the Privacy Act.

2. The agency SHALL publish or identify coverage by a System of Records Notice as applicable.

3. The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the agency that is acting as either an IdP or an RP in an identity federation triggers the requirements of the E-Government Act.

4. The agency SHALL publish or identify coverage by a Privacy Impact Assessment as applicable.

#### 4.2.1. <a name="blinding"></a>Blinding in Proxied Federation

While some proxy structures (typically those that exist primarily to simplify integration) MAY offer no additional subscriber privacy protection, others offer varying levels of privacy to the subscriber through a range of blinding technologies. Privacy policies may dictate appropriate use by the IdP, RP, and the federation proxy, but technical means such as blinding can increase effectiveness of these policies by making the data more difficult to obtain. It should also be noted that as the level of blinding increases, so does the technical and operational implementation complexity.

Note that even with the use of blinding technologies, it MAY still be possible for a blinded party to infer protected subscriber information through released attribute data or metadata such as analysis of timestamps, attribute bundle sizes, or attribute signer information. 

The following table illustrates a spectrum of blinding implementations used in proxied federation. This table is intended to be illustrative, and is neither comprehensive nor technology-specific.

<div class="text-center" markdown="1">

**Table 4-1: Federation Proxies**

</div>


|Proxy Type|RP knows IdP|IdP knows RP|Proxy can track subscriptions between RP and IdP|Proxy can see attributes of Subscriber|
|---|---|---|---|---|
|Non-blinding Proxy with Attributes|Yes|Yes|Yes|Yes|
|Non-blinding Proxy|Yes|Yes|Yes|No|
|Double Blind Proxy with Attributes|No|No|Yes|Yes|
|Double Blind Proxy|No|No|Yes|No|
|Triple Blind Proxy|No|No|No|No|

#### 4.2.2. Attribute Exposure and Masking

To mitigate the risk of unauthorized exposure of sensitive information (e.g., shoulder surfing), the IdP SHALL, by default, mask sensitive information displayed to the subscriber.  The IdP SHALL provide mechanisms for the subscriber to temporarily unmask such information in order for the subscriber to view full values.

The subscriber SHALL be able to view the attribute values to be transmitted, although masking mechanisms SHALL be employed, as necessary, to mitigate the risk of unauthorized exposure of sensitive information (e.g. shoulder surfing). The IdP SHALL provide effective mechanisms for redress of applicant complaints or problems (e.g., subscriber identifies an inaccurate attribute value). For more details on masking and redress, please see [Section 10. Usability Considerations](#sec10).  

The subscriber SHALL receive explicit notice and be able to provide positive confirmation before any attributes about the subscriber are transmitted to any RP. At a minimum, the notice SHOULD be provided by the party in the position to provide the most effective notice and obtain confirmation. See section 9.2 for considerations on determining which party should provide the notice and obtain confirmation. If the protocol in use allows for optional attributes, the subscriber SHALL be given the option to decide whether to transmit those attributes to the RP. A IdP MAY employ mechanisms to remember and re-transmit the exact attribute bundle to the same RP. 


