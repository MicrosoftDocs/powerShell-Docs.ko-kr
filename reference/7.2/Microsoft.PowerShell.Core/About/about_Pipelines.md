---
description: PowerShell에서 파이프라인으로 명령 결합
Locale: en-US
ms.date: 09/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pipelines?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pipelines
ms.openlocfilehash: e4ae85fbbfe5232048a90e1fe4f62db3e95e5f1b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601868"
---
# <a name="about-pipelines"></a><span data-ttu-id="042cc-103">파이프라인 정보</span><span class="sxs-lookup"><span data-stu-id="042cc-103">About Pipelines</span></span>

## <a name="short-description"></a><span data-ttu-id="042cc-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="042cc-104">Short description</span></span>

<span data-ttu-id="042cc-105">PowerShell에서 파이프라인으로 명령 결합</span><span class="sxs-lookup"><span data-stu-id="042cc-105">Combining commands into pipelines in the PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="042cc-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-106">Long description</span></span>

<span data-ttu-id="042cc-107">파이프라인은 파이프라인 연산자 ( `|` ) (ASCII 124)로 연결 되는 일련의 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-107">A pipeline is a series of commands connected by pipeline operators (`|`) (ASCII 124).</span></span> <span data-ttu-id="042cc-108">각 파이프라인 연산자는 이전 명령의 결과를 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-108">Each pipeline operator sends the results of the preceding command to the next command.</span></span>

<span data-ttu-id="042cc-109">첫 번째 명령의 출력은 처리를 위해 두 번째 명령에 대 한 입력으로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-109">The output of the first command can be sent for processing as input to the second command.</span></span> <span data-ttu-id="042cc-110">그리고 해당 출력을 다른 명령으로 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-110">And that output can be sent to yet another command.</span></span> <span data-ttu-id="042cc-111">결과는 일련의 간단한 명령으로 구성 된 복잡 한 명령 체인 또는 _파이프라인_ 입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-111">The result is a complex command chain or _pipeline_ that is composed of a series of simple commands.</span></span>

<span data-ttu-id="042cc-112">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-112">For example,</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="042cc-113">이 예제에서는 `Command-1` 를 내보내는 개체가로 보내집니다 `Command-2` .</span><span class="sxs-lookup"><span data-stu-id="042cc-113">In this example, the objects that `Command-1` emits are sent to `Command-2`.</span></span>
<span data-ttu-id="042cc-114">`Command-2` 개체를 처리 하 고로 보냅니다 `Command-3` .</span><span class="sxs-lookup"><span data-stu-id="042cc-114">`Command-2` processes the objects and sends them to `Command-3`.</span></span> <span data-ttu-id="042cc-115">`Command-3` 개체를 처리 하 고 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-115">`Command-3` processes the objects and send them down the pipeline.</span></span> <span data-ttu-id="042cc-116">파이프라인에 명령이 더 이상 없으므로 결과가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-116">Because there are no more commands in the pipeline, the results are displayed at the console.</span></span>

<span data-ttu-id="042cc-117">파이프라인에서 명령은 왼쪽에서 오른쪽 순서로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-117">In a pipeline, the commands are processed in order from left to right.</span></span> <span data-ttu-id="042cc-118">처리는 단일 작업으로 처리 되 고 출력은 생성 될 때 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-118">The processing is handled as a single operation and output is displayed as it's generated.</span></span>

<span data-ttu-id="042cc-119">다음은 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-119">Here is a simple example.</span></span> <span data-ttu-id="042cc-120">다음 명령은 메모장 프로세스를 가져온 다음 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-120">The following command gets the Notepad process and then stops it.</span></span>

<span data-ttu-id="042cc-121">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-121">For example,</span></span>

```powershell
Get-Process notepad | Stop-Process
```

<span data-ttu-id="042cc-122">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Process` 메모장 프로세스를 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-122">The first command uses the `Get-Process` cmdlet to get an object representing the Notepad process.</span></span> <span data-ttu-id="042cc-123">파이프라인 연산자 ()를 사용 하 여 `|` 프로세스 개체를 cmdlet으로 보내면이 `Stop-Process` Cmdlet이 메모장 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-123">It uses a pipeline operator (`|`) to send the process object to the `Stop-Process` cmdlet, which stops the Notepad process.</span></span> <span data-ttu-id="042cc-124">`Stop-Process`지정 된 프로세스가 파이프라인을 통해 전송 되기 때문에이 명령에는 프로세스를 지정 하기 위한 **이름** 또는 **ID** 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-124">Notice that the `Stop-Process` command doesn't have a **Name** or **ID** parameter to specify the process, because the specified process is submitted through the pipeline.</span></span>

<span data-ttu-id="042cc-125">이 파이프라인 예제에서는 현재 디렉터리에 있는 텍스트 파일을 가져오고, 1만 바이트 보다 긴 파일만 선택 하 고, 길이를 기준으로 정렬 하 고, 테이블에 있는 각 파일의 이름과 길이를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-125">This pipeline example gets the text files in the current directory, selects only the files that are more than 10,000 bytes long, sorts them by length, and displays the name and length of each file in a table.</span></span>

```powershell
Get-ChildItem -Path *.txt |
  Where-Object {$_.length -gt 10000} |
    Sort-Object -Property length |
      Format-Table -Property name, length
```

<span data-ttu-id="042cc-126">이 파이프라인은 지정 된 순서 대로 4 개의 명령으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-126">This pipeline consists of four commands in the specified order.</span></span> <span data-ttu-id="042cc-127">다음 그림에서는 파이프라인의 다음 명령에 전달 되는 각 명령의 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-127">The following illustration shows the output from each command as it's passed to the next command in the pipeline.</span></span>

```
Get-ChildItem -Path *.txt
| (FileInfo objects for *.txt)
V
Where-Object {$_.length -gt 10000}
| (FileInfo objects for *.txt)
| (      Length > 10000      )
V
Sort-Object -Property Length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
V
Format-Table -Property name, length
| (FileInfo objects for *.txt)
| (      Length > 10000      )
| (     Sorted by length     )
| (   Formatted in a table   )
V

Name                       Length
----                       ------
tmp1.txt                    82920
tmp2.txt                   114000
tmp3.txt                   114000
```

## <a name="using-pipelines"></a><span data-ttu-id="042cc-128">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="042cc-128">Using pipelines</span></span>

<span data-ttu-id="042cc-129">대부분의 PowerShell cmdlet은 파이프라인을 지원 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-129">Most PowerShell cmdlets are designed to support pipelines.</span></span> <span data-ttu-id="042cc-130">대부분의 경우 **Get** cmdlet의 결과를 동일한 명사의 다른 cmdlet으로 _파이프_ 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-130">In most cases, you can _pipe_ the results of a **Get** cmdlet to another cmdlet of the same noun.</span></span>
<span data-ttu-id="042cc-131">예를 들어 cmdlet의 출력을 `Get-Service` 또는 cmdlet으로 파이프 할 수 `Start-Service` 있습니다 `Stop-Service` .</span><span class="sxs-lookup"><span data-stu-id="042cc-131">For example, you can pipe the output of the `Get-Service` cmdlet to the `Start-Service` or `Stop-Service` cmdlets.</span></span>

<span data-ttu-id="042cc-132">이 예제 파이프라인은 컴퓨터에서 WMI 서비스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-132">This example pipeline starts the WMI service on the computer:</span></span>

```powershell
Get-Service wmi | Start-Service
```

<span data-ttu-id="042cc-133">또 다른 예로 `Get-Item` PowerShell 레지스트리 공급자 내 또는의 출력을 `Get-ChildItem` cmdlet으로 파이프 할 수 있습니다 `New-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="042cc-133">For another example, you can pipe the output of `Get-Item` or `Get-ChildItem` within the PowerShell registry provider to the `New-ItemProperty` cmdlet.</span></span> <span data-ttu-id="042cc-134">이 예제에서는 값이 **8124** 인 **noofemployees** 라는 새 레지스트리 항목을 **MyCompany** 레지스트리 키에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-134">This example adds a new registry entry, **NoOfEmployees**, with a value of **8124**, to the **MyCompany** registry key.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany |
  New-ItemProperty -Name NoOfEmployees -Value 8124
```

<span data-ttu-id="042cc-135">,,, 및와 같은 유틸리티 cmdlet은 대부분 `Get-Member` `Where-Object` `Sort-Object` `Group-Object` `Measure-Object` 파이프라인 에서만 거의 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-135">Many of the utility cmdlets, such as `Get-Member`, `Where-Object`, `Sort-Object`, `Group-Object`, and `Measure-Object` are used almost exclusively in pipelines.</span></span> <span data-ttu-id="042cc-136">모든 개체 유형을 이러한 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-136">You can pipe any object type to these cmdlets.</span></span> <span data-ttu-id="042cc-137">이 예에서는 각 프로세스에서 열린 핸들 수를 기준으로 컴퓨터의 모든 프로세스를 정렬 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-137">This example shows how to sort all the processes on the computer by the number of open handles in each process.</span></span>

```powershell
Get-Process | Sort-Object -Property handles
```

<span data-ttu-id="042cc-138">,,, 및와 같은 개체를 형식 지정, 내보내기 및 출력 cmdlet으로 파이프 할 수 있습니다 `Format-List` `Format-Table` `Export-Clixml` `Export-CSV` `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="042cc-138">You can pipe objects to the formatting, export, and output cmdlets, such as `Format-List`, `Format-Table`, `Export-Clixml`, `Export-CSV`, and `Out-File`.</span></span>

<span data-ttu-id="042cc-139">이 예에서는 cmdlet을 사용 하 여 `Format-List` 프로세스 개체의 속성 목록을 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-139">This example shows how to use the `Format-List` cmdlet to display a list of properties for a process object.</span></span>

```powershell
Get-Process winlogon | Format-List -Property *
```

<span data-ttu-id="042cc-140">약간의 연습을 통해 간단한 명령을 파이프라인으로 결합 하 여 시간을 절약 하 고 입력 한 다음 스크립팅을 보다 효율적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-140">With a bit of practice, you'll find that combining simple commands into pipelines saves time and typing, and makes your scripting more efficient.</span></span>

## <a name="how-pipelines-work"></a><span data-ttu-id="042cc-141">파이프라인 작동 방법</span><span class="sxs-lookup"><span data-stu-id="042cc-141">How pipelines work</span></span>

<span data-ttu-id="042cc-142">이 섹션에서는 입력 개체가 cmdlet 매개 변수에 바인딩되어 파이프라인 실행 중에 처리 되는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-142">This section explains how input objects are bound to cmdlet parameters and processed during pipeline execution.</span></span>

### <a name="accepts-pipeline-input"></a><span data-ttu-id="042cc-143">파이프라인 입력 허용</span><span class="sxs-lookup"><span data-stu-id="042cc-143">Accepts pipeline input</span></span>

<span data-ttu-id="042cc-144">파이프라인을 지원 하려면 수신 cmdlet에 파이프라인 입력을 허용 하는 매개 변수가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-144">To support pipelining, the receiving cmdlet must have a parameter that accepts pipeline input.</span></span> <span data-ttu-id="042cc-145">`Get-Help`명령을 **Full** 또는 **Parameter** 옵션과 함께 사용 하 여 파이프라인 입력을 허용 하는 cmdlet의 매개 변수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-145">Use the `Get-Help` command with the **Full** or **Parameter** options to determine which parameters of a cmdlet accept pipeline input.</span></span>

<span data-ttu-id="042cc-146">예를 들어 파이프라인 입력을 허용 하는 cmdlet의 매개 변수를 확인 하려면 `Start-Service` 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-146">For example, to determine which of the parameters of the `Start-Service` cmdlet accepts pipeline input, type:</span></span>

```powershell
Get-Help Start-Service -Full
```

<span data-ttu-id="042cc-147">or</span><span class="sxs-lookup"><span data-stu-id="042cc-147">or</span></span>

```powershell
Get-Help Start-Service -Parameter *
```

<span data-ttu-id="042cc-148">Cmdlet에 대 한 도움말에서는 `Start-Service` **InputObject** 및 **Name** 매개 변수만 파이프라인 입력을 허용 한다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-148">The help for the `Start-Service` cmdlet shows that only the **InputObject** and **Name** parameters accept pipeline input.</span></span>

```Output
-InputObject <ServiceController[]>
Specifies ServiceController objects representing the services to be started.
Enter a variable that contains the objects, or type a command or expression
that gets the objects.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByValue)
Accept wildcard characters?  false

-Name <String[]>
Specifies the service names for the service to be started.

The parameter name is optional. You can use Name or its alias, ServiceName,
or you can omit the parameter name.

Required?                    true
Position?                    0
Default value                None
Accept pipeline input?       True (ByPropertyName, ByValue)
Accept wildcard characters?  false
```

<span data-ttu-id="042cc-149">파이프라인을 통해 개체를로 보내면 `Start-Service` PowerShell에서 개체를 **InputObject** 및 **Name** 매개 변수와 연결 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-149">When you send objects through the pipeline to `Start-Service`, PowerShell attempts to associate the objects with the **InputObject** and **Name** parameters.</span></span>

### <a name="methods-of-accepting-pipeline-input"></a><span data-ttu-id="042cc-150">파이프라인 입력을 허용 하는 메서드</span><span class="sxs-lookup"><span data-stu-id="042cc-150">Methods of accepting pipeline input</span></span>

<span data-ttu-id="042cc-151">Cmdlet 매개 변수는 다음 두 가지 방법 중 하나로 파이프라인 입력을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-151">Cmdlets parameters can accept pipeline input in one of two different ways:</span></span>

- <span data-ttu-id="042cc-152">**Byvalue**: 매개 변수는 예상 되는 .net 유형과 일치 하거나 해당 형식으로 변환할 수 있는 값을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-152">**ByValue**: The parameter accepts values that match the expected .NET type or that can be converted to that type.</span></span>

  <span data-ttu-id="042cc-153">예를 들어의 **Name** 매개 변수는 `Start-Service` 값으로 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-153">For example, the **Name** parameter of `Start-Service` accepts pipeline input by value.</span></span> <span data-ttu-id="042cc-154">문자열로 변환할 수 있는 문자열 개체 또는 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-154">It can accept string objects or objects that can be converted to strings.</span></span>

- <span data-ttu-id="042cc-155">**Bypropertyname**: 매개 변수는 입력 개체에 매개 변수와 이름이 같은 속성이 있는 경우에만 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-155">**ByPropertyName**: The parameter accepts input only when the input object has a property of the same name as the parameter.</span></span>

  <span data-ttu-id="042cc-156">예를 들어의 Name 매개 변수는 `Start-Service` **name** 속성이 있는 개체를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-156">For example, the Name parameter of `Start-Service` can accept objects that have a **Name** property.</span></span> <span data-ttu-id="042cc-157">개체의 속성을 나열 하려면로 파이프 `Get-Member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-157">To list the properties of an object, pipe it to `Get-Member`.</span></span>

<span data-ttu-id="042cc-158">일부 매개 변수는 값 이나 속성 이름을 사용 하 여 개체를 받아들일 수 있으므로 파이프라인에서 더 쉽게 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-158">Some parameters can accept objects by both value or property name, making it easier to take input from the pipeline.</span></span>

### <a name="parameter-binding"></a><span data-ttu-id="042cc-159">매개 변수 바인딩</span><span class="sxs-lookup"><span data-stu-id="042cc-159">Parameter binding</span></span>

<span data-ttu-id="042cc-160">한 명령에서 다른 명령으로 개체를 파이프 하면 PowerShell에서 파이프 된 개체를 수신 cmdlet의 매개 변수와 연결 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-160">When you pipe objects from one command to another command, PowerShell attempts to associate the piped objects with a parameter of the receiving cmdlet.</span></span>

<span data-ttu-id="042cc-161">PowerShell의 매개 변수 바인딩 구성 요소는 다음 기준에 따라 입력 개체를 cmdlet 매개 변수와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-161">PowerShell's parameter binding component associates the input objects with cmdlet parameters according to the following criteria:</span></span>

- <span data-ttu-id="042cc-162">매개 변수는 파이프라인의 입력을 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-162">The parameter must accept input from a pipeline.</span></span>
- <span data-ttu-id="042cc-163">매개 변수는 전송 되는 개체의 형식 또는 필요한 형식으로 변환할 수 있는 형식을 수락 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-163">The parameter must accept the type of object being sent or a type that can be converted to the expected type.</span></span>
- <span data-ttu-id="042cc-164">매개 변수가 명령에 사용 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-164">The parameter wasn't used in the command.</span></span>

<span data-ttu-id="042cc-165">예를 들어 `Start-Service` cmdlet은 많은 매개 변수를 포함 하지만, **이름** 및 **InputObject** 는 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-165">For example, the `Start-Service` cmdlet has many parameters, but only two of them, **Name** and **InputObject** accept pipeline input.</span></span> <span data-ttu-id="042cc-166">**Name** 매개 변수는 문자열을 사용 하 고 **InputObject** 매개 변수는 서비스 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-166">The **Name** parameter takes strings and the **InputObject** parameter takes service objects.</span></span> <span data-ttu-id="042cc-167">따라서 문자열, 서비스 개체 및 개체를 문자열 또는 서비스 개체로 변환할 수 있는 속성으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-167">Therefore, you can pipe strings, service objects, and objects with properties that can be converted to string or service objects.</span></span>

<span data-ttu-id="042cc-168">PowerShell은 매개 변수 바인딩을 최대한 효율적으로 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-168">PowerShell manages parameter binding as efficiently as possible.</span></span> <span data-ttu-id="042cc-169">PowerShell이 특정 매개 변수에 바인딩되도록 제안 하거나 강제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-169">You can't suggest or force the PowerShell to bind to a specific parameter.</span></span> <span data-ttu-id="042cc-170">PowerShell에서 파이프 된 개체를 바인딩할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-170">The command fails if PowerShell can't bind the piped objects.</span></span>

<span data-ttu-id="042cc-171">바인딩 오류 문제 해결에 대 한 자세한 내용은이 문서의 뒷부분에 나오는 [파이프라인 오류 조사](#investigating-pipeline-errors) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="042cc-171">For more information about troubleshooting binding errors, see [Investigating Pipeline Errors](#investigating-pipeline-errors) later in this article.</span></span>

### <a name="one-at-a-time-processing"></a><span data-ttu-id="042cc-172">일회성 (일회성) 처리</span><span class="sxs-lookup"><span data-stu-id="042cc-172">One-at-a-time processing</span></span>

<span data-ttu-id="042cc-173">개체를 명령으로 파이프 하는 것은 명령의 매개 변수를 사용 하 여 개체를 제출 하는 것과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-173">Piping objects to a command is much like using a parameter of the command to submit the objects.</span></span> <span data-ttu-id="042cc-174">파이프라인 예제를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-174">Let's look at a pipeline example.</span></span> <span data-ttu-id="042cc-175">이 예제에서는 파이프라인을 사용 하 여 서비스 개체의 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-175">In this example, we use a pipeline to display a table of service objects.</span></span>

```powershell
Get-Service | Format-Table -Property Name, DependentServices
```

<span data-ttu-id="042cc-176">기능적으로의 **InputObject** 매개 변수를 사용 하 여 개체 컬렉션을 제출 하는 것과 같습니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="042cc-176">Functionally, this is like using the **InputObject** parameter of `Format-Table` to submit the object collection.</span></span>

<span data-ttu-id="042cc-177">예를 들어 **InputObject** 매개 변수를 사용 하 여 전달 된 변수에 서비스 컬렉션을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-177">For example, we can save the collection of services to a variable that is passed using the **InputObject** parameter.</span></span>

```powershell
$services = Get-Service
Format-Table -InputObject $services -Property Name, DependentServices
```

<span data-ttu-id="042cc-178">또는 **InputObject** 매개 변수에 명령을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-178">Or we can embed the command in the **InputObject** parameter.</span></span>

```powershell
Format-Table -InputObject (Get-Service) -Property Name, DependentServices
```

<span data-ttu-id="042cc-179">그러나 중요 한 차이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-179">However, there's an important difference.</span></span> <span data-ttu-id="042cc-180">여러 개체를 명령으로 파이프 하면 PowerShell에서 한 번에 하나씩 명령에 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-180">When you pipe multiple objects to a command, PowerShell sends the objects to the command one at a time.</span></span> <span data-ttu-id="042cc-181">명령 매개 변수를 사용 하는 경우 개체는 단일 배열 개체로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-181">When you use a command parameter, the objects are sent as a single array object.</span></span> <span data-ttu-id="042cc-182">이러한 사소한 차이로 인해 상당한 결과가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-182">This minor difference has significant consequences.</span></span>

<span data-ttu-id="042cc-183">파이프라인을 실행 하는 경우 PowerShell은 인터페이스를 구현 하는 모든 형식을 자동으로 열거 `IEnumerable` 하 고 파이프라인을 통해 한 번에 하나씩 멤버를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-183">When executing a pipeline, PowerShell automatically enumerates any type that implements the `IEnumerable` interface and sends the members through the pipeline one at a time.</span></span> <span data-ttu-id="042cc-184">예외는입니다 .이 경우에는 `[hashtable]` 메서드를 호출 해야 `GetEnumerator()` 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-184">The exception is `[hashtable]`, which requires a call to the `GetEnumerator()` method.</span></span>

<span data-ttu-id="042cc-185">다음 예제에서는 배열과 해시 테이블을 cmdlet으로 파이프 하 여 `Measure-Object` 파이프라인에서 받은 개체 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-185">In the following examples, an array and a hashtable are piped to the `Measure-Object` cmdlet to count the number of objects received from the pipeline.</span></span> <span data-ttu-id="042cc-186">배열에 여러 멤버가 있고 해시 테이블에 여러 개의 키-값 쌍이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-186">The array has multiple members, and the hashtable has multiple key-value pairs.</span></span> <span data-ttu-id="042cc-187">배열에 한 번에 하나씩만 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-187">Only the array is enumerated one at a time.</span></span>

```powershell
@(1,2,3) | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

```powershell
@{"One"=1;"Two"=2} | Measure-Object
```

```Output
Count    : 1
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

<span data-ttu-id="042cc-188">마찬가지로, cmdlet에서 cmdlet으로 여러 프로세스 개체를 파이프 하는 경우 `Get-Process` `Get-Member` PowerShell은 각 프로세스 개체를 한 번에 하나씩로 보냅니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="042cc-188">Similarly, if you pipe multiple process objects from the `Get-Process` cmdlet to the `Get-Member` cmdlet, PowerShell sends each process object, one at a time, to `Get-Member`.</span></span> <span data-ttu-id="042cc-189">`Get-Member` 프로세스 개체의 .NET 클래스 (형식)와 해당 속성 및 메서드를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-189">`Get-Member` displays the .NET class (type) of the process objects, and their properties and methods.</span></span>

```powershell
Get-Process | Get-Member
```

```Output
TypeName: System.Diagnostics.Process

Name      MemberType     Definition
----      ----------     ----------
Handles   AliasProperty  Handles = Handlecount
Name      AliasProperty  Name = ProcessName
NPM       AliasProperty  NPM = NonpagedSystemMemorySize
...
```

> [!NOTE]
> <span data-ttu-id="042cc-190">`Get-Member` 중복을 제거 하므로 개체가 모두 동일한 형식이 면 하나의 개체 유형만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-190">`Get-Member` eliminates duplicates, so if the objects are all of the same type, it only displays one object type.</span></span>

<span data-ttu-id="042cc-191">그러나의 **InputObject** 매개 변수를 사용 하는 경우은 (는) `Get-Member` `Get-Member` 단일 단위로 **시스템 진단** 개체의 배열을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-191">However, if you use the **InputObject** parameter of `Get-Member`, then `Get-Member` receives an array of **System.Diagnostics.Process** objects as a single unit.</span></span> <span data-ttu-id="042cc-192">개체의 배열 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-192">It displays the properties of an array of objects.</span></span> <span data-ttu-id="042cc-193">(System.string 형식 이름 뒤의 배열 기호 ()를 적어둡니다 `[]` .) </span><span class="sxs-lookup"><span data-stu-id="042cc-193">(Note the array symbol (`[]`) after the **System.Object** type name.)</span></span>

<span data-ttu-id="042cc-194">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-194">For example,</span></span>

```powershell
Get-Member -InputObject (Get-Process)
```

```Output
TypeName: System.Object[]

Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
Address            Method        System.Object& Address(Int32 )
Clone              Method        System.Object Clone()
...
```

<span data-ttu-id="042cc-195">이 결과는 의도 한 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-195">This result might not be what you intended.</span></span> <span data-ttu-id="042cc-196">그러나 이해 한 후에는 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-196">But after you understand it, you can use it.</span></span> <span data-ttu-id="042cc-197">예를 들어 모든 배열 개체에는 **Count** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-197">For example, all array objects have a **Count** property.</span></span> <span data-ttu-id="042cc-198">이를 사용 하 여 컴퓨터에서 실행 되는 프로세스 수를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-198">You can use that to count the number of processes running on the computer.</span></span>

<span data-ttu-id="042cc-199">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-199">For example,</span></span>

```powershell
(Get-Process).count
```

<span data-ttu-id="042cc-200">파이프라인으로 전송 되는 개체는 한 번에 하나씩 배달 된다는 점을 기억해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-200">It's important to remember that objects sent down the pipeline are delivered one at a time.</span></span>

## <a name="investigating-pipeline-errors"></a><span data-ttu-id="042cc-201">파이프라인 오류 조사</span><span class="sxs-lookup"><span data-stu-id="042cc-201">Investigating pipeline errors</span></span>

<span data-ttu-id="042cc-202">PowerShell에서 파이프 된 개체를 수신 cmdlet의 매개 변수와 연결할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-202">When PowerShell can't associate the piped objects with a parameter of the receiving cmdlet, the command fails.</span></span>

<span data-ttu-id="042cc-203">다음 예제에서는 레지스트리 키 간에 레지스트리 항목을 이동 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-203">In the following example, we try to move a registry entry from one registry key to another.</span></span> <span data-ttu-id="042cc-204">`Get-Item`Cmdlet은 대상 경로를 가져온 다음 cmdlet에 파이프 합니다 `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="042cc-204">The `Get-Item` cmdlet gets the destination path, which is then piped to the `Move-ItemProperty` cmdlet.</span></span> <span data-ttu-id="042cc-205">`Move-ItemProperty`명령은 이동할 레지스트리 항목의 현재 경로 및 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-205">The `Move-ItemProperty` command specifies the current path and name of the registry entry to be moved.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales |
Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
```

<span data-ttu-id="042cc-206">명령이 실패 하 고 PowerShell에서 다음과 같은 오류 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-206">The command fails and PowerShell displays the following error message:</span></span>

```Output
Move-ItemProperty : The input object can't be bound to any parameters for
the command either because the command doesn't take pipeline input or the
input and its properties do not match any of the parameters that take
pipeline input.
At line:1 char:23
+ $a | Move-ItemProperty <<<<  -Path HKLM:\Software\MyCompany\design -Name p
```

<span data-ttu-id="042cc-207">조사 하려면 cmdlet을 사용 `Trace-Command` 하 여 PowerShell의 매개 변수 바인딩 구성 요소를 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-207">To investigate, use the `Trace-Command` cmdlet to trace the parameter binding component of PowerShell.</span></span> <span data-ttu-id="042cc-208">다음 예제에서는 파이프라인이 실행 되는 동안 매개 변수 바인딩을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-208">The following example traces parameter binding while the pipeline is executing.</span></span> <span data-ttu-id="042cc-209">**PSHost** 매개 변수는 콘솔에 추적 결과를 표시 하 고 **FilePath** 매개 변수는 나중에 참조할 수 있도록 추적 결과를 `debug.txt` 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-209">The **PSHost** parameter displays the trace results in the console and the **FilePath** parameter send the trace results to the `debug.txt` file for later reference.</span></span>

```powershell
Trace-Command -Name ParameterBinding -PSHost -FilePath debug.txt -Expression {
  Get-Item -Path HKLM:\Software\MyCompany\sales |
    Move-ItemProperty -Path HKLM:\Software\MyCompany\design -Name product
}
```

<span data-ttu-id="042cc-210">추적 결과는 긴 하지만 cmdlet에 바인딩되는 값을 표시 한 `Get-Item` 다음 cmdlet에 바인딩되는 명명 된 값을 표시 합니다 `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="042cc-210">The results of the trace are lengthy, but they show the values being bound to the `Get-Item` cmdlet and then the named values being bound to the `Move-ItemProperty` cmdlet.</span></span>

```Output
...
BIND NAMED cmd line args [`Move-ItemProperty`]
BIND arg [HKLM:\Software\MyCompany\design] to parameter [Path]
...
BIND arg [product] to parameter [Name]
...
BIND POSITIONAL cmd line args [`Move-ItemProperty`]
...
```

<span data-ttu-id="042cc-211">마지막으로 경로를의 **대상** 매개 변수에 바인딩하려는 시도가 실패 한 것을 보여 줍니다 `Move-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="042cc-211">Finally, it shows that the attempt to bind the path to the **Destination** parameter of `Move-ItemProperty` failed.</span></span>

```Output
...
BIND PIPELINE object to parameters: [`Move-ItemProperty`]
PIPELINE object TYPE = [Microsoft.Win32.RegistryKey]
RESTORING pipeline parameter's original values
Parameter [Destination] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
Parameter [Credential] PIPELINE INPUT ValueFromPipelineByPropertyName NO
COERCION
...
```

<span data-ttu-id="042cc-212">Cmdlet을 사용 `Get-Help` 하 여 **Destination** 매개 변수의 특성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-212">Use the `Get-Help` cmdlet to view the attributes of the **Destination** parameter.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Destination

-Destination <String>
    Specifies the path to the destination location.

    Required?                    true
    Position?                    1
    Default value                None
    Accept pipeline input?       True (ByPropertyName)
    Accept wildcard characters?  false
```

<span data-ttu-id="042cc-213">결과는 **대상** 에서 파이프라인 입력만 "속성 이름"으로 사용 함을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-213">The results show that **Destination** takes pipeline input only "by property name".</span></span> <span data-ttu-id="042cc-214">따라서 파이프 된 개체에는 **Destination** 이라는 속성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-214">Therefore, the piped object must have a property named **Destination**.</span></span>

<span data-ttu-id="042cc-215">`Get-Member`에서 들어오는 개체의 속성을 보려면를 사용 `Get-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-215">Use `Get-Member` to see the properties of the object coming from `Get-Item`.</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\sales | Get-Member
```

<span data-ttu-id="042cc-216">출력은 항목이 **대상** 속성이 없는 **Microsoft Win32 RegistryKey** 개체 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-216">The output shows that the item is a **Microsoft.Win32.RegistryKey** object that doesn't have a **Destination** property.</span></span> <span data-ttu-id="042cc-217">명령이 실패 한 이유를 설명 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-217">That explains why the command failed.</span></span>

<span data-ttu-id="042cc-218">**Path** 매개 변수는 이름이 나 값을 기준으로 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-218">The **Path** parameter accepts pipeline input by name or by value.</span></span>

```Output
Get-Help Move-ItemProperty -Parameter Path

-Path <String[]>
    Specifies the path to the current location of the property. Wildcard
    characters are permitted.

    Required?                    true
    Position?                    0
    Default value                None
    Accept pipeline input?       True (ByPropertyName, ByValue)
    Accept wildcard characters?  true
```

<span data-ttu-id="042cc-219">명령을 수정 하려면 cmdlet에서 대상을 지정 하 `Move-ItemProperty` 고를 사용 `Get-Item` 하 여 이동 하려는 항목의 **경로** 를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-219">To fix the command, we must specify the destination in the `Move-ItemProperty` cmdlet and use `Get-Item` to get the **Path** of the item we want to move.</span></span>

<span data-ttu-id="042cc-220">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-220">For example,</span></span>

```powershell
Get-Item -Path HKLM:\Software\MyCompany\design |
Move-ItemProperty -Destination HKLM:\Software\MyCompany\sales -Name product
```

## <a name="intrinsic-line-continuation"></a><span data-ttu-id="042cc-221">내장 선 연속</span><span class="sxs-lookup"><span data-stu-id="042cc-221">Intrinsic line continuation</span></span>

<span data-ttu-id="042cc-222">앞서 설명한 것 처럼 파이프라인은 `|` 일반적으로 단일 줄로 작성 된 파이프라인 연산자 ()로 연결 되는 일련의 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-222">As already discussed, a pipeline is a series of commands connected by pipeline operators (`|`), usually written on a single line.</span></span> <span data-ttu-id="042cc-223">그러나 가독성을 위해 PowerShell을 사용 하면 파이프라인을 여러 줄로 분할할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-223">However, for readability, PowerShell allows you to split the pipeline across multiple lines.</span></span>
<span data-ttu-id="042cc-224">파이프 연산자가 줄의 마지막 토큰이 면 PowerShell 파서는 다음 줄을 현재 명령에 조인 하 여 파이프라인 생성을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-224">When a pipe operator is the last token on the line, the PowerShell parser joins the next line to current command to continue the construction of the pipeline.</span></span>

<span data-ttu-id="042cc-225">예를 들어 다음 한 줄 파이프라인이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-225">For example, the following single-line pipeline:</span></span>

```powershell
Command-1 | Command-2 | Command-3
```

<span data-ttu-id="042cc-226">다음과 같이 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-226">can be written as:</span></span>

```powershell
Command-1 |
  Command-2 |
    Command-3
```

<span data-ttu-id="042cc-227">후속 줄의 선행 공백은 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-227">The leading spaces on the subsequent lines are not significant.</span></span> <span data-ttu-id="042cc-228">들여쓰기는 가독성을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-228">The indentation enhances readability.</span></span>

<span data-ttu-id="042cc-229">PowerShell 7은 줄의 시작 부분에 파이프라인 문자를 사용 하 여 파이프라인의 연속에 대 한 지원을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-229">PowerShell 7 adds support for continuation of pipelines with the pipeline character at the beginning of a line.</span></span> <span data-ttu-id="042cc-230">다음 예에서는이 새 기능을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-230">The following examples show how you could use this new functionality.</span></span>

```powershell
# Wrapping with a pipe at the beginning of a line (no backtick required)
Get-Process | Where-Object CPU | Where-Object Path
    | Get-Item | Where-Object FullName -match "AppData"
    | Sort-Object FullName -Unique

# Wrapping with a pipe on a line by itself
Get-Process | Where-Object CPU | Where-Object Path
    |
    Get-Item | Where-Object FullName -match "AppData"
    |
    Sort-Object FullName -Unique
```

> [!IMPORTANT]
> <span data-ttu-id="042cc-231">셸에서 대화형으로 작업 하는 경우 <kbd>Ctrl</kbd>V를 사용 하 여 붙여 넣는 경우에만 줄의 시작 부분에 파이프라인을 사용 하 여 코드를 붙여 + <kbd></kbd> 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-231">When working interactively in the shell, pasting code with pipelines at the beginning of a line only when using <kbd>Ctrl</kbd>+<kbd>V</kbd> to paste.</span></span>
> <span data-ttu-id="042cc-232">붙여넣기 작업을 마우스 오른쪽 단추로 클릭 하면 한 번에 하나씩 줄이 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-232">Right-click paste operations insert the lines one at a time.</span></span> <span data-ttu-id="042cc-233">줄이 파이프라인 문자로 끝나지 않으므로 PowerShell은 입력을 완료 한 것으로 간주 하 고 입력 한 대로 해당 줄을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="042cc-233">Since the line does not end with a pipeline character, PowerShell considers the input to be complete and executes that line as entered.</span></span>

## <a name="see-also"></a><span data-ttu-id="042cc-234">참고 항목</span><span class="sxs-lookup"><span data-stu-id="042cc-234">See Also</span></span>

[<span data-ttu-id="042cc-235">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="042cc-235">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="042cc-236">about_Objects</span><span class="sxs-lookup"><span data-stu-id="042cc-236">about_Objects</span></span>](about_objects.md)

[<span data-ttu-id="042cc-237">about_Parameters</span><span class="sxs-lookup"><span data-stu-id="042cc-237">about_Parameters</span></span>](about_parameters.md)

[<span data-ttu-id="042cc-238">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="042cc-238">about_Command_Syntax</span></span>](about_command_syntax.md)

[<span data-ttu-id="042cc-239">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="042cc-239">about_ForEach</span></span>](about_foreach.md)

