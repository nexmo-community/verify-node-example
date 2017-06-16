# Two-Factor Authentication (2FA) Example for Node.JS

This node server offers an API to use the Nexmo Verify API to show off how to make a 2FA request.

## Configure with Your Nexmo API Keys

To use this sample you will first need a [Nexmo account](https://dashboard.nexmo.com/sign-up). Once you have your own API credentials, go to `.env` and set the values as required.

## 2FA Flow

1. Send a `POST` to `https://nexmo-verify.glitch.me/request` with a JSON body like `{"number": 14155550100}` Don't forget to include the country code!
2. You'll receive a JSON response with a `requestId` Take note of it! You need it to finish the 2FA request. The JSON response will look something like:
```json
{"requestId": "aaaaaaaabbbbccccdddd0123456789ab"}
```
3. You should receive an SMS with a 4 digit code. If you don't respond within 5 minutes, you'll also receive a voice call that will tell you your 4 digit code.
4. Send a `POST` to `https://nexmo-verify.glitch.me/check` with a JSON body including the `code` and the `requestId` It should look something like:
```json
{"code": "5309",
"request_id": "aaaaaaaa-bbbb-cccc-dddd-0123456789ab"}
```
5. If everything is successful you'll get a `200 OK` response with a json body of a response.

## Tutorials & Sample Code

This glitch porject is based off of the following resources:

- [How to Add Two-Factor Authentication (2FA) to Your Node.JS Web Apps Blog Post](https://www.nexmo.com/blog/2017/04/11/implement-two-factor-authentication-2fa-web-apps-node-js-dr/)

- [Two-Factor Authentication (2FA) Example for Node.JS GitHub Repo](https://github.com/nexmo-community/nexmo-node-quickstart/tree/master/verify)
