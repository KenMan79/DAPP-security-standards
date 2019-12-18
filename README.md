# DAPP Security Standards

The purpose of this repo is to highlight the security issues as well as provide DApp developers with the necessary information to launch their project securely or mitigate any issues that may occur.

Feel free to contact me if you have any questions or feedback dexaran@callisto.network / dexaran@ethereumclassic.org 

# General notes

[Nothing can be absolutely secure](https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=922194) (general paradigm of system security engineering). 

In this particular case the paradigm translates into:

>There is no single method of proving safety of a system. The system must rely on multiple methods of security enhancements. The more security enhancement practices are applied - the better.


There is no single universal method that is sufficient to ensure software security. None of formal verification, security audits, development of better programming languages, upgradeability of smart-contracts or any other measures can guarantee absolute safety of your software implementation. **Statement that a particular party is offering services that can guarantee complete safety of DApp is either a myth, a lie or a marketing move.**

A combination of security improvement methods and measures can significantly reduce the risk of DApp being hacked. Each security improvement strategy introduces a new layer of safety and it is strongly advised to rely on multiple "security layers". It may be even better to focus on system [fault-tolerance](https://en.wikipedia.org/wiki/Software_fault_tolerance) instead of trying to make it unhackable.

In the case of DApp, **fault tolerance** is the ability of DApp being fixed/debugged in case of detection of malicious activity.

When it comes to evaluating security enhancement methods it proves that [security audit](https://en.wikipedia.org/wiki/Information_technology_security_audit) is one of the most efficient methods albeit the most expensive one.

# Security improvement practices

Here I'd like to highlight the most common measures that a DApp developer must consider to improve the security aspect of the DApp:

- **Develop open-source applications.** Making your application open-source increases the level of security and ensures the ability to perform such security enhancement methods as "bug bounty" which further increases the overall level of system safety. There is a misconception that hiding the source codes of the system from public can prevent flaws and vulnerabilities from being exploited. This misconception is known as [security through obscurity](https://en.wikipedia.org/wiki/Security_through_obscurity).

- **Security audit.** Security audit is a peer review of the smart-contract code performed by a third party expert or a team of security experts. This proves to be one of the most efficient methods as it can cover any type of logical and application-specific mistakes. There are specialized companies offering security auditing services for smart-contract developers.

- **Bug bounty.** Bug bounty is a practice of publishing the source codes for community review and offering rewards for reporting the found vulnerabilities or flaws. Bug bounty is also a very efficient method of ensuring the system security if handled properly. The reward for finding a vulnerability must match the amount of work performed by the reviewer as well as match the level of harm that could be inflicted in case of reviewer deciding to exploit the vulnerability instead of reporting it.

- **Automated anomaly detection.** In case of DAPP the [anomaly detection](http://ids.cs.columbia.edu/sites/default/files/34880014.pdf) is a special feature of the smart-contract that automatically triggers countermeasures/alarms when unwanted behavior occurs in the smart-contract. In some cases it is possible to predict what kind of behavior is malicious and implement a "detection feature" and "contract disabling trigger". For example if you have developed a  casino and one player is winning 30 times in a row then it is obvious that he may be cheating and further investigation is necessary. It may be worth to disable the smart-contract thus disallowing the malicious player to drain it in case he is exploiting a vulnerability of the contract. The anomaly detection may be implemented as a kind of [watchdog service](https://www.webopedia.com/TERM/W/watchdog.html) and operated by third party offchain service without a need to implement it in smart-contract logic. The effectiveness of this method depends on the ability of smart-contract developer to determine which kind of activity should be considered "anomaly". This method is very good for preventing application-specific faults but it is not sufficient on its own. This practice should be used in combination with other security improvement measures.

- **Manual testing and testnet deployment.** Test your software. Test it more. Let smart-contract developers and all team members try the system with their own hands. Publish a version of the system at testnet and let community use it for a couple of months before the final release. This will definitely reduce the risk of vulnerabilities arising in the final version of the software. This is not a self-sufficient method of security improvement but it is cheap and efficient enough.

- **Automated testing.** Automated testing or [unit testing](https://en.wikipedia.org/wiki/Unit_testing) involves the development of a special software that will interact with the DApp for the sake of detection of any flaws and ensuring the correctness of DApps responses on any type of input. The effectiveness of this approach obviously depends on the correctness of the implementation of the testing software. In general automated tests are an auxiliary tool that can  reduce the overhead of security auditors/community reviewers/software testers. Automated testing can cover the routinuous cases of general software utility but it proves to be bad when it comes to identifying logical mistakes/ business model flaws or any other application-specific kind of potential threats. Automated tests are not a reliable measure of ensuring the overall system safety. These must be combined and used alongside other security enhancement procedures.

- **Formal verification.** [Formal verification](https://en.wikipedia.org/wiki/Formal_verification) much like the automated testing is an additional method of reducing the overhead for software testers/auditors/developers. This can be helpful in some cases but formal verification is not a self-sufficient method of ensuring system safety and must not be relied on.

- **Follow well-known programming practices.** Security is not a new area of programming and there are plenty of well-known mass-adopted methods and practices that are time proven already. **Adhere to coding standards. Comment your code.** It is strongly recommended for any contract developer to read the description of coding standards of the platform they intend to use. It is also recommended to read the respectable coding standards adopted by large-scale programming communities such as [GNU Coding Standard](https://www.gnu.org/prep/standards/standards.html). This is very important and it is not a matter of preferences! The coding standards are intended to make the logic represented by code pieces as straightforward as possible which greatly improves the ability of an auditor/software tester/code reviewer to identify and report a system flaw. The more readability of your code the better.

- **Make your application modular if possible.** Following this method of software development will improve the auditability of the code. This increases the effectiveness of auditing and testing as well. This may be hard with procedural programming languages as contrary to object-oriented practices. However dividing the program into independant modules allows for better testing/debugging and independant audits of each module. This also improves the upgradeability of the system which is important for fault-tolerance.

# Launching a DAPP following the best security practices

To ensure an adequate level of security, the DAPP developer must take the following steps in the sequence described.

0. Think about the coding standard and decide on it before you start so that all smart contracts are written in the same coding standard.

1. Develop your smart-contracts and comment the code if possible. It is way better to make it open-source and publish the results to the community for review. Consider adding an open-source license. Github is the right place to store your codes.

2. Once any functional part or application module is ready for use, you should begin public testing. Consider deploying a "work in progress" version to the public testnet. Test the operability of your DAPP there. Write unit tests if necessary.

3. As soon as your application development is finalized you should proceed with a security audit request and final testing. Find a security auditor and request the audit. Do not start the security audit when the application is still in development stage. Make sure that the DAPP development is finished and there will be no updates after the code is audited.

3.1 Announce the final testing and establish a feedback line. You should deploy the final stable version of the DAPP at testnet so that everyone could use it. The final testing stage may be handled at the same time the contract is undergoing the security audit. **It is very important to make community feedback collection as user-friendly as possible.** Take it seriously. It is better to set up multiple ways of collecting feedbacks including github, email, reddit thread and other public media. This is a very bad idea to require a user to register somewhere in order to provide his feedback regarding the usability of the DAPP or report any issues. You must respect your users time.Example: I'm competent enough to identify some bugs in DAPPs and I'm willing to report them but if I face a requirement to sign up on some forum that I'm not going to use (and I'm not going to use forums of every single project because I review hundreds of them each year) then I will give up and let developers resolve their problem on their own if they are not even capable of giving me a convenient way to submit the feedback so that I will not waste my time. I assume that most competent and well-paid developers will behave in the same way. Again, it is really important to introduce multiple feedback lines so that every user can find a convenient way to submit a bug report. This may save DAPP from a million dollar hack.
