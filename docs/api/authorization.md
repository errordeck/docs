# Authorization

When you send an error to Errordeck, you need to provide an authorization token. This token is used to identify your account and project.

## How to get an authorization token

1. Go to the dashboard
2. Select the team you have project in that you want to send errors to
3. Select the project you want to send errors to
4. Click on Settings
5. Click on API
6. Copy the API key

We use the API key as the authorization token. You can use the API key in the Authorization header. As example an CURL command with authorization token would look like this:


```bash
curl -H "Authorization: Bearer <API_KEY>" https://app.errordeck.com/api/:project_id/store
```