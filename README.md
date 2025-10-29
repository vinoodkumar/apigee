Apigee Hybrid Org Creation – Root Cause Identified

I completed end-to-end testing of the Apigee Hybrid org creation workflow.
The payload and API endpoint are correct and the call successfully reaches the Apigee control plane (us-apigee.googleapis.com).
Audit logs confirm the request was authorized and executed by our service account:
sa-hlx-apigee-deploy-nprd@eqx-helix-svc-act-dev.iam.gserviceaccount.com.

However, the Apigee API responded with a “failed precondition” error:

no entitlements are found for organization eqx-entapg-nonprod.
Select a different billing type or contact Apigee Sales to entitle the organization.

This means that while the project eqx-entapg-nonprod has Apigee API access,
it does not have an active Apigee Hybrid (Subscription) entitlement under its current billing account.

I’ve already spoken with the GCP team — they’ve reviewed the audit logs and will raise a support case after checking internally with Dhanraj to have the entitlement enabled.

Once the entitlement is active, the same workflow will work without any changes.
