# PasswordExpired
This workflow will send a Microsoft Teams message through Flowbot when a user's password is set to expire in 14 days

**Guide to Setting Up "Password Expired" Flow in Power Automate**

## Overview:

This guide will walk you through the process of setting up the "Password Expired" flow in Power Automate. This flow notifies users when their password is about to expire.

## Prerequisites:
- Azure App Registration.
- Power Automate account with a premium or per-user plan.
- Ensure you have enough API calls for this operation.

## Step-by-Step Instructions:

1. **Reoccurring Trigger Setup**:
   - Set your notice on a reoccurring trigger.
   - Configure the trigger to recur every day.

2. **Setting Up Variables**:
   - **varNumberDates**: Defines when you want the notification to start.
   - **varPassValid**: Input the duration (in days) for which the password is valid. Example: 90 days.
   - **varexpirationDate**: Stores the expiration date. It's a combination of the password's valid duration and the last reset date.
   - **vartenantID**: Retrieve this from your Azure Active Directory.
   - **varclientID**: Input the value from the app registration you created.
   - **varSecret**: This is where you input your secret key.

3. **HTTP Request Function**:
   - No changes are needed for the "Get user data" function.
   - This will list out the required information.

4. **Composing and Parsing JSON**:
   - Use the compose function to display the calculated values.
   - In the "Parse JSON" step, set it to ignore if a display name or email is null.
   - This step uses the user principal name for verification in the subsequent steps.

5. **Concurrency Settings**:
   - In the "Apply to each" loop, you can set it to run concurrently for up to 50 operations or dial it down if needed.

6. **Setting Expiration Date**:
   - Perform a calculation by adding the expiration last day's date to the number of valid days to get the expiration date.

7. **Conditions and Notifications**:
   - Use conditions to check if the password expiration is less than or equal to a specific number of days (e.g., 14 days).
   - If the condition is met, a message will be sent to the user via Power Automate. Otherwise, no action is taken.

8. **Posting Messages in Chat**:
   - Use the "Flowbot" to post messages. If done as a user, it will attach to a specific user, but as Flowbot, it appears as a Power Automate message.
   - The recipient is determined using the user principal name from the Graph API call.
   - In the message body, notify the user about the password expiration date and convert the time from UTC to your desired timezone.

9. **Testing**:
   - The flow has been tested with 2700 users and takes approximately 37 minutes to complete, sending batches of 50 notifications at a time.

10. **Caveat**:
   - Ensure you have enough API calls to execute this flow.
   - A premium or per-user plan is needed due to the HTTP connector.

## Conclusion:

This "Password Expired" flow is essential for organizations to remind their users in advance about password expirations. Ensure to test in your environment and adjust settings as necessary.
