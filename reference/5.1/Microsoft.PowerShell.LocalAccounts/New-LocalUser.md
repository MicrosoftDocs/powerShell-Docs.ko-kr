---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalUser
ms.openlocfilehash: d83f3ad12481df0849ff2fe3f61d553a9ffdcdde
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214673"
---
# <span data-ttu-id="bf6dd-103">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-103">New-LocalUser</span></span>

## <span data-ttu-id="bf6dd-104">개요</span><span class="sxs-lookup"><span data-stu-id="bf6dd-104">SYNOPSIS</span></span>

<span data-ttu-id="bf6dd-105">로컬 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-105">Creates a local user account.</span></span>

## <span data-ttu-id="bf6dd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bf6dd-106">SYNTAX</span></span>

### <span data-ttu-id="bf6dd-107">암호 (기본값)</span><span class="sxs-lookup"><span data-stu-id="bf6dd-107">Password (Default)</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> -Password <SecureString> [-PasswordNeverExpires]
 [-UserMayNotChangePassword] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bf6dd-108">NoPassword</span><span class="sxs-lookup"><span data-stu-id="bf6dd-108">NoPassword</span></span>

```
New-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-Disabled]
 [-FullName <String>] [-Name] <String> [-NoPassword] [-UserMayNotChangePassword] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="bf6dd-109">설명</span><span class="sxs-lookup"><span data-stu-id="bf6dd-109">DESCRIPTION</span></span>

<span data-ttu-id="bf6dd-110">`New-LocalUser`Cmdlet은 로컬 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-110">The `New-LocalUser` cmdlet creates a local user account.</span></span> <span data-ttu-id="bf6dd-111">이 cmdlet은 Microsoft 계정에 연결 된 로컬 사용자 계정 또는 로컬 사용자 계정을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-111">This cmdlet creates a local user account or a local user account that is connected to a Microsoft account.</span></span>

> [!NOTE]
> <span data-ttu-id="bf6dd-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="bf6dd-113">예제</span><span class="sxs-lookup"><span data-stu-id="bf6dd-113">EXAMPLES</span></span>

### <span data-ttu-id="bf6dd-114">예제 1: 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="bf6dd-114">Example 1: Create a user account</span></span>

```
PS C:\> New-LocalUser -Name "User02" -Description "Description of this account." -NoPassword
Name    Enabled  Description
----    -------  -----------
User02  True     Description of this account.
```

<span data-ttu-id="bf6dd-115">이 명령은 로컬 사용자 계정을 만들고 **Accountexpires** 또는 **Password** 매개 변수를 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-115">This command creates a local user account and does not specify the **AccountExpires** or **Password** parameters.</span></span> <span data-ttu-id="bf6dd-116">따라서 계정은 기본적으로 만료 되거나 암호가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-116">Therefore, the account doesn't expire or have a password by default.</span></span>

### <span data-ttu-id="bf6dd-117">예 2: 암호를 포함 하는 사용자 계정 만들기</span><span class="sxs-lookup"><span data-stu-id="bf6dd-117">Example 2: Create a user account that has a password</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> New-LocalUser "User03" -Password $Password -FullName "Third User" -Description "Description of this account."
Name    Enabled  Description
----    -------  -----------
User03  True     Description of this account.
```

<span data-ttu-id="bf6dd-118">첫 번째 명령은 cmdlet을 사용 하 여 암호를 묻는 메시지를 표시 합니다 `Read-Host` .</span><span class="sxs-lookup"><span data-stu-id="bf6dd-118">The first command prompts you for a password by using the `Read-Host` cmdlet.</span></span> <span data-ttu-id="bf6dd-119">명령은 암호를 변수에 보안 문자열로 저장 합니다 `$Password` .</span><span class="sxs-lookup"><span data-stu-id="bf6dd-119">The command stores the password as a secure string in the `$Password` variable.</span></span>

<span data-ttu-id="bf6dd-120">두 번째 명령은에 저장 된 암호를 사용 하 여 로컬 사용자 계정을 만듭니다 `$Password` .</span><span class="sxs-lookup"><span data-stu-id="bf6dd-120">The second command creates a local user account by using the password stored in `$Password`.</span></span> <span data-ttu-id="bf6dd-121">이 명령은 사용자 이름, 전체 이름 및 사용자 계정에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-121">The command specifies a user name, full name, and description for the user account.</span></span>

## <span data-ttu-id="bf6dd-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bf6dd-122">PARAMETERS</span></span>

### <span data-ttu-id="bf6dd-123">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="bf6dd-123">-AccountExpires</span></span>

<span data-ttu-id="bf6dd-124">사용자 계정이 만료 되는 시점을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-124">Specifies when the user account expires.</span></span> <span data-ttu-id="bf6dd-125">**DateTime** 개체를 가져오려면 cmdlet을 사용 `Get-Date` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-125">To obtain a **DateTime** object, use the `Get-Date` cmdlet.</span></span>
<span data-ttu-id="bf6dd-126">이 매개 변수를 지정 하지 않으면 계정이 만료 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-126">If you do not specify this parameter, the account does not expire.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-127">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="bf6dd-127">-AccountNeverExpires</span></span>

<span data-ttu-id="bf6dd-128">계정이 만료 되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-128">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-129">-Description</span><span class="sxs-lookup"><span data-stu-id="bf6dd-129">-Description</span></span>

<span data-ttu-id="bf6dd-130">사용자 계정에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-130">Specifies a comment for the user account.</span></span>
<span data-ttu-id="bf6dd-131">최대 길이는 48 자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-131">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-132">-사용 안 함</span><span class="sxs-lookup"><span data-stu-id="bf6dd-132">-Disabled</span></span>

<span data-ttu-id="bf6dd-133">이 cmdlet이 사용자 계정을 사용할 수 없는 것으로 만들기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-133">Indicates that this cmdlet creates the user account as disabled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-134">-FullName</span><span class="sxs-lookup"><span data-stu-id="bf6dd-134">-FullName</span></span>

<span data-ttu-id="bf6dd-135">사용자 계정의 전체 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-135">Specifies the full name for the user account.</span></span> <span data-ttu-id="bf6dd-136">전체 이름이 사용자 계정의 사용자 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-136">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-137">-Name</span><span class="sxs-lookup"><span data-stu-id="bf6dd-137">-Name</span></span>

<span data-ttu-id="bf6dd-138">사용자 계정의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-138">Specifies the user name for the user account.</span></span>

<span data-ttu-id="bf6dd-139">로컬 시스템에 대 한 로컬 사용자 계정을 만드는 경우 사용자 이름에는 최대 20 자의 대문자 또는 소문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-139">If you create a local user account for the local system, the user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="bf6dd-140">사용자 이름에는 다음 문자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-140">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="bf6dd-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="bf6dd-141">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

<span data-ttu-id="bf6dd-142">사용자 이름은 마침표 나 공백으로만 구성 될 수 없습니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="bf6dd-142">A user name cannot consist only of periods `.` or spaces.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-143">-NoPassword</span><span class="sxs-lookup"><span data-stu-id="bf6dd-143">-NoPassword</span></span>

<span data-ttu-id="bf6dd-144">사용자 계정에 암호가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-144">Indicates that the user account does not have a password.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoPassword
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-145">-Password</span><span class="sxs-lookup"><span data-stu-id="bf6dd-145">-Password</span></span>

<span data-ttu-id="bf6dd-146">사용자 계정에 대 한 암호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-146">Specifies a password for the user account.</span></span> <span data-ttu-id="bf6dd-147">`Read-Host -GetCredential`, 또는를 사용 `Get-Credential` 하 여 `ConvertTo-SecureString` 암호에 대 한 **SecureString** 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-147">You can use `Read-Host -GetCredential`, `Get-Credential`, or `ConvertTo-SecureString` to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="bf6dd-148">**Password** 및 **nopassword** 매개 변수를 생략 하면에서 `New-LocalUser` 새 사용자의 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-148">If you omit the **Password** and **NoPassword** parameters, `New-LocalUser` prompts you for the new user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: Password
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-149">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="bf6dd-149">-PasswordNeverExpires</span></span>

<span data-ttu-id="bf6dd-150">암호가 만료 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-150">Indicates whether the password expires.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Password
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-151">-UserMayNotChangePassword</span><span class="sxs-lookup"><span data-stu-id="bf6dd-151">-UserMayNotChangePassword</span></span>

<span data-ttu-id="bf6dd-152">사용자가 사용자 계정에 대 한 암호를 변경할 수 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-152">Indicates that the user cannot change the password on the user account.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bf6dd-153">-Confirm</span></span>

<span data-ttu-id="bf6dd-154">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-154">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bf6dd-155">-WhatIf</span></span>

<span data-ttu-id="bf6dd-156">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="bf6dd-157">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-157">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bf6dd-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bf6dd-158">CommonParameters</span></span>

<span data-ttu-id="bf6dd-159">이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-159">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="bf6dd-160">자세한 내용은 [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-160">For more information, see [about_CommonParameters](/reference/6/Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="bf6dd-161">입력</span><span class="sxs-lookup"><span data-stu-id="bf6dd-161">INPUTS</span></span>

### <span data-ttu-id="bf6dd-162">System.string, System.string, System.string, System.web. SecureString</span><span class="sxs-lookup"><span data-stu-id="bf6dd-162">System.String, System.DateTime, System.Boolean, System.Security.SecureString</span></span>

<span data-ttu-id="bf6dd-163">이 cmdlet에 문자열, **DateTime** 개체, 부울 값 또는 보안 문자열을 파이프 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-163">You can pipe a string, a **DateTime** object, a boolean value, or a secure string to this cmdlet.</span></span>

## <span data-ttu-id="bf6dd-164">출력</span><span class="sxs-lookup"><span data-stu-id="bf6dd-164">OUTPUTS</span></span>

### <span data-ttu-id="bf6dd-165">SecurityAccountsManager 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-165">System.Management.Automation.SecurityAccountsManager.LocalUser</span></span>

<span data-ttu-id="bf6dd-166">이 cmdlet은 **Localuser** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-166">This cmdlet returns a **LocalUser** object.</span></span>
<span data-ttu-id="bf6dd-167">이 개체는 사용자 계정에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-167">This object provides information about the user account.</span></span>

## <span data-ttu-id="bf6dd-168">참고</span><span class="sxs-lookup"><span data-stu-id="bf6dd-168">NOTES</span></span>

- <span data-ttu-id="bf6dd-169">사용자 이름은 컴퓨터의 다른 사용자 이름이 나 그룹 이름과 같을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-169">A user name cannot be identical to any other user name or group name on the computer.</span></span> <span data-ttu-id="bf6dd-170">사용자 이름은 마침표 나 공백으로만 구성 될 수 없습니다 `.` .</span><span class="sxs-lookup"><span data-stu-id="bf6dd-170">A user name cannot consist only of periods `.` or spaces.</span></span> <span data-ttu-id="bf6dd-171">사용자 이름에는 최대 20 자의 대문자 또는 소문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-171">A user name can contain up to 20 uppercase characters or lowercase characters.</span></span> <span data-ttu-id="bf6dd-172">사용자 이름에는 다음 문자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-172">A user name cannot contain the following characters:</span></span>

<span data-ttu-id="bf6dd-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span><span class="sxs-lookup"><span data-stu-id="bf6dd-173">`"`, `/`, `\`, `[`, `]`, `:`, `;`, `|`, `=`, `,`, `+`, `*`, `?`, `<`, `>`, `@`</span></span>

- <span data-ttu-id="bf6dd-174">암호에는 최대 127 자까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-174">A password can contain up to 127 characters.</span></span>
- <span data-ttu-id="bf6dd-175">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-175">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="bf6dd-176">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-176">The possible sources are as follows:</span></span>

  - <span data-ttu-id="bf6dd-177">로컬</span><span class="sxs-lookup"><span data-stu-id="bf6dd-177">Local</span></span>
  - <span data-ttu-id="bf6dd-178">Active Directory</span><span class="sxs-lookup"><span data-stu-id="bf6dd-178">Active Directory</span></span>
  - <span data-ttu-id="bf6dd-179">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="bf6dd-179">Azure Active Directory group</span></span>
  - <span data-ttu-id="bf6dd-180">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="bf6dd-180">Microsoft Account</span></span>

> [!NOTE]
> <span data-ttu-id="bf6dd-181">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-181">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="bf6dd-182">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf6dd-182">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="bf6dd-183">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bf6dd-183">RELATED LINKS</span></span>

[<span data-ttu-id="bf6dd-184">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-184">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="bf6dd-185">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-185">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="bf6dd-186">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-186">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="bf6dd-187">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-187">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="bf6dd-188">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-188">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="bf6dd-189">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="bf6dd-189">Set-LocalUser</span></span>](Set-LocalUser.md)
