---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: 645efc2d271a3b95801c8d0d264ee33ed788f15f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602815"
---
# <span data-ttu-id="dc0bc-102">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-102">Remove-Service</span></span>

## <span data-ttu-id="dc0bc-103">개요</span><span class="sxs-lookup"><span data-stu-id="dc0bc-103">SYNOPSIS</span></span>
<span data-ttu-id="dc0bc-104">Windows 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-104">Removes a Windows service.</span></span>

## <span data-ttu-id="dc0bc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc0bc-105">SYNTAX</span></span>

### <span data-ttu-id="dc0bc-106">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="dc0bc-106">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="dc0bc-107">InputObject</span><span class="sxs-lookup"><span data-stu-id="dc0bc-107">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="dc0bc-108">설명</span><span class="sxs-lookup"><span data-stu-id="dc0bc-108">DESCRIPTION</span></span>

<span data-ttu-id="dc0bc-109">`Remove-Service`Cmdlet은 레지스트리 및 서비스 데이터베이스에서 Windows 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-109">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="dc0bc-110">`Remove-Service`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-110">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="dc0bc-111">예제</span><span class="sxs-lookup"><span data-stu-id="dc0bc-111">EXAMPLES</span></span>

### <span data-ttu-id="dc0bc-112">예제 1: 서비스 제거</span><span class="sxs-lookup"><span data-stu-id="dc0bc-112">Example 1: Remove a service</span></span>

<span data-ttu-id="dc0bc-113">그러면 TestService 라는 서비스가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-113">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="dc0bc-114">예 2: 표시 이름을 사용 하 여 서비스 제거</span><span class="sxs-lookup"><span data-stu-id="dc0bc-114">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="dc0bc-115">이 예제에서는 TestService 라는 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-115">This example removes a service named TestService.</span></span> <span data-ttu-id="dc0bc-116">명령을 사용 하 여 `Get-Service` 표시 이름을 사용 하는 TestService 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-116">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="dc0bc-117">파이프라인 연산자 ( `|` )는 개체를로 파이프 하 여 `Remove-Service` 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-117">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="dc0bc-118">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dc0bc-118">PARAMETERS</span></span>

### <span data-ttu-id="dc0bc-119">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dc0bc-119">-InputObject</span></span>

<span data-ttu-id="dc0bc-120">제거할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-120">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="dc0bc-121">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-121">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController
Parameter Sets: InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dc0bc-122">-Name</span><span class="sxs-lookup"><span data-stu-id="dc0bc-122">-Name</span></span>

<span data-ttu-id="dc0bc-123">제거할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-123">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="dc0bc-124">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-124">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases: ServiceName, SN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="dc0bc-125">-Confirm</span><span class="sxs-lookup"><span data-stu-id="dc0bc-125">-Confirm</span></span>

<span data-ttu-id="dc0bc-126">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-126">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="dc0bc-127">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="dc0bc-127">-WhatIf</span></span>

<span data-ttu-id="dc0bc-128">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-128">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="dc0bc-129">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-129">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="dc0bc-130">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc0bc-130">CommonParameters</span></span>

<span data-ttu-id="dc0bc-131">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-131">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc0bc-132">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-132">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc0bc-133">입력</span><span class="sxs-lookup"><span data-stu-id="dc0bc-133">INPUTS</span></span>

### <span data-ttu-id="dc0bc-134">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-134">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="dc0bc-135">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-135">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="dc0bc-136">출력</span><span class="sxs-lookup"><span data-stu-id="dc0bc-136">OUTPUTS</span></span>

### <span data-ttu-id="dc0bc-137">없음</span><span class="sxs-lookup"><span data-stu-id="dc0bc-137">None</span></span>

<span data-ttu-id="dc0bc-138">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-138">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="dc0bc-139">참고</span><span class="sxs-lookup"><span data-stu-id="dc0bc-139">NOTES</span></span>

<span data-ttu-id="dc0bc-140">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-140">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="dc0bc-141">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dc0bc-141">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="dc0bc-142">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dc0bc-142">RELATED LINKS</span></span>

[<span data-ttu-id="dc0bc-143">Get-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-143">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="dc0bc-144">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-144">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="dc0bc-145">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-145">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="dc0bc-146">Set-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-146">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="dc0bc-147">Start-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-147">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="dc0bc-148">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-148">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="dc0bc-149">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="dc0bc-149">Suspend-Service</span></span>](Suspend-Service.md)
