# How to Choose an Encryption Tool or Service<a name="awscryp-choose-toplevel"></a>

AWS offers several different cryptographic tools and services\. This section is designed to help you learn about them and decide which tools and services you should use for your projects\. 

Most AWS services that store and manage your data support *server\-side encryption*, where the service that stores and manages your data also transparently encrypts and decrypts it for you\. AWS also supports *client\-side encryption* libraries that you can include in your applications\. These libraries make it easier to include best\-practice encryption in your application, even if you are not a cryptography expert\.

Before selecting your cryptographic tools and services, decide if you prefer client\-side encryption, server\-side encryption, or both\. Your decision depends on the design of your application, the sensitivity of your data, and the security requirements of your organization\. We try to make our client\-side encryption libraries easy to use, but for most applications it's much easier to have an AWS service manage encryption transparently\. 

**What do you need to protect your data?**
+ Do you need to create and manage the hardware security modules that store your encryption keys? Consider the [AWS CloudHSM](awscryp-choose-hsm.md) service\.
+ Would you benefit from an AWS service that protects your encryption keys for you? Consider [AWS Key Management Service](awscryp-choose-kms.md) \(AWS KMS\)\.
+ Do you need to protect your data before you send it to AWS? Use a client\-side encryption library, like the AWS Encryption SDK, the DynamoDB Encryption Client, or the Amazon S3 Encryption Client\.

**What type of data do you need to protect? **
+ To protect DynamoDB table items before you send them to DynamoDB, use the [DynamoDB Encryption Client](awscryp-choose-ddb.md)\. But be sure that you need it\. DynamoDB encryption at rest automatically protects all DynamoDB tables whenever they are written to disk\. 
+ To protect Amazon S3 objects before you send them to an Amazon S3 bucket, use the [Amazon S3 Encryption Client](Amazon Simple Storage Service Developer GuideUsingClientSideEncryption.html)\. Amazon S3 also offers [server\-side encryption](Amazon Simple Storage Service Developer Guideserv-side-encryption.html)\. 
+ To protect all other types of data at their source, use the [AWS Encryption SDK](awscryp-choose-sdk.md)\.

When choosing an SDK or an encryption client library, remember that they are not compatible\. You cannot use one library to encrypt data and a different library to decrypt the data\.

**Topics**
+ [When To Use AWS KMS](awscryp-choose-kms.md)
+ [When To Use AWS CloudHSM](awscryp-choose-hsm.md)
+ [When To Use AWS Encryption SDK](awscryp-choose-sdk.md)
+ [When To Use DynamoDB Encryption Client](awscryp-choose-ddb.md)