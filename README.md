# Custodian
This repo contains cloud custodian policies. The EC2 instance "Custodian" has the appropriate AWS CLI commands installed to run the policies. At this point there are 2 main policies
1. Turn on and off an instance: The file periodicPolicy.yml has such policy. In order to run it activate custodian virtual environment and run the following command: "custodian run --output-dir=. periodicPolicy.yml". 
2. Tag Compliance: The file ec2Tag.yml has multiple policies in there to check against the tags on EC2 and if the tags don't comply then mark the instances to be stopped and eventually terminate. An email can be automatically send when the instances are stopped or terminated. mailer-sqs.yml provides email related information. The following command can be run to specify the policies and setup email: "c7n-mailer --config mailer-sqs.yml --update-lambda && custodian run -c ec2Tag.yml -s ."
Further details can be found at
a. http://confluence.agiletrailblazers.com/display/DEV/CloudCustodian
b. http://confluence.agiletrailblazers.com/pages/viewpage.action?spaceKey=DEV&title=Tag+Compliance+Policy


