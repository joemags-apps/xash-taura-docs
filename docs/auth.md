# Xash API Documentation

Welcome to the Xash API Documentation. This guide provides instructions on how to get started with the Xash API, including how to authenticate and create a JSON Web Token (JWT) for securing your API calls.

## Authentication

The Xash API employs a combination of an email/username and password to generate JWTs for authenticating API endpoints.

### Account Creation

Before you begin making API calls, you need to create an account with Xash. Once your account is created, you can generate your JWT.

### Creating a JWT Token

Here is a quick example of how to create a JWT token:

#### Using Axios in Node.js

```js
import axios from 'axios';

const options = {
  method: 'POST',
  url: 'https://<BASE_URL>/auth/local',
  headers: {'Content-Type': 'application/json'},
  data: {
    identifier: 'username_or_email',
    password: 'YOUR_ACCOUNT_PASSWORD'
  }
};

axios.request(options).then(function (response) {
  console.log(response.data);
}).catch(function (error) {
  console.error(error);
});
```

Replace `<BASE_URL>` with the actual base URL of the Xash API. The `identifier` can be either your username or email, and `password` should be your account password.

### Successful Response

After sending the POST request to the authentication endpoint, you should receive a response containing your JWT. Here's an example of a successful response:

```json
{
  "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9....",
  "user": {
    "username": "username",
    "email": "email@example.com",
    "role": {
      "id": 1,
      "name": "Authenticated",
      "description": "Default role given to authenticated user.",
      "type": "authenticated"
    }
  }
}
```

Make sure to save the `jwt` value securely, as it will be required for all subsequent API calls that require authentication.

For further details on using the Xash API, refer to the following sections of our documentation or contact our support team.

[Return to Main Documentation](/)


[Proceed to Verification Documentation](verification.md)