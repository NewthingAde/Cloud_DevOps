
# Deploy Web Application using Cloud Formation

There are two sets of files, the YML files and the JSON files. The YML files create the environment and JSON is used to include the parameters into the environment.

## Architecture Diagram

![Oluwasegun_Adesanya (1)](https://user-images.githubusercontent.com/80678596/157886326-10c9b7cd-dfa6-4c4c-a528-f92db32ec378.png)

## Create infrastructure
      ###### Note that i put --capabilities CAPABILITY_NAMED_IAM in the second and thrid stack. That was because i assign IAM role so its is required i include the command else it will through out error

In order to create the infrastructure stack run the following commands in the same order as below:

aws cloudformation create-stack --stack-name Udagram --template-body file://network.yml --parameters file://network-parameters.json  --region=us-east-1

aws cloudformation create-stack --stack-name Udagramserver --template-body file://servers.yml --parameters file://server-parameters.json --capabilities CAPABILITY_NAMED_IAM --region=us-east-1

aws cloudformation create-stack --stack-name Udagrambastion --template-body file://Bastion.yml --parameters file://bastion-parameters.json  --capabilities CAPABILITY_NAMED_IAM  --region=us-east-1


## Verify deployment
To check whether the web application is running, follow the web application public URL, which could be found in output exports of application-servers cloud formation stack.

## Update infrastructure
To update the already existing infrastructure stack run any of the following command you want to update:

aws cloudformation update-stack --stack-name Udagram --template-body file://network.yml --parameters file://network-parameters.json  --region=us-east-1

aws cloudformation update-stack --stack-name Udagramserver --template-body file://servers.yml --parameters file://server-parameters.json --capabilities CAPABILITY_NAMED_IAM --region=us-east-1

aws cloudformation update-stack --stack-name Udagrambastion --template-body file://Bastion.yml --parameters file://bastion-parameters.json  --capabilities CAPABILITY_NAMED_IAM  --region=us-east-1



