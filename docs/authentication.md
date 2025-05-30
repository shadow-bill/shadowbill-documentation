# Authentication

Shadowbill uses API key-based authentication to secure all endpoints. This guide covers how to authenticate your requests, manage your API keys, and implement security best practices.

## Bearer tokens

All API requests must include an API key in the Authorization header using the Bearer token scheme:

```http
Authorization: Bearer <your_api_key>
```

Example Request:

```http
GET /organization/1
Host: api.shadowbill.com
Authorization: Bearer live_ok_1234567890abcdef
Content-Type: application/json
```

## API Key Types

The service provides different types of API keys for various use cases:

#### Organization Keys (Admin)

These are used for administrative operations and backend services:

  * Prefix: live_ok_ (live) or test_ok_ (test)
  * Scope: Full access to organization resources
  * Example permissions: Create/manage projects, billing, user management

#### Application Keys (Standard)

These are used for Application-specific metering and integrations, and will be the most common key type that you interact with:

  * Prefix: live_ak_ (live) or test_ak_ (test)
  * Scope: Limited to specific project resources
  * Example permissions: Usage recording, analytics viewing, key management within project

#### Read-Only Keys

These are generated for your non-technical employees to use when logging into Shadowbill. They can use these keys for viewing dashboards, reporting tools, monitoring systems, etc:

  * Prefix: live_rok_ (live) or test_rok_ (test)
  * Scope: Read-only access to usage data and analytics
  * Example permissions: View usage, analytics, billing data (no modifications)

#### Customer Keys

These are provided to your customers when you want to display generated invoices to your customers:

  * Prefix: live_ck_ (live) or test_ck_ (test)
  * Scope: Read-only access to a specific customer's data
  * Example permissions: View invoices, forward billing estimates