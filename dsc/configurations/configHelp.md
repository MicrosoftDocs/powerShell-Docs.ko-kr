---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 구성에 대한 도움말 작성
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683003"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="63077-103">DSC 구성에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="63077-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="63077-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="63077-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="63077-105">DSC 구성에 설명 기반 도움말을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63077-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="63077-106">사용자가 호출 하 여 도움말에 액세스할 수는 **구성** 사용 하 여 `-?`, 또는 사용 하 여 합니다 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="63077-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="63077-107">에 설명 기반 도움말 바로 위에 배치 합니다 `Configuration` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="63077-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="63077-108">매개 변수 선언, 또는 둘 다가 아래 예제와 같이 바로 위에 주석 블록을 사용 하 여 인라인에서 매개 변수 도움말을 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63077-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="63077-109">PowerShell 설명 기반 도움말에 대한 자세한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63077-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="63077-110">VSCode 및 ISE가 같은 PowerShell 개발 환경, 주석 요소 템플릿을 자동으로 삽입할 수 있도록 코드 조각 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63077-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="63077-111">다음 예제에서는 구성 및 각 구성에 대한 설명 기반 도움말을 포함하는 스크립트를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="63077-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="63077-112">이 예제에서는 매개 변수를 사용 하 여 구성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="63077-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="63077-113">구성에 매개 변수를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요 [구성 매개 변수 추가](add-parameters-to-a-configuration.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="63077-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
(and their descriptions) appear in help topic. To change the order, change the syntax.

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

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

## <a name="viewing-configuration-help"></a><span data-ttu-id="63077-114">구성 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="63077-114">Viewing configuration help</span></span>

<span data-ttu-id="63077-115">구성에 대 한 도움말을 보려면 다음을 사용 합니다 `Get-Help` 함수 또는 형식 이름 사용 하 여 cmdlet 함수 이름 뒤에 `-?`합니다.</span><span class="sxs-lookup"><span data-stu-id="63077-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="63077-116">다음은 출력에 전달 된 이전 구성의 `Get-Help`합니다.</span><span class="sxs-lookup"><span data-stu-id="63077-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="63077-117">구문 필드 및 매개 변수 특성은 자동으로 PowerShell에서를 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63077-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="63077-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="63077-118">See Also</span></span>

- [<span data-ttu-id="63077-119">DSC 구성</span><span class="sxs-lookup"><span data-stu-id="63077-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="63077-120">구성 작성, 컴파일 및 적용</span><span class="sxs-lookup"><span data-stu-id="63077-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="63077-121">구성에 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="63077-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
