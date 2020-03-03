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

