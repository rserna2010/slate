---
title: Finix API Reference

language_tabs:
  - shell: cURL
  - php: PHP
  - ruby: Ruby
  - python: Python
  - csharp: C#
  - java: Java
  - perl: Perl

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
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"tags\": {
    \"key\": \"value\"
  },
  \"entity\": {
    \"last_name\": \"saget\",
    \"phone\": \"1234567890\",
    \"personal_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 7\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"business_name\": \"business inc\",
    \"business_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 8\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"tax_id\": \"5779\",
    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",
    \"business_phone\": \"+1 (408) 756-4497\",
    \"first_name\": \"dwayne\",
    \"dob\": {
      \"year\": 1978,
      \"day\": 27,
      \"month\": 5
    },
    \"business_tax_id\": \"123456789\",
    \"doing_business_as\": \"doingBusinessAs\",
    \"email\": \"user@example.org\"
  }
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "tags": {
    "key": "value"
  },
  "entity": {
    "last_name": "saget",
    "phone": "1234567890",
    "personal_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 7",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "business_name": "business inc",
    "business_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 8",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "tax_id": "5779",
    "business_type": "LIMITED_LIABILITY_COMPANY",
    "business_phone": "+1 (408) 756-4497",
    "first_name": "dwayne",
    "dob": {
      "year": 1978,
      "day": 27,
      "month": 5
    },
    "business_tax_id": "123456789",
    "doing_business_as": "doingBusinessAs",
    "email": "user@example.org"
  }
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/identities', values, headers
puts response

```

```python
from urllib2 import Request, urlopen

values = """
  {
    "tags": {
      "key": "value"
    },
    "entity": {
      "last_name": "saget",
      "phone": "1234567890",
      "personal_address": {
        "city": "San Mateo",
        "country": "USA",
        "region": "CA",
        "line2": "Apartment 7",
        "line1": "741 Douglass St",
        "postal_code": "94114"
      },
      "business_name": "business inc",
      "business_address": {
        "city": "San Mateo",
        "country": "USA",
        "region": "CA",
        "line2": "Apartment 8",
        "line1": "741 Douglass St",
        "postal_code": "94114"
      },
      "tax_id": "5779",
      "business_type": "LIMITED_LIABILITY_COMPANY",
      "business_phone": "+1 (408) 756-4497",
      "first_name": "dwayne",
      "dob": {
        "year": 1978,
        "day": 27,
        "month": 5
      },
      "business_tax_id": "123456789",
      "doing_business_as": "doingBusinessAs",
      "email": "user@example.org"
    }
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }}");
Response response = client.target("http://b.papi.staging.finix.io/identities")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));

```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/identities", Content => $data);

print $response->as_string;

```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"tags\": {    \"key\": \"value\"  },  \"entity\": {    \"last_name\": \"saget\",    \"phone\": \"1234567890\",    \"personal_address\": {      \"city\": \"San Mateo\",      \"country\": \"USA\",      \"region\": \"CA\",      \"line2\": \"Apartment 7\",      \"line1\": \"741 Douglass St\",      \"postal_code\": \"94114\"    },    \"business_name\": \"business inc\",    \"business_address\": {      \"city\": \"San Mateo\",      \"country\": \"USA\",      \"region\": \"CA\",      \"line2\": \"Apartment 8\",      \"line1\": \"741 Douglass St\",      \"postal_code\": \"94114\"    },    \"tax_id\": \"5779\",    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",    \"business_phone\": \"+1 (408) 756-4497\",    \"first_name\": \"dwayne\",    \"dob\": {      \"year\": 1978,      \"day\": 27,      \"month\": 5    },    \"business_tax_id\": \"123456789\",    \"doing_business_as\": \"doingBusinessAs\",    \"email\": \"user@example.org\"  }}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("identities", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }

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
curl http://b.papi.staging.finix.io/identities \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
\"tags\": {
\"key\": \"value\"
},
\"entity\": {
\"last_name\": \"saget\",
\"phone\": \"1234567890\",
\"personal_address\": {
\"city\": \"San Mateo\",
\"country\": \"USA\",
\"region\": \"CA\",
\"line2\": \"Apartment 7\",
\"line1\": \"741 Douglass St\",
\"postal_code\": \"94114\"
},
\"business_name\": \"business inc\",
\"business_address\": {
\"city\": \"San Mateo\",
\"country\": \"USA\",
\"region\": \"CA\",
\"line2\": \"Apartment 8\",
\"line1\": \"741 Douglass St\",
\"postal_code\": \"94114\"
},
\"tax_id\": \"5779\",
\"business_type\": \"LIMITED_LIABILITY_COMPANY\",
\"business_phone\": \"+1 (408) 756-4497\",
\"first_name\": \"dwayne\",
\"dob\": {
\"year\": 1978,
\"day\": 27,
\"month\": 6
},
\"business_tax_id\": \"123456789\",
\"doing_business_as\": \"doingBusinessAs\",
\"email\": \"user@example.org\"
}
}"
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"tags\": {
    \"key\": \"value\"
  },
  \"entity\": {
    \"last_name\": \"saget\",
    \"phone\": \"1234567890\",
    \"personal_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 7\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"business_name\": \"business inc\",
    \"business_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 8\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"tax_id\": \"5779\",
    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",
    \"business_phone\": \"+1 (408) 756-4497\",
    \"first_name\": \"dwayne\",
    \"dob\": {
      \"year\": 1978,
      \"day\": 27,
      \"month\": 5
    },
    \"business_tax_id\": \"123456789\",
    \"doing_business_as\": \"doingBusinessAs\",
    \"email\": \"user@example.org\"
  }
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "tags": {
    "key": "value"
  },
  "entity": {
    "last_name": "saget",
    "phone": "1234567890",
    "personal_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 7",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "business_name": "business inc",
    "business_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 8",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "tax_id": "5779",
    "business_type": "LIMITED_LIABILITY_COMPANY",
    "business_phone": "+1 (408) 756-4497",
    "first_name": "dwayne",
    "dob": {
      "year": 1978,
      "day": 27,
      "month": 5
    },
    "business_tax_id": "123456789",
    "doing_business_as": "doingBusinessAs",
    "email": "user@example.org"
  }
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/identities', values, headers
puts response

```

```python
from urllib2 import Request, urlopen

values = """
  {
    "tags": {
      "key": "value"
    },
    "entity": {
      "last_name": "saget",
      "phone": "1234567890",
      "personal_address": {
        "city": "San Mateo",
        "country": "USA",
        "region": "CA",
        "line2": "Apartment 7",
        "line1": "741 Douglass St",
        "postal_code": "94114"
      },
      "business_name": "business inc",
      "business_address": {
        "city": "San Mateo",
        "country": "USA",
        "region": "CA",
        "line2": "Apartment 8",
        "line1": "741 Douglass St",
        "postal_code": "94114"
      },
      "tax_id": "5779",
      "business_type": "LIMITED_LIABILITY_COMPANY",
      "business_phone": "+1 (408) 756-4497",
      "first_name": "dwayne",
      "dob": {
        "year": 1978,
        "day": 27,
        "month": 5
      },
      "business_tax_id": "123456789",
      "doing_business_as": "doingBusinessAs",
      "email": "user@example.org"
    }
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }}");
Response response = client.target("http://b.papi.staging.finix.io/identities")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));

```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/identities", Content => $data);

print $response->as_string;

```

```c#
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"tags\": {    \"key\": \"value\"  },  \"entity\": {    \"last_name\": \"saget\",    \"phone\": \"1234567890\",    \"personal_address\": {      \"city\": \"San Mateo\",      \"country\": \"USA\",      \"region\": \"CA\",      \"line2\": \"Apartment 7\",      \"line1\": \"741 Douglass St\",      \"postal_code\": \"94114\"    },    \"business_name\": \"business inc\",    \"business_address\": {      \"city\": \"San Mateo\",      \"country\": \"USA\",      \"region\": \"CA\",      \"line2\": \"Apartment 8\",      \"line1\": \"741 Douglass St\",      \"postal_code\": \"94114\"    },    \"tax_id\": \"5779\",    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",    \"business_phone\": \"+1 (408) 756-4497\",    \"first_name\": \"dwayne\",    \"dob\": {      \"year\": 1978,      \"day\": 27,      \"month\": 5    },    \"business_tax_id\": \"123456789\",    \"doing_business_as\": \"doingBusinessAs\",    \"email\": \"user@example.org\"  }}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("identities", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }

```


> Example Response:

```json

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
curl http://b.papi.staging.finix.io/identities/ID623YcUS26vPJk7ctf7HREg \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.get 'http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', headers
puts response
```

```python
from urllib2 import Request, urlopen

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', headers=headers)

response_body = urlopen(request).read()
print response_body
```


```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

  using(var response = await httpClient.GetAsync("identities/{identity_id}"))
  {

        string responseData = await response.Content.ReadAsStringAsync();
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target("http://b.papi.staging.finix.io/identities/{identity_id}")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .get();

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->get("http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3");

print $response->as_string;
```


> Example Response:

```json

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
curl http://b.papi.staging.finix.io/identities/ID623YcUS26vPJk7ctf7HREg/merchants \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
    -d "{
     \"processor\": \"DUMMY_V1\"
     }"
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"tags\": {
    \"key\": \"value\"
  },
  \"entity\": {
    \"last_name\": \"saget\",
    \"phone\": \"1234567890\",
    \"personal_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 7\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"business_name\": \"business inc\",
    \"business_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 8\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"tax_id\": \"5779\",
    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",
    \"business_phone\": \"+1 (408) 756-4497\",
    \"first_name\": \"dwayne\",
    \"dob\": {
      \"year\": 1978,
      \"day\": 27,
      \"month\": 5
    },
    \"business_tax_id\": \"123456789\",
    \"doing_business_as\": \"doingBusinessAs\",
    \"email\": \"user@example.org\"
  }
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "tags": {
    "key": "value"
  },
  "entity": {
    "last_name": "saget",
    "phone": "1234567890",
    "personal_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 7",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "business_name": "business inc",
    "business_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 8",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "tax_id": "5779",
    "business_type": "LIMITED_LIABILITY_COMPANY",
    "business_phone": "+1 (408) 756-4497",
    "first_name": "dwayne",
    "dob": {
      "year": 1978,
      "day": 27,
      "month": 5
    },
    "business_tax_id": "123456789",
    "doing_business_as": "doingBusinessAs",
    "email": "user@example.org"
  }
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.get 'http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

  using(var response = await httpClient.GetAsync("identities/{identity_id}"))
  {

        string responseData = await response.Content.ReadAsStringAsync();
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target("http://b.papi.staging.finix.io/identities/{identity_id}")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .get();

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->get("http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3", Content => $data);

print $response->as_string;

```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/identities/ID623YcUS26vPJk7ctf7HREg/verifications \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
         \"tags\": {
           \"name\": \"test-verification\"
         },
         \"processor\": \"DUMMY_V1\",
         \"identity\": null,
         \"instrument\": null,
         \"merchant\": null
       }"
```


```php

```

```ruby

```

```python

```

```csharp

```

```java

```


```perl

```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/verifications/VIsDyryWpjGPj53KJHs2YdPe \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3/verifications");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"tags\": {
    \"name\": \"test-verification\"
  },
  \"processor\": \"DUMMY_V1\",
  \"identity\": null,
  \"instrument\": null,
  \"merchant\": null
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "tags": {
    "name": "test-verification"
  },
  "processor": "DUMMY_V1",
  "identity": null,
  "instrument": null,
  "merchant": null
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3/verifications', values, headers
puts response

```

```python
from urllib2 import Request, urlopen

values = """
  {
    "tags": {
      "name": "test-verification"
    },
    "processor": "DUMMY_V1",
    "identity": null,
    "instrument": null,
    "merchant": null
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3/verifications', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"tags\": {    \"name\": \"test-verification\"  },  \"processor\": \"DUMMY_V1\",  \"identity\": null,  \"instrument\": null,  \"merchant\": null}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("identities/{identity_id}/verifications", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'tags': {    'name': 'test-verification'  },  'processor': 'DUMMY_V1',  'identity': null,  'instrument': null,  'merchant': null}");
Response response = client.target("http://b.papi.staging.finix.io/identities/{identity_id}/verifications")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'tags': {    'name': 'test-verification'  },  'processor': 'DUMMY_V1',  'identity': null,  'instrument': null,  'merchant': null};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3/verifications", Content => $data);

print $response->as_string;
```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/identities/ID623YcUS26vPJk7ctf7HREg/merchants \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
    \"processor\": \"DUMMY_V1\"
    }"
```

```shell
curl http://b.papi.staging.finix.io/identities/ID623YcUS26vPJk7ctf7HREg/merchants \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
    -d "{
     \"processor\": \"DUMMY_V1\"
     }"
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"tags\": {
    \"key\": \"value\"
  },
  \"entity\": {
    \"last_name\": \"saget\",
    \"phone\": \"1234567890\",
    \"personal_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 7\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"business_name\": \"business inc\",
    \"business_address\": {
      \"city\": \"San Mateo\",
      \"country\": \"USA\",
      \"region\": \"CA\",
      \"line2\": \"Apartment 8\",
      \"line1\": \"741 Douglass St\",
      \"postal_code\": \"94114\"
    },
    \"tax_id\": \"5779\",
    \"business_type\": \"LIMITED_LIABILITY_COMPANY\",
    \"business_phone\": \"+1 (408) 756-4497\",
    \"first_name\": \"dwayne\",
    \"dob\": {
      \"year\": 1978,
      \"day\": 27,
      \"month\": 5
    },
    \"business_tax_id\": \"123456789\",
    \"doing_business_as\": \"doingBusinessAs\",
    \"email\": \"user@example.org\"
  }
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "tags": {
    "key": "value"
  },
  "entity": {
    "last_name": "saget",
    "phone": "1234567890",
    "personal_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 7",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "business_name": "business inc",
    "business_address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 8",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "tax_id": "5779",
    "business_type": "LIMITED_LIABILITY_COMPANY",
    "business_phone": "+1 (408) 756-4497",
    "first_name": "dwayne",
    "dob": {
      "year": 1978,
      "day": 27,
      "month": 5
    },
    "business_tax_id": "123456789",
    "doing_business_as": "doingBusinessAs",
    "email": "user@example.org"
  }
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.get 'http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3', headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

  using(var response = await httpClient.GetAsync("identities/{identity_id}"))
  {

        string responseData = await response.Content.ReadAsStringAsync();
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target("http://b.papi.staging.finix.io/identities/{identity_id}")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .get();

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'tags': {    'key': 'value'  },  'entity': {    'last_name': 'saget',    'phone': '1234567890',    'personal_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 7',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'business_name': 'business inc',    'business_address': {      'city': 'San Mateo',      'country': 'USA',      'region': 'CA',      'line2': 'Apartment 8',      'line1': '741 Douglass St',      'postal_code': '94114'    },    'tax_id': '5779',    'business_type': 'LIMITED_LIABILITY_COMPANY',    'business_phone': '+1 (408) 756-4497',    'first_name': 'dwayne',    'dob': {      'year': 1978,      'day': 27,      'month': 5    },    'business_tax_id': '123456789',    'doing_business_as': 'doingBusinessAs',    'email': 'user@example.org'  }};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->get("http://b.papi.staging.finix.io/identities/IDp98nxwJw9DzhXVPY9GsHs3", Content => $data);

print $response->as_string;

```




> Example Response:

```json

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
curl http://b.papi.staging.finix.io/merchants/MUtVCCtLfTYULwkW64dpYah7 \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/merchants/MUjE7E28Km3oNAcA4mWe67Td");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.get 'http://b.papi.staging.finix.io/merchants/MUjE7E28Km3oNAcA4mWe67Td', headers
puts response

```

```python

Try
from urllib2 import Request, urlopen

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/merchants/MUjE7E28Km3oNAcA4mWe67Td', headers=headers)

response_body = urlopen(request).read()
print response_body

```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

  using(var response = await httpClient.GetAsync("merchants/{merchant_id}"))
  {

        string responseData = await response.Content.ReadAsStringAsync();
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target("http://b.papi.staging.finix.io/merchants/{merchant_id}")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .get();

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));

```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->get("http://b.papi.staging.finix.io/merchants/MUjE7E28Km3oNAcA4mWe67Td");

print $response->as_string;

```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/payment_instruments \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
       \"expiration_year\": 2020,
       \"number\": \"4242424242424242\",
       \"expiration_month\": 12,
       \"address\": {
       \"city\": \"San Mateo\",
       \"country\": \"USA\",
       \"region\": \"CA\",
       \"line2\": \"Apartment 7\",
       \"line1\": \"741 Douglass St\",
       \"postal_code\": \"94114\"
       },
       \"security_code\": \"112\",
       \"type\": \"PAYMENT_CARD\",
       \"identity\": \"IDwKZpv3SEkogtUPtzSksFvw\"
       }"
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/payment_instruments");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",
  \"expiration_year\": 2020,
  \"number\": \"4242424242424242\",
  \"expiration_month\": 12,
  \"address\": {
    \"city\": \"San Mateo\",
    \"country\": \"USA\",
    \"region\": \"CA\",
    \"line2\": \"Apartment 7\",
    \"line1\": \"741 Douglass St\",
    \"postal_code\": \"94114\"
  },
  \"security_code\": \"112\",
  \"type\": \"PAYMENT_CARD\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "identity": "IDe1AVug8nRAjGux1wY5JJLa",
  "expiration_year": 2020,
  "number": "4242424242424242",
  "expiration_month": 12,
  "address": {
    "city": "San Mateo",
    "country": "USA",
    "region": "CA",
    "line2": "Apartment 7",
    "line1": "741 Douglass St",
    "postal_code": "94114"
  },
  "security_code": "112",
  "type": "PAYMENT_CARD"
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/payment_instruments', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

values = """
  {
    "identity": "IDe1AVug8nRAjGux1wY5JJLa",
    "expiration_year": 2020,
    "number": "4242424242424242",
    "expiration_month": 12,
    "address": {
      "city": "San Mateo",
      "country": "USA",
      "region": "CA",
      "line2": "Apartment 7",
      "line1": "741 Douglass St",
      "postal_code": "94114"
    },
    "security_code": "112",
    "type": "PAYMENT_CARD"
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/payment_instruments', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",  \"expiration_year\": 2020,  \"number\": \"4242424242424242\",  \"expiration_month\": 12,  \"address\": {    \"city\": \"San Mateo\",    \"country\": \"USA\",    \"region\": \"CA\",    \"line2\": \"Apartment 7\",    \"line1\": \"741 Douglass St\",    \"postal_code\": \"94114\"  },  \"security_code\": \"112\",  \"type\": \"PAYMENT_CARD\"}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("payment_instruments", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'expiration_year': 2020,  'number': '4242424242424242',  'expiration_month': 12,  'address': {    'city': 'San Mateo',    'country': 'USA',    'region': 'CA',    'line2': 'Apartment 7',    'line1': '741 Douglass St',    'postal_code': '94114'  },  'security_code': '112',  'type': 'PAYMENT_CARD'}");
Response response = client.target("http://b.papi.staging.finix.io/payment_instruments")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'expiration_year': 2020,  'number': '4242424242424242',  'expiration_month': 12,  'address': {    'city': 'San Mateo',    'country': 'USA',    'region': 'CA',    'line2': 'Apartment 7',    'line1': '741 Douglass St',    'postal_code': '94114'  },  'security_code': '112',  'type': 'PAYMENT_CARD'};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/payment_instruments", Content => $data);

print $response->as_string;
```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/payment_instruments \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
       \"account_type\": \"SAVINGS\",
       \"name\": \"Fran Lemke\",
       \"bank_code\": \"123123123\",
       \"country\": \"USA\",
       \"currency\": \"USD\",
       \"account_number\": \"123123123\",
       \"type\": \"BANK_ACCOUNT\",
       \"identity\": \"ID623YcUS26vPJk7ctf7HREg\"
       }"
```

```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/payment_instruments");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"currency\": \"USD\",
  \"account_type\": \"SAVINGS\",
  \"name\": \"Fran Lemke\",
  \"bank_code\": \"123123123\",
  \"country\": \"USA\",
  \"type\": \"BANK_ACCOUNT\",
  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",
  \"account_number\": \"123123123\"
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "currency": "USD",
  "account_type": "SAVINGS",
  "name": "Fran Lemke",
  "bank_code": "123123123",
  "country": "USA",
  "type": "BANK_ACCOUNT",
  "identity": "IDe1AVug8nRAjGux1wY5JJLa",
  "account_number": "123123123"
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/payment_instruments', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

values = """
  {
    "currency": "USD",
    "account_type": "SAVINGS",
    "name": "Fran Lemke",
    "bank_code": "123123123",
    "country": "USA",
    "type": "BANK_ACCOUNT",
    "identity": "IDe1AVug8nRAjGux1wY5JJLa",
    "account_number": "123123123"
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/payment_instruments', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```


```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"currency\": \"USD\",  \"account_type\": \"SAVINGS\",  \"name\": \"Fran Lemke\",  \"bank_code\": \"123123123\",  \"country\": \"USA\",  \"type\": \"BANK_ACCOUNT\",  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",  \"account_number\": \"123123123\"}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("payment_instruments", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'currency': 'USD',  'account_type': 'SAVINGS',  'name': 'Fran Lemke',  'bank_code': '123123123',  'country': 'USA',  'type': 'BANK_ACCOUNT',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'account_number': '123123123'}");
Response response = client.target("http://b.papi.staging.finix.io/payment_instruments")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'currency': 'USD',  'account_type': 'SAVINGS',  'name': 'Fran Lemke',  'bank_code': '123123123',  'country': 'USA',  'type': 'BANK_ACCOUNT',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'account_number': '123123123'};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/payment_instruments", Content => $data);

print $response->as_string;
```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/transfers \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d "{
       \"currency\": \"USD\",
       \"amount\": 100,
       \"processor\": \"DUMMY_V1\",
       \"identity\": \"ID623YcUS26vPJk7ctf7HREg\",
       \"source\": \"PId9VGeajrF45NTbsdX4vWY8\"
       }"
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/transfers");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"currency\": \"USD\",
  \"source\": \"PItgzimYnXFBVcBkn9gRS1yW\",
  \"processor\": \"DUMMY_V1\",
  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",
  \"amount\": 100
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

 values = '{
   "currency": "USD",
   "source": "PItgzimYnXFBVcBkn9gRS1yW",
   "processor": "DUMMY_V1",
   "identity": "IDe1AVug8nRAjGux1wY5JJLa",
   "amount": 100
 }'

 headers = {
   :content_type => 'application/vnd.json+api',
   :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
 }

 response = RestClient.post 'http://b.papi.staging.finix.io/transfers', values, headers
 puts response
```

```python
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "currency": "USD",
  "source": "PItgzimYnXFBVcBkn9gRS1yW",
  "processor": "DUMMY_V1",
  "identity": "IDe1AVug8nRAjGux1wY5JJLa",
  "amount": 100
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/transfers', values, headers
puts response
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"currency\": \"USD\",  \"source\": \"PItgzimYnXFBVcBkn9gRS1yW\",  \"processor\": \"DUMMY_V1\",  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",  \"amount\": 100}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("transfers", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'currency': 'USD',  'source': 'PItgzimYnXFBVcBkn9gRS1yW',  'processor': 'DUMMY_V1',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'amount': 100}");
Response response = client.target("http://b.papi.staging.finix.io/transfers")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'currency': 'USD',  'source': 'PItgzimYnXFBVcBkn9gRS1yW',  'processor': 'DUMMY_V1',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'amount': 100};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/transfers", Content => $data);

print $response->as_string;
```



> Example Response:

```json

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
curl http://b.papi.staging.finix.io/transfers \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d  "{
        \"currency\": \"USD\",
        \"amount\": 100,
        \"destination\": \"PI49C2Y8Z9wZ4ft1TLiN7yz\",
        \"processor\": \"DUMMY_V1\",
        \"identity\": \"ID623YcUS26vPJk7ctf7HREg\"
        }"
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/transfers");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"currency\": \"USD\",
  \"destination\": \"PIi98CoYWpQZi8w7ZimJxuJ\",
  \"processor\": \"DUMMY_V1\",
  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",
  \"amount\": 100
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "currency": "USD",
  "destination": "PIi98CoYWpQZi8w7ZimJxuJ",
  "processor": "DUMMY_V1",
  "identity": "IDe1AVug8nRAjGux1wY5JJLa",
  "amount": 100
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/transfers', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

values = """
  {
    "currency": "USD",
    "destination": "PIi98CoYWpQZi8w7ZimJxuJ",
    "processor": "DUMMY_V1",
    "identity": "IDe1AVug8nRAjGux1wY5JJLa",
    "amount": 100
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/transfers', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```

```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"currency\": \"USD\",  \"destination\": \"PIi98CoYWpQZi8w7ZimJxuJ\",  \"processor\": \"DUMMY_V1\",  \"identity\": \"IDe1AVug8nRAjGux1wY5JJLa\",  \"amount\": 100}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("transfers", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'currency': 'USD',  'destination': 'PIi98CoYWpQZi8w7ZimJxuJ',  'processor': 'DUMMY_V1',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'amount': 100}");
Response response = client.target("http://b.papi.staging.finix.io/transfers")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'currency': 'USD',  'destination': 'PIi98CoYWpQZi8w7ZimJxuJ',  'processor': 'DUMMY_V1',  'identity': 'IDe1AVug8nRAjGux1wY5JJLa',  'amount': 100};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/transfers", Content => $data);

print $response->as_string;

```


> Example Response:

```json

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
curl http://b.papi.staging.finix.io/transfers/TRmhPb7piECZgCucnrsXCVuL/reversals \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10 \
    -d  "{
       \"refund_amount\": 100,
       }"
```


```php
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/transfers/TRqYf7LLpck9yi5GaaLn6DFZ/reversals");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_POST, TRUE);

curl_setopt($ch, CURLOPT_POSTFIELDS, "{
  \"refund_amount\": 100
}");

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

values = '{
  "refund_amount": 100
}'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.post 'http://b.papi.staging.finix.io/transfers/TRqYf7LLpck9yi5GaaLn6DFZ/reversals', values, headers
puts response
```

```python
from urllib2 import Request, urlopen

values = """
  {
    "refund_amount": 100
  }
"""

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/transfers/TRqYf7LLpck9yi5GaaLn6DFZ/reversals', data=values, headers=headers)

response_body = urlopen(request).read()
print response_body
```


```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

    using (var content = new StringContent("{  \"refund_amount\": 100}", System.Text.Encoding.Default, "application/vnd.json+api"))
    {
      using (var response = await httpClient.PostAsync("transfers/{transfer_id}/reversals", content))
      {
        string responseData = await response.Content.ReadAsStringAsync();
      }
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Entity<String> payload = Entity.text("{  'refund_amount': 100}");
Response response = client.target("http://b.papi.staging.finix.io/transfers/{transfer_id}/reversals")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .post(payload);

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;
my $data = {  'refund_amount': 100};

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->post("http://b.papi.staging.finix.io/transfers/TRqYf7LLpck9yi5GaaLn6DFZ/reversals", Content => $data);

print $response->as_string;

```


> Example Response:

```json

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
curl http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2 \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```


```php

Try
<?php
$ch = curl_init();

curl_setopt($ch, CURLOPT_URL, "http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2");
curl_setopt($ch, CURLOPT_RETURNTRANSFER, TRUE);
curl_setopt($ch, CURLOPT_HEADER, FALSE);

curl_setopt($ch, CURLOPT_HTTPHEADER, array(
  "Content-Type: application/vnd.json+api",
  "Authorization: Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=="
));

$response = curl_exec($ch);
curl_close($ch);

var_dump($response);
```

```ruby
require 'rubygems' if RUBY_VERSION < '1.9'
require 'rest_client'

headers = {
  :content_type => 'application/vnd.json+api',
  :authorization => 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}

response = RestClient.get 'http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2', headers
puts response
```

```python
from urllib2 import Request, urlopen

headers = {
  'Content-Type': 'application/vnd.json+api',
  'Authorization': 'Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA=='
}
request = Request('http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2', headers=headers)

response_body = urlopen(request).read()
print response_body
```


```csharp
//Common testing requirement. If you are consuming an API in a sandbox/test region, uncomment this line of code ONLY for non production uses.
//System.Net.ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };

//Be sure to run "Install-Package Microsoft.Net.Http" from your nuget command line.
using System;
using System.Net.Http;

var baseAddress = new Uri("http://b.papi.staging.finix.io/");

using (var httpClient = new HttpClient{ BaseAddress = baseAddress })
{


  httpClient.DefaultRequestHeaders.TryAddWithoutValidation("authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

  using(var response = await httpClient.GetAsync("disputes/{dispute_id}"))
  {

        string responseData = await response.Content.ReadAsStringAsync();
  }
}
```

```java
// Maven : Add these dependecies to your pom.xml (java6+)
// <dependency>
//     <groupId>org.glassfish.jersey.core</groupId>
//     <artifactId>jersey-client</artifactId>
//     <version>2.8</version>
// </dependency>
// <dependency>
//     <groupId>org.glassfish.jersey.media</groupId>
//     <artifactId>jersey-media-json-jackson</artifactId>
//     <version>2.8</version>
// </dependency>

import javax.ws.rs.client.Client;
import javax.ws.rs.client.ClientBuilder;
import javax.ws.rs.client.Entity;
import javax.ws.rs.core.Response;
import javax.ws.rs.core.MediaType;

Client client = ClientBuilder.newClient();
Response response = client.target("http://b.papi.staging.finix.io/disputes/{dispute_id}")
  .request(MediaType.TEXT_PLAIN_TYPE)
  .header("Authorization", "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==")
  .get();

System.out.println("status: " + response.getStatus());
System.out.println("headers: " + response.getHeaders());
System.out.println("body:" + response.readEntity(String.class));
```


```perl
require LWP::UserAgent;

my $ua   = LWP::UserAgent->new;

$ua->default_header("Content-Type" => "application/vnd.json+api");
$ua->default_header("Authorization" => "Basic VVN3eXVHSmRWY3NSVHpEZVg5c21MVkdROjk2OGNiMjA3LTFhYmItNDEwMC05NDI1LTlhNzIzZTk5ZWIxMA==");

my $response = $ua->get("http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2");

print $response->as_string;

```


> Example Response:

```json

```

### HTTP Request

`GET http://b.papi.staging.finix.io/disputes/dispute_id`

### URL Parameters

Parameter | Description
--------- | -------------------------------------------------------------------
dispute_id | ID of the Dispute


## Upload Evidence For a Dispute


```shell
curl http://b.papi.staging.finix.io/disputes/DIgLjwDsdmAi82fQgZpxHmB2/files \
    -H "Content-Type: application/vnd.json+api" \
    -u  USwyuGJdVcsRTzDeX9smLVGQ:968cb207-1abb-4100-9425-9a723e99eb10
```

```php

```

```ruby

```

```python

```

```csharp

```

```java

```


```perl

```



> Example Response:

```json

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

