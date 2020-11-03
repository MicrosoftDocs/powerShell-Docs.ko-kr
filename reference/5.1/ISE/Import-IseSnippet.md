---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/import-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-IseSnippet
ms.openlocfilehash: 810be675fc593f665ccc6f3d5b86ac2f6b633863
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212385"
---
# <span data-ttu-id="0bbb1-103">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="0bbb1-103">Import-IseSnippet</span></span>

## <span data-ttu-id="0bbb1-104">개요</span><span class="sxs-lookup"><span data-stu-id="0bbb1-104">SYNOPSIS</span></span>
<span data-ttu-id="0bbb1-105">ISE 조각을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-105">Imports ISE snippets into the current session</span></span>

## <span data-ttu-id="0bbb1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0bbb1-106">SYNTAX</span></span>

### <span data-ttu-id="0bbb1-107">FromFolder (기본값)</span><span class="sxs-lookup"><span data-stu-id="0bbb1-107">FromFolder (Default)</span></span>

```
Import-IseSnippet [-Path] <String> [-Recurse] [<CommonParameters>]
```

### <span data-ttu-id="0bbb1-108">FromModule</span><span class="sxs-lookup"><span data-stu-id="0bbb1-108">FromModule</span></span>

```
Import-IseSnippet [-Recurse] -Module <String> [-ListAvailable] [<CommonParameters>]
```

## <span data-ttu-id="0bbb1-109">설명</span><span class="sxs-lookup"><span data-stu-id="0bbb1-109">DESCRIPTION</span></span>

<span data-ttu-id="0bbb1-110">`Import-IseSnippet`Cmdlet은 다시 사용할 수 있는 텍스트 "조각"을 모듈 또는 디렉터리에서 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-110">The `Import-IseSnippet` cmdlet imports reusable text "snippets" from a module or a directory into the current session.</span></span> <span data-ttu-id="0bbb1-111">코드 조각은 Windows PowerShell ISE에서 바로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-111">The snippets are immediately available for use in Windows PowerShell ISE.</span></span> <span data-ttu-id="0bbb1-112">이 cmdlet은 Windows PowerShell ISE (통합 스크립팅 환경) 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-112">This cmdlet works only in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

<span data-ttu-id="0bbb1-113">가져온 조각을 보고 사용 하려면 Windows PowerShell ISE **편집** 메뉴에서 **코드 조각 시작** 을 클릭 하거나 <kbd>ctrl</kbd> + <kbd>J</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-113">To view and use the imported snippets, from the Windows PowerShell ISE **Edit** menu, click **Start Snippets** or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="0bbb1-114">가져온 조각은 현재 세션에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-114">Imported snippets are available only in the current session.</span></span> <span data-ttu-id="0bbb1-115">코드 조각을 모든 Windows PowerShell ISE 세션으로 가져오려면 `Import-IseSnippet` Windows PowerShell 프로필에 명령을 추가 하거나 조각 파일을 로컬 코드 조각 디렉터리에 복사 `$home\Documents\WindowsPowershell\Snippets` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-115">To import the snippets into all Windows PowerShell ISE sessions, add an `Import-IseSnippet` command to your Windows PowerShell profile or copy the snippet files to your local snippets directory `$home\Documents\WindowsPowershell\Snippets`.</span></span>

<span data-ttu-id="0bbb1-116">코드 조각을 가져오려면 코드 조각 XML에서 Windows PowerShell ISE 코드 조각을 적절히 지정 하 고 Snippet.ps1XML 파일에 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-116">To import snippets, they must be properly formatted in the snippet XML for Windows PowerShell ISE snippets and saved in Snippet.ps1xml files.</span></span> <span data-ttu-id="0bbb1-117">적격 코드 조각을 만들려면 cmdlet을 사용 `New-IseSnippet` 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-117">To create eligible snippets, use the `New-IseSnippet` cmdlet.</span></span> <span data-ttu-id="0bbb1-118">`New-IseSnippet``<SnippetTitle>.Snippets.ps1xml`디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="0bbb1-118">`New-IseSnippet` creates a `<SnippetTitle>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span> <span data-ttu-id="0bbb1-119">조각을 Windows PowerShell 모듈의 Snippets 디렉터리나 다른 디렉터리로 이동하거나 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-119">You can move or copy the snippets to the Snippets directory of a Windows PowerShell module, or to any other directory.</span></span>

<span data-ttu-id="0bbb1-120">`Get-IseSnippet`로컬 코드 조각 디렉터리에서 사용자가 만든 코드 조각을 가져오는 cmdlet은 가져온 조각을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-120">The `Get-IseSnippet` cmdlet, which gets user-created snippets in the local snippets directory, does not get imported snippets.</span></span>

<span data-ttu-id="0bbb1-121">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="0bbb1-122">예제</span><span class="sxs-lookup"><span data-stu-id="0bbb1-122">EXAMPLES</span></span>

### <span data-ttu-id="0bbb1-123">예제 1: 디렉터리에서 조각 가져오기</span><span class="sxs-lookup"><span data-stu-id="0bbb1-123">Example 1: Import snippets from a directory</span></span>

<span data-ttu-id="0bbb1-124">이 예제에서는 디렉터리의 조각을 `\\Server01\Public\Snippets` 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-124">This example imports the snippets from the `\\Server01\Public\Snippets` directory into the current session.</span></span> <span data-ttu-id="0bbb1-125">**재귀** 매개 변수를 사용 하 여 조각 디렉터리의 모든 하위 디렉터리에서 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-125">It uses the **Recurse** parameter to get snippets from all subdirectories of the Snippets directory.</span></span>

```powershell
Import-IseSnippet -Path \\Server01\Public\Snippets -Recurse
```

### <span data-ttu-id="0bbb1-126">예제 2: 모듈에서 조각 가져오기</span><span class="sxs-lookup"><span data-stu-id="0bbb1-126">Example 2: Import snippets from a module</span></span>

<span data-ttu-id="0bbb1-127">이 예제에서는 **SnippetModule** 모듈에서 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-127">This example imports the snippets from the **SnippetModule** module.</span></span> <span data-ttu-id="0bbb1-128">명령이 실행 될 때 **SnippetModule** 모듈을 사용자의 세션으로 가져오지 않은 경우에도이 명령은 **ListAvailable** 매개 변수를 사용 하 여 코드 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-128">The command uses the **ListAvailable** parameter to import the snippets even if the **SnippetModule** module is not imported into the user's session when the command runs.</span></span>

```powershell
Import-IseSnippet -Module SnippetModule -ListAvailable
```

### <span data-ttu-id="0bbb1-129">예제 3: 모듈의 조각 찾기</span><span class="sxs-lookup"><span data-stu-id="0bbb1-129">Example 3: Find snippets in modules</span></span>

<span data-ttu-id="0bbb1-130">이 예제에서는 PSModulePath 환경 변수에 설치 된 모든 모듈의 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-130">This example gets snippets in all installed modules in the PSModulePath environment variable.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$_.fullname}
```

### <span data-ttu-id="0bbb1-131">예제 4: 모든 모듈 코드 조각 가져오기</span><span class="sxs-lookup"><span data-stu-id="0bbb1-131">Example 4: Import all module snippets</span></span>

<span data-ttu-id="0bbb1-132">이 예제에서는 설치 된 모든 모듈의 모든 조각을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-132">This example imports all snippets from all installed modules into the current session.</span></span> <span data-ttu-id="0bbb1-133">일반적으로 코드 조각이 있는 모듈은 `Import-IseSnippet` 모듈을 가져올 때 cmdlet을 사용 하 여이를 가져오기 때문에 다음과 같은 명령을 실행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-133">Typically, you don't need to run a command like this because modules that have snippets will use the `Import-IseSnippet` cmdlet to import them for you when the module is imported.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    ForEach-Object {$psise.CurrentPowerShellTab.Snippets.Load($_)}
```

### <span data-ttu-id="0bbb1-134">예 5: 모든 모듈 조각 복사</span><span class="sxs-lookup"><span data-stu-id="0bbb1-134">Example 5: Copy all module snippets</span></span>

<span data-ttu-id="0bbb1-135">이 예제에서는 설치 된 모든 모듈의 조각 파일을 현재 사용자의 조각 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-135">This example copies the snippet files from all installed modules into the Snippets directory of the current user.</span></span> <span data-ttu-id="0bbb1-136">현재 세션에만 영향을 주는 가져온 조각과 달리 복사된 조각은 모든 Windows PowerShell ISE 세션에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-136">Unlike imported snippets, which affect only the current session, copied snippets are available in every Windows PowerShell ISE session.</span></span>

```powershell
($env:PSModulePath).split(";") |
  ForEach-Object {dir $_\*\Snippets\*.Snippets.ps1xml -ErrorAction SilentlyContinue} |
    Copy-Item -Destination $home\Documents\WindowsPowerShell\Snippets
```

## <span data-ttu-id="0bbb1-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0bbb1-137">PARAMETERS</span></span>

### <span data-ttu-id="0bbb1-138">-ListAvailable</span><span class="sxs-lookup"><span data-stu-id="0bbb1-138">-ListAvailable</span></span>

<span data-ttu-id="0bbb1-139">이 cmdlet은 모듈을 현재 세션으로 가져오지 않은 경우에도 컴퓨터에 설치 된 모듈에서 조각을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-139">Indicates that this cmdlet gets snippets from modules that are installed on the computer, even if the modules are not imported into the current session.</span></span> <span data-ttu-id="0bbb1-140">이 매개 변수를 생략 하 고 **module** 매개 변수에 지정 된 모듈을 현재 세션으로 가져오지 않은 경우 모듈에서 코드 조각을 가져오지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-140">If this parameter is omitted, and the module that is specified by the **Module** parameter is not imported into the current session, the attempt to get the snippets from the module fails.</span></span>

<span data-ttu-id="0bbb1-141">이 매개 변수는 **Module** 매개 변수가 명령에 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-141">This parameter is valid only when the **Module** parameter is used in the command.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: FromModule
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bbb1-142">-모듈</span><span class="sxs-lookup"><span data-stu-id="0bbb1-142">-Module</span></span>

<span data-ttu-id="0bbb1-143">지정된 모듈의 조각을 현재 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-143">Imports snippets from the specified module into the current session.</span></span> <span data-ttu-id="0bbb1-144">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-144">Wildcard characters are not supported.</span></span>

<span data-ttu-id="0bbb1-145">이 매개 변수는와 같은 모듈 경로에 있는 코드 조각 하위 디렉터리에 있는 Snippet.ps1xml 파일에서 조각을 가져옵니다 `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="0bbb1-145">This parameter imports snippets from Snippet.ps1xml files in the Snippets subdirectory in the module path, such as `$home\Documents\WindowsPowerShell\Modules\<ModuleName>\Snippets`.</span></span>

<span data-ttu-id="0bbb1-146">이 매개 변수는 모듈 작성자가 시작 스크립트(예: 모듈 매니페스트의 **ScriptsToProcess** 키에 지정된 스크립트)에 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-146">This parameter is designed to be used by module authors in a startup script, such as a script specified in the **ScriptsToProcess** key of a module manifest.</span></span> <span data-ttu-id="0bbb1-147">모듈의 조각은 모듈을 사용 하 여 자동으로 가져오지 않지만 명령을 사용 하 여 가져올 수 있습니다 `Import-IseSnippet` .</span><span class="sxs-lookup"><span data-stu-id="0bbb1-147">Snippets in a module are not automatically imported with the module, but you can use an `Import-IseSnippet` command to import them.</span></span>

```yaml
Type: System.String
Parameter Sets: FromModule
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0bbb1-148">-Path</span><span class="sxs-lookup"><span data-stu-id="0bbb1-148">-Path</span></span>

<span data-ttu-id="0bbb1-149">이 cmdlet이 조각을 가져오는 조각 디렉터리의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-149">Specifies the path to the snippets directory in which this cmdlet imports snippets.</span></span>

```yaml
Type: System.String
Parameter Sets: FromFolder
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0bbb1-150">-재귀</span><span class="sxs-lookup"><span data-stu-id="0bbb1-150">-Recurse</span></span>

<span data-ttu-id="0bbb1-151">이 cmdlet은 **Path** 매개 변수 값의 모든 하위 디렉터리에서 조각을 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-151">Indicates that this cmdlet imports snippets from all subdirectories of the value of the **Path** parameter.</span></span>

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

### <span data-ttu-id="0bbb1-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0bbb1-152">CommonParameters</span></span>

<span data-ttu-id="0bbb1-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0bbb1-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0bbb1-155">입력</span><span class="sxs-lookup"><span data-stu-id="0bbb1-155">INPUTS</span></span>

### <span data-ttu-id="0bbb1-156">없음</span><span class="sxs-lookup"><span data-stu-id="0bbb1-156">None</span></span>

<span data-ttu-id="0bbb1-157">이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-157">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="0bbb1-158">출력</span><span class="sxs-lookup"><span data-stu-id="0bbb1-158">OUTPUTS</span></span>

### <span data-ttu-id="0bbb1-159">없음</span><span class="sxs-lookup"><span data-stu-id="0bbb1-159">None</span></span>

<span data-ttu-id="0bbb1-160">이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-160">This cmdlet does not generate output.</span></span>

## <span data-ttu-id="0bbb1-161">참고</span><span class="sxs-lookup"><span data-stu-id="0bbb1-161">NOTES</span></span>

- <span data-ttu-id="0bbb1-162">`Get-IseSnippet`가져온 코드 조각은 cmdlet을 사용 하 여 가져올 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-162">You cannot use the `Get-IseSnippet` cmdlet to get imported snippets.</span></span> <span data-ttu-id="0bbb1-163">`Get-IseSnippet` 디렉터리의 조각만 가져옵니다 `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="0bbb1-163">`Get-IseSnippet` gets only snippets in the `$home\Documents\WindowsPowerShell\Snippets` directory.</span></span>
- <span data-ttu-id="0bbb1-164">`Import-IseSnippet`**ISESnippetCollection** 개체의 **Load** 정적 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-164">`Import-IseSnippet` uses the **Load** static method of **Microsoft.PowerShell.Host.ISE.ISESnippetCollection** objects.</span></span> <span data-ttu-id="0bbb1-165">Windows PowerShell ISE 개체 모델에서 코드 조각의 **Load** 메서드를 사용할 수도 있습니다. `$psISE.CurrentPowerShellTab.Snippets.Load()`</span><span class="sxs-lookup"><span data-stu-id="0bbb1-165">You can also use the **Load** method of snippets in the Windows PowerShell ISE object model: `$psISE.CurrentPowerShellTab.Snippets.Load()`</span></span>
- <span data-ttu-id="0bbb1-166">`New-IseSnippet`Cmdlet은 types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-166">The `New-IseSnippet` cmdlet stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="0bbb1-167">따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션으로 이러한 조각을 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-167">As such, Windows PowerShell cannot load them into a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="0bbb1-168">**Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-168">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

  <span data-ttu-id="0bbb1-169">Cmdlet에서 반환 하는 서명 되지 않은 사용자 생성 코드 조각을 사용 하려면 `Import-IseSnippet` 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-169">To use unsigned user-created snippets that the `Import-IseSnippet` cmdlet returns, change the execution policy, and then restart Windows PowerShell ISE.</span></span>

  <span data-ttu-id="0bbb1-170">Windows PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0bbb1-170">For more information about Windows PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

## <span data-ttu-id="0bbb1-171">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0bbb1-171">RELATED LINKS</span></span>

[<span data-ttu-id="0bbb1-172">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="0bbb1-172">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="0bbb1-173">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="0bbb1-173">New-IseSnippet</span></span>](New-IseSnippet.md)
