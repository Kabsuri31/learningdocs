How to use specific providers:      


```terraform {
  required_providers {
    aws = {
        source  = "hashicorp/aws"
        version = "~> 5.0"
    }
  }
}  ```     

    How to use multiple provider   

Use Alias for provider block as below       
```provider "aws" {
  alias  = "us_west"
  region = "us-west-2"
}
provider "aws" {
  alias  = "us_east"
  region = "us-east-1"
}
resource "aws_instance" "example" {
  provider = aws.us_west
  ami      = "ami-12345678"
  instance_type = "t2.micro"
}```

    AUTHENTICATION

Environment variables (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY)        
Profile files in ~/.aws/credentials     
Directly in the provider block (though this is not recommended for security reasons).       