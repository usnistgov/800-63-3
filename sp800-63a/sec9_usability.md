<a name="sec9"></a>

<div class="breaker"></div>

## 9 Usability Considerations

_This section is informative._

This section is intended to raise implementers' awareness of the usability considerations associated with enrollment and identity proofing (for usability considerations for typical authenticator usage and intermittent events, see [SP 800-63B, Section 10](sp800-63b.html#sec10).

[ISO/IEC 9241-11](#ISO9241-11) defines usability as the "extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as the necessary elements for achieving effectiveness, efficiency, and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.

The overarching goal of usability for enrollment and identity proofing is to promote a smooth, positive enrollment process for users by minimizing user burden (e.g., time and frustration) and enrollment friction (e.g., the number of steps to complete and amount of information to track). To achieve this goal, organizations have to first familiarize themselves with their users.

The enrollment and identity proofing process sets the stage for a user's interactions with a given CSP and the online services that the user will access; as negative first impressions can influence user perception of subsequent interactions, organizations need to promote a positive user experience throughout the process.

Usability cannot be achieved in a piecemeal manner. Performing a usability evaluation on the enrollment and identity proofing process is critical. It is important to conduct usability evaluation with representative users, realistic goals and tasks, and appropriate contexts of use. The enrollment and identity proofing process should be designed and implemented so it is easy for users to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.

From the user's perspective, the three main steps of enrollment and identity proofing are pre-enrollment preparation, the enrollment and proofing session, and post-enrollment actions. These steps may occur in a single session or there could be significant time elapsed between each one (e.g., days or weeks).

General and step-specific usability considerations are described in sub-sections below.

**ASSUMPTIONS**

In this section, the term "users" means "applicants" or "subscribers."

Guidelines and considerations are described from the users' perspective. 

Accessibility differs from usability and is out of scope for this document. [Section 508](#Section508) was enacted to eliminate barriers in information technology and require federal agencies to make their electronic and information technology public content accessible to people with disabilities. Refer to Section 508 law and standards for accessibility guidance.

### 9.1 General User Experience Considerations Duuring Enrollment and Identity Proofing


This sub-section provides usability considerations that are applicable across all steps of the enrollment process. Usability considerations specific to each step are detailed in Sections [9.2](#sec9_2) to [9.4](#sec9_4).

* To avoid user frustration, streamline the process required for enrollment to make each step as clear and easy as possible.
 
* Clearly communicate how and where to acquire technical assistance. For example, provide helpful information such as a link to online self-service feature, chat sessions, and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to answer their own enrollment preparation questions without outside intervention.

* Clearly explain who is collecting their data and why. Also indicate the path their data will take, in particular where the data is being stored.

* Ensure all information presented is usable.
  * Follow good information design practice for all user-facing materials (e.g., data collection notices and fillable forms). 
  * Write materials in plain language, typically at a 6th to 8th grade literacy level, and avoid technical jargon. Use active voice and conversational style, logically sequence main points, use the same word consistently rather than synonyms to avoid confusion, and use bullets, numbers, and formatting where appropriate to aid readability. 
  * Consider text legibility, such as font style, size, color, and contrast with surrounding background. The highest contrast is black on white. Text legibility is important because users have different levels of visual acuity. Illegible text will contribute to user comprehension errors or user entry errors (e.g., when completing fillable forms).
  * Use sans serif font styles for electronic materials and serif fonts for paper materials.
  * When possible, avoid fonts that do not clearly distinguish between easily confusable characters (such as the letter "O" and the number "0"). This is especially important for enrollment codes.
  * Use a minimum font size of 12 points, as long as the text fits the display.
* Perform a usability evaluation for each step with representative users. Establish realistic goals and tasks, and appropriate contexts of use for the usability evaluation.


### <a name="sec9_2"></a>9.2 Pre-Enrollment Preparation

This section describes an effective approach to facilitate sufficient pre-enrollment preparation so users can avoid challenging, frustrating enrollment sessions. Ensuring users are as prepared as possible for their enrollment sessions is critical to the overall success and usability of the enrollment and identity proofing process. 

Such preparation is only possible if users receive the necessary information (e.g., required documentation) in a usable format in an appropriate timeframe. This includes making users aware of exactly what identity evidence will be required. Users do not need to know anything about IALs or whether the identity evidence required is scored as "fair," "strong," or "superior," whereas organizations need to know what IAL is required for access to a particular system. 

To ensure users are equipped to make informed decisions about whether to proceed with the enrollment process, and what will be needed for their session, provide users: 

* Information about the entire process, such as what to expect in each step.   
  * Clear explanations of the expected timeframes to allow users to plan accordingly. 

* Explanation of the need for — and benefits of — identity proofing to allow users to understand the value proposition. 

* Information on the monetary amount and acceptable forms of payment, and if there is an enrollment fee. Offering a larger variety of acceptable forms of payment allows users to choose their preferred payment operation.

* Information on whether the user's enrollment session will be in-person or in-person over remote channels, and whether a user can choose. Only provide information relevant to the allowable session option(s).
  * Information on the location(s), whether a user can choose their preferred location, and necessary logistical information for in-person or in-person over remote channels session. Note that users may be reluctant to bring identity evidence to certain public places (bank versus supermarket), as it increases exposure to loss or theft.
  * Information on the technical requirements (e.g., requirements for internet access) for remote sessions.
  * An option to set an appointment for in-person or in-person over remote channels identity proofing sessions to minimize wait times. If walk-ins are allowed, make it clear to users that their wait times may be greater without an appointment.
    * Provide clear instructions for setting up an enrollment session appointment, reminders, and how to reschedule existing appointments.
    * Offer appointment reminders and allow users to specify their preferred appointment reminder format(s) (e.g., postal mail, voicemail, email, text message). Users need information such as date, time, location, and a description of required identity evidence.
* Information on the allowed and required identity evidence and attributes, whether each piece is voluntary or mandatory, and the consequences for not providing the complete set of identity evidence. Users need to know the specific combinations of identity evidence, including requirements specific to a piece of identity evidence (e.g., a raised seal on a birth certificate). This is especially important due to potential difficulties procuring the necessary identity evidence. 
  * Where possible, implement tools to make it easier to obtain the necessary identity evidence.
  * Inform users of any special requirements for minors and people with unique needs. For example, provide users with the information necessary to use trusted referees, such as a notary, legal guardian, or some other form of certified individual that can legally vouch for or act on behalf of the individual (see [Section 5.3.4](#trustref)). 
  * If forms are required:
     * Provide fillable forms before and at the enrollment session. Do not require users to have access to a printer. 
     * Minimize the amount of information users must enter on a form, as users are easily frustrated and more error-prone with longer forms. Where possible, pre-populate forms. 

### 9.3 Enrollment and Proofing Session

Usability considerations specific to the enrollment session include:

* Remind users at the start of the enrollment session of the enrollment session procedure, without expecting them to remember from the pre-enrollment preparation step. If the enrollment session does not immediately follow pre-enrollment preparation, it is especially important to clearly remind users of the typical timeframe to complete the proofing and enrollment phase. 
  * Provide rescheduling options for in-person or in-person over remote channels.
  * Provide a checklist with the allowed and required identity evidence to ensure users have the requisite identity evidence to proceed with the enrollment session, including enrollment codes, if applicable. If users do not have the complete set of identity evidence, they must be informed regarding whether they can complete a partial identity proofing session.
  * Notify users regarding what information will be destroyed, what, if any, information will be retained for future follow-up sessions, and what identity evidence they will need to bring to complete a future session. Ideally, users can choose whether they would like to complete a partial identity proofing session.
  * Set user expectations regarding the outcome of the enrollment session as prior identity verification experiences may drive their expectations (e.g., receiving a driver's license in person, receiving a passport in the mail). 
  * Clearly indicate whether users will receive an authenticator immediately at the end of a successful enrollment session, if users have to schedule an appointment to pick it up in person, or if users will receive it in the mail and when they can expect to receive it.

* During the enrollment session, there are several requirements to provide users with explicit notice at the time of identity proofing, such as what data will be retained on record by the CSP (see [Section 4.2.](#genProofReqs) and [Section 8.](#sec8) for detailed requirements on notices). If CSPs seek consent from a user for additional attributes or uses of their attributes for any purpose other than identity proofing, authentication, authorization or attribute assertions, per 4.2 requirement (5), make CSPs aware that requesting additional attributes or uses may be unexpected or may make users uncomfortable. If users do not perceive benefit(s) to the additional collection or uses, but perceive extra risk, they may be unwilling or hesitant to provide consent or continue the process. Provide users with explicit notice of the additional requirements. 
* Avoid using KBV since it is extremely problematic from a usability perspective. KBV tends to be error-prone and frustrating for users given the limitations of human memory. If KBV is used, address the following usability considerations. 
  * KBV questions should have relevance and context to users for them to be able to answer correctly. 
  * Phrase KBV questions clearly, as ambiguity can lead to user errors. For example, when asking about a user's social security balance, clearly specify which time period as social security accounts fluctuate. 
  * Prior to being asked KBV questions, users must be informed of:
    * The number of allowed attempts and remaining attempt(s).
    * The fact that KBV questions will change on subsequent attempts. 
    * During the KBV session, provide timeout inactivity warnings prior to timeout. 
* If an enrollment code is issued:
    * Notify users in advance that they will receive an enrollment code, when to expect it, the length of time for which the code is valid, and how it will arrive (e.g., physical mail, SMS, landline telephone, email, or physical mailing address).
    * When an enrollment code is delivered to a user, include instructions on how to use the code, and the length of time for which the code is valid. This is especially important given the short validity timeframes specified in [Section 4.4.1.6](#4-4-1-6). 
    * If issuing a machine-readable optical label, such as a QR Code (see [Section 4.6.](#enrollmentcode)), provide users with information on how to obtain QR code scanning capabilities (e.g., acceptable QR code applications).
    * Inform users that they will be required to repeat the enrollment process if enrollment codes expire or are lost before use.
    * Provide users with alternative options as not all users are able to use this level of technology. For example, users may not have the technology needed for this approach to be feasible.
* At the end of the enrollment session, 
  * If enrollment is successful, send users confirmation regarding the successful enrollment and information on next steps (e.g., when and where to pick up their authenticator, when it will arrive in the mail).
  * If enrollment is partially complete (due to users not having the complete set of identity evidence, users choosing to stop the process, or session timeouts), communicate to users:  
  	* what information will be destroyed;
  	* what, if any, information will be retained for future follow-up sessions;
  	* how long the information will be retained; and 
  	* what identity evidence they will need to bring to a future session.
  * If enrollment is unsuccessful, provide users with clear instructions for alternative enrollment session types, for example, offering in-person proofing for users that can not complete remote proofing.
* If users receive the authenticator during the enrollment session, provide users information on the use and maintenance of the authenticator. For example, information could include instructions for use (especially if there are different requirements for first-time use or initialization), information on authenticator expiration, how to protect the authenticator, and what to do if the authenticator is lost or stolen. 

* For both in-person and in-person proofing performed over remote channels enrollment sessions, additional usability considerations apply:
  * At the start of the enrollment session, operators or attendants need to explain their role to users (e.g., whether operators or attendants will walk users through the enrollment session or observe silently and only interact as needed).
  * At the start of the enrollment session, inform users that they must not depart during the session, and that their actions must be visible throughout the session.
  * When biometrics are collected during the enrollment session, provide users clear instructions on how to complete the collection process. The instructions are best given just prior to the process. Verbal instructions with corrective feedback from a live operator are the most effective (e.g., instruct users where the biometric sensor is, when to start, how to interact with the sensor, and when the biometric collection is completed).

* Since remote identity proofing is conducted online, follow general web usability principles. For example: 
  * Design the user interface to walk users through the enrollment process.
  * Reduce users' memory load.
  * Make the interface consistent.
  * Clearly label sequential steps.
  * Make the starting point clear.
  * Design to support multiple platforms and device sizes.
  * Make the navigation consistent, easy to find, and easy to follow. 
      

###  <a name="sec9_4"></a>9.4 Post-Enrollment 
Post-enrollment refers to the step immediately after enrollment but prior to typical usage of an authenticator (for usability considerations for typical authenticator usage and intermittent events, see [SP800-63B](sp800-63b.html), Section 10.1-10.3. As described above, users have already been informed at the end of their enrollment session regarding the expected delivery (or pick-up) mechanism by which they will receive their authenticator.

Usability considerations for post-enrollment include:

* Minimize the amount of time that users wait for their authenticator to arrive. Shorter wait times will allow users to access information systems and services more quickly. 

* Inform users whether they need to go to a physical location to pick up their authenticators. The previously-identified usability considerations for appointments and reminders still apply. 

* Along with the authenticator, give users information relevant to the use and maintenance of the authenticator; this may include instructions for use, especially if there are different requirements for first-time use or initialization, information on authenticator expiration, and what to do if the authenticator is lost or stolen. 
