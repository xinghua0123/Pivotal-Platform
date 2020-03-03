### Login PAS as admin
```shell
cf login -a <API_URL> -u <USERNAME> -p <PASSWORD> -o <ORG> -s <SPACE>
```
Example:
```shell
cf login --skip-ssl-validation -a https://api.sys.beverlyhills.cf-app.com -u admin -p <password> -o system -s system
```

### Create organization qouta
```shell
cf create-quota QUOTA [-m TOTAL_MEMORY] [-i INSTANCE_MEMORY] [-r ROUTES] [-s SERVICE_INSTANCES] [-a APP_INSTANCES] [--allow-paid-service-plans] [--reserved-route-ports RESERVED_ROUTE_PORTS]
```
Example:
```shell
cf create-quota org-quota -m 120G -r 500 -s 75
```

### Create new organization
```shell
cf create-org <org_name> -q <org_qouta_name> # -q will attach certain organization qouta to the newly created organization 
cf target -o <org_name> # targeting specific organization and manage all the spaces inside the organization
```

### Create space qouta
```shell
cf create-space-quota QUOTA [-i INSTANCE_MEMORY] [-m MEMORY] [-r ROUTES] [-s SERVICE_INSTANCES] [-a APP_INSTANCES] [--allow-paid-service-plans] [--reserved-route-ports RESERVED_ROUTE_PORTS]
```

Example:
```shell
cf create-space-quota space-quota -i 2G -m 30G -s 5 -a 15 -r 15
```

### Create new space
```shell
cf create-space SPACE [-o ORG] [-q SPACE_QUOTA]
```
Example:
```shell
cf create-space team-1 -o "dell-hackathon" -q "space-quota" # -q will attach certain space qouta to the newly created space
```

### Create user
```shell
cf create-user <username> <password>
cf set-space-role <username> <org_name> <space_name> <space-role> 
```
The following describes each type of user role in PAS:

- Admin: Perform operational actions on all orgs and spaces using the Cloud Controller API. Assigned the cloud_controller.admin scope in UAA.
- Admin Read-Only: Read-only access to all Cloud Controller API resources. Assigned the cloud_controller.admin_read_only scope in UAA.
- Global Auditor: Read-only access to all Cloud Controller API resources except for secrets, such as environment variables. The Global Auditor role cannot access those values. Assigned the cloud_controller.global_auditor scope in UAA.
- Org Managers: Administer the org.
- Org Auditors: Read-only access to user information and org quota usage information.
- Org Users: Read-only access to the list of other org users and their roles. When an Org Manager gives a person an Org or Space role, that person automatically receives Org User status in that org.
- Space Managers: Administer a space within an org.
- Space Developers: Manage apps, services, and space-scoped service brokers in a space.
- Space Auditors: Read-only access to a space.
