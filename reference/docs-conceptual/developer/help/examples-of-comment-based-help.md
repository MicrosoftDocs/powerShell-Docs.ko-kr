---
title: 주석 기반 도움말의 예 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367822"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="7fa3c-102">설명 기반 도움말 예제</span><span class="sxs-lookup"><span data-stu-id="7fa3c-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="7fa3c-103">이 항목에는 스크립트 및 함수에 대 한 주석 기반 도움말을 사용 하는 방법을 보여 주는 예제가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="7fa3c-104">예제 1: 함수에 대 한 주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="7fa3c-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="7fa3c-105">다음 샘플 함수는 주석 기반 도움말을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="7fa3c-106">다음 출력은 추가 확장 기능에 대 한 도움말을 표시 하는 Get-help 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="7fa3c-107">예제 2: 스크립트에 대 한 주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="7fa3c-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="7fa3c-108">다음 샘플 함수는 주석 기반 도움말을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="7fa3c-109">Closing **#>** 와 `Param` 문 사이에 빈 줄을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="7fa3c-110">`Param` 문이 없는 스크립트에서 도움말 항목의 마지막 주석과 첫 번째 함수 선언 사이에는 두 개 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="7fa3c-111">이러한 빈 줄이 없으면 Get-help는 스크립트 대신 도움말 항목을 함수와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="7fa3c-112">다음 명령은 스크립트 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-112">The following command gets the script Help.</span></span> <span data-ttu-id="7fa3c-113">스크립트가 Path 환경 변수에 나열 된 디렉터리를 n이 아니기 때문에 스크립트 도움말을 가져오는 Get-help 명령은 스크립트 경로를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="7fa3c-114">예 3: Param 문의 매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="7fa3c-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="7fa3c-115">이 예에서는 함수나 스크립트의 `Param` 문에 parameterdescriptions을 삽입 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="7fa3c-116">이 형식은 매개 변수 설명이 간단한 경우에 가장 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="7fa3c-117">결과는 예 1의 결과와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="7fa3c-118">Get-help는 `.Parameter` 키워드가 함께 제공 된 것 처럼 매개 변수 설명을 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="7fa3c-119">예 4: XML 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="7fa3c-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="7fa3c-120">함수 및 스크립트에 대 한 XML 기반 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="7fa3c-121">주석 기반 도움말을 구현 하는 것이 좋지만 도움말 콘텐츠를 보다 정확 하 게 제어 하거나 도움말 항목을 여러 언어로 번역 하려는 경우에는 XML 기반 도움말이 필요 합니다. 다음 예에서는 Update-Month 스크립트의 처음 몇 줄을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="7fa3c-122">스크립트는 `.ExternalHelp` 키워드를 사용 하 여 스크립트에 대 한 XML 기반 도움말 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="7fa3c-123">다음 예에서는 함수에서 `.ExternalHelp` 키워드를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="7fa3c-124">예 5: 다른 도움말 항목으로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="7fa3c-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="7fa3c-125">다음 코드는 한 번에 하나의 도움말 텍스트 화면을 표시 하는 Windows PowerShell의 기본 제공 `Help` 함수 시작 부분에서 발췌 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="7fa3c-126">Get-help cmdlet에 대 한 도움말 항목에서 도움말 함수를 설명 하므로 Help 함수는 `.ForwardHelpTargetName` 및 `.ForwardHelpCategory` 키워드를 사용 하 여 사용자를 Get-help cmdlet 도움말 항목으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="7fa3c-127">다음 명령은이 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-127">The following command uses this feature.</span></span> <span data-ttu-id="7fa3c-128">사용자가 Help 함수에 대 한 Get-help 명령을 입력 하면 get-help는 get-help cmdlet에 대 한 도움말 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fa3c-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```