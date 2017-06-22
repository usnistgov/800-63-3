<a name="privacy"></a>

## <a name="privacy-section-header"></a> 9 Privacy Considerations

*This section is informative.*

### 9.1 Minimizing Tracking and Profiling

Federation offers numerous benefits to RPs and subscribers, but requires subscribers to have trust in the IdP. Accordingly, to build subscriber trust in a federated model, it is important that uses of subscriber data are appropriately limited and scoped to the purpose for which it was originally collected. Consult your SAOP if there are questions about whether proposed uses fall within the scope of these permitted uses. [Sections 5](#federation), [5.1.4](#proxied), and [6.3](#ppi) cover a number of technical requirements, the objective of which is to minimize privacy risks arising from increased capabilities to track and profile subscribers. For example, a subscriber using the same IdP to authenticate to multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed absent federation. The availability of such data makes it vulnerable to uses that may not be anticipated or desired by the subscriber and may inhibit subscriber adoption of federated services.

[Section 5.2](#privacy-reqs) also encourages the use of technical measures to provide unlinkability and prevent subscriber activity tracking and profiling. While IdP policies and procedures are important in ensuring adherence to appropriate use limitation and purpose specification principles, technical measures such as outlined in [Section 5.1.4](#proxied) for proxied federation and [Section 6.3](#ppi) for pairwise pseudonymous identifiers, can increase the effectiveness of these policies by making it more difficult to track or profile subscribers beyond operational requirements.

### <a name="notice"></a> 9.2 Notice and Consent

To build subscriber trust in federation, subscribers need to be able to develop reliable assumptions about how their information is being processed. For instance, it can be helpful for subscribers to understand what information will be transmitted, which attributes for the transaction are required versus optional, and to have the ability to decide whether to transmit optional attributes to the RP. Accordingly, [Section 7](#presentation) requires that positive confirmation be obtained from the subscriber before any attributes about the subscriber are transmitted to any RP. In determining when a set of RPs should share a common pairwise pseudonymous identifier as in [Section 6.3.2](#ppi-gen), the IdP considers the subscriber's understanding of such a grouping of RPs and the role of notice in assisting such understanding. An effective notice will take into account user experience design standards and research, as well as an assessment of privacy risks that may arise from the information processing. There are various factors to be considered, including the reliability of the assumptions subscribers may have about the processing and the role of different entities involved in federation. However, a link to a complex, legalistic privacy policy or general terms and conditions that a substantial number of subscribers do not read or understand is never an effective notice.

[Section 7](#presentation) does not specify which party should provide the notice. In some cases, a party in a federation may not have a direct connection to the subscriber in order to provide notice and obtain consent. Although multiple parties may elect to provide notice, it is permissible for parties to determine in advance, either contractually or through trust framework policies, which party will provide the notice and obtain confirmation, as long as the determination is being based upon factors that center on enabling the subscriber to pay attention to the notice and make an informed choice.

If an IdP is using a whitelist of RPs as described in [Section 4.2](#runtime-decisions), any RPs on that list are not presented to the subscriber during an authentication transaction. Since the IdP does not provide notice to the subscriber at runtime, the IdP makes its list of whitelisted RPs available to the subscriber so that the subscriber can see which RPs on the whitelist have access to which of the subscriber's attributes in an authentication transaction. Since IdPs can not share a subscriber's authentication information or attributes with a whitelisted RP outside of an authentication transaction involving the subscriber (see [Section 5.2](#privacy-reqs)), the existence of an RP on a list of IdPs does not indicate that the subscriber's information will be shared. However, if the subscriber logs into any of the whitelisted RPs using the IdP, the attributes indicated will be shared as part of the authentication transaction.

If a subscriber's runtime decisions were stored by the IdP to facilitate future transactions, the IdP also needs to allow the subscriber to view and revoke any RPs that were previously approved during a runtime decision. This list includes information on which attributes were approved.

### <a name="minimization"></a> 9.3 Data Minimization

Federation enables the data exposed to an RP to be minimized &mdash; resultantly, the subscriber's privacy is enhanced. Although an IdP may collect additional attributes beyond what the RP requires for its use case, only those attributes that were explicitly requested by the RP are to be transmitted by the IdP. In some instances, an RP does not require a full value of an attribute. For example, an RP may need to know whether the subscriber is over 13 years old, but has no need for the full date of birth. To minimize collection of potentially sensitive PII, the RP may request an attribute reference (e.g., Question: Is the subscriber over 13 years old? Response: Y/N or Pass/Fail). This minimizes the RP's collection of potentially sensitive and unnecessary PII. Accordingly, [Section 7.3](#protecting-information) requires the RP to, where feasible, request attribute references rather than full attribute values. To support this RP requirement IdPs are, in turn, required to support attribute references.

### <a name="agency-privacy"></a>9.4 Agency-Specific Privacy Compliance 

[Section 5.2](#privacy-reqs) identifies agency requirements to consult their SAOP to determine privacy compliance requirements. It is critical to involve your agency's SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and advise the agency on compliance obligations such as whether the federation triggers the Privacy Act of 1974 or the E-Government Act of 2002 requirement to conduct a PIA. For example, if the Agency is serving as an IdP in a federation, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records since credentials would be maintained at the IdP on behalf of any RP it federates with. If, however, the agency is an RP and using a third-party IdP, digital authentication may not trigger the requirements of the Privacy Act, depending on what data passed from the RP is maintained by the agency as the RP (in such instances the agency may have a broader programmatic SORN that covers such data).

The SAOP can similarly assist the agency in determining whether a PIA is required. These considerations should not be read as a requirement to develop a Privacy Act SORN or PIA for use of a federated credential alone. In many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital authentication process or includes the digital authentication process as part of a larger programmatic PIA that discusses the program or benefit the agency is establishing online access.

Due to the many components of digital authentication, it is important for the SAOP to have an awareness and understanding of each individual component. For example, other privacy artifacts may be applicable to an agency offering or using federated IdP or RP services, such as Data Use Agreements, Computer Matching Agreements, etc. The SAOP can assist the agency in determining what additional requirements apply. Moreover, a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.


### 9.5 <a name="blinding"></a>Blinding in Proxied Federation

While some proxy structures — typically those that exist primarily to simplify integration — may not offer additional subscriber privacy protection, others offer varying levels of privacy to the subscriber through a range of blinding technologies. Privacy policies may dictate appropriate use of the subscriber attributes and authentication transaction data (e.g., identities of the ultimate IdP and RP) by the IdP, RP, and the federation proxy. Technical means such as blinding can increase effectiveness of these policies by making the data more difficult to obtain. As the level of blinding increases, the technical and operational implementation complexity may increase. Proxies need to map transactions to the appropriate parties on either side as well as manage the keys for all parties in the transaction.

Even with the use of blinding technologies, a blinded party may still infer protected subscriber information through released attribute data or metadata, such as by analysis of timestamps, attribute bundle sizes, or attribute signer information. The IdP could consider additional privacy-enhancing approaches to reduce the risk of revealing identifying information of the entities participating in the federation.

The following table illustrates a spectrum of blinding implementations used in proxied federation. This table is intended to be illustrative, and is neither comprehensive nor technology-specific.

<div class="text-center" markdown="1">

**Table 9-1 Federation Proxies**

</div>


|Proxy Type|RP knows IdP|IdP knows RP|Proxy can track subscriptions between RP and IdP|Proxy can see attributes of Subscriber|
|---|:---:|:---:|:---:|:---:|
|Non-Blinding Proxy with Attributes|Yes|Yes|Yes|Yes|
|Non-Blinding Proxy|Yes|Yes|Yes|N/A|
|Double Blind Proxy with Attributes|No|No|Yes|Yes|
|Double Blind Proxy|No|No|Yes|N/A|
|Triple Blind Proxy with or without Attributes|No|No|No|No|

