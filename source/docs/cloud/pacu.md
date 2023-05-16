# PACU

[Pacu](https://github.com/RhinoSecurityLabs/pacu) is an open-source Python exploitation framework for AWS cloud environments. It can be used for reconnaissance, 
privilege escalation, lateral movement, exploitation, and evasion in the cloud. Pacu uses modules to do things like 

* Enumerate users, roles, resources, lambda data, and s3 buckets
* Identify privilege paths and misconfigurations
* Perform injection 
* Gain persistence within the cloud

## Usage

1. Change to the pacu directory and create a new session
2. Import some keys we found in an internal repository
3. Run the aws__enum_account module to verify the keys are working
4. Find out current permissions by populating the database with the iam__enum_permissions command
5. Run the iam__privesc_scan module for additional checks
6. Choose from the attack options Pacu has confirmed exist, or the potential attacks it listed for privesc
7. Enumerate other users and policies to determine what access they have, with iam__enum_users_roles_policies_groups --users
8. Use the data command to query information about services, configurations, and more from the Pacu database
9. Leverage the access to move into the compute resources
10. ...
