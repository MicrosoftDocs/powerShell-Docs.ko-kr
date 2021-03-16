---
description: 원격 명령의 출력을 해석 하 고 형식을 지정 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Output
ms.openlocfilehash: 476afc62089795d22002ece05c7ce2bf53994237
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600129"
---
# <a name="about-remote-output"></a><span data-ttu-id="8a1d1-103">원격 출력 정보</span><span class="sxs-lookup"><span data-stu-id="8a1d1-103">About Remote Output</span></span>

## <a name="short-description"></a><span data-ttu-id="8a1d1-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="8a1d1-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="8a1d1-105">원격 명령의 출력을 해석 하 고 형식을 지정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-105">Describes how to interpret and format the output of remote commands.</span></span>

## <a name="long-description"></a><span data-ttu-id="8a1d1-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="8a1d1-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="8a1d1-107">원격 컴퓨터에서 실행 된 명령의 출력은 로컬 컴퓨터에서 실행 되는 것과 동일한 명령의 출력과 유사 하지만 몇 가지 중요 한 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-107">The output of a command that was run on a remote computer might look like output of the same command run on a local computer, but there are some significant differences.</span></span>

<span data-ttu-id="8a1d1-108">이 항목에서는 원격 컴퓨터에서 실행 되는 명령의 출력을 해석 하 고, 서식을 지정 하 고, 표시 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-108">This topic explains how to interpret, format, and display the output of commands that are run on remote computers.</span></span>

## <a name="displaying-the-computer-name"></a><span data-ttu-id="8a1d1-109">컴퓨터 이름 표시</span><span class="sxs-lookup"><span data-stu-id="8a1d1-109">DISPLAYING THE COMPUTER NAME</span></span>

<span data-ttu-id="8a1d1-110">Invoke-Command cmdlet을 사용 하 여 원격 컴퓨터에서 명령을 실행 하는 경우이 명령은 데이터를 생성 한 컴퓨터의 이름을 포함 하는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-110">When you use the Invoke-Command cmdlet to run a command on a remote computer, the command returns an object that includes the name of the computer that generated the data.</span></span> <span data-ttu-id="8a1d1-111">원격 컴퓨터 이름은 PSComputerName 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-111">The remote computer name is stored in the PSComputerName property.</span></span>

<span data-ttu-id="8a1d1-112">대부분의 명령에 대해 기본적으로 PSComputerName이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-112">For many commands, the PSComputerName is displayed by default.</span></span> <span data-ttu-id="8a1d1-113">예를 들어 다음 명령은 Server01 및 Server02의 두 원격 컴퓨터에서 Get-Culture 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-113">For example, the following command runs a Get-Culture command on two remote computers, Server01 and Server02.</span></span> <span data-ttu-id="8a1d1-114">아래에 표시 되는 출력에는 명령이 실행 된 원격 컴퓨터의 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-114">The output, which appears below, includes the names of the remote computers on which the command ran.</span></span>

```powershell
C:\PS> invoke-command -script {get-culture} -comp Server01, Server02

LCID  Name    DisplayName                PSComputerName
----  ----    -----------                --------------
1033  en-US   English (United States)    Server01
1033  es-AR   Spanish (Argentina)        Server02
```

<span data-ttu-id="8a1d1-115">Invoke-Command의 HideComputerName 매개 변수를 사용 하 여 PSComputerName 속성을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-115">You can use the HideComputerName parameter of Invoke-Command to hide the PSComputerName property.</span></span> <span data-ttu-id="8a1d1-116">이 매개 변수는 하나의 원격 컴퓨터에서 데이터를 수집 하는 명령을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-116">This parameter is designed for commands that collect data from only one remote computer.</span></span>

<span data-ttu-id="8a1d1-117">다음 명령은 Server01 원격 컴퓨터에서 Get-Culture 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-117">The following command runs a Get-Culture command on the Server01 remote computer.</span></span> <span data-ttu-id="8a1d1-118">HideComputerName 매개 변수를 사용 하 여 PSComputerName 속성 및 관련 속성을 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-118">It uses the HideComputerName parameter to hide the PSComputerName property and related properties.</span></span>

```powershell
C:\PS> invoke-command -scr {get-culture} -comp Server01 -HideComputerName

LCID             Name             DisplayName
----             ----             -----------
1033             en-US            English (United States)
```

<span data-ttu-id="8a1d1-119">기본적으로 표시 되지 않는 경우 PSComputerName 속성을 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-119">You can also display the PSComputerName property if it is not displayed by default.</span></span>

<span data-ttu-id="8a1d1-120">예를 들어 다음 명령은 Format-Table cmdlet을 사용 하 여 원격 Get-Date 명령의 출력에 PSComputerName 속성을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-120">For example, the following commands use the Format-Table cmdlet to add the PSComputerName property to the output of a remote Get-Date command.</span></span>

```powershell
$dates = invoke-command -script {get-date} -computername Server01, Server02
$dates | format-table DateTime, PSComputerName -auto

DateTime                            PSComputerName
--------                            --------------
Monday, July 21, 2008 7:16:58 PM    Server01
Monday, July 21, 2008 7:16:58 PM    Server02
```

## <a name="displaying-the-machinename-property"></a><span data-ttu-id="8a1d1-121">MACHINENAME 속성 표시</span><span class="sxs-lookup"><span data-stu-id="8a1d1-121">DISPLAYING THE MACHINENAME PROPERTY</span></span>

<span data-ttu-id="8a1d1-122">Get Process, Get-help 및 Get EventLog를 비롯 한 여러 cmdlet에는 원격 컴퓨터의 개체를 가져오는 ComputerName 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-122">Several cmdlets, including Get-Process, Get-Service, and Get-EventLog, have a ComputerName parameter that gets the objects on a remote computer.</span></span>
<span data-ttu-id="8a1d1-123">이러한 cmdlet은 PowerShell 원격을 사용 하지 않으므로 Windows PowerShell에서 원격 기능을 사용 하도록 구성 되지 않은 컴퓨터 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-123">These cmdlets do not use PowerShell remoting, so you can use them even on computers that are not configured for remoting in Windows PowerShell.</span></span>

<span data-ttu-id="8a1d1-124">이러한 cmdlet이 반환 하는 개체는 MachineName 속성에 원격 컴퓨터의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-124">The objects that these cmdlets return store the name of the remote computer in the MachineName property.</span></span> <span data-ttu-id="8a1d1-125">이러한 개체에는 PSComputerName 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-125">(These objects do not have a PSComputerName property.)</span></span>

<span data-ttu-id="8a1d1-126">예를 들어이 명령은 Server01 및 Server02 원격 컴퓨터에서 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-126">For example, this command gets the PowerShell process on the Server01 and Server02 remote computers.</span></span> <span data-ttu-id="8a1d1-127">기본 표시에는 MachineName 속성이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-127">The default display does not include the MachineName property.</span></span>

```powershell
C:\PS> get-process PowerShell -computername server01, server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
920      38    97524     114504   575     9.66   2648 PowerShell
194       6    24256      32384   142            3020 PowerShell
352      27    63472      63520   577     3.84   4796 PowerShell
```

<span data-ttu-id="8a1d1-128">Format-Table cmdlet을 사용 하 여 프로세스 개체의 MachineName 속성을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-128">You can use the Format-Table cmdlet to display the MachineName property of the process objects.</span></span>

<span data-ttu-id="8a1d1-129">예를 들어 다음 명령은 $p 변수에 프로세스를 저장 한 다음 파이프라인 연산자 (|)를 사용 하 여 $p의 프로세스를 Format-Table 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-129">For example, the following command saves the processes in the $p variable and then uses a pipeline operator (|) to send the processes in $p to the Format-Table command.</span></span> <span data-ttu-id="8a1d1-130">이 명령은 Format-Table의 Property 매개 변수를 사용 하 여 MachineName 속성을 표시에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-130">The command uses the Property parameter of Format-Table to include the MachineName property in the display.</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02
C:\PS> $P | format-table -property ID, ProcessName, MachineName -auto

Id ProcessName MachineName
-- ----------- -----------
2648 PowerShell  Server02
3020 PowerShell  Server01
4796 PowerShell  Server02
```

<span data-ttu-id="8a1d1-131">다음 보다 복잡 한 명령은 MachineName 속성을 기본 프로세스 표시에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-131">The following more complex command adds the MachineName property to the default process display.</span></span> <span data-ttu-id="8a1d1-132">해시 테이블을 사용 하 여 계산 된 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-132">It uses hash tables to specify calculated properties.</span></span> <span data-ttu-id="8a1d1-133">다행히 사용 하기 위해 이해할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-133">Fortunately, you do not have to understand it to use it.</span></span>

<span data-ttu-id="8a1d1-134">(억음 [']는 연속 문자입니다.)</span><span class="sxs-lookup"><span data-stu-id="8a1d1-134">(Note that the backtick [\`] is the continuation character.)</span></span>

```powershell
C:\PS> $p = get-process PowerShell -comp Server01, Server02

C:\PS> $p | format-table -property Handles, `
@{Label="NPM(K)";Expression={int}}, `
@{Label="PM(K)";Expression={int}}, `
@{Label="WS(K)";Expression={int}}, `
@{Label="VM(M)";Expression={int}}, `
@{Label="CPU(s)";Expression={if ($.CPU -ne $()){ $.CPU.ToString("N")}}}, `
Id, ProcessName, MachineName -auto

Handles NPM(K) PM(K)  WS(K) VM(M) CPU(s)   Id ProcessName MachineName
------- ------ -----  ----- ----- ------   -- ----------- -----------
920     38 97560 114532   576        2648 PowerShell  Server02
192      6 24132  32028   140        3020 PowerShell  Server01
438     26 48436  59132   565        4796 PowerShell  Server02

```

## <a name="deserialized-objects"></a><span data-ttu-id="8a1d1-135">DESERIALIZE 된 개체</span><span class="sxs-lookup"><span data-stu-id="8a1d1-135">DESERIALIZED OBJECTS</span></span>

<span data-ttu-id="8a1d1-136">출력을 생성 하는 원격 명령을 실행 하면 명령 출력이 네트워크를 통해 로컬 컴퓨터에 다시 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-136">When you run remote commands that generate output, the command output is transmitted across the network back to the local computer.</span></span>

<span data-ttu-id="8a1d1-137">PowerShell cmdlet이 반환 하는 개체와 같은 대부분의 라이브 Microsoft .NET 프레임 워크 개체는 네트워크를 통해 전송할 수 없으므로 라이브 개체는 "직렬화" 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-137">Because most live Microsoft .NET Framework objects (such as the objects that PowerShell cmdlets return) cannot be transmitted over the network, the live objects are "serialized".</span></span> <span data-ttu-id="8a1d1-138">즉, 라이브 개체는 개체 및 해당 속성의 XML 표현으로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-138">In other words, the live objects are converted into XML representations of the object and its properties.</span></span> <span data-ttu-id="8a1d1-139">그런 다음 XML 기반의 직렬화 된 개체가 네트워크를 통해 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-139">Then, the XML-based serialized object is transmitted across the network.</span></span>

<span data-ttu-id="8a1d1-140">로컬 컴퓨터에서 PowerShell은 xml 기반의 직렬화 된 개체를 수신 하 고 XML 기반 개체를 표준 .NET Framework 개체로 변환 하 여 "deserialize" 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-140">On the local computer, PowerShell receives the XML-based serialized object and "deserializes" it by converting the XML-based object into a standard .NET Framework object.</span></span>

<span data-ttu-id="8a1d1-141">그러나 deserialize 된 개체는 라이브 개체가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-141">However, the deserialized object is not a live object.</span></span> <span data-ttu-id="8a1d1-142">Serialize 된 시점의 개체 스냅숏에는 속성을 포함 하지만 메서드는 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-142">It is a snapshot of the object at the time that it was serialized, and it includes properties but no methods.</span></span> <span data-ttu-id="8a1d1-143">파이프라인에 전달 하 고, 선택한 속성을 표시 하 고, 서식을 지정 하는 등 PowerShell에서 이러한 개체를 사용 하 고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-143">You can use and manage these objects in PowerShell, including passing them in pipelines, displaying selected properties, and formatting them.</span></span>

<span data-ttu-id="8a1d1-144">대부분의 deserialize 된 개체는 Types.ps1xml 또는 Format.ps1xml 파일의 항목에 의해 자동으로 표시 되도록 서식이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-144">Most deserialized objects are automatically formatted for display by entries in the Types.ps1xml or Format.ps1xml files.</span></span> <span data-ttu-id="8a1d1-145">그러나 로컬 컴퓨터에는 원격 컴퓨터에서 생성 된 모든 deserialize 된 개체에 대 한 형식 지정 파일이 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-145">However, the local computer might not have formatting files for all of the deserialized objects that were generated on a remote computer.</span></span> <span data-ttu-id="8a1d1-146">개체의 형식을 지정 하지 않으면 각 개체의 속성이 모두 콘솔의 스트리밍 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-146">When objects are not formatted, all of the properties of each object appear in the console in a streaming list.</span></span>

<span data-ttu-id="8a1d1-147">개체의 서식이 자동으로 지정 되지 않은 경우에는 Format-Table 또는 서식 목록과 같은 서식 지정 cmdlet을 사용 하 여 선택한 속성의 서식을 지정 하 고 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-147">When objects are not formatted automatically, you can use the formatting cmdlets, such as Format-Table or Format-List, to format and display selected properties.</span></span> <span data-ttu-id="8a1d1-148">또는 Out-GridView cmdlet을 사용 하 여 테이블에 개체를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-148">Or, you can use the Out-GridView cmdlet to display the objects in a table.</span></span>

<span data-ttu-id="8a1d1-149">또한 로컬 컴퓨터에 없는 cmdlet을 사용 하는 원격 컴퓨터에서 명령을 실행 하는 경우 컴퓨터에 해당 개체에 대 한 형식 지정 파일이 없으므로 명령이 반환 하는 개체의 형식이 올바르게 지정 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-149">Also, if you run a command on a remote computer that uses cmdlets that you do not have on your local computer, the objects that the command returns might not be formatted properly because you do not have the formatting files for those objects on your computer.</span></span> <span data-ttu-id="8a1d1-150">다른 컴퓨터에서 형식 지정 데이터를 가져오려면 Get-FormatData 및 Export-FormatData cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-150">To get formatting data from another computer, use the Get-FormatData and Export-FormatData cmdlets.</span></span>

<span data-ttu-id="8a1d1-151">System.io.directoryinfo 개체 및 Guid와 같은 일부 개체 유형은 수신 될 때 라이브 개체로 다시 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-151">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="8a1d1-152">이러한 개체는 특별 한 처리 나 서식 지정이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-152">These objects do not need any special handling or formatting.</span></span>

## <a name="ordering-the-results"></a><span data-ttu-id="8a1d1-153">결과 정렬</span><span class="sxs-lookup"><span data-stu-id="8a1d1-153">ORDERING THE RESULTS</span></span>

<span data-ttu-id="8a1d1-154">Cmdlet의 ComputerName 매개 변수에서 컴퓨터 이름의 순서는 PowerShell이 원격 컴퓨터에 연결 하는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-154">The order of the computer names in the ComputerName parameter of cmdlets determines the order in which PowerShell connects to the remote computers.</span></span> <span data-ttu-id="8a1d1-155">그러나 결과는 로컬 컴퓨터에 표시 되는 순서 대로 표시 되며,이는 순서가 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-155">However, the results appear in the order in which the local computer receives them, which might be a different order.</span></span>

<span data-ttu-id="8a1d1-156">결과의 순서를 변경 하려면 Sort-Object cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-156">To change the order of the results, use the Sort-Object cmdlet.</span></span> <span data-ttu-id="8a1d1-157">PSComputerName 또는 MachineName 속성을 기준으로 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-157">You can sort on the PSComputerName or MachineName property.</span></span> <span data-ttu-id="8a1d1-158">다른 컴퓨터의 결과가 섞여 있도록 개체의 다른 속성을 기준으로 정렬할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8a1d1-158">You can also sort on another property of the object so that the results from different computers are interspersed.</span></span>

## <a name="see-also"></a><span data-ttu-id="8a1d1-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a1d1-159">SEE ALSO</span></span>

[<span data-ttu-id="8a1d1-160">about_Remote</span><span class="sxs-lookup"><span data-stu-id="8a1d1-160">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="8a1d1-161">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="8a1d1-161">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="8a1d1-162">Format-Table</span><span class="sxs-lookup"><span data-stu-id="8a1d1-162">Format-Table</span></span>](xref:Microsoft.PowerShell.Utility.Format-Table)

[<span data-ttu-id="8a1d1-163">Get-Process</span><span class="sxs-lookup"><span data-stu-id="8a1d1-163">Get-Process</span></span>](xref:Microsoft.PowerShell.Management.Get-Process)

[<span data-ttu-id="8a1d1-164">Get-Service</span><span class="sxs-lookup"><span data-stu-id="8a1d1-164">Get-Service</span></span>](xref:Microsoft.PowerShell.Management.Get-Service)

[<span data-ttu-id="8a1d1-165">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="8a1d1-165">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="8a1d1-166">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8a1d1-166">Select-Object</span></span>](xref:Microsoft.PowerShell.Utility.Select-Object)
