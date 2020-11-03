---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalUser
ms.openlocfilehash: a6352611b757dae828a2efef07f9ce65abaa5e2e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215617"
---
# <span data-ttu-id="ce74c-103">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-103">Set-LocalUser</span></span>

## <span data-ttu-id="ce74c-104">개요</span><span class="sxs-lookup"><span data-stu-id="ce74c-104">SYNOPSIS</span></span>
<span data-ttu-id="ce74c-105">로컬 사용자 계정을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-105">Modifies a local user account.</span></span>

## <span data-ttu-id="ce74c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ce74c-106">SYNTAX</span></span>

### <span data-ttu-id="ce74c-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="ce74c-107">Name (Default)</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Name] <String> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ce74c-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="ce74c-108">InputObject</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-InputObject] <LocalUser> [-Password <SecureString>] [-PasswordNeverExpires <Boolean>]
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ce74c-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="ce74c-109">SecurityIdentifier</span></span>

```
Set-LocalUser [-AccountExpires <DateTime>] [-AccountNeverExpires] [-Description <String>] [-FullName <String>]
 [-Password <SecureString>] [-PasswordNeverExpires <Boolean>] [-SID] <SecurityIdentifier>
 [-UserMayChangePassword <Boolean>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ce74c-110">설명</span><span class="sxs-lookup"><span data-stu-id="ce74c-110">DESCRIPTION</span></span>
<span data-ttu-id="ce74c-111">**Set localuser** cmdlet은 로컬 사용자 계정을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-111">The **Set-LocalUser** cmdlet modifies a local user account.</span></span>
<span data-ttu-id="ce74c-112">이 cmdlet은 로컬 사용자 계정의 암호를 다시 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-112">This cmdlet can reset the password of a local user account.</span></span>

> [!NOTE]
> <span data-ttu-id="ce74c-113">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-113">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="ce74c-114">예제</span><span class="sxs-lookup"><span data-stu-id="ce74c-114">EXAMPLES</span></span>

### <span data-ttu-id="ce74c-115">예제 1: 사용자 계정에 대 한 설명 변경</span><span class="sxs-lookup"><span data-stu-id="ce74c-115">Example 1: Change a description of a user account</span></span>

```
PS C:\> Set-LocalUser -Name "Admin07" -Description "Description of this account."
```

<span data-ttu-id="ce74c-116">이 명령은 Admin07 이라는 사용자 계정에 대 한 설명을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-116">This command changes the description of a user account named Admin07.</span></span>

### <span data-ttu-id="ce74c-117">예 2: 계정에 대 한 암호 변경</span><span class="sxs-lookup"><span data-stu-id="ce74c-117">Example 2: Change the password on an account</span></span>

```
PS C:\> $Password = Read-Host -AsSecureString
PS C:\> $UserAccount = Get-LocalUser -Name "User02"
PS C:\> $UserAccount | Set-LocalUser -Password $Password
```

<span data-ttu-id="ce74c-118">첫 번째 명령은 Read-Host cmdlet을 사용 하 여 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-118">The first command prompts you for a password by using the Read-Host cmdlet.</span></span>
<span data-ttu-id="ce74c-119">명령은 암호를 $Password 변수에 보안 문자열로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-119">The command stores the password as a secure string in the $Password variable.</span></span>

<span data-ttu-id="ce74c-120">두 번째 명령은 User02 **사용자** 를 사용 하 여 이름이 인 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-120">The second command gets a user account named User02 by using **Get-LocalUser** .</span></span>
<span data-ttu-id="ce74c-121">이 명령은 $UserAccount 변수에 계정을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-121">The command stores the account in the $UserAccount variable.</span></span>

<span data-ttu-id="ce74c-122">세 번째 명령은 $UserAccount에 저장 된 사용자 계정에 새 암호를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-122">The third command sets the new password on the user account stored in $UserAccount.</span></span>

## <span data-ttu-id="ce74c-123">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ce74c-123">PARAMETERS</span></span>

### <span data-ttu-id="ce74c-124">-AccountExpires</span><span class="sxs-lookup"><span data-stu-id="ce74c-124">-AccountExpires</span></span>
<span data-ttu-id="ce74c-125">사용자 계정이 만료 되는 시점을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-125">Specifies when the user account expires.</span></span>
<span data-ttu-id="ce74c-126">**DateTime** 개체를 가져오려면 Get-Date cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-126">To obtain a **DateTime** object, use the Get-Date cmdlet.</span></span>

<span data-ttu-id="ce74c-127">계정이 만료 되지 않도록 하려면 *AccountNeverExpires* 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-127">If you do not want the account to expire, specify the *AccountNeverExpires* parameter.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-128">-AccountNeverExpires</span><span class="sxs-lookup"><span data-stu-id="ce74c-128">-AccountNeverExpires</span></span>
<span data-ttu-id="ce74c-129">계정이 만료 되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-129">Indicates that the account does not expire.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-130">-Description</span><span class="sxs-lookup"><span data-stu-id="ce74c-130">-Description</span></span>
<span data-ttu-id="ce74c-131">사용자 계정에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-131">Specifies a comment for the user account.</span></span>
<span data-ttu-id="ce74c-132">최대 길이는 48 자입니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-132">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-133">-FullName</span><span class="sxs-lookup"><span data-stu-id="ce74c-133">-FullName</span></span>
<span data-ttu-id="ce74c-134">사용자 계정의 전체 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-134">Specifies the full name for the user account.</span></span>
<span data-ttu-id="ce74c-135">전체 이름이 사용자 계정의 사용자 이름과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-135">The full name differs from the user name of the user account.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-136">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ce74c-136">-InputObject</span></span>
<span data-ttu-id="ce74c-137">이 cmdlet이 변경 되는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-137">Specifies the user account that this cmdlet changes.</span></span>
<span data-ttu-id="ce74c-138">사용자 계정을 가져오려면 Get-LocalUser cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-138">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-139">-Name</span><span class="sxs-lookup"><span data-stu-id="ce74c-139">-Name</span></span>
<span data-ttu-id="ce74c-140">이 cmdlet이 변경 되는 사용자 계정의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-140">Specifies the name of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-141">-Password</span><span class="sxs-lookup"><span data-stu-id="ce74c-141">-Password</span></span>
<span data-ttu-id="ce74c-142">사용자 계정에 대 한 암호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-142">Specifies a password for the user account.</span></span>
<span data-ttu-id="ce74c-143">사용자 계정이 Microsoft 계정에 연결 된 경우 암호를 설정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="ce74c-143">If the user account is connected to a Microsoft account, do not set a password.</span></span>

<span data-ttu-id="ce74c-144">`Read-Host -GetCredential`, Get Credential 또는 ConvertTo-SecureString를 사용 하 여 암호에 대 한 **SecureString** 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-144">You can use `Read-Host -GetCredential`, Get-Credential, or ConvertTo-SecureString to create a **SecureString** object for the password.</span></span>

<span data-ttu-id="ce74c-145">*Password* 및 *nopassword* 매개 변수를 생략 하면 **설정-localuser** 사용자의 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-145">If you omit the *Password* and *NoPassword* parameters, **Set-LocalUser** prompts you for the user's password.</span></span>

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-146">-PasswordNeverExpires</span><span class="sxs-lookup"><span data-stu-id="ce74c-146">-PasswordNeverExpires</span></span>
<span data-ttu-id="ce74c-147">암호가 만료 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-147">Indicates whether the password expires.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-148">-SID</span><span class="sxs-lookup"><span data-stu-id="ce74c-148">-SID</span></span>
<span data-ttu-id="ce74c-149">이 cmdlet이 변경 되는 사용자 계정의 SID (보안 ID)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-149">Specifies the security ID (SID) of the user account that this cmdlet changes.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-150">-UserMayChangePassword</span><span class="sxs-lookup"><span data-stu-id="ce74c-150">-UserMayChangePassword</span></span>
<span data-ttu-id="ce74c-151">사용자가 사용자 계정에 대 한 암호를 변경할 수 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-151">Indicates that the user can change the password on the user account.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce74c-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ce74c-152">-Confirm</span></span>
<span data-ttu-id="ce74c-153">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ce74c-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ce74c-154">-WhatIf</span></span>
<span data-ttu-id="ce74c-155">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-155">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ce74c-156">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ce74c-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce74c-157">CommonParameters</span></span>
<span data-ttu-id="ce74c-158">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce74c-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce74c-159">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce74c-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ce74c-160">입력</span><span class="sxs-lookup"><span data-stu-id="ce74c-160">INPUTS</span></span>

### <span data-ttu-id="ce74c-161">SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. n a m l.</span><span class="sxs-lookup"><span data-stu-id="ce74c-161">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="ce74c-162">로컬 사용자, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-162">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="ce74c-163">출력</span><span class="sxs-lookup"><span data-stu-id="ce74c-163">OUTPUTS</span></span>

### <span data-ttu-id="ce74c-164">없음</span><span class="sxs-lookup"><span data-stu-id="ce74c-164">None</span></span>
<span data-ttu-id="ce74c-165">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-165">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ce74c-166">참고</span><span class="sxs-lookup"><span data-stu-id="ce74c-166">NOTES</span></span>

* <span data-ttu-id="ce74c-167">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-167">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="ce74c-168">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-168">The possible sources are as follows:</span></span>

- <span data-ttu-id="ce74c-169">로컬</span><span class="sxs-lookup"><span data-stu-id="ce74c-169">Local</span></span>
- <span data-ttu-id="ce74c-170">Active Directory</span><span class="sxs-lookup"><span data-stu-id="ce74c-170">Active Directory</span></span>
- <span data-ttu-id="ce74c-171">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="ce74c-171">Azure Active Directory group</span></span>
- <span data-ttu-id="ce74c-172">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="ce74c-172">Microsoft Account</span></span>

<span data-ttu-id="ce74c-173">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-173">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="ce74c-174">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce74c-174">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="ce74c-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ce74c-175">RELATED LINKS</span></span>

[<span data-ttu-id="ce74c-176">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-176">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="ce74c-177">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-177">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="ce74c-178">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-178">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="ce74c-179">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-179">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="ce74c-180">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-180">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="ce74c-181">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="ce74c-181">Rename-LocalUser</span></span>](Rename-LocalUser.md)
