---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 22e6a8de2b52039e0a23cab135f81ff74bdf929a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217370"
---
# <span data-ttu-id="53463-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="53463-103">Out-GridView</span></span>

## <span data-ttu-id="53463-104">개요</span><span class="sxs-lookup"><span data-stu-id="53463-104">SYNOPSIS</span></span>
<span data-ttu-id="53463-105">별도의 창에 있는 대화형 테이블로 출력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="53463-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53463-106">SYNTAX</span></span>

### <span data-ttu-id="53463-107">PassThru (기본값)</span><span class="sxs-lookup"><span data-stu-id="53463-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="53463-108">연결 시도 간격</span><span class="sxs-lookup"><span data-stu-id="53463-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="53463-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="53463-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="53463-110">설명</span><span class="sxs-lookup"><span data-stu-id="53463-110">DESCRIPTION</span></span>

<span data-ttu-id="53463-111">Cmdlet은 출력을 `Out-GridView` 대화형 테이블에 표시 하는 그리드 뷰 창에 명령의 출력을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="53463-112">이 cmdlet은 사용자 인터페이스를 필요로 하기 때문에 Windows Server Core 또는 Windows Nano Server에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="53463-113">다음 테이블 기능을 사용하여 데이터를 조사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="53463-114">열 숨기기, 표시 및 순서 바꾸기</span><span class="sxs-lookup"><span data-stu-id="53463-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="53463-115">행 정렬</span><span class="sxs-lookup"><span data-stu-id="53463-115">Sort rows</span></span>
- <span data-ttu-id="53463-116">빠른 필터</span><span class="sxs-lookup"><span data-stu-id="53463-116">Quick Filter</span></span>
- <span data-ttu-id="53463-117">조건 필터 추가</span><span class="sxs-lookup"><span data-stu-id="53463-117">Add Criteria Filter</span></span>
- <span data-ttu-id="53463-118">복사 및 붙여넣기</span><span class="sxs-lookup"><span data-stu-id="53463-118">Copy and paste</span></span>

<span data-ttu-id="53463-119">전체 지침은이 문서의 [참고](#notes) 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53463-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="53463-120">이 cmdlet은 PowerShell 7에서 다시 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-120">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="53463-121">이 cmdlet은 Windows 데스크톱을 지 원하는 Windows 시스템 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-121">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span> <span data-ttu-id="53463-122">이 cmdlet의 플랫폼 간 버전은 PowerShell 갤러리 [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) 모듈을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53463-122">For a cross-platform version of this cmdlet, see the [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) module in the PowerShell Gallery.</span></span>

## <span data-ttu-id="53463-123">예제</span><span class="sxs-lookup"><span data-stu-id="53463-123">EXAMPLES</span></span>

### <span data-ttu-id="53463-124">예제 1: 표 뷰로 출력 프로세스</span><span class="sxs-lookup"><span data-stu-id="53463-124">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="53463-125">이 예제에서는 로컬 컴퓨터에서 실행 중인 프로세스를 가져와 그리드 뷰 창으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-125">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="53463-126">예제 2: 변수를 사용 하 여 프로세스를 그리드 뷰로 출력</span><span class="sxs-lookup"><span data-stu-id="53463-126">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="53463-127">또한이 예제에서는 로컬 컴퓨터에서 실행 중인 프로세스를 가져와 그리드 뷰 창으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-127">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="53463-128">Cmdlet의 출력 `Get-Process` 은 변수에 저장 됩니다 `$P` .</span><span class="sxs-lookup"><span data-stu-id="53463-128">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="53463-129">그런 다음 `$P` 가로 파이프 됩니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-129">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="53463-130">예제 3: 그리드 보기에서 선택한 속성 표시</span><span class="sxs-lookup"><span data-stu-id="53463-130">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="53463-131">이 예에서는 실행 중인 프로세스의 선택 된 속성을 그리드 보기에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-131">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="53463-132">의 출력은 `Get-Process` `Select-Object` **Name** , **WorkingSet** 및 **PeakWorkingSet** 속성을 선택 하기 위해로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-132">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="53463-133">다른 파이프라인 연산자는 필터링 된 개체를 cmdlet으로 보내 `Sort-Object` **WorkingSet** 속성의 값을 기준으로 내림차순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-133">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="53463-134">그런 다음 정렬 된 결과를로 파이프 `Out-GridView` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-134">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="53463-135">그런 다음에는 그리드 뷰의 기능을 사용하여 데이터를 검색, 정렬 및 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-135">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="53463-136">예 4: 출력을 변수에 저장 한 다음 그리드 보기 출력</span><span class="sxs-lookup"><span data-stu-id="53463-136">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="53463-137">이 예에서는 변수에 cmdlet 출력을 저장 한 다음로 보냅니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-137">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="53463-138">`Get-ChildItem` 자동 변수를 사용 하 여 PowerShell 설치 디렉터리 및 해당 하위 디렉터리에 있는 모든 파일을 가져옵니다 `$PSHOME` .</span><span class="sxs-lookup"><span data-stu-id="53463-138">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="53463-139">명령의 괄호는 연산 순서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-139">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="53463-140">따라서 `Get-ChildItem` 명령의 출력이 `$A` 에 전송 되기 전에 변수에 저장 됩니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-140">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="53463-141">예 5: 지정 된 컴퓨터에 대 한 프로세스를 그리드 뷰에 출력</span><span class="sxs-lookup"><span data-stu-id="53463-141">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="53463-142">이 예에서는 Server01 컴퓨터에서 실행 중인 프로세스를 그리드 뷰 창에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-142">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="53463-143">Examle는 `ogv` cmdlet에 대 한 별칭인를 사용 합니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-143">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="53463-144">**Title** 매개 변수는 창 제목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-144">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="53463-145">예 6: 원격 컴퓨터의 데이터를 그리드 보기에 출력</span><span class="sxs-lookup"><span data-stu-id="53463-145">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="53463-146">이 예제에서는 원격 컴퓨터에서 수집 된 데이터를로 보내는 방법을 보여 줍니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-146">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="53463-147">`Invoke-Command` 는 `Get-Culture` 세 대의 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-147">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="53463-148">결과 데이터는로 파이프 됩니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-148">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="53463-149">원격 컴퓨터에서 실행 되는 스크립트 블록에는 명령이 포함 되지 않습니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-149">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="53463-150">이 명령이 포함된 경우에는 명령이 각 원격 컴퓨터에서 그리드 뷰 창을 열려고 할 때 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-150">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="53463-151">예제 7:를 통해 여러 항목 전달 `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="53463-151">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="53463-152">이 예에서는 창에서 여러 프로세스를 선택할 수 있습니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-152">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="53463-153">선택한 프로세스가 명령에 전달 되 `Export-Csv` 고 파일에 기록 됩니다 `ProcessLog.csv` .</span><span class="sxs-lookup"><span data-stu-id="53463-153">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="53463-154">의 **PassThru** 매개 변수를 `Out-GridView` 사용 하 여 파이프라인에서 여러 항목을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-154">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="53463-155">**PassThru** 매개 변수는 **OutputMode** 매개 변수의 **Multiple** 값을 사용하는 경우와 동일한 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-155">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="53463-156">예 8: Windows 바로 가기를 만듭니다. `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="53463-156">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="53463-157">이 예에서는의 **Wait** 매개 변수를 사용 하 여 `Out-GridView` 창에 대 한 Windows 바로 가기를 만드는 방법을 보여 줍니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-157">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="53463-158">이 명령줄은 Windows 바로 가기에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-158">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="53463-159">**Wait** 매개 변수가 없으면 창이 열리는 즉시 PowerShell이 종료 됩니다 `Out-GridView` `Out-GridView` . 그러면 창이 거의 즉시 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-159">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="53463-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53463-160">PARAMETERS</span></span>

### <span data-ttu-id="53463-161">-InputObject</span><span class="sxs-lookup"><span data-stu-id="53463-161">-InputObject</span></span>

<span data-ttu-id="53463-162">Cmdlet이에 대 한 입력으로 허용 하는 개체를 지정 합니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-162">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="53463-163">**InputObject** 매개 변수를 사용 하 여 개체 컬렉션을로 보내는 경우 `Out-GridView` 는 `Out-GridView` 컬렉션을 하나의 컬렉션 개체로 처리 하 고 컬렉션을 나타내는 행 하나를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-163">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="53463-164">컬렉션의 각 개체를 표시 하려면 파이프라인 연산자 (|)를 사용 하 여 개체를로 보냅니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-164">To display the each object in the collection, use a pipeline operator (|) to send objects to `Out-GridView`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="53463-165">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="53463-165">-OutputMode</span></span>

<span data-ttu-id="53463-166">대화형 창이 파이프라인을 다른 명령에 대 한 입력으로 전송 하는 항목을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-166">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="53463-167">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-167">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="53463-168">대화형 창의 항목을 파이프라인으로 보내려면 항목을 클릭하여 선택한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-168">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="53463-169">이 매개 변수 값이 파이프라인으로 보낼 수 있는 항목 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-169">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="53463-170">없음</span><span class="sxs-lookup"><span data-stu-id="53463-170">None.</span></span>  <span data-ttu-id="53463-171">항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-171">No items.</span></span> <span data-ttu-id="53463-172">이것은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="53463-172">This is the default value.</span></span>
- <span data-ttu-id="53463-173">단일:</span><span class="sxs-lookup"><span data-stu-id="53463-173">Single.</span></span> <span data-ttu-id="53463-174">0개의 항목 또는 1개의 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="53463-174">Zero items or one item.</span></span> <span data-ttu-id="53463-175">다음 명령에서 입력 개체를 하나만 사용할 수 있는 경우 이 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-175">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="53463-176">배수로.</span><span class="sxs-lookup"><span data-stu-id="53463-176">Multiple.</span></span> <span data-ttu-id="53463-177">0개, 1개 또는 많은 항목.</span><span class="sxs-lookup"><span data-stu-id="53463-177">Zero, one, or many items.</span></span> <span data-ttu-id="53463-178">다음 명령에서 여러 개의 입력 개체를 사용할 수 있는 경우 이 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-178">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="53463-179">이 값은 **Passthru** 매개 변수와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-179">This value is equivalent to the **Passthru** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53463-180">-PassThru</span><span class="sxs-lookup"><span data-stu-id="53463-180">-PassThru</span></span>

<span data-ttu-id="53463-181">Cmdlet이 대화형 창의 항목을 다른 명령에 대 한 입력으로 파이프라인에서 보내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-181">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="53463-182">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-182">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="53463-183">이 매개 변수는 **OutputMode** 매개 변수의 **Multiple** 값을 사용하는 경우와 동일한 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-183">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="53463-184">대화형 창의 항목을 파이프라인으로 보내려면 항목을 클릭하여 선택한 다음 확인을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-184">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="53463-185">Shift 키나 Ctrl 키를 누른 상태에서 클릭할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-185">Shift-click and Ctrl-click are supported.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53463-186">-Title</span><span class="sxs-lookup"><span data-stu-id="53463-186">-Title</span></span>

<span data-ttu-id="53463-187">창의 제목 표시줄에 표시 되는 텍스트를 지정 합니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-187">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="53463-188">기본적으로 제목 표시줄에는를 호출 하는 명령이 표시 됩니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-188">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53463-189">-Wait</span><span class="sxs-lookup"><span data-stu-id="53463-189">-Wait</span></span>

<span data-ttu-id="53463-190">Cmdlet이 명령 프롬프트를 표시 하지 않고 창이 닫힐 때까지 Windows PowerShell을 닫지 않도록 지정 합니다 `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="53463-190">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="53463-191">기본적으로 창이 열리면 명령 프롬프트가 반환 `Out-GridView` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-191">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="53463-192">이 기능을 사용 하면 `Out-GridView` Windows 바로 가기에서 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-192">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="53463-193">`Out-GridView` **Wait** 매개 변수 없이 바로 가기에서를 사용 하면 `Out-GridView` PowerShell을 닫기 전에 창이 일시적 으로만 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53463-193">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53463-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53463-194">CommonParameters</span></span>

<span data-ttu-id="53463-195">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53463-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53463-196">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53463-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53463-197">입력</span><span class="sxs-lookup"><span data-stu-id="53463-197">INPUTS</span></span>

### <span data-ttu-id="53463-198">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="53463-198">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="53463-199">이 cmdlet에 개체를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-199">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="53463-200">출력</span><span class="sxs-lookup"><span data-stu-id="53463-200">OUTPUTS</span></span>

### <span data-ttu-id="53463-201">없음</span><span class="sxs-lookup"><span data-stu-id="53463-201">None</span></span>

<span data-ttu-id="53463-202">일반적으로는 `Out-GridView` 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-202">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="53463-203">**PassThru** 매개 변수를 사용 하는 경우 선택한 행을 나타내는 개체가 파이프라인으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-203">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="53463-204">참고</span><span class="sxs-lookup"><span data-stu-id="53463-204">NOTES</span></span>

<span data-ttu-id="53463-205">원격 명령을 사용하여 다른 컴퓨터에서 그리드 뷰 창을 열 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-205">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="53463-206">로 전송 하는 명령 출력은 `Out-GridView` `Format` cmdlet (예: 또는 cmdlet)을 사용 하 여 포맷할 수 없습니다 `Format-Table` `Format-Wide` .</span><span class="sxs-lookup"><span data-stu-id="53463-206">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="53463-207">속성을 선택 하려면 cmdlet을 사용 `Select-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-207">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="53463-208">원격 명령에서 역직렬화된 출력은 그리드 뷰 창에서 서식이 제대로 지정되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-208">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="53463-209">**바로 가기 키**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="53463-209">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="53463-210">사용할 키:</span><span class="sxs-lookup"><span data-stu-id="53463-210">Use this key:</span></span>              |                                   <span data-ttu-id="53463-211">수행할 작업:</span><span class="sxs-lookup"><span data-stu-id="53463-211">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="53463-212"><kbd>탭</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-212"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="53463-213">커서를 **필터** 상자에서 **조건 추가** 메뉴로 이동 하 여 다시 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-213">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="53463-214"><kbd>서 위쪽 화살표</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-214"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="53463-215">한 행 위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-215">Move up one row.</span></span> <span data-ttu-id="53463-216">첫 번째 데이터 행의 열 머리글로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-216">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="53463-217"><kbd>아래쪽 화살표</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-217"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="53463-218">한 행 아래로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-218">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="53463-219"><kbd>왼쪽 화살표</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-219"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="53463-220">열 머리글 행에서 한 열 왼쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-220">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="53463-221"><kbd>오른쪽 화살표</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-221"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="53463-222">열 머리글 행에서 한 열 오른쪽으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-222">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="53463-223"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-223"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="53463-224">열 머리글 행에 열 선택 옵션을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-224">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="53463-225"><kbd>Enter</kbd> 또는 <kbd>스페이스바</kbd></span><span class="sxs-lookup"><span data-stu-id="53463-225"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="53463-226">열 머리글 행에서 열 데이터를 정렬 합니다 (a-z, A-z).</span><span class="sxs-lookup"><span data-stu-id="53463-226">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="53463-227">**그리드 뷰 창 기능을 사용 하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-227">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="53463-228">**열을 숨기거나 표시하려면:**</span><span class="sxs-lookup"><span data-stu-id="53463-228">**To hide or show a column:**</span></span>

1. <span data-ttu-id="53463-229">열 머리글을 마우스 오른쪽 단추로 클릭 하 고 **열 선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-229">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="53463-230">**열 선택** 대화 상자에서 화살표 키를 사용 하 여 선택한 열 사이에 있는 열을 사용 가능한 열 상자로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-230">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="53463-231">**열 선택** 상자의 열만 그리드 뷰 창에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-231">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="53463-232">**열의 순서를 바꾸려면:**</span><span class="sxs-lookup"><span data-stu-id="53463-232">**To reorder columns:**</span></span>

<span data-ttu-id="53463-233">열을 원하는 위치로 끌어서 놓을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-233">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="53463-234">또는 다음 단계를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-234">Or use the following steps:</span></span>

1. <span data-ttu-id="53463-235">열 머리글을 마우스 오른쪽 단추로 클릭 하 고 **열 선택** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-235">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="53463-236">**열 선택** 대화 상자에서 **위로 이동** 및 **아래로 이동** 단추를 사용 하 여 열을 다시 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-236">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="53463-237">목록 맨 위에 있는 열은 그리드 뷰 창의 목록 맨 아래에 있는 열의 왼쪽에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="53463-237">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="53463-238">**테이블 데이터를 정렬하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-238">**How to Sort Table Data**</span></span>

- <span data-ttu-id="53463-239">데이터를 정렬하려면 열 머리글을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-239">To sort the data, click a column header.</span></span>
- <span data-ttu-id="53463-240">정렬 순서를 변경 하려면 열 머리글을 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-240">To change the sort order, click the column header again.</span></span> <span data-ttu-id="53463-241">같은 머리글을 클릭할 때마다 정렬 순서가 오름차순과 내림차순 간에 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-241">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="53463-242">현재 순서는 열 머리글의 삼각형으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-242">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="53463-243">**테이블 데이터를 정렬하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-243">**How to Select Table Data**</span></span>

- <span data-ttu-id="53463-244">행을 선택 하려면 행을 선택 하거나 위쪽 또는 아래쪽 화살표를 사용 하 여 행으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-244">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="53463-245">머리글 행을 제외 하 고 모든 행을 선택 하려면 <kbd>ctrl</kbd> + <kbd>A</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-245">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="53463-246">연속 된 행을 선택 하려면 <kbd>shift</kbd> 키를 누른 상태에서 행을 클릭 하거나 화살표 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-246">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="53463-247">비연속적인 행을 선택 하려면 Ctrl 키를 누른 <kbd>채</kbd> 클릭 하 여 선택 영역에 행을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-247">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="53463-248">열이나 전체 열 머리글 행은 선택할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-248">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="53463-249">**행을 복사하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-249">**How to Copy Rows**</span></span>

- <span data-ttu-id="53463-250">테이블에서 하나 이상의 행을 복사 하려면 행을 선택 하 고 CTRL + C를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="53463-250">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="53463-251">복사한 데이터는 원하는 텍스트 또는 스프레드시트 프로그램에 붙여 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-251">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="53463-252">열 또는 행의 일부나 열 머리글 행은 복사할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-252">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="53463-253">**테이블에서 검색 하는 방법 (빠른 필터)**</span><span class="sxs-lookup"><span data-stu-id="53463-253">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="53463-254">필터 상자를 사용 하 여 테이블에서 데이터를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-254">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="53463-255">상자에 입력하면 입력한 텍스트가 포함된 항목만 테이블에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-255">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="53463-256">텍스트를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-256">Search for text.</span></span> <span data-ttu-id="53463-257">테이블에서 텍스트를 검색 하려면 필터 상자에 찾을 텍스트를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-257">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="53463-258">여러 단어를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-258">Search for multiple words.</span></span> <span data-ttu-id="53463-259">테이블에서 여러 단어를 검색하려면 단어를 공백으로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-259">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="53463-260">`Out-GridView` 모든 단어 (논리적 AND)를 포함 하는 행을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-260">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="53463-261">리터럴 구를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-261">Search for literal phrases.</span></span> <span data-ttu-id="53463-262">공백이나 특수 문자가 포함된 구를 검색하려면 구를 따옴표로 묶어 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-262">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="53463-263">`Out-GridView` 구와 정확히 일치 하는 항목을 포함 하는 행을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-263">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="53463-264">열에서 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-264">Search in columns.</span></span> <span data-ttu-id="53463-265">하나 이상의 열에서 텍스트를 검색하려면 다음 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-265">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="53463-266">예를 들어 **DisplayName** 열에서 "Net"을 찾으려면 **필터** 상자에 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-266">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="53463-267">**DisplayName** 및 **Name** 열에서 "Net"이 포함 된 행을 찾으려면 **필터** 상자에 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-267">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="53463-268">검색을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-268">Turn off search.</span></span> <span data-ttu-id="53463-269">전체 테이블을 다시 표시 하려면 **필터** 상자의 오른쪽 위 모서리에 있는 빨간색 X 단추를 클릭 하거나 **필터** 상자에서 텍스트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-269">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="53463-270">**조건을 사용하여 테이블 필터링**</span><span class="sxs-lookup"><span data-stu-id="53463-270">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="53463-271">규칙 또는 조건을 사용 하 여 테이블에 표시 되는 항목을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-271">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="53463-272">항목은 사용자가 설정한 모든 조건을 충족 하는 경우에만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-272">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="53463-273">사용 가능한 조건은 그리드 뷰 창에 표시되는 개체의 속성 및 이러한 속성의 .NET Framework 유형에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-273">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="53463-274">각 조건의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-274">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="53463-275">다른 속성에 대 한 조건은 **및** 에서 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-275">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="53463-276">동일한 속성의 조건은 **또는** 로 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-276">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="53463-277">논리적 연결자는 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-277">You cannot change the logical connectors.</span></span>

<span data-ttu-id="53463-278">조건은 표시에만 영향을 주고</span><span class="sxs-lookup"><span data-stu-id="53463-278">The criteria only affects the display.</span></span> <span data-ttu-id="53463-279">테이블의 항목을 실제로 삭제하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-279">It does not delete items from the table.</span></span>

<span data-ttu-id="53463-280">**조건을 추가하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-280">**How to Add Criteria**</span></span>

1. <span data-ttu-id="53463-281">**조건 추가** 메뉴 단추를 표시 하려면 창의 오른쪽 위 모서리에서 확장 화살표를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-281">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="53463-282">**조건 추가** 메뉴 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-282">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="53463-283">열(속성)을 클릭하여 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-283">Click to select columns (properties).</span></span> <span data-ttu-id="53463-284">속성은 하나 이상 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53463-284">You can select one or many properties.</span></span>
4. <span data-ttu-id="53463-285">속성 선택을 마쳤으면 **추가** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-285">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="53463-286">추가를 취소 하려면 **취소** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-286">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="53463-287">조건을 더 추가 하려면 **조건 추가** 단추를 다시 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-287">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="53463-288">**조건을 편집하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-288">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="53463-289">연산자를 변경 하려면 파란색 연산자 값을 클릭 한 다음 드롭다운 목록에서 다른 연산자를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-289">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="53463-290">값을 입력 하거나 변경 하려면 값 상자에 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-290">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="53463-291">잘못된 값을 입력하면 원형 X 아이콘이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="53463-291">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="53463-292">값을 제거하려면 변경하세요.</span><span class="sxs-lookup"><span data-stu-id="53463-292">To remove it, change the value.</span></span>
- <span data-ttu-id="53463-293">**또는** 문을 만들려면 동일한 속성을 사용 하 여 조건을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-293">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="53463-294">**조건을 삭제하는 방법**</span><span class="sxs-lookup"><span data-stu-id="53463-294">**How to Delete Criteria**</span></span>

- <span data-ttu-id="53463-295">선택한 조건을 삭제 하려면 각 조건 옆에 있는 빨간색 X를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-295">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="53463-296">모든 조건을 삭제 하려면 **모두 지우기** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="53463-296">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="53463-297">관련 링크</span><span class="sxs-lookup"><span data-stu-id="53463-297">RELATED LINKS</span></span>

[<span data-ttu-id="53463-298">Out-File</span><span class="sxs-lookup"><span data-stu-id="53463-298">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="53463-299">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="53463-299">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="53463-300">Out-String</span><span class="sxs-lookup"><span data-stu-id="53463-300">Out-String</span></span>](Out-String.md)

