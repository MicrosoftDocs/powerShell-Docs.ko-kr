---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/enable-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-LocalUser
ms.openlocfilehash: 80d062578e7114b69e5cb5f3367b56da3871b9df
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211914"
---
# <span data-ttu-id="4191a-103">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-103">Enable-LocalUser</span></span>

## <span data-ttu-id="4191a-104">개요</span><span class="sxs-lookup"><span data-stu-id="4191a-104">SYNOPSIS</span></span>
<span data-ttu-id="4191a-105">로컬 사용자 계정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-105">Enables a local user account.</span></span>

## <span data-ttu-id="4191a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4191a-106">SYNTAX</span></span>

### <span data-ttu-id="4191a-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="4191a-107">InputObject</span></span>

```
Enable-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4191a-108">기본값</span><span class="sxs-lookup"><span data-stu-id="4191a-108">Default</span></span>

```
Enable-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4191a-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="4191a-109">SecurityIdentifier</span></span>

```
Enable-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4191a-110">설명</span><span class="sxs-lookup"><span data-stu-id="4191a-110">DESCRIPTION</span></span>
<span data-ttu-id="4191a-111">**Localuser** cmdlet은 로컬 사용자 계정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-111">The **Enable-LocalUser** cmdlet enables local user accounts.</span></span>
<span data-ttu-id="4191a-112">사용자 계정이 사용 하지 않도록 설정 된 경우 사용자가 로그온 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-112">When a user account is disabled, the user cannot log on.</span></span>
<span data-ttu-id="4191a-113">사용자 계정을 사용 하도록 설정 하면 사용자가 로그온 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-113">When a user account is enabled, the user can log on.</span></span>

> [!NOTE]
> <span data-ttu-id="4191a-114">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-114">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="4191a-115">예제</span><span class="sxs-lookup"><span data-stu-id="4191a-115">EXAMPLES</span></span>

### <span data-ttu-id="4191a-116">예제 1: 이름을 지정 하 여 계정 설정</span><span class="sxs-lookup"><span data-stu-id="4191a-116">Example 1: Enable an account by specifying a name</span></span>

```
PS C:\> Enable-LocalUser -Name "Admin02"
```

<span data-ttu-id="4191a-117">이 명령은 Admin02 이라는 사용자 계정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-117">This command enables the user account named Admin02.</span></span>

### <span data-ttu-id="4191a-118">예제 2: 파이프라인을 사용 하 여 계정 설정</span><span class="sxs-lookup"><span data-stu-id="4191a-118">Example 2: Enable an account by using the pipeline</span></span>

```
PS C:\> Get-LocalUser -Name "Administrator" | Enable-LocalUser
```

<span data-ttu-id="4191a-119">이 명령은 **LocalUser** 를 사용 하 여 기본 제공 관리자 계정을 가져온 다음 파이프라인 연산자를 사용 하 여 현재 cmdlet으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-119">This command gets the built-in Administrator account by using **Get-LocalUser** , and then passes it to the current cmdlet by using the pipeline operator.</span></span>
<span data-ttu-id="4191a-120">이 cmdlet은 해당 계정을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-120">That cmdlet enables that account.</span></span>

## <span data-ttu-id="4191a-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4191a-121">PARAMETERS</span></span>

### <span data-ttu-id="4191a-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="4191a-122">-InputObject</span></span>
<span data-ttu-id="4191a-123">이 cmdlet이 사용할 수 있는 사용자 계정의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-123">Specifies an array of user accounts that this cmdlet enables.</span></span>
<span data-ttu-id="4191a-124">사용자 계정을 가져오려면 Get-LocalUser cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-124">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalUser[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4191a-125">-Name</span><span class="sxs-lookup"><span data-stu-id="4191a-125">-Name</span></span>
<span data-ttu-id="4191a-126">이 cmdlet이 사용 하는 사용자 계정의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-126">Specifies an array of names of the user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4191a-127">-SID</span><span class="sxs-lookup"><span data-stu-id="4191a-127">-SID</span></span>
<span data-ttu-id="4191a-128">이 cmdlet이 사용할 수 있는 사용자 계정의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-128">Specifies an array of user accounts that this cmdlet enables.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier[]
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="4191a-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4191a-129">-Confirm</span></span>
<span data-ttu-id="4191a-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4191a-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4191a-131">-WhatIf</span></span>
<span data-ttu-id="4191a-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4191a-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4191a-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4191a-134">CommonParameters</span></span>
<span data-ttu-id="4191a-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4191a-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4191a-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4191a-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4191a-137">입력</span><span class="sxs-lookup"><span data-stu-id="4191a-137">INPUTS</span></span>

### <span data-ttu-id="4191a-138">SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. n a m l.</span><span class="sxs-lookup"><span data-stu-id="4191a-138">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="4191a-139">로컬 사용자, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-139">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="4191a-140">출력</span><span class="sxs-lookup"><span data-stu-id="4191a-140">OUTPUTS</span></span>

### <span data-ttu-id="4191a-141">없음</span><span class="sxs-lookup"><span data-stu-id="4191a-141">None</span></span>
<span data-ttu-id="4191a-142">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4191a-143">참고</span><span class="sxs-lookup"><span data-stu-id="4191a-143">NOTES</span></span>

* <span data-ttu-id="4191a-144">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-144">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="4191a-145">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-145">The possible sources are as follows:</span></span>

- <span data-ttu-id="4191a-146">로컬</span><span class="sxs-lookup"><span data-stu-id="4191a-146">Local</span></span>
- <span data-ttu-id="4191a-147">Active Directory</span><span class="sxs-lookup"><span data-stu-id="4191a-147">Active Directory</span></span>
- <span data-ttu-id="4191a-148">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="4191a-148">Azure Active Directory group</span></span>
- <span data-ttu-id="4191a-149">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="4191a-149">Microsoft Account</span></span>

<span data-ttu-id="4191a-150">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-150">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="4191a-151">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4191a-151">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="4191a-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4191a-152">RELATED LINKS</span></span>

[<span data-ttu-id="4191a-153">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-153">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="4191a-154">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-154">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="4191a-155">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-155">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="4191a-156">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-156">Remove-LocalUser</span></span>](Remove-LocalUser.md)

[<span data-ttu-id="4191a-157">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-157">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="4191a-158">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="4191a-158">Set-LocalUser</span></span>](Set-LocalUser.md)
