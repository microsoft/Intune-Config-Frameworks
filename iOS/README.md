
# iOS/iPadOS Security Configuration Framework

As mobile usage becomes more prevalent in your organizations, so does the need to protect your work or school data on those devices. One method used to protect that data is through device enrollment. Device enrollment enables organizations to deploy compliance policies (PIN strength, jailbreak/root validation, etc.), as well as configuration policies (WIFI, certificates, VPN, etc.). Device enrollment also enables organizations to manage app lifecycle.

iOS/iPadOS supports several enrollment scenarios, two of which are covered as part of this framework:

- [Device enrollment for personally owned devices](https://docs.microsoft.com/mem/intune/enrollment/ios-enroll): These devices are personally owned and used for both work and personal use.
- [Supervised automated device enrollment for corporate-owned devices](https://docs.microsoft.com/mem/intune/enrollment/device-enrollment-program-enroll-ios): These devices are corporate-owned, associated with a single user, and used exclusively for work and not personal use.

The iOS/iPadOS security configuration framework is organized into several distinct configuration scenarios, providing guidance for personally owned and supervised devices.

For more information, see [iOS/iPadOS Security Configuration Framework](https://docs.microsoft.com/mem/intune/enrollment/ios-ipados-configuration-framework).

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
- [iOS/iPadOS Security Configuration Framework](https://docs.microsoft.com/mem/intune/enrollment/ios-ipados-configuration-framework)

## Copyright

Copyright (c) 2021 Microsoft Corporation. ALl rights reserved.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
