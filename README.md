- name: Create Apigee Organization (Data Residency)
  if: steps.validate_org.outputs.org_exists == 'false'
  id: create_org
  run: |
    echo "🚀 Creating Apigee Organization with Data Residency..."
    echo "Control Plane: ${CONTROL_PLANE_LOCATION}, Consumer Region: ${CONSUMER_DATA_REGION}"

    RESPONSE=$(curl -s -w "\n%{http_code}" -X POST \
      -H "Authorization: Bearer ${{ steps.token.outputs.token }}" \
      -H "Content-Type: application/json" \
      -d '{
        "name": "'"${ORG_NAME}"'",
        "billingType": "'"${BILLING_TYPE}"'",
        "runtimeType": "'"${RUNTIMETYPE}"'",
        "controlPlaneRegion": "'"${CONTROL_PLANE_LOCATION}"'",
        "apiConsumerDataLocation": "'"${CONSUMER_DATA_REGION}"'"
      }' \
      "https://${CONTROL_PLANE_LOCATION}-apigee.googleapis.com/v1/organizations?parent=projects/${APIGEE_PROJECT}")

    BODY=$(echo "$RESPONSE" | head -n1)
    CODE=$(echo "$RESPONSE" | tail -n1)

    echo "--------------------"
    echo "HTTP Status: $CODE"
    echo "Raw Response:"
    echo "$BODY"
    echo "--------------------"

    if [ "$CODE" -eq 409 ]; then
      echo "✅ Organization already exists. Skipping creation."
      exit 0
    elif [ "$CODE" -ge 400 ]; then
      echo "❌ Org creation failed with HTTP $CODE"
      if echo "$BODY" | jq -e '.error.message' >/dev/null 2>&1; then
        echo "Error details:"
        echo "$BODY" | jq '.error'
      else
        echo "Raw (non-JSON) response:"
        echo "$BODY"
      fi
      exit 1
    fi
