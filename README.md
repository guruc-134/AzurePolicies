# AzurePolicies

Open AI SL - 19
{
  "mode": "Indexed",
  "policyRule": {
    "if": {
      "allOf": [
        {
          "field": "type",
          "equals": "Microsoft.CognitiveServices/accounts"
        },
        {
          "field": "kind",
          "equals": "OpenAI"
        },
        {
          "field": "privateEndpoints",
          "notExists": true
        }
      ]
    },
    "then": {
      "effect": "deny",
      "details": "Deployment of OpenAI resources is only allowed if a private endpoint is attached."
    }
  },
  "parameters": {}
}

Open AI SL - 20
{
  "mode": "Indexed",
  "policyRule": {
    "if": {
      "allOf": [
        {
          "field": "type",
          "equals": "Microsoft.CognitiveServices/accounts"
        },
        {
          "field": "kind",
          "equals": "OpenAI"
        },
        {
          "field": "privateEndpoints",
          "notExists": true
        }
      ]
    },
    "then": {
      "effect": "audit",
      "details": "Deployment of OpenAI resources with public endpoints is discouraged. Consider attaching a private endpoint for enhanced security."
    }
  },
  "parameters": {}
}

Open AI SL - 21
{
  "mode": "Indexed",
  "policyRule": {
    "if": {
      "allOf": [
        {
          "field": "type",
          "equals": "Microsoft.CognitiveServices/accounts"
        },
        {
          "field": "kind",
          "equals": "OpenAI"
        },
        {
          "field": "properties.publicNetworkAccessEnabled",
          "equals": true
        },
        {
          "field": "privateDnsZoneResourceReference",
          "notExists": true
        }
      ]
    },
    "then": {
      "effect": "deny",
      "details": "Deployment of OpenAI resources with public network access and no private DNS zone reference is denied. Ensure private access and DNS resolution are configured securely."
    }
  },
  "parameters": {}
}


