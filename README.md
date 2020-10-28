## Amazon's Photo Upload Tutorial
This will be built off of the directory: ../amazon_view_photo. While not a prequisite, my original attempt to use the upload photo tutorial failed, so this attempt will try to remedy that by building 
off of a successful implementation

### Important Links
- The tutorial for viewing photo albums can be found [here](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/s3-example-photos-view.html)
	- I followed this tutorial in creating the needed Cognito Identity Pool [here](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/getting-started-browser.html#getting-started-browser-create-identity-pool)
	- This [site](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/) has the most recent information regarding the AWS SDK
- The tutorial for uploading files can be found [here](https://docs.aws.amazon.com/sdk-for-javascript/v2/developer-guide/s3-example-photo-album.html)
### Amazon Resource Information
- This is the information regarded to the amazon resources used
	- S3 Bucket
		- bucket name: viewphotobucket
		- Updated CORS Configuration: 
			<?xml version="1.0" encoding="UTF-8"?>
			<CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/">
			    <CORSRule>
			        <AllowedOrigin>*</AllowedOrigin>
			        <AllowedMethod>POST</AllowedMethod>
			        <AllowedMethod>GET</AllowedMethod>
			        <AllowedMethod>PUT</AllowedMethod>
			        <AllowedMethod>DELETE</AllowedMethod>
			        <AllowedMethod>HEAD</AllowedMethod>
			        <AllowedHeader>*</AllowedHeader>
			        <ExposeHeader>ETag</ExposeHeader>
			    </CORSRule>
			</CORSConfiguration>
	- IAM 
		- new policy name: UploadBucketPolicy
			- allows s3:DeleteObject, GetObject, ListBucket, and Put object on our bucket
	- Cognito Identity Pool
		- pool name: ViewPhotoIdentity
		- Unauthorized Role: Cognito_ViewPhotoIdentityUnauth_Role
		- sample code: 
			// Initialize the Amazon Cognito credentials provider
			AWS.config.region = 'us-east-1'; // Region
			AWS.config.credentials = new AWS.CognitoIdentityCredentials({
			    IdentityPoolId: 'us-east-1:7bbbddf8-b270-4cf2-af9b-c8a4bd406f12',
			});
		- polly.html was implemented just to test that the Cognito Identity Pool functioned properly
