<a name="sec9"></a>

<div class="breaker"></div>

# 9. Usability Considerations

_This section is informative._

[ISO/IEC 9241-11](#ISO9241-11) defines usability as the "extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, goals, and context of use as key elements necessary for achieving effectiveness, efficiency, and satisfaction. A holistic approach considering these key elements is necessary to achieve usability. 

The overarching goal of usability for enrollment and identity proofing is to promote a smooth, positive enrollment process for users by minimizing user burden (e.g., time and frustration) and enrollment friction (e.g., the number of steps to complete and amount of information to track). 

The enrollment and identity proofing process sets the stage for a user’s interactions with a CSP; since negative first impressions can influence user perception of subsequent interactions, organizations benefit from promoting a positive user experience throughout the process. 

An organization’s first step to promoting a smooth, positive enrollment process is familiarizing itself with the user. This consists of matching users with suitable CSPs based on their characteristics ahead of the enrollment and identity proofing process. 

The enrollment and identity proofing process should be designed and implemented so it is easy for users to do the right thing and to recover when something goes wrong, and hard to do the wrong thing or impersonate an individual. 

The current section takes this holistic view in applying usability principles to the enrollment and identity proofing process, with the goal of raising implementers’ awareness of usability considerations associated with enrollment and identity proofing (for usability considerations for typical authenticator usage and intermittent events, see 800-63-3B).

##### ASSUMPTIONS 

In this section, the term “users” means “applicants” or “subscribers.”

Guidelines and considerations are described from the end-users’ perspective, as usability guidelines can only be written from this perspective. 

Accessibility and usability differ significantly, therefore accessibility is out of scope for this section. Accessibility can instead be addressed in an organization’s implementation plans. 

### 9.1. User Experience During Enrollment and Identity Proofing
From the user’s perspective, the three main stages of enrollment and identity proofing are pre-enrollment preparation, enrollment and proofing session, and post-enrollment actions. Note these stages may occur in a single session or there could be significant time elapsed between each stage (for example, days or weeks).

It is important to clearly communicate how and where to acquire technical assistance at every stage of the process. For example, provide users information—such as a link to online self-service feature, chat sessions, and a phone number for help desk support. Ideally, sufficient information is provided to enable users to answer their own enrollment preparation questions without outside intervention.

Regardless of form – be it digital or physical – ensure information presented to the user is accessible and readable. 
•	Follow good information design practice for all user-facing materials (e.g., data collection notices and fillable forms). 
•	Write materials in plain language (typically at a 6th to 8th grade literacy level) and avoid technical jargon. Use active voice and conversational style, logically sequence main points, use the same word consistently rather than synonyms to avoid confusion, and use bullets, numbers, and formatting where appropriate to aid readability. 
•	Consider text legibility, such as font style, size, color, and contrast with surrounding background. Illegible text will contribute to user comprehension errors or user entry errors (e.g., when completing fillable forms).
•	Sans serif font styles are recommended for electronic materials; serif fonts are recommended for paper materials. 
•	Avoid, when possible, fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”). This is especially important for enrollment codes. 
•	Consider using a minimum font size of 12 points, as long as the text fits for display.

Usability considerations for each stage are detailed below. Most apply to all identity proofing approaches. However, additional considerations are provided for specific proofing methods.

#### 9.1.1. Pre-Enrollment Preparation

This section is devoted to describing an effective approach to facilitate sufficient pre-enrollment preparation so users can avoid challenging, frustrating enrollment sessions. Ensuring users are as prepared as possible for their enrollment sessions is critical to the overall success and usability of the enrollment and identity proofing process. 

Such preparation is only possible if users receive the necessary information (e.g., documentation required or system requirements) in a usable format in an appropriate timeframe. This includes making them aware of exactly what identity evidence will be required – conveyed from the users’ perspective, not the implementers’ perspectives - regardless of whether the session is in-person, virtual in-person, or remote. For example, while organizations need to know in advance what type of IAL is required for access to a particular information system, users do not need to know anything about IALs or whether the identity evidence required is scored as ‘fair’, ‘strong’, or ‘superior’; users simply need to know what materials are required and how and where to provide them. 

In order to ensure users are equipped to make informed decisions about whether to proceed with the enrollment process, and what will be needed for their session, include in messaging: 

* Information about the entire process, such as what to expect in each step. 
    * Clear explanations of the expected timeframes allow users to plan accordingly.
*   Explanation of the need for—and benefits of—identity proofing. 
*   The minimal number of steps required, with each as clear and easy as possible. 
*   Information on the monetary amount and acceptable forms of payment, in case there is an enrollment fee. 
*   Whether the user’s enrollment session will be in-person, virtual in-person, or remote (and whether a user is allowed to choose). Only provide information relevant to the allowable session option(s). 
    * Information on the location(s) (and whether a user is allowed to choose her or his preferred location) and necessary logistical information for in-person or virtual in-person session. 
    * Information on the technical requirements (e.g., requirements for internet access) for remote sessions.
    * An option to set an appointment for in-person or virtual in-person identity proofing sessions to minimize wait times. If walk-ins are allowed, make it clear to users that their wait times may be greater without an appointment.
      * Provide clear instructions regarding setting up an enrollment session appointment and reminders, and how to reschedule existing appointments.
      * Offer appointment reminders and allow users to specify their preferred appointment reminder format(s) (e.g., postal mail, voicemail, email, text message). Include all pertinent enrollment session information in appointment reminders: date, time, and location (or technical requirements for a virtual in-person session, such as a link to join a virtual session), and a description of required identity evidence. 
*   Information on the exact allowed and required identity evidence and attributes, whether each piece is voluntary or mandatory, and the consequences for not providing the complete set of identity evidence. Users need to know the specific combinations of identity evidence, including requirements specific to a particular piece of identity evidence (e.g., a raised seal on a birth certificate, an original authenticator for obtaining a derived authenticator). This is especially important due to potential difficulties procuring the necessary identity evidence. 
    * Where possible, implement tools to make it easier to obtain the necessary identity evidence. 
    * Inform users of any special requirements for minors and people with unique needs. For example, provide users with the information necessary to use trusted referees, such as a notary, legal guardian, or some other form of certified individual that can legally vouch for or act on behalf of the individual (see Section 5.4.4). 
    * If forms are required: 
      * Provide fillable forms before and at the enrollment session. Do not require that users have access to a printer. 
      * Minimize the amount of information users must enter on a form, as users are easily frustrated and more error-prone with longer forms. Where possible, pre-populate forms. 

#### 9.1.2. Enrollment and Proofing Session

Usability considerations for the enrollment session include:  

*   Remind users at the start of the enrollment session of the enrollment session procedure, without expecting them to remember from the pre-enrollment preparation stage. If the enrollment session does not immediately follow the pre-enrollment preparation stage, it is especially important to clearly remind users of the typical timeframe to complete the proofing and enrollment phase. 
      * Provide rescheduling options (for in-person or virtual in-person), as users may need to reschedule their enrollment session appointment if they do not have adequate time to complete the enrollment session.
    * Provide a checklist with the allowed and required identity evidence to ensure users have the requisite identity evidence to proceed with the enrollment session, including enrollment codes if applicable. If users do not have the complete set of identity evidence, they must be informed regarding whether they can complete a partial identity proofing session. Notify users regarding what information will be destroyed, what (if any) information will be retained for future follow-up sessions, and what identity evidence they will need to bring to complete a future session. Ideally, users can choose whether or not they would like to complete a partial identity proofing session.
    * Set user expectations regarding the outcome of the enrollment session. Setting user expectations is critical as prior identity verification experiences may drive their expectations (e.g., receiving a drivers license in person, receiving a passport in the mail).
*   During the enrollment session, there are several requirements to provide users with explicit notice at the time of identity proofing, such as what data will be retained on record by the CSP (see Section 4.2 and Section 8 for detailed requirements on notices). If CSPs seek consent from a user for additional attributes or uses of their attributes for any purpose other than identity proofing, authentication, authorization or attribute assertions, per 4.2(5), make CSPs aware that requesting additional attributes or uses may be unexpected or may make users uncomfortable. If users do not perceive benefit(s) to the additional collection or uses, but perceive extra risk, they may be unwilling or hesitant to provide consent or continue the process. CSPs provide users with explicit notice of the additional requirements. 
*   If at all possible, avoid using KBV, as KBV is extremely problematic from a usability perspective. It is error-prone and frustrating for users given the limitations of human memory, and has a low probability of success. 
    * The types of questions used in KBV are often extremely difficult for users to answer correctly. The questions often ask users to recall old, infrequently used information, or information that changes over time. KBV questions must still have relevance to users for them to be able to answer correctly. 
    * It is especially important that CSPs clearly phrase KBV questions, as ambiguity can lead to user errors when answering. 
    * Free-form versus multiple-choice KBV questions have different usability implications. If free-form responses are required, accept all semantically correct answers.
      * Write multiple-choice KBV questions as to reduce potential confusion. 
    The number of allowed attempts. As they progress through the KBV process, users must be informed of the number of remaining attempt(s).
    * The fact that KBV questions will change on subsequent attempts. 
    * Timeouts. During the KBV session, provide timeout inactivity warnings prior to timeout. 
*   If an enrollment code is issued:
    * Notify users in advance that they will receive an enrollment code, when to expect it, the length of time for which the code is valid, and the means by which it will arrive (e.g., physical mail, SMS, landline telephone, email, or physical mailing address).
    * When an enrollment code is delivered to a user, include instructions on how to use the code, and the length of time for which the code is valid. This is especially important given the short validity timeframes specified in Section 4.5.6. 
  * If the CSP issues a machine readable optical label, such as a QR Code (see Section 4.7), provide users with information on how to obtain QR code scanning capabilities (e.g., acceptable QR code applications).
    * If enrollment codes expire or are lost before use, inform users that they will be required to repeat the enrollment process. 
*   At the end of the enrollment session, 
    * If enrollment is successful,
      * Send users confirmation regarding the successful enrollment and informing them of next steps (e.g., when and where to pick up their authenticator, when it will arrive in the mail).
    * If enrollment is partial (due to users not having the complete set of identity evidence, users choosing to stop the process, or session timeouts),
      * Communicate to users what information will be destroyed and what, if any, information will be retained for future follow-up sessions (and for how long), and what identity evidence they will need to bring to complete a future session.
    * If enrollment is unsuccessful, 
      * Provide users with clear instructions for alternative enrollment session type(s), for example, offering in-person proofing if users failed remote proofing.
*   If users receive the authenticator during the enrollment session, provide information on the use and maintenance of the authenticator. For example, instructions for use (especially if there are different requirements for first-time use or initialization), information on authenticator expiration, and what to do if the authenticator is lost or stolen. 
*   Depending on enrollment session type (in-person, virtual in-person, or remote), additional usability considerations apply.
    * In-person
      * At the start of the enrollment session, operators explain their role to users (e.g. whether the operator will walk users through the enrollment session or observe silently and only interact as needed). 
      * If users choose to complete a partial enrollment session (due to not having the requisite set of identity evidence), offer provisions to schedule a follow-up session to complete the enrollment process. The previously identified usability considerations for appointments still apply. 
      * If biometrics are being collected during the enrollment session, provide users clear instructions on how to complete the collection process just prior to the process. Verbal instructions with corrective feedback from a live operator are the most effective (e.g. instruct users where the biometric sensor is, when to start, how to interact with the sensor, when the biometric collection is completed).
      * If users receive the authenticator during the enrollment session, operators demonstrate use and help users test the authenticator during enrollment sessions to ensure the authenticator works correctly and users understand its operation.
    * Virtual in-person
      * If enrollment sessions are conducted in publicly-observable spaces (e.g., a kiosk in a bank, a supermarket), design and place the enrollment station to minimize user concern of being observed by others. 
      * At the start of the enrollment session, inform users that they must not depart during the session, and that all their actions must be visible throughout the session. 
      * If users choose to complete a partial enrollment session (due to not having the requisite set of identity evidence), provisions must be made to schedule a follow-up session to complete the enrollment process. The previously identified usability considerations for appointments still apply. 
      * If biometrics are being collected during the enrollment session, provide users clear instructions on how to complete the collection process. Provide instructions just prior to the collection process. Verbal instructions with corrective feedback from a live operator are the most effective. For example, instruct users where the biometric sensor is, when to start, how to interact with the sensor, and when the biometric collection is completed.
      * If users receive the authenticator during the enrollment session, operators demonstrate use and help users test the authenticator during enrollment sessions to ensure the authenticator works correctly and users understand its operation.
    * Remote
      * Since remote identity proofing sessions are conducted online, follow general web usability principles. For example, design the user interface to walk users through the enrollment process; reduce users’ memory load; make the interface consistent; clearly label sequential steps; make the starting point clear; design to support multiple platforms and device sizes; and make the navigation consistent, easy to find, and easy to follow. 
      * Explain clearly to the users who is collecting and who is retaining which information they’re providing. For instance, if a user is going to stay on the CSP site to enter financial information that will be sent to a 3rd party vendor, explain this to users so they understand the path their data will take.

####  9.1.3. Post-Enrollment 
Post-enrollment refers to the stage immediately after enrollment but prior to typical usage of an authenticator (for usability considerations for typical authenticator usage and intermittent events, see 800-63-3B). As described above, users have already been informed at the end of their enrollment session regarding the expected delivery (or pick-up) mechanism by which they will receive their authenticator.
Usability considerations for post-enrollment include:

*   CSPs strive to minimize the amount of time that users wait for their authenticator to arrive. Shorter wait times will allow users to access information systems and services more quickly. 
*   Users are informed of whether they need to go to a physical location to pick up their authenticators. The previously identified usability considerations for appointments and reminders still apply. 
*   Along with the authenticator, users are given information relevant to the use and maintenance of the authenticator; this may include instructions for use (especially if there are different requirements for first-time use or initialization), information on authenticator expiration, and what to do if the authenticator is lost or stolen.