---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-service?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Service
ms.openlocfilehash: d5189dfb39e9505efd39bfd55791d512e40a7c3e
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94343796"
---
# <span data-ttu-id="63c27-103">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-103">Remove-Service</span></span>

## <span data-ttu-id="63c27-104">개요</span><span class="sxs-lookup"><span data-stu-id="63c27-104">SYNOPSIS</span></span>
<span data-ttu-id="63c27-105">Windows 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-105">Removes a Windows service.</span></span>

## <span data-ttu-id="63c27-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="63c27-106">SYNTAX</span></span>

### <span data-ttu-id="63c27-107">이름 (기본값)</span><span class="sxs-lookup"><span data-stu-id="63c27-107">Name (Default)</span></span>

```
Remove-Service [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="63c27-108">InputObject</span><span class="sxs-lookup"><span data-stu-id="63c27-108">InputObject</span></span>

```
Remove-Service [-InputObject <ServiceController>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="63c27-109">설명</span><span class="sxs-lookup"><span data-stu-id="63c27-109">DESCRIPTION</span></span>

<span data-ttu-id="63c27-110">`Remove-Service`Cmdlet은 레지스트리 및 서비스 데이터베이스에서 Windows 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-110">The `Remove-Service` cmdlet removes a Windows service in the registry and in the service database.</span></span>

<span data-ttu-id="63c27-111">`Remove-Service`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-111">The `Remove-Service` cmdlet was introduced in PowerShell 6.0.</span></span>

## <span data-ttu-id="63c27-112">예제</span><span class="sxs-lookup"><span data-stu-id="63c27-112">EXAMPLES</span></span>

### <span data-ttu-id="63c27-113">예제 1: 서비스 제거</span><span class="sxs-lookup"><span data-stu-id="63c27-113">Example 1: Remove a service</span></span>

<span data-ttu-id="63c27-114">그러면 TestService 라는 서비스가 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-114">This removes a service named TestService.</span></span>

```powershell
Remove-Service -Name "TestService"
```

### <span data-ttu-id="63c27-115">예 2: 표시 이름을 사용 하 여 서비스 제거</span><span class="sxs-lookup"><span data-stu-id="63c27-115">Example 2: Remove a service using the display name</span></span>

<span data-ttu-id="63c27-116">이 예제에서는 TestService 라는 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-116">This example removes a service named TestService.</span></span> <span data-ttu-id="63c27-117">명령을 사용 하 여 `Get-Service` 표시 이름을 사용 하는 TestService 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-117">The command uses `Get-Service` to get an object that represents the TestService service using the display name.</span></span> <span data-ttu-id="63c27-118">파이프라인 연산자 ( `|` )는 개체를로 파이프 하 여 `Remove-Service` 서비스를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-118">The pipeline operator (`|`) pipes the object to `Remove-Service`, which removes the service.</span></span>

```powershell
Get-Service -DisplayName "Test Service" | Remove-Service
```

## <span data-ttu-id="63c27-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="63c27-119">PARAMETERS</span></span>

### <span data-ttu-id="63c27-120">-InputObject</span><span class="sxs-lookup"><span data-stu-id="63c27-120">-InputObject</span></span>

<span data-ttu-id="63c27-121">제거할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-121">Specifies **ServiceController** objects that represent the services to remove.</span></span> <span data-ttu-id="63c27-122">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="63c27-122">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="63c27-123">-Name</span><span class="sxs-lookup"><span data-stu-id="63c27-123">-Name</span></span>

<span data-ttu-id="63c27-124">제거할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-124">Specifies the service names of the services to remove.</span></span> <span data-ttu-id="63c27-125">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-125">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="63c27-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="63c27-126">-Confirm</span></span>

<span data-ttu-id="63c27-127">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="63c27-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="63c27-128">-WhatIf</span></span>

<span data-ttu-id="63c27-129">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-129">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="63c27-130">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="63c27-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="63c27-131">CommonParameters</span></span>

<span data-ttu-id="63c27-132">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="63c27-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="63c27-133">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63c27-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="63c27-134">입력</span><span class="sxs-lookup"><span data-stu-id="63c27-134">INPUTS</span></span>

### <span data-ttu-id="63c27-135">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-135">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="63c27-136">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-136">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="63c27-137">출력</span><span class="sxs-lookup"><span data-stu-id="63c27-137">OUTPUTS</span></span>

### <span data-ttu-id="63c27-138">없음</span><span class="sxs-lookup"><span data-stu-id="63c27-138">None</span></span>

<span data-ttu-id="63c27-139">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-139">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="63c27-140">참고</span><span class="sxs-lookup"><span data-stu-id="63c27-140">NOTES</span></span>

<span data-ttu-id="63c27-141">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-141">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="63c27-142">이 cmdlet을 실행 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="63c27-142">To run this cmdlet, start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="63c27-143">관련 링크</span><span class="sxs-lookup"><span data-stu-id="63c27-143">RELATED LINKS</span></span>

[<span data-ttu-id="63c27-144">Get-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-144">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="63c27-145">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-145">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="63c27-146">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-146">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="63c27-147">Set-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-147">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="63c27-148">Start-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-148">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="63c27-149">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-149">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="63c27-150">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="63c27-150">Suspend-Service</span></span>](Suspend-Service.md)
