---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215297"
---
# <span data-ttu-id="75299-103">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="75299-103">Restore-DscConfiguration</span></span>

## <span data-ttu-id="75299-104">개요</span><span class="sxs-lookup"><span data-stu-id="75299-104">SYNOPSIS</span></span>
<span data-ttu-id="75299-105">노드의 이전 구성을 다시 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-105">Reapplies the previous configuration for the node.</span></span>

## <span data-ttu-id="75299-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="75299-106">SYNTAX</span></span>

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="75299-107">설명</span><span class="sxs-lookup"><span data-stu-id="75299-107">DESCRIPTION</span></span>
<span data-ttu-id="75299-108">이전 구성이 있는 경우 **start-dscconfiguration** cmdlet은 노드에 대 한 이전 구성을 다시 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-108">The **Restore-DscConfiguration** cmdlet reapplies the previous configuration for the node, if a previous configuration exists.</span></span>
<span data-ttu-id="75299-109">CIM(Common Information Model) 세션을 사용하여 컴퓨터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-109">Specify computers by using Common Information Model (CIM) sessions.</span></span>
<span data-ttu-id="75299-110">대상 컴퓨터를 지정하지 않으면 cmdlet이 로컬 컴퓨터의 구성을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-110">If you do not specify a target computer, the cmdlet restores the configuration of the local computer.</span></span>
<span data-ttu-id="75299-111">특정 노드에 대 한 이전 구성이 없는 경우이 cmdlet은 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-111">If there is no previous configuration for a particular node, this cmdlet returns an error message.</span></span>

<span data-ttu-id="75299-112">이 cmdlet은 **Confirm** 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75299-112">This cmdlet does not support the **Confirm** parameter.</span></span>

## <span data-ttu-id="75299-113">예제</span><span class="sxs-lookup"><span data-stu-id="75299-113">EXAMPLES</span></span>

### <span data-ttu-id="75299-114">예 1: 로컬 컴퓨터에 대 한 구성 복원</span><span class="sxs-lookup"><span data-stu-id="75299-114">Example 1: Restore the configuration for the local computer</span></span>

```
PS C:\> Restore-DscConfiguration
```

<span data-ttu-id="75299-115">이 명령은 로컬 컴퓨터의 구성을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-115">This command restores the configuration for the local computer.</span></span>

### <span data-ttu-id="75299-116">예 2: 지정 된 컴퓨터에 대 한 구성 복원</span><span class="sxs-lookup"><span data-stu-id="75299-116">Example 2: Restore configuration for a specified computer</span></span>

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

<span data-ttu-id="75299-117">이 예제에서는 CIM 세션에 지정된 컴퓨터의 구성을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-117">This example restores configuration on a computer specified by a CIM session.</span></span>
<span data-ttu-id="75299-118">또한 cmdlet에 사용하기 위해 이름이 Server01인 컴퓨터에 대한 CIM 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75299-118">The example creates a CIM session for a computer named Server01 for use with the cmdlet.</span></span>
<span data-ttu-id="75299-119">또는 지정한 여러 컴퓨터에 cmdlet을 적용하기 위해 CIM 세션 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75299-119">Alternatively, create an array of CIM sessions to apply the cmdlet to multiple specified computers.</span></span>

<span data-ttu-id="75299-120">첫 번째 명령은 **New-CimSession** cmdlet을 사용하여 CIM 세션을 만든 다음 **CimSession** 개체를 $Session 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-120">The first command creates a CIM session by using the **New-CimSession** cmdlet, and then stores the **CimSession** object in the $Session variable.</span></span>
<span data-ttu-id="75299-121">또한 암호를 입력하라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-121">The command prompts you for a password.</span></span>
<span data-ttu-id="75299-122">자세한 내용을 보려면 `Get-Help New-CimSession`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="75299-122">For more information, type `Get-Help New-CimSession`.</span></span>

<span data-ttu-id="75299-123">두 번째 명령은 $Session 변수에 저장 된 **CimSession** 개체로 식별 된 컴퓨터 (이 경우 이름이 Server01 인 컴퓨터)의 구성을 복원 합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-123">The second command restores the configuration for the computers identified by the **CimSession** objects stored in the $Session variable, in this case, the computer named Server01.</span></span>

## <span data-ttu-id="75299-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="75299-124">PARAMETERS</span></span>

### <span data-ttu-id="75299-125">-AsJob</span><span class="sxs-lookup"><span data-stu-id="75299-125">-AsJob</span></span>
<span data-ttu-id="75299-126">이 cmdlet이 명령을 백그라운드 작업으로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75299-126">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="75299-127">-CimSession</span><span class="sxs-lookup"><span data-stu-id="75299-127">-CimSession</span></span>
<span data-ttu-id="75299-128">원격 세션에서 또는 원격 컴퓨터에서 cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-128">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="75299-129">**CimSession** 또는 **CimSession** cmdlet의 출력과 같은 컴퓨터 이름 또는 세션 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-129">Enter a computer name or a session object, such as the output of a **New-CimSession** or **Get-CimSession** cmdlet.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75299-130">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="75299-130">-ThrottleLimit</span></span>
<span data-ttu-id="75299-131">cmdlet을 실행하도록 설정할 수 있는 최대 동시 작업 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-131">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="75299-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="75299-132">-Confirm</span></span>
<span data-ttu-id="75299-133">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="75299-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="75299-134">-WhatIf</span></span>
<span data-ttu-id="75299-135">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="75299-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="75299-136">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="75299-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="75299-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="75299-137">CommonParameters</span></span>
<span data-ttu-id="75299-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="75299-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="75299-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75299-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="75299-140">입력</span><span class="sxs-lookup"><span data-stu-id="75299-140">INPUTS</span></span>

## <span data-ttu-id="75299-141">출력</span><span class="sxs-lookup"><span data-stu-id="75299-141">OUTPUTS</span></span>

## <span data-ttu-id="75299-142">참고</span><span class="sxs-lookup"><span data-stu-id="75299-142">NOTES</span></span>

## <span data-ttu-id="75299-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="75299-143">RELATED LINKS</span></span>

[<span data-ttu-id="75299-144">Windows PowerShell Desired State Configuration 개요</span><span class="sxs-lookup"><span data-stu-id="75299-144">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="75299-145">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="75299-145">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="75299-146">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="75299-146">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="75299-147">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="75299-147">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="75299-148">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="75299-148">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
