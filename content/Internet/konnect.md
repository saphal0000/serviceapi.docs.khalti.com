# Konnect (KCMS)

**Note:** Below is the list of ISPs under KCMS and their service slugs:

##### **Izone:** `izone`

##### **World Fiber Net:** `world-fiber-net`

##### **DG Link:** `dg-link`

##### **Loop Network:** `loop-network`

##### **Acme Internet:** `acme-internet`

**Type:** Multi-Step API

### Test Username:

There are 3 different types of users. New users cannot make online payments:

- **New**
- **Active**
- **Expired**

### 1. Detail Fetch API

**Request URL:**  `{{base_url}}/api/servicegroup/details/konnect/`

**Request Method:**  
`POST`

**Service Slug:** `service_slug`

**Service Parameters:**

<pre><code class="json">
{
    "token": "token",
    "username": "username",
    "reference": "unique_reference",
    "service_slug": "service_slug"  // e.g., izone, world-fiber-net, etc.
}
</code></pre>

**Responses:**

- **Response for username: new**

<pre><code class="json">
{
    "status": false,
    "error_code": "4000",
    "message": "Can't fulfill request",
    "error": "client_error",
    "details": "This customer's first subscription payment cannot be paid online. Please contact the nearest office.",
    "error_data": {},
    "state": "Error"
}
</code></pre>

- **Response for username: active**

<pre><code class="json">
{
    "customer": {
        "username": "9779869045195",
        "name": "Chandra Mani Neupane",
        "mobile": "9869045195",
        "status": "Active"
    },
    "current_subscription": {
        "package": "Fiber Internet (First Installation 20Mbps Home)",
        "end_date": "2021-04-30",
        "status": "Active"
    },
    "due": {
        "amount": "0.00000",
        "message": "Due Amount is NIL"
    },
    "packages": [
        {
            "package_id": "1-13286-5-3",
            "package_name": "Fiber Internet (First Installation) - 3 Month(s)",
            "amount": 5999,
            "current": true
        },
        {
            "package_id": "1-13286-5-12",
            "package_name": "Fiber Internet (First Installation) - 12 Month(s)",
            "amount": 15500,
            "current": false
        }
    ],
    "session_id": 179,
    "status": true
}
</code></pre>

- **Response for username: expired**

<pre><code class="json">
{
    "customer": {
        "username": "9779803074977",
        "name": "koshish bortaula",
        "mobile": "",
        "status": "Expired"
    },
    "current_subscription": {
        "package": "NET+TV - 30Mbps",
        "end_date": "2021-01-31",
        "status": "Expired"
    },
    "due": {
        "amount": "0",
        "message": "Due Amount is NIL"
    },
    "packages": [
        {
            "package_id": "1-4412-8-1",
            "package_name": "NET+TV - 30Mbps - 1 Month(s)",
            "amount": 1850,
            "current": false
        },
        {
            "package_id": "1-4412-8-3",
            "package_name": "NET+TV - 30Mbps - 3 Month(s)",
            "amount": 5550,
            "current": false
        },
        {
            "package_id": "1-4412-8-6",
            "package_name": "NET+TV - 30Mbps - 6 Month(s)",
            "amount": 9250,
            "current": false
        },
        {
            "package_id": "1-4412-8-12",
            "package_name": "NET+TV - 30Mbps - 12 Month(s)",
            "amount": 18500,
            "current": true
        }
    ],
    "session_id": 180,
    "status": true
}
</code></pre>

---

### 2. Payment API

**Request URL:**  
`{{base_url}}/api/servicegroup/commit/konnect/`

**Request Method:**  
`POST`

**Service Parameters:**

<pre><code class="json">
{
    "token": "token",
    "reference": "unique reference",
    "package_id": "package id of selected package",
    "amount": "amount of selected package",
    "session_id": "obtained from previous API"
}
</code></pre>

**Response:**

<pre><code class="json">
{
    "status": true,
    "state": "Success",
    "message": "Successfully Completed Transaction",
    "extra_data": {},
    "detail": "Payment made successfully. Account will be activated in few minutes",
    "credits_consumed": 5999.0,
    "credits_available": 9998.37,
    "id": 74020
}
</code></pre>
