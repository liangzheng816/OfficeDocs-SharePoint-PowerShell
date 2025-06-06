---
manager: mengkel
ms.author: samkabue
title: Get started with the SharePoint Online Management Shell
description:  Get started with the SharePoint Online Management Shell
---

# Get started with SharePoint Online Management Shell #

To get started using PowerShell to manage SharePoint Online, you need to install the SharePoint Online Management Shell and connect to SharePoint Online.

Install the SharePoint Online Management Shell by downloading and running the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251) or installing the module from the [PowerShell Gallery](https://www.powershellgallery.com/packages/Microsoft.Online.SharePoint.PowerShell/). Once installed, the module is available for use, and you do not need to install it again until you need features introduced in a later version. For example, you may need to install a new version for TLS 1.2 negotiation after October 2018.

First you can check if you have already installed the SharePoint Online Management Shell by running the following command in administrative mode in PowerShell:

```powershell
Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ListAvailable | Select Name,Version
```

If your operating system is using Windows PowerShell 5, you can also install the SharePoint Online Management Shell by running the following command in administrative mode:

```powershell
Install-Module -Name Microsoft.Online.SharePoint.PowerShell
```

If you don't have administrative privileges on the system, you can install the SharePoint Online Management Shell only for the current user by running the following command: 

```powershell
Install-Module -Name Microsoft.Online.SharePoint.PowerShell -Scope CurrentUser
```

To ensure you have all available cmdlets, you should always make sure the module is up to date. You can update the SharePoint Online Management Shell by running the following command in administrative mode:

```powershell
Update-Module -Name Microsoft.Online.SharePoint.PowerShell
```

To open the SharePoint Online Management Shell command prompt, from the **Start** screen, type **sharepoint**, and then click **SharePoint Online Management Shell**.

> [!VIDEO https://www.youtube.com/embed/TMzHAWEQjlk]

> [!NOTE]
> In order to run SharePoint Online PowerShell commands in a Windows PowerShell 7 console, you must import the SharePoint module using the -UseWindowsPowerShell parameter.
```powershell
Import-Module Microsoft.Online.SharePoint.PowerShell -UseWindowsPowerShell
```

## To connect with a user name and password

1. Run the following command at the SharePoint Online Management Shell command prompt:

   ```powershell
   Connect-SPOService -Url https://contoso-admin.sharepoint.com -Credential admin@contoso.com
   ```

2. When prompted with the Windows PowerShell credential request dialog box, type the password for the SharePoint admin account.

To assign a user the SharePoint admin role, see [Assign admin roles](/microsoft-365/admin/add-users/assign-admin-roles) or [Assign admin roles to Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/assign-roles-to-user-accounts-with-microsoft-365-powershell).

> [!NOTE]
> If you encounter issues trying to connect or receive an error such as 'Error message: Could not connect to SharePoint Online', you may need to use Modern Authentication. See the following example: 

  ```powershell
  Connect-SPOService -Credential $creds -Url https://tenant-admin.sharepoint.com -ModernAuth $true -AuthenticationUrl https://login.microsoftonline.com/organizations
   ```

## To connect with multifactor authentication (MFA)

1. Run the following command at the SharePoint Online Management Shell command prompt:

   ```powershell
   Connect-SPOService -Url https://contoso-admin.sharepoint.com
   ```

2. When prompted with the **Microsoft SharePoint Online Management Shell** dialog box, type the account name and password for a SharePoint administrator account, and then click **Sign in**.

3. Follow the instructions in the **Microsoft SharePoint Online Management Shell** dialog box to provide the additional authentication information, such as a verification code, and then click **Sign in**.

You are now ready to use SharePoint Online commands.

> [!NOTE]
> There is a known issue between the SharePoint Online Management Shell module and SharePoint Client Components SDK where the module will fail to load if both are installed on the same computer. If you encounter this issue, uninstall the SharePoint Client Components SDK.
