# SkyLeague Bastion Account Access Template

Template to allow SkyLeague team secure access to your AWS Organization / Accounts.

CloudFormation template URL on SkyLeague S3:

`https://`

In order to design, build and embed our solutions in your AWS Organization and/or AWS Accounts, SkyLeague uses a "bastion account", a new AWS Account created in the SkyLeague AWS Organization, dedicated to you as a client, which will be used by the SkyLeague team for secure, very limited read-only access.

This CloudFormation template (and accompanying Terraform) contains a single IAM role which provides secure, very limited, read-only access for debugging, monitoring and troubleshooting.

You or your cloud engineering team can review and deploy this role to any AWS Account you would like to provide the SkyLeague account secure very limited read-only access to.

For convenience and standardization, the IAM role uses several IAM Managed Policies created and maintained by AWS:

- `arn:aws:iam::aws:policy/SecurityAudit`: access to security related meta-data, e.g. can list EC2s running but cannot execute actions on them, also see https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html#jf_security-auditor
- `arn:aws:iam::aws:policy/job-function/ViewOnlyAccess`: ability to list resources, but not see their contents, e.g. can see a list of DynamoDB tables, but cannot access its items, also see: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html#jf_view-only-user

**Note:** We deliberately _do not use_ `arn:aws:iam::aws:policy/ReadOnlyAccess` (and neither should you!) because it has very wide permissions in e.g. downloading full S3 bucket object contents (data exfil risk!) and running Scan queries on DynamoDB (unintended performance and cost impact!).

Feel free to submit PR's if you see things that can be improved or create an issue if you have any questions or suggestions!

See you in the Cloud ;)

The SkyLeague Founders.
