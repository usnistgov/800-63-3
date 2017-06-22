<a name="sec10"></a>

<div class="breaker"></div>

## 10 Usability Considerations

_This section is informative._

[ISO/IEC 9241-11](#ISO9241) defines usability as the "extent to which a product can be used by specified users to achieve specified goals with effectiveness, efficiency and satisfaction in a specified context of use." This definition focuses on users, their goals, and the context of use as key elements necessary for achieving effectiveness, efficiency, and satisfaction. A holistic approach that accounts for these key elements is necessary to achieve usability.

A user's goal for accessing an information system is to perform an intended task. Authentication is the function that enables this goal. However, from the user's perspective, authentication stands between them and their intended task. Effective design and implementation of authentication makes it easy to do the right thing, hard to do the wrong thing, and easy to recover when the wrong thing happens.

Organizations need to be cognizant of the overall implications of their stakeholders' entire digital authentication ecosystem. Users often employ one or more authenticator, each for a different RP. They then struggle to remember passwords, to recall which authenticator goes with which RP, and to carry multiple physical authentication devices. Evaluating the usability of authentication is critical, as poor usability often results in coping mechanisms and unintended work-arounds that can ultimately degrade the effectiveness of security controls.

Integrating usability into the development process can lead to authentication solutions that are secure and usable while still addressing users' authentication needs and organizations' business goals.

The impact of usability across digital systems needs to be considered as part of the risk assessment when deciding on the appropriate AAL. Authenticators with a higher AAL sometimes offer better usability and should be allowed for use for lower AAL applications.

Leveraging federation for authentication can alleviate many of the usability issues, though such an approach has its own tradeoffs, as discussed in [SP 800-63C](sp800-63c.html).

This section provides general usability considerations and possible implementations, but does not recommend specific solutions. The implementations mentioned are examples to encourage innovative technological approaches to address specific usability needs. Further, usability considerations and their implementations are sensitive to many factors that prevent a one-size-fits-all solution. For example, a font size that works in the desktop computing environment may force text to scroll off of a small OTP device screen. Performing a usability evaluation on the selected authenticator is a critical component of implementation. It is important to conduct evaluations with representative users, realistic goals and tasks, and appropriate contexts of use.

**ASSUMPTIONS**

In this section, the term "users" means "claimants" or "subscribers."

Guidelines and considerations are described from the users' perspective.

Accessibility differs from usability and is out of scope for this document. [Section 508](#Section508) was enacted to eliminate barriers in information technology and require federal agencies to make their online public content accessible to people with disabilities. Refer to Section 508 law and standards for accessibility guidance.

### <a name="usabilitycommon"></a> 10.1 Usability Considerations Common to Authenticators
When selecting and implementing an authentication system, consider usability across the entire lifecycle of the selected authenticators (e.g., typical use and intermittent events), while being mindful of the combination of users, their goals, and context of use.

A single authenticator type usually does not suffice for the entire user population. Therefore, whenever possible — based on AAL requirements — CSPs should support alternative authenticator types and allow users to choose based on their needs. Task immediacy, perceived cost benefit tradeoffs, and unfamiliarity with certain authenticators often impact choice. Users tend to choose options that incur the least burden or cost at that moment. For example, if a task requires immediate access to an information system, a user may prefer to create a new account and password rather than select an authenticator requiring more steps. Alternatively, users may choose a federated identity option — approved at the appropriate AAL — if they already have an account with an identity provider. Users may understand some authenticators better than others, and have different levels of trust based on their understanding and experience.

Positive user authentication experiences are integral to the success of an organization achieving desired business outcomes. Therefore, they should strive to consider authenticators from the users' perspective. The overarching authentication usability goal is to minimize user burden and authentication friction (e.g., the number of times a user has to authenticate, the steps involved, and the amount of information he or she has to track). Single sign-on exemplifies one such minimization strategy.

Usability considerations applicable to most authenticators are described below. Subsequent sections describe usability considerations specific to a particular authenticator.

Usability considerations for typical usage of all authenticators include:

* Provide information on the use and maintenance of the authenticator, e.g., what to do if the authenticator is lost or stolen, and instructions for use — especially if there are different requirements for first-time use or initialization.

* Authenticator availability should also be considered as users will need to remember to have their authenticator readily available. Consider the need for alternate authentication options to protect against loss, damage, or other negative impacts to the original authenticator.

* Whenever possible, based on AAL requirements, users should be provided with alternate authentication options. This allows users to choose an authenticator based on their context, goals, and tasks (e.g., the frequency and immediacy of the task). Alternate authentication options also help address availability issues that may occur with a particular authenticator.

* Characteristics of user-facing text:
  * Write user-facing text (e.g., instructions, prompts, notifications, error messages) in plain language for the intended audience. Avoid technical jargon and, typically, write for a 6th to 8th grade literacy level.
  * Consider the legibility of user-facing and user-entered text, including font style, size, color, and contrast with surrounding background. Illegible text contributes to user entry errors. To enhance legibility, consider the use of:
    * High contrast. The highest contrast is black on white.
    * Sans serif fonts for electronic displays. Serif fonts for printed materials.
    * Fonts that clearly distinguish between easily confusable characters (e.g., the capital letter "O" and the number "0").
    * A minimum font size of 12 points as long as the text fits for display on the device.

* User experience during authenticator entry:
  * Offer the option to display text during entry, as masked text entry is error-prone. Once a given character is displayed long enough for the user to see, it can be hidden. Consider the device when determining masking delay time, as it takes longer to enter memorized secrets on mobile devices (e.g., tablets and smartphones) than on traditional desktop computers. Ensure masking delay durations are consistent with user needs.
  * Ensure the time allowed for text entry is adequate (i.e., the entry screen does not time out prematurely). Ensure allowed text entry times are consistent with user needs.
  * Provide clear, meaningful and actionable feedback on entry errors to reduce user confusion and frustration. Significant usability implications arise when users do not know they have entered text incorrectly.
  * Allow at least 10 entry attempts for authenticators requiring the entry of the authenticator output by the user. The longer and more complex the entry text, the greater the likelihood of user entry errors.
  * Provide clear, meaningful feedback on the number of remaining allowed attempts. For rate limiting (i.e., throttling), inform users how long they have to wait until the next attempt to reduce confusion and frustration.

* Minimize the impact of form-factor constraints, such as limited touch and display areas on mobile devices:
  * Larger touch areas improve usability for text entry since typing on small devices is significantly more error prone and time consuming than typing on a full-size keyboard. The smaller the onscreen keyboard, the more difficult it is to type, due to the size of the input mechanism (e.g., a finger) relative to the size of the on-screen target.
  * Follow good user interface and information design for small displays.

Intermittent events include events such as reauthentication, account lock-out, expiration, revocation, damage, loss, theft, and non-functional software.

Usability considerations for intermittent events across authenticator types include:

* To prevent users from needing to reauthenticate due to user inactivity, prompt users in order to trigger activity just before (e.g., 2 minutes) an inactivity timeout would otherwise occur.

* Prompt users with adequate time (e.g., 1 hour) to save their work before the fixed periodic reauthentication event required regardless of user activity.

* Clearly communicate how and where to acquire technical assistance. For example, provide users with information such as a link to an online self-service feature, chat sessions or a phone number for help desk support. Ideally, sufficient information can be provided to enable users to recover from intermittent events on their own without outside intervention.

### 10.2 Usability Considerations by Authenticator Type
In addition to the previously described general usability considerations applicable to most authenticators ([Section 10.1](#usabilitycommon)), the following sections describe other usability considerations specific to particular authenticator types.

#### <a name="memorizedsecrets"></a> 10.2.1 Memorized Secrets
**_Typical Usage_**

Users manually input the memorized secret (commonly referred to as a password or PIN).

Usability considerations for typical usage include:

* Memorability of the memorized secret.
  * The likelihood of recall failure increases as there are more items for users to remember. With fewer memorized secrets, users can more easily recall the specific memorized secret needed for a particular RP.
  * The memory burden is greater for a less frequently used password.

* User experience during entry of the memorized secret.
  * Support copy and paste functionality in fields for entering memorized secrets, including passphrases.

**_Intermittent Events_**

Usability considerations for intermittent events include:

* When users create and change memorized secrets:
  * Clearly communicate information on how to create and change memorized secrets.
  * Clearly communicate memorized secret requirements, as specified in [Section 5.1.1](#reqauthtype).
  * Allow at least 64 characters in length to support the use of passphrases. Encourage users to make memorized secrets as lengthy as they want, using any characters they like (including spaces), thus aiding memorization.
  * Do not impose other composition rules (e.g. mixtures of different character types) on memorized secrets.
  * Do not require that memorized secrets be changed arbitrarily (e.g., periodically) unless there is a user request or evidence of authenticator compromise. (See [Section 5.1.1](#reqauthtype) for additional information).

* Provide clear, meaningful and actionable feedback when chosen passwords are rejected (e.g., when it appears on a "black list" of unacceptable passwords or has been used previously).

#### 10.2.2 Look-Up Secrets
**_Typical Usage_**

Users use the authenticator — printed or electronic — to look up the appropriate secret(s) needed to respond to a verifier's prompt. For example, a user may be asked to provide a specific subset of the numeric or character strings printed on a card in table format.

Usability considerations for typical usage include:

* User experience during entry of look-up secrets.
  * Consider the prompts' complexity and size. The larger the subset of secrets a user is prompted to look up, the greater the usability implications. Both the cognitive workload and physical difficulty for entry should be taken into account when selecting the quantity and complexity of look-up secrets for authentication.

#### 10.2.3 Out-of-Band
**_Typical Usage_**

Out-of-band authentication requires users have access to a primary and secondary communication channel.

Usability considerations for typical usage:

* Notify users of the receipt of a secret on a locked device. However, if the out of band device is locked, authentication to the device should be required to access the secret.

* Depending on the implementation, consider form-factor constraints as they are particularly problematic when users must enter text on mobile devices. Providing larger touch areas will improve usability for entering secrets on mobile devices.

* A better usability option is to offer features that do not require text entry on mobile devices (e.g., a single tap on the screen, or a copy feature so users can copy and paste out-of-band secrets). Providing users such features is particularly helpful when the primary and secondary channels are on the same device. For example, it is difficult for users to transfer the authentication secret on a smartphone because they must switch back and forth—potentially multiple times—between the out of band application and the primary channel.

#### 10.2.4 Single-Factor OTP Device
**_Typical Usage_**

Users access the OTP generated by the single-factor OTP device. The authenticator output is typically displayed on the device and the user enters it for the verifier.

Usability considerations for typical usage include:

* Authenticator output allows at least one minute between changes, but ideally allows users the full two minutes as specified in [Section 5.1.4.1](#sfotpa). Users need adequate time to enter the authenticator output (including looking back and forth between the single-factor OTP device and the entry screen).

* Depending on the implementation, the following are additional usability considerations for implementers:
  * If the single-factor OTP device supplies its output via an electronic interface (e.g, USB) this is preferable since users do not have to manually enter the authenticator output. However, if a physical input (e.g., pressing a button) is required to operate, the location of the USB ports could pose usability difficulties. For example, the USB ports of some computers are located on the back of the computer and will be difficult for users to reach.
  * Limited availability of a direct computer interface such as a USB port could pose usability difficulties. For example, the number of USB ports on laptop computers is often very limited. This may force users to unplug other USB peripherals in order to use the single-factor OTP device.

#### 10.2.5 Multi-Factor OTP Device
**_Typical Usage_**

Users access the OTP generated by the multi-factor OTP device through a second authentication factor. The OTP is typically displayed on the device and the user manually enters it for the verifier. The second authentication factor may be achieved through some kind of integral entry pad to enter a memorized secret, an integral biometric (e.g., fingerprint) reader, or a direct computer interface (e.g., USB port). Usability considerations for the additional factor apply as well — see [Section 10.2.1](#memorizedsecrets) for memorized secrets and [Section 10.4](#biomusability) for biometrics used in multi-factor authenticators.

Usability considerations for typical usage include:

* User experience during manual entry of the authenticator output.
  * For time-based OTP, provide a grace period in addition to the time during which the OTP is displayed. Users need adequate time to enter the authenticator output, including looking back and forth between the multi-factor OTP device and the entry screen.
  * Consider form-factor constraints if users must unlock the multi-factor OTP device via an integral entry pad or enter the authenticator output on mobile devices. Typing on small devices is significantly more error prone and time-consuming than typing on a traditional keyboard. The smaller the integral entry pad and onscreen keyboard, the more difficult it is to type. Providing larger touch areas improves usability for unlocking the multi-factor OTP device or entering the authenticator output on mobile devices.
  * Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the multi-factor OTP device.

#### 10.2.6 Single-Factor Cryptographic Software
**_Typical Usage_**

Users authenticate by proving possession and control of the cryptographic software key.

Usability considerations for typical usage include:

* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users from having to deal with multiple similarly- and ambiguously-named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.

#### 10.2.7 Single-Factor Cryptographic Device
**_Typical Usage_**

Users authenticate by proving possession of the single-factor cryptographic device.

Usability considerations for typical usage include:

* Requiring a physical input (e.g., pressing a button) to operate the single-factor cryptographic device could pose usability difficulties. For example, some USB ports are located on the back of computers, making it difficult for users to reach.

* Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the single-factor cryptographic device.

#### 10.2.8 Multi-Factor Cryptographic Software
**_Typical Usage_**

In order to authenticate, users prove possession and control of the cryptographic key stored on disk or some other "soft" media that requires activation. The activation is through the input of a second authentication factor, either a memorized secret or a biometric. Usability considerations for the additional factor apply as well — see [Section 10.2.1](#memorizedsecrets) for memorized secrets and [Section 10.4](#biomusability) for biometrics used in multi-factor authenticators.

Usability considerations for typical usage include:

* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users from having to deal with multiple similarly- and ambiguously-named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.

#### 10.2.9 Multi-Factor Cryptographic Device
**_Typical Usage_**

Users authenticate by proving possession of the multi-factor cryptographic device and control of the protected cryptographic key. The device is activated by a second authentication factor, either a memorized secret or a biometric. Usability considerations for the additional factor apply as well — see [Section 10.2.1](#memorizedsecrets) for memorized secrets and [Section 10.4](#biomusability) for biometrics used in multi-factor authenticators.

Usability considerations for typical usage include:

* Do not require users to keep multi-factor cryptographic devices connected following authentication. Users may forget to disconnect the multi-factor cryptographic device when they are done with it (e.g., forgetting a smartcard in the smartcard reader and walking away from the computer).
  * Users need to be informed regarding whether the multi-factor cryptographic device is required to stay connected or not.

* Give cryptographic keys appropriately descriptive names that are meaningful to users since users have to recognize and recall which cryptographic key to use for which authentication task. This prevents users being faced with multiple similarly and ambiguously named cryptographic keys. Selecting from multiple cryptographic keys on smaller mobile devices (such as smartphones) may be particularly problematic if the names of the cryptographic keys are shortened due to reduced screen size.

* Limited availability of a direct computer interface like a USB port could pose usability difficulties. For example, laptop computers often have a limited number of USB ports, which may force users to unplug other USB peripherals to use the multi-factor cryptographic device.

### 10.3 Summary of Usability Considerations
[Table 10-1](#t10-1) summarizes the usability considerations for typical usage and intermittent events for each authenticator type. Many of the usability considerations for typical usage apply to most of the authenticator types, as demonstrated in the rows. The table highlights common and divergent usability characteristics across the authenticator types. Each column allows readers to easily identify the usability attributes to address for each authenticator. Depending on users' goals and context of use, certain attributes may be valued over others. Whenever possible, provide alternative authenticator types and allow users to choose between them.

Multi-factor authenticators (e.g., multi-factor OTP devices, multi-factor cryptographic software, and multi-factor cryptographic devices) also inherit their secondary factor's usability considerations. As biometrics are only allowed as an activation factor in multi-factor authentication solutions, usability considerations for biometrics are not included in Table 10-1 and are discussed in Section 10.4.

<a name="t10-1"></a>

<div class="text-center" markdown="1">

**Table 10-1 Usability Considerations Summary by Authenticator Type**

![](sp800-63b/media/use.png)

</div>

### <a name="biomusability"></a> 10.4 Biometrics Usability Considerations
This section provides a high-level overview of general usability considerations for biometrics. A more detailed discussion of biometric usability can be found in *Usability & Biometrics, Ensuring Successful Biometric Systems* [NIST Usability](#use-and-bio).

Although there are other biometric modalities, the following three biometric modalities are more commonly used for authentication: fingerprint, face and iris.

**_Typical Usage_**

* For all modalities, user familiarity and practice with the device improves performance.

* Device affordances (i.e., properties of a device that allow a user to perform an action), feedback, and clear instructions are critical to a user's success with the biometric device. For example, provide clear instructions on the required actions for liveness detection.

* Ideally, users can select the modality they are most comfortable with for their second authentication factor. The user population may be more comfortable and familiar with — and accepting of — some biometric modalities than others.

* User experience with biometrics as an activation factor.
  * Provide clear, meaningful feedback on the number of remaining allowed attempts. For example, for rate limiting (i.e., throttling), inform users of the time period they have to wait until next attempt to reduce user confusion and frustration.

* Fingerprint Usability Considerations:
  * Users have to remember which finger(s) they used for initial enrollment.
  * The amount of moisture on the finger(s) affects the sensor's ability for successful capture.
  * Additional factors influencing fingerprint capture quality include age, gender, and occupation (e.g., users handling chemicals or working extensively with their hands may have degraded friction ridges).

* Face Usability Considerations:
  * Users have to remember whether they wore any artifacts (e.g., glasses) during enrollment because it affects facial recognition accuracy.
  * Differences in environmental lighting conditions can affect facial recognition accuracy.
  * Facial expressions affect facial recognition accuracy (e.g., smiling versus neutral expression).
  * Facial poses affect facial recognition accuracy (e.g., looking down or away from the camera).

* Iris Usability Considerations:
  * Wearing colored contacts may affect the iris recognition accuracy.
  * Users who have had eye surgery may need to re-enroll post-surgery.
  * Differences in environmental lighting conditions can affect iris recognition accuracy, especially for certain iris colors.

**_Intermittent Events_**

As biometrics are only permitted as a second factor for multi-factor authentication, usability considerations for intermittent events with the primary factor still apply. Intermittent events with biometrics use include, but are not limited to, the following, which may affect recognition accuracy:

* If users injure their enrolled finger(s), fingerprint recognition may not work. Fingerprint authentication will be difficult for users with degraded fingerprints.
* The time elapsed between the time of facial recognition for authentication and the time of the initial enrollment can affect recognition accuracy as a user's face changes naturally over time. A user's weight change may also be a factor.
* Iris recognition may not work for people who had eye surgery, unless they re-enroll.

Across all biometric modalities, usability considerations for intermittent events include:

* An alternative authentication method must be available and functioning. In cases where biometrics do not work, allow users to use a memorized secret as an alternative second factor.
* Provisions for technical assistance:
  * Clearly communicate information on how and where to acquire technical assistance. For example, provide users information such as a link to an online self-service feature and a phone number for help desk support. Ideally, provide sufficient information to enable users to recover from intermittent events on their own without outside intervention.
  * Inform users of factors that may affect the sensitivity of the biometric sensor (e.g., cleanliness of the sensor).
