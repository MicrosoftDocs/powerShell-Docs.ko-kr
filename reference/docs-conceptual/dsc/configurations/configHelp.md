---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 구성에 대한 도움말 작성
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954140"
---
# <a name="writing-help-for-dsc-configurations"></a>DSC 구성에 대한 도움말 작성

>적용 대상: Windows PowerShell 5.0

DSC 구성에 설명 기반 도움말을 사용할 수 있습니다. 사용자는 `-?`가 포함된 **구성**을 호출하거나 [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet을 사용하여 도움말에 액세스할 수 있습니다. `Configuration` 키워드 바로 위에 주석 기반 도움말을 배치합니다.
매개 변수 선언 바로 위에 주석 블록과 인라인으로 매개 변수 도움말을 배치하거나 둘 다 아래 예제와 같이 배치할 수 있습니다.

PowerShell 설명 기반 도움말에 대한 자세한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.

> [!NOTE]
> VSCode 및 ISE 같은 PowerShell 개발 환경에도 주석 블록 템플릿을 자동으로 삽입할 수 있는 코드 조각이 있습니다.

다음 예제에서는 구성 및 각 구성에 대한 설명 기반 도움말을 포함하는 스크립트를 보여줍니다. 이 예제에서는 매개 변수를 사용하는 구성을 보여 줍니다. 구성에서 매개 변수를 사용하는 방법에 대한 자세한 내용은 [구성에 매개 변수 추가](add-parameters-to-a-configuration.md)를 참조하세요.

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

## <a name="viewing-configuration-help"></a>구성 도움말 보기

구성에 대한 도움말을 보려면 함수의 이름과 함께 `Get-Help` cmdlet을 사용하거나 함수의 이름 뒤에 `-?`를 붙여 입력하세요. 다음은 `Get-Help`로 전달된 이전 구성의 출력입니다.

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
> 구문 필드 및 매개 변수 특성은 PowerShell에서 자동으로 생성됩니다.

## <a name="see-also"></a>참고 항목

- [DSC 구성](configurations.md)
- [구성 작성, 컴파일 및 적용](write-compile-apply-configuration.md)
- [구성에 매개 변수 추가](add-parameters-to-a-configuration.md)
