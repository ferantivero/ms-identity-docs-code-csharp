---
# Metadata required by https://docs.microsoft.com/samples/browse/
# Metadata properties: https://review.docs.microsoft.com/help/contribute/samples/process/onboarding?branch=main#add-metadata-to-readme
languages:
- csharp
page_type: sample
name: ".NET MAUI Multi-platform App Sign-in user"
description: "This is a .NET MAUI Multi-platform App Sign-in user that sign-in users. The code in this sample is used by one or more articles on docs.microsoft.com."
products:
- azure
- azure-active-directory
- ms-graph
urlFragment: ms-identity-docs-code-csharp
---
# .NET MAUI Multi-platform App - Sign-in user | Microsoft identity platform

<!-- Build badges here
![Build passing.](https://img.shields.io/badge/build-passing-brightgreen.svg) ![Code coverage.](https://img.shields.io/badge/coverage-100%25-brightgreen.svg) ![License.](https://img.shields.io/badge/license-MIT-green.svg)
-->

This sample demonstrates a .NET MAUI Multi-platform App that sign-in users by using the `Microsoft.Identity.Client`.

<!-- IMAGE or CONSOLE OUTPUT of running/executed app -->

> :page_with_curl: This sample application backs one or more technical articles on docs.microsoft.com. <!-- TODO: Link to first tutorial in series when published. -->

## Prerequisites

1. An Azure Active Directory (Azure AD) tenant. You can [open an Azure account for free](https://azure.microsoft.com/free) to get an Azure AD instance.
1. [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/#download-preview)
1. [.NET 6.0 SDK](https://dotnet.microsoft.com/download/dotnet/6.0)
1. [.NET MAUI](https://docs.microsoft.com/en-us/dotnet/maui/get-started/installation)

## Setup

### 1. Register the web API application in your Azure Active Directory

First, complete the steps in [Register an application with the Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/quickstart-register-app) to register the sample app.

Use the following settings for your app registration:

| App registration <br/> setting | Value for this sample app                                         | Notes                                                                                                       |
|:------------------------------:|:------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| **Name**                       | `active-directory-dotnet-xplat-maui`                              | Suggested value for this sample. <br/> You can change the app name at any time.                             |
| **Supported account types**    | **My organization only**                                          | Required for this sample. <br/> Support for the Single tenant.                                              |
| **Platform type**              | `Mobile and desktop applications`                                 | Required value for this sample. <br/> Enables the required and optional settings for the app type.          |
| **Redirect URIs**              | `https://login.microsoftonline.com/common/oauth2/nativeclient`    | Required value for this sample. <br/> You can change that later in your own implementation.                 |

> :information_source: **Bold text** in the table matches (or is similar to) a UI element in the Azure portal, while `code formatting` indicates a value you enter into a text box or select in the Azure portal.

<details>
   <summary>:computer: Alternative: Register the application using az-cli</summary>

1. Register a new Azure AD App with a reply url

   ```bash
   AZURE_AD_APP_CLIENT_ID_XPLAT=$(az ad app create --display-name "active-directory-dotnet-xplat-maui" --reply-urls "https://login.microsoftonline.com/common/oauth2/nativeclient" --native-app true --query appId -o tsv)
   ```

</details>

### 2. Configure the web app

1. Open the `XPlat.csrpoj` under the the `sign-in-xplat` folder in your code editor.
1. Open the `MainPage.xaml.cs` file and modify the following code:

    ```csharp
    private const string ClientId = "[Enter the Client Id (Application ID obtained from the Azure portal), e.g. ba74781c2-53c2-442a-97c2-3d60re42f403]";
    private const string Tenant = "[Copy the Tenant Id from the Azure portal]";
    ```

## Run the application

### 1. Run the .NET MAUI App

1. Press `F5` and ensure you have selected `Windows Machine`

### 2. Signin into the app

1. Once the app is running you can sign-in with your user credentials.

### 3. Clean up

1. Delete the Azure AD app

   ```bash
   az ad app delete --id $AZURE_AD_APP_CLIENT_ID_XPLAT
   ```

## About the code

The .NET MAUI Multi-platform App will allow users to sign-in, so it can retrieve a Security Token scoped specifically for the Microsoft Graph API, and will use that token to access the user's information.

## Reporting problems

### Sample app not working?

If you can't get the sample working, you've checked [Stack Overflow](http://stackoverflow.com/questions/tagged/msal), and you've already searched the issues in this sample's repository, open an issue report the problem.

1. Search the [GitHub issues](../../../../issues) in the repository - your problem might already have been reported or have an answer.
1. Nothing similar? [Open an issue](LINK_HERE) that clearly explains the problem you're having running the sample app.

### All other issues

> :warning: WARNING: Any issue _not_ limited to running this or another sample app will be closed without being addressed.

For all other requests, see [Support and help options for developers | Microsoft identity platform](https://docs.microsoft.com/azure/active-directory/develop/developer-support-help-options).

## Contributing

If you'd like to contribute to this sample, see [CONTRIBUTING.MD](/CONTRIBUTING.md).

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.