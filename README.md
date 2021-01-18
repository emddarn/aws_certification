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


**IAM service** - used to create security identity - e.g. users, groups etc. - can be controlled thourgh policies and roles 

**Users:** entity represents person or service - assign access key id and secret access key - acess aws through cli, api, programatic access, sdk developement tool  

pswrod: access to management console ...access key for programtic access 

- by default, users don't have any access to account, root user credential email address - always have full admin permission - no restrict
- best practice - don't use root credentials, no sharing; create iam user and assign admin permission, enable mfa
- user can represent application (service account); upto 500 suers; user can have name (eric, ethan, etc) and ARN; create iam account for users and never share and define - 
- password policy: password length and complexity
**Group:** collect users together and attach policites to them - not an identity; can't specity group in the poicity while writing..but assign plicity to user....groups are like developer, admin, and assign policity required...assign policy principle of least privilege (security best practice don't give more than need priv)...can't put group in another group.
roles: roles: creatd and used or assumed by an entity (application or service can use role for permission) - delegating permission for resources to user/services - don't have to username/password in code - both iam user/service assume role to gain temporary securty credentials and use API - 
policity: documents to define permission - applied users/group/roles - written in json - all permission is implicity denied (denied by default unless in the policy) - if there's multiple policy assigned, the most restricive one is applice. iam policy simulator - test plolicy - condiion eleemtn: apply further conditional logic (maynot come in practiotioner)
authentication methods: 3 key methods - 1. access key: access keyid + secrted access key ..can use mfa = used for programatic access - create/view/modify in console - while creating you can see it once, but can't see that anymore...it lost, recreate. users can have right to change it or disable user access to key to prevent using
2. iam user: user log in using password to management console - 
3. sign-in certificate: certicate can be used to access services

console password: username+password to access amc
restrict to chagne password in general and then use specific policy to allow certain user to chagne password
SSL/TSL certificate -used to atuthenticate to certian services (not imp for certification)
MFA; combine password+virtual (google authenticator app)/physical mfa device - add 2nd level of authenticaiton
SDS service - gives *limited privil certedtial* - *temporary* - assume a role, some credet given to role - but rotated over time
iam best practices:(imp):
locking away root acces key
create indivitual user - no sharing account
use aws-defined plicityes to dfein policies whenever possible (to prvent mistake)
use groups to assign permission - put users to groups
grant least privilege to do user's job
use access level to review iam permission - periodically check/review to all user/grrp/roles
config stong password policy
MFA
use roles for application run on EC2 (use roles than access  key)
delegate by using roles instead of sharing credentials
rotate credentials regularly
remov unncessary credentials
use policy condition for extra security (policy applies only computer has specific ip range)
monitor activity 

