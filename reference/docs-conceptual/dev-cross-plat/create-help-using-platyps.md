---
title: PlatyPS를 사용하여 XML 기반 도움말 만들기
description: PlatyPS를 사용하면 XML 기반 도움말을 빠르고 효율적으로 만들 수 있습니다.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972583"
---
# <a name="create-xml-based-help-using-platyps"></a><span data-ttu-id="183ed-103">PlatyPS를 사용하여 XML 기반 도움말 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-103">Create XML-based help using PlatyPS</span></span>

<span data-ttu-id="183ed-104">PowerShell 모듈을 만들 때 만드는 cmdlet에 관한 자세한 도움말을 포함하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-104">When creating a PowerShell module, it is always recommended that you include detailed help for the cmdlets you create.</span></span> <span data-ttu-id="183ed-105">컴파일된 코드에서 cmdlet을 구현하는 경우에는 XML 기반 도움말을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-105">If your cmdlets are implemented in compiled code, you must use the XML-based help.</span></span> <span data-ttu-id="183ed-106">해당 XML 형식을 MAML(Microsoft Assistance Markup Language)이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-106">This XML format is known as the Microsoft Assistance Markup Language (MAML).</span></span>

<span data-ttu-id="183ed-107">레거시 PowerShell SDK 설명서에서는 모듈에 패키지된 PowerShell cmdlet에 관한 도움말을 만드는 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-107">The legacy PowerShell SDK documentation covers the details of creating help for PowerShell cmdlets packaged into modules.</span></span> <span data-ttu-id="183ed-108">그러나 PowerShell은 XML 기반 도움말을 만들기 위한 도구를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-108">However, PowerShell does not provide any tools for creating the XML-based help.</span></span> <span data-ttu-id="183ed-109">SDK 설명서에서는 MAML 도움말의 구조를 설명하지만 복잡하고 깊게 중첩된 MAML 콘텐츠는 사용자가 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-109">The SDK documentation explains the structure of MAML help, but leaves you the task of creating the complex, and deeply nested, MAML content by hand.</span></span>

<span data-ttu-id="183ed-110">해당 작업에는 [PlatyPS][] 모듈이 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-110">This is where the [PlatyPS][] module can help.</span></span>

## <a name="what-is-platyps"></a><span data-ttu-id="183ed-111">PlatyPS란?</span><span class="sxs-lookup"><span data-stu-id="183ed-111">What is PlatyPS?</span></span>

<span data-ttu-id="183ed-112">PlatyPS는 MAML을 더 쉽게 만들고 유지 관리할 수 있도록 ‘해커톤’ 프로젝트로 시작한 [오픈 소스][platyps-repo] 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-112">PlatyPS is an [open-source][platyps-repo] tool that started as a _hackathon_ project to make the creation and maintenance of MAML easier.</span></span> <span data-ttu-id="183ed-113">PlatyPS는 모듈에서 각 cmdlet의 매개 변수 세트 및 개별 매개 변수에 관한 구문을 문서화합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-113">PlatyPS documents the syntax of parameter sets and the individual parameters for each cmdlet in your module.</span></span> <span data-ttu-id="183ed-114">PlatyPS는 구문 정보를 포함하는 구조화된 [Markdown][] 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-114">PlatyPS creates structured [Markdown][] files that contain the syntax information.</span></span> <span data-ttu-id="183ed-115">설명을 만들거나 예제를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-115">It can't create descriptions or provide examples.</span></span>

<span data-ttu-id="183ed-116">PlatyPS는 설명 및 예제를 입력할 자리 표시자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-116">PlatyPS creates placeholders for you to fill in descriptions and examples.</span></span> <span data-ttu-id="183ed-117">필요한 정보를 추가한 후 PlatyPS는 Markdown 파일을 MAML 파일로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-117">After adding the required information, PlatyPS compiles the Markdown files into MAML files.</span></span> <span data-ttu-id="183ed-118">PowerShell의 도움말 시스템에서는 일반 텍스트 개념 도움말 파일(정보 항목)도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-118">PowerShell's help system also allows for plain-text conceptual help files (about topics).</span></span> <span data-ttu-id="183ed-119">PlatyPS에는 새 ‘정보’ 파일의 구조화된 Markdown 템플릿을 만드는 cmdlet이 있지만, 해당 `about_*.help.txt` 파일은 수동으로 유지 관리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-119">PlatyPS has a cmdlet to create a structured Markdown template for a new _about_ file, but these `about_*.help.txt` files must be maintained manually.</span></span>

<span data-ttu-id="183ed-120">모듈에 MAML 및 텍스트 도움말 파일을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-120">You can include the MAML and Text help files with your module.</span></span> <span data-ttu-id="183ed-121">PlatyPS를 사용하여 도움말 파일을 업데이트 가능한 도움말용으로 호스트될 수 있는 CAB 패키지로 컴파일할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-121">You can also use PlatyPS to compile the help files into a CAB package that can be hosted for updateable help.</span></span>

## <a name="get-started-using-platyps"></a><span data-ttu-id="183ed-122">PlatyPS를 사용하여 시작</span><span class="sxs-lookup"><span data-stu-id="183ed-122">Get started using PlatyPS</span></span>

<span data-ttu-id="183ed-123">먼저 PowerShell 갤러리에서 PlatyPS를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-123">First you must install PlatyPS from the PowerShell Gallery.</span></span>

```powershell
Install-Module platyps -Force
Import-Module platyps
```

<span data-ttu-id="183ed-124">다음 순서도는 PowerShell 참조 콘텐츠를 만들거나 업데이트하는 프로세스를 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-124">The following flowchart outlines the process for creating or updating PowerShell reference content.</span></span>

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="PlatyPS를 사용하여 XML 기반 도움말을 만드는 워크플로":::

##  <a name="create-markdown-content-for-a-powershell-module"></a><span data-ttu-id="183ed-126">PowerShell 모듈의 Markdown 콘텐츠 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-126">Create Markdown content for a PowerShell module</span></span>

1. <span data-ttu-id="183ed-127">새 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-127">Import your new module into the session.</span></span> <span data-ttu-id="183ed-128">문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-128">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="183ed-129">다음 명령을 실행하여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-129">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="183ed-130">PlatyPS를 사용하여 모듈 페이지 및 모듈 내에 있는 모든 관련 cmdlet의 의 Markdown 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-130">Use PlatyPS to generate Markdown files for your module page and all associated cmdlets within the module.</span></span> <span data-ttu-id="183ed-131">문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-131">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   <span data-ttu-id="183ed-132">출력 폴더가 없으면 `New-MarkdownHelp`가 해당 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-132">If the output folder does not exist, `New-MarkdownHelp` creates it.</span></span> <span data-ttu-id="183ed-133">이 예제에서 `New-MarkdownHelp`는 모듈에 있는 각 cmdlet의 Markdown 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-133">In this example, `New-MarkdownHelp` creates a Markdown file for each cmdlet in the module.</span></span> <span data-ttu-id="183ed-134">또한 `<ModuleName>.md`이라는 파일에 ‘모듈 페이지’를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-134">It also creates the _module page_ in a file named `<ModuleName>.md`.</span></span> <span data-ttu-id="183ed-135">해당 모듈 페이지에는 모듈에 포함된 cmdlet 목록과 **개요** 설명의 자리 표시자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-135">This module page contains a list of the cmdlets contained in the module and placeholders for the **Synopsis** description.</span></span> <span data-ttu-id="183ed-136">모듈 페이지의 메타데이터는 모듈 매니페스트에서 가져오며 PlatyPS에서 HelpInfo XML 파일을 만드는 데 사용됩니다([아래](#creating-an-updateable-help-package) 설명된 대로).</span><span class="sxs-lookup"><span data-stu-id="183ed-136">The metadata in the module page comes from the module manifest and is used by PlatyPS to create the HelpInfo XML file (as explained [below](#creating-an-updateable-help-package)).</span></span>

   <span data-ttu-id="183ed-137">`New-MarkdownAboutHelp`는 `about_topic_name.md`라는 새 ‘정보’ 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-137">`New-MarkdownAboutHelp` creates a new _about_ file named `about_topic_name.md`.</span></span>

   <span data-ttu-id="183ed-138">자세한 내용은 [New-MarkdownHelp][] 및 [New-MarkdownAboutHelp][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-138">For more information, see [New-MarkdownHelp][] and [New-MarkdownAboutHelp][].</span></span>

### <a name="update-existing-markdown-content-when-the-module-changes"></a><span data-ttu-id="183ed-139">모듈이 변경될 때 기존 Markdown 콘텐츠 업데이트</span><span class="sxs-lookup"><span data-stu-id="183ed-139">Update existing Markdown content when the module changes</span></span>

<span data-ttu-id="183ed-140">PlatyPS는 모듈의 기존 Markdown 파일도 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-140">PlatyPS can also update existing Markdown files for a module.</span></span> <span data-ttu-id="183ed-141">해당 단계를 사용하여 새 cmdlet, 새 매개 변수 또는 변경된 매개 변수가 있는 기존 모듈을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-141">Use this step to update existing modules that have new cmdlets, new parameters, or parameters that have changed.</span></span>

1. <span data-ttu-id="183ed-142">새 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-142">Import your new module into the session.</span></span> <span data-ttu-id="183ed-143">문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-143">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="183ed-144">다음 명령을 실행하여 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-144">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="183ed-145">PlatyPS를 사용하여 모듈 방문 페이지 및 모듈 내 모든 관련 cmdlet의 Markdown 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-145">Use PlatyPS to update Markdown files for your module landing page and all associated cmdlets within the module.</span></span> <span data-ttu-id="183ed-146">문서화해야 하는 각 모듈에 대해 해당 단계를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-146">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   <span data-ttu-id="183ed-147">`Update-MarkdownHelpModule`은 지정된 폴더에서 cmdlet 및 모듈 Markdown 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-147">`Update-MarkdownHelpModule` updates the cmdlet and module Markdown files in the specified folder.</span></span>
   <span data-ttu-id="183ed-148">`about_*.md` 파일은 업데이트하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-148">It does not update the `about_*.md` files.</span></span> <span data-ttu-id="183ed-149">모듈 파일(`ModuleName.md`)은 cmdlet 파일에 추가된 새 **개요** 텍스트를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-149">The module file (`ModuleName.md`) receives any new **Synopsis** text that has been added to the cmdlet files.</span></span> <span data-ttu-id="183ed-150">cmdlet 파일의 업데이트에는 다음 변경 내용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-150">Updates to cmdlet files include the following change:</span></span>

   - <span data-ttu-id="183ed-151">새 매개 변수 세트</span><span class="sxs-lookup"><span data-stu-id="183ed-151">New parameter sets</span></span>
   - <span data-ttu-id="183ed-152">새 매개 변수</span><span class="sxs-lookup"><span data-stu-id="183ed-152">New parameters</span></span>
   - <span data-ttu-id="183ed-153">업데이트된 매개 변수 메타데이터</span><span class="sxs-lookup"><span data-stu-id="183ed-153">Updated parameter metadata</span></span>
   - <span data-ttu-id="183ed-154">업데이트된 입력 및 출력 형식 정보</span><span class="sxs-lookup"><span data-stu-id="183ed-154">Updated input and output type information</span></span>

   <span data-ttu-id="183ed-155">자세한 내용은 [Update-MarkdownHelpModule][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-155">For more information, see [Update-MarkdownHelpModule][].</span></span>

## <a name="edit-the-new-or-updated-markdown-files"></a><span data-ttu-id="183ed-156">새로운 또는 업데이트된 Markdown 파일 편집</span><span class="sxs-lookup"><span data-stu-id="183ed-156">Edit the new or updated Markdown files</span></span>

<span data-ttu-id="183ed-157">PlatyPS는 매개 변수 세트 및 개별 매개 변수의 구문을 문서화합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-157">PlatyPS documents the syntax of the parameter sets and the individual parameters.</span></span> <span data-ttu-id="183ed-158">설명을 만들거나 예제를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-158">It can't create descriptions or provide examples.</span></span> <span data-ttu-id="183ed-159">콘텐츠가 필요한 특정 영역은 중괄호에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-159">The specific areas where content is needed are contained in curly braces.</span></span> <span data-ttu-id="183ed-160">`{{ Fill in the Description }}`</span><span class="sxs-lookup"><span data-stu-id="183ed-160">For example: `{{ Fill in the Description }}`</span></span>

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="VS Code의 자리 표시자를 보여 주는 Markdown 템플릿":::

<span data-ttu-id="183ed-162">개요, cmdlet 설명, 각 매개 변수 설명 및 하나 이상의 예제를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-162">You need to add a synopsis, a description of the cmdlet, descriptions for each parameter, and at least one example.</span></span>

<span data-ttu-id="183ed-163">PowerShell 콘텐츠를 작성하는 방법에 관한 자세한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-163">For detailed information about writing PowerShell content, see the following articles:</span></span>

- [<span data-ttu-id="183ed-164">PowerShell 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="183ed-164">PowerShell style guide</span></span>](/powershell/scripting/community/contributing/powershell-style-guide)
- [<span data-ttu-id="183ed-165">참조 문서 편집</span><span class="sxs-lookup"><span data-stu-id="183ed-165">Editing reference articles</span></span>](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> <span data-ttu-id="183ed-166">PlatyPS에는 cmdlet 참조에 사용되는 특정 스키마가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-166">PlatyPS has a specific schema that is uses for cmdlet reference.</span></span> <span data-ttu-id="183ed-167">해당 스키마는 문서의 특정 섹션에서 특정 Markdown 블록만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-167">That schema only allows certain Markdown blocks in specific sections of the document.</span></span> <span data-ttu-id="183ed-168">콘텐츠를 잘못된 위치에 배치하면 PlatyPS 빌드 단계가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-168">If you put content in the wrong location, the PlatyPS build step fails.</span></span> <span data-ttu-id="183ed-169">자세한 내용은 PlatyPS 리포지토리에서 [스키마][] 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-169">For more information, see the [schema][] documentation in the PlatyPS repository.</span></span> <span data-ttu-id="183ed-170">잘 구성된(Well-Formed) cmdlet 참조의 전체 예제는 [Get-Item][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-170">For a complete example of well-formed cmdlet reference, see [Get-Item][].</span></span>

<span data-ttu-id="183ed-171">각 cmdlet에 필요한 콘텐츠를 제공한 후에는 모듈 방문 페이지를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-171">After providing the required content for each of your cmdlets, you need to make sure that you update the module landing page.</span></span> <span data-ttu-id="183ed-172">`<module-name>.md` 파일의 YAML 메타데이터에서 모듈에 올바른 `Module Guid` 및 `Download Help Link` 값이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-172">Verify your module has the correct `Module Guid` and `Download Help Link` values in the YAML metadata of the `<module-name>.md` file.</span></span> <span data-ttu-id="183ed-173">누락된 메타데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-173">Add any missing metadata.</span></span>

<span data-ttu-id="183ed-174">또한 일부 cmdlet에는 **개요**(‘간단한 설명’)가 없을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-174">Also, you may notice that some cmdlets may be missing a **Synopsis** (_short description_).</span></span> <span data-ttu-id="183ed-175">다음 명령은 **개요** 설명 텍스트를 사용하여 모듈 방문 페이지를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-175">The following command updates the module landing page with your **Synopsis** description text.</span></span> <span data-ttu-id="183ed-176">모듈 방문 페이지를 열어 설명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-176">Open the module landing page to verify the descriptions.</span></span>

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

<span data-ttu-id="183ed-177">모든 콘텐츠를 입력했으므로 PowerShell 콘솔에서 `Get-Help`를 통해 표시되는 MAML 도움말 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-177">Now that you have entered all the content, you can create the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

## <a name="create-the-external-help-files"></a><span data-ttu-id="183ed-178">외부 도움말 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-178">Create the external help files</span></span>

<span data-ttu-id="183ed-179">해당 단계에서는 PowerShell 콘솔에서 `Get-Help`를 통해 표시되는 MAML 도움말 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-179">This step creates the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

<span data-ttu-id="183ed-180">MAML 파일을 빌드하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-180">To build the MAML files, run the following command:</span></span>

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

<span data-ttu-id="183ed-181">`New-ExternalHelp`는 모든 cmdlet Markdown 파일을 하나 이상의 MAML 파일로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-181">`New-ExternalHelp` converts all of the cmdlet Markdown files into one (or more) MAML files.</span></span> <span data-ttu-id="183ed-182">정보 파일은 `about_topic_name.help.txt` 이름 형식의 일반 텍스트 파일로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-182">About files are converted to plain-text files with the following name format: `about_topic_name.help.txt`.</span></span>
<span data-ttu-id="183ed-183">Markdown 콘텐츠는 PlatyPS 스키마의 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-183">The Markdown content must meet the requirement of the PlatyPS schema.</span></span> <span data-ttu-id="183ed-184">콘텐츠가 스키마를 따르지 않으면 `New-ExternalHelp`가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-184">`New-ExternalHelp` will exits with errors when the content does not follow the schema.</span></span> <span data-ttu-id="183ed-185">스키마 위반을 해결하려면 파일을 편집해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-185">You must edit the files to fix the schema violations.</span></span>

> [!CAUTION]
> <span data-ttu-id="183ed-186">PlatyPS는 `about_*.md` 파일을 일반 텍스트로 변환하는 작업을 제대로 수행하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-186">PlatyPS does a poor job converting the `about_*.md` files to plain text.</span></span> <span data-ttu-id="183ed-187">적합한 결과를 얻으려면 매우 간단한 Markdown을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-187">You must use very simple Markdown to get acceptable results.</span></span> <span data-ttu-id="183ed-188">PlatyPS가 변환하도록 허용하지 않고 일반 텍스트 `about_topic_name.help.txt` 형식으로 파일을 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-188">You may want to maintain the files in plain-text `about_topic_name.help.txt` format, rather than allowing PlatyPS to convert them.</span></span>

<span data-ttu-id="183ed-189">해당 단계가 완료되면 대상 출력 폴더에 `*-help.xml` 및 `about_*.help.txt` 파일이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-189">Once this step is complete, you will see `*-help.xml` and `about_*.help.txt` files in the target output folder.</span></span>

<span data-ttu-id="183ed-190">자세한 내용은 [New-ExternalHelp][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-190">For more information, see [New-ExternalHelp][]</span></span>

### <a name="test-the-compiled-help-files"></a><span data-ttu-id="183ed-191">컴파일된 도움말 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="183ed-191">Test the compiled help files</span></span>

<span data-ttu-id="183ed-192">[Get-HelpPreview][] cmdlet을 사용하여 콘텐츠를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-192">You can verify the content with the [Get-HelpPreview][] cmdlet:</span></span>

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

<span data-ttu-id="183ed-193">cmdlet은 컴파일된 MAML 파일을 읽고 `Get-Help`에서 받은 동일한 형식으로 콘텐츠를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-193">The cmdlet reads the compiled MAML file and outputs the content in the same format you would receive from `Get-Help`.</span></span> <span data-ttu-id="183ed-194">이렇게 하면 결과를 검사하여 Markdown 파일이 제대로 컴파일되었는지 확인하고 원하는 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-194">This allows you to inspect the results to verify that the Markdown files compiled correctly and produce the desired results.</span></span> <span data-ttu-id="183ed-195">오류가 발견되면 Markdown 파일을 다시 컴파일하고 MAML를 다시 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-195">If you find an error, re-edit the Markdown files and recompile the MAML.</span></span>

<span data-ttu-id="183ed-196">이제 도움말 파일을 게시할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-196">Now you are ready to publish your help files.</span></span>

## <a name="publishing-your-help"></a><span data-ttu-id="183ed-197">도움말 게시</span><span class="sxs-lookup"><span data-stu-id="183ed-197">Publishing your help</span></span>

<span data-ttu-id="183ed-198">이제 Markdown 파일을 PowerShell 도움말 파일로 컴파일했으므로 사용자가 파일을 사용할 수 있도록 설정할 준비가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-198">Now that you have compiled the Markdown files into PowerShell help files, you are ready to make the files available to users.</span></span> <span data-ttu-id="183ed-199">PowerShell 콘솔에서 도움말을 제공하는 두 가지 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-199">There are two options for providing help in the PowerShell console.</span></span>

- <span data-ttu-id="183ed-200">모듈을 사용하여 도움말 파일 패키지</span><span class="sxs-lookup"><span data-stu-id="183ed-200">Package the help files with the module</span></span>
- <span data-ttu-id="183ed-201">`Update-Help` cmdlet을 사용하여 사용자가 설치하는 업데이트 가능한 도움말 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-201">Create an updateable help package that users install with the `Update-Help` cmdlet</span></span>

### <a name="packaging-help-with-the-module"></a><span data-ttu-id="183ed-202">모듈의 도움말 패키지</span><span class="sxs-lookup"><span data-stu-id="183ed-202">Packaging help with the module</span></span>

<span data-ttu-id="183ed-203">도움말 파일은 모듈과 함께 패키지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-203">The help files can be packaged with your module.</span></span> <span data-ttu-id="183ed-204">폴더 구조에 관한 자세한 내용은 [모듈의 도움말 작성][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-204">See [Writing Help for Modules][] for details of the folder structure.</span></span> <span data-ttu-id="183ed-205">모듈 매니페스트의 **FileList** 키 값에 도움말 파일 목록을 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-205">You should include the list of Help files in the value of the **FileList** key in the module manifest.</span></span>

### <a name="creating-an-updateable-help-package"></a><span data-ttu-id="183ed-206">업데이트 가능한 도움말 패키지 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-206">Creating an updateable help package</span></span>

<span data-ttu-id="183ed-207">개략적으로 업데이트 가능한 도움말을 만드는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-207">At a high level, the steps to create updateable help include:</span></span>

1. <span data-ttu-id="183ed-208">도움말 파일을 호스트할 인터넷 사이트 찾기</span><span class="sxs-lookup"><span data-stu-id="183ed-208">Find an internet site to host your help files</span></span>
1. <span data-ttu-id="183ed-209">모듈 매니페스트에 **HelpInfoURI** 키 추가</span><span class="sxs-lookup"><span data-stu-id="183ed-209">Add a **HelpInfoURI** key to your module manifest</span></span>
1. <span data-ttu-id="183ed-210">HelpInfo XML 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-210">Create a HelpInfo XML file</span></span>
1. <span data-ttu-id="183ed-211">CAB 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="183ed-211">Create CAB files</span></span>
1. <span data-ttu-id="183ed-212">파일 업로드</span><span class="sxs-lookup"><span data-stu-id="183ed-212">Upload your files</span></span>

<span data-ttu-id="183ed-213">자세한 내용은 [업데이트 가능한 도움말 지원: 단계별][step-by-step]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-213">For more information, see [Supporting Updateable Help: Step-by-step][step-by-step].</span></span>

<span data-ttu-id="183ed-214">PlatyPS는 해당 단계 중 일부를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-214">PlatyPS assists you with  some of these steps.</span></span>

<span data-ttu-id="183ed-215">**HelpInfoURI**는 인터넷에서 도움말 파일이 호스트되는 위치를 가리키는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-215">The **HelpInfoURI** is a URL that points to location where your help files are hosted on the internet.</span></span> <span data-ttu-id="183ed-216">해당 값은 모듈 매니페스트에서 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-216">This value is configured in the module manifest.</span></span> <span data-ttu-id="183ed-217">`Update-Help`는 모듈 매니페스트를 읽어서 해당 URL을 가져오고 업데이트 가능한 도움말 콘텐츠를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-217">`Update-Help` reads the module manifest to get this URL and download the updateable help content.</span></span> <span data-ttu-id="183ed-218">해당 URL은 개별 파일이 아닌 폴더 위치만 가리켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-218">This URL should only point to the folder location and not to individual files.</span></span> <span data-ttu-id="183ed-219">`Update-Help`는 모듈 매니페스트 및 HelpInfo XML 파일의 기타 정보에 따라 다운로드할 파일 이름을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-219">`Update-Help` constructs the filenames to download based on other information from the module manifest and the HelpInfo XML file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="183ed-220">**HelpInfoURI**는 슬래시 문자(`/`)로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-220">The **HelpInfoURI** must end with a forward-slash character (`/`).</span></span> <span data-ttu-id="183ed-221">해당 문자가 없으면 `Update-Help`는 콘텐츠를 다운로드할 올바른 파일 경로를 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-221">Without that character, `Update-Help` cannot construct the correct file paths to download the content.</span></span> <span data-ttu-id="183ed-222">또한 대부분의 HTTP 기반 파일 서비스는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-222">Also, most HTTP-based file services are case-sensitive.</span></span> <span data-ttu-id="183ed-223">HelpInfo XML 파일의 모듈 메타데이터에는 적절한 대/소문자가 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-223">It is important that the module metadata in the HelpInfo XML file contains the proper letter case.</span></span>

<span data-ttu-id="183ed-224">`New-ExternalHelp` cmdlet은 출력 폴더에 HelpInfo XML 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-224">The `New-ExternalHelp` cmdlet creates the HelpInfo XML file in the output folder.</span></span> <span data-ttu-id="183ed-225">HelpInfo XML 파일은 모듈 Markdown 파일(`ModuleName.md`)에 포함된 YAML 메타데이터를 사용하여 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-225">The HelpInfo XML file is built using YAML metadata contained in the module Markdown files (`ModuleName.md`).</span></span>

<span data-ttu-id="183ed-226">`New-ExternalHelpCab` cmdlet은 컴파일한 MAML 및 `about_*.help.txt` 파일을 포함하는 ZIP 및 CAB 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-226">The `New-ExternalHelpCab` cmdlet creates ZIP and CAB files containing the MAML and `about_*.help.txt` files you compiled.</span></span> <span data-ttu-id="183ed-227">CAB 파일은 모든 버전의 PowerShell과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-227">CAB files are compatible with all versions of PowerShell.</span></span>
<span data-ttu-id="183ed-228">PowerShell 6 이상은 ZIP 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-228">PowerShell 6 and higher can use ZIP files.</span></span>

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

<span data-ttu-id="183ed-229">ZIP 및 CAB 파일을 만든 후 ZIP, CAB 및 HelpInfo XML 파일을 HTTP 파일 서버에 업로드합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-229">After creating the ZIP and CAB files, upload the ZIP, CAB, and HelpInfo XML files to your HTTP file server.</span></span> <span data-ttu-id="183ed-230">**HelpInfoURI**에 지정된 위치에 파일을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-230">Put the files in the location indicated by the **HelpInfoURI**.</span></span>

<span data-ttu-id="183ed-231">자세한 내용은 [New-ExternalHelpCab][]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-231">For more information, see [New-ExternalHelpCab][].</span></span>

### <a name="other-publishing-options"></a><span data-ttu-id="183ed-232">기타 게시 옵션</span><span class="sxs-lookup"><span data-stu-id="183ed-232">Other publishing options</span></span>

<span data-ttu-id="183ed-233">Markdown은 게시를 위해 다른 형식으로 쉽게 변환할 수 있는 다양한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-233">Markdown is a versatile format that is easy to transform to other formats for publishing.</span></span> <span data-ttu-id="183ed-234">[Pandoc][] 같은 도구를 사용하여 Markdown 도움말 파일을 일반 텍스트, HTML, PDF 및 Office 문서 형식을 포함한 다양한 문서 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-234">Using a tool like [Pandoc][], you can convert your Markdown help files to many different document formats, including plain text, HTML, PDF, and Office document formats.</span></span>

<span data-ttu-id="183ed-235">또한 PowerShell 6 이상에서 cmdlet [ConvertFrom-Markdown][] 및 [Show-Markdown][]을 사용하여 Markdown를 HTML로 변환하거나 PowerShell 콘솔에서 다채로운 표시를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-235">Also, the cmdlets [ConvertFrom-Markdown][] and [Show-Markdown][] in PowerShell 6 and higher can be used to convert Markdown to HTML or create a colorful display in the PowerShell console.</span></span>

## <a name="known-issues"></a><span data-ttu-id="183ed-236">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="183ed-236">Known issues</span></span>

<span data-ttu-id="183ed-237">PlatyPS는 만들고 컴파일하는 Markdown 파일 구조의 [스키마][]에 매우 민감합니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-237">PlatyPS is very sensitive to the [schema][] for the structure of the Markdown files it creates and compiles.</span></span> <span data-ttu-id="183ed-238">해당 스키마를 위반하는 매우 쓰기 쉬운 유효한 Markdown입니다.</span><span class="sxs-lookup"><span data-stu-id="183ed-238">It is very easy write valid Markdown that violates this schema.</span></span> <span data-ttu-id="183ed-239">자세한 내용은 [PowerShell 스타일 가이드][] 및 [참조 문서 편집][]을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="183ed-239">For more information, consult the [PowerShell style guide][] and [Editing reference articles][].</span></span>

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell 스타일 가이드]: /powershell/scripting/community/contributing/powershell-style-guide
[PowerShell style guide]: /powershell/scripting/community/contributing/powershell-style-guide
[참조 문서 편집]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Editing reference articles]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[모듈에 관한 도움말 작성]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[Writing Help for Modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
