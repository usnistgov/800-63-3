<div class="breaker"></div>
<a name="sec10"></a>

## 10. Usability Considerations

*This section is informative.*

[ISO/IEC 9241-11](#ISO9241-11) defines usability as the "extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as key elements necessary for achieving effectiveness, efficiency and satisfaction. A holistic approach considering these key elements is necessary to achieve usability. This section addresses the usability considerations that have been identified with federated identity systems.   

One of the major potential usability benefits of federated identity systems is to address the problem of individuals needing to maintain too many authenticators, such as multiple user names and passwords. While other authentication methods have been extensively researched and have well-established usability guidelines, federated identity is more nascent and therefore lacks deep and conclusive research findings. It is very much an active research topic in the usability domain. As the field matures, usability guidelines for federated identity systems will have stronger supporting data. 


A well-planned and executed user experience is critical to the success of any authentication method. The overall user experience with federated identity systems should be as smooth and easy as possible, without undermining a user's ability to understand how their data are being treated and by whom. Federated identity systems should:  

-  Minimize user burden (e.g., frustration, learning curve).
-  Minimize the use of unfamiliar technical jargon and details (e.g., users do not need to know the terms CSP and RP).
-  Provide clear, honest, and meaningful communications to users (e.g., notices of information flow should be explicit and easy to understand).
-  Use graphics and illustrations to help users form complete and accurate mental models of federated identity systems.

To ensure success of federated identity systems from users' perspectives, it is imperative that iterative and continuous usability evaluations are performed with representative users and realistic tasks in an appropriate context.

##### ASSUMPTIONS 

In this section, the term "users" means "subscribers" or "claimants." This section describes usability themes from users' perspectives, as usability can only be considered from the users' perspective.

Accessibility and usability differ significantly; accessibility is out of scope for this section. The organizations and agencies participating in the federation can address accessibility in its implementation plans and can consult other federal guidance for best practices. 

### 10.1. Considerations

The following sections provide recommended practices to enhance the user experience of federated identity systems.  The primary goal of these recommendations is to alleviate the potential for friction and user drop-off that could be caused by the possible confusion created when an RP needs to redirect control from their site to an IdP.  A good user experience may also result in increased demand of federation by users, triggering increased adoption by RPs. 

This section is organized by the functional elements a user may encounter when interacting with a federated identity system.  These elements are:  

1.	Authentication requests - the end-to-end process by which an RP requests that a user select and authenticate with an external IdP;
2.	Choosing from multiple accounts - the scenario in which a user or group of users has multiple federated accounts from which to select;
3.	Attribute Sharing - the specific user experience recommendations when the RP is requesting attributes;
4.	Lifecycle Management - the functions available to the users to manage their account, consent, and relationships at the IdP.

#### 10.1.1. Authentication Requests

Federated identity systems typically redirect the user from the RP to the IdP, and back again. This could be jarring to users for various reasons.  They may think the redirects are the result of a malicious entity.  Or they may be concerned about leaving one domain for another, especially if the root domain changes (e.g., .gov to .com).  In addition, RPs may be concerned with branding and any friction that may keep a user from executing their intended transaction.  The following list considers tactics that can be employed to resolve negative user experience; in addition, these techniques could facilitate RP acceptance of temporarily turning control of the user experience to the IdP as the authentication request proceeds. Possible considerations include:  

1.	Users will benefit from a simple understanding of how federated identity works to make informed trust decisions. As with all user-facing text, clearly explaining to users in plain language that is easy to understand, and avoiding technical jargon - as specified in [800-63A, Section 9](sp800-63a.html#sec9) - will positively impact their decision-making process to proceed within a federated environment.
2.	Leverage standards, specifications, and APIs that embed user experience considerations in, rather than those that shift user experience out of the technical integration between IdP and RP. For example, OpenID Connect requires user consent to release attributes and has accommodations for joint branding of the login and consent screen.
3.	The IdP user interface (UI) should be as simple as possible, and leverage modern techniques to seamlessly appear to be part of the SP application.
4. If the user does not have an account with any available IdPs, it could help to walk a user through the available options and help determine the most appropriate CSP for their needs. 
4.	Display the URL of the IdP so that the user has visual assurance that he or she is not being phished by a malicious site.
5.	Display RP branding within the IdP UI.  It is appealing to the users to have visual confirmation (via branding) to know they are logging in with their IdP (per #4 above) for access to the destination RP.  For example, a dialog box with the SP logo could read "You are authenticating to gain access to SP.gov."

#### 10.1.2. Multiple Accounts

It is possible that a user may maintain multiple accounts at a single IdP, or in some cases, have a shared household computer where multiple people have accounts at the same IdP. The IdP is encouraged to consider approaches such as [Account Chooser](http://openid.net/wg/ac/). Account chooser allows users to select from a list of accounts they have accessed in the recent past, rather than start the federation process by selecting their IdP from a list of potential IdPs.  Techniques such as this limit the burden on a user to select the correct account, and IdP, to use in each transaction.  This avoids unnecessary click-throughs for the user to ultimately select the IdP he or she wants as well as the account he or she wants to use for a given RP transaction.

#### 10.1.3. Attribute Sharing

In some cases, an RP will request user attributes from the IdP to provide access to certain pages or transactions.  Some considerations for attribute release include:  

1.  To build trust, give users control of the disclosure of their information and ask for their explicit consent through the appropriate use of notifications (see [Section 9.2, Notice and Consent](#notice)).
2. Collect information for constrained usage only, and minimize information disclosure (see [Section 9.3, Data Minimization](#minimization). Superfluous information collection and disclosure or user tracking may erode user trust.  
3. Ask for user consent to which attributes and attribute values are released to ensure their veracity. Partial or complete masking of attribute values is required. It is recommended that the unmasking capability uses UI elements that encourage only temporary unmasking (for example, text that is available via a mouse hover or a context sensitive popup).  Unmasking on the same page as the masked data is discouraged (see [Section 6](#sec6)).
4. Enable users to consent to a partial list of attributes, rather than an all or nothing approach.  Similarly, RPs are encouraged to allow some degree of online access even if the user does not consent to share all information.
5. Base attribute sharing on the transaction being requested, not on all possible transactions a user may or may not access at the RP.
6. Do not display system generated attributes such as a pairwise pseudonymous identifier (not to be confused with system derived attribute claims, such as 'older than' derived from 'date of birth'), to users, even if it is shared with the RP as part of the authentication response.  If these types of attributes are visible to the user, display them in a portion of the UI that is separated from actual user attributes such as name or email. Additionally, provide a user-friendly description of the attributes to avoid confusion. Toggle this information on/off, via a UI control such as a check box, with the default as 'off,' so the user has to explicitly select whether to review this information (see SP 800-53C [Section 6](#sec6) and [Section 9](#sec9)).
7. Use standards, such as OAuth or OpenID Connect, that build attribute consent into the protocol - so they're not a feature external to the federated transaction.
8. Provide easy to find redress methods (see [Section 6](#sec6) for more details) such that a user can recover from invalid attribute information claimed by the IdP.
9. Limit the number of times a user will need to consent to the release of attributes. Upon first access it is normal to request consent; on subsequent access attempts to the same RP, consent is not needed, provided the IdP offers appropriate lifecycle management functions as discussed in [Section 10.1.4](#lifecycle).

#### <a name="lifecycle"></a> 10.1.4. Lifecycle Management

Users should be able to manage the relationship between their identity at an IdP and its linkage to an RP. An IdP may provide functionality to manage this relationship  as a simple and easy to use account setting - rather than something that is difficult to find or access, or requires phone or in-person interaction. An IdP should consider the following:  

1.	Allows users to manage each IdP to RP connection, to include complete separation as well as the removal of RP access to one or more attributes.
2. Allow users to delete their identities completely, removing all information about the user, to include transaction history.
