<a name="sec6"></a>

<div class="breaker"></div>

## 6 <a name="CYOA"></a>Selecting Assurance Levels

_This section is normative._

The risk assessment results are the primary factor in selecting the most appropriate levels. This section details how to apply the results of the risk assessment with additional factors unrelated to risk to determine the most advantageous xAL selection.

First, compare the risk assessment impact profile to the impact profiles associated with each assurance level, as shown in [Table 6-1](#63Sec6-Table6-1) below. To determine the required assurance level, find the lowest level whose impact profile meets or exceeds the potential impact for every category analyzed in the risk assessment.

<a name="63Sec6-Table6-1"></a>
<div class="text-center" markdown="1">
**Table 6-1 Maximum Potential Impacts for Each Assurance Level**
</div>

<table>

 <tr>

 <td></td>
    <td style="text-align: center" colspan="3"><strong>Assurance Level</strong></td>
  </tr>
  <tr>

  <th>Impact Categories</th>
    <th>1</th>
    <th>2</th>
    <th>3</th>
  </tr>
  <tr>
    <td>Inconvenience, distress or damage to standing or reputation</td>
    <td>Low</td>
    <td>Mod</td>
    <td>High</td>
  </tr>
  <tr>
    <td>Financial loss or agency liability</td>
    <td>Low</td>
    <td>Mod</td>
    <td>High</td>
  </tr>
   <tr>
    <td>Harm to agency programs or public interests</td>
    <td>N/A</td>
    <td>Low/Mod</td>
    <td>High</td>
  <tr>
  <tr>
    <td>Unauthorized release of sensitive information</td>
    <td>N/A</td>
    <td>Low/Mod</td>
    <td>High</td>
  </tr> 
    <td>Personal Safety</td>
    <td>N/A</td>
    <td>Low</td>
    <td>Mod/High</td>
  </tr>
  
  </tr>
  <tr>
    <td>Civil or criminal violations</td>
    <td>N/A</td>
    <td>Low/Mod</td>
    <td>High</td>
  </tr>
 
</table>

In analyzing risks, the agency SHALL consider all of the expected direct and indirect results of an authentication failure, including the possibility that there will be more than one failure, or harms to more than one person or organization. The definitions of potential impacts contain some relative terms, like "serious" or "minor," whose meaning will depend on context. The agency SHOULD consider the context and the nature of the persons or entities affected to decide the relative significance of these harms. Over time, the meaning of these terms will become more definite as agencies gain practical experience with these issues. The analysis of harms to agency programs or other public interests depends strongly on the context; the agency SHOULD consider these issues with care.

It is possible that the assurance levels may differ across IAL, AAL, and FAL. For example, suppose an agency establishes a "health tracker" application in which users submit personal information in the form of personal health information (PHI). In line with the terms of [EO 13681](#EO13681) requiring "that all agencies making personal data accessible to citizens through digital applications require the use of multiple factors of authentication," the agency is required to implement MFA at AAL2 or AAL3.

EO 13681 also requires agencies employ "an effective identity proofing process, as appropriate" when personal information is released. This does not mean that proofing at IAL2 or IAL3 (to match the required AAL) is necessary. In the above example, there may be no need for the agency system to know the actual identity of the user. In this case, an "effective proofing process" would be to not proof at all, therefore the agency would select IAL1. This allows the user of the health tracker system to be pseudonymous.

Despite the user being pseudonymous, the agency should still select AAL2 or AAL3 for authentication because a malicious actor could gain access to the user's PHI by compromising the account.

> Note: An agency can accept a higher assurance level than those required in the table above. For example, in a federated transaction, an agency can accept an IAL3 identity if their application is assessed at IAL2. The same holds true for authenticators: stronger authenticators can be used at RPs that have lower authenticator requirements. However, RPs will have to ensure that this only occurs in federated scenarios with appropriate privacy protections by the CSP such that only attributes that have been requested by the RP and authorized by the subscriber are provided to the RP and that excessive personal information does not leak from the credential or an assertion. See the [privacy considerations in SP 800-63C](sp800-63c.html#privacy) for more details.

<!---->

> Note: The upshot of potentially having a different IAL, AAL, and FAL within a single application stems from the fact that this document no longer supports the notion of an overall LOA &mdash; the "low watermark" approach to determining LOA no longer applies. An application with IAL1 and AAL2 should not be considered any less secure or privacy-enhancing than an application with IAL2 and AAL2. The only difference between these applications is the amount of proofing required, which may not impact the security and privacy of each application. That said, if an agency incorrectly determines the xAL, security and privacy could very well be impacted.

### <a name="IAL_CYOA"></a> 6.1 Selecting IAL

The IAL decision tree in [Figure 6-1](#63Sec6-Figure1) combines the results from the risk assessment with additional considerations related to identity proofing services to allow agencies to select the most appropriate identity proofing requirements for their digital service offering. 

The IAL selection does not mean the digital service provider will need to perform the proofing themselves. More information on whether an agency can federate is provided in [Section 7](#toFedorNotToFed). 

<a name="63Sec6-Figure1"></a>
<div class="text-center" markdown="1">
<img src="sp800-63-3/media/IAL_CYOA.png" alt="IAL Choose Your Own" style="width:1000px;height:1093px;;min-width: 1000px;min-height:1093px;"/>

**Figure 6-1 Selecting IAL**
</div>


<div class="text-left" markdown="1">
<table style="width:100%">
  <tr>
    <td><img src="sp800-63-3/media/ial-step1.png" alt="IAL Step 1"/></td>
  </tr>
  <tr>
   <td>The risk assessment and IAL selection can be short circuited by answering this question first. If the service does not require any personal information to execute any digital transactions, the system can operate at IAL1.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/ial-step2.png" alt="IAL Step 2"/></td>
  </tr>
  <tr>
   <td>If personal information is needed, the RP needs to determine if validated and verified attributes are required, or if self-asserted attributes are acceptable. If even a single validated and verified attribute is needed, then the provider will need to accept attributes that have been IAL2 or IAL3 proofed. Again, the selection of IAL can be short circuited to IAL1 if the agency can deliver the digital service with self-asserted attributes only.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/ial-step3.png" alt="IAL Step 3"/></td>
  </tr>
  <tr>
   <td>At this point, the agency understands that some level of proofing is required. Step 3 is intended to look at the potential impacts of an identity proofing failure to determine if IAL2 or IAL3 is the most appropriate selection. The primary identity proofing failure an agency may encounter is accepting a falsified identity as true, therefore providing a service or benefit to the wrong or ineligible person. In addition, proofing, when not required, or collecting more information than needed is a risk in and of itself. Hence, obtaining verified attribute information when not needed is also considered an identity proofing failure. This step should identify if the agency answered Step 1 and 2 incorrectly, realizing they do not need personal information to deliver the service. Risk should be considered from the perspective of the organization and to the user, since one may not be negatively impacted while the other could be significantly harmed. Agency risk management processes should commence with this step.</td>
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/ial-step4.png" alt="IAL Step 4"/></td>
  </tr>
  <tr>
   <td>Step 4 is intended to determine if the personal information required by the agency will ultimately resolve to a unique identity. In other words, the agency needs to know the full identity of the subject accessing the digital service, and pseudonymous access, even with a few validated and verified attributes, is not possible. If the agency needs to uniquely identify the subject, the process can end. However, the agency should consider if Step 5 is of value to them, as the acceptance of claims will reduce exposure to the risk of over collecting and storing more personal information than is necessary.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/ial-step5.png" alt="IAL Step 5"/></td>
  </tr>
  <tr>
   <td>Step 5 focuses on whether the digital service can be provided without having access to full attribute values. This does not mean all attributes must be delivered as claims, but this step does ask the agency to look at each personal attribute they have deemed necessary, and identify which can suffice as claims and which need to be complete values. A federated environment is best suited for receiving claims, as the digital service provider is not in control of the attribute information to start with. If the application also performs all required identity proofing, claims may not make sense since full values are already under the digital service provider's control.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/ial-step6.png" alt="IAL Step 6"/></td>
  </tr>
  <tr>
   <td>If the agency has reached Step 6, claims should be used. This step identifies the digital service as an excellent candidate for accepting federated attribute references from a CSP (or multiple CSPs), since it has been determined that complete attribute values are not needed to deliver the digital service.</td> 
  </tr>
  </table>
</div>

> Note: Agencies should also consider their constituents' demographics when selecting the most appropriate proofing process. While not a function of IAL selection, certain proofing processes may be more appropriate for some demographics than others. Agencies will benefit as this type of analysis ensures the greatest opportunity for their constituents to be proofed successfully.
 
### <a name="AAL_CYOA"></a> 6.2 Selecting AAL

The AAL decision tree in [Figure 6-2](#63Sec6-Figure2) combines the results from the risk assessment with additional considerations related to authentication to allow agencies to select the most appropriate authentication requirements for their digital service offering. 

The AAL selection does not mean the digital service provider will need to issue authenticators themselves. More information on whether the agency can federate is provided in [Section 7](#toFedorNotToFed). 

<a name="63Sec6-Figure2"></a>
<div class="text-center" markdown="1">
<img src="sp800-63-3/media/AAL_CYOA.png" alt="AAL Choose Your Own" style="width:1000px;height:958px;;min-width: 1000px;min-height:958px;"/>

**Figure 6-2 Selecting AAL**
</div>

<div class="text-left" markdown="1">
<table style="width:100%">
  <tr>
    <td><img src="sp800-63-3/media/aal-step1.png" alt="AAL Step 1"/></td>
  </tr>
  <tr>
   <td>Step 1 asks agencies to look at the potential impacts of an authentication failure. In other words, what would occur if an unauthorized user accessed one or more valid user accounts? Risk should be considered from the perspective of the organization and to a valid user, since one may not be negatively impacted while the other could be significantly harmed. Agency risk management processes should commence with this step.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/aal-step2.png" alt="AAL Step 2"/></td>
  </tr>
  <tr>

   <td>MFA is required when any personal information is made available online. Since the other paths in this decision tree already drive the agency to an AAL that requires MFA, the question of personal information is only raised at this point. That said, personal information release at all AALs should be considered when performing the risk assessment. An important point at this step is that the collection of personal information, if not made available online, does not need to be validated or verified to require an AAL of 2 or higher. Release of even self-asserted personal information requires account protection via MFA. Even though self-asserted information can be falsified, most users will provide accurate information to benefit from the digital service. As such, self-asserted data must be protected appropriately.</td> 

  </tr>
  
  </table>
</div>

### <a name="FAL_CYOA"></a> 6.3 Selecting FAL

The FAL decision tree in [Figure 6-3](#63Sec6-Figure3) combines the results from the risk assessment with additional considerations related to federation to allow agencies to select the most appropriate requirements for their digital service offering. 

<a name="63Sec6-Figure3"></a>
<div class="text-center" markdown="1">
<img src="sp800-63-3/media/FAL_CYOA.png" alt="FAL Choose Your Own" style="width:1000px;height:983px;;min-width: 1000px;min-height:983px;"/>

**Figure 6-3 Selecting FAL**
</div>

<div class="text-left" markdown="1">
<table style="width:100%">
  <tr>
    <td><img src="sp800-63-3/media/fal-step1.png" alt="FAL Step 1"/></td>
  </tr>
  <tr>
   <td>Step 1 asks agencies to look at the potential impacts of a federation failure. In other words, what would occur if an unauthorized user could compromise an assertion? Examples of compromise include use of assertion replay to impersonate a valid user or leakage of assertion information information through the browser. Risk should be considered from the perspective of the organization and to the subscriber, since one may not be negatively impacted while the other could be significantly harmed. Agency risk management processes should commence with this step.</td> 
  </tr>
  <tr>
    <td><img src="sp800-63-3/media/fal-step2.png" alt="FAL Step 2"/></td>
  </tr>
  <tr>

   <td>FAL2 is required when any personal information is passed in an assertion. Personal information release at all FALs should be considered when performing the risk assessment. FAL2 or higher is required when any personal information is contained in an assertion, as the audience and encryption requirements at FAL1 are not sufficient to protect personal information from being released. Release of even self-asserted personal information requires assertion protection via FAL2. Even though self-asserted information can be falsified, most users will provide accurate information to benefit from the digital service. However, when personal information is available to the RP via an authorized API call, such information need not be included in the assertion itself. Since the assertion no longer includes personal information, it need not be encrypted and this FAL requirement does not apply.</td> 

  </tr>
  <tr>
    <td><img src="sp800-63-3/media/fal-step3.png" alt="FAL Step 3"/></td>
  </tr>
  <tr>
   <td>RPs should use a back-channel presentation mechanism as described in [SP 800-63C Section 7.1](sp800-63c.html#back-channel) where possible as such mechanisms allow for greater privacy and security. Since the subscriber handles only an assertion reference and not the assertion itself, there is less chance of leakage of attributes or other sensitive information found in the assertion to the subscriber's browser or other programs. As the RP directly presents the assertion reference to the IdP, the IdP can often take steps to identify and authenticate the RP during this step. Further, as the RP fetches the assertion directly from the IdP over an authenticated protected channel, there are fewer opportunities for an attacker to inject an assertion into an RP.</td> 
  </tr>
  
  </table>
</div>

All FALs require assertions to have a baseline of protections, including signatures, expirations, audience restrictions, and others enumerated in [SP 800-63C](sp800-63c.html#assertions). When taken together, these measures make it so that assertions cannot be created or modified by an unauthorized party, and that an RP will not accept an assertion created for a different system. 

### 6.4 Combining xALs 

This guideline introduces a model where individual xALs can be selected without requiring parity to each other. While options exist to select varying xALs for a system, in many instances the same level will be chosen for all xALs.

The ability to combine varying xALs offers significant flexibility to agencies, but not all combinations are possible due to the nature of the data collected from an individual and the authenticators to protect that data. [Table 6-2](#63sec6-Table2) details valid combinations of IAL and AAL to ensure personal information remains protected by MFA.

<a name="63sec6-Table2"></a>

<div class="text-center" markdown="1">

**Table 6-2 Acceptable Combinations of IAL and AAL**

</div>


| | AAL1 | AAL2 | AAL3 |
|:-:|:-:|:-:|:-:|
| **IAL1: Without personal data** | Allowed | Allowed | Allowed |
| **IAL1: With personal data** | **NO** | Allowed | Allowed |
| **IAL2** |  **NO** | Allowed | Allowed |
| **IAL3** |  **NO** | Allowed | Allowed |

> Note: Per Executive Order 13681 [[EO 13681]](#EO13681), the release of personal data requires protection with MFA, even if the personal data is self-asserted and not validated. When the transaction does not make personal data accessible, authentication may occur at AAL1, although providing an option for the user to choose stronger authentication is recommended. In addition, it may be possible at IAL1 to self-assert information that is not personal, in which case AAL1 is acceptable.
