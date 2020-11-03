---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localuser?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalUser
ms.openlocfilehash: de1054971dab19f8cfae654208488ca9ce5e17e4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215634"
---
# <span data-ttu-id="7b9d3-103">Remove-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-103">Remove-LocalUser</span></span>

## <span data-ttu-id="7b9d3-104">개요</span><span class="sxs-lookup"><span data-stu-id="7b9d3-104">SYNOPSIS</span></span>
<span data-ttu-id="7b9d3-105">로컬 사용자 계정을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-105">Deletes local user accounts.</span></span>

## <span data-ttu-id="7b9d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7b9d3-106">SYNTAX</span></span>

### <span data-ttu-id="7b9d3-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="7b9d3-107">InputObject</span></span>

```
Remove-LocalUser [-InputObject] <LocalUser[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7b9d3-108">기본값</span><span class="sxs-lookup"><span data-stu-id="7b9d3-108">Default</span></span>

```
Remove-LocalUser [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7b9d3-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7b9d3-109">SecurityIdentifier</span></span>

```
Remove-LocalUser [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7b9d3-110">설명</span><span class="sxs-lookup"><span data-stu-id="7b9d3-110">DESCRIPTION</span></span>
<span data-ttu-id="7b9d3-111">**Remove localuser** cmdlet은 로컬 사용자 계정을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-111">The **Remove-LocalUser** cmdlet deletes local user accounts.</span></span>

## <span data-ttu-id="7b9d3-112">예제</span><span class="sxs-lookup"><span data-stu-id="7b9d3-112">EXAMPLES</span></span>

### <span data-ttu-id="7b9d3-113">예제 1: 사용자 계정 삭제</span><span class="sxs-lookup"><span data-stu-id="7b9d3-113">Example 1: Delete a user account</span></span>

```
PS C:\> Remove-LocalUser -Name "AdminContoso02"
```

<span data-ttu-id="7b9d3-114">이 명령은 AdminContoso02 이라는 사용자 계정을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-114">This command deletes the user account named AdminContoso02.</span></span>

> [!NOTE]
> <span data-ttu-id="7b9d3-115">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="7b9d3-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7b9d3-116">PARAMETERS</span></span>

### <span data-ttu-id="7b9d3-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7b9d3-117">-InputObject</span></span>
<span data-ttu-id="7b9d3-118">이 cmdlet이 삭제 하는 사용자 계정의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-118">Specifies an array of user accounts that this cmdlet deletes.</span></span>
<span data-ttu-id="7b9d3-119">사용자 계정을 가져오려면 Get-LocalUser cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-119">To obtain a user account, use the Get-LocalUser cmdlet.</span></span>

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

### <span data-ttu-id="7b9d3-120">-Name</span><span class="sxs-lookup"><span data-stu-id="7b9d3-120">-Name</span></span>
<span data-ttu-id="7b9d3-121">이 cmdlet이 삭제 하는 사용자 계정의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-121">Specifies an array of names of the user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="7b9d3-122">-SID</span><span class="sxs-lookup"><span data-stu-id="7b9d3-122">-SID</span></span>
<span data-ttu-id="7b9d3-123">이 cmdlet이 삭제 하는 사용자 계정의 Sid (보안 Id) 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-123">Specifies an array of security IDs (SIDs) of user accounts that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="7b9d3-124">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7b9d3-124">-Confirm</span></span>
<span data-ttu-id="7b9d3-125">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-125">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7b9d3-126">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7b9d3-126">-WhatIf</span></span>
<span data-ttu-id="7b9d3-127">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-127">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7b9d3-128">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-128">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7b9d3-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7b9d3-129">CommonParameters</span></span>
<span data-ttu-id="7b9d3-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7b9d3-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7b9d3-132">입력</span><span class="sxs-lookup"><span data-stu-id="7b9d3-132">INPUTS</span></span>

### <span data-ttu-id="7b9d3-133">SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. n a m l.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-133">System.Management.Automation.SecurityAccountsManager.LocalUser, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="7b9d3-134">로컬 사용자, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-134">You can pipe a local user, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="7b9d3-135">출력</span><span class="sxs-lookup"><span data-stu-id="7b9d3-135">OUTPUTS</span></span>

### <span data-ttu-id="7b9d3-136">없음</span><span class="sxs-lookup"><span data-stu-id="7b9d3-136">None</span></span>
<span data-ttu-id="7b9d3-137">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-137">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7b9d3-138">참고</span><span class="sxs-lookup"><span data-stu-id="7b9d3-138">NOTES</span></span>

* <span data-ttu-id="7b9d3-139">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-139">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="7b9d3-140">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-140">The possible sources are as follows:</span></span>

- <span data-ttu-id="7b9d3-141">로컬</span><span class="sxs-lookup"><span data-stu-id="7b9d3-141">Local</span></span>
- <span data-ttu-id="7b9d3-142">Active Directory</span><span class="sxs-lookup"><span data-stu-id="7b9d3-142">Active Directory</span></span>
- <span data-ttu-id="7b9d3-143">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="7b9d3-143">Azure Active Directory group</span></span>
- <span data-ttu-id="7b9d3-144">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="7b9d3-144">Microsoft Account</span></span>

<span data-ttu-id="7b9d3-145">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-145">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="7b9d3-146">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b9d3-146">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="7b9d3-147">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7b9d3-147">RELATED LINKS</span></span>

[<span data-ttu-id="7b9d3-148">Disable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-148">Disable-LocalUser</span></span>](Disable-LocalUser.md)

[<span data-ttu-id="7b9d3-149">Enable-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-149">Enable-LocalUser</span></span>](Enable-LocalUser.md)

[<span data-ttu-id="7b9d3-150">Get-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-150">Get-LocalUser</span></span>](Get-LocalUser.md)

[<span data-ttu-id="7b9d3-151">New-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-151">New-LocalUser</span></span>](New-LocalUser.md)

[<span data-ttu-id="7b9d3-152">Rename-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-152">Rename-LocalUser</span></span>](Rename-LocalUser.md)

[<span data-ttu-id="7b9d3-153">Set-LocalUser</span><span class="sxs-lookup"><span data-stu-id="7b9d3-153">Set-LocalUser</span></span>](Set-LocalUser.md)
