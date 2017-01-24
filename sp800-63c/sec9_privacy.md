<div class="breaker"></div>
<a name="sec9"></a>

## <a name="privacy-section-header"></a> 9. Privacy Considerations

These privacy considerations are non-normative.

### 9.1. Minimizing Tracking and Profiling

Federation offers numerous benefits to RPs and subscribers, but requires subscribers to have trust in the IdP. Accordingly, to build subscriber trust in a federated model, it is important that uses of subscriber data are appropriately limited and scoped to the purpose for which it was originally collected. Consult your Senior Agency Official for Privacy if there are questions about whether proposed agency uses fall within the scope of these uses. Sections [4](#sec4), [4.1.4](#proxied), and [5.2.5](#ppi) cover a number of technical requirements the objective for which is to minimize privacy risks arising from increased capabilities to track and profile subscribers. For example, a subscriber using the same IdP to authenticate to multiple RPs allows the IdP to build a profile of subscriber transactions that would not have existed absent federation. The availability of such data makes it vulnerable to uses that may not be anticipated or desired by the subscriber and may inhibit subscriber adoption of federated services.

[Section 4.2](#privacy-reqs) also encourages the use of technical measures to provide unlinkability and prevent subscriber activity tracking and profiling. While IdP policies and procedures are important in ensuring adherence to appropriate use limitation and purpose specification principles, technical measures such as outlined in [Section 4.1.4](#proxied) for proxied federation and [Section 5.2.5](#ppi) for pairwise pseudonymous identifiers, can increase the effectiveness of these policies by making it more difficult to track or profile subscribers beyond operational requirements.


### 9.2. Notice and Consent

To build subscriber trust in federation, transparency must be provided to the subscriber to understand what information will be transmitted, what is required versus optional, and the ability to decide whether to transmit optional attributes to the RP.  Accordingly, [Section 6](#sec6) requires that positive confirmation be obtained from the subscriber before any attributes about the subscriber are transmitted to any RP.  An effective notice will take into account user experience design standards and research, as well as an assessment of privacy risks that may arise from the collection. There are many factors that should be considered, including the reliability of the assumptions subscribers may have about the collection, whether other information is being collected and appended to the information collected from the subscriber. However, an effective notice is never only a link that leads to a complex, legalistic privacy policy or general terms and conditions that a substantial number of subscribers do not read or understand. 

[Section 6](#sec6) does not specify which party should provide the notice.  In some cases, a party in a federation may not have a direct connection to the subscriber to provide notice and obtain consent. Although multiple parties may elect to provide notice, it is permissible for parties to determine in advance either contractually or through trust framework policies which party will provide the notice and obtain confirmation, as long as the determination is being based upon factors that center on enabling the subscriber to pay attention to the notice and make an informed choice.



### 9.3. Data Minimization

Although an IdP may collect additional attributes beyond what the RP requires for its use case, only those attributes that were explicitly requested by the RP are to be transmitted by the IdP. In some instances, an RP does not require a full value of an attribute; for example, an RP may need to know whether the subscriber is over 13 years old, but has no need for the full date of birth. To minimize the collection of potentially sensitive PII, the RP may request an attribute claim (e.g., Question: Is the subscriber over 13 years old? Response: Y/N or Pass/Fail).  This minimizes the RPs collection of potentially sensitive and unnecessary PII.  Accordingly, Section 6.4 requires the RP to, where feasible, request attribute claims rather than full attribute values.  To support this RP requirement, IdPs are in turn, required to support attribute claims.


### 9.4. Agency Specific Privacy Compliance 

[Section 4.2](#privacy-reqs) identifies agency requirements to consult their SAOP to determine privacy compliance requirements. It is critical to involve your agency's SAOP in the earliest stages of digital authentication system development to assess and mitigate privacy risks and as advise the agency on compliance obligations such as whether the federation triggers the Privacy Act of 1974 or the E-Government Act of 2002 requirement to conduct a Privacy Impact Assessment.  For example, if the Agency is serving as a CSP in a federation, it is likely that the Privacy Act requirements will be triggered and require coverage by either a new or existing Privacy Act system of records since credentials would be maintained on behalf of the agency RP.  If, however, the agency is an RP and using a 3rd party IdP, digital authentication may not trigger the requirements of the Privacy Act, depending on what data passed from the RP is maintained by the agency as the RP (in such instances the agency may have a broader programmatic SORN that covers such data).

The SAOP can similarly assist the agency in determining whether a PIA is required. These considerations should not be read as a requirement to develop a Privacy Act System of Records Notice or PIA for use of a federated credential alone; in many cases it will make the most sense to draft a PIA and SORN that encompasses the entire digital authentication process or include the digital authentication process as part of a larger programmatic PIA that discusses the program or benefit the agency is establishing online access.

Due to the many components of digital authentication, it is important for the SAOP to have an awareness and understanding of each individual component so as to advise appropriately on what compliance requirements apply. Moreover a thorough understanding of the individual components of digital authentication will enable the SAOP to thoroughly assess and mitigate privacy risks either through compliance processes or by other means.


### 9.5. <a name="blinding"></a>Blinding in Proxied Federation

While some proxy structures (typically those that exist primarily to simplify integration) may not offer additional subscriber privacy protection, others offer varying levels of privacy to the subscriber through a range of blinding technologies. Privacy policies may dictate appropriate use by the IdP, RP, and the federation proxy, but technical means such as blinding can increase effectiveness of these policies by making the data more difficult to obtain. As the level of blinding increases, the technical and operational implementation complexity may as well.

Even with the use of blinding technologies, a blinded party may still infer protected subscriber information through released attribute data or metadata such as analysis of timestamps, attribute bundle sizes, or attribute signer information. The IdP could consider additional privacy-enhancing approaches to reduce the risk of revealing identifying information of the entities participating in the federation.


The following table illustrates a spectrum of blinding implementations used in proxied federation. This table is intended to be illustrative, and is neither comprehensive nor technology-specific.

<div class="text-center" markdown="1">

**Table 9-1: Federation Proxies**

</div>


|Proxy Type|RP knows IdP|IdP knows RP|Proxy can track subscriptions between RP and IdP|Proxy can see attributes of Subscriber|
|---|:---:|:---:|:---:|:---:|
|Non-blinding Proxy with Attributes|Yes|Yes|Yes|Yes|
|Non-blinding Proxy|Yes|Yes|Yes|N/A|
|Double Blind Proxy with Attributes|No|No|Yes|Yes|
|Double Blind Proxy|No|No|Yes|N/A|
|Triple Blind Proxy with or without Attributes|No|No|No|No|

