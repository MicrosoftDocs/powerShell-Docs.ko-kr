---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: 8ce2182117167d93c8f7abd86eeb2c79abdf09c8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599960"
---
# <span data-ttu-id="17f6e-102">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-102">Resume-Service</span></span>

## <span data-ttu-id="17f6e-103">개요</span><span class="sxs-lookup"><span data-stu-id="17f6e-103">SYNOPSIS</span></span>
<span data-ttu-id="17f6e-104">하나 이상의 일시 중단(일시 중지)된 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-104">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="17f6e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="17f6e-105">SYNTAX</span></span>

### <span data-ttu-id="17f6e-106">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="17f6e-106">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="17f6e-107">기본값</span><span class="sxs-lookup"><span data-stu-id="17f6e-107">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="17f6e-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="17f6e-108">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="17f6e-109">설명</span><span class="sxs-lookup"><span data-stu-id="17f6e-109">DESCRIPTION</span></span>

<span data-ttu-id="17f6e-110">`Resume-Service`Cmdlet은 지정 된 각 서비스에 대 한 다시 시작 메시지를 Windows 서비스 컨트롤러로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-110">The `Resume-Service` cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="17f6e-111">일시 중단 된 서비스는 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-111">If a service is suspended, it resumes.</span></span> <span data-ttu-id="17f6e-112">현재 실행 중인 경우에는 메시지가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-112">If it is currently running, the message is ignored.</span></span> <span data-ttu-id="17f6e-113">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 다시 시작할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="17f6e-114">예제</span><span class="sxs-lookup"><span data-stu-id="17f6e-114">EXAMPLES</span></span>

### <span data-ttu-id="17f6e-115">예 1: 로컬 컴퓨터에서 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-115">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="17f6e-116">이 명령은 로컬 컴퓨터에서 시스템 이벤트 알림 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-116">This command resumes the System Event Notification service on the local computer.</span></span> <span data-ttu-id="17f6e-117">서비스 이름은 sens으로 명령에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-117">The service name is represented in the command by sens.</span></span> <span data-ttu-id="17f6e-118">이 명령은 **name** 매개 변수를 사용 하 여 서비스의 서비스 이름을 지정 합니다. 그러나 매개 변수 이름은 선택 사항 이므로이 명령은 매개 변수 이름을 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-118">The command uses the **Name** parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="17f6e-119">예제 2: 모든 일시 중단 된 서비스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="17f6e-119">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="17f6e-120">이 명령은 컴퓨터에서 일시 중단 된 모든 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-120">This command resumes all of the suspended services on the computer.</span></span> <span data-ttu-id="17f6e-121">`Get-Service`Cmdlet 명령은 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-121">The `Get-Service` cmdlet command gets all of the services on the computer.</span></span> <span data-ttu-id="17f6e-122">파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Where-Object` .이 Cmdlet은 **상태** 속성이 일시 중지 됨 인 서비스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-122">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects the services that have a **Status** property of Paused.</span></span> <span data-ttu-id="17f6e-123">다음 파이프라인 연산자는 `Resume-Service` 일시 중지 된 서비스를 다시 시작 하는에 결과를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-123">The next pipeline operator sends the results to `Resume-Service`, which resumes the paused services.</span></span>

<span data-ttu-id="17f6e-124">실제로 **WhatIf** 매개 변수를 사용 하 여 명령 실행 전에 명령 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="17f6e-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="17f6e-125">PARAMETERS</span></span>

### <span data-ttu-id="17f6e-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="17f6e-126">-DisplayName</span></span>

<span data-ttu-id="17f6e-127">다시 시작할 서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-127">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="17f6e-128">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-128">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DisplayName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17f6e-129">-제외</span><span class="sxs-lookup"><span data-stu-id="17f6e-129">-Exclude</span></span>

<span data-ttu-id="17f6e-130">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="17f6e-131">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="17f6e-132">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="17f6e-133">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-133">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17f6e-134">-포함</span><span class="sxs-lookup"><span data-stu-id="17f6e-134">-Include</span></span>

<span data-ttu-id="17f6e-135">다시 시작할 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-135">Specifies services to resume.</span></span> <span data-ttu-id="17f6e-136">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-136">The value of this parameter qualifies **Name** parameter.</span></span> <span data-ttu-id="17f6e-137">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="17f6e-138">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-138">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="17f6e-139">-InputObject</span><span class="sxs-lookup"><span data-stu-id="17f6e-139">-InputObject</span></span>

<span data-ttu-id="17f6e-140">다시 시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-140">Specifies **ServiceController** objects that represent the services to resumed.</span></span> <span data-ttu-id="17f6e-141">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="17f6e-141">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.ServiceProcess.ServiceController[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17f6e-142">-Name</span><span class="sxs-lookup"><span data-stu-id="17f6e-142">-Name</span></span>

<span data-ttu-id="17f6e-143">다시 시작할 서비스의 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-143">Specifies the service names of the services to be resumed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="17f6e-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="17f6e-144">-PassThru</span></span>

<span data-ttu-id="17f6e-145">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-145">Returns an object that represents the service.</span></span> <span data-ttu-id="17f6e-146">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-146">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="17f6e-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="17f6e-147">-Confirm</span></span>

<span data-ttu-id="17f6e-148">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="17f6e-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="17f6e-149">-WhatIf</span></span>

<span data-ttu-id="17f6e-150">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="17f6e-151">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-151">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="17f6e-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="17f6e-152">CommonParameters</span></span>

<span data-ttu-id="17f6e-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="17f6e-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="17f6e-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="17f6e-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="17f6e-155">입력</span><span class="sxs-lookup"><span data-stu-id="17f6e-155">INPUTS</span></span>

### <span data-ttu-id="17f6e-156">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-156">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="17f6e-157">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-157">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="17f6e-158">출력</span><span class="sxs-lookup"><span data-stu-id="17f6e-158">OUTPUTS</span></span>

### <span data-ttu-id="17f6e-159">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="17f6e-159">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="17f6e-160">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 다시 시작 된 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-160">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="17f6e-161">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-161">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="17f6e-162">참고</span><span class="sxs-lookup"><span data-stu-id="17f6e-162">NOTES</span></span>

<span data-ttu-id="17f6e-163">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-163">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="17f6e-164">일시 중단 된 서비스의 상태가 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="17f6e-165">서비스가 다시 시작 되 면 상태는 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-165">When services are resumed, their status is Running.</span></span>
- <span data-ttu-id="17f6e-166">`Resume-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-166">`Resume-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="17f6e-167">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="17f6e-168">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="17f6e-169">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="17f6e-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="17f6e-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="17f6e-170">RELATED LINKS</span></span>

[<span data-ttu-id="17f6e-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="17f6e-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="17f6e-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="17f6e-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="17f6e-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="17f6e-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="17f6e-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="17f6e-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="17f6e-178">Remove-Service</span></span>](Remove-Service.md)