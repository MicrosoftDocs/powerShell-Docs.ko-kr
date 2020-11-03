---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: ccc72ac961adbcba542a7b8be55ad49df68a5ef6
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224297"
---
# <span data-ttu-id="9da83-103">Write-Output</span><span class="sxs-lookup"><span data-stu-id="9da83-103">Write-Output</span></span>

## <span data-ttu-id="9da83-104">개요</span><span class="sxs-lookup"><span data-stu-id="9da83-104">SYNOPSIS</span></span>
<span data-ttu-id="9da83-105">지정된 개체를 파이프라인의 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-105">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="9da83-106">명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-106">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="9da83-107">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9da83-107">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="9da83-108">설명</span><span class="sxs-lookup"><span data-stu-id="9da83-108">DESCRIPTION</span></span>

<span data-ttu-id="9da83-109">`Write-Output`Cmdlet은 지정 된 개체를 파이프라인의 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-109">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="9da83-110">명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-110">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="9da83-111">`Write-Output` "출력 스트림" 또는 "성공 파이프라인"이 라고도 하는 개체를 기본 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-111">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="9da83-112">오류 개체를 오류 파이프라인으로 보내려면 Write-Error를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="9da83-112">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="9da83-113">이 cmdlet은 대개 콘솔에 문자열 및 다른 개체를 표시하기 위해 스크립트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-113">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="9da83-114">에 대 한 기본 제공 별칭 중 하나 `Write-Output` 는를 `echo` 사용 하는 다른 셸과 유사 하며 `echo` , 기본 동작은 파이프라인 끝에 출력을 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-114">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="9da83-115">PowerShell에서는 일반적으로 출력이 기본적으로 표시 되는 인스턴스에서 cmdlet을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-115">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="9da83-116">예를 들어 `Get-Process | Write-Output`는 `Get-Process`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-116">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="9da83-117">또는를 `echo "Home directory: $HOME"` 작성할 수 있습니다 `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="9da83-117">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="9da83-118">기본적으로는 `Write-Output` cmdlet에 제공 된 컬렉션을 통해 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-118">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="9da83-119">그러나 `Write-Output` 는 **noenumerate** 매개 변수를 사용 하 여 파이프라인에서 단일 개체로 컬렉션을 전달 하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-119">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="9da83-120">예제</span><span class="sxs-lookup"><span data-stu-id="9da83-120">EXAMPLES</span></span>

### <span data-ttu-id="9da83-121">예 1: 개체를 가져와 콘솔에 기록</span><span class="sxs-lookup"><span data-stu-id="9da83-121">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="9da83-122">첫 번째 명령은 컴퓨터에서 실행 중인 프로세스를 가져와서 변수에 저장 합니다 `$P` .</span><span class="sxs-lookup"><span data-stu-id="9da83-122">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="9da83-123">두 번째 및 세 번째 명령은 콘솔에의 프로세스 개체를 표시 합니다 `$P` .</span><span class="sxs-lookup"><span data-stu-id="9da83-123">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="9da83-124">예 2: 다른 cmdlet에 출력 전달</span><span class="sxs-lookup"><span data-stu-id="9da83-124">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="9da83-125">이 명령은 "테스트 출력" 문자열을 cmdlet에 파이프 합니다 .이 cmdlet은 system.string `Get-Member` 클래스의 **System.String** 멤버를 표시 하 여 해당 문자열이 파이프라인을 따라 전달 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-125">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="9da83-126">예제 3: 출력에 열거 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="9da83-126">Example 3: Suppress enumeration in output</span></span>

```powershell
Write-Output 1,2,3 | Measure-Object
```

```Output
Count    : 3
...
```

```powershell
Write-Output 1,2,3 -NoEnumerate | Measure-Object
```

```Output
Count    : 1
...
```

<span data-ttu-id="9da83-127">이 명령은 **Noenumerate** 매개 변수를 추가 하 여 파이프라인을 통해 컬렉션이 나 배열을 단일 개체로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-127">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="9da83-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9da83-128">PARAMETERS</span></span>

### <span data-ttu-id="9da83-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9da83-129">-InputObject</span></span>

<span data-ttu-id="9da83-130">파이프라인으로 보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-130">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="9da83-131">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="9da83-131">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9da83-132">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="9da83-132">-NoEnumerate</span></span>

<span data-ttu-id="9da83-133">기본적으로 cmdlet은 `Write-Output` 항상 해당 출력을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-133">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="9da83-134">**Noenumerate** 매개 변수는 기본 동작을 억제 하 고 출력을 열거 하지 못하도록 합니다 `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="9da83-134">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="9da83-135">괄호를 강제로 열거 하므로 명령이 괄호 안에 래핑된 경우 **Noenumerate** 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-135">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="9da83-136">예를 들어 `(Write-Output 1,2,3)` 는 배열을 여전히 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-136">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9da83-137">Windows PowerShell에서 PowerShell 6.2 이상에서 수정 된이 스위치에 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-137">There is an issue with this switch in Windows PowerShell that is fixed in PowerShell 6.2 and above.</span></span> <span data-ttu-id="9da83-138">**Noenumerate** 를 사용 하 고 **InputObject** 매개 변수를 명시적으로 사용 하는 경우 명령은 여전히를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-138">When using **NoEnumerate** and explicitly using the **InputObject** parameter, the command still enumerates.</span></span> <span data-ttu-id="9da83-139">이 문제를 해결 하려면 **InputObject** 인수 메서드에 액세스할를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-139">To work around this, pass the **InputObject** argument(s) positionally.</span></span>

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

### <span data-ttu-id="9da83-140">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9da83-140">CommonParameters</span></span>

<span data-ttu-id="9da83-141">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9da83-141">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9da83-142">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9da83-142">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9da83-143">입력</span><span class="sxs-lookup"><span data-stu-id="9da83-143">INPUTS</span></span>

### <span data-ttu-id="9da83-144">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="9da83-144">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9da83-145">개체를로 파이프 할 수 있습니다 `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="9da83-145">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="9da83-146">출력</span><span class="sxs-lookup"><span data-stu-id="9da83-146">OUTPUTS</span></span>

### <span data-ttu-id="9da83-147">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="9da83-147">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9da83-148">`Write-Output` 입력으로 전송 되는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9da83-148">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="9da83-149">참고</span><span class="sxs-lookup"><span data-stu-id="9da83-149">NOTES</span></span>

## <span data-ttu-id="9da83-150">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9da83-150">RELATED LINKS</span></span>

[<span data-ttu-id="9da83-151">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="9da83-151">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="9da83-152">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="9da83-152">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="9da83-153">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="9da83-153">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="9da83-154">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="9da83-154">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="9da83-155">쓰기 오류</span><span class="sxs-lookup"><span data-stu-id="9da83-155">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="9da83-156">Write-Host</span><span class="sxs-lookup"><span data-stu-id="9da83-156">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="9da83-157">Write-Information</span><span class="sxs-lookup"><span data-stu-id="9da83-157">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="9da83-158">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="9da83-158">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="9da83-159">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="9da83-159">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="9da83-160">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="9da83-160">Write-Warning</span></span>](Write-Warning.md)
