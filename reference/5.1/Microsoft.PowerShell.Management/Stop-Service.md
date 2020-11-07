---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-service?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Service
ms.openlocfilehash: 77ce507d0eaf476e2c24f41e433bd69fdcb416bb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94342572"
---
# <span data-ttu-id="10678-103">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="10678-103">Stop-Service</span></span>

## <span data-ttu-id="10678-104">개요</span><span class="sxs-lookup"><span data-stu-id="10678-104">SYNOPSIS</span></span>
<span data-ttu-id="10678-105">실행 중인 하나 이상의 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-105">Stops one or more running services.</span></span>

## <span data-ttu-id="10678-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="10678-106">SYNTAX</span></span>

### <span data-ttu-id="10678-107">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="10678-107">InputObject (Default)</span></span>

```
Stop-Service [-Force] [-NoWait] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="10678-108">기본값</span><span class="sxs-lookup"><span data-stu-id="10678-108">Default</span></span>

```
Stop-Service [-Force] [-NoWait] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="10678-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="10678-109">DisplayName</span></span>

```
Stop-Service [-Force] [-NoWait] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="10678-110">설명</span><span class="sxs-lookup"><span data-stu-id="10678-110">DESCRIPTION</span></span>

<span data-ttu-id="10678-111">`Stop-Service`Cmdlet은 지정 된 각 서비스에 대 한 중지 메시지를 Windows 서비스 컨트롤러로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="10678-111">The `Stop-Service` cmdlet sends a stop message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="10678-112">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 중지할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass a service object that represents the service that you want to stop.</span></span>

## <span data-ttu-id="10678-113">예제</span><span class="sxs-lookup"><span data-stu-id="10678-113">EXAMPLES</span></span>

### <span data-ttu-id="10678-114">예 1: 로컬 컴퓨터에서 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="10678-114">Example 1: Stop a service on the local computer</span></span>

```
PS C:\> Stop-Service -Name "sysmonlog"
```

<span data-ttu-id="10678-115">이 명령은 로컬 컴퓨터의 성능 로그 및 알림(SysmonLog) 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-115">This command stops the Performance Logs and Alerts (SysmonLog) service on the local computer.</span></span>

### <span data-ttu-id="10678-116">예 2: 표시 이름을 사용 하 여 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="10678-116">Example 2: Stop a service by using the display name</span></span>

```
PS C:\> Get-Service -DisplayName "telnet" | Stop-Service
```

<span data-ttu-id="10678-117">이 명령은 로컬 컴퓨터의 텔넷 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-117">This command stops the Telnet service on the local computer.</span></span> <span data-ttu-id="10678-118">명령은를 사용 `Get-Service` 하 여 텔넷 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10678-118">The command uses `Get-Service` to get an object that represents the Telnet service.</span></span> <span data-ttu-id="10678-119">파이프라인 연산자 ( `|` )는 개체를로 파이프 하 여 `Stop-Service` 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-119">The pipeline operator (`|`) pipes the object to `Stop-Service`, which stops the service.</span></span>

### <span data-ttu-id="10678-120">예 3: 종속 서비스를 포함 하는 서비스 중지</span><span class="sxs-lookup"><span data-stu-id="10678-120">Example 3: Stop a service that has dependent services</span></span>

```
PS C:\> Get-Service -Name "iisadmin" | Format-List -Property Name, DependentServices
PS C:\> Stop-Service -Name "iisadmin" -Force -Confirm
```

<span data-ttu-id="10678-121">이 예에서는 로컬 컴퓨터의 IISAdmin 서비스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-121">This example stops the IISAdmin service on the local computer.</span></span> <span data-ttu-id="10678-122">이 서비스를 중지 하면 IISAdmin 서비스에 종속 된 서비스도 중지 되므로 `Stop-Service` iisadmin 서비스에 종속 된 서비스를 나열 하는 명령 앞에를 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-122">Because stopping this service also stops the services that depend on the IISAdmin service, it is best to precede `Stop-Service` with a command that lists the services that depend on the IISAdmin service.</span></span>

<span data-ttu-id="10678-123">첫 번째 명령은 IISAdmin에 종속된 서비스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-123">The first command lists the services that depend on IISAdmin.</span></span> <span data-ttu-id="10678-124">을 사용 `Get-Service` 하 여 IISAdmin 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="10678-124">It uses `Get-Service` to get an object that represents the IISAdmin service.</span></span> <span data-ttu-id="10678-125">파이프라인 연산자 ( `|` )는 결과를 cmdlet으로 전달 합니다 `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="10678-125">The pipeline operator (`|`) passes the result to the `Format-List` cmdlet.</span></span> <span data-ttu-id="10678-126">이 명령은의 **Property** 매개 변수를 사용 하 여 `Format-List` 서비스의 **Name** 및 **DependentServices** 속성만 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-126">The command uses the **Property** parameter of `Format-List` to list only the **Name** and **DependentServices** properties of the service.</span></span>

<span data-ttu-id="10678-127">두 번째 명령은 IISAdmin 서비스를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-127">The second command stops the IISAdmin service.</span></span> <span data-ttu-id="10678-128">**Force** 매개 변수는 종속 서비스가 있는 서비스를 중지 하는 데 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-128">The **Force** parameter is required to stop a service that has dependent services.</span></span> <span data-ttu-id="10678-129">이 명령은 **Confirm** 매개 변수를 사용 하 여 각 서비스를 중지 하기 전에 사용자의 확인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-129">The command uses the **Confirm** parameter to request confirmation from the user before it stops each service.</span></span>

## <span data-ttu-id="10678-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="10678-130">PARAMETERS</span></span>

### <span data-ttu-id="10678-131">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="10678-131">-DisplayName</span></span>

<span data-ttu-id="10678-132">중지할 서비스의 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-132">Specifies the display names of the services to stop.</span></span>
<span data-ttu-id="10678-133">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="10678-134">-제외</span><span class="sxs-lookup"><span data-stu-id="10678-134">-Exclude</span></span>

<span data-ttu-id="10678-135">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-135">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="10678-136">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-136">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="10678-137">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-137">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="10678-138">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-138">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="10678-139">-Force</span><span class="sxs-lookup"><span data-stu-id="10678-139">-Force</span></span>

<span data-ttu-id="10678-140">서비스가 종속 된 서비스를 포함 하는 경우에도 cmdlet이 서비스를 중지 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-140">Forces the cmdlet to stop a service even if that service has dependent services.</span></span>

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

### <span data-ttu-id="10678-141">-포함</span><span class="sxs-lookup"><span data-stu-id="10678-141">-Include</span></span>

<span data-ttu-id="10678-142">이 cmdlet이 중지 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-142">Specifies services that this cmdlet stops.</span></span> <span data-ttu-id="10678-143">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="10678-144">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-144">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="10678-145">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="10678-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="10678-146">-InputObject</span></span>

<span data-ttu-id="10678-147">중지할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-147">Specifies **ServiceController** objects that represent the services to stop.</span></span> <span data-ttu-id="10678-148">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="10678-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="10678-149">-Name</span><span class="sxs-lookup"><span data-stu-id="10678-149">-Name</span></span>

<span data-ttu-id="10678-150">중지할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-150">Specifies the service names of the services to stop.</span></span> <span data-ttu-id="10678-151">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-151">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="10678-152">-NoWait</span><span class="sxs-lookup"><span data-stu-id="10678-152">-NoWait</span></span>

<span data-ttu-id="10678-153">이 cmdlet이 대기 안 함 옵션을 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="10678-153">Indicates that this cmdlet uses the no wait option.</span></span>

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

### <span data-ttu-id="10678-154">-PassThru</span><span class="sxs-lookup"><span data-stu-id="10678-154">-PassThru</span></span>

<span data-ttu-id="10678-155">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-155">Returns an object that represents the service.</span></span> <span data-ttu-id="10678-156">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-156">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="10678-157">-Confirm</span><span class="sxs-lookup"><span data-stu-id="10678-157">-Confirm</span></span>

<span data-ttu-id="10678-158">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-158">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="10678-159">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="10678-159">-WhatIf</span></span>

<span data-ttu-id="10678-160">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-160">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="10678-161">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-161">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="10678-162">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="10678-162">CommonParameters</span></span>

<span data-ttu-id="10678-163">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="10678-163">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="10678-164">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10678-164">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="10678-165">입력</span><span class="sxs-lookup"><span data-stu-id="10678-165">INPUTS</span></span>

### <span data-ttu-id="10678-166">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="10678-166">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="10678-167">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-167">You can pipe a service object or a string that contains the name of a service to this cmdlet.</span></span>

## <span data-ttu-id="10678-168">출력</span><span class="sxs-lookup"><span data-stu-id="10678-168">OUTPUTS</span></span>

### <span data-ttu-id="10678-169">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="10678-169">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="10678-170">이 cmdlet은 **PassThru** 매개 변수를 사용 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-170">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you use the **PassThru** parameter.</span></span> <span data-ttu-id="10678-171">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-171">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="10678-172">참고</span><span class="sxs-lookup"><span data-stu-id="10678-172">NOTES</span></span>

<span data-ttu-id="10678-173">`Stop-Service`기본 제공 별칭인 **spsv** 로 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-173">You can also refer to `Stop-Service` by its built-in alias, **spsv**.</span></span> <span data-ttu-id="10678-174">자세한 내용은 about_Aliases를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="10678-174">For more information, see about_Aliases.</span></span>

<span data-ttu-id="10678-175">`Stop-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-175">`Stop-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="10678-176">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10678-176">If a command does not work correctly, you might not have the required permissions.</span></span>

<span data-ttu-id="10678-177">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="10678-177">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="10678-178">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="10678-178">The service names appear in the **Name** column and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="10678-179">관련 링크</span><span class="sxs-lookup"><span data-stu-id="10678-179">RELATED LINKS</span></span>

[<span data-ttu-id="10678-180">Get-Service</span><span class="sxs-lookup"><span data-stu-id="10678-180">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="10678-181">New-Service</span><span class="sxs-lookup"><span data-stu-id="10678-181">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="10678-182">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="10678-182">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="10678-183">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="10678-183">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="10678-184">Set-Service</span><span class="sxs-lookup"><span data-stu-id="10678-184">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="10678-185">Start-Service</span><span class="sxs-lookup"><span data-stu-id="10678-185">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="10678-186">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="10678-186">Suspend-Service</span></span>](Suspend-Service.md)
