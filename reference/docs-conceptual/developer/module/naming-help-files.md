---
title: 도움말 파일 이름 지정 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf54eac7-88c6-4108-a5f6-2f0906d1662b
caps.latest.revision: 5
ms.openlocfilehash: d13324871bac7ba21c0e042e8674c5996e5dba85
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560222"
---
# <a name="naming-help-files"></a><span data-ttu-id="abd23-102">도움말 파일 이름 지정</span><span class="sxs-lookup"><span data-stu-id="abd23-102">Naming Help Files</span></span>

<span data-ttu-id="abd23-103">이 항목에서는 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있도록 XML 기반 도움말 파일의 이름을 지정할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="abd23-104">이름 요구 사항은 각 명령 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="abd23-105">Cmdlet 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="abd23-105">Cmdlet Help Files</span></span>

<span data-ttu-id="abd23-106">C # Cmdlet에 대 한 도움말 파일은 cmdlet이 정의 된 어셈블리의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="abd23-107">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="abd23-108">어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="abd23-109">예를 들어, [Get WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet은 Microsoft. PowerShell .dll 어셈블리에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="abd23-110">`Get-Help`Cmdlet은 `Get-WinEvent` 모듈 디렉터리의 dll-help 파일 에서만 cmdlet에 대 한 도움말 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="abd23-111">공급자 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="abd23-111">Provider Help files</span></span>

<span data-ttu-id="abd23-112">Windows PowerShell 공급자에 대 한 도움말 파일은 공급자가 정의 된 어셈블리의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="abd23-113">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="abd23-114">어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="abd23-115">예를 들어 인증서 공급자는 Microsoft. PowerShell. .dll 어셈블리에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="abd23-116">이 `Get-Help` cmdlet은 모듈 디렉터리의 dll-help 파일 에서만 인증서 공급자에 대 한 도움말 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="abd23-117">함수 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="abd23-117">Function Help Files</span></span>

<span data-ttu-id="abd23-118">함수는 [주석 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 을 사용 하 여 문서화 하거나 XML 도움말 파일에 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="abd23-119">함수가 XML 파일에 설명 되어 있는 경우 함수에 `.ExternalHelp` xml 파일에 함수를 연결 하는 comment 키워드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="abd23-120">그렇지 않으면 `Get-Help` cmdlet이 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="abd23-121">함수 도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="abd23-122">그러나 함수가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="abd23-123">예를 들어 다음 함수는 MyModule 파일에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="abd23-124">CIM 명령 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="abd23-124">CIM Command Help Files</span></span>

<span data-ttu-id="abd23-125">Cim 명령의 도움말 파일은 CIM 명령이 정의 된 CDXML 파일의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="abd23-126">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="abd23-127">CIM 명령은 모듈에 중첩 모듈로 포함 될 수 있는 CDXML 파일에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="abd23-128">CIM 명령을 세션으로 함수로 가져오는 경우 Windows PowerShell은 함수 `.ExternalHelp` 를 cim 명령이 정의 된 CDXML 파일에 대해 이름이 지정 된 XML 도움말 파일에 연결 하는 함수 정의에 주석 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="abd23-129">워크플로 도움말 파일 스크립팅</span><span class="sxs-lookup"><span data-stu-id="abd23-129">Script Workflow Help Files</span></span>

<span data-ttu-id="abd23-130">모듈에 포함 된 스크립트 워크플로는 XML 기반 도움말 파일로 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="abd23-131">도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="abd23-132">그러나 스크립트 워크플로가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="abd23-133">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="abd23-134">다른 스크립팅된 명령과 달리 스크립트 워크플로에는 `.ExternalHelp` 설명 키워드를 사용 하 여 도움말 파일에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="abd23-135">대신 Windows PowerShell은 모듈 디렉터리의 UI 문화권 관련 하위 디렉터리에서 XML 기반 도움말 파일을 검색 하 고 모든 파일의 스크립트 워크플로에 대 한 도움말을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="abd23-136">`.ExternalHelp`comment 키워드는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="abd23-137">`.ExternalHelp`Comment 키워드는 무시 되므로 `Get-Help` cmdlet은 모듈에 포함 된 경우에만 스크립트 워크플로에 대 한 도움말을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd23-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>
