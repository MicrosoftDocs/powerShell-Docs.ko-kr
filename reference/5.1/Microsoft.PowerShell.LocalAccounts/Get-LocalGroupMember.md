---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/get-localgroupmember?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-LocalGroupMember
ms.openlocfilehash: 200368c5d13bd027302ad824533e6c187906ed0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211890"
---
# <span data-ttu-id="a78f4-103">Get-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a78f4-103">Get-LocalGroupMember</span></span>

## <span data-ttu-id="a78f4-104">개요</span><span class="sxs-lookup"><span data-stu-id="a78f4-104">SYNOPSIS</span></span>
<span data-ttu-id="a78f4-105">로컬 그룹에서 멤버를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-105">Gets members from a local group.</span></span>

## <span data-ttu-id="a78f4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a78f4-106">SYNTAX</span></span>

### <span data-ttu-id="a78f4-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="a78f4-107">Default (Default)</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-Name] <String> [<CommonParameters>]
```

### <span data-ttu-id="a78f4-108">그룹</span><span class="sxs-lookup"><span data-stu-id="a78f4-108">Group</span></span>

```
Get-LocalGroupMember [-Group] <LocalGroup> [[-Member] <String>] [<CommonParameters>]
```

### <span data-ttu-id="a78f4-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="a78f4-109">SecurityIdentifier</span></span>

```
Get-LocalGroupMember [[-Member] <String>] [-SID] <SecurityIdentifier> [<CommonParameters>]
```

## <span data-ttu-id="a78f4-110">설명</span><span class="sxs-lookup"><span data-stu-id="a78f4-110">DESCRIPTION</span></span>
<span data-ttu-id="a78f4-111">**Get LocalGroupMember** cmdlet은 로컬 그룹에서 구성원을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-111">The **Get-LocalGroupMember** cmdlet gets members from a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="a78f4-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="a78f4-113">예제</span><span class="sxs-lookup"><span data-stu-id="a78f4-113">EXAMPLES</span></span>

### <span data-ttu-id="a78f4-114">예 1: Administrators 그룹의 모든 구성원 가져오기</span><span class="sxs-lookup"><span data-stu-id="a78f4-114">Example 1: Get all members of the Administrators group</span></span>

```
PS C:\> Get-LocalGroupMember -Group "Administrators"
ObjectClass Name                    PrincipalSource
----------- ----                    ---------------
User        CONTOSOPC\Administrator Local
User        CONTOSOPC\LocalAdmin    Local
```

<span data-ttu-id="a78f4-115">이 명령은 로컬 Administrators 그룹의 모든 구성원을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-115">This command gets all the members of the local Administrators group.</span></span>

## <span data-ttu-id="a78f4-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a78f4-116">PARAMETERS</span></span>

### <span data-ttu-id="a78f4-117">-그룹</span><span class="sxs-lookup"><span data-stu-id="a78f4-117">-Group</span></span>
<span data-ttu-id="a78f4-118">이 cmdlet이 멤버를 가져오는 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-118">Specifies the security group from which this cmdlet gets members.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: Group
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a78f4-119">-Member</span><span class="sxs-lookup"><span data-stu-id="a78f4-119">-Member</span></span>
<span data-ttu-id="a78f4-120">이 cmdlet이 보안 그룹에서 가져온 사용자 또는 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-120">Specifies a user or group that this cmdlet gets from a security group.</span></span>
<span data-ttu-id="a78f4-121">이름 또는 SID (보안 ID)를 기준으로 사용자 또는 그룹을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-121">You can specify users or groups by name or security ID (SID).</span></span>
<span data-ttu-id="a78f4-122">S-R-I-s-s에서 SID 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-122">Specify SID strings in S-R-I-S-S .</span></span>
<span data-ttu-id="a78f4-123">.</span><span class="sxs-lookup"><span data-stu-id="a78f4-123">.</span></span> <span data-ttu-id="a78f4-124">.</span><span class="sxs-lookup"><span data-stu-id="a78f4-124">.</span></span>
<span data-ttu-id="a78f4-125">형식.</span><span class="sxs-lookup"><span data-stu-id="a78f4-125">format.</span></span>
<span data-ttu-id="a78f4-126">와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-126">You can use wildcard characters.</span></span>
<span data-ttu-id="a78f4-127">이 매개 변수를 지정 하지 않으면 cmdlet은 그룹의 모든 구성원을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-127">If you do not specify this parameter, the cmdlet gets all members of the group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a78f4-128">-Name</span><span class="sxs-lookup"><span data-stu-id="a78f4-128">-Name</span></span>
<span data-ttu-id="a78f4-129">이 cmdlet이 멤버를 가져오는 보안 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-129">Specifies the name of the security group from which this cmdlet gets members.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a78f4-130">-SID</span><span class="sxs-lookup"><span data-stu-id="a78f4-130">-SID</span></span>
<span data-ttu-id="a78f4-131">이 cmdlet이 구성원을 가져오는 보안 그룹의 보안 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-131">Specifies the security ID of the security group from which this cmdlet gets members.</span></span>

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

### <span data-ttu-id="a78f4-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a78f4-132">CommonParameters</span></span>
<span data-ttu-id="a78f4-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a78f4-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a78f4-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a78f4-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a78f4-135">입력</span><span class="sxs-lookup"><span data-stu-id="a78f4-135">INPUTS</span></span>

### <span data-ttu-id="a78f4-136">SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="a78f4-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="a78f4-137">로컬 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-137">You can pipe a local group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="a78f4-138">출력</span><span class="sxs-lookup"><span data-stu-id="a78f4-138">OUTPUTS</span></span>

### <span data-ttu-id="a78f4-139">SecurityAccountsManager</span><span class="sxs-lookup"><span data-stu-id="a78f4-139">Microsoft.SecurityAccountsManager.LocalPrincipal</span></span>
<span data-ttu-id="a78f4-140">이 cmdlet은 로컬 보안 주체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-140">This cmdlet returns local principals.</span></span>

## <span data-ttu-id="a78f4-141">참고</span><span class="sxs-lookup"><span data-stu-id="a78f4-141">NOTES</span></span>

* <span data-ttu-id="a78f4-142">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="a78f4-143">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="a78f4-144">로컬</span><span class="sxs-lookup"><span data-stu-id="a78f4-144">Local</span></span>
- <span data-ttu-id="a78f4-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="a78f4-145">Active Directory</span></span>
- <span data-ttu-id="a78f4-146">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="a78f4-146">Azure Active Directory group</span></span>
- <span data-ttu-id="a78f4-147">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="a78f4-147">Microsoft Account</span></span>

<span data-ttu-id="a78f4-148">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="a78f4-149">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a78f4-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="a78f4-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a78f4-150">RELATED LINKS</span></span>

[<span data-ttu-id="a78f4-151">Add-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a78f4-151">Add-LocalGroupMember</span></span>](Add-LocalGroupMember.md)

[<span data-ttu-id="a78f4-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="a78f4-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="a78f4-153">Remove-LocalGroupMember</span><span class="sxs-lookup"><span data-stu-id="a78f4-153">Remove-LocalGroupMember</span></span>](Remove-LocalGroupMember.md)
