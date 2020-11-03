---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/get-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-IseSnippet
ms.openlocfilehash: c43dae3f178ae778d78fe3718fa85fd2635eba86
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "93218105"
---
# <span data-ttu-id="12e32-103">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="12e32-103">Get-IseSnippet</span></span>

## <span data-ttu-id="12e32-104">개요</span><span class="sxs-lookup"><span data-stu-id="12e32-104">SYNOPSIS</span></span>
<span data-ttu-id="12e32-105">사용자가 만든 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-105">Gets snippets that the user created.</span></span>

## <span data-ttu-id="12e32-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="12e32-106">SYNTAX</span></span>

```
Get-IseSnippet [<CommonParameters>]
```

## <span data-ttu-id="12e32-107">설명</span><span class="sxs-lookup"><span data-stu-id="12e32-107">DESCRIPTION</span></span>

<span data-ttu-id="12e32-108">`Get-IseSnippet`Cmdlet은 사용자가 만든 재사용 가능한 텍스트 조각을 포함 하는 types.ps1xml 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-108">The `Get-IseSnippet` cmdlet gets the PS1XML files that contain reusable text snippets that the user created.</span></span> <span data-ttu-id="12e32-109">Windows PowerShell ISE (통합 스크립팅 환경) 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-109">It works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="12e32-110">Cmdlet을 사용 하 여 `New-IseSnippet` 코드 조각을 만들 때는 `New-IseSnippet` `<SnippetTitle>.Snippets.ps1xml` 디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="12e32-110">When you use the `New-IseSnippet` cmdlet to create a snippet, `New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
<span data-ttu-id="12e32-111">`Get-IseSnippet` 조각 디렉터리의 조각 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-111">`Get-IseSnippet` gets the snippet files in the Snippets directory.</span></span>

<span data-ttu-id="12e32-112">이 cmdlet은 cmdlet을 통해 모듈에서 가져온 코드 조각 또는 조각을 기본으로 가져오지 않습니다 `Import-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="12e32-112">This cmdlet does not get built-in snippets or snippets that are imported from modules through the `Import-IseSnippet` cmdlet.</span></span>

<span data-ttu-id="12e32-113">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-113">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="12e32-114">예제</span><span class="sxs-lookup"><span data-stu-id="12e32-114">EXAMPLES</span></span>

### <span data-ttu-id="12e32-115">예제 1: 모든 사용자 정의 코드 조각 가져오기</span><span class="sxs-lookup"><span data-stu-id="12e32-115">Example 1: Get all user-defined snippets</span></span>

<span data-ttu-id="12e32-116">이 예제에서는 코드 조각 디렉터리의 모든 사용자 정의 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-116">This example gets all user-define snippets in the Snippets directory.</span></span>

```powershell
Get-IseSnippet
```

### <span data-ttu-id="12e32-117">예제 2: 원격 컴퓨터의 모든 사용자 정의 조각을 공유 디렉터리에 복사</span><span class="sxs-lookup"><span data-stu-id="12e32-117">Example 2: Copy all user-defined snippets from remote computers to a shared directory</span></span>

<span data-ttu-id="12e32-118">이 예제에서는 원격 컴퓨터 그룹의 사용자가 만든 모든 조각을 공유 코드 조각 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-118">This example copies all of the user-created snippets from a group of remote computers to a shared Snippets directory.</span></span>

```powershell
Invoke-Command -Computer (Get-Content Servers.txt) {Get-IseSnippet | Copy-Item -Destination \\Server01\Share01\Snippets}
```

<span data-ttu-id="12e32-119">`Invoke-Command``Get-IseSnippet`파일의 컴퓨터에서 실행 됩니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="12e32-119">`Invoke-Command` runs `Get-IseSnippet` on the computers in the `Servers.txt` file.</span></span> <span data-ttu-id="12e32-120">파이프라인 연산자 ( `|` )는 조각 파일을 cmdlet으로 전송 하 여 `Copy-Item` **Destination** 매개 변수로 지정 된 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-120">A pipeline operator (`|`) sends the snippet files to the `Copy-Item` cmdlet, which copies them to the directory that is specified by the **Destination** parameter.</span></span>

### <span data-ttu-id="12e32-121">예제 3: 로컬 컴퓨터에 각 조각의 제목 및 텍스트 표시</span><span class="sxs-lookup"><span data-stu-id="12e32-121">Example 3: Display the title and text of each snippet on a local computer</span></span>

<span data-ttu-id="12e32-122">이 예제에서는 및 cmdlet을 사용 하 여 `Get-IseSnippet` `Select-Xml` 로컬 컴퓨터에 있는 각 조각의 제목과 텍스트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-122">This example uses the `Get-IseSnippet` and `Select-Xml` cmdlets to display the title and text of each snippet on the local computer.</span></span>

```powershell
#Parse-Snippet Function
function Parse-Snippet {
  $SnippetFiles = Get-IseSnippet
  $SnippetNamespace = @{x="http://schemas.microsoft.com/PowerShell/Snippets"}
  foreach ($SnippetFile in $SnippetFiles) {
     Write-Host ""
     $Title = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Title" |
       ForEach-Object {$_.Node.InnerXML}
     $Text = Select-Xml -Path $SnippetFile.FullName -Namespace $SnippetNamespace -XPath "//x:Script" |
       ForEach-Object {$_.Node.InnerText}
     Write-Host "Title: $Title"
     Write-Host "Text: $Text"
   }
}
```

```Output
Title: Mandatory
Text:
Param
(
  [parameter(Mandatory=True)]
  [String[]]
  $<ParameterName>
)

Title: Copyright
Text:  (c) Fabrikam, Inc. 2012
```

### <span data-ttu-id="12e32-123">예제 4: 세션의 모든 조각에 대 한 제목 및 설명 표시</span><span class="sxs-lookup"><span data-stu-id="12e32-123">Example 4: Display the title and description of all snippets in the session</span></span>

<span data-ttu-id="12e32-124">이 예제에서는 기본 제공 조각, 사용자 정의 조각 및 가져온 조각을 포함 하 여 세션에 있는 모든 조각의 제목 및 설명을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-124">This example displays the title and description of all snippets in the session, including built-in snippets, user-defined snippets, and imported snippets.</span></span>

```powershell
$PSISE.CurrentPowerShellTab.Snippets | Format-Table DisplayTitle, Description
```

<span data-ttu-id="12e32-125">`$PSISE`변수는 Windows PowerShell ISE 호스트 프로그램을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-125">The `$PSISE` variable represents the Windows PowerShell ISE host program.</span></span> <span data-ttu-id="12e32-126">변수의 **Currentpowershelltab** 속성은 `$PSISE` 현재 세션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-126">The **CurrentPowerShellTab** property of the `$PSISE` variable represent the current session.</span></span> <span data-ttu-id="12e32-127">**Snippets** 속성은 현재 세션의 조각을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-127">The **Snippets** property represents snippets in the current session.</span></span>

<span data-ttu-id="12e32-128">`$PSISE.CurrentPowerShellTab.Snippets`이 명령은 cmdlet과 달리 코드 조각을 나타내는 **new-isesnippet** 개체를 반환 합니다. `Get-IseSnippet`</span><span class="sxs-lookup"><span data-stu-id="12e32-128">The `$PSISE.CurrentPowerShellTab.Snippets` command returns a **Microsoft.PowerShell.Host.ISE.ISESnippet** object that represents a snippet, unlike the `Get-IseSnippet` cmdlet.</span></span> <span data-ttu-id="12e32-129">`Get-IseSnippet` 조각 파일을 나타내는 파일 개체 (System.web)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-129">`Get-IseSnippet` returns a file object (System.Io.FileInfo) that represents a snippet file.</span></span>

<span data-ttu-id="12e32-130">`Format-Table`Cmdlet은 테이블에 있는 코드 조각의 **displaytitle** 및 **Description** 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-130">The `Format-Table` cmdlet displays the **DisplayTitle** and **Description** properties of the snippets in a table.</span></span>

## <span data-ttu-id="12e32-131">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="12e32-131">PARAMETERS</span></span>

### <span data-ttu-id="12e32-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="12e32-132">CommonParameters</span></span>

<span data-ttu-id="12e32-133">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="12e32-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="12e32-134">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12e32-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="12e32-135">입력</span><span class="sxs-lookup"><span data-stu-id="12e32-135">INPUTS</span></span>

## <span data-ttu-id="12e32-136">출력</span><span class="sxs-lookup"><span data-stu-id="12e32-136">OUTPUTS</span></span>

### <span data-ttu-id="12e32-137">System.object</span><span class="sxs-lookup"><span data-stu-id="12e32-137">System.IO.FileInfo</span></span>

<span data-ttu-id="12e32-138">이 cmdlet은 조각 파일을 나타내는 file 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-138">This cmdlet returns a file object that represents the snippet file.</span></span>

## <span data-ttu-id="12e32-139">참고</span><span class="sxs-lookup"><span data-stu-id="12e32-139">NOTES</span></span>

* <span data-ttu-id="12e32-140">`New-IseSnippet`Cmdlet은 types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-140">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="12e32-141">따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션에 이러한 조각을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-141">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted**.</span></span> <span data-ttu-id="12e32-142">**Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-142">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="12e32-143">Cmdlet에서 반환 하는 서명 되지 않은 사용자 생성 코드 조각을 사용 하려면 `Get-IseSnippet` 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="12e32-143">To use unsigned user-created snippets that the `Get-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="12e32-144">Windows PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="12e32-144">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="12e32-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="12e32-145">RELATED LINKS</span></span>

[<span data-ttu-id="12e32-146">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="12e32-146">New-IseSnippet</span></span>](New-IseSnippet.md)

[<span data-ttu-id="12e32-147">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="12e32-147">Import-IseSnippet</span></span>](Import-IseSnippet.md)
