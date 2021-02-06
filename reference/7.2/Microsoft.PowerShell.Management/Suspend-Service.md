---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/suspend-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Suspend-Service
ms.openlocfilehash: 9515f524df38813817b3fefd1437a3e2df296392
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602818"
---
# <span data-ttu-id="aad34-102">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-102">Suspend-Service</span></span>

## <span data-ttu-id="aad34-103">개요</span><span class="sxs-lookup"><span data-stu-id="aad34-103">SYNOPSIS</span></span>
<span data-ttu-id="aad34-104">실행 중인 하나 이상의 서비스를 일시 중단(일시 중지)합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-104">Suspends (pauses) one or more running services.</span></span>

## <span data-ttu-id="aad34-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="aad34-105">SYNTAX</span></span>

### <span data-ttu-id="aad34-106">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="aad34-106">InputObject (Default)</span></span>

```
Suspend-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="aad34-107">기본값</span><span class="sxs-lookup"><span data-stu-id="aad34-107">Default</span></span>

```
Suspend-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="aad34-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="aad34-108">DisplayName</span></span>

```
Suspend-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="aad34-109">설명</span><span class="sxs-lookup"><span data-stu-id="aad34-109">DESCRIPTION</span></span>

<span data-ttu-id="aad34-110">`Suspend-Service`Cmdlet은 지정 된 각 서비스에 대 한 일시 중단 메시지를 Windows 서비스 컨트롤러로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-110">The `Suspend-Service` cmdlet sends a suspend message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="aad34-111">일시 중단 된 동안 서비스는 계속 실행 되지만 사용 cmdlet 등의 작업은 다시 시작할 때까지 중지 됩니다 `Resume-Service` .</span><span class="sxs-lookup"><span data-stu-id="aad34-111">While suspended, the service is still running, but its action is stopped until resumed, such as by usingthe `Resume-Service` cmdlet.</span></span> <span data-ttu-id="aad34-112">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 일시 중단할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the services that you want to suspend.</span></span>

## <span data-ttu-id="aad34-113">예제</span><span class="sxs-lookup"><span data-stu-id="aad34-113">EXAMPLES</span></span>

### <span data-ttu-id="aad34-114">예제 1: 서비스 일시 중단</span><span class="sxs-lookup"><span data-stu-id="aad34-114">Example 1: Suspend a service</span></span>

```
PS C:\> Suspend-Service -DisplayName "Telnet"
```

<span data-ttu-id="aad34-115">이 명령은 로컬 컴퓨터의 텔넷 서비스(Tlntsvr)를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-115">This command suspends the Telnet service (Tlntsvr) service on the local computer.</span></span>

### <span data-ttu-id="aad34-116">예 2: 서비스를 일시 중단할 경우 발생 하는 상황 표시</span><span class="sxs-lookup"><span data-stu-id="aad34-116">Example 2: Display what would happen if you suspend services</span></span>

```
PS C:\> Suspend-Service -Name lanman* -WhatIf
```

<span data-ttu-id="aad34-117">이 명령은 서비스 이름이 lanman로 시작 하는 서비스를 일시 중지 한 경우 발생 하는 상황을 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-117">This command tells what would happen if you suspended the services that have a service name that starts with lanman.</span></span> <span data-ttu-id="aad34-118">서비스를 일시 중단 하려면 **WhatIf** 매개 변수 없이 명령을 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-118">To suspend the services, rerun the command without the **WhatIf** parameter.</span></span>

### <span data-ttu-id="aad34-119">예제 3: 서비스 가져오기 및 일시 중단</span><span class="sxs-lookup"><span data-stu-id="aad34-119">Example 3: Get and suspend a service</span></span>

```
PS C:\> Get-Service schedule | Suspend-Service
```

<span data-ttu-id="aad34-120">이 명령은 cmdlet을 사용 하 여 `Get-Service` 컴퓨터의 작업 스케줄러 (Schedule) 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-120">This command uses the `Get-Service` cmdlet to get an object that represents the Task Scheduler (Schedule) service on the computer.</span></span> <span data-ttu-id="aad34-121">파이프라인 연산자 ( `|` )는 결과를에 전달 하 여 서비스를 `Suspend-Service` 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-121">The pipeline operator (`|`) passes the result to `Suspend-Service`, which suspends the service.</span></span>

### <span data-ttu-id="aad34-122">예제 4: 일시 중단할 수 있는 모든 서비스 일시 중단</span><span class="sxs-lookup"><span data-stu-id="aad34-122">Example 4: Suspend all services that can be suspended</span></span>

```
PS C:\> Get-Service | Where-Object {$_.CanPauseAndContinue -eq "True"} | Suspend-Service -Confirm
```

<span data-ttu-id="aad34-123">이 명령은 일시 중단할 수 있는 컴퓨터의 모든 서비스를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-123">This command suspends all of the services on the computer that can be suspended.</span></span> <span data-ttu-id="aad34-124">를 사용 `Get-Service` 하 여 컴퓨터의 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-124">It uses `Get-Service` to get objects that represent the services on the computer.</span></span> <span data-ttu-id="aad34-125">파이프라인 연산자는 결과를 cmdlet으로 전달 합니다 `Where-Object` .이 cmdlet은 `$True` **Canpauseandcontinue** 속성의 값이 인 서비스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-125">The pipeline operator passes the results to the `Where-Object` cmdlet, which selects only the services that have a value of `$True` for the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="aad34-126">다른 파이프라인 연산자는 결과를에 전달 `Suspend-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-126">Another pipeline operator passes the results to `Suspend-Service`.</span></span> <span data-ttu-id="aad34-127">**Confirm** 매개 변수는 각 서비스를 일시 중단 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-127">The **Confirm** parameter prompts you for confirmation before suspending each of the services.</span></span>

## <span data-ttu-id="aad34-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="aad34-128">PARAMETERS</span></span>

### <span data-ttu-id="aad34-129">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="aad34-129">-DisplayName</span></span>

<span data-ttu-id="aad34-130">일시 중단할 서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-130">Specifies the display names of the services to be suspended.</span></span> <span data-ttu-id="aad34-131">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-131">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="aad34-132">-제외</span><span class="sxs-lookup"><span data-stu-id="aad34-132">-Exclude</span></span>

<span data-ttu-id="aad34-133">지정 된 서비스에서 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-133">Specifies services to omit from the specified services.</span></span> <span data-ttu-id="aad34-134">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-134">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="aad34-135">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-135">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="aad34-136">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-136">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="aad34-137">-포함</span><span class="sxs-lookup"><span data-stu-id="aad34-137">-Include</span></span>

<span data-ttu-id="aad34-138">일시 중단할 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-138">Specifies services to suspend.</span></span> <span data-ttu-id="aad34-139">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-139">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="aad34-140">이름 요소 또는 패턴(예: "*s*")을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-140">Enter a name element or pattern, such as "s\*".</span></span> <span data-ttu-id="aad34-141">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-141">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="aad34-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="aad34-142">-InputObject</span></span>

<span data-ttu-id="aad34-143">일시 중단할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-143">Specifies **ServiceController** objects that represent the services to suspend.</span></span> <span data-ttu-id="aad34-144">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="aad34-144">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="aad34-145">-Name</span><span class="sxs-lookup"><span data-stu-id="aad34-145">-Name</span></span>

<span data-ttu-id="aad34-146">일시 중단할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-146">Specifies the service names of the services to suspend.</span></span> <span data-ttu-id="aad34-147">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-147">Wildcard characters are permitted.</span></span>

<span data-ttu-id="aad34-148">매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-148">The parameter name is optional.</span></span> <span data-ttu-id="aad34-149">**이름** 또는 별칭, **ServiceName** 을 사용 하거나 매개 변수 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-149">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: ServiceName

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="aad34-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="aad34-150">-PassThru</span></span>

<span data-ttu-id="aad34-151">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-151">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="aad34-152">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="aad34-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="aad34-153">-Confirm</span></span>

<span data-ttu-id="aad34-154">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="aad34-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="aad34-155">-WhatIf</span></span>

<span data-ttu-id="aad34-156">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="aad34-157">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="aad34-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="aad34-158">CommonParameters</span></span>

<span data-ttu-id="aad34-159">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="aad34-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="aad34-160">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aad34-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="aad34-161">입력</span><span class="sxs-lookup"><span data-stu-id="aad34-161">INPUTS</span></span>

### <span data-ttu-id="aad34-162">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-162">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="aad34-163">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-163">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="aad34-164">출력</span><span class="sxs-lookup"><span data-stu-id="aad34-164">OUTPUTS</span></span>

### <span data-ttu-id="aad34-165">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="aad34-165">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="aad34-166">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-166">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="aad34-167">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="aad34-168">참고</span><span class="sxs-lookup"><span data-stu-id="aad34-168">NOTES</span></span>

<span data-ttu-id="aad34-169">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-169">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="aad34-170">`Suspend-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-170">`Suspend-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="aad34-171">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-171">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="aad34-172">`Suspend-Service` 는 일시 중단 및 다시 시작을 지 원하는 서비스만 일시 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-172">`Suspend-Service` can suspend only services that support being suspended and resumed.</span></span> <span data-ttu-id="aad34-173">특정 서비스를 일시 중단할 수 있는지 확인 하려면 `Get-Service` **Canpauseandcontinue** 속성과 함께 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-173">To determine whether a particular service can be suspended, use the `Get-Service` cmdlet together with the **CanPauseAndContinue** property.</span></span> <span data-ttu-id="aad34-174">예를 들어 `Get-Service wmi | Format-List Name, CanPauseAndContinue`입니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-174">For example, `Get-Service wmi | Format-List Name, CanPauseAndContinue`.</span></span> <span data-ttu-id="aad34-175">일시 중단할 수 있는 컴퓨터의 모든 서비스를 찾으려면를 입력 `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-175">To find all services on the computer that can be suspended, type `Get-Service | Where-Object {$_.CanPauseAndContinue -eq $true}`.</span></span>
- <span data-ttu-id="aad34-176">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-176">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="aad34-177">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="aad34-177">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="aad34-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="aad34-178">RELATED LINKS</span></span>

[<span data-ttu-id="aad34-179">Get-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-179">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="aad34-180">New-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-180">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="aad34-181">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-181">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="aad34-182">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-182">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="aad34-183">Set-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-183">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="aad34-184">Start-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-184">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="aad34-185">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-185">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="aad34-186">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="aad34-186">Remove-Service</span></span>](Remove-Service.md)
