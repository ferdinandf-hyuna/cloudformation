# AWS: Cloudformation: S3 Bucket Webhosting
This Cloudformation template and associated parameters file, will create two S3 buckets and allow a flat HTML web site (or static assets) to be served from one of these buckets.  The other bucket is used to re-direct traffic to the original bucket.

### Prerequisites

The script is designed to use a domain that is already registered and has a zone file in Route 53.  However, should have a domain registered with anotehr Domain Registrar, a parameter has been provided to turn off the creation of two Route 53 A records, so these can be manually created elsewhere.

### Parameters

- '**RootDomainName**' - Supply the name of the root domain registered in Route 53 e.g. 'domain.com' or 'awstutorial.cloud'


	{
		"ParameterKey": "Indexpage",
		"ParameterValue": "index.html"		
	},
	{
		"ParameterKey": "Errorpage",
		"ParameterValue": "error.html"	
	},
    {
     	"ParameterKey": "AddToDNSZoneFile",
		"ParameterValue": "yes"	   
    },
    {
     	"ParameterKey": "LoggingBucket",
		"ParameterValue": "palindrome-logs"	   
    }
]
