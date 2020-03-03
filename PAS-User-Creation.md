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
The following describes each type of space role in PAS:

- Space Managers: Administer a space within an org.
- Space Developers: Manage apps, services, and space-scoped service brokers in a space.
- Space Auditors: Read-only access to a space.
