{
  "protoPayload": {
    "@type": "type.googleapis.com/google.cloud.audit.AuditLog",
    "status": {
      "code": 9,
      "message": "no entitlements are found for organization eqx-entapg-nonprod. Select a different billing type to proceed or contact Apigee sales to entitle organization eqx-entapg-nonprod with the appropriate subscription at https://cloud.google.com/contact?direct=true&pre_product=apigee&int_campaign=contact-sales: failed precondition"
    },
    "authenticationInfo": {
      "principalEmail": "sa-hlx-apigee-deploy-nprd@eqx-helix-svc-act-dev.iam.gserviceaccount.com",
      "serviceAccountKeyName": "//iam.googleapis.com/projects/eqx-helix-svc-act-dev/serviceAccounts/sa-hlx-apigee-deploy-nprd@eqx-helix-svc-act-dev.iam.gserviceaccount.com/keys/c9d92daef6275905a378cc82fa872a0c6b584aa2",
      "principalSubject": "serviceAccount:sa-hlx-apigee-deploy-nprd@eqx-helix-svc-act-dev.iam.gserviceaccount.com",
      "oauthInfo": {
        "oauthClientId": "107155986870950139715"
      }
    },
    "requestMetadata": {
      "callerIp": "10.249.220.196",
      "callerSuppliedUserAgent": "curl/7.68.0,gzip(gfe)",
      "callerNetwork": "//compute.googleapis.com/projects/nonprod-shared-l2/global/networks/__unknown__",
      "requestAttributes": {
        "time": "2025-10-29T11:28:40.204532884Z",
        "auth": {}
      },
      "destinationAttributes": {}
    },
    "serviceName": "apigee.googleapis.com",
    "methodName": "google.cloud.apigee.v1.OrganizationService.CreateOrganization",
    "authorizationInfo": [
      {
        "resource": "projects/eqx-entapg-nonprod",
        "permission": "apigee.organizations.create",
        "granted": true,
        "resourceAttributes": {},
        "permissionType": "ADMIN_WRITE"
      }
    ],
    "resourceName": "projects/eqx-entapg-nonprod",
    "request": {
      "organization": {
        "billingType": "SUBSCRIPTION",
        "name": "eqx-entapg-nonprod",
        "apiConsumerDataLocation": "us-west1",
        "runtimeType": "HYBRID"
      },
      "parent": "projects/eqx-entapg-nonprod",
      "@type": "type.googleapis.com/google.cloud.apigee.v1.CreateOrganizationRequest"
    },
    "resourceLocation": {
      "currentLocations": [
        "us",
        "us-west1"
      ]
    }
  },
  "insertId": "affpvdg3hk",
  "resource": {
    "type": "audited_resource",
    "labels": {
      "service": "apigee.googleapis.com",
      "project_id": "eqx-entapg-nonprod",
      "method": "google.cloud.apigee.v1.OrganizationService.CreateOrganization"
    }
  },
  "timestamp": "2025-10-29T11:28:40.728235286Z",
  "severity": "ERROR",
  "logName": "projects/eqx-entapg-nonprod/logs/cloudaudit.googleapis.com%2Factivity",
  "receiveTimestamp": "2025-10-29T11:28:40.728235286Z"
}
