---
external help file: Microsoft.Powershell.LocalAccounts.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.LocalAccounts
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.localaccounts/set-localgroup?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-LocalGroup
ms.openlocfilehash: 471c3c7bc01bf26dfe9d8eec26e4414464cae02e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215626"
---
# <span data-ttu-id="7f805-103">Set-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f805-103">Set-LocalGroup</span></span>

## <span data-ttu-id="7f805-104">개요</span><span class="sxs-lookup"><span data-stu-id="7f805-104">SYNOPSIS</span></span>
<span data-ttu-id="7f805-105">로컬 보안 그룹을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-105">Changes a local security group.</span></span>

## <span data-ttu-id="7f805-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f805-106">SYNTAX</span></span>

### <span data-ttu-id="7f805-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="7f805-107">InputObject</span></span>

```
Set-LocalGroup -Description <String> [-InputObject] <LocalGroup> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f805-108">기본값</span><span class="sxs-lookup"><span data-stu-id="7f805-108">Default</span></span>

```
Set-LocalGroup -Description <String> [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7f805-109">SecurityIdentifier</span><span class="sxs-lookup"><span data-stu-id="7f805-109">SecurityIdentifier</span></span>

```
Set-LocalGroup -Description <String> [-SID] <SecurityIdentifier> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7f805-110">설명</span><span class="sxs-lookup"><span data-stu-id="7f805-110">DESCRIPTION</span></span>
<span data-ttu-id="7f805-111">**LocalGroup** cmdlet은 로컬 보안 그룹을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-111">The **Set-LocalGroup** cmdlet changes a local security group.</span></span>

## <span data-ttu-id="7f805-112">예제</span><span class="sxs-lookup"><span data-stu-id="7f805-112">EXAMPLES</span></span>

### <span data-ttu-id="7f805-113">예제 1: 그룹 설명 변경</span><span class="sxs-lookup"><span data-stu-id="7f805-113">Example 1: Change a group description</span></span>

```
PS C:\> Set-LocalGroup -Name "SecurityGroup04" -Description "This is a sample description."
```

<span data-ttu-id="7f805-114">이 명령은 로컬 그룹에 대 한 설명을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-114">This command changes the description of a local group.</span></span>

> [!NOTE]
> <span data-ttu-id="7f805-115">64 비트 시스템의 32 비트 PowerShell에서는 Microsoft. PowerShell. LocalAccounts 모듈을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-115">The Microsoft.PowerShell.LocalAccounts module is not available in 32-bit PowerShell on a 64-bit system.</span></span>

## <span data-ttu-id="7f805-116">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7f805-116">PARAMETERS</span></span>

### <span data-ttu-id="7f805-117">-Description</span><span class="sxs-lookup"><span data-stu-id="7f805-117">-Description</span></span>
<span data-ttu-id="7f805-118">그룹에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-118">Specifies a comment for the group.</span></span>
<span data-ttu-id="7f805-119">최대 길이는 48 자입니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-119">The maximum length is 48 characters.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f805-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="7f805-120">-InputObject</span></span>
<span data-ttu-id="7f805-121">이 cmdlet이 변경 하는 보안 그룹을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-121">Specifies the security group that this cmdlet changes.</span></span>
<span data-ttu-id="7f805-122">보안 그룹을 얻으려면 Get-LocalGroup cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-122">To obtain a security group, use the Get-LocalGroup cmdlet.</span></span>

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

### <span data-ttu-id="7f805-123">-Name</span><span class="sxs-lookup"><span data-stu-id="7f805-123">-Name</span></span>
<span data-ttu-id="7f805-124">이 cmdlet이 변경 하는 보안 그룹의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-124">Specifies the name of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="7f805-125">-SID</span><span class="sxs-lookup"><span data-stu-id="7f805-125">-SID</span></span>
<span data-ttu-id="7f805-126">이 cmdlet이 변경 하는 보안 그룹의 SID (보안 ID)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-126">Specifies the security ID (SID) of the security group that this cmdlet changes.</span></span>

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

### <span data-ttu-id="7f805-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7f805-127">-Confirm</span></span>
<span data-ttu-id="7f805-128">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-128">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7f805-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7f805-129">-WhatIf</span></span>
<span data-ttu-id="7f805-130">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-130">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7f805-131">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-131">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7f805-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f805-132">CommonParameters</span></span>
<span data-ttu-id="7f805-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f805-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f805-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f805-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f805-135">입력</span><span class="sxs-lookup"><span data-stu-id="7f805-135">INPUTS</span></span>

### <span data-ttu-id="7f805-136">SecurityAccountsManager. LocalGroup, System.string, SecurityIdentifier.. n a m a.</span><span class="sxs-lookup"><span data-stu-id="7f805-136">System.Management.Automation.SecurityAccountsManager.LocalGroup, System.String, System.Security.Principal.SecurityIdentifier</span></span>
<span data-ttu-id="7f805-137">보안 그룹, 문자열 또는 SID를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-137">You can pipe a security group, a string, or a SID to this cmdlet.</span></span>

## <span data-ttu-id="7f805-138">출력</span><span class="sxs-lookup"><span data-stu-id="7f805-138">OUTPUTS</span></span>

### <span data-ttu-id="7f805-139">없음</span><span class="sxs-lookup"><span data-stu-id="7f805-139">None</span></span>
<span data-ttu-id="7f805-140">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-140">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7f805-141">참고</span><span class="sxs-lookup"><span data-stu-id="7f805-141">NOTES</span></span>

* <span data-ttu-id="7f805-142">**Principalsource** 속성은 개체의 소스를 설명 하는 **localuser** , **LocalGroup** 및 **localuser** 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-142">The **PrincipalSource** property is a property on **LocalUser** , **LocalGroup** , and **LocalPrincipal** objects that describes the source of the object.</span></span> <span data-ttu-id="7f805-143">가능한 소스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-143">The possible sources are as follows:</span></span>

- <span data-ttu-id="7f805-144">로컬</span><span class="sxs-lookup"><span data-stu-id="7f805-144">Local</span></span>
- <span data-ttu-id="7f805-145">Active Directory</span><span class="sxs-lookup"><span data-stu-id="7f805-145">Active Directory</span></span>
- <span data-ttu-id="7f805-146">Azure Active Directory 그룹</span><span class="sxs-lookup"><span data-stu-id="7f805-146">Azure Active Directory group</span></span>
- <span data-ttu-id="7f805-147">Microsoft 계정</span><span class="sxs-lookup"><span data-stu-id="7f805-147">Microsoft Account</span></span>

<span data-ttu-id="7f805-148">**Principalsource** 는 windows 10, windows Server 2016 이상 버전의 windows 운영 체제 에서만 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-148">**PrincipalSource** is supported only by Windows 10, Windows Server 2016, and later versions of the Windows operating system.</span></span> <span data-ttu-id="7f805-149">이전 버전의 경우 속성은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f805-149">For earlier versions, the property is blank.</span></span>

## <span data-ttu-id="7f805-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7f805-150">RELATED LINKS</span></span>

[<span data-ttu-id="7f805-151">Get-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f805-151">Get-LocalGroup</span></span>](Get-LocalGroup.md)

[<span data-ttu-id="7f805-152">New-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f805-152">New-LocalGroup</span></span>](New-LocalGroup.md)

[<span data-ttu-id="7f805-153">Remove-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f805-153">Remove-LocalGroup</span></span>](Remove-LocalGroup.md)

[<span data-ttu-id="7f805-154">Rename-LocalGroup</span><span class="sxs-lookup"><span data-stu-id="7f805-154">Rename-LocalGroup</span></span>](Rename-LocalGroup.md)
