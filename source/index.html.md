---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the GrowthGenius API! You can use our API to access GrowthGenius API endpoints, which can get information on various contacts, accounts, and campaigns.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
```

> Make sure to replace `YOUR API KEY HERE` with your API key.

growthgenius uses API keys to allow access to the API. You can register a new growthgenius API key at our [developer portal](https://api.growthgenius.com/integrations/v1/developers).

growthgenius expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YOUR API KEY HERE`

<aside class="notice">
You must replace <code>YOUR API KEY HERE</code> with your personal API key.
</aside>

# Contact API

A Contact is a person your team has explicitly added to your database. It can be from prospected from GrowthGenius, manually added by your team, or created by the API.

## Create a Contact

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "first_name": "Elon",
    "last_name": "Musk",
    "title": "CEO",
    "organization_name": "Tesla"
}' "https://api.growthgenius.com/integrations/v1/contacts"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "contact": {
    "annual_revenue": null,
    "bad_data_reason": null,
    "city": null,
    "company_address": null,
    "company_city": "Melbourne",
    "company_country": "New Zealand",
    "company_linkedin_url": "linkedin.com/company/anz",
    "company_name": "Anz",
    "company_name_informal": null,
    "company_state": "Victoria",
    "contact_account": { "id": 485499, "status": "cold" },
    "contact_account_id": 485499,
    "corporate_phone": null,
    "country": "New Zealand",
    "created_at": "2021-01-19T17:06:25.730-05:00",
    "custom1": null,
    "custom2": null,
    "custom3": null,
    "custom4": null,
    "custom5": null,
    "custom6": null,
    "custom7": null,
    "custom8": null,
    "custom9": null,
    "email": "tony.barkley@anz.com",
    "email_confidence": 100,
    "email_status": null,
    "employee_count": null,
    "facebook_url": null,
    "first_name": "Tony",
    "first_phone": null,
    "full_name": "Tony Barkley",
    "home_phone": null,
    "id": 1102755,
    "industry": "Banking",
    "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
    "label_names": null,
    "last_name": "Barkley",
    "linkedin_url": "linkedin.com/in/tony-barkley-92824584",
    "linkedin_username": "tony-barkley-92824584",
    "lists": null,
    "mobile_phone": "NaN",
    "name": "Tony Barkley",
    "other_phone": null,
    "prospect_id": 236811124,
    "seo_description": null,
    "stage": null,
    "state": "Bay Of Plenty",
    "status": "Ongoing",
    "technologies": "",
    "title": "Relationship Associate",
    "twitter_url": null,
    "unstructured_data": null,
    "updated_at": "2021-01-19T17:07:20.529-05:00",
    "upload_identifier": null,
    "user_id": 1,
    "website": "anz.com",
    "work_phone": null
  }
}
```

GrowthGenius does not run any deduplication during CREATE. If your record contains the same email or name+company as an existing contact, GrowthGenius will create a new contact instead of updating the existing contact.

### HTTP Request

`POST https://api.growthgenius.com/integrations/v1/contacts`

### Query Parameters

| Parameter    | Description                                                                                                                                                                                                                                                     | Example                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| first_name   | First Name                                                                                                                                                                                                                                                      | Elon                       |
| last_name    | Last Name                                                                                                                                                                                                                                                       | Musk                       |
| title        | Title                                                                                                                                                                                                                                                           | CEO                        |
| account_id   | ID of the Account (Optional)                                                                                                                                                                                                                                    | "583f2f7ed9ced98ab5bfXXXX" |
| account_name | Account Name                                                                                                                                                                                                                                                    | Tesla                      |
| email        | Email                                                                                                                                                                                                                                                           | elon@tesla.com             |
| website_url  | The organization website Apollo can use to enrich data for you. DO NOT pass in personal social media URLs such as "http://www.linkedin.com/profile_url", or your data will be incorrectly enriched. This argument will be ignored if you pass in a valid email. | "http://www.tesla.com"     |

## Update a Contact

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.get()
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "first_name": "Elon",
    "last_name": "Musk",
    "title": "CEO",
    "organization_name": "Tesla"
}' "https://api.growthgenius.com/integrations/v1/contacts/YOUR-CONTACT-ID"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "contact": {
    "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
    "full_name": "Elon Musk",
    "fist_name": "Elon",
    "last_name": "Musk",
    "email": "elon@tesla.com",
    "//": "..."
  }
}
```

This endpoint updates a contact.

### HTTP Request

`PATCH https://api.growthgenius.com/integrations/v1/contacts/:id`

### Query Parameters

| Parameter    | Description                                                                                                                                                                                                                                                     | Example                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| first_name   | First Name                                                                                                                                                                                                                                                      | Elon                       |
| last_name    | Last Name                                                                                                                                                                                                                                                       | Musk                       |
| title        | Title                                                                                                                                                                                                                                                           | CEO                        |
| account_id   | ID of the Account (Optional)                                                                                                                                                                                                                                    | "583f2f7ed9ced98ab5bfXXXX" |
| account_name | Account Name                                                                                                                                                                                                                                                    | Tesla                      |
| email        | Email                                                                                                                                                                                                                                                           | elon@tesla.com             |
| website_url  | The organization website Apollo can use to enrich data for you. DO NOT pass in personal social media URLs such as "http://www.linkedin.com/profile_url", or your data will be incorrectly enriched. This argument will be ignored if you pass in a valid email. | "http://www.tesla.com"     |

## Delete a Contact

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.get()
```

```shell
curl "https://api.growthgenius.com/integrations/v1/contacts" \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "contact": {
    "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
    "full_name": "Elon Musk",
    "fist_name": "Elon",
    "last_name": "Musk",
    "email": "elon@tesla.com",
    "//": "..."
  }
}
```

This endpoint updates a contact.

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/contacts/:id`

### Query Parameters

| Parameter    | Description                                                                                                                                                                                                                                                     | Example                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| first_name   | First Name                                                                                                                                                                                                                                                      | Elon                       |
| last_name    | Last Name                                                                                                                                                                                                                                                       | Musk                       |
| title        | Title                                                                                                                                                                                                                                                           | CEO                        |
| account_id   | ID of the Account (Optional)                                                                                                                                                                                                                                    | "583f2f7ed9ced98ab5bfXXXX" |
| account_name | Account Name                                                                                                                                                                                                                                                    | Tesla                      |
| email        | Email                                                                                                                                                                                                                                                           | elon@tesla.com             |
| website_url  | The organization website Apollo can use to enrich data for you. DO NOT pass in personal social media URLs such as "http://www.linkedin.com/profile_url", or your data will be incorrectly enriched. This argument will be ignored if you pass in a valid email. | "http://www.tesla.com"     |

## Get All Contacts

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.get()
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "q_keywords": "Elon Musk, CEO, Tesla",
    "sort_by_field": "contact_last_activity_date",
    "sort_ascending": false
}' "https://api.growthgenius.com/integrations/v1/contacts/search"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "contacts": [
    {
      "id": "5da8ceXXXXXXXXXXXXXXXXXX",
      "first_name": "Tim",
      "last_name": "Zheng",
      "name": "Tim Zheng",
      "linkedin_url": "http://www.linkedin.com/in/tim-zheng-677ba010",
      "title": "Founder & CEO",
      "contact_stage_id": "5c48fbXXXXXXXXXXXXXXXXXX",
      "owner_id": "5c1004XXXXXXXXXXXXXXXXXX",
      "person_id": "5f2b88XXXXXXXXXXXXXXXXXX",
      "email_needs_tickling": false,
      "organization_name": "Apollo",
      "source": "search",
      "original_source": "email_import",
      "organization_id": "5e66b6XXXXXXXXXXXXXXXXXX",
      "headline": "Founder & CEO at Apollo",
      "photo_url": "https://some-url.fyvrk",
      "present_raw_address": "San Francisco, California, United States",
      "linkedin_uid": "38777275",
      "extrapolated_email_confidence": 0,
      "salesforce_id": "0031UXXXXXXXXXXXXXX",
      "salesforce_lead_id": null,
      "salesforce_contact_id": "0031UXXXXXXXXXXXXXXX",
      "salesforce_account_id": "0011UXXXXXXXXXXXXXXX",
      "salesforce_owner_id": "0051UXXXXXXXXXXXXXXX",
      "created_at": "2019-10-17T20:25:07.594Z",
      "lead_request_id": null,
      "test_predictive_score": null,
      "emailer_campaign_ids": [],
      "email_manually_changed": false,
      "direct_dial_status": null,
      "direct_dial_enrichment_failed_at": null,
      "email_status": "verified",
      "account_id": "5f1fadXXXXXXXXXXXXXXXXXX",
      "last_activity_date": "2018-06-26T16:30:35.000+00:00",
      "hubspot_vid": null,
      "hubspot_company_id": null,
      "sanitized_phone": null,
      "merged_crm_ids": [],
      "typed_custom_fields": {
        "5d856eXXXXXXXXXXXXXXXXXX": "Tim Zheng"
      },
      "updated_at": "2020-07-28T04:44:51.448Z",
      "queued_for_crm_push": false,
      "starred_by_user_ids": [],
      "suggested_from_rule_engine_config_id": null,
      "label_ids": [],
      "has_pending_email_arcgate_request": false,
      "has_email_arcgate_request": false,
      "existence_level": "full",
      "email": "random@somedomain.com",
      "salesforce_record_url": "https://na85.salesforce.com/0031UXXXXXXXXXXXXXXXXXX",
      "contact_campaign_statuses": [],
      "state": "California",
      "city": "San Francisco",
      "country": "United States",
      "account": {
        "id": "5f1fadXXXXXXXXXXXXXXXXXX",
        "name": "Apollo",
        "website_url": "http://www.apollo.io",
        "blog_url": null,
        "angellist_url": null,
        "linkedin_url": "http://www.linkedin.com/company/apolloio",
        "twitter_url": "https://twitter.com/MeetApollo/",
        "facebook_url": "https://www.facebook.com/MeetApollo/",
        "languages": [],
        "alexa_ranking": 77520,
        "phone": null,
        "linkedin_uid": "18511550",
        "publicly_traded_symbol": null,
        "publicly_traded_exchange": null,
        "logo_url": "https://apollo-server.com/uploads/pictures/5f0265XXXXXXXXXXXXXXXXXX/picture",
        "crunchbase_url": null,
        "primary_domain": "apollo.io",
        "starred_by_user_ids": [],
        "persona_counts": {},
        "domain": "apollo.io",
        "team_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "typed_custom_fields": {},
        "organization_id": "5e66b6XXXXXXXXXXXXXXXXXX",
        "account_stage_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "source": "salesforce",
        "original_source": "salesforce",
        "owner_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "created_at": "2020-07-28T04:44:13.821Z",
        "phone_status": "no_status",
        "test_predictive_score": null,
        "hubspot_id": null,
        "salesforce_id": "0011UXXXXXXXXXX",
        "salesforce_owner_id": "0051UXXXXXXXXXX",
        "parent_account_id": null,
        "account_playbook_statuses": [],
        "existence_level": "full",
        "label_ids": [],
        "modality": "account",
        "salesforce_record_url": "https://na85.salesforce.com/0011UXXXXXXXXXXX"
      },
      "organization": {
        "id": "5e66b6XXXXXXXXXXXXXXXXXX",
        "name": "Apollo",
        "website_url": "http://www.apollo.io",
        "blog_url": null,
        "angellist_url": null,
        "linkedin_url": "http://www.linkedin.com/company/apolloio",
        "twitter_url": "https://twitter.com/MeetApollo/",
        "facebook_url": "https://www.facebook.com/MeetApollo/",
        "languages": [],
        "alexa_ranking": 77520,
        "phone": null,
        "linkedin_uid": "18511550",
        "publicly_traded_symbol": null,
        "publicly_traded_exchange": null,
        "logo_url": "https://apollo-server.com/uploads/pictures/5f0265XXXXXXXXXXXXXXXXXX/picture",
        "crunchbase_url": null,
        "primary_domain": "apollo.io",
        "starred_by_user_ids": [],
        "persona_counts": {}
      },
      "phone_numbers": [],
      "account_phone_note": null,
      "contact_job_change_event": null
    }
  ],
  "breadcrumbs": [
    {
      "label": "Contains Keywords",
      "signal_field_name": "q_keywords",
      "value": "Tim Zheng, CEO, Apollo",
      "display_name": "Tim Zheng, CEO, Apollo"
    }
  ],
  "partial_results_only": false,
  "disable_eu_prospecting": false,
  "partial_results_limit": 10000,
  "pagination": {
    "page": 1,
    "per_page": 25,
    "total_entries": 1,
    "total_pages": 1
  },
  "num_fetch_result": null
}
```

This endpoint retrieves all contacts.

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/contacts`

### Query Parameters

| Parameter         | Description                                                                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| q_keywords        | The contact's name, title, company, or email                                                                                                                  |
| contact_stage_ids | An array of stage ids the contact must belong to. Refer to /contact_stages to get a list of possible stage ids.                                               |
| sort_by_field     | Possible values: "contact_last_activity_date", "contact_email_last_opened_at", "contact_email_last_clicked_at", "contact_created_at", or "contact_updated_at" |
| sort_ascending    | Possible values: true or false                                                                                                                                |
| page              | which page to return. Defaults to 1                                                                                                                           |
| per_page          | how many contacts to return per page. Max = 200                                                                                                               |

## Get a Specific Contact

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get(2)
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.get(2)
```

```shell
curl "https://api.growthgenius.com/integrations/v1/contacts/2" \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let max = api.contacts.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific contact.

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/contacts/<ID>`

### URL Parameters

| Parameter | Description                       |
| --------- | --------------------------------- |
| ID        | The ID of the contact to retrieve |

## Delete a Specific Contact

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.delete(2)
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.delete(2)
```

```shell
curl "https://api.growthgenius.com/integrations/v1/contacts/2" \
  -X DELETE \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let max = api.contacts.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific contact.

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/contacts/<ID>`

### URL Parameters

| Parameter | Description                     |
| --------- | ------------------------------- |
| ID        | The ID of the contact to delete |

# Message API

A Message is a message your team has created in a campaign.

## Create a Message

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.get
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE"
}' "https://api.growthgenius.com/integrations/v1/messages"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let messages = api.messages.get();
```

> The above command returns JSON structured like this:

```json
{
  "message": "Hello world!"}
}
```

GrowthGenius does not run any deduplication during CREATE. If your record contains the same email or name+company as an existing message, GrowthGenius will create a new message instead of updating the existing message.

### HTTP Request

`POST https://api.growthgenius.com/integrations/v1/messages`

### Query Parameters

| Parameter  | Description | Example |
| ---------- | ----------- | ------- |
| contact_id | Contact ID  | 123     |
| user_id    | User ID     | 256     |

## Update a message

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.messages.get()
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "first_name": "Elon",
    "last_name": "Musk",
    "title": "CEO",
    "organization_name": "Tesla"
}' "https://api.growthgenius.com/integrations/v1/messages/YOUR-message-ID"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let messages = api.messages.get();
```

> The above command returns JSON structured like this:

```json
{
  "message": {
    "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
    "full_name": "Elon Musk",
    "fist_name": "Elon",
    "last_name": "Musk",
    "email": "elon@tesla.com",
    "//": "..."
  }
}
```

This endpoint updates a message.

### HTTP Request

`PATCH https://api.growthgenius.com/integrations/v1/messages/:id`

### Query Parameters

| Parameter  | Description | Example |
| ---------- | ----------- | ------- |
| contact_id | Contact ID  | 123     |
| user_id    | User ID     | 256     |

## Delete a message

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.messages.get()
```

```shell
curl "https://api.growthgenius.com/integrations/v1/messages?contact_id=123&user_id=456" \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let messages = api.messages.get();
```

> The above command returns JSON structured like this:

```json
{
  "message": {
    "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
    "full_name": "Elon Musk",
    "fist_name": "Elon",
    "last_name": "Musk",
    "email": "elon@tesla.com",
    "//": "..."
  }
}
```

This endpoint updates a message.

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/messages/:id`

### Query Parameters

| Parameter  | Description | Example |
| ---------- | ----------- | ------- |
| contact_id | Contact ID  | 123     |
| user_id    | User ID     | 256     |

## Get All messages

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.messages.get()
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "q_keywords": "Elon Musk, CEO, Tesla",
    "sort_by_field": "message_last_activity_date",
    "sort_ascending": false
}' "https://api.growthgenius.com/integrations/v1/messages/search"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let messages = api.messages.get();
```

> The above command returns JSON structured like this:

```json
{
  "messages": [
    {
      "id": "5da8ceXXXXXXXXXXXXXXXXXX",
      "first_name": "Tim",
      "last_name": "Zheng",
      "name": "Tim Zheng",
      "linkedin_url": "http://www.linkedin.com/in/tim-zheng-677ba010",
      "title": "Founder & CEO",
      "message_stage_id": "5c48fbXXXXXXXXXXXXXXXXXX",
      "owner_id": "5c1004XXXXXXXXXXXXXXXXXX",
      "person_id": "5f2b88XXXXXXXXXXXXXXXXXX",
      "email_needs_tickling": false,
      "organization_name": "Apollo",
      "source": "search",
      "original_source": "email_import",
      "organization_id": "5e66b6XXXXXXXXXXXXXXXXXX",
      "headline": "Founder & CEO at Apollo",
      "photo_url": "https://some-url.fyvrk",
      "present_raw_address": "San Francisco, California, United States",
      "linkedin_uid": "38777275",
      "extrapolated_email_confidence": 0,
      "salesforce_id": "0031UXXXXXXXXXXXXXX",
      "salesforce_lead_id": null,
      "salesforce_message_id": "0031UXXXXXXXXXXXXXXX",
      "salesforce_account_id": "0011UXXXXXXXXXXXXXXX",
      "salesforce_owner_id": "0051UXXXXXXXXXXXXXXX",
      "created_at": "2019-10-17T20:25:07.594Z",
      "lead_request_id": null,
      "test_predictive_score": null,
      "emailer_campaign_ids": [],
      "email_manually_changed": false,
      "direct_dial_status": null,
      "direct_dial_enrichment_failed_at": null,
      "email_status": "verified",
      "account_id": "5f1fadXXXXXXXXXXXXXXXXXX",
      "last_activity_date": "2018-06-26T16:30:35.000+00:00",
      "hubspot_vid": null,
      "hubspot_company_id": null,
      "sanitized_phone": null,
      "merged_crm_ids": [],
      "typed_custom_fields": {
        "5d856eXXXXXXXXXXXXXXXXXX": "Tim Zheng"
      },
      "updated_at": "2020-07-28T04:44:51.448Z",
      "queued_for_crm_push": false,
      "starred_by_user_ids": [],
      "suggested_from_rule_engine_config_id": null,
      "label_ids": [],
      "has_pending_email_arcgate_request": false,
      "has_email_arcgate_request": false,
      "existence_level": "full",
      "email": "random@somedomain.com",
      "salesforce_record_url": "https://na85.salesforce.com/0031UXXXXXXXXXXXXXXXXXX",
      "message_campaign_statuses": [],
      "state": "California",
      "city": "San Francisco",
      "country": "United States",
      "account": {
        "id": "5f1fadXXXXXXXXXXXXXXXXXX",
        "name": "Apollo",
        "website_url": "http://www.apollo.io",
        "blog_url": null,
        "angellist_url": null,
        "linkedin_url": "http://www.linkedin.com/company/apolloio",
        "twitter_url": "https://twitter.com/MeetApollo/",
        "facebook_url": "https://www.facebook.com/MeetApollo/",
        "languages": [],
        "alexa_ranking": 77520,
        "phone": null,
        "linkedin_uid": "18511550",
        "publicly_traded_symbol": null,
        "publicly_traded_exchange": null,
        "logo_url": "https://apollo-server.com/uploads/pictures/5f0265XXXXXXXXXXXXXXXXXX/picture",
        "crunchbase_url": null,
        "primary_domain": "apollo.io",
        "starred_by_user_ids": [],
        "persona_counts": {},
        "domain": "apollo.io",
        "team_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "typed_custom_fields": {},
        "organization_id": "5e66b6XXXXXXXXXXXXXXXXXX",
        "account_stage_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "source": "salesforce",
        "original_source": "salesforce",
        "owner_id": "5c1004XXXXXXXXXXXXXXXXXX",
        "created_at": "2020-07-28T04:44:13.821Z",
        "phone_status": "no_status",
        "test_predictive_score": null,
        "hubspot_id": null,
        "salesforce_id": "0011UXXXXXXXXXX",
        "salesforce_owner_id": "0051UXXXXXXXXXX",
        "parent_account_id": null,
        "account_playbook_statuses": [],
        "existence_level": "full",
        "label_ids": [],
        "modality": "account",
        "salesforce_record_url": "https://na85.salesforce.com/0011UXXXXXXXXXXX"
      },
      "organization": {
        "id": "5e66b6XXXXXXXXXXXXXXXXXX",
        "name": "Apollo",
        "website_url": "http://www.apollo.io",
        "blog_url": null,
        "angellist_url": null,
        "linkedin_url": "http://www.linkedin.com/company/apolloio",
        "twitter_url": "https://twitter.com/MeetApollo/",
        "facebook_url": "https://www.facebook.com/MeetApollo/",
        "languages": [],
        "alexa_ranking": 77520,
        "phone": null,
        "linkedin_uid": "18511550",
        "publicly_traded_symbol": null,
        "publicly_traded_exchange": null,
        "logo_url": "https://apollo-server.com/uploads/pictures/5f0265XXXXXXXXXXXXXXXXXX/picture",
        "crunchbase_url": null,
        "primary_domain": "apollo.io",
        "starred_by_user_ids": [],
        "persona_counts": {}
      },
      "phone_numbers": [],
      "account_phone_note": null,
      "message_job_change_event": null
    }
  ],
  "breadcrumbs": [
    {
      "label": "Contains Keywords",
      "signal_field_name": "q_keywords",
      "value": "Tim Zheng, CEO, Apollo",
      "display_name": "Tim Zheng, CEO, Apollo"
    }
  ],
  "partial_results_only": false,
  "disable_eu_prospecting": false,
  "partial_results_limit": 10000,
  "pagination": {
    "page": 1,
    "per_page": 25,
    "total_entries": 1,
    "total_pages": 1
  },
  "num_fetch_result": null
}
```

This endpoint retrieves all messages.

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/messages`

### Query Parameters

| Parameter      | Description                                                                                                                                                   |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| contact_id     | Contact ID                                                                                                                                                    |
| user_id        | User ID                                                                                                                                                       |
| sort_by_field  | Possible values: "message_last_activity_date", "message_email_last_opened_at", "message_email_last_clicked_at", "message_created_at", or "message_updated_at" |
| sort_ascending | Possible values: true or false                                                                                                                                |
| page           | which page to return. Defaults to 1                                                                                                                           |
| per_page       | how many messages to return per page. Max = 200                                                                                                               |

## Get a Specific message

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.get(2)
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.messages.get(2)
```

```shell
curl "https://api.growthgenius.com/integrations/v1/messages/2" \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let max = api.messages.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific message.

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/messages/<ID>`

### URL Parameters

| Parameter | Description                       |
| --------- | --------------------------------- |
| ID        | The ID of the message to retrieve |

## Delete a Specific message

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.messages.delete(2)
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.messages.delete(2)
```

```shell
curl "https://api.growthgenius.com/integrations/v1/messages/2" \
  -X DELETE \
  -H "Authorization: YOUR API KEY HERE"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let max = api.messages.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted": ":("
}
```

This endpoint deletes a specific message.

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/messages/<ID>`

### URL Parameters

| Parameter | Description                     |
| --------- | ------------------------------- |
| ID        | The ID of the message to delete |
