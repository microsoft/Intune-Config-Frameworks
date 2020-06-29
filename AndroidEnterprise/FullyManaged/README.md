
# Android Enterprise Security Configuration Framework - Fully Managed

As mobile usage becomes more prevalent in your organizations, so does the need to protect your work or school data on those devices. One method used to protect that data is through device enrollment. Device enrollment enables organizations to deploy compliance policies (PIN strength, jailbreak/root validation, etc.), as well as configuration policies (WIFI, certificates, VPN, etc.). Device enrollment also enables organizations to manage app lifecycle.

With Android 5.0, Google introduced a new management profile with the introduction of managed device (device owner) and work profile (profile owner) modes (what is collectively known as Android Enterprise now).

Android Enterprise supports several enrollment scenarios, two of which are covered as part of this framework:

- Android Enterprise work profile – this enrollment model is typically used for personally-owned devices, where IT wants to provide a clear separation boundary between work and personal data. Policies controlled by IT ensure that the work data cannot be transferred into the personal profile.
- Android Enterprise fully managed devices – these devices are corporate-owned, associated with a single user, and used exclusively for work and not personal use.

The Android Enterprise security configuration framework is organized into several distinct configuration scenarios, providing guidance for work profile and fully managed scenarios.

For Android Enterprise fully managed devices:

- Fully managed basic security (Level 1) – Microsoft recommends this configuration as the minimum security configuration for an enterprise device. This configuration is applicable to most mobile users accessing work or school data. Some of the controls may impact user experience.
- Fully managed enhanced security (Level 2) – Microsoft recommends this configuration for devices where users access sensitive or confidential information. Some of the controls may impact user experience.
- Fully managed high security (Level 3) - Microsoft recommends this configuration for devices used by specific users or groups who are uniquely high risk (users who handle highly sensitive data where unauthorized disclosure causes considerable material loss to the organization). An organization likely to be targeted by well-funded and sophisticated adversaries should aspire to this configuration.

> [!NOTE]
> The framework is designed with the understanding that organizations own the Android Enterprise fully managed devices.

For more information, see [Android Enterprise Security Configuration Framework](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework).

## Prerequisites

Importing the JSON templates into an Intune tenant requires the following:

- Install the AzureAD PowerShell module by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt
- An Intune tenant which supports the Azure Portal with a production or trial license (https://docs.microsoft.com/en-us/intune-azure/introduction/what-is-microsoft-intune)
- Using the Microsoft Graph APIs to configure Intune controls and policies requires an Intune license.
- An account with permissions to administer the Intune Service
- PowerShell v5.0 on Windows 10 x64
- First time usage of these scripts requires a Global Administrator of the Tenant to accept the permissions of the application

## Steps

1. Download the [CompliancePolicy_Import_FromJSON.ps1](https://github.com/microsoftgraph/powershell-intune-samples/blob/master/CompliancePolicy/CompliancePolicy_Import_FromJSON.ps1).
1. Download the [DeviceConfiguration_Import_FromJSON.ps1](https://github.com/microsoftgraph/powershell-intune-samples/blob/master/DeviceConfiguration/DeviceConfiguration_Import_FromJSON.ps1).
1. Download the JSON templates in this directory.
1. Open Windows PowerShell.
1. Navigate to the directory containing the script and execute CompliancePolicy_Import_FromJSON.ps1 or DeviceConfiguration_Import_FromJSON.ps1.
1. The first time you run the script, you will be asked to authenticate with Azure Active Directory:
    ```
    Please specify your user principal name for Azure Authentication:
    ```
    Once you have provided a user principal name a popup will open prompting for your password. After a successful authentication with Azure Active Directory the user token will last for an hour, once the hour expires within the PowerShell session you will be asked to re-authenticate.

6. If you are running the script for the first time against your tenant a popup will be presented stating:

    ```
    Microsoft Intune PowerShell needs permission to:

    * Sign you in and read your profile
    * Read all groups
    * Read directory data
    * Read and write Microsoft Intune Device Configuration and Policies (preview)
    * Read and write Microsoft Intune RBAC settings (preview)
    * Perform user-impacting remote actions on Microsoft Intune devices (preview)
    * Sign in as you
    * Read and write Microsoft Intune devices (preview)
    * Read and write all groups
    * Read and write Microsoft Intune configuration (preview)
    * Read and write Microsoft Intune apps (preview)
    ```
    Note: If your user account is targeted for device based conditional access your device must be enrolled or compliant to pass authentication.

7. The script will prompt you to enter the full path to the JSON template file. Enter the full path escaping with quotation marks; for example "C:\Framework\JSON\level-1-wp-basic-security-compliance.json"

    ```
    Please specify a path to a JSON file to import data from e.g. C:\IntuneOutput\Policies\policy.json:
    ```
8. Verify that the script import is successful by reviewing the policy within Microsoft Endpoint Manager.
9. Assign the policy to users.


## Additional resources

- [Intune Graph Samples](https://github.com/microsoftgraph/powershell-intune-samples)
- [Android Enterprise Security Configuration Framework](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework)

## Copyright

Copyright (c) 2020 Microsoft Corporation. ALl rights reserved.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
