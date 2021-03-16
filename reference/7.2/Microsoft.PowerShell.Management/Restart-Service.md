---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: f88e07e36ec7c6adf7f24e2c6e57ae5864eb1a60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599756"
---
# <span data-ttu-id="e4ba1-102">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-102">Restart-Service</span></span>

## <span data-ttu-id="e4ba1-103">개요</span><span class="sxs-lookup"><span data-stu-id="e4ba1-103">SYNOPSIS</span></span>
<span data-ttu-id="e4ba1-104">하나 이상의 서비스를 중지한 다음 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-104">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="e4ba1-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4ba1-105">SYNTAX</span></span>

### <span data-ttu-id="e4ba1-106">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="e4ba1-106">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4ba1-107">기본값</span><span class="sxs-lookup"><span data-stu-id="e4ba1-107">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e4ba1-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e4ba1-108">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e4ba1-109">설명</span><span class="sxs-lookup"><span data-stu-id="e4ba1-109">DESCRIPTION</span></span>

<span data-ttu-id="e4ba1-110">`Restart-Service`Cmdlet은 지정 된 서비스에 대 한 중지 메시지를 Windows 서비스 컨트롤러로 보낸 다음 시작 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-110">The `Restart-Service` cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span> <span data-ttu-id="e4ba1-111">서비스가 이미 중지된 경우에는 오류 알림 없이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-111">If a service was already stopped, it is started without notifying you of an error.</span></span> <span data-ttu-id="e4ba1-112">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 다시 시작할 각 서비스를 나타내는 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="e4ba1-113">예제</span><span class="sxs-lookup"><span data-stu-id="e4ba1-113">EXAMPLES</span></span>

### <span data-ttu-id="e4ba1-114">예 1: 로컬 컴퓨터에서 서비스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="e4ba1-114">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="e4ba1-115">이 명령은 로컬 컴퓨터의 WMI(Windows Management Instrumentation)(WinMgmt) 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-115">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="e4ba1-116">예제 2: 서비스 제외</span><span class="sxs-lookup"><span data-stu-id="e4ba1-116">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="e4ba1-117">이 명령은 net Logon 서비스를 제외 하 고 Net으로 시작 하는 표시 이름이 있는 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-117">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="e4ba1-118">예 3: 중지 된 모든 네트워크 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="e4ba1-118">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="e4ba1-119">이 명령은 컴퓨터에서 중지된 모든 네트워크 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-119">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="e4ba1-120">이 명령은 cmdlet을 사용 하 여 `Get-Service` 서비스 이름이 net으로 시작 하는 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-120">This command uses the `Get-Service` cmdlet to get objects that represent the services whose service name starts with net.</span></span> <span data-ttu-id="e4ba1-121">파이프라인 연산자 ( `|` )는 서비스 개체를 cmdlet으로 보냅니다 `Where-Object` .이 cmdlet은 중지 됨 상태의 서비스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-121">The pipeline operator (`|`) sends the services object to the `Where-Object` cmdlet, which selects only the services that have a status of stopped.</span></span> <span data-ttu-id="e4ba1-122">다른 파이프라인 연산자가 선택한 서비스를로 보냅니다 `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="e4ba1-122">Another pipeline operator sends the selected services to `Restart-Service`.</span></span>

<span data-ttu-id="e4ba1-123">실제로 **WhatIf** 매개 변수를 사용 하 여 명령 실행 전에 명령 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-123">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="e4ba1-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4ba1-124">PARAMETERS</span></span>

### <span data-ttu-id="e4ba1-125">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="e4ba1-125">-DisplayName</span></span>

<span data-ttu-id="e4ba1-126">다시 시작할 서비스의 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-126">Specifies the display names of services to restarted.</span></span> <span data-ttu-id="e4ba1-127">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-127">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e4ba1-128">-제외</span><span class="sxs-lookup"><span data-stu-id="e4ba1-128">-Exclude</span></span>

<span data-ttu-id="e4ba1-129">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-129">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="e4ba1-130">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-130">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e4ba1-131">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-131">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="e4ba1-132">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-132">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e4ba1-133">-Force</span><span class="sxs-lookup"><span data-stu-id="e4ba1-133">-Force</span></span>

<span data-ttu-id="e4ba1-134">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-134">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e4ba1-135">-포함</span><span class="sxs-lookup"><span data-stu-id="e4ba1-135">-Include</span></span>

<span data-ttu-id="e4ba1-136">이 cmdlet이 다시 시작 되는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-136">Specifies services that this cmdlet restarts.</span></span> <span data-ttu-id="e4ba1-137">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-137">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="e4ba1-138">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-138">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="e4ba1-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e4ba1-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="e4ba1-140">-InputObject</span></span>

<span data-ttu-id="e4ba1-141">다시 시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-141">Specifies **ServiceController** objects that represent the services to restart.</span></span> <span data-ttu-id="e4ba1-142">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="e4ba1-143">-Name</span><span class="sxs-lookup"><span data-stu-id="e4ba1-143">-Name</span></span>

<span data-ttu-id="e4ba1-144">다시 시작할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-144">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="e4ba1-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="e4ba1-145">-PassThru</span></span>

<span data-ttu-id="e4ba1-146">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-146">Returns an object that represents the service.</span></span> <span data-ttu-id="e4ba1-147">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e4ba1-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e4ba1-148">-Confirm</span></span>

<span data-ttu-id="e4ba1-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e4ba1-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e4ba1-150">-WhatIf</span></span>

<span data-ttu-id="e4ba1-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-151">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e4ba1-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e4ba1-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4ba1-153">CommonParameters</span></span>

<span data-ttu-id="e4ba1-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4ba1-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4ba1-156">입력</span><span class="sxs-lookup"><span data-stu-id="e4ba1-156">INPUTS</span></span>

### <span data-ttu-id="e4ba1-157">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="e4ba1-158">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="e4ba1-159">출력</span><span class="sxs-lookup"><span data-stu-id="e4ba1-159">OUTPUTS</span></span>

### <span data-ttu-id="e4ba1-160">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="e4ba1-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="e4ba1-161">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 다시 시작 된 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="e4ba1-162">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e4ba1-163">참고</span><span class="sxs-lookup"><span data-stu-id="e4ba1-163">NOTES</span></span>

<span data-ttu-id="e4ba1-164">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-164">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="e4ba1-165">`Restart-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-165">`Restart-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="e4ba1-166">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-166">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="e4ba1-167">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면 "를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-167">To find the service names and display names of the services on your system, type `Get-Service`".</span></span>
  <span data-ttu-id="e4ba1-168">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="e4ba1-168">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="e4ba1-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e4ba1-169">RELATED LINKS</span></span>

[<span data-ttu-id="e4ba1-170">Get-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-170">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="e4ba1-171">New-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-171">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="e4ba1-172">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-172">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="e4ba1-173">Set-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-173">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="e4ba1-174">Start-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-174">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="e4ba1-175">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-175">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="e4ba1-176">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-176">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="e4ba1-177">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="e4ba1-177">Remove-Service</span></span>](Remove-Service.md)