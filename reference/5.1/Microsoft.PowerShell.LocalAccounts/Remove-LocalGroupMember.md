---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroupMember
ms.openlocfilehash: 6e6264a65c343657c2f2f87384d76cc3f1554d3d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214681"
---
# <span data-ttu-id="23614-103">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="23614-103">Remove-LocalGroupMember</span></span>

## <span data-ttu-id="23614-104">개요</span><span class="sxs-lookup"><span data-stu-id="23614-104">SYNOPSIS</span></span>
<span data-ttu-id="23614-105">로컬 그룹에서 구성원을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-105">Removes members from a local group.</span></span>

## <span data-ttu-id="23614-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23614-106">SYNTAX</span></span>

### <span data-ttu-id="23614-107">그룹</span><span class="sxs-lookup"><span data-stu-id="23614-107">Group</span></span>

```
Remove-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="23614-108">기본값</span><span class="sxs-lookup"><span data-stu-id="23614-108">Default</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="23614-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="23614-109">SecurityIdentifier</span></span>

```
Remove-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="23614-110">설명</span><span class="sxs-lookup"><span data-stu-id="23614-110">DESCRIPTION</span></span>
<span data-ttu-id="23614-111">**Remove LocalGroupMember** cmdlet은 로컬 그룹에서 사용자 또는 그룹을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-111">The **Remove-LocalGroupMember** cmdlet removes users or groups from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="23614-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="23614-113">예제</span><span class="sxs-lookup"><span data-stu-id="23614-113">EXAMPLES</span></span>

### <span data-ttu-id="23614-114">예제 1: Administrators 그룹에서 구성원 제거</span><span class="sxs-lookup"><span data-stu-id="23614-114">Example 1: Remove members from the Administrators group</span></span>

```
PS C:\> Remove-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

<span data-ttu-id="23614-115">이 명령은 로컬 관리자 그룹에서 여러 멤버를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-115">This command removes several members from the local Administrators group.</span></span>
<span data-ttu-id="23614-116">이 cmdlet이 제거 하는 구성원에는 로컬 사용자 계정, Microsoft 계정, Azure Active Directory 계정 및 도메인 그룹이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23614-116">The members that this cmdlet removes include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span>
<span data-ttu-id="23614-117">이 예제에서는 Outlook.com에서 계정의 사용자 이름에 자리 표시자 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-117">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

## <span data-ttu-id="23614-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="23614-118">PARAMETERS</span></span>

### <span data-ttu-id="23614-119">-그룹</span><span class="sxs-lookup"><span data-stu-id="23614-119">-Group</span></span>
<span data-ttu-id="23614-120">이 cmdlet이 구성원을 제거 하는 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-120">Specifies the security group from which this cmdlet removes members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23614-121">-Member</span><span class="sxs-lookup"><span data-stu-id="23614-121">-Member</span></span>
<span data-ttu-id="23614-122">이 cmdlet이 보안 그룹에서 제거 하는 사용자 또는 그룹의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-122">Specifies an array of users or groups that this cmdlet removes from a security group.</span></span>
<span data-ttu-id="23614-123">이름, SID (보안 ID) 또는 **Localprincipal** 개체를 기준으로 사용자 또는 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-123">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>
<span data-ttu-id="23614-124">S-R-I-s-s에서 SID 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-124">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="23614-125">.</span><span class="sxs-lookup"><span data-stu-id="23614-125">.</span></span> <span data-ttu-id="23614-126">.</span><span class="sxs-lookup"><span data-stu-id="23614-126">.</span></span>
<span data-ttu-id="23614-127">형식.</span><span class="sxs-lookup"><span data-stu-id="23614-127">format.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalPrincipal[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="23614-128">-Name</span><span class="sxs-lookup"><span data-stu-id="23614-128">-Name</span></span>
<span data-ttu-id="23614-129">이 cmdlet이 구성원을 제거 하는 보안 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-129">Specifies the name of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23614-130">-SID</span><span class="sxs-lookup"><span data-stu-id="23614-130">-SID</span></span>
<span data-ttu-id="23614-131">이 cmdlet이 구성원을 제거 하는 보안 그룹의 보안 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-131">Specifies the security ID of the security group from which this cmdlet removes members.</span></span>

```yaml
Type: System.Security.Principal.SecurityIdentifier
Parameter Sets: SecurityIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="23614-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="23614-132">-Confirm</span></span>
<span data-ttu-id="23614-133">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="23614-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="23614-134">-WhatIf</span></span>
<span data-ttu-id="23614-135">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="23614-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="23614-136">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="23614-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23614-137">CommonParameters</span></span>
<span data-ttu-id="23614-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23614-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23614-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="23614-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="23614-140">입력</span><span class="sxs-lookup"><span data-stu-id="23614-140">INPUTS</span></span>

### <span data-ttu-id="23614-141">SecurityAccountsManager, SecurityIdentifier, system.web. 사용자. m a.. m a.</span><span class="sxs-lookup"><span data-stu-id="23614-141">System.Management.Automation.SecurityAccountsManager.LocalPrincipal, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="23614-142">로컬 보안 주체, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="23614-143">출력</span><span class="sxs-lookup"><span data-stu-id="23614-143">OUTPUTS</span></span>

### <span data-ttu-id="23614-144">없음</span><span class="sxs-lookup"><span data-stu-id="23614-144">None</span></span>
<span data-ttu-id="23614-145">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="23614-146">참고</span><span class="sxs-lookup"><span data-stu-id="23614-146">NOTES</span></span>

* <span data-ttu-id="23614-147">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="23614-147">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="23614-148">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-148">The possible sources are as follows:</span></span>

- <span data-ttu-id="23614-149">로컬</span><span class="sxs-lookup"><span data-stu-id="23614-149">Local</span></span>
- <span data-ttu-id="23614-150">Active Directory</span><span class="sxs-lookup"><span data-stu-id="23614-150">Active Directory</span></span>
- <span data-ttu-id="23614-151">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="23614-151">Azure Active Directory group</span></span>
- <span data-ttu-id="23614-152">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="23614-152">Microsoft Account</span></span>

<span data-ttu-id="23614-153">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23614-153">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="23614-154">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23614-154">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="23614-155">관련 링크</span><span class="sxs-lookup"><span data-stu-id="23614-155">RELATED LINKS</span></span>

[<span data-ttu-id="23614-156">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="23614-156">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="23614-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="23614-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="23614-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="23614-158">New-LocalGroup</span></span>](New-LocalGroup.md)
