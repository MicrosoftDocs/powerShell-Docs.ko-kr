---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/resume-service?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Resume-Service
ms.openlocfilehash: f5bf1eab12b65b6e6ffeeb92c983777a576c503b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211865"
---
# <span data-ttu-id="83013-103">Resume-Service</span><span class="sxs-lookup"><span data-stu-id="83013-103">Resume-Service</span></span>

## <span data-ttu-id="83013-104">개요</span><span class="sxs-lookup"><span data-stu-id="83013-104">SYNOPSIS</span></span>
<span data-ttu-id="83013-105">하나 이상의 일시 중단(일시 중지)된 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-105">Resumes one or more suspended (paused) services.</span></span>

## <span data-ttu-id="83013-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="83013-106">SYNTAX</span></span>

### <span data-ttu-id="83013-107">InputObject (기본값)</span><span class="sxs-lookup"><span data-stu-id="83013-107">InputObject (Default)</span></span>

```
Resume-Service [-InputObject] <ServiceController[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="83013-108">기본값</span><span class="sxs-lookup"><span data-stu-id="83013-108">Default</span></span>

```
Resume-Service [-Name] <String[]> [-PassThru] [-Include <String[]>] [-Exclude <String[]>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="83013-109">DisplayName</span><span class="sxs-lookup"><span data-stu-id="83013-109">DisplayName</span></span>

```
Resume-Service [-PassThru] -DisplayName <String[]> [-Include <String[]>] [-Exclude <String[]>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="83013-110">설명</span><span class="sxs-lookup"><span data-stu-id="83013-110">DESCRIPTION</span></span>

<span data-ttu-id="83013-111">**다시 시작 서비스** cmdlet은 지정 된 각 서비스에 대 한 다시 시작 메시지를 Windows 서비스 컨트롤러로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83013-111">The **Resume-Service** cmdlet sends a resume message to the Windows Service Controller for each of the specified services.</span></span>
<span data-ttu-id="83013-112">일시 중단 된 서비스는 다시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83013-112">If a service is suspended, it resumes.</span></span>
<span data-ttu-id="83013-113">현재 실행 중인 경우에는 메시지가 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83013-113">If it is currently running, the message is ignored.</span></span>
<span data-ttu-id="83013-114">서비스 이름 또는 표시 이름으로 서비스를 지정 하거나 *InputObject* 매개 변수를 사용 하 여 다시 시작할 서비스를 나타내는 서비스 개체를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-114">You can specify the services by their service names or display names, or you can use the *InputObject* parameter to pass a service object that represents the services that you want to resume.</span></span>

## <span data-ttu-id="83013-115">예제</span><span class="sxs-lookup"><span data-stu-id="83013-115">EXAMPLES</span></span>

### <span data-ttu-id="83013-116">예 1: 로컬 컴퓨터에서 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-116">Example 1: Resume a service on the local computer</span></span>

```
PS C:\> Resume-Service "sens"
```

<span data-ttu-id="83013-117">이 명령은 로컬 컴퓨터에서 시스템 이벤트 알림 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-117">This command resumes the System Event Notification service  on the local computer.</span></span>
<span data-ttu-id="83013-118">서비스 이름은 sens으로 명령에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83013-118">The service name is represented in the command by sens.</span></span>
<span data-ttu-id="83013-119">이 명령은 *name* 매개 변수를 사용 하 여 서비스의 서비스 이름을 지정 합니다. 그러나 매개 변수 이름은 선택 사항 이므로이 명령은 매개 변수 이름을 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-119">The command uses the *Name* parameter to specify the service name of the service, but the command omits the parameter name because the parameter name is optional.</span></span>

### <span data-ttu-id="83013-120">예제 2: 모든 일시 중단 된 서비스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="83013-120">Example 2: Resume all suspended services</span></span>

```
PS C:\> Get-Service | Where-Object {$_.Status -eq "Paused"} | Resume-Service
```

<span data-ttu-id="83013-121">이 명령은 컴퓨터에서 일시 중단 된 모든 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-121">This command resumes all of the suspended  services on the computer.</span></span>
<span data-ttu-id="83013-122">Get-Service cmdlet 명령은 컴퓨터의 모든 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="83013-122">The Get-Service cmdlet command gets all of the services on the computer.</span></span>
<span data-ttu-id="83013-123">파이프라인 연산자 (|)가 Where-Object cmdlet으로 결과를 전달 합니다 .이 cmdlet은 **Status** 속성이 일시 중지 됨 인 서비스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-123">The pipeline operator (|) passes the results to the Where-Object cmdlet, which selects the services that have a **Status** property of Paused.</span></span>
<span data-ttu-id="83013-124">다음 파이프라인 연산자는 일시 중지 된 서비스를 다시 시작 하는 **다시 시작 서비스** 에 결과를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="83013-124">The next pipeline operator sends the results to **Resume-Service** , which resumes the paused services.</span></span>

<span data-ttu-id="83013-125">실제로 *WhatIf* 매개 변수를 사용 하 여 명령 실행 전에 명령 효과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-125">In practice, you would use the *WhatIf* parameter to determine the effect of the command before you run it.</span></span>

## <span data-ttu-id="83013-126">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="83013-126">PARAMETERS</span></span>

### <span data-ttu-id="83013-127">-DisplayName</span><span class="sxs-lookup"><span data-stu-id="83013-127">-DisplayName</span></span>

<span data-ttu-id="83013-128">다시 시작할 서비스의 표시 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-128">Specifies the display names of the services to be resumed.</span></span>
<span data-ttu-id="83013-129">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-129">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="83013-130">-제외</span><span class="sxs-lookup"><span data-stu-id="83013-130">-Exclude</span></span>

<span data-ttu-id="83013-131">이 cmdlet이 생략 하는 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-131">Specifies services that this cmdlet omits.</span></span>
<span data-ttu-id="83013-132">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-132">The value of this parameter qualifies the *Name* parameter.</span></span>
<span data-ttu-id="83013-133">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-133">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="83013-134">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-134">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="83013-135">-포함</span><span class="sxs-lookup"><span data-stu-id="83013-135">-Include</span></span>

<span data-ttu-id="83013-136">다시 시작할 서비스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-136">Specifies services to resume.</span></span>
<span data-ttu-id="83013-137">이 매개 변수 값은 *Name* 매개 변수를 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-137">The value of this parameter qualifies *Name* parameter.</span></span>
<span data-ttu-id="83013-138">이름 요소 또는 패턴 (예: s \*)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-138">Enter a name element or pattern, such as s\*.</span></span>
<span data-ttu-id="83013-139">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-139">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="83013-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="83013-140">-InputObject</span></span>

<span data-ttu-id="83013-141">다시 시작할 서비스를 나타내는 **ServiceController** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-141">Specifies **ServiceController** objects that represent the services to resumed.</span></span>
<span data-ttu-id="83013-142">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="83013-142">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="83013-143">-Name</span><span class="sxs-lookup"><span data-stu-id="83013-143">-Name</span></span>

<span data-ttu-id="83013-144">다시 시작할 서비스의 서비스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-144">Specifies the service names of the services to be resumed.</span></span>

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

### <span data-ttu-id="83013-145">-PassThru</span><span class="sxs-lookup"><span data-stu-id="83013-145">-PassThru</span></span>

<span data-ttu-id="83013-146">서비스를 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-146">Returns an object that represents the service.</span></span>
<span data-ttu-id="83013-147">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-147">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="83013-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="83013-148">-Confirm</span></span>

<span data-ttu-id="83013-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="83013-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="83013-150">-WhatIf</span></span>

<span data-ttu-id="83013-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="83013-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="83013-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="83013-153">CommonParameters</span></span>

<span data-ttu-id="83013-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="83013-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="83013-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="83013-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="83013-156">입력</span><span class="sxs-lookup"><span data-stu-id="83013-156">INPUTS</span></span>

### <span data-ttu-id="83013-157">ServiceController, System.string입니다.</span><span class="sxs-lookup"><span data-stu-id="83013-157">System.ServiceProcess.ServiceController, System.String</span></span>

<span data-ttu-id="83013-158">서비스 개체 또는 서비스 이름이 포함 된 문자열을이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-158">You can pipe a service object or a string that contains a service name to this cmdlet.</span></span>

## <span data-ttu-id="83013-159">출력</span><span class="sxs-lookup"><span data-stu-id="83013-159">OUTPUTS</span></span>

### <span data-ttu-id="83013-160">None, ServiceController</span><span class="sxs-lookup"><span data-stu-id="83013-160">None, System.ServiceProcess.ServiceController</span></span>

<span data-ttu-id="83013-161">이 cmdlet은 *PassThru* 매개 변수를 지정 하는 경우 다시 시작 된 서비스를 나타내는 **ServiceController** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-161">This cmdlet generates a **System.ServiceProcess.ServiceController** object that represents the resumed service, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="83013-162">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-162">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="83013-163">참고</span><span class="sxs-lookup"><span data-stu-id="83013-163">NOTES</span></span>

* <span data-ttu-id="83013-164">일시 중단 된 서비스의 상태가 일시 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83013-164">The status of services that have been suspended is Paused.</span></span> <span data-ttu-id="83013-165">서비스가 다시 시작 되 면 상태는 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="83013-165">When services are resumed, their status is Running.</span></span>
* <span data-ttu-id="83013-166">**다시 시작 서비스** 는 현재 사용자에 게이 작업을 수행할 수 있는 권한이 있는 경우에만 서비스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-166">**Resume-Service** can control services only when the current user has permission to do this.</span></span> <span data-ttu-id="83013-167">따라서 명령이 제대로 작동하지 않는 경우 필요한 권한이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83013-167">If a command does not work correctly, you might not have the required permissions.</span></span>
* <span data-ttu-id="83013-168">시스템에서 서비스의 서비스 이름 및 표시 이름을 찾으려면를 입력 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="83013-168">To find the service names and display names of the services on your system, type `Get-Service`.</span></span> <span data-ttu-id="83013-169">서비스 이름은 **Name** 열에 나타나고 표시 이름은 **DisplayName** 열에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="83013-169">The service names appear in the **Name** column, and the display names appear in the **DisplayName** column.</span></span>

## <span data-ttu-id="83013-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="83013-170">RELATED LINKS</span></span>

[<span data-ttu-id="83013-171">Get-Service</span><span class="sxs-lookup"><span data-stu-id="83013-171">Get-Service</span></span>](Get-Service.md)

[<span data-ttu-id="83013-172">New-Service</span><span class="sxs-lookup"><span data-stu-id="83013-172">New-Service</span></span>](New-Service.md)

[<span data-ttu-id="83013-173">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="83013-173">Restart-Service</span></span>](Restart-Service.md)

[<span data-ttu-id="83013-174">Set-Service</span><span class="sxs-lookup"><span data-stu-id="83013-174">Set-Service</span></span>](Set-Service.md)

[<span data-ttu-id="83013-175">Start-Service</span><span class="sxs-lookup"><span data-stu-id="83013-175">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="83013-176">Stop-Service</span><span class="sxs-lookup"><span data-stu-id="83013-176">Stop-Service</span></span>](Stop-Service.md)

[<span data-ttu-id="83013-177">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="83013-177">Suspend-Service</span></span>](Suspend-Service.md)

[<span data-ttu-id="83013-178">Remove-Service</span><span class="sxs-lookup"><span data-stu-id="83013-178">Remove-Service</span></span>](Remove-Service.md)

