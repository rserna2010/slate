---
title: Finix API Reference

language_tabs:
  - shell: cURL
  - php: PHP
  - ruby: Ruby
  - python: Python

includes:
  - errors

search: true
---

# Introduction

A payments API for platforms and marketplaces.

We have language bindings in cURL and PHP! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

```shell
# With cURL, just supply your username as basic auth (-u) in the header of each request as follows:
curl "api_endpoint_here"
  -u USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```

```php

```

To communicate with the Finix API, you'll need to authenticate your requests with a username and password. For the sandbox environment please use the following credentials:

- Username: `USwyuGJdVcsRTzDeX9smLVGQ`

- Password: `968cb207-1abb-4100-9425-9a723e99eb10`

> To authorize, use this code:




<aside class="notice">
You must replace <code>USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb1</code> with your personal API key.
</aside>

# Identities
An Identity resource represents a business or person. Payment Instrument resources may be associated to an Identity.

## Create a New Identity

```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`POST http://b.papi.staging.finix.io/identities`

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
first_name | *string*, **optional** | First name of the customer or representative of the business | Dwayne
last_name | *string*, **optional** | Last name of the customer or representative of the business | Johnson
tax_id | *string*, **optional** | Last four digits of the Social Security integer of the customer or representative of the business | 5779
day | *integer*, **optional** | Day field of date of birth | 1
month | *integer*, **optional** | Month field of date of birth | 2
year | *string*, **optional** | Year field of date of birth | 1988
phone | *string*, **optional** | Phone integer of the person. Note: There's a separate field for the business phone integer | 1408756449
email | *string*, **optional** | Email address of the customer or representative of the business. | someone@example
business_name | *string*, **optional** | Full legal business name if the Identity is a business | Business, Inc
doing_business_as | *string*, **optional** | Name business is using with customers if different from its legal name | Bob's Burgers
business_type | *string*, **optional** | The type of business | LIMITED_LIABILITY_COMPANY
business_tax_id | *string*, **optional** | Employee Identification integer of the business if the customer is a business | 123456789
business_phone | *string*, **optional** | Phone integer of the business | 0123456789
mcc | *integer*, **optional** | MCC code for the business | 1520
settlement_bank_account | *string*, **optional** | (ID of the default Payment Instrument used to settle funds | PIvmSjVFkMaMbUnkjM9yJq6D
settlement_currency | *string*, **optional** | Default currency used when settling funds to this Identity | USD
max_transaction_amount | *integer*, **optional** | Maximum transaction allowed for the Identity in cents | 100

## Retrieve an Identity


```shell

```

```php
require 'kittn'

```

> Example Response:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a previously created Identity.


### HTTP Request

`GET http://b.papi.staging.finix.io/identities/identity_id`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
identity_id | ID of the Identity


## Underwrite an Identity


```shell

```

```php
require 'kittn'

```

> Example Response:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

Underwrite a previously created Identity resource so that they can act as a seller and have funds disbursed to their bank account.


### HTTP Request

`POST http://b.papi.staging.finix.io/identities/identity_id/merchants`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
identity_id | ID of the Identity

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
processor | *string*, **required** | Processor used for underwriting the Identity, please use "DUMMY_V1" for now to test the API. | DUMMY_V1


# Identity Verifications
Identities (merchants) to whom you wish to pay out must be underwritten as per KYC regulations. Each attempt at verifying an Identity creates a Verification resource.

## Create an Identity Verification


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

Perform an identity verification check against a previously created Identity.

### HTTP Request

`POST http://b.papi.staging.finix.io/identities/identity_id/verifications`


### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
identity_id | ID of the Identity


### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
processor | *string*, **required** | Service used for verifying the Identity, please use "DUMMY_V1" for now to test the API. | DUMMY_V1


## Retrieve a Verification


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

Perform an identity verification check against a previously created Identity.

### HTTP Request

`GET  http://b.papi.staging.finix.io/verifications/verification_id`


### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
verification_id | ID of the Verification resource


# Merchants
An Identity resource represents a business or person. Payment Instrument resources may be associated to an Identity.

## Create a New Merchant

```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

To create a Merchant you must underwrite a previously created Identity resource.

### HTTP Request

`POST http://b.papi.staging.finix.io/identities/identity_id/merchants`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
identity_id | ID of the Identity

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
processor | *string*, **required** | Processor used for underwriting the Identity, please use "DUMMY_V1" for now to test the API. | DUMMY_V1



## Retrieve a Merchant


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`GET http://b.papi.staging.finix.io/merchants/merchant_id`


### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
merchant_id | ID of the Merchant



# Payment Instruments
A Payment Instrument resource represents either a credit card or bank account. All information is securely vaulted and referenced by an ID. A Payment Instrument may be created multiple times, and each tokenization produces a unique ID. Each ID may only be associated one time and to only one Identity. Once associated, a Payment Instrument may not be disassociated from an Identity.

## Create a New Card

```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`POST http://b.papi.staging.finix.io/payment_instruments`

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
identity | *string*, **required** | Identity resource which the card is associated. | IDf1vj1U5SA7sbGiuP9vwfn8
first_name | *string*, **optional** | Customer's first name on card. | Dwayne
last_name | *string*, **optional** | Customer's last name on card. | Johnson
full_name | *string*, **optional** | Customer's full name on card. | Dwayne Johnson
type | *string*, **required** | Type of Payment Instrument. For cards input PAYMENT_CARD. | PAYMENT_CARD
number | *string*, **required** | The digits of the credit card integer. | 1111 111 1111 1111
security_code | *string*, **optional** | The 3-4 digit security code for the card. | 123
expiration_month | *integer*, **required** | Expiration month (e.g. 12 for December). | 11
expiration_year | *integer*, **required** | Expiration year. | 2020
available_account_type | *string*, **optional** | TBD. | foo
line1 | *string*, **optional** | Street address of the associated card. | 1423 S Joane Way
line2 | *string*, **optional** | Second line of the address of the associated card. |  Apt. 3
city | *string*, **optional** | City of the associated card. | San Mateo
region | *string*, **optional** | State of the associated card. | CA
postal_code | *string*, **optional** | Postal of the associated card. | 92704
country | *string*, **optional** | Country of the associated card. | USA

## Create a New Bank Account


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`POST http://b.papi.staging.finix.io/payment_instruments`

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
full_name | *string*, **optional** | Customer's full name on card. | Dwayne Johnson
identity | *string*, **required**| Identity resource which the card is associated. | IDe1AVug8nRAjGux1wY5JJLa
account_type | *string*, **required** | Checking or Savings | SAVINGS
iban | *string*, **optional** | International Bank Account integer | foo
type | *string*, **required** | Type of Payment Instrument. For cards input PAYMENT_CARD. | BANK_ACCOUNT
first_name | *string*, **optional** | Customer's first name on bank account. | Dwayne
last_name | *string*, **optional** | Customer's last name on card. | Johnson
account_number | *string*, **required** | Masked account integer. | 84012312415
country | *string*, **optional** | Country of the associated bank account. | USA
bank_code | *string*, **required** | Routing integer format. Specified in FedACH database defined by the US Federal Reserve. | 840123124
bic | *string*, **optional** | TBD. | foo
company_name | *string*, **optional** | Name of company if the bank account is a company account. |  Bob's Burgers
currency | *string*, **optional** | Default currency used when settling funds. | USD
available_account_type | *string*, **optional** | TBD. | foo


# Transfers
A Transfer resource represents any omnidirectional flow of funds. Transfers can represent either a debit to a card, a credit to a bank account, or a refund to a card depending on the request. Transfers have a state attribute representing the current state of the transaction. There are three possible status values: PENDING, COMPLETED, or FAILED.

## Debit a Card

```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

A Transfer consisting of obtaining (charging) money from a card (i.e. debit).

### HTTP Request

`POST http://b.papi.staging.finix.io/transfers`

### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
source | *string*, **required** | The Payment Instrument to debited. | PIvmSjVFkMaMbUnkjM9yJq6D
identity | *string*, **required** | UID. | IDf1vj1U5SA7sbGiuP9vwfn8
amount | *integer*, **required** | The amount of the debit in cents. | 100

## Credit a Bank Account


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

A Transfer consisting of sending money to a bank account (i.e. credit).

### HTTP Request

`POST http://b.papi.staging.finix.io/transfers`

### Request Arguments


Field | Type | Description | Example
----- | ---- | ----------- | -------
destination | *string*, **required** | The Payment Instrument to credited. | PIdX4dGe57HXjpzfgK2oN6cN
identity | *string*, **required** | UID. | IDf1vj1U5SA7sbGiuP9vwfn8
amount | *integer*, **required** | The amount of the credit in cents. | 100


## Refund a Debit


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

A Transfer representing a refund of a debit transaction. The amount of the refund may be any value up to the amount of the original debit.

### HTTP Request

`POST http://b.papi.staging.finix.io/transfers/transfer_id/reversals`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
transfer_id | ID of the original Transfer


### Request Arguments

Field | Type | Description | Example
----- | ---- | ----------- | -------
refund_amount | *integer*, **required** | The amount of the refund in cents. Must be equal to or less than the amount of the original debit. | 100


# Disputes
Disputes, also known as chargebacks, represent any customer-disputed charge.

## Retrieve a Dispute

```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

### HTTP Request

`GET http://b.papi.staging.finix.io/disputes/dispute_id`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
dispute_id | ID of the Dispute


## Upload Evidence For a Dispute


```shell

```

```php

```

> Example Response:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

A Transfer consisting of sending money to a bank account (i.e. credit).

### HTTP Request

`POST http://b.papi.staging.finix.io/disputes/dispute_id/files`


### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
dispute_id | ID of the Dispute


### Request Arguments


Field | Type | Description | Example
----- | ---- | ----------- | -------
destination | *string*, **required** | The Payment Instrument to credited. | PIdX4dGe57HXjpzfgK2oN6cN
identity | *string*, **required** | UID. | IDf1vj1U5SA7sbGiuP9vwfn8
amount | *integer*, **required** | The amount of the credit in cents. | 100

