# NTC E-SIM

This document describes the NTC e-SIM purchase API. Use this endpoint to sell NTC e-SIMs to end customers

---

### 1. Purchase (NTC e-SIM)

This endpoint processes e-SIM purchase requests and returns activation information on success.

**POST**  
`{{base_url}}/api/use/ntc-e-sim/`

#### Request Body (JSON)

<pre><code class="json">
{
    "token": "<your token>",
    "reference": "unique-reference-123",
    "amount": 90,
    "name": "Test Bahadur Kansakar",
    "dob": "2000-01-01",
    "address": "Panipokhari",
    "email": "ram.bahadur@gmail.com",
    "father": "Hari Bahadur Shrestha",
    "grandfather": "Man Bahadur Shrestha",
    "mother": "Sita Devi Shrestha",
    "document_number": "12345678",
    "issue": "2088-05-15",
    "pp_photo1": "+fpfHqY9vUSABjI8vr+...",
    "pp_photo2": "+fpfHqY9vUSABjI8vr+...",
    "pp_photo3": "+fpfHqY9vUSABjI8vr+...",
    "t_n_c": true
}
</code></pre>

**Field notes**

- **amount:** Fixed at `90` (NPR) for the NTC e-SIM product. Do not change.
- **reference:** Unique string per request; duplicate references will be rejected.
- **issue:** Issue date in ISO Gregorian format `YYYY-MM-DD`.
- **pp_photo1/2/3:** Base64-encoded image strings (JPEG/PNG). Maximum 2 MB per image.
- **t_n_c:** Boolean; must be `true` to indicate customer accepted terms and conditions.

---

#### Success Response

<pre><code class="json">
{
    "status": true,
    "state": "Success",
    "message": "e-SIM purchase successful",
    "activation_code": "ABC123DEF",
    "id": 12345,
    "credits_consumed": 90.0,
    "credits_available": 999999.0
}
</code></pre>

---

#### Error Responses

Validation error (invalid parameters):

<pre><code class="json">
{
    "status": false,
    "error_code": "1010",
    "message": "Validation error",
    "error": "invalid_parameters",
    "details": {
        "amount": "enter valid amount"
    },
    "state": "Error"
}
</code></pre>

Duplicate reference id:

<pre><code class="json">
{
    "status": false,
    "error_code": "1013",
    "message": "Request with duplicate reference id obtained",
    "error": "duplicate_request",
    "state": "Error"
}
</code></pre>

**Note:** Upon successful registration we will send a confirmation email to the user containing the SIM details.

