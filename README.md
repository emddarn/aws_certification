## 3. Cloud Overview:

**AWS region** is a geographical area. Each region consists of 2 or more availabilty region. Every amazon region is completely isolated from other amazon region.

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
reservation - discount upto 75% but commit for term 1yr or 3 yr only - pay monthly, pay partail upfront and pay rest monthly, pay full in upfront, reservation for EC2, DynamoDB, Elastichache, RDS DB, Redshift 

**AWS accepatble use policy** - describes phohibited use of AWS
