# Creating an S3 bucket<a name="create-s3-bucket"></a>

The S3 bucket for your media capture pipeline must belong to the same AWS account and AWS Region as the Amazon Chime SDK meeting\. In addition, you must give the `s3:PutObject` and `s3:PutObjectAcl` permission to the Amazon Chime service principal [chime\.amazonaws\.com](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html)\. You can do that with the S3 console or the CLI\.

**Note**  
If you need to encrypt data, you must use Amazon S3\-Managed Keys\. We don't support server\-side encryption using Customer Master Keys stored in the AWS Key Management Service\. 

The following example shows an S3 bucket policy\.

```
{
    "Version": "2012-10-17",
    "Id": "AWSChimeMediaCaptureBucketPolicy",
    "Statement": [
        {
            "Sid": "AWSChimeMediaCaptureBucketPolicy",
            "Effect": "Allow",
            "Principal": {
                "Service": "chime.amazonaws.com"
            },
            "Action": [ "s3:PutObject", "s3:PutObjectAcl" ],
            "Resource": "arn:aws:s3:::bucket name/*"
        }
    ]
}
```