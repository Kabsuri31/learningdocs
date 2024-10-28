######We have built in function for  

>numeric         

abs, ceil, floor, max, min, 

>string      

lower,upper, join, split,length

>collections     

length, tolist, tomap, merge, keys, values, contains

>filesystem      

file(path)

>control flow funtions       

if(condition, true_value, false_value): Returns true_value if the condition is true; otherwise, false_value.        
for_each(list): Iterates over a list in loops (useful in modules).      
for: Generates new lists or maps from input.            


    DYNAMIC BLOCK

Reduce duplication of code      
```resource "aws_instance" "example" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
  dynamic "tag" {
    for_each = var.instance_tags
    content {
      key   = tag.key
      value = tag.value
    }
  }
}```


    Terraform import Command

Get the unique ID of resources from AWS        
run import command      
    ```terraform import aws_instance.my_ec2 <unique_ID>```
This will update state file but configuration TF file needs to be manually added .

    Terraform state management
Use like AWS s3 for storage and dynamo for state locking to prevent concurrent operation.


    Terraform workspace
terraform workspace new dev         
terraform workspace select dev ( switching workspace )


    Terraform Dependency Management

depends_on: Ensure a resource depends on another, even if Terraform doesn’t infer the dependency.       
```resource "aws_instance" "app" {
  depends_on = [aws_security_group.sg]
  ami           = var.ami_id
  instance_type = "t2.micro"
}```


    Terraform Data Sources
Data sources allow you to retrieve information about existing infrastructure from the provider without managing it.     
```data "aws_ami" "latest" {
  most_recent = true
  owners      = ["amazon"]
  filter {
    name   = "name"
    values = ["amzn2-ami-hvm-*"]
  }
}
resource "aws_instance" "example" {
  ami           = data.aws_ami.latest.id
  instance_type = "t2.micro"
}```


    Terraform Provisioners (With Caution)
Provisioners execute scripts on resources during or after their creation.       
file-exec                
remote-exec         
local-exec          

    Handling Drift Detection
Drift occurs when the actual state of resources diverges from the Terraform state file.         
terraform refresh: Sync state with actual infrastructure.       


    Debugging and Troubleshooting Terraform

Terraform Logs: Use TF_LOG environment variables (e.g., TF_LOG=DEBUG) for detailed logging.     
Dependency Graph: Visualize the resource dependencies using terraform graph.


    Testing Terraform Configurations

Terraform Validate: Ensures the syntax is correct.      
Terratest: A Go-based framework to write infrastructure tests.      
Checkov and tfsec: Static code analysis tools to detect security and compliance issues.     


    Performance Optimization
Parallelism: Use the -parallelism flag to speed up resource creation.       
```terraform apply -parallelism=10```


    Use Plan and Apply Targets
If you know which resources need to be updated, target specific resources instead of planning and applying the entire configuration.            
```terraform apply -target=aws_instance.web```

    Resource Lifecyle Arguements 
create_before_destroy       
prevent_destroy     
ignore_changes      