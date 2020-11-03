---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-pssnapin?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSSnapin
ms.openlocfilehash: e74aff3e52c61f41a54664efbab9c0f195b0d409
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212778"
---
# <span data-ttu-id="96f16-103">Remove-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="96f16-103">Remove-PSSnapin</span></span>

## <span data-ttu-id="96f16-104">개요</span><span class="sxs-lookup"><span data-stu-id="96f16-104">SYNOPSIS</span></span>
<span data-ttu-id="96f16-105">현재 세션에서 Windows PowerShell 스냅인을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-105">Removes Windows PowerShell snap-ins from the current session.</span></span>

## <span data-ttu-id="96f16-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="96f16-106">SYNTAX</span></span>

```
Remove-PSSnapin [-Name] <String[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="96f16-107">설명</span><span class="sxs-lookup"><span data-stu-id="96f16-107">DESCRIPTION</span></span>
<span data-ttu-id="96f16-108">**Add-pssnapin** cmdlet은 현재 세션에서 Windows PowerShell 스냅인을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-108">The **Remove-PSSnapin** cmdlet removes a Windows PowerShell snap-in from the current session.</span></span>
<span data-ttu-id="96f16-109">이 cmdlet을 사용 하 여 windows PowerShell에 추가 된 스냅인을 제거할 수 있습니다 .이 cmdlet을 사용 하 여 Windows PowerShell과 함께 설치 된 스냅인을 제거할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-109">You can use it to remove snap-ins that you have added to Windows PowerShell You cannot use this cmdlet to remove the snap-ins that are installed with Windows PowerShell.</span></span>

<span data-ttu-id="96f16-110">현재 세션에서 스냅인을 제거 하면 스냅인이 여전히 로드 되지만 스냅인의 cmdlet 및 공급자는 세션에서 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-110">After you remove a snap-in from the current session, the snap-in is still loaded, but the cmdlets and providers in the snap-in are no longer available in the session.</span></span>

## <span data-ttu-id="96f16-111">예제</span><span class="sxs-lookup"><span data-stu-id="96f16-111">EXAMPLES</span></span>

### <span data-ttu-id="96f16-112">예제 1: 스냅인 제거</span><span class="sxs-lookup"><span data-stu-id="96f16-112">Example 1: Remove a snap-in</span></span>

```
PS C:\> remove-pssnapin -Name Microsoft.Exchange
```

<span data-ttu-id="96f16-113">이 명령은 현재 세션에서 **Microsoft Exchange** 스냅인을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-113">This command removes the **Microsoft.Exchange** snap-in from the current session.</span></span>
<span data-ttu-id="96f16-114">명령이 완료되면 스냅인이 지원하는 cmdlet 및 공급자를 세션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-114">When the command is complete, the cmdlets and providers that the snap-in supported are not available in the session.</span></span>

### <span data-ttu-id="96f16-115">예제 2: 파이프라인에서 이름을 사용 하 여 스냅인 제거</span><span class="sxs-lookup"><span data-stu-id="96f16-115">Example 2: Remove snap-ins by using names with the pipeline</span></span>

```
PS C:\> Get-PSSnapIn smp* | Remove-PSSnapIn
```

<span data-ttu-id="96f16-116">이 명령은 현재 세션에서 smp로 시작 하는 이름을 가진 Windows PowerShell 스냅인을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-116">This command removes the Windows PowerShell snap-ins that have names that start with smp from the current session.</span></span>

<span data-ttu-id="96f16-117">이 명령은 **add-pssnapin** cmdlet을 사용 하 여 스냅인을 나타내는 개체를 가져옵니다. 파이프라인 연산자 (|)가 결과를 **add-pssnapin** cmdlet으로 보내면이 cmdlet이 결과를 세션에서 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-117">The command uses the **Get-PSSnapin** cmdlet to get objects that represent the snap-ins. The pipeline operator (|) sends the results to the **Remove-PSSnapin** cmdlet, which removes them from the session.</span></span>
<span data-ttu-id="96f16-118">명령이 완료되면 스냅인이 지원하는 cmdlet 및 공급자를 세션에서 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-118">The providers and cmdlets that this snap-in supports are no longer available in the session.</span></span>

<span data-ttu-id="96f16-119">개체를 **add-pssnapin** 에 파이프 하면 개체 이름이 *name 매개 변수와* 연결 됩니다 .이 매개 변수는 **name** 속성을 가진 파이프라인의 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-119">When you pipe objects to **Remove-PSSnapin** , the names of the objects are associated with the *Name* parameter, which accepts objects from the pipeline that have a **Name** property.</span></span>

### <span data-ttu-id="96f16-120">예제 3: 이름을 사용 하 여 스냅인 제거</span><span class="sxs-lookup"><span data-stu-id="96f16-120">Example 3: Remove snap-ins by using names</span></span>

```
PS C:\> Remove-PSSnapin -Name *event*
```

<span data-ttu-id="96f16-121">이 명령은 이벤트를 포함 하는 이름이 있는 모든 Windows PowerShell 스냅인을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-121">This command removes all Windows PowerShell snap-ins that have names that include event.</span></span>

## <span data-ttu-id="96f16-122">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="96f16-122">PARAMETERS</span></span>

### <span data-ttu-id="96f16-123">-Name</span><span class="sxs-lookup"><span data-stu-id="96f16-123">-Name</span></span>
<span data-ttu-id="96f16-124">현재 세션에서 제거할 Windows PowerShell 스냅인의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-124">Specifies the names of Windows PowerShell snap-ins to remove from the current session.</span></span>
<span data-ttu-id="96f16-125">와일드카드 문자(\*)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-125">Wildcard characters (\*) are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="96f16-126">-PassThru</span><span class="sxs-lookup"><span data-stu-id="96f16-126">-PassThru</span></span>
<span data-ttu-id="96f16-127">스냅인을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-127">Returns an object that represents the snap-in.</span></span>
<span data-ttu-id="96f16-128">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-128">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="96f16-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="96f16-129">-Confirm</span></span>
<span data-ttu-id="96f16-130">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="96f16-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="96f16-131">-WhatIf</span></span>
<span data-ttu-id="96f16-132">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="96f16-133">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="96f16-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96f16-134">CommonParameters</span></span>
<span data-ttu-id="96f16-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="96f16-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="96f16-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="96f16-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="96f16-137">입력</span><span class="sxs-lookup"><span data-stu-id="96f16-137">INPUTS</span></span>

### <span data-ttu-id="96f16-138">PSSnapInInfo.</span><span class="sxs-lookup"><span data-stu-id="96f16-138">System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="96f16-139">스냅인 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-139">You can pipe a snap-in object to this cmdlet.</span></span>

## <span data-ttu-id="96f16-140">출력</span><span class="sxs-lookup"><span data-stu-id="96f16-140">OUTPUTS</span></span>

### <span data-ttu-id="96f16-141">None, PSSnapInInfo</span><span class="sxs-lookup"><span data-stu-id="96f16-141">None, System.Management.Automation.PSSnapInInfo</span></span>
<span data-ttu-id="96f16-142">이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 스냅인을 나타내는 **PSSnapInInfo** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-142">This cmdlet generates a **System.Management.Automation.PSSnapInInfo** object that represents the snap-in, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="96f16-143">기본적으로 **add-pssnapin** 은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-143">By default, **Remove-PSSnapin** does not generate any output.</span></span>

## <span data-ttu-id="96f16-144">참고</span><span class="sxs-lookup"><span data-stu-id="96f16-144">NOTES</span></span>

* <span data-ttu-id="96f16-145">**Add-pssnapin** 는 세션에서 스냅인을 제거 하기 전에 Windows PowerShell의 버전을 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-145">**Remove-PSSnapin** does not check the version of Windows PowerShell before removing a snap-in from the session.</span></span> <span data-ttu-id="96f16-146">스냅인을 제거할 수 없는 경우 경고가 표시되고 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-146">If a snap-in cannot be removed, a warning appears and the command fails.</span></span>
* <span data-ttu-id="96f16-147">**Add-pssnapin** 는 현재 세션에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-147">**Remove-PSSnapin** affects only the current session.</span></span> <span data-ttu-id="96f16-148">Add-PSSnapin 명령을 Windows PowerShell 프로필에 추가한 경우 이후 세션에서 스냅인을 제거하려면 이 명령을 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-148">If you have added an Add-PSSnapin command to your Windows PowerShell profile, you should delete the command to remove the snap-in from future sessions.</span></span> <span data-ttu-id="96f16-149">지침을 보려면을 입력 `Get-Help about_Profiles` 합니다.</span><span class="sxs-lookup"><span data-stu-id="96f16-149">For instructions, type `Get-Help about_Profiles`.</span></span>

## <span data-ttu-id="96f16-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="96f16-150">RELATED LINKS</span></span>

[<span data-ttu-id="96f16-151">Add-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="96f16-151">Add-PSSnapin</span></span>](Add-PSSnapin.md)

[<span data-ttu-id="96f16-152">Get-PSSnapin</span><span class="sxs-lookup"><span data-stu-id="96f16-152">Get-PSSnapin</span></span>](Get-PSSnapin.md)
