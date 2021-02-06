---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-service?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Service
ms.openlocfilehash: b1df4490da501111ccb44dea2645a333fdf5c27e
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601268"
---
# <span data-ttu-id="41574-102">Start-Service</span><span class="sxs-lookup"><span data-stu-id="41574-102">Start-Service</span></span>

## <span data-ttu-id="41574-103">개요</span><span class="sxs-lookup"><span data-stu-id="41574-103">SYNOPSIS</span></span>
<span data-ttu-id="41574-104">하나 이상의 중지된 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-104">Starts one or more stopped services.</span></span>

## <span data-ttu-id="41574-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41574-105">SYNTAX</span></span>

### <span data-ttu-id="41574-106">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="41574-106">InputObject (Default)</span></span>

```
Start-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="41574-107">기본값</span><span class="sxs-lookup"><span data-stu-id="41574-107">Default</span></span>

```
Start-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="41574-108">DisplayName</span><span class="sxs-lookup"><span data-stu-id="41574-108">DisplayName</span></span>

```
Start-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="41574-109">설명</span><span class="sxs-lookup"><span data-stu-id="41574-109">DESCRIPTION</span></span>

<span data-ttu-id="41574-110">`Start-Service`Cmdlet은 지정 된 각 서비스에 대 한 시작 메시지를 Windows 서비스 컨트롤러로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41574-110">The `Start-Service` cmdlet sends a start message to the Windows Service Controller for each of the specified services.</span></span> <span data-ttu-id="41574-111">서비스가 이미 실행 중인 경우에는 오류 없이 메시지가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="41574-111">If a service is already running, the message is ignored without error.</span></span> <span data-ttu-id="41574-112">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 **InputObject** 매개 변수를 사용 하 여 시작 하려는 서비스를 나타내는 서비스 개체를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-112">You can specify the services by their service names or display names, or you can use the **InputObject** parameter to supply a service object that represents the services that you want to start.</span></span>

## <span data-ttu-id="41574-113">예제</span><span class="sxs-lookup"><span data-stu-id="41574-113">EXAMPLES</span></span>

### <span data-ttu-id="41574-114">예제 1: 이름을 사용 하 여 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="41574-114">Example 1: Start a service by using its name</span></span>

<span data-ttu-id="41574-115">이 예에서는 로컬 컴퓨터에서 EventLog 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-115">This example starts the EventLog service on the local computer.</span></span> <span data-ttu-id="41574-116">**Name** 매개 변수는 서비스 이름으로 서비스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-116">The **Name** parameter identifies the service by its service name.</span></span>

```powershell
Start-Service -Name "eventlog"
```

### <span data-ttu-id="41574-117">예제 2: 서비스를 시작 하지 않고 정보 표시</span><span class="sxs-lookup"><span data-stu-id="41574-117">Example 2: Display information without starting a service</span></span>

<span data-ttu-id="41574-118">이 예에서는 "remote"를 포함 하는 표시 이름이 있는 서비스를 시작한 경우 발생 하는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41574-118">This example shows what would occur if you started the services that have a display name that includes "remote".</span></span>

```powershell
Start-Service -DisplayName *remote* -WhatIf
```

<span data-ttu-id="41574-119">**DisplayName** 매개 변수는 서비스 이름 대신 표시 이름으로 서비스를 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-119">The **DisplayName** parameter identifies the services by their display name instead of their service name.</span></span> <span data-ttu-id="41574-120">**WhatIf** 매개 변수를 사용 하면 cmdlet에서 명령을 실행할 때 발생 하는 작업을 표시 하지만 변경 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-120">The **WhatIf** parameter causes the cmdlet to display what would happen when you run the command but does not make changes.</span></span>

### <span data-ttu-id="41574-121">예 3: 서비스를 시작 하 고 텍스트 파일에 작업 기록</span><span class="sxs-lookup"><span data-stu-id="41574-121">Example 3: Start a service and record the action in a text file</span></span>

<span data-ttu-id="41574-122">이 예에서는 컴퓨터에서 WMI (WMI(Windows Management Instrumentation)) 서비스를 시작 하 고 services.txt 파일에 작업 레코드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-122">This example starts the Windows Management Instrumentation (WMI) service on the computer and adds a record of the action to the services.txt file.</span></span>

```powershell
$s = Get-Service wmi
Start-Service -InputObject $s -PassThru | Format-List >> services.txt
```

<span data-ttu-id="41574-123">먼저를 사용 `Get-Service` 하 여 WMI 서비스를 나타내는 개체를 가져온 다음 `$s` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-123">First we use `Get-Service` to get an object that represent the WMI service and store it in the `$s` variable.</span></span> <span data-ttu-id="41574-124">다음으로 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-124">Next, we start the service.</span></span> <span data-ttu-id="41574-125">**PassThru** 매개 변수를 사용 하지 않으면에서 `Start-Service` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-125">Without the **PassThru** parameter, `Start-Service` does not create any output.</span></span> <span data-ttu-id="41574-126">파이프라인 연산자 (|)는 개체 출력을 `Start-Service` cmdlet에 전달 `Format-List` 하 여 개체를 속성 목록으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-126">The pipeline operator (|) passes the object output by `Start-Service` to the `Format-List` cmdlet to format the object as a list of its properties.</span></span> <span data-ttu-id="41574-127">추가 리디렉션 연산자 ( \> \> )는 출력을 services.txt 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-127">The append redirection operator (\>\>) redirects the output to the services.txt file.</span></span> <span data-ttu-id="41574-128">출력은 기존 파일의 끝에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41574-128">The output is added to the end of the existing file.</span></span>

### <span data-ttu-id="41574-129">예제 4: 비활성화 된 서비스 시작</span><span class="sxs-lookup"><span data-stu-id="41574-129">Example 4: Start a disabled service</span></span>

<span data-ttu-id="41574-130">이 예제에서는 서비스의 시작 유형이 **사용 하지 않도록 설정** 된 경우 서비스를 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41574-130">This example shows how to start a service when the start type of the service is **Disabled**.</span></span>

```
PS> Start-Service tlntsvr
Start-Service : Service 'Telnet (TlntSvr)' cannot be started due to the following error: Cannot start service TlntSvr on computer '.'.
At line:1 char:14
+ Start-Service  <<<< tlntsvr

PS> Get-CimInstance win32_service | Where-Object Name -eq "tlntsvr"
ExitCode  : 0
Name      : TlntSvr
ProcessId : 0
StartMode : Disabled
State     : Stopped
Status    : OK

PS> Set-Service tlntsvr -StartupType manual
PS> Start-Service tlntsvr
```

<span data-ttu-id="41574-131">텔넷 서비스 (tlntsvr)를 시작 하려는 첫 번째 시도가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-131">The first attempt to start the Telnet service (tlntsvr) fails.</span></span> <span data-ttu-id="41574-132">`Get-CimInstance`명령은 Tlntsvr 서비스의 **StartMode** 속성을 **사용할 수** 없다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="41574-132">The `Get-CimInstance` command shows that the **StartMode** property of the Tlntsvr service is **Disabled**.</span></span> <span data-ttu-id="41574-133">`Set-Service`Cmdlet은 시작 유형을 **수동으로** 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-133">The `Set-Service` cmdlet changes the start type to **Manual**.</span></span> <span data-ttu-id="41574-134">이제 명령을 다시 제출할 수 있습니다 `Start-Service` .</span><span class="sxs-lookup"><span data-stu-id="41574-134">Now, we can resubmit the `Start-Service` command.</span></span> <span data-ttu-id="41574-135">명령이 성공적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="41574-135">This time, the command succeeds.</span></span> <span data-ttu-id="41574-136">명령이 성공 했는지 확인 하려면를 실행 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-136">To verify that the command succeeded, run `Get-Service`.</span></span>

## <span data-ttu-id="41574-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41574-137">PARAMETERS</span></span>

### <span data-ttu-id="41574-138">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="41574-138">-DisplayName</span></span>

<span data-ttu-id="41574-139">시작할 서비스의 표시 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-139">Specifies the display names of the services to start.</span></span> <span data-ttu-id="41574-140">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-140">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="41574-141">-제외</span><span class="sxs-lookup"><span data-stu-id="41574-141">-Exclude</span></span>

<span data-ttu-id="41574-142">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-142">Specifies services that this cmdlet omits.</span></span> <span data-ttu-id="41574-143">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-143">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="41574-144">이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-144">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="41574-145">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-145">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="41574-146">-포함</span><span class="sxs-lookup"><span data-stu-id="41574-146">-Include</span></span>

<span data-ttu-id="41574-147">이 cmdlet이 시작 되는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-147">Specifies services that this cmdlet starts.</span></span> <span data-ttu-id="41574-148">이 매개 변수 값은 **Name** 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-148">The value of this parameter qualifies the **Name** parameter.</span></span> <span data-ttu-id="41574-149">이름 요소 또는 패턴 (예:)을 입력 `s*` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-149">Enter a name element or pattern, such as `s*`.</span></span> <span data-ttu-id="41574-150">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-150">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="41574-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="41574-151">-InputObject</span></span>

<span data-ttu-id="41574-152">시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-152">Specifies **ServiceController** objects representing the services to be started.</span></span> <span data-ttu-id="41574-153">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="41574-153">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="41574-154">-Name</span><span class="sxs-lookup"><span data-stu-id="41574-154">-Name</span></span>

<span data-ttu-id="41574-155">시작할 서비스의 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-155">Specifies the service names for the service to be started.</span></span>

<span data-ttu-id="41574-156">매개 변수 이름은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="41574-156">The parameter name is optional.</span></span> <span data-ttu-id="41574-157">**이름** 또는 별칭, **ServiceName** 을 사용 하거나 매개 변수 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-157">You can use **Name** or its alias, **ServiceName**, or you can omit the parameter name.</span></span>

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

### <span data-ttu-id="41574-158">-PassThru</span><span class="sxs-lookup"><span data-stu-id="41574-158">-PassThru</span></span>

<span data-ttu-id="41574-159">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-159">Returns an object that represents the service.</span></span> <span data-ttu-id="41574-160">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="41574-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41574-161">-Confirm</span></span>

<span data-ttu-id="41574-162">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41574-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41574-163">-WhatIf</span></span>

<span data-ttu-id="41574-164">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-164">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="41574-165">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41574-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41574-166">CommonParameters</span></span>

<span data-ttu-id="41574-167">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41574-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41574-168">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41574-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41574-169">입력</span><span class="sxs-lookup"><span data-stu-id="41574-169">INPUTS</span></span>

### <span data-ttu-id="41574-170">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="41574-170">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="41574-171">서비스 또는 서비스 이름이 포함 된 문자열을 나타내는 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-171">You can pipe objects that represent the services or strings that contain the service names to this cmdlet.</span></span>

## <span data-ttu-id="41574-172">출력</span><span class="sxs-lookup"><span data-stu-id="41574-172">OUTPUTS</span></span>

### <span data-ttu-id="41574-173">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="41574-173">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="41574-174">이 cmdlet은 **PassThru** 를 지정 하는 경우 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-174">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the service, if you specify **PassThru**.</span></span> <span data-ttu-id="41574-175">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-175">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="41574-176">참고</span><span class="sxs-lookup"><span data-stu-id="41574-176">NOTES</span></span>

<span data-ttu-id="41574-177">이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-177">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="41574-178">의 기본 제공 별칭인를 참조할 수도 있습니다 `Start-Service` `sasv` .</span><span class="sxs-lookup"><span data-stu-id="41574-178">You can also refer to `Start-Service` by its built-in alias, `sasv`.</span></span> <span data-ttu-id="41574-179">자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41574-179">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="41574-180">`Start-Service` 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-180">`Start-Service` can control services only if the current user has permission to do this.</span></span> <span data-ttu-id="41574-181">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-181">If a command does not work correctly, you might not have the required permissions.</span></span>
- <span data-ttu-id="41574-182">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-182">To find the service names and display names of the services on your system, type `Get-Service`.</span></span>
  <span data-ttu-id="41574-183">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="41574-183">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>
- <span data-ttu-id="41574-184">시작 유형이 수동, 자동 또는 자동 (지연 된 시작) 인 서비스만 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-184">You can start only the services that have a start type of Manual, Automatic, or Automatic (Delayed Start).</span></span> <span data-ttu-id="41574-185">시작 유형이 Disabled 인 서비스는 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="41574-185">You cannot start the services that have a start type of Disabled.</span></span> <span data-ttu-id="41574-186">`Start-Service`메시지와 함께 명령이 실패 하는 경우를 `Cannot start service \<service-name\> on computer` 사용 `Get-CimInstance` 하 여 서비스의 시작 유형을 찾고, 필요 하면 cmdlet을 사용 하 여 `Set-Service` 서비스의 시작 유형을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="41574-186">If a `Start-Service` command fails with the message `Cannot start service \<service-name\> on computer`, use `Get-CimInstance` to find the start type of the service and, if you have to, use the `Set-Service` cmdlet to change the start type of the service.</span></span>
- <span data-ttu-id="41574-187">성능 로그 및 경고 (SysmonLog)와 같은 일부 서비스는 수행할 작업이 없는 경우 자동으로 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41574-187">Some services, such as Performance Logs and Alerts (SysmonLog) stop automatically if they have no work to do.</span></span> <span data-ttu-id="41574-188">PowerShell이 거의 즉시 중지 하는 서비스를 시작 하면 다음과 같은 메시지가 표시 됩니다. `Service \<display-name\> start failed.`</span><span class="sxs-lookup"><span data-stu-id="41574-188">When PowerShell starts a service that stops itself almost immediately, it displays the following message: `Service \<display-name\> start failed.`</span></span>

## <span data-ttu-id="41574-189">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41574-189">RELATED LINKS</span></span>

[<span data-ttu-id="41574-190">Get-Service</span><span class="sxs-lookup"><span data-stu-id="41574-190">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="41574-191">New-Service</span><span class="sxs-lookup"><span data-stu-id="41574-191">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="41574-192">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="41574-192">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="41574-193">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="41574-193">Resume-Service</span></span>](Resume-Service.md)

[<span data-ttu-id="41574-194">Set-Service</span><span class="sxs-lookup"><span data-stu-id="41574-194">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="41574-195">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="41574-195">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="41574-196">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="41574-196">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="41574-197">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="41574-197">Remove-Service</span></span>](Remove-Service.md)
