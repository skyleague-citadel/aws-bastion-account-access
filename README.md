# Client Access Template

Template to allow SkyLeague team secure access to your AWS Organization / Accounts.

CloudFormation template URL on S3:

`https://`

In order to design, build and embed our solutions in your AWS Organization and/or AWS Accounts, SkyLeague uses a "bastion account", a new AWS Account created in the SkyLeague AWS Organization, dedicated to you as a client, which will be used by the SkyLeague team for very limited read-only access.

This CloudFormation template (and accompanying Terraform) contains an IAM role which provides basic read-only access for debugging, monitoring and troubleshooting.

For convenience and standardization, the IAM role uses a couple of IAM Managed Policies maintained by AWS:

- `arn:aws:iam::aws:policy/SecurityAudit`: access to security related meta-data, e.g. can list EC2s running but cannot execute actions on them, also see https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html#jf_security-auditor
- `arn:aws:iam::aws:policy/job-function/ViewOnlyAccess`: ability to list resources, but not see their contents, e.g. can see a list of DynamoDB tables, but cannot access items, also see: https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html#jf_view-only-user

We deliberately do not use `arn:aws:iam::aws:policy/ReadOnlyAccess` (and neither should you) because it has very wide permissions in e.g. downloading full S3 bucket object contents (data exfil!) and running Scan queries on DynamoDB (unexpected performance and cost impact!).

Feel free to submit PR's if you see things that can be improved or create an issue if you have any questions or suggestions!

See you in the Cloud ;)

The SkyLeague Founders.
