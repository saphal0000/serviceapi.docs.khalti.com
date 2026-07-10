# Genius 


**Note:** Below is the list of ISPs under Genius and their service slugs:

##### **Chitrawan Unique Net:** `chitrawan-unique-net`

##### **Wifi Nepal:** `wifi-nepal-v5`

**Type:** Multi-Step API

------------------------------------------------------------------------

## 1. Detail Fetch API

**Request URL:** `{{base_url}}/api/servicegroup/details/genius/`

**Request Method:**
`POST`


### Request Parameters

<pre><code class="json">
{
    "token": "token",
    "reference": "unique_reference",
    "request_id": "request_id",
    "service_slug": "service_slug"  // e.g. wifi-nepal-v5
}
</code></pre>

### Sample Response

<pre><code class="json">
{
    "amount": 0,
    "customer_name": "Khalti Test",
    "phone": "9800000000",
    "address": "Basnetgaun, Lalitpur-04, Lalitpur",
    "packages": [
        {
            "amount": 1500,
            "package_id": 202,
            "name": "100 mbps 1 month"
        }
    ],
    "session_id": 26015,
    "status": true
}
</code></pre>


## 2. Payment API

**Request URL:**
`{{base_url}}/api/servicegroup/commit/genius/`

**Request Method:**
`POST`

### Request Parameters

<pre><code class="json">
{
    "reference": "unique_reference",
    "token": "token",
    "session_id": "session_id_from_detail_api",
    "package_id": "selected_package_id",
    "amount": "selected_package_amount"
}
</code></pre>

### Sample Response

<pre><code class="json">
{
    "status": true,
    "state": "Success",
    "message": "Successfully Completed Transaction",
    "extra_data": {},
    "detail": "SUCCESS",
    "credits_consumed": 1500,
    "credits_available": 99994,
    "id": 126362
}
</code></pre>

