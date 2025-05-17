# User and Group Management

## Objective
This section covers how to create and manage users and groups in Azure Active Directory (Entra ID) to control access and permissions.

---

## Prerequisites

- Azure AD Administrator or equivalent permissions.
- Access to the Azure Portal or Azure CLI/PowerShell.
- AzureAD or Microsoft.Graph PowerShell modules installed (depending on version used).

---

## Step 1: Create a New User in Azure Portal

1. Sign in to the [Azure Portal](https://portal.azure.com).
2. Navigate to **Azure Active Directory** > **Users**.
3. Click **+ New user**.
4. Fill in the required fields like **Name**, **Username**, and optionally assign roles.
5. Click **Create**.

![Create New User in Azure Portal](images/user-management-step1.png)

---

## Step 2: Create a New User Using PowerShell

```powershell
# Connect to Azure AD
Connect-AzureAD

# Create a new user with password profile
New-AzureADUser -DisplayName "John Doe" `
                -UserPrincipalName "john.doe@example.com" `
                -AccountEnabled $true `
                -PasswordProfile @{ Password = "P@ssword123"; ForceChangePasswordNextLogin = $true } `
                -MailNickname "johndoe"

## Step 3: Create a New Group in Azure Portal

1. Sign in to the [Azure Portal](https://portal.azure.com).
2. Navigate to **Azure Active Directory** > **Groups**.
3. Click **+ New group**.
4. Select the **Group type** (Security or Microsoft 365).
5. Enter a **Group name** and **Description**.
6. Click **Create**.

![Create New Group](images/group-management-step1.png)

---

## Step 4: Add Users to a Group Using PowerShell

```powershell
# Connect to Azure AD
Connect-AzureAD

# Add user to a group
Add-AzureADGroupMember -ObjectId <GroupObjectId> -RefObjectId <UserObjectId>

