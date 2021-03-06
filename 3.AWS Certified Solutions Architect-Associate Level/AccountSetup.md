# Getting Started

1. Create an AWS Account
2. Setting up a billing alarm
3. Adding MFA to the account root user

## 1. Create an AWS Account

Any new AWS account includes 12-months of free tier access. [Create a free account on AWS here](https://aws.amazon.com/free/ ).

## 2. Setting up a billing alarm

Creating a billing alarm sends an email message to the user when the estimated charges for AWS exceeds a specified threshold. Steps to create a billing alarm:

### Enable Billing Alert

1) Log-in to the AWS account either as a root user or an IAM user, whose access to the Billing and Cost Management console has been activated.
2) If necessary, change the Region to US East (N. Virginia). Billing metric data is stored in this Region and represents worldwide charges. This data includes the estimated charges for every service in AWS that you use, as well as the estimated overall total of your AWS charges.
3) On the top right corner of the console, click on the account name and select 'My Billing Dashboard' which will take you to the billing console where we will set up the billing alarm.
4) Select 'Billing Preferences' under 'Preferences', on left side of the navigation bar. You will see few check boxes:

    i) Select 'Receive Billing alerts'.

    ii) Select 'Free tier usage alerts' and enter email address associated with the AWS account.

    iii) Select 'Receive PDF Invoice By Email' to receive a PDF version of the invoice via email. This step is optional.

5) Click 'Save Preferences' and the changes you made on this page will be committed to your account.

### Create a Billing Alert using the CloudWatch console

1) Open the [CloudWatch console]( https://console.aws.amazon.com/cloudwatch/) . Click 'Services' on top-left side of the console and type 'CloudWatch' in the search bar.
2) In the left side navigation pane, choose 'Alarms' and then 'Create Alarm'.
3) Choose Select metric. It will take you to the next page where you will see 'Billing' and two metrics under 'Billing'. Click on 'Billing'->'Total Estimated Charge'.
4) Select the check box next to the EstimatedCharges, and choose 'Select metric'.
5) Go to the 'Conditions' part of the page, and select

    i) Threshold type 'Static'.

    ii) Whenever EstimatedCharges is 'Greater' .

    iii) for Than, select the monetary amount that must be exceeded to trigger the alarm. Eg. 100 USD.

6) Choose 'Next'.
7) Under 'Notification', select

    i) Whenever this alarm state is 'in Alarm'.

    ii) Select an SNS topic 'Create new topic'.

    iii) Create a new topic, enter the unique name for notification. In our example, we will set it to 'BillingTopic'.

    iv) Email endpoints that will receive the notification , enter the email id or list of email ids that wil receive the email notification under SNS topic yo just created.

    v) Click 'Create topic'.

    vi) After creating the topic, SNS will send you the confirmation email that you just entered. Go to the email account that you listed in step (iv), Click on the link to confirm the email id.

8) When finished, choose 'Next'.
9) Enter a name and description for the alarm. The name must contain only ASCII characters. Then choose 'Next'.
10) Under 'Preview and create', confirm that the information and conditions are what you want, then choose 'Create alarm'.

### Delete a Billing Alarm

1) Open the [CloudWatch console]( https://console.aws.amazon.com/cloudwatch/) . Click 'Services' on top-left side of the console and type 'CloudWatch' in the search bar.
2) In the left side navigation bar, choose Alarms.
3) Select the check box next to BillingAlarm and choose 'Actions'->'Delete'.
4) When Prompted for confirmation, choose 'Yes,Delete'.

After finishing up with all the steps, go to the AWS home screen. Select 'My Billing Dashboard' from the drop down menu under your account name on top right corner of the screen. It will take you to the Billing and Cost Management Dashboard, which will give you an overview of any cost that have occurred related to the AWS account.

To make things easier going forward, Select 'Cost Explorer' on left side of the navigation bar, and click 'Enable Cost Explorer'. This tool allows you to explore the AWS bills.

## 3. Adding MFA to the account root user

### What is MFA

Multi-factor authentication (MFA) is an authentication method in which a computer user is granted access only after successfully presenting two or more pieces of evidence (or factors) to an authentication mechanism: Password set up by the user and one time password generated by the MFA app on user device like phone etc. Examples of MFA are:

a. Google Authenticator

b. One password

c. LastPass Authenticator

### Setup MFA with AWS account

To set-up MFA with your AWS account, select account name->'My Security Credentials' on top right side of the screen. You will see list of AWS Security Credentials.

1. Select 'Multi-factor authentication (MFA)'
2. Install 'Google Authenticator' on your mobile device.
3. Click on 'Activate MFA'.
4. Choose 'Virtual MFA device' (for authenticator app installed on the mobile device).
5. You will see a small screen pop-up with below options.

    a) Install a device.

    b) Open Google Authenticator on your mobile device. Click 'Show QR code' on the pop-up screen, Scan the QR code from pop-up screen on the Google authenticator app on your mobile device.

    c) Enter 2 consecutive MFA codes on the pop-up screen from the Google authenticator app on your phone.
6. Click 'Assign MFA'.

To verify that you have successfully assigned MFA to your account, sign out from your account and sign-in again. The sign-in console will ask for email id, password and one time generated code. Enter all the credentials and it will take you to the AWS home screen. It means you have successfully added MFA to the root user account.


Links to AWS official site:

1. [AWS Free Trial](https://aws.amazon.com/free/start-your-free-trial/)
2. [Create and Active a new Amazon Wed Service account](https://aws.amazon.com/premiumsupport/knowledge-center/create-and-activate-aws-account/)
3. [Create a billing alert to monitor your estimated AWS charges](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/monitor_estimated_charges_with_cloudwatch.html)
4. [Using MFA in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html)
5. [Enabling MFA devices](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa_enable.html)