# CreateModel<a name="API_CreateModel"></a>

Creates a model in Amazon SageMaker\. In the request, you name the model and describe one or more containers\. For each container, you specify the docker image containing inference code, artifacts \(from prior training\), and custom environment map that the inference code uses when you deploy the model into production\. 

Use this API to create a model only if you want to use Amazon SageMaker hosting services\. To host your model, you create an endpoint configuration with the `CreateEndpointConfig` API, and then create an endpoint with the `CreateEndpoint` API\. 

Amazon SageMaker then deploys all of the containers that you defined for the model in the hosting environment\. 

In the `CreateModel` request, you must define at least one container with the `PrimaryContainer` parameter\. You can optionally specify additional containers with the `SupplementalContainers` parameter\. 

In the request, you also provide an IAM role that Amazon SageMaker can assume to access model artifacts and docker image for deployment on ML compute hosting instances\. In addition, you also use the IAM role to manage permissions the inference code needs\. For example, if the inference code access any other AWS resources, you grant necessary permissions via this role\.

## Request Syntax<a name="API_CreateModel_RequestSyntax"></a>

```
{
   "ExecutionRoleArn": "string",
   "ModelName": "string",
   "PrimaryContainer": { 
      "ContainerHostname": "string",
      "Environment": { 
         "string" : "string" 
      },
      "Image": "string",
      "ModelDataUrl": "string"
   },
   "SupplementalContainers": [ 
      { 
         "ContainerHostname": "string",
         "Environment": { 
            "string" : "string" 
         },
         "Image": "string",
         "ModelDataUrl": "string"
      }
   ],
   "Tags": [ 
      { 
         "Key": "string",
         "Value": "string"
      }
   ]
}
```

## Request Parameters<a name="API_CreateModel_RequestParameters"></a>

For information about the parameters that are common to all actions, see Common Parameters\.

The request accepts the following data in JSON format\.

 ** ExecutionRoleArn **   
The Amazon Resource Name \(ARN\) of the IAM role that Amazon SageMaker can assume to access model artifacts and docker image for deployment on ML compute instances\. Deploying on ML compute instances is part of model hosting\. For more information, see [Amazon SageMaker Roles](http://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html)\.   
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `^arn:aws[a-z\-]*:iam::\d{12}:role/?[a-zA-Z_0-9+=,.@\-_/]+$`   
Required: No

 ** ModelName **   
The name of the new model\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** PrimaryContainer **   
The location of the primary docker image containing inference code, associated artifacts, and custom environment map that the inference code uses when the model is deployed into production\.   
Type: [ContainerDefinition](API_ContainerDefinition.md) object  
Required: Yes

 ** SupplementalContainers **   
The additional optional containers to deploy\.  
Type: Array of [ContainerDefinition](API_ContainerDefinition.md) objects  
Array Members: Maximum number of 5 items\.  
Required: No

 ** Tags **   
An array of key\-value pairs\. For more information, see [Using Cost Allocation Tags](http://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html#allocation-what) in the *AWS Billing and Cost Management User Guide*\.   
Type: Array of [Tag](API_Tag.md) objects  
Array Members: Minimum number of 0 items\. Maximum number of 50 items\.  
Required: No

## Response Syntax<a name="API_CreateModel_ResponseSyntax"></a>

```
{
   "ModelArn": "string"
}
```

## Response Elements<a name="API_CreateModel_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** ModelArn **   
The ARN of the model created in Amazon SageMaker\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.

## Errors<a name="API_CreateModel_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **ResourceLimitExceeded**   
 You have exceeded an Amazon SageMaker resource limit\. For example, you might have too many training jobs created\.   
HTTP Status Code: 400

## See Also<a name="API_CreateModel_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/sagemaker-2017-07-24/CreateModel) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/sagemaker-2017-07-24/CreateModel) 