---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Out Cmdlet을 사용하여 데이터 리디렉션
ms.assetid: 2a4acd33-041d-43a5-a3e9-9608a4c52b0c
ms.openlocfilehash: 7c601b09cc53524eb55014b8ea19a5d79cb98b0e
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293302"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="8edda-103">Out-\* Cmdlet을 사용하여 데이터 리디렉션</span><span class="sxs-lookup"><span data-stu-id="8edda-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="8edda-104">Windows PowerShell에는 데이터 출력을 직접 제어할 수 있는 여러 가지 cmdlet이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="8edda-105">이러한 cmdlet은 두 가지 중요한 특성을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="8edda-106">첫째, 일반적으로 이러한 cmdlet은 데이터를 특정 텍스트 형식으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="8edda-107">이는 텍스트 입력을 필요로 하는 시스템 구성 요소에 데이터를 출력하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="8edda-108">즉, 개체를 텍스트로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="8edda-109">따라서 Windows PowerShell 콘솔 창에 표시되는 대로 텍스트의 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="8edda-110">둘째, 이러한 cmdlet은 Windows PowerShell에서 다른 위치로 정보를 내보내기 때문에 Windows PowerShell의 동사 **Out**을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="8edda-111">**Out-Host** cmdlet은 항상 호스트 창을 Windows PowerShell의 외부에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="8edda-112">이는 Windows PowerShell에서 데이터를 내보내면 실제로 데이터가 제거되기 때문에 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="8edda-113">다음과 같이 데이터를 호스트 창으로 페이징하는 파이프라인을 만든 다음 목록 형식으로 지정해 보면 이 동작을 재현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="8edda-114">이 명령을 실행하면 프로세스 정보 페이지가 목록 형식으로 표시되어야 하지만</span><span class="sxs-lookup"><span data-stu-id="8edda-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="8edda-115">다음과 같이 기본 표 형식 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="8edda-116">**Out-Host** cmdlet은 데이터를 콘솔에 직접 보내기 때문에 **Format-List** 명령에는 서식을 지정할 데이터가 전달되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="8edda-117">이 명령을 구성하는 올바른 방법은 다음과 같이 **Out-Host** cmdlet을 파이프라인 끝에 배치하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="8edda-118">이렇게 하면 프로세스 데이터가 페이징되어 표시되기 전에 목록으로 형식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="8edda-119">이러한 내용은 모든 **Out** cmdlet에 적용되므로</span><span class="sxs-lookup"><span data-stu-id="8edda-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="8edda-120">**Out** cmdlet을 항상 파이프라인 끝에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="8edda-121">모든 **Out** cmdlet은 줄 길이 제한과 같은 콘솔 창에 적용되는 형식을 사용하여 출력을 텍스트로 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="8edda-122">콘솔 출력 페이징(Out-Host)</span><span class="sxs-lookup"><span data-stu-id="8edda-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="8edda-123">기본적으로 Windows PowerShell은 데이터를 호스트 창으로 보내는데, 이는 Out-Host cmdlet이 수행하는 작업과 똑같습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="8edda-124">Out-Host cmdlet의 주된 용도는 앞에서 설명한 대로 데이터를 페이징하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="8edda-125">예를 들어 다음 명령은 Out-Host를 사용하여 Get-Command cmdlet의 출력을 페이징합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="8edda-126">**more** 함수를 사용하여 데이터를 페이징할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="8edda-127">Windows PowerShell에서 **more**는 **Out-Host -Paging**을 호출하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="8edda-128">다음 명령은 **more** 함수를 사용하여 Get-Command의 출력을 페이징하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="8edda-129">하나 이상의 파일 이름을 more 함수에 대한 인수로 포함하면 more 함수는 이러한 파일을 읽고 해당 내용을 호스트로 페이징합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="8edda-130">출력 삭제(Out-Null)</span><span class="sxs-lookup"><span data-stu-id="8edda-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="8edda-131">**Out-Null** cmdlet은 수신한 입력을 즉시 삭제하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="8edda-132">이 cmdlet은 명령 실행의 부작용으로 수신되는 불필요한 데이터를 삭제하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="8edda-133">다음 명령을 입력하면 명령에서 아무 것도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="8edda-134">**Out-Null** cmdlet은 오류 출력을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="8edda-135">예를 들어 다음 명령을 입력하면 Windows PowerShell이 'Is-NotACommand'를 인식할 수 없다는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="8edda-136">데이터 인쇄(Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="8edda-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="8edda-137">**Out-Printer** cmdlet을 사용하여 데이터를 인쇄할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="8edda-138">프린터 이름을 제공하지 않으면 **Out-Printer** cmdlet은 기본 프린터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="8edda-139">표시 이름만 지정하면 아무 Windows 기반 컴퓨터나 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="8edda-140">프린터 포트 매핑이나 심지어 실제 프린터도 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="8edda-141">예를 들어 Microsoft Office Document Imaging 도구가 설치되어 있으면 다음과 같이 입력하여 데이터를 이미지 파일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="8edda-142">데이터 저장(Out-File)</span><span class="sxs-lookup"><span data-stu-id="8edda-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="8edda-143">**Out-File** cmdlet을 사용하여 출력을 콘솔 창이 아니라 파일로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="8edda-144">다음 명령줄은 프로세스 목록을 **C:\\temp\\processlist.txt** 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="8edda-145">이전의 출력 리디렉션에 익숙한 경우 **Out-File** cmdlet을 사용하면 알고 있는 것과 다른 결과가 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="8edda-146">이 동작을 이해하려면 **Out-File** cmdlet이 작동하는 컨텍스트를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="8edda-147">기본적으로 **Out-File** cmdlet은 유니코드 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="8edda-148">이 형식은 최선의 기본 출력 형식이지만 이 기본 출력 형식을 사용할 경우 ASCII 파일을 출력하는 도구가 올바로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="8edda-149">다음과 같이 **Encoding** 매개 변수를 사용하면 기본 출력 형식을 ASCII로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="8edda-150">**Out-file**은 콘솔에 표시되는 것처럼 파일 내용의 형식을 지정하기 때문에</span><span class="sxs-lookup"><span data-stu-id="8edda-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="8edda-151">대부분의 경우 콘솔 창에서처럼 출력이 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="8edda-152">예를 들어 다음 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="8edda-153">출력은 다음과 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="8edda-154">출력할 때 화면 너비에 맞추기 위해 강제로 줄을 바꾸지 않으려면 **Width** 매개 변수를 사용하여 줄 너비를 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="8edda-155">**Width**는 32비트 정수 매개 변수이기 때문에 에 지정할 수 있는 최대값은 2147483647입니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="8edda-156">줄 길이를 최대값으로 설정하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="8edda-157">**Out-File** cmdlet은 콘솔에 표시된 상태로 출력을 저장하려는 경우에 가장 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="8edda-158">출력 형식을 보다 자세히 제어하려면 고급 도구가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="8edda-159">이러한 도구에 대해서는 다음 장에서 개체 조작에 대해 설명할 때 함께 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="8edda-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>