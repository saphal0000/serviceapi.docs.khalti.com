# NETTV Worldcup API Documentation

## Overview

This document describes the multi-step API for fetching details and processing payments related to NETTV (Worldcup) services. It includes request and response formats for Detail Fetch, Package Details, and Payment APIs.

## Detail Fetch API

**Request URL:** `{{url}}/api/servicegroup/details/worldcup/`  
**Request Method:** POST

### Service Params

<pre><code class="json">
{
    "token": "{{token}}",
    "username": "kpoli",
    "reference": "{{$guid}}"
}
</code></pre>

### Response

<pre><code class="json">
{
    "status": true,
    "stb_list": [
        {
            "serial": "00226DBB5B42"
        }
    ],
    "username": "kpoli",
    "session_id": 45399
}
</code></pre>

## Package Details API

**Request URL:** `{{url}}/api/servicegroup/getpackagerates/worldcup/`  
**Request Method:** POST

### Service Params

<pre><code class="json">
{
    "token": "{{token}}",
    "serial_no": "{{stb_serials}}",
    "session_id": "{{session_id}}"
}
</code></pre>

### Response

<pre><code class="json">
{
    "status": true,
    "username": "kpoli",
    "stb": "00226DBB5B42",
    "package_status": "active",
    "expiry_date": "2026-07-08",
    "package_name": "NETTV Elite Package -1 Month",
    "stb_type": "primary",
    "user_id": 0,
    "package_list": [
        {
            "name": "NETTV FIFA 2026 Pass",
            "duration": "2 months",
            "package_price": 884.07,
            "discount": 0.0,
            "amount": 998.0,
            "package_sales_id": 1131,
            "package_id": 1131
        }
    ],
    "session_id": 45414
}
</code></pre>

## Payment API

**Request URL:** `{{url}}/api/servicegroup/commit/worldcup/`  
**Request Method:** POST

### Service Params

<pre><code class="json">
{
    "token": "{{token}}",
    "amount": "998",
    "session_id": "{{session_id}}",
    "package_sales_id": "1131"
}
</code></pre>

### Response

<pre><code class="json">
{
    "status": true,
    "state": "Success",
    "message": "Successfully Completed Transaction",
    "extra_data": {},
    "detail": "Transaction Successful",
    "credits_consumed": 998.0,
    "credits_available": 99986576520.0098,
    "id": 177654
}
</code></pre>