
# Intune Configuration Framework

As mobile usage becomes more prevalent in your organizations, so does the need to protect against data leakage scenarios. Intune offers choices to organizations to tailor the protection to their specific needs through APp Protection Policies, as well as device compliance and configuration policies for mobile platforms. For some, it may not be obvious which policy settings are required to implement a complete scenario. To help organizations prioritize client endpoint hardening, Microsoft is leveraging a configuration framework taxonomy that is broken down into distinct configuration levels, with each level building off the previous level. 

This repository includes the configuration level JSON templates for Intune App Protection Policies and device compliance and configuration policies for mobile platforms. The JSON templates can be imported into Intune using the Intune PowerShell scripts.

As with any framework, settings within a corresponding level may need to be adjusted based on the needs of the organization as data protection must evaluate the threat environment, risk appetite, and impact to usability. 

## Prerequisites

Importing the JSON templates into an Intune tenant requires the following:

- Install the AzureAD PowerShell module by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt
- An Intune tenant which supports the Azure Portal with a production or trial license (https://docs.microsoft.com/mem/intune/fundamentals/what-is-intune)
- Using the Microsoft Graph APIs to configure Intune controls and policies requires an Intune license.
- An account with permissions to administer the Intune Service
- PowerShell v5.0 on Windows 10 x64
- First time usage of these scripts requires a Global Administrator of the Tenant to accept the permissions of the application

## Additional resources

- [Intune Graph Samples](https://github.com/microsoftgraph/powershell-intune-samples)

## Copyright

Copyright (c) 2020 Microsoft Corporation. ALl rights reserved.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
