

## AAA

#### AAA = Authentication, Authorization, Accountability

Authentication, Authorization, Accountability (A.A.A) is a term for controlling the access to the system resources, auditing usage, enforcing policies and offering the details need to charge for services.

### Authentication

Authentication generally deals with personal identification. Providing proof for your identity and confirmed by the system is authentication. Different methods of authentications are: 

- __Knowledge:__ Something you know (Username or Password), 
- __Characteristics:__ Something you are (fingerprint or eye scan), 
- __Ownership:__ Something you have (credit card or token),
- something you do (the way you sign your name), 
- somewhere you are (GPS). 


### Authorization

Authorization ensures that user includes the permission/privilege to perform a certain action.  It is when a person is given privilege to access certain data. Only authorised person should be able to access the sensitive data. 

**For example,**
 the user playing network access role should only include the access rights associated with network action. He shouldn’t be allowed to access storage or other components. Both actions of authorization and authentication are interdependent. Usually, the process of authorization validation occurs after the successful authentication.

#### Access Control

Access control is a security aspect that handles how user as well as system communicates and use resources. In order to enforce security, each and every access to the system and its resources should be controlled and should ensure only authorized access are allowed. This feature is mainly used to protect against unauthorized disclosure, corruption, modification, and destruction. It generally acts as the first line of defense to avoid the unauthorized access and entry. It comprises a set of controls that restrict access to resources based on the group membership, identity, clearance, physical & logical location and need-to-know. In addition, the access can be in the method of permission to consume, enter, control, restrict, use and protect the resource to guarantee three basic principles such as Availability, Confidentiality, and Integrity.

### Accountability

Accountability is the third plank in the AAA framework. It offers administrators, the ability to track the activities that users performed at a certain situation. It is a primary method to view what services were utilized and how much resources were used up by users. Tracking of data, resources and network usage. This can be useful when there is a breach, you can have a look at the log files to identify who and how the breach happened. Generally, accountability is enforced by performing audits as well as establishing systems to make and keep audit trails. This log management can be helpful in the prospect of IT accountability and data security. It enforces that action can be determined and traced back.


#### Non-repudiation

Non-repudiation is the assurance that someone cannot deny the validity of something. Non-repudiation is a legal concept that is widely used in information security and refers to a service, which provides proof of the origin of data and the integrity of the data. In other words, non-repudiation makes it very difficult to successfully deny who/where a message came from as well as the authenticity and integrity of that message. Non-repudiation deals with making evidence to prove certain actions. It is all about proving that an event or action has taken place that can’t be repudiated later. The non-repudiation can be achieved via the use of:

- __Digital Signature__ – In addition to ensuring data integrity, digital signatures guarantees the sender’s identity. It basically enforces and the sender can’t deny later.

- __Timestamps__ - It possess the time and date when the document was composed to generate an evidence that the document was available at a particular time.

__Levels Of Non-Repudiation__

In order to experience a complete level of non-repudiation communication, it is essential to ensure this at three basic levels:

- __Of Origin__ – can be ensured by sending data along with digital signature & certificate

- __At Delivery__ - can be ensured with recipient acknowledgment

- __For Submission__ – can be ensured by sending delivery recipient to sender
