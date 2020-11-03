---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/remove-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-LocalGroup
ms.openlocfilehash: 6a2f921972fef1794581b301df6e7439e56c7f47
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214674"
---
# <span data-ttu-id="82128-103">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="82128-103">Remove-LocalGroup</span></span>

## <span data-ttu-id="82128-104">개요</span><span class="sxs-lookup"><span data-stu-id="82128-104">SYNOPSIS</span></span>
<span data-ttu-id="82128-105">로컬 보안 그룹을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-105">Deletes local security groups.</span></span>

## <span data-ttu-id="82128-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82128-106">SYNTAX</span></span>

### <span data-ttu-id="82128-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="82128-107">InputObject</span></span>

```
Remove-LocalGroup [-InputObject] <LocalGroup[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82128-108">기본값</span><span class="sxs-lookup"><span data-stu-id="82128-108">Default</span></span>

```
Remove-LocalGroup [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="82128-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="82128-109">SecurityIdentifier</span></span>

```
Remove-LocalGroup [-SID] <SecurityIdentifier[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="82128-110">설명</span><span class="sxs-lookup"><span data-stu-id="82128-110">DESCRIPTION</span></span>
<span data-ttu-id="82128-111">**LocalGroup** cmdlet은 로컬 보안 그룹을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-111">The **Remove-LocalGroup** cmdlet deletes local security groups.</span></span>
<span data-ttu-id="82128-112">이 cmdlet은 로컬 그룹만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-112">This cmdlet deletes only a local group.</span></span>
<span data-ttu-id="82128-113">해당 그룹에 속한 사용자 계정, 컴퓨터 계정 또는 그룹 계정은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-113">It does not delete the user accounts, computer accounts, or group accounts that belong to that group.</span></span>
<span data-ttu-id="82128-114">삭제 된 그룹은 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-114">You cannot recover a deleted group.</span></span>

<span data-ttu-id="82128-115">그룹을 삭제 하 고 그룹 이름이 같은 다른 그룹을 만든 경우 새 그룹에 대 한 새 권한을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-115">If you delete a group and then create another group that has the same group name, you must set new permissions for the new group.</span></span>
<span data-ttu-id="82128-116">새 그룹은 해당 그룹에 할당 된 사용 권한을 상속 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-116">The new group does not inherit the permissions that were assigned to the group.</span></span>

> [!NOTE]
> <span data-ttu-id="82128-117">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-117">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="82128-118">예제</span><span class="sxs-lookup"><span data-stu-id="82128-118">EXAMPLES</span></span>

### <span data-ttu-id="82128-119">예제 1: 보안 그룹 삭제</span><span class="sxs-lookup"><span data-stu-id="82128-119">Example 1: Delete a security group</span></span>

```
PS C:\> Remove-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="82128-120">이 명령은 SecurityGroup04 라는 그룹을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-120">This command deletes the group named SecurityGroup04.</span></span>

## <span data-ttu-id="82128-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82128-121">PARAMETERS</span></span>

### <span data-ttu-id="82128-122">-InputObject</span><span class="sxs-lookup"><span data-stu-id="82128-122">-InputObject</span></span>
<span data-ttu-id="82128-123">이 cmdlet이 삭제 하는 보안 그룹의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-123">Specifies an array of security groups that this cmdlet deletes.</span></span>
<span data-ttu-id="82128-124">그룹을 얻으려면 Get-LocalGroup cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-124">To obtain groups, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="82128-125">-Name</span><span class="sxs-lookup"><span data-stu-id="82128-125">-Name</span></span>
<span data-ttu-id="82128-126">이 cmdlet이 삭제 하는 보안 그룹의 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-126">Specifies an array of names of the security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="82128-127">-SID</span><span class="sxs-lookup"><span data-stu-id="82128-127">-SID</span></span>
<span data-ttu-id="82128-128">이 cmdlet이 삭제 하는 보안 그룹의 보안 Id (Sid) 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-128">Specifies an array of security IDs (SIDs) of security groups that this cmdlet deletes.</span></span>

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

### <span data-ttu-id="82128-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="82128-129">-Confirm</span></span>
<span data-ttu-id="82128-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="82128-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="82128-131">-WhatIf</span></span>
<span data-ttu-id="82128-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82128-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="82128-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="82128-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82128-134">CommonParameters</span></span>
<span data-ttu-id="82128-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82128-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82128-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82128-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82128-137">입력</span><span class="sxs-lookup"><span data-stu-id="82128-137">INPUTS</span></span>

### <span data-ttu-id="82128-138">SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="82128-138">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="82128-139">보안 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-139">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="82128-140">출력</span><span class="sxs-lookup"><span data-stu-id="82128-140">OUTPUTS</span></span>

### <span data-ttu-id="82128-141">없음</span><span class="sxs-lookup"><span data-stu-id="82128-141">None</span></span>
<span data-ttu-id="82128-142">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-142">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="82128-143">참고</span><span class="sxs-lookup"><span data-stu-id="82128-143">NOTES</span></span>

* <span data-ttu-id="82128-144">이 cmdlet은 다음과 같은 기본 그룹을 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-144">This cmdlet cannot delete the following default groups:</span></span>

- <span data-ttu-id="82128-145">관리자</span><span class="sxs-lookup"><span data-stu-id="82128-145">Administrators</span></span>
- <span data-ttu-id="82128-146">Backup Operators</span><span class="sxs-lookup"><span data-stu-id="82128-146">Backup Operators</span></span>
- <span data-ttu-id="82128-147">Cryptographic Operators</span><span class="sxs-lookup"><span data-stu-id="82128-147">Cryptographic Operators</span></span>
- <span data-ttu-id="82128-148">Distributed COM Users</span><span class="sxs-lookup"><span data-stu-id="82128-148">Distributed COM Users</span></span>
- <span data-ttu-id="82128-149">Event Log Readers</span><span class="sxs-lookup"><span data-stu-id="82128-149">Event Log Readers</span></span>
- <span data-ttu-id="82128-150">게스트</span><span class="sxs-lookup"><span data-stu-id="82128-150">Guests</span></span>
- <span data-ttu-id="82128-151">Hyper-V 관리자</span><span class="sxs-lookup"><span data-stu-id="82128-151">Hyper-V Administrators</span></span>
- <span data-ttu-id="82128-152">IIS_IUSRS</span><span class="sxs-lookup"><span data-stu-id="82128-152">IIS_IUSRS</span></span>
- <span data-ttu-id="82128-153">Network Configuration Operators</span><span class="sxs-lookup"><span data-stu-id="82128-153">Network Configuration Operators</span></span>
- <span data-ttu-id="82128-154">성능 로그 사용자</span><span class="sxs-lookup"><span data-stu-id="82128-154">Performance Log Users</span></span>
- <span data-ttu-id="82128-155">성능 모니터 사용자</span><span class="sxs-lookup"><span data-stu-id="82128-155">Performance Monitor Users</span></span>
- <span data-ttu-id="82128-156">Power Users</span><span class="sxs-lookup"><span data-stu-id="82128-156">Power Users</span></span>
- <span data-ttu-id="82128-157">Remote Desktop Users</span><span class="sxs-lookup"><span data-stu-id="82128-157">Remote Desktop Users</span></span>
- <span data-ttu-id="82128-158">원격 관리 사용자</span><span class="sxs-lookup"><span data-stu-id="82128-158">Remote Management Users</span></span>
- <span data-ttu-id="82128-159">Replicator</span><span class="sxs-lookup"><span data-stu-id="82128-159">Replicator</span></span>
- <span data-ttu-id="82128-160">사용자</span><span class="sxs-lookup"><span data-stu-id="82128-160">Users</span></span>
- <span data-ttu-id="82128-161">WinRMRemoteWMIUsers__</span><span class="sxs-lookup"><span data-stu-id="82128-161">WinRMRemoteWMIUsers__</span></span>

* <span data-ttu-id="82128-162">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="82128-162">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="82128-163">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-163">The possible sources are as follows:</span></span>

- <span data-ttu-id="82128-164">로컬</span><span class="sxs-lookup"><span data-stu-id="82128-164">Local</span></span>
- <span data-ttu-id="82128-165">Active Directory</span><span class="sxs-lookup"><span data-stu-id="82128-165">Active Directory</span></span>
- <span data-ttu-id="82128-166">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="82128-166">Azure Active Directory group</span></span>
- <span data-ttu-id="82128-167">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="82128-167">Microsoft Account</span></span>

<span data-ttu-id="82128-168">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82128-168">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="82128-169">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82128-169">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="82128-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="82128-170">RELATED LINKS</span></span>

[<span data-ttu-id="82128-171">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="82128-171">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="82128-172">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="82128-172">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="82128-173">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="82128-173">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="82128-174">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="82128-174">Set-LocalGroup</span></span>](Set-LocalGroup.md)
