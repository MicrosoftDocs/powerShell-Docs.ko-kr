---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-modulemember?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-ModuleMember
ms.openlocfilehash: 8d99f861a9cbdc72d30975275c49c6cd5bde2bed
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211329"
---
# <span data-ttu-id="7e385-103">Export-ModuleMember</span><span class="sxs-lookup"><span data-stu-id="7e385-103">Export-ModuleMember</span></span>

## <span data-ttu-id="7e385-104">개요</span><span class="sxs-lookup"><span data-stu-id="7e385-104">SYNOPSIS</span></span>
<span data-ttu-id="7e385-105">내보내는 모듈 멤버를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-105">Specifies the module members that are exported.</span></span>

## <span data-ttu-id="7e385-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e385-106">SYNTAX</span></span>

```
Export-ModuleMember [[-Function] <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="7e385-107">설명</span><span class="sxs-lookup"><span data-stu-id="7e385-107">DESCRIPTION</span></span>

<span data-ttu-id="7e385-108">**Export-modulemember** cmdlet은 스크립트 모듈 (.psm1) 파일 또는 New-Module cmdlet을 사용 하 여 만든 동적 모듈에서 내보낸 모듈 멤버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-108">The **Export-ModuleMember** cmdlet specifies the module members that are exported from a script module (.psm1) file, or from a dynamic module created by using the New-Module cmdlet.</span></span>
<span data-ttu-id="7e385-109">모듈 멤버에는 cmdlet, 함수, 변수 및 별칭이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-109">Module members include cmdlets, functions, variables, and aliases.</span></span>
<span data-ttu-id="7e385-110">이 cmdlet은 스크립트 모듈 파일이나 동적 모듈에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-110">This cmdlet can be used only in a script module file or a dynamic module.</span></span>

<span data-ttu-id="7e385-111">스크립트 모듈에 **export-modulemember** 명령이 포함 되어 있지 않으면 스크립트 모듈의 함수 및 별칭을 내보내고 변수는 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-111">If a script module does not include an **Export-ModuleMember** command, the functions and aliases in the script module are exported, but the variables are not.</span></span>
<span data-ttu-id="7e385-112">스크립트 모듈에 **export-modulemember** 명령이 포함 된 경우 **export-modulemember** 명령에 지정 된 멤버만 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-112">When a script module includes **Export-ModuleMember** commands, only the members specified in the **Export-ModuleMember** commands are exported.</span></span>
<span data-ttu-id="7e385-113">**Export-modulemember** 를 사용 하 여 스크립트 모듈이 다른 모듈에서 가져오는 멤버를 표시 하지 않거나 내보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-113">You can also use **Export-ModuleMember** to suppress or export members that the script module imports from other modules.</span></span>

<span data-ttu-id="7e385-114">**Export-modulemember** 명령은 선택 사항 이지만 모범 사례입니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-114">An **Export-ModuleMember** command is optional, but it is a best practice.</span></span>
<span data-ttu-id="7e385-115">명령에서 기본값을 확인하는 경우에도 모듈 작성자의 의도를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-115">Even if the command confirms the default values, it demonstrates the intention of the module author.</span></span>

## <span data-ttu-id="7e385-116">예제</span><span class="sxs-lookup"><span data-stu-id="7e385-116">EXAMPLES</span></span>

### <span data-ttu-id="7e385-117">예제 1: 스크립트 모듈에서 함수 및 별칭 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-117">Example 1: Export functions and aliases in a script module</span></span>

```powershell
Export-ModuleMember -Function * -Alias *
```

<span data-ttu-id="7e385-118">이 명령은 스크립트 모듈에 정의 된 모든 함수 및 별칭을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-118">This command exports all the functions and aliases defined in the script module.</span></span>

### <span data-ttu-id="7e385-119">예제 2: 특정 별칭 및 함수 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-119">Example 2: Export specific aliases and functions</span></span>

```powershell
Export-ModuleMember -Function Get-Test, New-Test, Start-Test -Alias gtt, ntt, stt
```

<span data-ttu-id="7e385-120">이 명령은 스크립트 모듈에 정의된 별칭 3개와 함수 3개를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-120">This command exports three aliases and three functions defined in the script module.</span></span>

<span data-ttu-id="7e385-121">이 명령 형식을 사용하여 모듈 멤버의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-121">You can use this command format to specify the names of module members.</span></span>

### <span data-ttu-id="7e385-122">예제 3: 멤버 없음 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-122">Example 3: Export no members</span></span>

```powershell
Export-ModuleMember
```

<span data-ttu-id="7e385-123">이 명령은 스크립트 모듈에 정의된 멤버를 내보내지 않도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-123">This command specifies that no members defined in the script module are exported.</span></span>

<span data-ttu-id="7e385-124">모듈 멤버를 내보내지 않도록 하지만 멤버를 숨기지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-124">This command prevents the module members from being exported, but it does not hide the members.</span></span>
<span data-ttu-id="7e385-125">사용자는 모듈 멤버를 읽고 복사하거나 호출 연산자(&)를 사용하여 내보내 지지 않는 모듈 멤버를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-125">Users can read and copy module members or use the call operator (&) to invoke module members that are not exported.</span></span>

### <span data-ttu-id="7e385-126">예제 4: 특정 변수 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-126">Example 4: Export a specific variable</span></span>

```powershell
Export-ModuleMember -Variable increment
```

<span data-ttu-id="7e385-127">이 명령은 스크립트 모듈에서 $increment 변수만 내보내고</span><span class="sxs-lookup"><span data-stu-id="7e385-127">This command exports only the $increment variable from the script module.</span></span>
<span data-ttu-id="7e385-128">다른 멤버는 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-128">No other members are exported.</span></span>

<span data-ttu-id="7e385-129">모듈의 함수를 내보내는 것 외에도 변수를 내보내려는 경우 **export-modulemember** 명령에는 모든 함수의 이름과 변수의 이름이 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-129">If you want to export a variable, in addition to exporting the functions in a module, the **Export-ModuleMember** command must include the names of all of the functions and the name of the variable.</span></span>

### <span data-ttu-id="7e385-130">예 5: 여러 내보내기 명령</span><span class="sxs-lookup"><span data-stu-id="7e385-130">Example 5: Multiple export commands</span></span>

```powershell
# From TestModule.psm1
Function New-Test
{
    Write-Output 'I am New-Test function'
}
Export-ModuleMember -Function New-Test

function Validate-Test
{
    Write-Output 'I am Validate-Test function'
}
function Start-Test
{
    Write-Output 'I am Start-Test function'
}
Set-Alias stt Start-Test
Export-ModuleMember -Function Start-Test -Alias stt
```

<span data-ttu-id="7e385-131">이 명령은 스크립트 모듈 (.psm1) 파일에서 여러 **export-modulemember** 명령이 해석 되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-131">These commands show how multiple **Export-ModuleMember** commands are interpreted in a script module (.psm1) file.</span></span>

<span data-ttu-id="7e385-132">함수 3개와 별칭 1개를 만든 다음 함수 2개와 별칭을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-132">These commands create three functions and one alias, and then they export two of the functions and the alias.</span></span>

<span data-ttu-id="7e385-133">**Export-modulemember** 명령이 없으면 세 가지 함수와 별칭을 모두 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-133">Without the **Export-ModuleMember** commands, all three of the functions and the alias would be exported.</span></span>
<span data-ttu-id="7e385-134">**Export-modulemember** 명령을 사용 하면 **새 테스트** 및 **시작-테스트** 함수 및 STT 별칭을 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-134">With the **Export-ModuleMember** commands, only the **New-Test** and **Start-Test** functions and the STT alias are exported.</span></span>

### <span data-ttu-id="7e385-135">예제 6: 동적 모듈에서 멤버 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-135">Example 6: Export members in a dynamic module</span></span>

```powershell
New-Module -Script {function SayHello {"Hello!"}; Set-Alias Hi SayHello; Export-ModuleMember -Alias Hi -Function SayHello}
```

<span data-ttu-id="7e385-136">이 명령은 **새 모듈** cmdlet을 사용 하 여 만든 동적 모듈에서 Export-ModuleMember를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-136">This command shows how to use Export-ModuleMember in a dynamic module that is created by using the **New-Module** cmdlet.</span></span>

<span data-ttu-id="7e385-137">이 예에서는 **export-modulemember** 를 사용 하 여 동적 모듈에서 Hi와 **SayHello** 함수를 모두 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-137">In this example, **Export-ModuleMember** is used to export both the Hi alias and the **SayHello** function in the dynamic module.</span></span>

### <span data-ttu-id="7e385-138">예제 7: 단일 명령에서 함수 선언 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="7e385-138">Example 7: Declare and export a function in a single command</span></span>

```powershell
# From TestModule.psm1
function Export
{
  param (
    [Parameter(Mandatory=$true)]
    [ValidateSet("function","variable")]
    $Type,
    [Parameter(Mandatory=$true)]
    $Name,
    [Parameter(Mandatory=$true)]
    $Value
    )

    if ($Type -eq "function")
    {
        Set-item "function:script:$Name" $Value
        Export-ModuleMember $Name
    }
    else
    {
    Set-Variable -scope Script $Name $Value
    Export-ModuleMember -variable $Name
    }
}

Export function New-Test {Write-Output 'I am New-Test function'}
function helper {Write-Output 'I am helper function'}

Export variable Interval 0
$Interval = 2
```

<span data-ttu-id="7e385-139">이 예에는 함수를 **Export** 선언 하거나 변수를 만든 다음 `Export-ModuleMember` 함수 또는 변수에 대 한 명령을 작성 하는 Export 라는 함수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-139">This example includes a function named **Export** that declares a function or creates a variable, and then writes an `Export-ModuleMember` command for the function or variable.</span></span>
<span data-ttu-id="7e385-140">이 함수를 사용하면 하나의 명령으로 함수 또는 변수를 선언하고 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-140">This lets you declare and export a function or variable in a single command.</span></span>

<span data-ttu-id="7e385-141">**Export** 함수를 사용 하려면 스크립트 모듈에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-141">To use the **Export** function, include it in your script module.</span></span>
<span data-ttu-id="7e385-142">함수를 내보내려면 `Export` **function** 키워드 앞에를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-142">To export a function, type `Export` before the **Function** keyword.</span></span>

<span data-ttu-id="7e385-143">변수를 내보내려면 다음 형식을 사용하여 변수를 선언하고 변수 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-143">To export a variable, use the following format to declare the variable and set its value:</span></span>

`Export variable <variable-name> <value>`

<span data-ttu-id="7e385-144">예제의 명령은 올바른 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-144">The commands in the example show the correct format.</span></span>
<span data-ttu-id="7e385-145">이 예제에서는 **새-테스트** 함수 및 $Interval 변수만 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-145">In this example, only the **New-Test** function and the $Interval variable are exported.</span></span>

## <span data-ttu-id="7e385-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7e385-146">PARAMETERS</span></span>

### <span data-ttu-id="7e385-147">-별칭</span><span class="sxs-lookup"><span data-stu-id="7e385-147">-Alias</span></span>

<span data-ttu-id="7e385-148">스크립트 모듈 파일에서 내보내는 별칭을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-148">Specifies the aliases that are exported from the script module file.</span></span>
<span data-ttu-id="7e385-149">별칭 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-149">Enter the alias names.</span></span>
<span data-ttu-id="7e385-150">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-150">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7e385-151">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7e385-151">-Cmdlet</span></span>

<span data-ttu-id="7e385-152">스크립트 모듈 파일에서 내보내는 cmdlet을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-152">Specifies the cmdlets that are exported from the script module file.</span></span>
<span data-ttu-id="7e385-153">cmdlet 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-153">Enter the cmdlet names.</span></span>
<span data-ttu-id="7e385-154">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-154">Wildcard characters are permitted.</span></span>

<span data-ttu-id="7e385-155">스크립트 모듈 파일에서 cmdlet을 만들 수는 없지만 이진 모듈의 cmdlet을 스크립트 모듈로 가져온 다음 스크립트 모듈에서 다시 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-155">You cannot create cmdlets in a script module file, but you can import cmdlets from a binary module into a script module and re-export them from the script module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7e385-156">-함수</span><span class="sxs-lookup"><span data-stu-id="7e385-156">-Function</span></span>

<span data-ttu-id="7e385-157">스크립트 모듈 파일에서 내보내는 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-157">Specifies the functions that are exported from the script module file.</span></span>
<span data-ttu-id="7e385-158">함수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-158">Enter the function names.</span></span>
<span data-ttu-id="7e385-159">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-159">Wildcard characters are permitted.</span></span>
<span data-ttu-id="7e385-160">함수 이름 문자열을 **export-modulemember** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-160">You can also pipe function name strings to **Export-ModuleMember** .</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="7e385-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="7e385-161">-Variable</span></span>

<span data-ttu-id="7e385-162">스크립트 모듈 파일에서 내보내는 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-162">Specifies the variables that are exported from the script module file.</span></span>
<span data-ttu-id="7e385-163">달러 기호 없이 변수 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-163">Enter the variable names, without a dollar sign.</span></span>
<span data-ttu-id="7e385-164">와일드카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-164">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7e385-165">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e385-165">CommonParameters</span></span>

<span data-ttu-id="7e385-166">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e385-166">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e385-167">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7e385-167">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e385-168">입력</span><span class="sxs-lookup"><span data-stu-id="7e385-168">INPUTS</span></span>

### <span data-ttu-id="7e385-169">System.String</span><span class="sxs-lookup"><span data-stu-id="7e385-169">System.String</span></span>

<span data-ttu-id="7e385-170">이 cmdlet에 함수 이름 문자열을 파이프 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-170">You can pipe function name strings to this cmdlet.</span></span>

## <span data-ttu-id="7e385-171">출력</span><span class="sxs-lookup"><span data-stu-id="7e385-171">OUTPUTS</span></span>

### <span data-ttu-id="7e385-172">없음</span><span class="sxs-lookup"><span data-stu-id="7e385-172">None</span></span>

<span data-ttu-id="7e385-173">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-173">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7e385-174">참고</span><span class="sxs-lookup"><span data-stu-id="7e385-174">NOTES</span></span>

* <span data-ttu-id="7e385-175">내보낸 멤버 목록에서 멤버를 제외 하려면 다른 모든 멤버를 나열 하지만 제외 하려는 멤버를 생략 하는 **export-modulemember** 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="7e385-175">To exclude a member from the list of exported members, add an **Export-ModuleMember** command that lists all other members but omits the member that you want to exclude.</span></span>

## <span data-ttu-id="7e385-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7e385-176">RELATED LINKS</span></span>

[<span data-ttu-id="7e385-177">Get-Module</span><span class="sxs-lookup"><span data-stu-id="7e385-177">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="7e385-178">모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="7e385-178">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="7e385-179">Remove-Module</span><span class="sxs-lookup"><span data-stu-id="7e385-179">Remove-Module</span></span>](Remove-Module.md)
