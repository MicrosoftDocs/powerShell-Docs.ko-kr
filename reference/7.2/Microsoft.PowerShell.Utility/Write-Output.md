---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-output?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Output
ms.openlocfilehash: 7e0c958201dbd1b42d1f4c4ee286b8aca1f8595a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601842"
---
# <span data-ttu-id="c327e-102">Write-Output</span><span class="sxs-lookup"><span data-stu-id="c327e-102">Write-Output</span></span>

## <span data-ttu-id="c327e-103">개요</span><span class="sxs-lookup"><span data-stu-id="c327e-103">SYNOPSIS</span></span>
<span data-ttu-id="c327e-104">지정된 개체를 파이프라인의 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-104">Sends the specified objects to the next command in the pipeline.</span></span> <span data-ttu-id="c327e-105">명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-105">If the command is the last command in the pipeline, the objects are displayed in the console.</span></span>

## <span data-ttu-id="c327e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c327e-106">SYNTAX</span></span>

```
Write-Output [-InputObject] <PSObject[]> [-NoEnumerate] [<CommonParameters>]
```

## <span data-ttu-id="c327e-107">설명</span><span class="sxs-lookup"><span data-stu-id="c327e-107">DESCRIPTION</span></span>

<span data-ttu-id="c327e-108">`Write-Output`Cmdlet은 지정 된 개체를 파이프라인의 다음 명령으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-108">The `Write-Output` cmdlet sends the specified object down the pipeline to the next command.</span></span>
<span data-ttu-id="c327e-109">명령이 파이프라인에서 마지막 명령인 경우 개체가 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-109">If the command is the last command in the pipeline, the object is displayed in the console.</span></span>

<span data-ttu-id="c327e-110">`Write-Output` "출력 스트림" 또는 "성공 파이프라인"이 라고도 하는 개체를 기본 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-110">`Write-Output` sends objects down the primary pipeline, also known as the "output stream" or the "success pipeline."</span></span> <span data-ttu-id="c327e-111">오류 개체를 오류 파이프라인으로 보내려면 Write-Error를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="c327e-111">To send error objects down the error pipeline, use Write-Error.</span></span>

<span data-ttu-id="c327e-112">이 cmdlet은 대개 콘솔에 문자열 및 다른 개체를 표시하기 위해 스크립트에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-112">This cmdlet is typically used in scripts to display strings and other objects on the console.</span></span> <span data-ttu-id="c327e-113">에 대 한 기본 제공 별칭 중 하나 `Write-Output` 는를 `echo` 사용 하는 다른 셸과 유사 하며 `echo` , 기본 동작은 파이프라인 끝에 출력을 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-113">One of the built-in aliases for `Write-Output` is `echo` and similar to other shells that use `echo`, the default behavior is to display the output at the end of a pipeline.</span></span> <span data-ttu-id="c327e-114">PowerShell에서는 일반적으로 출력이 기본적으로 표시 되는 인스턴스에서 cmdlet을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-114">In PowerShell, it is generally not necessary to use the cmdlet in instances where the output is displayed by default.</span></span> <span data-ttu-id="c327e-115">예를 들어 `Get-Process | Write-Output`는 `Get-Process`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-115">For example, `Get-Process | Write-Output` is equivalent to `Get-Process`.</span></span> <span data-ttu-id="c327e-116">또는를 `echo "Home directory: $HOME"` 작성할 수 있습니다 `"Home directory: $HOME"` .</span><span class="sxs-lookup"><span data-stu-id="c327e-116">Or, `echo "Home directory: $HOME"` can be written, `"Home directory: $HOME"`.</span></span>

<span data-ttu-id="c327e-117">기본적으로는 `Write-Output` cmdlet에 제공 된 컬렉션을 통해 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-117">By default, `Write-Output` enumerates through collections provided to the cmdlet.</span></span> <span data-ttu-id="c327e-118">그러나 `Write-Output` 는 **noenumerate** 매개 변수를 사용 하 여 파이프라인에서 단일 개체로 컬렉션을 전달 하는 데 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-118">However, `Write-Output` can also be used to pass collections down the pipeline as a single object with the **NoEnumerate** parameter.</span></span>

## <span data-ttu-id="c327e-119">예제</span><span class="sxs-lookup"><span data-stu-id="c327e-119">EXAMPLES</span></span>

### <span data-ttu-id="c327e-120">예 1: 개체를 가져와 콘솔에 기록</span><span class="sxs-lookup"><span data-stu-id="c327e-120">Example 1: Get objects and write them to the console</span></span>

```powershell
$P = Get-Process
Write-Output $P
```

<span data-ttu-id="c327e-121">첫 번째 명령은 컴퓨터에서 실행 중인 프로세스를 가져와서 변수에 저장 합니다 `$P` .</span><span class="sxs-lookup"><span data-stu-id="c327e-121">The first command gets processes running on the computer and stores them in the `$P` variable.</span></span>

<span data-ttu-id="c327e-122">두 번째 및 세 번째 명령은 콘솔에의 프로세스 개체를 표시 합니다 `$P` .</span><span class="sxs-lookup"><span data-stu-id="c327e-122">The second and third commands display the process objects in `$P` on the console.</span></span>

### <span data-ttu-id="c327e-123">예 2: 다른 cmdlet에 출력 전달</span><span class="sxs-lookup"><span data-stu-id="c327e-123">Example 2: Pass output to another cmdlet</span></span>

```powershell
Write-Output "test output" | Get-Member
```

<span data-ttu-id="c327e-124">이 명령은 "테스트 출력" 문자열을 cmdlet에 파이프 합니다 .이 cmdlet은 system.string `Get-Member` 클래스의  멤버를 표시 하 여 해당 문자열이 파이프라인을 따라 전달 되었음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-124">This command pipes the "test output" string to the `Get-Member` cmdlet, which displays the members of the **System.String** class, demonstrating that the string was passed along the pipeline.</span></span>

### <span data-ttu-id="c327e-125">예제 3: 출력에 열거 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="c327e-125">Example 3: Suppress enumeration in output</span></span>

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

<span data-ttu-id="c327e-126">이 명령은 **Noenumerate** 매개 변수를 추가 하 여 파이프라인을 통해 컬렉션이 나 배열을 단일 개체로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-126">This command adds the **NoEnumerate** parameter to treat a collection or array as a single object through the pipeline.</span></span>

## <span data-ttu-id="c327e-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="c327e-127">PARAMETERS</span></span>

### <span data-ttu-id="c327e-128">-InputObject</span><span class="sxs-lookup"><span data-stu-id="c327e-128">-InputObject</span></span>

<span data-ttu-id="c327e-129">파이프라인으로 보낼 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-129">Specifies the objects to send down the pipeline.</span></span> <span data-ttu-id="c327e-130">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="c327e-130">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="c327e-131">-NoEnumerate</span><span class="sxs-lookup"><span data-stu-id="c327e-131">-NoEnumerate</span></span>

<span data-ttu-id="c327e-132">기본적으로 cmdlet은 `Write-Output` 항상 해당 출력을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-132">By default, the `Write-Output` cmdlet always enumerates its output.</span></span> <span data-ttu-id="c327e-133">**Noenumerate** 매개 변수는 기본 동작을 억제 하 고 출력을 열거 하지 못하도록 합니다 `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="c327e-133">The **NoEnumerate** parameter suppresses the default behavior, and prevents `Write-Output` from enumerating output.</span></span> <span data-ttu-id="c327e-134">괄호를 강제로 열거 하므로 명령이 괄호 안에 래핑된 경우 **Noenumerate** 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-134">The **NoEnumerate** parameter has no effect if the command is wrapped in parentheses, because the parentheses force enumeration.</span></span> <span data-ttu-id="c327e-135">예를 들어 `(Write-Output 1,2,3)` 는 배열을 여전히 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-135">For example, `(Write-Output 1,2,3)` still enumerates the array.</span></span>

> [!NOTE]
> <span data-ttu-id="c327e-136">이 스위치는 PowerShell Core 6.2 이상 에서만 제대로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-136">This switch only works correctly with PowerShell Core 6.2 and newer.</span></span> <span data-ttu-id="c327e-137">이전 버전의 PowerShell Core에서 컬렉션은이 스위치를 사용 하는 경우에도 여전히 열거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-137">On older versions of PowerShell Core, the collection is still enumerated even with use of this switch.</span></span>

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

### <span data-ttu-id="c327e-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c327e-138">CommonParameters</span></span>

<span data-ttu-id="c327e-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c327e-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c327e-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c327e-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c327e-141">입력</span><span class="sxs-lookup"><span data-stu-id="c327e-141">INPUTS</span></span>

### <span data-ttu-id="c327e-142">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c327e-142">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c327e-143">개체를로 파이프 할 수 있습니다 `Write-Output` .</span><span class="sxs-lookup"><span data-stu-id="c327e-143">You can pipe objects to `Write-Output`.</span></span>

## <span data-ttu-id="c327e-144">출력</span><span class="sxs-lookup"><span data-stu-id="c327e-144">OUTPUTS</span></span>

### <span data-ttu-id="c327e-145">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="c327e-145">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="c327e-146">`Write-Output` 입력으로 전송 되는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c327e-146">`Write-Output` returns the objects that are submitted as input.</span></span>

## <span data-ttu-id="c327e-147">참고</span><span class="sxs-lookup"><span data-stu-id="c327e-147">NOTES</span></span>

## <span data-ttu-id="c327e-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="c327e-148">RELATED LINKS</span></span>

[<span data-ttu-id="c327e-149">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="c327e-149">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="c327e-150">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="c327e-150">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="c327e-151">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="c327e-151">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="c327e-152">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="c327e-152">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="c327e-153">Write-Error</span><span class="sxs-lookup"><span data-stu-id="c327e-153">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="c327e-154">Write-Host</span><span class="sxs-lookup"><span data-stu-id="c327e-154">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="c327e-155">Write-Information</span><span class="sxs-lookup"><span data-stu-id="c327e-155">Write-Information</span></span>](Write-Information.md)

[<span data-ttu-id="c327e-156">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="c327e-156">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="c327e-157">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="c327e-157">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="c327e-158">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="c327e-158">Write-Warning</span></span>](Write-Warning.md)
