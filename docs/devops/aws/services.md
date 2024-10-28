        AWS config                  
- AWS Config is a powerful tool for managing the configurations of your AWS resources. It helps organizations maintain compliance, improve security, and enhance governance over their cloud infrastructure. By continuously monitoring and recording resource configurations, AWS Config provides valuable insights into your AWS environment, enabling better management and operational efficiency.

Add rule to monitor or track changes to your resources like ec2 rule for monitoring approved AMIs is being used or not.



        AWS system manager ( SSM  )

- AWS Systems Manager makes life easier by giving you one place to manage, automate, and secure your servers, whether they’re in AWS or on-premises. It reduces manual effort, ensures consistency, and keeps your infrastructure well-maintained.

Simple Example Use Case     
If you have 50 servers (EC2 instances) running a web application, and you want to:
Install security patches on all servers.
Update a configuration file across all servers.
Monitor server health and ensure they meet compliance rules.
With Systems Manager, you can automate all of this without logging into each server one-by-one.


        AWS s3 acceleration
Upload to edge location and then to s3 remote location  
    
        AWS migration services and database services

application or DB can be migrated to cloud . like mysql to RDS 
    
        7 R's of migration
< MOST EFFORT >
    Refactor - (Rearchitect to a cloud native serverless arch)
    Replatform  (ex: database to PASS RDS service)
    Repurchase -  use a different soln ( eg SAAS )      
    Rehost - ( lift and shift )     
    Relocate without modifications (lift and shift)     
    Retain as it is ( can be visit later )      
    Retire some applications        
< LEAST EFFORT >
    