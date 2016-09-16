<a name="sec4"></a>

## 4. Federation
Federation is a process that allows for the conveyance of identity and authentication information across a set of networked systems. In a federation scenario, the verifier or CSP is known as the *identity provider*, or IdP. In this document, the *relying party*, or RP, is the party that receives the federated identity.

![Figure 1: Federation](sp800-63c/media/federation.png)

**Figure 1: Federation**

In a federation protocol, a triangle is formed between the subscriber, the IdP, and the RP (Figure 1). Depending on the specifics of the protocol, different information passes across each leg of the triangle at different times. The subscriber communicates with both the IdP and the RP, usually through a web browser. The RP and the IdP communicate with each other, though this communication can happen over the front channel (through redirects involving the subscriber), over the back channel (through a direct connection), or via a packaged information bundle (such as a cryptographically protected and self-contained assertion).

The subscriber authenticates to the IdP using some form of primary credential, and then that authentication event is asserted to the RP across the network. The IdP can also make attribute statements about the subscriber as part of this process. These attributes and authentication event information are usually carried to the RP through the use of an assertion (see section 5.).

The RP communication with the IdP reveals to the IdP where the subscriber is conducting a transaction. Communications from multiple RPs allow the IdP to build a profile of subscriber transactions that would not have existed absent federation. This aggregation could enable new capabilities for subscriber tracking and use of profile information that do not align with the privacy interests of the subscribers. 

The IdP SHALL NOT disclose information on subscriber activities at an RP to any party, nor use the information for any purpose other than federated authentication, to comply with law or legal process, or in the case of a specific user request for the information. The IdP SHOULD employ technical measures to provide unlinkability and prevent subscriber activity tracking and profiling.

A IdP MAY disclose information on subscriber activities to other RPs within the federation for security purposes such as communication of compromised subscriber accounts.

The following requirements apply specifically to agencies:

a) The agency SHALL consult with their Senior Agency Official for Privacy to conduct and analysis to determine whether the agency acting as either an IdP, or an RP in an identity federation triggers the requirements of the Privacy Act.

b) The agency SHALL publish, or identify coverage by a System of Records Notice as applicable.

c) The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the agency acting as either an IdP, or an RP in an identity federation triggers the requirements of the E-Government Act.

d) The agency SHALL publish or identify coverage by a Privacy Impact Assessment, as applicable.

### 4.1. Federation Models

This section provides an overview of a few common models of identity federation currently in use. In these models, trust is established between members of the federation in several different ways. Some models mandate that federated parties have a high level of trust. Other models allow for parties with a diversity of trust relationships.

#### 4.1.1 Central Authority

Some federated parties trust a central authority to make trust decisions for them and communicate metadata between parties. In this model, the central authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards.

Most federations using the central authority model have a single level of trust - either parties are in the federation or they are not. However, more sophisticated federations have multiple tiers of trust which can be used by federated parties to tell whether other parties in the federation have been more thoroughly vetted or have some common purpose that justifies a higher level of trust. This higher level of trust makes some parties in the federation more likely to automatically release information about their users to the parties in the higher tiers.

#### 4.1.2 Manual Registration

In the manual registration model of federation, system administrators communicate metadata and test system interoperability before transactions take place between users over the wire. Metadata for each party who wishes to participate is manually input into a registry of federated parties. Each party maintains their own registry of other parties whom they have deemed trustworthy.

Manual registration can take place on a case by case basis without any authority or federation operator in place. In this case, an existing pairwise trust relationship is generally already in place between the IdP and the RP. 

Manual registration can work in concert with a central authority model. In this case, a registry is pre-populated with parties trusted by the central authority, and more parties are added manually on an as-needed basis.

#### <a name="dynamic-registration"></a> 4.1.3 Dynamic Registration

In the dynamic registration model of federation, systems have a well-known location where other systems can find their metadata. They also have predictable API endpoints where new systems can register themselves without human involvement. Systems that make use of dynamic registration SHOULD require verifiable human interaction, such as the approval of the identity federation transaction by the authenticated subscriber at the IdP. 

Frequently, parties in a dynamic registration model have no way to trust each other ahead of time, so little information is exchanged by default. This problem is somewhat mitigated by a technology called software statements, which allow federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes describing the RP software, cryptographically signed by certifying bodies. Because both parties trust the certifying body, that trust can be extended to the other party in the dynamic registration partnership.  This allows trust to be established or elevated between the federating parties. See [[RFC 7591]](#RFC7591) section 2.3 for more information.

Many federated parties establish whitelists of other federated parties who may dynamically register with some predetermined level of trust. They also establish blacklists of federated parties who may be allowed dynamically register with a low level of trust, or who may not be allowed to dynamically register at all. Everything that is not on a whitelist or a blacklist can be considered to be in a gray area or on a "graylist." Graylisted parties generally start out with a low level of trust until they can be reviewed by a human who can determine an appropriate level of trust. 

#### 4.1.4 Proxied Federation

In a proxied federation model, the communication between the IdP and the RP is proxied in a way that prevents direct communication between the two parties. There may be multiple methods of achieving this effect, but common configurations include a third party that acts as a federation proxy (or "broker") or a network of "nodes" that distribute the communications. 

Effectively, the parties still function in some degree as a federation IdP on one side and a federation RP on the other side. Notably, a federation proxy acts as an IdP to all federated RPs and as an RP to all federated IdPs. Therefore, all normative requirements that apply to IdPs and RPs SHALL apply to the parties of such a system in their respective roles.

![Figure 2: Federation Proxy](sp800-63c/media/broker.png)

**Figure 2: Federation Proxy**

A proxied federation model can provide various benefits. For example, federation proxies can enable simplified technical integrations between the RP and IdP by eliminating the need for multiple point to point integrations, which can be onerous for protocols which do not support [dynamic registration](#dynamic-registration). Additionally, to the extent a proxied federation model effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that may not wish to reveal their subscriber lists to each other, as well as mitigate some of the privacy risks of point to point federation described above. 

While some proxied deployments offer no additional privacy protection (such as those that exist as integration points), others can offer varying levels of privacy to the subscriber through a range of blinding technologies. NOTE: even with the use of blinding technologies, it may still be possible for a blinded party to deduce subscriber behavior patterns through analysis of timestamps, cookies, attributes, or attribute bundle sizes. Privacy policies may dictate appropriate use by the IdP, RP, and the federation proxy, but blinding technology can increase effectiveness of these policies by making the data more difficult to access. It should also be noted that as the level of blinding increases, so does the technical and operational implementation complexity.

The following list illustrates a spectrum of blinding implementations:

1.	The federation proxy does not blind the RP and IdP from one another. The federation proxy is able to monitor and track all subscriber relationships between the RPs and IdPs, and has visibility into any attributes it is transmitting in the assertion.
2.	The federation proxy does not blind the RP and IdP from one another. The federation proxy is able to monitor and track all subscriber relationships between the RPs and IdPs, but has no visibility into any attributes it is transmitting in the assertion.
3.	The federation proxy blinds the RP and IdP from each other. The federation proxy is able to monitor and track all subscriber relationships between the RPs and IdPs, and has visibility into any attributes it is transmitting in the assertion.
4.	The federation proxy blinds the RP and IdP from each other. The federation proxy is able to monitor and track all subscriber relationships between the RPs and IdPs, but has no visibility into any attributes it is transmitting in the assertion.
5. The federation proxy blinds the RP, IdP, and itself. The federation proxy cannot monitor or track any subscriber relationships, and has no visibility into any attributes it is transmitting in the assertion. 




 




