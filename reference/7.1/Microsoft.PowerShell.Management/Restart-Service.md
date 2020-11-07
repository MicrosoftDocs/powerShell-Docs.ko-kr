---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/restart-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restart-Service
ms.openlocfilehash: fee113e20b178c2b86b8f95cd3147f991aed8efe
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346635"
---
# <span data-ttu-id="f28e4-103">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-103">Restart-Service</span></span>

## <span data-ttu-id="f28e4-104">개요</span><span class="sxs-lookup"><span data-stu-id="f28e4-104">SYNOPSIS</span></span>
<span data-ttu-id="f28e4-105">하나 이상의 서비스를 중지한 다음 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-105">Stops and then starts one or more services.</span></span>

## <span data-ttu-id="f28e4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f28e4-106">SYNTAX</span></span>

### <span data-ttu-id="f28e4-107">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="f28e4-107">InputObject (Default)</span></span>

```
Restart-Service [-Force] [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>]
 [-Exclude <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f28e4-108">기본값</span><span class="sxs-lookup"><span data-stu-id="f28e4-108">Default</span></span>

```
Restart-Service [-Force] [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f28e4-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f28e4-109">DisplayName</span></span>

```
Restart-Service [-Force] [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f28e4-110">설명</span><span class="sxs-lookup"><span data-stu-id="f28e4-110">DESCRIPTION</span></span>

<span data-ttu-id="f28e4-111">`Restart-Service`Cmdlet은 지정 된 서비스에 대 한 중지 메시지를 Windows 서비스 컨트롤러로 보낸 다음 시작 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-111">The `Restart-Service` cmdlet sends a stop message and then a start message to the Windows Service Controller for a specified service.</span></span> <span data-ttu-id="f28e4-112">서비스가 이미 중지된 경우에는 오류 알림 없이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-112">If a service was already stopped, it is started without notifying you of an error.</span></span> <span data-ttu-id="f28e4-113">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 다시 시작할 각 서비스를 나타내는 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-113">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to pass an object that represents each service that you want to restart.</span></span>

## <span data-ttu-id="f28e4-114">예제</span><span class="sxs-lookup"><span data-stu-id="f28e4-114">EXAMPLES</span></span>

### <span data-ttu-id="f28e4-115">예 1: 로컬 컴퓨터에서 서비스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="f28e4-115">Example 1: Restart a service on the local computer</span></span>

```powershell
PS C:\> Restart-Service -Name winmgmt
```

<span data-ttu-id="f28e4-116">이 명령은 로컬 컴퓨터의 WMI(Windows Management Instrumentation)(WinMgmt) 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-116">This command restarts the Windows Management Instrumentation service (WinMgmt) on the local computer.</span></span>

### <span data-ttu-id="f28e4-117">예제 2: 서비스 제외</span><span class="sxs-lookup"><span data-stu-id="f28e4-117">Example 2: Exclude a service</span></span>

```powershell
PS C:\> Restart-Service -DisplayName "net*" -Exclude "net logon"
```

<span data-ttu-id="f28e4-118">이 명령은 net Logon 서비스를 제외 하 고 Net으로 시작 하는 표시 이름이 있는 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-118">This command restarts the services that have a display name that starts with Net, except for the Net Logon service.</span></span>

### <span data-ttu-id="f28e4-119">예 3: 중지 된 모든 네트워크 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="f28e4-119">Example 3: Start all stopped network services</span></span>

```powershell
PS C:\> Get-Service -Name "net*" | Where-Object {$_.Status -eq "Stopped"} | Restart-Service
```

<span data-ttu-id="f28e4-120">이 명령은 컴퓨터에서 중지된 모든 네트워크 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-120">This command starts all of the stopped network services on the computer.</span></span>

<span data-ttu-id="f28e4-121">이 명령은 cmdlet을 사용 하 여 `Get-Service` 서비스 이름이 net으로 시작 하는 서비스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-121">This command uses the `Get-Service` cmdlet to get objects that represent the services whose service name starts with net.</span></span> <span data-ttu-id="f28e4-122">파이프라인 연산자 ( `|` )는 서비스 개체를 cmdlet으로 보냅니다 `Where-Object` .이 cmdlet은 중지 됨 상태의 서비스만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-122">The pipeline operator (`|`) sends the services object to the `Where-Object` cmdlet, which selects only the services that have a status of stopped.</span></span> <span data-ttu-id="f28e4-123">다른 파이프라인 연산자가 선택한 서비스를로 보냅니다 `Restart-Service` .</span><span class="sxs-lookup"><span data-stu-id="f28e4-123">Another pipeline operator sends the selected services to `Restart-Service`.</span></span>

<span data-ttu-id="f28e4-124">실제로 **WhatIf** 매개 변수를 사용 하 여 명령 실행 전에 명령 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-124">In practice, you would use the **WhatIf** parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="f28e4-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f28e4-125">PARAMETERS</span></span>

### <span data-ttu-id="f28e4-126">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="f28e4-126">-DisplayName</span></span>

<span data-ttu-id="f28e4-127">다시 시작할 서비스의 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-127">Specifies the display names of services to restarted.</span></span> <span data-ttu-id="f28e4-128">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-128">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f28e4-129">-제외</span><span class="sxs-lookup"><span data-stu-id="f28e4-129">-Exclude</span></span>

<span data-ttu-id="f28e4-130">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-130">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="f28e4-131">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-131">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="f28e4-132">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-132">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="f28e4-133">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-133">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f28e4-134">-Force</span><span class="sxs-lookup"><span data-stu-id="f28e4-134">-Force</span></span>

<span data-ttu-id="f28e4-135">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-135">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f28e4-136">-포함</span><span class="sxs-lookup"><span data-stu-id="f28e4-136">-Include</span></span>

<span data-ttu-id="f28e4-137">이 cmdlet이 다시 시작 되는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-137">Specifies services that this cmdlet restarts.</span></span> <span data-ttu-id="f28e4-138">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-138">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="f28e4-139">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-139">Enter a name element or pattern, such as s\*.</span></span> <span data-ttu-id="f28e4-140">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f28e4-141">-InputObject</span><span class="sxs-lookup"><span data-stu-id="f28e4-141">-InputObject</span></span>

<span data-ttu-id="f28e4-142">다시 시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-142">Specifies **ServiceController** objects that represent the services to restart.</span></span> <span data-ttu-id="f28e4-143">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="f28e4-143">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="f28e4-144">-Name</span><span class="sxs-lookup"><span data-stu-id="f28e4-144">-Name</span></span>

<span data-ttu-id="f28e4-145">다시 시작할 서비스의 서비스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-145">Specifies the service names of the services to restart.</span></span>

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

### <span data-ttu-id="f28e4-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f28e4-146">-PassThru</span></span>

<span data-ttu-id="f28e4-147">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-147">Returns an object that represents the service.</span></span> <span data-ttu-id="f28e4-148">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f28e4-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f28e4-149">-Confirm</span></span>

<span data-ttu-id="f28e4-150">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f28e4-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f28e4-151">-WhatIf</span></span>

<span data-ttu-id="f28e4-152">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-152">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f28e4-153">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f28e4-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f28e4-154">CommonParameters</span></span>

<span data-ttu-id="f28e4-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f28e4-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f28e4-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f28e4-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f28e4-157">입력</span><span class="sxs-lookup"><span data-stu-id="f28e4-157">INPUTS</span></span>

### <span data-ttu-id="f28e4-158">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-158">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="f28e4-159">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-159">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="f28e4-160">출력</span><span class="sxs-lookup"><span data-stu-id="f28e4-160">OUTPUTS</span></span>

### <span data-ttu-id="f28e4-161">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="f28e4-161">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="f28e4-162">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 다시 시작 된 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-162">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the restarted service, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f28e4-163">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f28e4-164">참고</span><span class="sxs-lookup"><span data-stu-id="f28e4-164">NOTES</span></span>

<span data-ttu-id="f28e4-165">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-165">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="f28e4-166">`Restart-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-166">`Restart-Service` can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="f28e4-167">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-167">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="f28e4-168">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면 "를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-168">To find the service names and display names of the services on your system, type `Get-Service`".</span></span>
  <span data-ttu-id="f28e4-169">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="f28e4-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="f28e4-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f28e4-170">RELATED LINKS</span></span>

[<span data-ttu-id="f28e4-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="f28e4-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="f28e4-173">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-173">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="f28e4-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="f28e4-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="f28e4-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="f28e4-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="f28e4-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="f28e4-178">Remove-Service</span></span>](Remove-Service.md)
