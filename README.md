# route53-dyndns

Bash script to get public IP from icanhazip.com and update an AWS Route53 hostname using the AWS CLI.

## Installation

Requirements: 
- aws cli (pip install awscli or apt-get install awscli)
- curl
- Configure your AWS keys with `aws configure`

```
cd <somewhere on your file system such as /opt/>
git clone https://github.com/ctrlrsf/route53-dyndns.git
```

## Sample usage

AWS_ZONE_ID and DYN_HOST environment variables are required.
- AWS_ZONE_ID - The AWS Route53 zone ID
- DYN_HOST - the hostname / resource record name that should be updated

```
AWS_ZONE_ID=xxxxxxxxx DYN_HOST=some.host.name.com /opt/route53-dyndns/update-dns
```

## Sample Crontab

```
SHELL=/bin/bash
# Update dynamic DNS if necessary
*/5 * * * * AWS_ZONE_ID=xxxxxxxxx DYN_HOST=some.host.name.com /opt/route53-dyndns/update-dns |& ts >> ~/.route53-dyndns.log
```
