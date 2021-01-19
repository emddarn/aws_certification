## 3. Overview:

**region** is a geographical area. Each region consists of 2 or more availabilty region. Every amazon region is completely isolated from other amazon region.

The **avaialbity zones (AZ)** are the location where we launch resources e.g. EC2 
There are multiple availabilty zones in each region 
AZs are physically separated and isloated from each other - BUT are connected with low latency, high throughput, redundant connection. **Use case:** split resouce within region - but different AZs -> leads to highly resilient apps 
Failure (power, network) in one AZ - doesn't affect another AZ

3 fundamentatl of **AWS pricing** - *compute*, *storage*, *outbound data-transfer* 
send data into aws - not charge - e.g. upload to S3 
pull data out aws - charged - e.g. pull from S3 

**Model of payment**
- on-demand - compute capacity - no discount, no commitment
- dedicated - deploy your application - HW dedicated to me - not sharing with other users on AWS
- spot instance - purchase capacity (spare) - no commitment, good discount - but can't get shut-down if somebody pays for resources 
<br/>reservation - discount upto 75% but commit for term 1yr or 3 yr only. 

<br/>You can pay
<ul>
  <li>pay monthly,</li>
  <li>- pay partail upfront and pay rest monthly, </li>
  <li>-pay full in upfront, reservation for EC2, DynamoDB, Elastichache, RDS DB, Redshift<li>
</ul>



**AWS accepatble use policy** - describes phohibited use of AWS


**IAM service** - used to create security identity - e.g. users, groups etc. - can be controlled through policies and roles 

**Users:** entity represents person or service 
- assign Access Key ID and Secret Access Key - needed to access AWS through CLI, API, programatic access, SDK developement tool  
- by default, users don't have any access to account, 
- root user's credential: email address - always have full admin permission - no restriction
- user can represent application (service account); upto 500 suers; user can have name (eric, ethan, etc) and ARN; create IAM account for users and never share 
- best practice - don't use root credentials; no sharing; create IAM user and assign admin permission: enable multi-factor authetication (MFA)
- define password policy: password length and complexity

We need 
- password - to access the management console
- access key - for programtic access 

**Group:** collect users together and attach policites to them 
- not an identity; 
- can't specity group in the poicity *while writing* - but can assign policy later
- groups are like developer, admin, and assign policity required
- assign policy principle of least privilege (security best practice don't give more than needed privilege)
- can't put group in another group.

**roles:** creatd and used or assumed by an entity (application or service can use role for permission) 
- used to delegate permission for resources to user/services 
- don't have to put username/password in code 
- both IAM user/service assume role to gain temporary securty credentials and use API  

**policy:** documents to define permission 
- applied users/group/roles 
- written in json 
- all permission is implicity denied (denied by default unless in the policy) 
- if there's multiple policy assigned, the most restricive one is applied
- IAM policy simulator - used to test policy 
- condiion element: apply further conditional logic (maynot come in practiotioner)

**authentication methods:** 3 key methods - 
* access key: access keyid + secrted access key ..can use mfa = used for programatic access - create/view/modify in console - while creating you can see it once, but can't see that anymore...it lost, recreate. users can have right to change it or disable user access to key to prevent using
* iam user: user log in using password to management console - 
* sign-in certificate: certicate can be used to access services

*console password:* username+password to access account 
- we can restrict to change password in general and then use specific policy to allow certain user to change password

*SSL/TSL certificate*
- used to atuthenticate to certian services (not imp for certification)

*MFA:* combine password+virtual (google authenticator app)/physical mfa device - add 2nd level of authenticaiton

*SDS service* - gives *limited privilege certedtial* - *temporary* - assume a role, some credential given to role - but rotated over time

**IAM best practices:(imp):**
- locking away root acces key 
- create individual user - no sharing account
- use aws-defined policies to define policies whenever possible (to prvent mistake)
- use groups to assign permission - put users to groups
- grant least privilege to do user's job
- use access level to review IAM permission - periodically check/review to all user/group/roles
- configure stong password policy
- MFA
- use roles for application run on EC2 (use roles than access  key)
- delegate by using roles instead of sharing credentials
- rotate credentials regularly
- remove unncessary credentials
- use policy condition for extra security (e.g. policy to apply only computer has specific IP range)
- monitor activity 

