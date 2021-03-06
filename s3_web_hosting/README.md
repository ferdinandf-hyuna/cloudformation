# AWS: Cloudformation: S3 Bucket Webhosting
This Cloudformation template and associated parameters file, will create two S3 buckets and allow a flat HTML web site (or static assets) to be served from one of these buckets.  The other bucket is used to re-direct traffic to the original bucket.

### Prerequisites

The script is designed to use a domain that is already registered and has a zone file in Route 53.  However, should have a domain registered with anotehr Domain Registrar, a parameter has been provided to turn off the creation of two Route 53 A records, so these can be manually created elsewhere.

### Parameters

- '**RootDomainName**' - Supply the name of the root domain registered in Route 53 e.g. 'domain.com' or 'awstutorial.cloud'
- '**Indexpage**' - Supply the name of the index page i.e. the first page of the Website. e.g. 'index.html'
- '**Errorpage**' - Supply the name of the error page i.e. the page displayed when 404s are encountered. e.g. 'error.html'
- '**LoggingBucket**' - Specify the name a bucket that the HTTP logs will reside in.  A bucket will be created with this name.
- '**AddToDNSZoneFile**' - This is a yes/no toggle.  'yes' means allowing the template to create A records in the zone file specified in Route 53.  However, if you aren't using Route 53 as a Domain Registrar or don't want this template to manage the records, choose 'no'.
- '**AddIAMGroupAndPolicy**' - This is a yes/no toggle.  'yes' means allow the template to create an IAM Group and Policy to allow any user to be able to to upload, edit and delete objects from the newly created S3 bucket.  Choose 'no' if you don't want this to be created.

### Deploy Template

Use the following command to validate the template;

`aws cloudformation validate-template --template-body file://s3_hosting_domain.json`

Once validated, use the following command to deploy the Cloudformation Stack;

`aws cloudformation create-stack --stack-name "S3-Hosting-Stack" --template-body file://s3_hosting_domain.json --parameters file://s3_hosting_parameters.json --capabilities CAPABILITY_NAMED_IAM`
