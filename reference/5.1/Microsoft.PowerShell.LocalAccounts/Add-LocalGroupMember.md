---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/add-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-LocalGroupMember
ms.openlocfilehash: 06993c8f6618472f4809e37fbf83d298d13ae515
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211929"
---
# <span data-ttu-id="a2d2b-103">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a2d2b-103">Add-LocalGroupMember</span></span>

## <span data-ttu-id="a2d2b-104">개요</span><span class="sxs-lookup"><span data-stu-id="a2d2b-104">SYNOPSIS</span></span>
<span data-ttu-id="a2d2b-105">로컬 그룹에 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-105">Adds members to a local group.</span></span>

## <span data-ttu-id="a2d2b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a2d2b-106">SYNTAX</span></span>

### <span data-ttu-id="a2d2b-107">그룹</span><span class="sxs-lookup"><span data-stu-id="a2d2b-107">Group</span></span>

```
Add-LocalGroupMember [-Group] <LocalGroup> [-Member] <LocalPrincipal[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="a2d2b-108">기본값</span><span class="sxs-lookup"><span data-stu-id="a2d2b-108">Default</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a2d2b-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="a2d2b-109">SecurityIdentifier</span></span>

```
Add-LocalGroupMember [-Member] <LocalPrincipal[]> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a2d2b-110">설명</span><span class="sxs-lookup"><span data-stu-id="a2d2b-110">DESCRIPTION</span></span>

<span data-ttu-id="a2d2b-111">`Add-LocalGroupMember`Cmdlet은 로컬 보안 그룹에 사용자 또는 그룹을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-111">The `Add-LocalGroupMember` cmdlet adds users or groups to a local security group.</span></span> <span data-ttu-id="a2d2b-112">그룹에 할당된 권리와 사용 권한은 모두 해당 그룹의 구성원 전체에게 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-112">All the rights and permissions that are assigned to a group are assigned to all members of that group.</span></span>

<span data-ttu-id="a2d2b-113">로컬 컴퓨터의 Administrators 그룹 구성원은 해당 컴퓨터에 대한 모든 권한을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-113">Members of the Administrators group on a local computer have Full Control permissions on that computer.</span></span> <span data-ttu-id="a2d2b-114">Administrators 그룹의 사용자 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-114">Limit the number of users in the Administrators group.</span></span>

<span data-ttu-id="a2d2b-115">컴퓨터가 도메인에 가입되어 있는 경우에는 해당 도메인과 트러스트된 도메인의 사용자 계정, 컴퓨터 계정 및 그룹 계정을 로컬 그룹에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-115">If the computer is joined to a domain, you can add user accounts, computer accounts, and group accounts from that domain and from trusted domains to a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="a2d2b-116">컴퓨터가 도메인에 가입 되어 있는 경우 도메인의 구성원과 이름이 같은 로컬 사용자를 추가 하려고 하면 도메인 구성원이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-116">If the computer is joined to a domain and you try to add a local user that has the same name as a member of the domain it adds the domain member.</span></span>

## <span data-ttu-id="a2d2b-117">예제</span><span class="sxs-lookup"><span data-stu-id="a2d2b-117">EXAMPLES</span></span>

### <span data-ttu-id="a2d2b-118">예제 1: Administrators 그룹에 멤버 추가</span><span class="sxs-lookup"><span data-stu-id="a2d2b-118">Example 1: Add members to the Administrators group</span></span>

<span data-ttu-id="a2d2b-119">이 명령은 로컬 Administrators 그룹에 여러 개의 멤버를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-119">This command adds several members to the local Administrators group.</span></span> <span data-ttu-id="a2d2b-120">새 구성원에는 로컬 사용자 계정, Microsoft 계정, Azure Active Directory 계정 및 도메인 그룹이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-120">The new members include a local user account, a Microsoft account, an Azure Active Directory account, and a domain group.</span></span> <span data-ttu-id="a2d2b-121">이 예제에서는 Outlook.com에서 계정의 사용자 이름에 자리 표시자 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-121">This example uses a placeholder value for the user name of an account at Outlook.com.</span></span>

```powershell
Add-LocalGroupMember -Group "Administrators" -Member "Admin02", "MicrosoftAccount\username@Outlook.com", "AzureAD\DavidChew@contoso.com", "CONTOSO\Domain Admins"
```

## <span data-ttu-id="a2d2b-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a2d2b-122">PARAMETERS</span></span>

### <span data-ttu-id="a2d2b-123">-그룹</span><span class="sxs-lookup"><span data-stu-id="a2d2b-123">-Group</span></span>

<span data-ttu-id="a2d2b-124">이 cmdlet이 구성원을 추가할 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-124">Specifies the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a2d2b-125">-Member</span><span class="sxs-lookup"><span data-stu-id="a2d2b-125">-Member</span></span>

<span data-ttu-id="a2d2b-126">이 cmdlet이 보안 그룹에 추가 하는 사용자 또는 그룹의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-126">Specifies an array of users or groups that this cmdlet adds to a security group.</span></span> <span data-ttu-id="a2d2b-127">이름, SID (보안 ID) 또는 **Localprincipal** 개체를 기준으로 사용자 또는 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-127">You can specify users or groups by name, security ID (SID), or **LocalPrincipal** objects.</span></span>

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

### <span data-ttu-id="a2d2b-128">-Name</span><span class="sxs-lookup"><span data-stu-id="a2d2b-128">-Name</span></span>

<span data-ttu-id="a2d2b-129">이 cmdlet이 멤버를 추가 하는 보안 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-129">Specifies the name of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a2d2b-130">-SID</span><span class="sxs-lookup"><span data-stu-id="a2d2b-130">-SID</span></span>

<span data-ttu-id="a2d2b-131">이 cmdlet이 멤버를 추가 하는 보안 그룹의 보안 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-131">Specifies the security ID of the security group to which this cmdlet adds members.</span></span>

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

### <span data-ttu-id="a2d2b-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a2d2b-132">-Confirm</span></span>

<span data-ttu-id="a2d2b-133">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a2d2b-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a2d2b-134">-WhatIf</span></span>

<span data-ttu-id="a2d2b-135">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-135">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a2d2b-136">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a2d2b-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2d2b-137">CommonParameters</span></span>

<span data-ttu-id="a2d2b-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a2d2b-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a2d2b-140">입력</span><span class="sxs-lookup"><span data-stu-id="a2d2b-140">INPUTS</span></span>

### <span data-ttu-id="a2d2b-141">SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-141">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>

<span data-ttu-id="a2d2b-142">로컬 보안 주체, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-142">You can pipe a local principal, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="a2d2b-143">출력</span><span class="sxs-lookup"><span data-stu-id="a2d2b-143">OUTPUTS</span></span>

### <span data-ttu-id="a2d2b-144">없음</span><span class="sxs-lookup"><span data-stu-id="a2d2b-144">None</span></span>

<span data-ttu-id="a2d2b-145">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-145">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a2d2b-146">참고</span><span class="sxs-lookup"><span data-stu-id="a2d2b-146">NOTES</span></span>

<span data-ttu-id="a2d2b-147">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-147">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

<span data-ttu-id="a2d2b-148">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-148">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="a2d2b-149">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-149">The possible sources are as follows:</span></span>

- <span data-ttu-id="a2d2b-150">로컬</span><span class="sxs-lookup"><span data-stu-id="a2d2b-150">Local</span></span>
- <span data-ttu-id="a2d2b-151">Active Directory</span><span class="sxs-lookup"><span data-stu-id="a2d2b-151">Active Directory</span></span>
- <span data-ttu-id="a2d2b-152">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="a2d2b-152">Azure Active Directory group</span></span>
- <span data-ttu-id="a2d2b-153">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="a2d2b-153">Microsoft Account</span></span>

<span data-ttu-id="a2d2b-154">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-154">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="a2d2b-155">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2d2b-155">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="a2d2b-156">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a2d2b-156">RELATED LINKS</span></span>

[<span data-ttu-id="a2d2b-157">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a2d2b-157">Get-LocalGroupMember</span></span>](Get-LocalGroupMember.md)

[<span data-ttu-id="a2d2b-158">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="a2d2b-158">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="a2d2b-159">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a2d2b-159">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
