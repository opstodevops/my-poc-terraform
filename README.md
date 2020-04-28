# my-poc-terraform
Code repository for my POC Terraform project

## Recording the commands for each section for reference

### 001-start
```
terraform init
terraform validate
terraform plan -out terraform.tfplan
terraform apply "terraform.tfplan"
terraform destroy
```

### 002-progress
```
#First run
terraform init
terraform plan -out terraform.tfplan
terraform apply "terraform.tfplan"

terraform show
terraform output

#Second run
#Renamed the files to use the NEW config
ren main.tf main.tf.old
ren main.tf.rename main.tf

terraform plan -out terraform.tfplan
terraform apply "terraform.tfplan"

terraform destroy

#Haven't renamed the files back to their original names
```

### 003-vpcandsgs
```
terraform init
terraform plan -out terraform.tfplan
terraform apply "terraform.tfplan"

terraform destroy
```

### 004-multiAZ
```
#Functions testing
terraform console #run in TF console
min(42,5,16)
cidrsubnet(var.network_address_space, 8, 0)
cidrhost(cidrsubnet(var.network_address_space, 8, 0),5)
lookup(local.common_tags, "BillingCode", "Unknown")
lookup(local.common_tags, "Missing", "Unknown")
local.s3_bucket_name

#Configuration command
terraform init
terraform plan -out terraform.tfplan
terraform apply "terraform.tfplan"

terraform destroy
```

### 005-breakmodule
```
terraform init
terraform workspace new Development
terraform plan -out development.tfplan
terraform apply "development.tfplan"

terraform workspace new UAT
terraform plan -out uat.tfplan
terraform apply "uat.tfplan"

#Don't forget to remove from tfvars, variables, and resource provider
$env:AWS_ACCESS_KEY_ID="AWS_ACCESS_KEY_ID"
$env:AWS_SECRET_ACCESS_KEY="AWS_SECRET_ACCESS_KEY"

terraform workspace new Production
terraform plan -out production.tfplan
terraform apply "production.tfplan"

terraform destroy

terraform workspace select UAT
terraform destroy

terraform workspace select Development
terraform destroy
```

### 006-createmodules
```
terraform init
terraform workspace new Development
terraform plan -out development.tfplan
terraform apply "development.tfplan"

terraform destroy
```