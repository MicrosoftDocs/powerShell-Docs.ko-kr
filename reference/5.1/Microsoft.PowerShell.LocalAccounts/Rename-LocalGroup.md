---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/rename-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-LocalGroup
ms.openlocfilehash: 566d33bdeb52323cca41fa9757d36334b40f1654
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215625"
---
# <span data-ttu-id="9c115-103">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="9c115-103">Rename-LocalGroup</span></span>

## <span data-ttu-id="9c115-104">개요</span><span class="sxs-lookup"><span data-stu-id="9c115-104">SYNOPSIS</span></span>
<span data-ttu-id="9c115-105">로컬 보안 그룹의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-105">Renames a local security group.</span></span>

## <span data-ttu-id="9c115-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9c115-106">SYNTAX</span></span>

### <span data-ttu-id="9c115-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="9c115-107">InputObject</span></span>

```
Rename-LocalGroup [-InputObject] <LocalGroup> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c115-108">기본값</span><span class="sxs-lookup"><span data-stu-id="9c115-108">Default</span></span>

```
Rename-LocalGroup [-Name] <String> [-NewName] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9c115-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="9c115-109">SecurityIdentifier</span></span>

```
Rename-LocalGroup [-NewName] <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9c115-110">설명</span><span class="sxs-lookup"><span data-stu-id="9c115-110">DESCRIPTION</span></span>
<span data-ttu-id="9c115-111">**LocalGroup** cmdlet은 로컬 보안 그룹의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-111">The **Rename-LocalGroup** cmdlet renames a local security group.</span></span>

> [!NOTE]
> <span data-ttu-id="9c115-112">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-112">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="9c115-113">예제</span><span class="sxs-lookup"><span data-stu-id="9c115-113">EXAMPLES</span></span>

### <span data-ttu-id="9c115-114">예제 1: 그룹 이름 변경</span><span class="sxs-lookup"><span data-stu-id="9c115-114">Example 1: Change the name of a group</span></span>

```
PS C:\> Rename-LocalGroup -Name "SecurityGroup" -NewName "SecurityGroup04"
```

<span data-ttu-id="9c115-115">이 명령은 SecurityGroup 이라는 보안 그룹의 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-115">This command renames a security group named SecurityGroup.</span></span>

## <span data-ttu-id="9c115-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9c115-116">PARAMETERS</span></span>

### <span data-ttu-id="9c115-117">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9c115-117">-InputObject</span></span>
<span data-ttu-id="9c115-118">이 cmdlet이 이름을 바꿀 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-118">Specifies the security group that this cmdlet renames.</span></span>
<span data-ttu-id="9c115-119">보안 그룹을 얻으려면 Get-LocalGroup cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-119">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.LocalGroup
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9c115-120">-Name</span><span class="sxs-lookup"><span data-stu-id="9c115-120">-Name</span></span>
<span data-ttu-id="9c115-121">이 cmdlet이 이름을 바꿀 보안 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-121">Specifies the name of the security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="9c115-122">-NewName</span><span class="sxs-lookup"><span data-stu-id="9c115-122">-NewName</span></span>
<span data-ttu-id="9c115-123">보안 그룹의 새 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-123">Specifies a new name for the security group.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9c115-124">-SID</span><span class="sxs-lookup"><span data-stu-id="9c115-124">-SID</span></span>
<span data-ttu-id="9c115-125">이 cmdlet이 이름을 바꾸는 보안 그룹의 SID (보안 ID)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-125">Specifies the security ID (SID) of a security group that this cmdlet renames.</span></span>

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

### <span data-ttu-id="9c115-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9c115-126">-Confirm</span></span>
<span data-ttu-id="9c115-127">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9c115-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9c115-128">-WhatIf</span></span>
<span data-ttu-id="9c115-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="9c115-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9c115-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9c115-131">CommonParameters</span></span>
<span data-ttu-id="9c115-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9c115-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9c115-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9c115-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9c115-134">입력</span><span class="sxs-lookup"><span data-stu-id="9c115-134">INPUTS</span></span>

### <span data-ttu-id="9c115-135">SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="9c115-135">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="9c115-136">보안 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-136">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="9c115-137">출력</span><span class="sxs-lookup"><span data-stu-id="9c115-137">OUTPUTS</span></span>

### <span data-ttu-id="9c115-138">없음</span><span class="sxs-lookup"><span data-stu-id="9c115-138">None</span></span>
<span data-ttu-id="9c115-139">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-139">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="9c115-140">참고</span><span class="sxs-lookup"><span data-stu-id="9c115-140">NOTES</span></span>

* <span data-ttu-id="9c115-141">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-141">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="9c115-142">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-142">The possible sources are as follows:</span></span>

- <span data-ttu-id="9c115-143">로컬</span><span class="sxs-lookup"><span data-stu-id="9c115-143">Local</span></span>
- <span data-ttu-id="9c115-144">Active Directory</span><span class="sxs-lookup"><span data-stu-id="9c115-144">Active Directory</span></span>
- <span data-ttu-id="9c115-145">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="9c115-145">Azure Active Directory group</span></span>
- <span data-ttu-id="9c115-146">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="9c115-146">Microsoft Account</span></span>

<span data-ttu-id="9c115-147">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-147">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="9c115-148">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c115-148">For earlier  versions, the property is blank.</span></span>

## <span data-ttu-id="9c115-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9c115-149">RELATED LINKS</span></span>

[<span data-ttu-id="9c115-150">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="9c115-150">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="9c115-151">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="9c115-151">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="9c115-152">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="9c115-152">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="9c115-153">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="9c115-153">Set-LocalGroup</span></span>](Set-LocalGroup.md)
