# flask_project
Design and Implementation of a Lightweight Education Data Bay Area (E-DBA)
(A Project shared by courses Software Engineering and Advanced Software Development Workshop)
The requirements might be subject to refinement. 
1Introduction
More and more organizations need to share data with other organizations. “Every organization needs to share data with other organizations in a transparent and interoperable way while adhering to corporate policies and data sovereignty regulations” (From Eclipse Dataspace Connector Website) International dataspace association launched an architecture for this purpose (See Figure 1). 

Figure 1 IDS Dataspace model (https://internationaldataspaces.org/)
Our project is inspired by this model but not limited to. This system expects the following main goals:
1)Providing an easy and secure way for the data provision and data consumption among the registered high education organizations.
2)Student identity authentication. 
3)Student theses’ access.
4)Online payment.
5)Course information sharing.
6)Data vault service (Optional).

2User roles
The system can be used by the following users. Each user can access the system according to his role. 
2.1Administrator
There are three levels of administers: T-Admin, E-Admin, and O-Convener.
2.1.1Technical admin (T-Admin)
Assume that there is only one technical admin in E-DBA. T-Admin 1) responds to the help requests from other users on the problems in using the system, 2) sets up two management administrators.
T-Admin usually log in the system once every weekday, answering the user questions that have not been answered. He can also view answered questions. The questions are listed in order of time. Each question has a short title, description, questioner’ email, role, submit time, and response time. Users can view the responses from T-Admin through “Seek help”.
2.1.2E-Admin, Senior E-Admin
E-DBA platform has two management admins. 
E-Admin
E-Admin’s job includes:
a)Approving or rejecting the registration applications. 
A registration application from an O-Convener is processed within three days. When E-Admin approves an application, a notice will be sent to Senior E-Admin’s email box. If E-Admin rejects an application, an email notice will be sent to applicant’s email box directly.
b)Explaining platform data sharing policies. 
There could be several policies. E-Admin can add, delete, or update a policy. The policy can be uploaded in a pdf file. 
c)Checking log information
All the user activities in E-DBA system will be recorded, including login time, logout time, services accessed, and organizations the provide those services. E-Admin can check log information for all organizations. Log information can be checked according to activities, user names, dates, or organizations. Nobody can modify the log content.
d)Setting an E-DBA bank account and a membership fee
Senior E-Admin 
Senior E-Admin approves/rejects the registration applications approved by E-Admin. After Senior E-Admin gets a notice from E-Admin through the E-DBA system, he can login the system, view the applications to approve and corresponding documents. Once he approves/rejects, a notice will be sent to O-Convener immediately. If approved, O-Convener’s email address and his role will be recorded in the E-DBA system so that O-Convener can login later. A workspace is assigned to this registered organization.
2.1.3O-Convener
Each organization should have a convener (O-Convener) who is responsible for the business connection with the E-DBA, including registration, maintenance of services, and maintenance of user name list from his organization. The registration follows the following steps.
a)The O-Convener should provide application information, including a required proof document and an email address of the convener through the system entrance Register for approval. Register entrance does not need to login. The O-Convener should input the following information: organization name in full, organization name in short, an email address for registration. Assume that only one pdf file will be uploaded as the proofing document. When an O-Convener offers a valid email address, a code is sent to his email box and he needs to input the code in the system to verify. 
b)The registration application needs to be reviewed by E-Admin and Senior E-Admin. Details refer to E-Admin and Senior E-Admin’s jobs.
c)If the registration application is approved, a workspace in E-DBA is assigned to this O-Convener. The O-Convener can login the system by offering registered email address and the code sent by E-DBA.  
d)Each O-Convener can then submit a list of members who can access E-DBA in his organization. The list is in the required excel file format (see an example in Appendices). He can also choose to add/delete/edit an individual member in E-DBA through provided UI. 
Membership fee should be paid for members in the offered list. Once new members are added, payment might be needed. There is no member fee refund when members are removed. Details about the membership fee refer to Appendices. 
2.1.4Data provider and data consumer
Currently only users from the authorized organizations can access the system. Except users with admin roles, any of other users can be a data provider, a data consumer or both, depending on the access right set up by the O-Convener in user’s organization.
A user can have one or more of following rights:
1)Public data access (access right level: 1)
2)Private data consumption (access right level: 2)
3)Private data provision (access right level: 3)
A user with higher level can access all the information that can be accessed by lower levels.
They can seek help if they encounter any problems in using the system. They can also check the responses from T-Admin. A star is shown besides an asked question indicating that the question has been answered. 

3Services
3.1Workspace
Each organization has a workspace. In this workspace,
1)O-Convener must offer a banking account for payment and receiving service fee. The input information include: bank name, account no, account name, and password (not shown). 
2)O-Convener can manage the list of members that can access the system. O-Convener can set up a payment quota for each user in thesis download. 
3)O-Convener can check the log of any activities related to his own organization only. Log information can be checked according to activities, user names, dates 
4)O-Convener can add/remove the services to/from his workspace. The services can be chosen from a list of candidate services. Currently, three kinds of services can be provided: course information sharing (free), student identity authentication, thesis sharing. The “Student identity authentication” service can only be accessed by private data consumer. The “student identity authentication” and “thesis sharing” services needs to configure database interface information before they can be used. The O-Convener can set up the charges for these two services. The O-Convener can also designate thesis download services to all organizations or to some of organizations, free or charged. The charges are paid once a user uses the service. Before the configuration, the services can be shown to private data providers from his organization only. 
5)A private data provider from an organization can do the configuration for the services. Once a service is added and configured, this service should be accessible to data consumers according to the user’s access right.  A private data provider adds/removes/edits course information and configure database interface information for thesis sharing and student information services. Details about the configuration UI will be provided later.

3.2Data access
A user needs to enter an organization’s workspace to access the service. He can search for organizations among registered organizations. There are two kinds of data regarding their access rights. 
1)Public data
Course information
Course information is public for free. Each organization can manage the courses provided by itself. Public area stays in the organization space and is open to any user with public access right. Each course contains course title, units, and course description. A user can search for courses through a keyword. 
Thesis sharing
A user can access a thesis from an organization based on the access right set up by that organization. Access right could be display only or download. Thesis access may be charged, set up by the organization who offers thesis sharing service. 

2)Private data
i.Student identity authentication service
A registered organization can provide the student identity authentication service for the enrolled students including graduates. A user can use this service in two ways
Input student basic information from the UI. 
Batch input in an excel file. The file includes the same required columns. 
The output of this access is Yes/No. 
ii.Student GPA record access
Two access ways are same as above in item i. The output of the student record includes: student name, enroll year, graduation year, and GPA. This service is paid according to the number of records.
These service are paid according to the access person-times. Data consumer need to pay according to the charges set up by O-Convener		 
3.3Payment 
The system will provide online payment. There are following payment methods:
a)Transfer
b)PayPal
c)WeChat
d)Alipay
e)Credit card
The first payment method is a must. Other methods are optional, (i.e., in this system, you can make them gray, not accessible). When the first method is used, the fee is paid by organization. If payment is not successful, the user should contact the O-Convener of his organization.
3.4Vault (optional)
This is an optional feature. The system provides the vault service for the organization which cannot maintain their databases by themselves. However, they can export the information from database and share with designated functions and rights. The information will be stored and accessed according to rights set up by provider. E-DBA can provide the vault and corresponding services according to the right set up by the provider. No extra points are given for the implementation of this function in this semester.

4Appendices
4.1Forms
4.1.1An example of a member list
O-Convener provides the access list to E-DBA. Here is an example（Attention: *@ if email has *, it means that all the users with this email format can login with given access right）
name	email	access right	Quota for thesis download
Alice Huang	Alice_Huang@uic.edu.cn	3	500 RMB
John Chow	John_Chow@uic.edu.cn	2	 0
	*@mail.uic.edu.cn	1	100 RMB
Table 1 An Example of Membership Table
4.1.2E-DBA charge table
Membership charge is fixed or configured by E-Admin. Prices of services are set up by O-Convener. 
Service type	charge
Course information sharing	0
Organization membership	Access right level 1: 1000 RMB in total or 10 RMB/person. (O-Convener can choose one way to pay membership fee)
Access right level 2: 100 RMB/person
Access right level 3: 0
The membership fee is fixed. It is better if the membership fee can be set up by E-Admin.
Thesis download, student identity authentication or records	Determined by O-Convener
Table 2 Service Charges
4.2Policies
There can be several policies. For example: 
Copyright policy,
Private data collection policy, and so on

4.3External Databases (for test)
Attention: For the following databases, the given interfaces should not be directly used in the code. The interface information is inputted in the configuration service by private data provider.  
4.3.1Student information database
There are two interfaces:
1)Identity authentication 
Input: student name, id, photo
Output: y/n
2)Student record
Input: student name, id
Output: student name, enroll year, graduation year, and GPA
4.3.2Thesis database
There are two interfaces:
1)Unknown title 
Input: keywords
Output: list of the theses with keywords in their titles
2)Known title
Input: thesis title
Output: pdf file
4.3.3Bank account databases
The interface of checkAccountValidity is:
Input: bank name, account name, account number, password 
Output: success/fail.
The interface of transferMoney is:
Input: 
out bank: bank name, account name, account number, password
in bank: bank name, account name, account number
amount 
Output: success/fail.

 
