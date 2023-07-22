# Troubleshooting

Below are some common issues that users have had from initial deployment, updating and general usage.

Note that these steps come from the community - if you notice any mistakes, please either edit this page or get in touch via the [Discord server](https://discord.gg/Cyberdrain). Please note the Contributor Code of Conduct.

### Clear Token Cache

{% hint style="info" %}
Hosted clients can clear their own token cache via [management.cipp.app](https://management.cipp.app)
{% endhint %}

1. Go to Settings
2. Select **Backend**
3. Select **Go to Function App Configuration**
4. At each item that has the source _Key Vault_ there should be a green checkbox. If there is no green checkbox, restart the function app and try in 30 minutes
5. Rename the _RefreshToken_, for example to _RefreshToken2_
6. Select **Save**
7. Select **Overview** in the side menu
8. Stop the app & wait 5 minutes.
9. Start the app
10. Go back to **Configuration** in the side menu.
11. Reset the token names to their original values, for example back to _RefreshToken_ and then Select **Save**.
12. Stop the app once more for 5 minutes then start it again.

The tokens should no longer be in the cache.

### Multi-Factor Authentication Troubleshooting

1. The account you use to generate your SAM tokens for CIPP must have Microsoft (Azure AD) MFA enabled, it can't use third-party MFA.
2. You can't have the `Allow users to remember multi-factor authentication on devices they trust` option enabled in the [classic MFA admin portal](https://account.activedirectory.windowsazure.com/UserManagement/MfaSettings.aspx). In either customer or the partner tenant.
3. Check our section on [Conditional Access](https://cipp.app/docs/user/gettingstarted/postinstall/conditionalaccess/) on how to handle Conditional Access issues.

### Request not applicable to target tenant.

The required license for this feature is not available for this tenant. Check the tenant's license information to ensure that it has the necessary license for the requested operation. Most seen around security tasks that require M365 BP or Azure AD P1.

### Neither tenant is B2C or tenant doesn't have premium license

This feature requires a P1 license or higher. Check the license information of your clients tenant to ensure that they have the necessary licenses.

### Response status code does not indicate success: 400 (Bad Request).

Error 400 occurred. There is an issue with the request. Most likely an incorrect value is being sent. If you receive this error with a permissions check, please redo your SAM setup.

### _Microsoft.Skype.Sync.Pstn.Tnm.Common.Http.HttpResponseException_

Could not connect to Teams Admin center. The tenant might be missing a Teams license. Check the license information to ensure that the necessary licenses are available.

### _Provide valid credential._

This occurs when GDAP has been deployed, but the user is not in any of the GDAP groups.

### subscription within the tenant has lapsed

There is no Exchange subscription available, so exchange connections are no longer possible.

### _User was not found._

The relationship between this tenant and the partner has been dissolved from the **client** side. Check the partner relationship information and ensure that it is still active. This error also occurs when a GDAP relationship has expired.

### _The user or administrator has not consented to use the application_

Multiple Potential Causes:

1. The user has not authorized the CIPP-SAM Application. Use the Settings -> Tenants -> Refresh button to refresh the permissions.
2. The user that was used for the CIPP Authorisation is a guest in this tenant
3. DAP: If the client is using DAP. The user might not be in the AdminAgents group.
4. GDAP: if you are using GDAP and have not added the user to the correct group(s) for CIPP to function.

### _AADSTS50020_ or The user you have used for your Secure Application Model is a guest in this tenant, or your are using GDAP and have not added the user to the correct group. Please delete the guest user to gain access to this tenant.

1. The user has not authorized the CIPP-SAM Application. Use the Settings -> Tenants -> Refresh button to refresh the permissions.
2. The user that was used for the CIPP Authorisation is a guest in this tenant
3. The user might not be in the AdminAgents group.
4. GDAP: if you are using GDAP and have not added the user to the correct group(s) for CIPP to function.

### _invalid or malformed_

The request is malformed. the body does not contain JSON or variables have not expanded. Look for typos such as incorrect bracket usage

### _Windows Store repository apps feature is not supported for this tenant_

This tenant does not have Intune WinGet support available. Check the licensing information to ensure that the necessary licenses are available.

### AADSTS650051

The application was approved by the user, but does not exist yet. Wait 5 minutes and try to reauthorize.

### _AppLifecycle\_2210_

Failed to call Intune APIs. Does the tenant have a license available? Check the license information to ensure that the necessary licenses are available.

### Insufficient access rights to perform the operation.

The user does not have sufficient access rights to perform the operation or is missing the necessary Exchange role. Check the user's access rights and Exchange role information, when using GDAP the user must be in the "Exchange Administrators" group.

### Device object was not found in the tenant 'xxxxxxxxxx' or 'UserPrincipal doesn't have the key ID configured'

When executing the first authorization for CIPP, a trusted device was used. This device has been deleted from the Intune portal. Reauthorization is required by using the SAM Wizard "I'd like to refresh my tokens" option.

### The provided grant has expired due to it being revoked, a fresh auth token is needed. The user might have changed or reset their password

The user that authorized the CSP or Graph API connection has had their password changed, sessions revoked, or account disabled. Reauthorization is required by using the SAM Wizard "I'd like to refresh my tokens" option.

### Due to a configuration change made by your administrator, or because you moved to a new location, you must use multi-factor authentication to access

This error can have two causes.

1. The user has not had MFA set up when performing authorization.
2. The client has Conditional Access policies blocking CIPP's access. See the chapter about Conditional Access to resolve.

### presented multi-factor authentication has expired to the policies configured by your administrator, you must refresh your multi-factor authentication to access

This error occurs when a Conditional Access Policy has set the maximum lifetime. Suggested is to change the Conditional Access Policy to exclude "Service Provider users". See the chapter about how to resolve this under Conditional Access.

### The token has expired

The refresh token could not be retrieved and stored. The user must reauthorize.

### The property 'LastGraphError' cannot be found on this object

This error occurs when CIPP cannot write to the errors table - Clear your tenant cache from the settings menu and try again. You might also receive the error when a tenant access check has failed, the only way to clear the Last Graph Error is by removing the tenant cache.

### AADSTS7000222: The provided client secret keys for app {appid} are expired.

This occurs when the app has exists for more than 2 years and requires a new certificate or secret, or when a secret has been expired manually.

1. [Go to Azure Portal](https://portal.azure.com/#view/Microsoft\_AAD\_IAM/ActiveDirectoryMenuBlade/\~/RegisteredApps)
2. Find and click on your app
3. Navigate to "Certificates & secrets"
4. Click "+ New client secret"
5. Enter a description, choose an expiration, and click "Add"
6. Copy the new client **secret value**
7. Go to CIPP -> Settings -> SAM Wizard
8. Use the option "I have an existing application and would like to enter my keys"
9. Enter only the new secret and click Next.
10. Execute a Token Cache Clear. Hosted clients can clear their own token cache via [management.cipp.app](https://management.cipp.app)

{% hint style="info" %}
Hosted clients can clear their own token cache via [management.cipp.app](https://management.cipp.app)
{% endhint %}

#### Credits

This troubleshooting document was created with the help of [Ashley Cooper](https://www.linkedin.com/in/adelnet/)
