# Redeem Xash-OTT API Documentation

This documentation covers the process of redeeming an OTT voucher using the Xash-OTT API. The API endpoint accepts a voucher PIN and returns a status code indicating the outcome of the redemption process.

## Beta Version Notice

Please note that this API method is in beta. It is experimental, and errors may be expected.

## Making a Redeem Request

To redeem an OTT voucher, send an authenticated request with your JWT to the following endpoint:

### Endpoint

```
POST https://<BASE_URL>/api/v0.1/ott-redeem
```

### Headers

```
Authorization: Bearer <YOUR_JWT_TOKEN>
```

Replace `<BASE_URL>` with the actual base URL of the Xash API, and `<YOUR_JWT_TOKEN>` with the JWT token you obtained after authenticating.

### Body Parameters

- `pin` (string): The voucher PIN to redeem.
- `uid` (string, optional): A unique identifier for the request.
- `phone` (string): The user's phone number for reference.

### Successful Redemption Response

If the voucher is redeemed successfully, and the account is topped up, the API will return:

```json
{
  "message": "Redeemed Successfully",
  "data": {
    "units": "0.25",
    "amount": "R4.65",
    "phone": "+263771234567"
  }
}
```

### Pending Top-Up Response

If the PIN is redeemed but the account top-up fails, the server will retry the top-up in 10 minutes:

```json
{
  "message": "Pending top-up",
  "data": {
    "units": "0.25",
    "amount": "R5.00",
    "phone": "+26371234567"
  }
}
```

### Error Responses

#### Invalid Voucher or Phone

If the provided phone number or PIN is invalid or has been used, the API will return:

```json
{
  "statusCode": 400,
  "error": "Bad Request",
  "message": "Invalid Voucher. If this is an error, kindly contact support || \"OTT Pin\" with value \"377569623311s\" fails to match the required pattern: /^\\d+$/"
}
```

#### Unauthorized Access

If the JWT token is invalid:

```json
{
  "statusCode": 401,
  "error": "Unauthorized",
  "message": "Invalid token. || ERROR_MESSAGE"
}
```

For support or more information on using the Redeem Xash-OTT API, please reach out to our API support team.


[Return to Verification Docs](verification.md)