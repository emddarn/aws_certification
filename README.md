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
- pay monthly, 
- pay partail upfront and pay rest monthly, 
- pay full in upfront, reservation for EC2, DynamoDB, Elastichache, RDS DB, Redshift 

**AWS accepatble use policy** - describes phohibited use of AWS


IAM service - used to create security identifty -8isers, groups, controlling thourgh policies and roles
users: entity represents person or service - assign access keyid and secret access key - acess aws through cli, api, programatic access, sdk developement tool
pswrod: access to management console ...access key for programtic access
bydefault, users don't have any access to account, root user credential email address - always have full admin permission - no restrict
best practice - don't use root credentials, no sharing, create iam user and assign admin permission, enable mfa
user can represent application (service account), upto 500 suers, user can have name (eric, ethan, etc) and ARN. create iam account for users and never share and define password policy: password length and complexity
group: collect users together and attach policites to them..not an identity. can't specity group in the poicity wheile wrrtting..but assign plicity to user....groups are like developer, admin, and assign policity required...assign policy principle of least privilege (security best practice don't give more than need priv)...can't put group in another group.
roles:
