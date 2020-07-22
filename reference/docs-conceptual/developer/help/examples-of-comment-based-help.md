---
title: 설명 기반 도움말 예제
ms.date: 09/12/2016
ms.openlocfilehash: 3858fa7f15d71c505dacaf9679910d45ef4640e5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893495"
---
# <a name="examples-of-comment-based-help"></a>설명 기반 도움말 예제

이 항목에는 스크립트 및 함수에 대 한 주석 기반 도움말을 사용 하는 방법을 보여 주는 예제가 포함 되어 있습니다.

## <a name="example-1-comment-based-help-for-a-function"></a>예제 1: 함수에 대 한 주석 기반 도움말

 다음 샘플 함수는 주석 기반 도움말을 포함 합니다.

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

다음 출력은 `Get-Help` 함수에 대 한 도움말을 표시 하는 명령의 결과를 보여 줍니다 `Add-Extension` .

```powershell
C:\PS> get-help add-extension -full
```

```Output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a>예제 2: 스크립트에 대 한 주석 기반 도움말

다음 샘플 함수는 주석 기반 도움말을 포함 합니다.

Closing 문과 문 사이에 빈 줄을 확인 **#>** `Param` 합니다. 문이 없는 스크립트에서 `Param` 도움말 항목의 마지막 주석과 첫 번째 함수 선언 사이에는 두 개 이상의 빈 줄이 있어야 합니다. 이러한 빈 줄이 없으면는 `Get-Help` 스크립트 대신 도움말 항목을 함수와 연결 합니다.

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

다음 명령은 스크립트 도움말을 가져옵니다. 스크립트가 Path 환경 변수에 나열 된 디렉터리에 있지 않기 때문에 스크립트 `Get-Help` 도움말을 가져오는 명령은 스크립트 경로를 지정 해야 합니다.

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```Output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a>예 3: Param 문의 매개 변수 설명

이 예에서는 `Param` 함수 또는 스크립트의 문에 매개 변수 설명을 삽입 하는 방법을 보여 줍니다. 이 형식은 매개 변수 설명이 간단한 경우에 가장 유용 합니다.

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

결과는 예 1의 결과와 같습니다. `Get-Help`키워드와 함께 제공 된 것 처럼 매개 변수 설명을 해석 합니다 `.Parameter` .

## <a name="example-4--redirecting-to-an-xml-file"></a>예 4: XML 파일로 리디렉션

함수 및 스크립트에 대 한 XML 기반 도움말 항목을 작성할 수 있습니다. 주석 기반 도움말을 구현 하는 것이 좋지만 도움말 콘텐츠를 보다 정확 하 게 제어 하거나 도움말 항목을 여러 언어로 번역 하려는 경우에는 XML 기반 도움말이 필요 합니다. 다음 예에서는 스크립트의 처음 몇 줄을 보여 줍니다 `Update-Month.ps1` . 스크립트는 키워드를 사용 하 여 `.ExternalHelp` 스크립트에 대 한 XML 기반 도움말 항목의 경로를 지정 합니다.

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

다음 예에서는 함수에서 키워드를 사용 하는 방법을 보여 줍니다 `.ExternalHelp` .

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a>예 5: 다른 도움말 항목으로 리디렉션

다음 코드는 한 `Help` 번에 하나의 도움말 텍스트 화면을 표시 하는 PowerShell의 기본 제공 함수 시작 부분에서 발췌 한 것입니다. Get-help cmdlet에 대 한 도움말 항목에서 도움말 함수를 설명 하므로 Help 함수는 및 키워드를 사용 하 여 `.ForwardHelpTargetName` `.ForwardHelpCategory` 사용자를 Get-help cmdlet 도움말 항목으로 리디렉션합니다.

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

다음 명령은이 기능을 사용 합니다. 사용자가 `Get-Help` 함수에 대 한 명령을 입력 하면 `Help` 에서 `Get-Help` cmdlet에 대 한 도움말 항목을 표시 합니다 `Get-Help` .

```powershell
C:\PS> get-help help
```

```Output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```
