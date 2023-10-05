## Guide to Create App Registration in Azure

Creating an App Registration in Azure is a fundamental step when you want to integrate your application with Azure services or Microsoft Graph. In this guide, we’ll walk through the process of setting up an App Registration in Azure and assigning the necessary permissions for the scenarios you outlined.

### Prerequisites:
- An Azure account.
- The necessary permissions: [Link provided](https://learn.microsoft.com/en-us/graph/api/user-list?view=graph-rest-1.0&tabs=http)

### Steps:

1. **Login to Azure Portal**:
   - Go to the [Azure Portal](https://portal.azure.com/).
   - Sign in using your Azure credentials.

2. **Navigate to App Registrations**:
   - In the left navigation pane, search for and select “App registrations”.

3. **Create New Registration**:
   - Click on the “New registration” button at the top.
   - Provide a meaningful name for your application.
   - Leave the default settings for Supported account types or choose as per your requirement.
   - Click "Register".

4. **Assign Permissions**:

   For **Delegated** permissions:
   - Under “Manage”, click on “API permissions”.
   - Click on "Add a permission" and select “Microsoft Graph”.
   - Select “Delegated permissions”.
   - Add the following permissions:
     - User.ReadBasic.All
     - User.ReadAll
     - User.Directory.ReadAll

   For **Application** permissions:
   - Repeat the steps above but select “Application permissions” instead of “Delegated permissions”.
   - Add the following permissions:
     - User.ReadAll
     - User.Directory.ReadAll

5. **No Write Permissions**:
   - Ensure that no write permissions are granted if you only need read access.

6. **Retrieve Values for Power App**:
   - Go to the “Overview” tab.
   - Here, you'll find Application (client) ID, Directory (tenant) ID, and other details which can be put into the Power App as variables as needed.

7. **Validation**:
   - If there's an issue with permissions after you've set up your App Registration, you can troubleshoot using the Microsoft Graph API Explorer.
   - Copy the command/query from the HTTP OK connector.
   - Navigate to the [Graph API Explorer](https://developer.microsoft.com/en-us/graph/graph-explorer).
   - Paste the command/query into the Graph API Explorer.
   - Head over to the permissions tab to see what permissions might be missing. You can differentiate between directory and user permissions and identify what you might have missed.

### Important Notes:

- Ensure that your App Registration is set up prior to running any flows. If it's not correctly set up or if you don't have the necessary permissions, the flow will indicate that the proper permissions are missing.

- This guide assumes that you’re familiar with Azure and Microsoft Graph concepts. If you’re not, you might need to explore Azure documentation further or consider engaging with Azure support or community forums for specific issues or queries.

By following this guide, you should have a correctly set-up App Registration with the right permissions for your needs. Remember to always review and ensure that you’re not over-provisioning permissions; only grant what's necessary for your application's functionality.
