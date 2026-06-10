# Max TV API Documentation

## Overview

This document describes the API for fetching details and processing payments for Max TV (Worldcup) services. It includes request and response formats for the Detail Fetch and Payment APIs.

## Detail Fetch API

- **Request URL:** `{{base_url}}/api/servicegroup/details/worldcup-maxtv/`  
- **Request Method:** POST

### Service Params

<pre><code class="json">
{
    "subscriber_code": "7760337001845297",
    "token": "{{token}}",
    "reference": "{{$guid}}"
}
</code></pre>

### Response

<pre><code class="json">
{
    "packages": [
        {
            "package_id": 1,
            "package_name": "FIFA 2026 RESIDE",
            "duration": "50 Days",
            "package_price": 999,
            "discount": 0,
            "amount": 999
        }
    ],
    "session_id": 53226,
    "status": true
}
</code></pre>

## Payment API

- **Request URL:** `{{base_url}}/api/servicegroup/commit/worldcup-maxtv/`  
- **Request Method:** POST

### Service Params

<pre><code class="json">
{
    "token": "{{token}}",
    "amount": "999",
    "session_id": "53226",
    "package_id": "1"
}
</code></pre>

### Response

<pre><code class="json">
{
    "id": 235668,
    "status": true,
    "state": "Success",
    "detail": "Transaction Success",
    "message": "Your operation is in success.",
    "credits_consumed": 999.0,
    "credits_available": xxxx,
    "extra_data": {}
}
</code></pre>

### Notes

- Replace `{{base_url}}`, `{{token}}`, and `{{$guid}}` with appropriate values when calling the API.