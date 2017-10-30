About the Repository
===================


This repository contains cloudformation templates which can be used to replicate the Infrastructure from one region to another. It is necessary to have a basic idea of the following terms while working with AWS Cloudformation.

**Template** :  It describes AWS resources and their properties.

**Stack** :  To provision all the resources which are listed in template, a stack is needed which can be created by submitting the template.

----------



#### Prerequesites


There are some prerequisites which should be in place while using the templates:

1) If the stack is being created via IAM User which do not have admin access. The following IAM policies can be used to give Cloudformation related permission to IAM user.

       "cloudformation:CreateUploadBucket",
       "cloudformation:GetTemplateSummary",
       "cloudformation:ValidateTemplate",
       "cloudformation:CreateStack",
       "cloudformation:GetStackPolicy",
       "cloudformation:DeleteStack",
       "cloudformation:UpdateStack",
       "cloudformation:CreateChangeSet",
       "cloudformation:DescribeChangeSet",
       "cloudformation:ExecuteChangeSet",
       "config:DescribeConfigurationRecorders"

2) Once the above policies have been associated with IAM user. Here comes the manual work which need to be done in order to do the replication smoothly across regions and it include the following :

- Creating Amazon EC2 Key Pair 


	 As of now Amazon Cloudformation doesn't support creating key pair so it need to be created manually and the name of the key should be in specific format. Take a look at the link below to create a key pair. 

	Link: [*Creating Your Key Pair Using Amazon EC2*](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair) 
	 
For eg:
```
if the replication is to be carried out for us-east-2 then the key name should be in the format:

"sample-key-useast2"
```
- Copy AMI 	

	As the cloudformation include the creation of several EC2 Instances and thus the Instances requires some base Image i.e, AMI to be used during Instance creation and for that a custom AMI has been baked. Therefore this AMI should be present in the region before creating the stack. Take a look at the link to copy the AMI from one region to another.

	Link : [*Copying an AMI*](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/CopyingAMIs.html)



How to Trigger it from CI Server
-------------------

TBD ..

