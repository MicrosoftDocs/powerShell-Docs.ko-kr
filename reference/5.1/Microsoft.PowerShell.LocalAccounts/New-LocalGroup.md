---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/new-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-LocalGroup
ms.openlocfilehash: de66ad724d3cfee2d296d3b431618768a9cd38da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214689"
---
# <span data-ttu-id="6cfba-103">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-103">New-LocalGroup</span></span>

## <span data-ttu-id="6cfba-104">개요</span><span class="sxs-lookup"><span data-stu-id="6cfba-104">SYNOPSIS</span></span>
<span data-ttu-id="6cfba-105">로컬 보안 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-105">Creates a local security group.</span></span>

## <span data-ttu-id="6cfba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6cfba-106">SYNTAX</span></span>

```
New-LocalGroup [-Description <String>] [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6cfba-107">설명</span><span class="sxs-lookup"><span data-stu-id="6cfba-107">DESCRIPTION</span></span>
<span data-ttu-id="6cfba-108">**LocalGroup** Cmdlet은 보안 계정 관리자에서 로컬 보안 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-108">The **New-LocalGroup** cmdlet creates a local security group in the Security Account Manager.</span></span>

> [!NOTE]
> <span data-ttu-id="6cfba-109">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-109">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="6cfba-110">예제</span><span class="sxs-lookup"><span data-stu-id="6cfba-110">EXAMPLES</span></span>

### <span data-ttu-id="6cfba-111">예제 1: 보안 그룹 만들기</span><span class="sxs-lookup"><span data-stu-id="6cfba-111">Example 1: Create a security group</span></span>

```
PS C:\> New-LocalGroup -Name "SecurityGroup04"
```

<span data-ttu-id="6cfba-112">이 명령은 SecurityGroup04 라는 그룹을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-112">This command creates a group named SecurityGroup04.</span></span>

## <span data-ttu-id="6cfba-113">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6cfba-113">PARAMETERS</span></span>

### <span data-ttu-id="6cfba-114">-Description</span><span class="sxs-lookup"><span data-stu-id="6cfba-114">-Description</span></span>
<span data-ttu-id="6cfba-115">그룹에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-115">Specifies a comment for the group.</span></span>
<span data-ttu-id="6cfba-116">최대 길이는 48 자입니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-116">The maximum length is 48 characters.</span></span>

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

### <span data-ttu-id="6cfba-117">-Name</span><span class="sxs-lookup"><span data-stu-id="6cfba-117">-Name</span></span>
<span data-ttu-id="6cfba-118">그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-118">Specifies a name for the group.</span></span>
<span data-ttu-id="6cfba-119">최대 길이는 256자입니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-119">The maximum length is 256 characters.</span></span>

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

### <span data-ttu-id="6cfba-120">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6cfba-120">-Confirm</span></span>
<span data-ttu-id="6cfba-121">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-121">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6cfba-122">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6cfba-122">-WhatIf</span></span>
<span data-ttu-id="6cfba-123">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-123">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6cfba-124">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-124">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6cfba-125">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6cfba-125">CommonParameters</span></span>
<span data-ttu-id="6cfba-126">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6cfba-126">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6cfba-127">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cfba-127">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6cfba-128">입력</span><span class="sxs-lookup"><span data-stu-id="6cfba-128">INPUTS</span></span>

### <span data-ttu-id="6cfba-129">System.String</span><span class="sxs-lookup"><span data-stu-id="6cfba-129">System.String</span></span>
<span data-ttu-id="6cfba-130">이 cmdlet에 문자열을 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-130">You can pipe a string to this cmdlet.</span></span>

## <span data-ttu-id="6cfba-131">출력</span><span class="sxs-lookup"><span data-stu-id="6cfba-131">OUTPUTS</span></span>

### <span data-ttu-id="6cfba-132">SecurityAccountsManager. LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-132">System.Management.Automation.SecurityAccountsManager.LocalGroup</span></span>
<span data-ttu-id="6cfba-133">이 cmdlet은 보안 그룹을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-133">This cmdlet returns a security group.</span></span>

## <span data-ttu-id="6cfba-134">참고</span><span class="sxs-lookup"><span data-stu-id="6cfba-134">NOTES</span></span>

* <span data-ttu-id="6cfba-135">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-135">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="6cfba-136">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-136">The possible sources are as follows:</span></span>

- <span data-ttu-id="6cfba-137">로컬</span><span class="sxs-lookup"><span data-stu-id="6cfba-137">Local</span></span>
- <span data-ttu-id="6cfba-138">Active Directory</span><span class="sxs-lookup"><span data-stu-id="6cfba-138">Active Directory</span></span>
- <span data-ttu-id="6cfba-139">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="6cfba-139">Azure Active Directory group</span></span>
- <span data-ttu-id="6cfba-140">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="6cfba-140">Microsoft Account</span></span>

<span data-ttu-id="6cfba-141">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-141">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="6cfba-142">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cfba-142">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="6cfba-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6cfba-143">RELATED LINKS</span></span>

[<span data-ttu-id="6cfba-144">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-144">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="6cfba-145">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-145">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="6cfba-146">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-146">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)

[<span data-ttu-id="6cfba-147">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="6cfba-147">Set-LocalGroup</span></span>](Set-LocalGroup.md)
