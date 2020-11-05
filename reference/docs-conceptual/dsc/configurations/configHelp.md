---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 구성에 대한 도움말 작성
description: DSC 구성에 설명 기반 도움말을 사용할 수 있습니다. 사용자는 `-?` 매개 변수가 포함된 구성을 호출하거나 Get-Help cmdlet을 사용하여 도움말에 액세스할 수 있습니다.
ms.openlocfilehash: 01c4f43253f4d4d8421ea3e0dfca797776acd426
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658655"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="98826-105">DSC 구성에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="98826-105">Writing help for DSC configurations</span></span>

> <span data-ttu-id="98826-106">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="98826-106">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="98826-107">DSC 구성에 설명 기반 도움말을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98826-107">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="98826-108">사용자는 `-?`가 포함된 **구성** 을 호출하거나 [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet을 사용하여 도움말에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98826-108">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="98826-109">`Configuration` 키워드 바로 위에 주석 기반 도움말을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="98826-109">Place your Comment-based help directly above the `Configuration` keyword.</span></span> <span data-ttu-id="98826-110">매개 변수 선언 바로 위에 주석 블록과 인라인으로 매개 변수 도움말을 배치하거나 둘 다 아래 예제와 같이 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98826-110">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="98826-111">PowerShell 설명 기반 도움말에 대한 자세한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98826-111">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="98826-112">VS Code 및 ISE 같은 PowerShell 개발 환경에도 주석 블록 템플릿을 자동으로 삽입할 수 있는 코드 조각이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="98826-112">PowerShell development environments, like VS Code and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="98826-113">다음 예제에서는 구성 및 각 구성에 대한 설명 기반 도움말을 포함하는 스크립트를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="98826-113">The following example shows a script that contains a configuration and comment-based help for it.</span></span>
<span data-ttu-id="98826-114">이 예제에서는 매개 변수를 사용하는 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="98826-114">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="98826-115">구성에서 매개 변수를 사용하는 방법에 대한 자세한 내용은 [구성에 매개 변수 추가](add-parameters-to-a-configuration.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="98826-115">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each
configuration.

.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or
script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description
on the lines following the .PARAMETER keyword. Windows PowerShell interprets all text between the
.PARAMETER line and the next keyword or the end of the comment block as part of the parameter
description. The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script
syntax determines the order in which the parameters (and their descriptions) appear in help topic.
To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a
description. Repeat this keyword for each example. PowerShell automatically prefaces the first line
with a PowerShell prompt. Additional lines are treated as output and description. The example can
contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="98826-116">구성 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="98826-116">Viewing configuration help</span></span>

<span data-ttu-id="98826-117">구성에 대한 도움말을 보려면 함수의 이름과 함께 `Get-Help` cmdlet을 사용하거나 함수의 이름 뒤에 `-?`를 붙여 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="98826-117">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="98826-118">다음은 `Get-Help`로 전달된 이전 구성의 출력입니다.</span><span class="sxs-lookup"><span data-stu-id="98826-118">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```Output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>]
      [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>]
      [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function
        or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter
        description on the lines following the .PARAMETER keyword. Windows PowerShell interprets all
        text between the .PARAMETER line and the next keyword or the end of the comment block as
        part of the parameter description. The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or
        script syntax determines the order in which the parameters (and their descriptions) appear
        in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a
    description. Repeat this keyword for each example. PowerShell automatically prefaces the first
    line with a PowerShell prompt. Additional lines are treated as output and description. The
    example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the
    examples in help text.


    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.


REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="98826-119">구문 필드 및 매개 변수 특성은 PowerShell에서 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="98826-119">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="98826-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="98826-120">See Also</span></span>

- [<span data-ttu-id="98826-121">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="98826-121">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="98826-122">구성 작성, 컴파일 및 적용</span><span class="sxs-lookup"><span data-stu-id="98826-122">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="98826-123">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="98826-123">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
