<a name="appA"></a>

## Appendix A: Strength of Memorized Secrets

*This appendix is non-normative.*

### A.1 Introduction

Despite widespread frustration with the use of passwords from both a usability and security standpoint, they remain a very widely used form of authentication. Humans, however, have only a limited ability to memorize complex, arbitrary secrets, so they often choose passwords that can be easily guessed. To address the resultant security concerns, online services have introduced rules in an effort to increase the complexity of these memorized secrets. The most notable form of these is composition rules, which require the user to choose passwords constructed using a mix of character types, such as at least one digit, uppercase letter, and symbol. However, analyses of breached password databases reveals that the benefit of such rules is not nearly as significant as initially thought, although the impact on usability and memorability is severe.

Complexity of user-chosen passwords has often been characterized using the information theory concept of entropy[ref]. While entropy can be readily calculated for data having deterministic distribution functions, estimating the entropy for user-chosen passwords is difficult and past efforts to do so have not been particularly accurate. For this reason, a different and somewhat simpler approach, based primarily on password length, is presented herein.

It should be noted that there are many attacks associated with the use of passwords that are not affected by password complexity. Keystroke logging, phishing, and social engineering attacks are equally effective on complex passwords as simple ones. Observation, “shoulder-surfing” attacks are only slightly more difficult for complex passwords. These attacks are outside the scope of this Appendix.

### A.2 Length

Password length has been found to be the primary factor in characterizing password strength. Passwords that are too short yield to brute force attacks as well as to dictionary attacks using words and commonly chosen passwords.

The minimum password length that should be required depends to a large extent on the threat model being addressed. Online attacks where the attacker attempts to log in by guessing the password can be readily addressed by throttling the rate of login attempts permitted. In order to prevent an attacker (or a claimant with poor typing skills) from easily inflicting a denial-of-service attack on the subscriber by making many incorrect guesses, passwords need to be complex enough that throttling does not occur after a modest number of erroneous attempts, but does occur before there is a significant chance of a successful guess.

Offline attacks are sometimes possible when one or more hashed passwords is obtained by the attacker through a database breach. The ability of the attacker to determine one or more users’ passwords depends on the way in which the password is stored. Commonly, passwords are salted with a random value and hashed, preferably using a computationally expensive algorithm. Even with such measures, the current ability of attackers to compute many billions of hashes per second with no throttling requires passwords to be orders of magnitude more complex to resist such attacks.

Users should be encouraged to make their passwords as lengthy as they want. Since the size of a hashed password is independent of its length, there is no reason not to permit the use of lengthy passwords (or pass phrases) if the user wishes.

### A.3 Complexity

As noted above, composition rules are commonly used in an attempt to decrease the guessability of user-chosen passwords. Research has shown, however, that users respond in very predictable ways to the requirements imposed by composition rules. For example, a user that might have chosen “password” as their password would be relatively likely to choose “Password1” if required to include an uppercase letter and a number, or “Password1!” if a symbol is also required.

Users also express frustration when attempts to create complex passwords are rejected by online services. Many services reject passwords with spaces and various special characters. In some cases the special characters that are not accepted might be an effort to avoid attacks like SQL Injection that depend on those characters. But a properly hashed password would not be sent intact to a database in any case, so such precautions are unnecessary. Users should also be able to include space characters to allow the use of phrases. Spaces themselves, however, add little to the complexity of passwords and may introduce usability issues (e.g., the undetected use of two spaces rather than one), so it may be beneficial to remove spaces in typed passwords prior to verification.

Users’ password choices are very predictable, so attackers are likely to try guess passwords that have been successful in the past. These include dictionary words and passwords from previous breaches, such as the “Password1!” example above. For this reason, it is recommended that passwords chosen by users be compared against a “black list” of unacceptable passwords. This list should include passwords from previous breach corpuses, dictionary words, and specific words (such as the name of the service itself) that users are likely to choose. Since user choice of passwords will also be governed by a minimum length requirement, this dictionary need only include entries meeting that requirement.
