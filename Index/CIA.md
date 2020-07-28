> **[Home](https://github.com/RakeshKengale/RaKKeN)  /  CIA**


## CIA Triad

#### CIA = Confidentiality, Integrity, Availability

__Confidentiality:__ Systems and data are accessible to authorized users only.

__Integrity:__ Systems and data are accurate and complete.

__Availability:__ Systems and data are accessible when they are needed.

## Confidentiality

Confidentiality is concerned with preventing unauthorized access to sensitive information. It is designed to ensure the wrong people cannot gain access to sensitive information while ensuring the right people can access it. Access to information must be restricted only to those who are authorized to view the required data. The two main ways to ensure confidentiality are cryptography and access control.

### How To Maintain Confidentiality.

Data encryption is a common method of ensuring confidentiality. User IDs and passwords constitute a standard procedure; two-factor authentication is becoming the norm. Other options include biometric verification and security tokens, key fobs or soft tokens.Extra measures might be taken in the case of extremely sensitive documents, such as storing only on air gapped computers, disconnected storage devices or, for highly sensitive information, in hard copy form only.

Cryptography – It involves the process of generating code, which allows the sender and recipients to communicate by authenticating each other with secret keys.

Steganography – Technique of hiding a piece of secret information within a non-secret text or image.

Access Control – Implementing appropriate access control mechanism to prevent from unauthorized and unauthenticated access. 

## Integrity

Integrity assures the sensitive data is trustworthy and accurate. Consistency, accuracy, and trustworthiness of data should be maintained over its life cycle. Sensitive data should not be altered in transit, and security measures, such as file permissions and user access controls, should be taken to make sure that it cannot be modified by unauthorized users. 

### How To Maintain Confidentiality.

These measures include file permissions and user access controls. Version control may be used to prevent erroneous changes or accidental deletion by authorized users from becoming a problem. In addition, some means must be in place to detect any changes in data that might occur as a result of non-human-caused events such as an electromagnetic pulse (EMP) or server crash. Some data might include checksums, even cryptographic checksums, for verification of integrity. Backups or redundancies must be available to restore the affected data to its correct state.
Integrity can also be verified using a hashing algorithm. Essentially, a hash of the message is generated and appended to the end of the message. The receiving party calculates the hash of the message they received and compares it to the hash they received. If something changed in transit, the hashes won’t match.

Input Validation – It ensures the integrity by restricting or validating the values that the user enters.

Hashing – It offers integrity by the way of combining hash function and shared secret key.

Digital Signature – It involves a mathematical technique to make sure that there is no alteration in the message.


## Availability 

Availability  is the guarantee of reliable and constant access to your sensitive data by authorized people. Authorized users should be able to access data whenever they need to do so. It is best guaranteed by properly maintaining all hardware and software necessary to ensure the availability of sensitive data. It’s also important to keep up with system upgrades. ensures that information and resources are available to those who need them. 

### How To Maintain Confidentiality.

It is implemented using methods such as hardware maintenance, software patching and network optimization. Processes such as redundancy, failover, RAID and high-availability clusters are used to mitigate serious consequences when hardware issues do occur. Dedicated hardware devices can be used to guard against downtime and unreachable data due to malicious actions such as distributed denial-of-service (DDoS) attacks.



**References**

- [Basic principles - CIA](https://en.wikipedia.org/wiki/Information_security#Basic_principles)