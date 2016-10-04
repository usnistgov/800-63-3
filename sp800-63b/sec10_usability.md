<a name="sec10"></a>

## 10. Usability Considerations

_This section is informative._

[ISO/IEC 9241-11](#ISO9241-11) defines usability as: Extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use. This definition focuses on users, goals, and context of use as key elements necessary for achieving effectiveness, efficiency and satisfaction. A holistic approach considering these key elements is necessary to achieve usability.    

Users’ goals for accessing an information system are to perform their intended tasks. Authentication is not a user’s primary task, but an enabling task standing between the users and their goals.  Authentication should be designed and implemented to make it easy for users to do the right thing, hard to do the wrong thing, and easy to recover when something goes wrong.  

Organizations must be cognizant of the overall implications of their stakeholders entire digital authentication ecosystem. Many times, users employ one or more authenticators, each for different RPs. Users struggle to remember passwords, to carry multiple authentication devices, and to remember which authenticator goes with which RP. It is critical to evaluate the usability of authentication, since poor usability often results in user coping mechanisms and unintended user work-arounds, which can ultimately degrade the intended security controls.  

In order to address users’ authentication needs and organizations’ security goals, organizations should assess the impact of usability across their digital systems, as part of the risk assessment when deciding on the Authenticator Assurance Level (AAL) requirements. If authenticators with a higher AAL offer better usability, users should be allowed to use them for lower AAL applications. For example, rather than forcing users to manage many passwords, allow users to use their favorite authenticator across the organization’s applications. Users should be able to choose their authenticator, and in some instances, may choose to only have to manage one authenticator for their digital authentication needs. For example, this may be achieved by adopting identity federation (see NIST SP 800-63C, Federation and Assertions).
For the selection of an authenticator, only by considering the combination of users, their goals, and context of use with the authenticator and the security risk assessment can usability and security be achieved in tandem. The current section takes this holistic view in applying usability principles to authenticators across their lifecycle.  

##### ASSUMPTIONS  

In this section, the term “users” means “Claimants” or “Subscribers.”
This section describes guidelines and considerations from the end-users’ perspective, as usability guidelines can only be written from the end-users’ perspective.  
 
Accessibility and usability differ significantly; therefore, accessibility is out of scope for this section. However, organizations should obviously address accessibility in their implementation plans.

### 10.1. Usability Considerations by Authenticator Type  
For the selection and implementation of an authentication system, usability should be considered across the entire lifecycle of the selected authenticator(s): enrollment and distribution, typical use, and intermittent events, being mindful of the combination of users, users’ goals, and context of use. This section discusses the usability considerations of authenticators for their typical use and intermittent events, with the goal of raising implementers’ awareness of usability considerations associated with authenticators, and possible implementation options to enhance usability.  
 
In general, a single authenticator option will likely not suffice for the entire population of users.  Therefore, whenever possible (depending on the AAL requirements), implementers should provide alternative authenticator types to users and allow users to choose between them depending on their needs. For example, the immediacy of the user’s task, a cost benefit analysis, or unfamiliarity with certain types of authenticators will affect the user’s choice of authenticator.  Users generally choose options that incur the least burden or cost at that moment in time.  For example, if a user’s task requires immediate access to an information system, a user may prefer to create a new user account and password rather than selecting an authenticator requiring more steps for access to the information system. Alternatively, users may choose to use a federated identity option (approved at the appropriate AAL) if they already have an account with an identity provider. Users may understand some authenticators better than others, and have different levels of trust based on their understanding.  
 
This section focuses on general usability considerations and possible implementations, rather than recommending specific implementation solutions. The possible implementations are provided as examples in order to encourage innovative technological approaches to address specific usability needs. Furthermore, usability considerations and their associated implementation solutions are sensitive to many factors, including context of use; these dependencies prevent a one-size-fits-all solution. For example, in the desktop computing environment, a minimum font size of 12 points may generally work for displaying user facing text, but the same font size of 12 points may force text to scroll off of a small OTP device screen, making it unusable. This is why performing a usability evaluation on the selected authenticator is a critical component of authenticator implementation; evaluations must be conducted with representative users, realistic goals and tasks, and appropriate contexts of use.  
 
Positive user authentication experience is integral to the success of an organizations’ security posture. Therefore, implementers should strive to consider authenticators from the users’ points of view. The overarching goal of usability for authentication is to minimize the authentication burden on users, and to minimize authentication friction (the number of times a user has to authenticate and the steps involved in that authentication, and the amount of information they have to keep track of). For example, one such minimization strategy may be single sign-on (SSO).

#### 10.1.1. Summary of Usability Considerations  
 
[Table 10-1](#t10-1) summarizes the usability considerations for typical usage and intermittent events for each of the eight authenticators. The sections following the table provide more detailed discussion on each authenticator. Many of the usability considerations for typical usage apply to the majority of the authenticator types, evidenced by examining the rows. The table highlights common and divergent usability characteristics across the authenticator types. Each column allows readers to easily identify the usability attributes that must be addressed for each authenticator. Depending on users’ goals and the context of use, users may value certain usability attributes more than others. Whenever possible, provide alternative authenticator types to users and allow users to choose between them. 
It is important to note that multi-factor authenticators (i.e., multi-factor OTP devices, multi-factor cryptographic software, and multi-factor cryptographic devices) also inherit usability considerations of their secondary factor. Since biometrics is only allowed as an activation factor in multi-factor authentication solutions, usability considerations for biometrics are not included in [Table 10-1](#63bSec10-Table1) and are discussed in section 10.2.

<a name="63bSec10-Table1"></a>

<div class="text-center" markdown="1">

**Table 10-1 Usability Considerations Summary by Authenticator Types**
![](sp800-63b/media/use.png)

</div>


#### 10.1.2. Memorized Secret  

**_Typical Usage_**  

Users manually input the memorized secret (commonly referred to as a password or PIN).    

Usability considerations for typical usage include:  

*  Availability of the memorized secret.
	*  	Users must remember or have their memorized secret readily available. The more items users must remember, the more memory interference will occur, and the greater likelihood of recall failure. For less frequently used passwords, these memory burdens are magnified. Having fewer memorized secrets makes it easier for users to recall the specific memorized secret needed for that particular RP.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues, for example, when users cannot recall their memorized secrets.  

*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Legibility of user facing text or text entered by users should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors. For example, legibility considerations include:
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for displaying unmasked secrets. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
		*  If possible depending on the size of the device, a minimum font size of 12 points is recommended as long as the text fits for display on the device.  


*  User experience during entry of memorized secrets.
	*  Fields for entry of memorized secrets should support copy and paste functionality. Entry fields should support memorized secrets of at least 64 characters in length; this allows the use of passphrases if desired.
	*  An option to display the memorized secret during entry should be offered to the user. Masked text entry is error-prone since users cannot see what they are typing. After the character is displayed for a time sufficient for the user to see the character, then the character can be hidden. It will take longer for users to enter memorized secrets on mobile devices (such as tablets and smartphones) than on traditional desktop computers.  Therefore, the masking delay time should take into consideration the device on which the user is entering their memorized secrets. 
	*  Time allowed for entry of memorized secrets should be adequate to enter the secret, i.e., the entry screen does not time out prematurely.
	*  Users should be given clear, meaningful and actionable feedback on entry errors. Such feedback can help reduce user confusion and frustration.  Significant usability implications will arise when users do not know that they have entered their memorized secret incorrectly, preventing users from accomplishing their tasks.  However, care should be taken to not provide so much detail that an attacker can glean information rendering the memorized secret vulnerable. 
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. The longer and more complex the memorized secrets, the greater the likelihood of user entry errors.  
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 

Depending on the implementation, form-factor constraints should be considered, as they are particularly problematic if users must enter their memorized secrets on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the keyboard). Providing larger touch areas will improve usability for entering memorized secrets on mobile devices.    


**_Intermittent Events_**  

Intermittent events with memorized secrets include, but are not limited to, reauthentication; account lock-out; throttling; number of allowed attempts exceeded; expired memorized secrets; and revocation. Additionally, users may proactively change their memorized secret.  

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. This is particularly important when memorized secrets are used as a second factor at AAL 3 where reauthentication is required at 15 minutes of user inactivity.
*  When memorized secrets are used at AAL 2 or AAL 3, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions to create and change memorized secrets. 
	*  Information on how to create and change memorized secrets should be clearly communicated to users. 
	*  Simplify memorized secret policies by implementing technical defenses, including implementing approved encryption, storing memorized secrets in a form that is resistant to offline attacks, and using blacklists. (see Section 5.1.1 for details).
		*  Memorized secret requirements such as minimum length should be clearly communicated to users. Memorized secrets SHALL be at least 8 characters in length as specified in Section 5.1.1.
		*  Users should be encouraged to make their memorized secrets as lengthy as they want, and using any characters they like, including spaces. This will allow users to create passphrases to aid memorization. Users should be allowed at least 64 characters in length to support the use of passphrases if desired.
		*  No other composition rules (complexity rules) should be imposed (mixtures of different character types, for example) on memorized secrets.
		*  Memorized secrets should not be required to be changed arbitrarily (e.g., periodically) unless there is evidence of compromise of the authenticator or a user requests a change. (Section 5.1.1)
	*  When creating memorized secrets, users should not be asked to provide specific types of information (e.g., “What is your favorite food?”, or “What was the name of your first pet?”). These types of questions are difficult for users to remember, especially because information such as personal preferences can change over time. 
	*  Users should be given clear, meaningful and actionable feedback when chosen passwords are rejected by online services. For example, when a password is rejected because it appears on a “black list” of unacceptable passwords or has been used previously used. The user should be advised that they need to select a different secret because their previous choice was commonly used.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.
	
#### 10.1.3. Look-up Secrets  

**_Typical Usage_**

Users use the authenticator (physical or electronic record) to look up the appropriate secret(s) needed to respond to a prompt from the verifier. For example, a user may be asked by the verifier to provide a specific subset of the numeric or character strings printed on a card in table format.

Usability considerations for typical usage include:

*  Availability of the look-up secret authenticator.
	*  Users must have their look-up secret authenticators readily in possession when the prompt is delivered. 
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with look-up secrets.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Legibility of text for displaying both prompts and look-up secrets should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors. For example, legibility considerations include: 
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for electronic look-up secrets; serif fonts are recommended for physical look-up secrets.
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  User experience during entry of look-up secrets.
	*  The complexity and size of the prompts should be considered. The larger the subset of secrets a user is prompted to look up, the greater the usability implications are, both the cognitive workload and physical difficulty during entry. 
	*  Entry of look-up secrets should not be masked. Masked text entry is error-prone since users cannot see what they are typing. For unmasked text entry of look-up secrets, the legibility considerations for prompts and look-up secrets described above also apply.
	*  Time allowed for entry of look-up secrets should be commensurate with the length and complexity of the look-up secrets, i.e., the entry screen does not time out prematurely. 
	*  Users should be given clear, meaningful and actionable feedback on entry errors. Such feedback can help reduce user confusion and frustration.
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. The longer and more complex the look-up secrets, the greater the likelihood of user entry errors.
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  Form-factor constraints should be considered if users must enter their look-up secrets on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the keyboard). Providing larger touch areas will improve usability for entering look up secrets on mobile devices.

	
**_Intermittent Events_**

Intermittent events with look-up secrets include, but are not limited to, reauthentication; account lock-out; throttling; number of allowed attempts exceeded; damaged, lost, or stolen look-up secret authenticator; expired look-up secrets; and revocation.  

Usability considerations for intermittent events include:

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. 
*  When look-up secrets are used at AAL 2, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

#### 10.1.4. Out of Band

**_Typical Usage_**

Out of band authentication requires that users have access to a primary and secondary communication channel. Users present the one-time authentication secret (i.e., the out of band secret) received on the secondary channel to the verifier using the primary channel for authentication. 

Usability considerations for typical usage include:

*  Availability of the out of band device.
	*  Users must have their out of band device readily in possession.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with out of band devices.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Legibility of text for displaying the authentication secret should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:  
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for the authentication secret. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  User experience during entry of authentication secret.
	*  Entry of the authentication secret should not be masked. Masked text entry is error-prone since users cannot see what they are typing. For unmasked text entry of authenticator output, the legibility considerations described above also apply.
	*  Time allowed for entry of the authentication secret should be commensurate with the length and complexity of the authentication secret, i.e., the entry screen does not time out prematurely. 
	*  Users should be given clear, meaningful and actionable feedback on entry errors. Such feedback can help reduce user confusion and frustration.
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. The longer and more complex the authentication secret, the greater the likelihood of user entry errors.
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  Users should be notified of the receipt of an authentication secret on a locked device. However, if the out of band device is locked by a user, the user will need to authenticate to the device to access the authentication secret (since the authentication secret cannot be displayed on a locked device screen). 
	*  Form-factor constraints should be considered if users must enter their authentication secrets on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the keyboard).  Providing larger touch areas will improve usability for entering authentication secrets on mobile devices.
		*  A better usability option is to offer users features that do not require text entry on mobile devices, for example, a single tap on the screen, or a copy feature so users can copy and paste the out of band secrets. 
*  Providing users such features will be particularly helpful in scenarios where the primary and secondary channels are on the same device. For example, on a smartphone, it is difficult for users to transfer the authentication secret because users must switch back and forth — potentially multiple times  —between the out of band application and the primary channel. 

**_Intermittent Events_**

Intermittent events with out of band devices include, but are not limited to, reauthentication; account lock-out; throttling; authentication secret not received; number of allowed attempts exceeded; damaged, lost, or stolen out of band devices; and revocation. Additionally, users often proactively change or upgrade their mobile devices, which would necessitate updating the linkage between the primary and secondary channels.

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. 
*  When out of band is used at AAL 2, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

#### 10.1.5. Single Factor OTP Device  

**_Typical Usage_**  

Users access the authenticator output (i.e., one-time password) generated by the single-factor OTP device. The authenticator output is typically displayed on the device and manually input by the user to the verifier, although direct electronic output from the device as input to a computer is also allowed.  

Usability considerations for typical usage include:  

*  Availability of the single-factor OTP device.
	*  Users must have their single-factor OTP device readily in possession.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with single-factor OTP devices.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Legibility of text for displaying authenticator output should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for authenticator output. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  User experience during manual entry of authenticator output.
	*  Entry of authenticator output should not be masked. Masked text entry is error-prone since users cannot see what they are typing. For unmasked text entry of authenticator output, the legibility considerations described above also apply.
	*  Time allowed for entry of authenticator output should be commensurate with the length and complexity of the authenticator output, i.e., the entry screen does not time out prematurely.
		*  Authenticator output should allow at least one minute between changes, but ideally allow users the full 2 minutes as specified in the requirement that the nonce be changed at least once every 2 minutes. Users need adequate time to enter the authenticator output (including looking back and forth between the single-factor OTP device and the entry screen).
	*  Users should be given clear, meaningful and actionable feedback on entry errors. Such feedback can help reduce user confusion and frustration.
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. The longer and more complex the authenticator output, the greater the likelihood of user entry errors.
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  Form-factor constraints should be considered if users must enter the authenticator output on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the keyboard). Providing larger touch areas will improve usability for entering the authenticator output on mobile devices.  
	*  If the single-factor OTP device supplies its output via an electronic interface such as USB, this is preferable since users do not have to manually enter the authenticator output. However, if a physical input (such as pressing a button) is required to operate, the location of the USB ports could pose usability difficulties. For example, the USB ports of some computers are located on the back of the computer that will be difficult for users to reach.
		*  Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited which may force users to unplug other USB peripherals in order to use the single-factor OTP device.  

**_Intermittent Events_**  

Intermittent events with single-factor OTP devices include, but are not limited to, reauthentication; account lock-out; throttling; number of allowed attempts exceeded; damaged, lost, or stolen single-factor OTP devices; and revocation.  

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. 
*  When single-factor OTP devices are used at AAL 2, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

#### 10.1.6. Multi-Factor OTP Device  

**_Typical Usage_**  

Users access the authenticator output (i.e., one-time password) generated by the multi-factor OTP device that requires activation through a second authentication factor. The authenticator output is typically displayed on the device and manually input by the user to the verifier, although direct electronic output from the device as input to a computer is also allowed. The second factor of authentication may be achieved through some kind of integral entry pad to enter a memorized secret, an integral biometric (e.g., fingerprint) reader or a direct computer interface (e.g., USB port). Usability considerations for the additional factor apply as well (see section 10.1.2 for Memorized Secrets and section 10.2 for Biometrics used in Multi-Factor Authenticators).  

Usability considerations for typical usage include:  

*  Availability of the multi-factor OTP device.
	*  Users must have their multi-factor OTP device readily in possession.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with multi-factor OTP devices.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Legibility of text for displaying authenticator output should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:  
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for authenticator output. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  User experience during manual entry of authenticator output.
	*  Entry of authenticator output should not be masked. Masked text entry is error-prone since users cannot see what they are typing. For unmasked text entry of authenticator output, the legibility considerations described above also apply.
	*  Time allowed for entry of authenticator output should be commensurate with the length and complexity of the authenticator output, i.e., the entry screen does not time out prematurely.
		*  Authenticator output should allow at least one minute between changes, but ideally allow users the full 2 minutes as specified in the requirement that the nonce be changed at least once every 2 minutes. Users need adequate time to enter the authenticator output (including looking back and forth between the multi-factor OTP device and the entry screen).
	*  Users should be given clear, meaningful and actionable feedback on entry errors. Such feedback can help reduce user confusion and frustration.
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. The longer and more complex the authenticator output, the greater the likelihood of user entry errors.
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  Form-factor constraints should be considered if users must unlock the multi-factor OTP device via an integral entry pad; and/or if users must enter the authenticator output on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the integral entry pad and the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the integral entry pad and the onscreen keyboard). Providing larger touch areas will improve usability for unlocking the multi-factor OTP device or entering the authenticator output on mobile devices.
	*  Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited which may force users to unplug other USB peripherals in order to use the multi-factor OTP device.  
	
**_Intermittent Events_**  

Intermittent events with multi-factor OTP devices include, but are not limited to, reauthentication; account lock-out; throttling; number of allowed attempts exceeded (for either factor); damaged, lost, or stolen multi-factor OTP devices; and revocation.  

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. This is particularly important when multi-factor OTP devices are used at AAL 3 where reauthentication is required at 15 minutes of user inactivity.
*  When multi-factor OTP devices are used at AAL 2 or AAL 3, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

#### 10.1.7. Single Factor Cryptographic Device  

**_Typical Usage_**
Users prove possession of the single-factor cryptographic device in order to authenticate.  

Usability considerations for typical usage include:  

*  Availability of the single-factor cryptographic device.
	*  Users must have their single-factor cryptographic device readily in possession.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with single-factor cryptographic devices.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Text legibility should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:  
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for authenticator output. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  If a physical input (such as pressing a button) is required to operate the single-factor cryptographic device, this could pose usability difficulties. For example, the USB ports of some computers are located on the back of the computer that will be difficult for users to reach. 
		*  Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited which may force users to unplug other USB peripherals in order to use the single-factor cryptographic device.  
		

**_Intermittent Events_**  

Intermittent events with single-factor cryptographic devices include, but are not limited to, reauthentication; damaged, lost, or stolen single-factor cryptographic devices; and revocation.  

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. This is particularly important when single-factor cryptographic devices are used as part of a multi-factor solution at AAL 3 where reauthentication is required at 15 minutes of user inactivity.
*  When single-factor cryptographic devices are used at AAL 2 or AAL 3, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

#### 10.1.8. Multi-Factor Cryptographic Software   

**_Typical Usage_**  

In order to authenticate, users prove possession and control of the cryptographic key stored on disk or some other “soft” media that requires activation. The activation is through the input of a second authentication factor, either a memorized secret or a biometric; usability considerations for the additional factor apply as well (see section 10.1.2 for Memorized Secrets and section 10.2 for Biometrics used in Multi-Factor Authenticators).  

Usability considerations for typical usage include:  

*  Characteristics of user facing text. 
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Text legibility should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:  
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for authenticator output. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  All cryptographic keys should be given appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users being faced with multiple similarly and ambiguously named cryptographic keys. Selection among multiple cryptographic keys on smaller mobile devices (such as smartphones) may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.
	*  Form-factor constraints should be considered if users must unlock the multi-factor cryptographic software on mobile devices (such as tablets and smartphones). Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the onscreen keyboard, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the keyboard).  

**_Intermittent Events_**  

Intermittent events with multi-factor cryptographic software include, but are not limited to, reauthentication; account lock-out; number of allowed attempts exceeded ; non-functional multi-factor cryptographic software; and revocation.  

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. 
*  When multi-factor cryptographic software is used at AAL 2, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.  

#### 10.1.9. Multi-Factor Cryptographic Device  

**_Typical Usage_**  

In order to authenticate, users prove possession of the multi-factor cryptographic device and control of the protected cryptographic key. The device is activated by a second authentication factor, either a memorized secret or a biometric; usability considerations for the additional factor apply as well (see section 10.1.2 for Memorized Secrets and section 10.2 for Biometrics used in Multi-Factor Authenticators).

Usability considerations for typical usage include:

*  Availability of the multi-factor cryptographic device.
	*  Users must have their multi-factor cryptographic device readily in possession.
	*  Whenever possible (depending on the AAL requirements), users should be provided with alternative authentication options. This will allow users to choose their preferred option given their context, goals, and tasks (for example, based on the frequency and immediacy of the task). Alternative authentication options will help address availability issues with multi-factor cryptographic devices.
*  Characteristics of user facing text.
	*  Any user facing text (e.g., instructions, prompts, notifications, error messages) should be written in plain language for the intended audience. Avoid the use of technical jargon and write for a 6th to 8th grade literacy level.
	*  Text legibility should be considered, such as font style, size, color, and contrast with surrounding background. Font legibility is important because users have different levels of visual acuity. Illegible text will contribute to user entry errors.  For example, legibility considerations include:  
		*  The highest contrast is black on white.
		*  Sans serif font styles are recommended for authenticator output. 
		*  Fonts that do not clearly distinguish between easily confusable characters (such as the capital letter “O” and the number zero “0”) are not recommended for use.
*  Depending on the implementation, the following are additional usability considerations for implementers:
	*  Ideally, the multi-factor cryptographic devices should not require a hardware connection to use. However, if using a hardware connection, the multi-factor cryptographic device should not require users to keep the device connected. Users may forget to disconnect the multi-factor cryptographic device when they are done with it (such as forgetting a smartcard in the smartcard reader and walking away from the computer).
		*  Users need to be informed regarding whether the multi-factor cryptographic device is required to stay connected or not. 
	*  All cryptographic keys should be given appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users being faced with multiple similarly and ambiguously named cryptographic keys. Selection among multiple cryptographic keys on smaller mobile devices (such as smartphones) may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.
	*  Form-factor constraints should be considered if users must unlock the multi-factor cryptographic device via an integral entry pad. Typing on small devices is significantly more error prone and time consuming than typing on a traditional keyboard for a desktop computer. The smaller the integral entry pad, the more difficult it is to type. This is due to the size of the input mechanism (i.e., a finger) relative to the size of the target (i.e., a single key on the integral entry pad). Providing larger touch areas will improve usability for unlocking the multi-factor cryptographic device.
	*  Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited which may force users to unplug other USB peripherals in order to use the multi-factor cryptographic device.  

**_Intermittent Events_**  

Intermittent events with multi-factor cryptographic devices include, but are not limited to, reauthentication; account lock-out; throttling; number of allowed attempts exceeded; damaged, lost, or stolen multi-factor cryptographic devices; and revocation.

Usability considerations for intermittent events include:  

*  To prevent undesired reauthentication events due to user inactivity, users should be prompted to cause activity just before (e.g., 2 minutes before) the inactivity timeout would otherwise occur. This is particularly important when multi-factor cryptographic devices are used at AAL 3 where reauthentication is required at 15 minutes of user inactivity.
*  When multi-factor cryptographic devices are used at AAL 2 or AAL 3, users should be prompted and given adequate time (e.g., 1 hour) to save their work prior to the mandatory reauthentication event required at least once every 12 hours, regardless of user activity.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.

### 10.2. Usability Considerations of Biometrics   

For multi-factor authenticators, biometrics can be used as an additional factor.  Therefore, in contrast to the previous usability considerations for authenticator types, this section provides only a high-level overview of general usability considerations for biometrics. For a more detailed discussion of biometric usability, see Usability & Biometrics, Ensuring Successful Biometric Systems, <http://www.nist.gov/customcf/get_pdf.cfm?pub_id=152184>.

Although there are additional biometric modalities, the following three biometric modalities are more commonly used for authentication: fingerprint, face and iris.  

**_Typical Usage_**  

*  For all modalities, user familiarity and practice with the device improves performance. 
*  Device affordances (properties of an object that allow a user to perform an action), feedback, and clear instructions are critical factors to a user’s success with the biometric device. For example, clear instructions describing user actions required for liveness detection should be provided to users.
*  Ideally, users should be given the choice to select the modality with which they are most comfortable for their second authentication factor. The user population may be more comfortable with and accepting of some biometric modalities than others. For example, the use of iris technology is not as widely accepted or used as are fingerprints and face.  
*  User experience with biometrics as an activation factor.
	*  Number of allowed attempts should be considered – allow minimum of 10 attempts. 
	*  Users should be given clear and meaningful feedback on number of remaining allowed attempts. For example, for rate limiting (throttling), users should be informed of the time period they have to wait until next attempt. Such feedback can help reduce user confusion and frustration. 
*  Fingerprint Usability Considerations:
	*  Users must remember which finger(s) they used for initial enrollment.
	*  The amount of moisture on the finger(s) affects the sensor’s ability for successful capture.
	*  Additional factors also influence fingerprint capture quality, including age, gender, and occupation (e.g., users handling chemicals or who work extensively with their hands may have degraded friction ridges). 
*  Face Usability Considerations:
	*  Users must remember whether they wore any artifacts, such as glasses, during enrollment because it affects facial recognition accuracy.
	*  Differences in environmental lighting conditions can affect facial recognition accuracy.
	*  Facial poses affect facial recognition accuracy (e.g., smiling versus neutral expression).
*  Iris Usability Considerations:
	*  Users wearing colored contacts have the potential to affect the iris recognition accuracy. 
	*  Users who have had eye surgery may need to re-enroll post-surgery.
	*  Differences in environmental lighting conditions can affect iris recognition accuracy, especially for certain iris colors.  

**_Intermittent Events_**  

Since biometrics are only permitted as a second factor in a multi-factor authentication scenario, usability considerations for intermittent events with the primary factor still apply.  Intermittent events with the use of biometrics include, but are not limited to, the following that may affect recognition accuracy:  

*  If a user injures his/her enrolled finger(s), fingerprint recognition may not work. Fingerprint authentication will be difficult for users with degraded fingerprints. 
*  The time elapsed between the time of facial recognition for authentication and the time of the initial enrollment can affect the recognition accuracy as a user’s face changes naturally over time. A user’s weight changes (e.g., weight gain or loss) may also be a factor.
*  Iris recognition may not work for people who have had eye surgery unless they re-enroll.  

Across all biometric modalities, usability considerations for intermittent events include:  

*  For all modalities, an alternative authentication method must be available and functioning. In cases where biometrics do not work, users must be allowed to use a memorized secret as an alternative second factor.
*  Provisions for technical assistance.
	*  Information on how and where to acquire technical assistance should be clearly communicated to users. For example, provide users information such as a link to online self-service feature and a phone number for help desk support. Ideally, sufficient information should be provided to enable users to recover from intermittent events on their own without outside intervention.
	*  Users need to be informed regarding factors that may affect the sensitivity of the biometric sensor (e.g., cleanliness of the sensor).
