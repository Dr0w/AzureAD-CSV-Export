# Azure AD CSV Export
Prerequisites:

## Create and configure app for Azure AD Export
To use service principal authentication, you must configure first the app and permissions.
Steps to Create an App Registration and Configure Permissions
1. Register an App in Azure AD:
Go to the Azure portal.
Navigate to Azure Active Directory > App registrations > New registration.
Name your app and set the supported account types (e.g., single-tenant).
Click Register.
2. Create a Client Secret:
In the app registration, go to Certificates & secrets.
Click New client secret.
Add a description and set an expiration period.
Click Add and copy the client secret value. You won’t be able to see it again.
3. Assign API Permissions:
Go to API permissions.
Click Add a permission > Microsoft Graph > Application permissions.
Add the necessary permission Directory.Read.All.
Click Add permissions and then Grant admin consent for your tenant.
4. Note the Tenant ID and Client ID:
In the app registration, copy the Application (client) ID and Directory (tenant) ID.

## Before you begin, ensure you have the following installed and configured:
- Microsoft Graph PowerShell Module
- PowerShell 7 (or later)
- .NET Framework 4.7.2 (or later)
- Azure App configured for Service Principal Authentication

## Upgrade to PowerShell 7 or Later
- Ensure your PowerShell version is 7 or later. You can check your PowerShell version by running:
$PSVersionTable.PSVersion

## Powershell distribution site:
- Installing PowerShell on Windows
https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.4#installing-the-msi-package

## You can download and install the .NET Framework from the official Microsoft website:
- Download .NET Framework 4.7.2
https://dotnet.microsoft.com/en-us/download/dotnet-framework/net472

## Install Microsoft Graph PowerShell Module
- Follow the instructions here:
https://learn.microsoft.com/en-us/powershell/microsoftgraph/installation?view=graph-powershell-1.0

## Azure App configured for Service Principal Authentication
- tenantId, clientId, clientSecret - are ready

## Steps to Run the Script
- Open PowerShell as Administrator.
- Install the Microsoft.Graph Module:
```powershell
Install-Module -Name Microsoft.Graph -Scope CurrentUser
```
- Copy the script to directory you prefer.
- Navigate to the directory where the script is saved:
```powershell
cd "C:\path\to\your\script\directory"
```
- Execute the script with browser authentication:
```powershell
.\Import_AzureAD.ps1
```
- Execute the script with service principal authentication:
```powershell
.\Import_AzureAD.ps1 -tenantId "your-tenant-id" -clientId "your-client-id" -clientSecret "your-client-secret"
```

- In case you will receive a message like “.ps1 is not digitally signed. The script will not execute on the system.” , run:
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```
>This command sets the execution policy to bypass for only the current PowerShell session after the window is closed, the next PowerShell session will open running with the default execution policy. “Bypass” means nothing is blocked and no warnings, prompts, or messages will be displayed.
