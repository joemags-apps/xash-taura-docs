# Verifying OTT Voucher

Verify the status of an OTT voucher to ensure it is valid and unredeemed. This endpoint checks the voucher's validity in the system and returns its status.

## Endpoint for Voucher Verification

` POST https://<BASE_URL>/api/v0.1/ott-redeem/verify `

This endpoint accepts a voucher PIN and returns its current status.

### Request

- **Headers**:
  - `Accept: application/json`

- **Body Parameters**:
  - `pin`: The 12-digit voucher PIN (required, must be numeric).

### Request Example

Use the following command to verify a voucher:

```bash
curl -X POST 'https://<BASE_URL>/api/v0.1/ott-redeem/verify' \
--header 'Accept: application/json' \
--form 'pin="YOUR_VOUCHER_PIN"'
```

*Replace `YOUR_VOUCHER_PIN` with the actual PIN.*

### Responses

#### Success: Voucher Already Used

```json
{
  "message": "Voucher already used",
  "used_by": "identifier_of_user",
  "receiver": "recipient_phone_number",
  "value": "amount_of_voucher",
  "date": "date_of_use",
  "status": 200
}
```

#### Success: Voucher Valid

```json
{
  "success": true,
  "message": "Voucher valid and not redeemed",
  "serial": "serial_number_of_voucher",
  "voucherID": "unique_voucher_identifier",
  "value": "value_of_voucher",
  "status": 200,
  "amount": "monetary_value_of_voucher"
}
```

#### Error: Invalid PIN Format

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Invalid PIN format. The PIN must be a 12-digit numeric value."
}
```

*Make sure to handle these responses in your application to provide appropriate feedback to the user.*

For more assistance or to report issues, please contact our API support team.

[Return to Auth Docs](auth.md)

[Proceed to Redemption Docs](redemption.md)
