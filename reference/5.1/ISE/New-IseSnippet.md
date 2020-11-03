---
external help file: ISE-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: ISE
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/ise/new-isesnippet?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-IseSnippet
ms.openlocfilehash: 0ed1c2913fc7531574bfbdd435a002d60931d24a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212378"
---
# <span data-ttu-id="29db2-103">New-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="29db2-103">New-IseSnippet</span></span>

## <span data-ttu-id="29db2-104">개요</span><span class="sxs-lookup"><span data-stu-id="29db2-104">SYNOPSIS</span></span>
<span data-ttu-id="29db2-105">Windows PowerShell ISE 코드 조각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-105">Creates a Windows PowerShell ISE code snippet.</span></span>

## <span data-ttu-id="29db2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="29db2-106">SYNTAX</span></span>

```
New-IseSnippet [-Title] <String> [-Description] <String> [-Text] <String> [-Author <String>]
 [-CaretOffset <Int32>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="29db2-107">설명</span><span class="sxs-lookup"><span data-stu-id="29db2-107">DESCRIPTION</span></span>

<span data-ttu-id="29db2-108">`New-ISESnippet`Cmdlet은 Windows PowerShell ISE을 위한 다시 사용할 수 있는 텍스트 "조각"을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-108">The `New-ISESnippet` cmdlet creates a reusable text "snippet" for Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-109">조각을 사용하여 Windows PowerShell ISE의 스크립트 창 또는 명령 창에 텍스트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-109">You can use snippets to add text to the Script pane or Command pane in Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-110">이 cmdlet은 Windows PowerShell ISE에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-110">This cmdlet is available only in Windows PowerShell ISE.</span></span>

<span data-ttu-id="29db2-111">Windows PowerShell 3.0부터 Windows PowerShell ISE에는 기본 제공 조각 컬렉션이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-111">Beginning in Windows PowerShell 3.0, Windows PowerShell ISE includes a collection of built-in snippets.</span></span> <span data-ttu-id="29db2-112">Cmdlet을 사용 하 여 `New-ISESnippet` 기본 제공 컬렉션에 추가할 고유한 코드 조각을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-112">The `New-ISESnippet` cmdlet lets you create your own snippets to add to the built-in collection.</span></span> <span data-ttu-id="29db2-113">조각 파일을 보고, 변경하며, 추가하고, 삭제하며, 공유하고, Windows PowerShell 모듈에 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-113">You can view, change, add, delete, and share snippet files and include them in Windows PowerShell modules.</span></span> <span data-ttu-id="29db2-114">Windows PowerShell ISE에서 코드 조각을 보려면 **편집** 메뉴에서 **코드 조각 시작** 을 선택 하거나 <kbd>ctrl</kbd> + <kbd>J</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-114">To see snippets in Windows PowerShell ISE, from the **Edit** menu, select **Start Snippets** or press <kbd>CTRL</kbd>+<kbd>J</kbd>.</span></span>

<span data-ttu-id="29db2-115">`New-ISESnippet`Cmdlet은 `<Title>.Snippets.ps1xml` 지정한 제목을 사용 하 여 디렉터리에 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="29db2-115">The `New-ISESnippet` cmdlet creates a `<Title>.Snippets.ps1xml` file in the `$home\Documents\WindowsPowerShell\Snippets` directory with the title that you specify.</span></span> <span data-ttu-id="29db2-116">작성 중인 모듈에 조각 파일을 포함하려면 모듈 디렉터리의 Snippets 하위 디렉터리에 조각 파일을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-116">To include a snippet file in a module that you are authoring, add the snippet file to a Snippets subdirectory of your module directory.</span></span>

<span data-ttu-id="29db2-117">실행 정책이 **제한** 되거나 **AllSigned** 세션에서 사용자가 만든 코드 조각을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-117">You cannot use user-created snippets in a session in which the execution policy is **Restricted** or **AllSigned** .</span></span>

<span data-ttu-id="29db2-118">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="29db2-119">예제</span><span class="sxs-lookup"><span data-stu-id="29db2-119">EXAMPLES</span></span>

### <span data-ttu-id="29db2-120">예제 1: Comment-Based 도움말 코드 조각 만들기</span><span class="sxs-lookup"><span data-stu-id="29db2-120">Example 1: Create a Comment-Based help snippet</span></span>

```
New-IseSnippet -Title Comment-BasedHelp -Description "A template for comment-based help." -Text "<#
    .SYNOPSIS

    .DESCRIPTION
    .PARAMETER  <Parameter-Name>
    .INPUTS
    .OUTPUTS
    .EXAMPLE
    .LINK
#>"
```

<span data-ttu-id="29db2-121">이 명령은 Windows PowerShell ISE용 Comment-BasedHelp 조각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-121">This command creates a Comment-BasedHelp snippet for Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-122">`Comment-BasedHelp.snippets.ps1xml`사용자의 코드 조각 디렉터리에 이라는 파일을 만듭니다 `$home\Documents\WindowsPowerShell\Snippets` .</span><span class="sxs-lookup"><span data-stu-id="29db2-122">It creates a file named `Comment-BasedHelp.snippets.ps1xml` in the user's Snippets directory `$home\Documents\WindowsPowerShell\Snippets`.</span></span>

### <span data-ttu-id="29db2-123">예제 2: 필수 코드 조각 만들기</span><span class="sxs-lookup"><span data-stu-id="29db2-123">Example 2: Create a mandatory snippet</span></span>

```
$M = @'
Param
(
  [parameter(Mandatory=$true)]
  [String[]]
  $<ParameterName>
)
'@

New-ISESnippet -Text $M -Title Mandatory -Description "Adds a mandatory function parameter." -Author "Patti Fuller, Fabrikam Corp." -Force
```

<span data-ttu-id="29db2-124">이 예제에서는 Windows PowerShell ISE에 대 한 **필수** 라는 코드 조각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-124">This example creates a snippet named **Mandatory** for Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-125">첫 번째 명령은 조각 텍스트를 변수에 저장 합니다 `$M` .</span><span class="sxs-lookup"><span data-stu-id="29db2-125">The first command saves the snippet text in the `$M` variable.</span></span> <span data-ttu-id="29db2-126">두 번째 명령은 cmdlet을 사용 하 여 `New-ISESnippet` 코드 조각을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-126">The second command uses the `New-ISESnippet` cmdlet to create the snippet.</span></span> <span data-ttu-id="29db2-127">이 명령은 **Force** 매개 변수를 사용하여 이전 조각을 같은 이름으로 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-127">The command uses the **Force** parameter to overwrite a previous snippet with the same name.</span></span>

### <span data-ttu-id="29db2-128">예 3: 폴더의 필수 코드 조각을 대상 폴더로 복사</span><span class="sxs-lookup"><span data-stu-id="29db2-128">Example 3: Copy a mandatory snippet from a folder to a destination folder</span></span>

```
Copy-Item "$Home\Documents\WindowsPowerShell\Snippets\Mandatory.Snippets.ps1xml" -Destination "\\Server\Share"
```

<span data-ttu-id="29db2-129">이 명령은 cmdlet을 사용 하 여 `Copy-Item` Server\Share 파일 공유에 배치 하는 폴더에서 **필수** 코드 조각을 복사 `New-ISESnippet` 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-129">This command uses the `Copy-Item` cmdlet to copy the **Mandatory** snippet from the folder where `New-ISESnippet` places it to the Server\Share file share.</span></span>

## <span data-ttu-id="29db2-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="29db2-130">PARAMETERS</span></span>

### <span data-ttu-id="29db2-131">-작성자</span><span class="sxs-lookup"><span data-stu-id="29db2-131">-Author</span></span>

<span data-ttu-id="29db2-132">코드 조각의 작성자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-132">Specifies the author of the snippet.</span></span> <span data-ttu-id="29db2-133">작성자 필드는 조각 파일에 나타나지만 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-133">The author field appears in the snippet file, but it does not appear when you click the snippet name in Windows PowerShell ISE.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-134">-CaretOffset</span><span class="sxs-lookup"><span data-stu-id="29db2-134">-CaretOffset</span></span>

<span data-ttu-id="29db2-135">이 cmdlet이 커서를 배치할 조각 텍스트의 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-135">Specifies the character of the snippet text that this cmdlet places the cursor on.</span></span> <span data-ttu-id="29db2-136">커서 위치를 나타내는 정수를 입력합니다. 여기서 "1"은 텍스트의 첫 번째 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-136">Enter an integer that represents the cursor position, with "1" representing the first character of text.</span></span> <span data-ttu-id="29db2-137">기본값 0(영)은 커서를 텍스트의 첫 번째 문자 바로 앞에 둡니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-137">The default value, 0 (zero), places the cursor immediately before the first character of text.</span></span> <span data-ttu-id="29db2-138">이 매개 변수는 조각 텍스트를 들여쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-138">This parameter does not indent the snippet text.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-139">-Description</span><span class="sxs-lookup"><span data-stu-id="29db2-139">-Description</span></span>

<span data-ttu-id="29db2-140">조각에 대 한 설명을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-140">Specifies a description of the snippet.</span></span> <span data-ttu-id="29db2-141">설명 값은 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-141">The description value appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-142">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-142">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-143">-Force</span><span class="sxs-lookup"><span data-stu-id="29db2-143">-Force</span></span>

<span data-ttu-id="29db2-144">이 cmdlet이 같은 위치에 있는 동일한 이름의 조각 파일을 덮어쓰도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-144">Indicates that this cmdlet overwrites snippet files with the same name in the same location.</span></span> <span data-ttu-id="29db2-145">기본적으로는 `New-ISESnippet` 파일을 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-145">By default, `New-ISESnippet` does not overwrite files.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-146">-텍스트</span><span class="sxs-lookup"><span data-stu-id="29db2-146">-Text</span></span>

<span data-ttu-id="29db2-147">조각을 선택할 때 추가되는 텍스트 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-147">Specifies the text value that is added when you select the snippet.</span></span> <span data-ttu-id="29db2-148">조각 텍스트는 Windows PowerShell ISE에서 조각 이름을 클릭하면 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-148">The snippet text appears when you click the snippet name in Windows PowerShell ISE.</span></span> <span data-ttu-id="29db2-149">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-149">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-150">-Title</span><span class="sxs-lookup"><span data-stu-id="29db2-150">-Title</span></span>

<span data-ttu-id="29db2-151">조각의 제목 또는 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-151">Specifies a title or name for the snippet.</span></span> <span data-ttu-id="29db2-152">제목은 조각 파일의 이름도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-152">The title also names the snippet file.</span></span> <span data-ttu-id="29db2-153">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-153">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="29db2-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="29db2-154">CommonParameters</span></span>

<span data-ttu-id="29db2-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="29db2-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="29db2-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29db2-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="29db2-157">입력</span><span class="sxs-lookup"><span data-stu-id="29db2-157">INPUTS</span></span>

### <span data-ttu-id="29db2-158">없음</span><span class="sxs-lookup"><span data-stu-id="29db2-158">None</span></span>

<span data-ttu-id="29db2-159">이 cmdlet은 파이프라인에서 입력을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-159">This cmdlet does not take input from the pipeline.</span></span>

## <span data-ttu-id="29db2-160">출력</span><span class="sxs-lookup"><span data-stu-id="29db2-160">OUTPUTS</span></span>

### <span data-ttu-id="29db2-161">없음</span><span class="sxs-lookup"><span data-stu-id="29db2-161">None</span></span>

<span data-ttu-id="29db2-162">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-162">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="29db2-163">참고</span><span class="sxs-lookup"><span data-stu-id="29db2-163">NOTES</span></span>

<span data-ttu-id="29db2-164">`New-IseSnippet` types.ps1xml 파일에 새 사용자가 만든 코드 조각을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-164">`New-IseSnippet` stores new user-created snippets in unsigned .ps1xml files.</span></span> <span data-ttu-id="29db2-165">따라서 Windows PowerShell은 실행 정책이 **AllSigned** 또는 **Restricted** 인 세션에 이러한 조각을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-165">As such, Windows PowerShell cannot add them to a session in which the execution policy is **AllSigned** or **Restricted** .</span></span> <span data-ttu-id="29db2-166">**Restricted** 또는 **AllSigned** 세션에서는 사용자가 만든 서명되지 않은 조각을 만들고 가져올 수는 있지만 세션에 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-166">In a **Restricted** or **AllSigned** session, you can create, get, and import unsigned user-created snippets, but you cannot use them in the session.</span></span>

<span data-ttu-id="29db2-167">`New-IseSnippet` **제한** 된 또는 **AllSigned** 세션에서 cmdlet을 사용 하는 경우 코드 조각이 만들어지지만 Windows PowerShell에서 새로 만든 코드 조각을 세션에 추가 하려고 할 때 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-167">If you use the `New-IseSnippet` cmdlet in a **Restricted** or **AllSigned** session, the snippet is created, but an error message appears when Windows PowerShell tries to add the newly created snippet to the session.</span></span> <span data-ttu-id="29db2-168">새 조각과 사용자가 만든 서명되지 않은 다른 조각을 사용하려면 실행 정책을 변경한 후 Windows PowerShell ISE를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-168">To use the new snippet (and other unsigned user-created snippets), change the execution policy, and then restart Windows PowerShell ISE.</span></span>

<span data-ttu-id="29db2-169">Windows PowerShell 실행 정책에 대한 자세한 내용은 about_Execution_Policies(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29db2-169">For more information about Windows PowerShell execution policies, see about_Execution_Policies.</span></span>

- <span data-ttu-id="29db2-170">코드 조각을 변경 하려면 조각 파일을 편집 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-170">To change a snippet, edit the snippet file.</span></span> <span data-ttu-id="29db2-171">Windows PowerShell ISE의 스크립트 창에서 조각 파일을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-171">You can edit snippet files in the Script pane of Windows PowerShell ISE.</span></span>
- <span data-ttu-id="29db2-172">추가한 코드 조각을 삭제 하려면 조각 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-172">To delete a snippet that you added, delete the snippet file.</span></span>
- <span data-ttu-id="29db2-173">기본 제공 코드 조각은 삭제할 수 없지만 "$psise를 사용 하 여 모든 기본 제공 코드 조각을 숨길 수 있습니다. Options. ShowDefaultSnippets = $false "명령입니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-173">You cannot delete a built-in snippet, but you can hide all built-in snippets by using the "$psise.Options.ShowDefaultSnippets=$false" command.</span></span>
- <span data-ttu-id="29db2-174">기본 제공 코드 조각과 동일한 이름을 가진 코드 조각을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-174">You can create a snippet that has the same name as a built-in snippet.</span></span> <span data-ttu-id="29db2-175">두 조각 모두 Windows PowerShell ISE의 조각 메뉴에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="29db2-175">Both snippets appear in the snippet menu in Windows PowerShell ISE.</span></span>

## <span data-ttu-id="29db2-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="29db2-176">RELATED LINKS</span></span>

[<span data-ttu-id="29db2-177">Get-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="29db2-177">Get-IseSnippet</span></span>](Get-IseSnippet.md)

[<span data-ttu-id="29db2-178">Import-IseSnippet</span><span class="sxs-lookup"><span data-stu-id="29db2-178">Import-IseSnippet</span></span>](Import-IseSnippet.md)
