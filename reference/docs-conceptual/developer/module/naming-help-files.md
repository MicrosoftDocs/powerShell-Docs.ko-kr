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
ms.openlocfilehash: f65a90023df88fceafae1d1875ddf46b9088e2b8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367012"
---
# <a name="naming-help-files"></a><span data-ttu-id="15aad-102">도움말 파일 이름 지정</span><span class="sxs-lookup"><span data-stu-id="15aad-102">Naming Help Files</span></span>

<span data-ttu-id="15aad-103">이 항목에서는 [get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있도록 XML 기반 도움말 파일의 이름을 지정할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="15aad-104">이름 요구 사항은 각 명령 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-104">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="15aad-105">Cmdlet 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="15aad-105">Cmdlet Help Files</span></span>

<span data-ttu-id="15aad-106">Cmdlet에 대 한 C# 도움말 파일은 cmdlet이 정의 된 어셈블리의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-106">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="15aad-107">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-107">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="15aad-108">어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-108">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="15aad-109">예를 들어, [Get WinEvent; PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet은 Microsoft. PowerShell .dll 어셈블리에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-109">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="15aad-110">@No__t cmdlet은 모듈 디렉터리의 dll-help 파일에 있는 `Get-WinEvent` cmdlet에 대 한 도움말 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-110">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="15aad-111">공급자 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="15aad-111">Provider Help files</span></span>

<span data-ttu-id="15aad-112">Windows PowerShell 공급자에 대 한 도움말 파일은 공급자가 정의 된 어셈블리의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-112">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="15aad-113">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-113">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="15aad-114">어셈블리가 중첩 모듈인 경우에도 어셈블리 이름 형식이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-114">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="15aad-115">예를 들어 인증서 공급자는 Microsoft. PowerShell. .dll 어셈블리에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-115">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="15aad-116">@No__t-0 cmdlet은 모듈 디렉터리의 dll-help 파일 에서만 인증서 공급자에 대 한 도움말 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-116">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="15aad-117">함수 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="15aad-117">Function Help Files</span></span>

<span data-ttu-id="15aad-118">함수는 [주석 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 을 사용 하 여 문서화 하거나 XML 도움말 파일에 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-118">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="15aad-119">함수가 XML 파일에 문서화 된 경우 함수는 함수를 XML 파일에 연결 하는 `.ExternalHelp` comment 키워드를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-119">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="15aad-120">그렇지 않으면 `Get-Help` cmdlet이 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-120">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="15aad-121">함수 도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-121">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="15aad-122">그러나 함수가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-122">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="15aad-123">예를 들어 다음 함수는 MyModule 파일에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-123">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="15aad-124">CIM 명령 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="15aad-124">CIM Command Help Files</span></span>

<span data-ttu-id="15aad-125">Cim 명령의 도움말 파일은 CIM 명령이 정의 된 CDXML 파일의 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-125">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="15aad-126">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-126">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="15aad-127">CIM 명령은 모듈에 중첩 모듈로 포함 될 수 있는 CDXML 파일에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-127">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="15aad-128">CIM 명령을 세션으로 함수로 가져오는 경우 Windows PowerShell은 함수를 CIM 명령이 정의 된 CDXML 파일에 대해 이름이 지정 된 XML 도움말 파일에 연결 하는 함수 정의에 `.ExternalHelp` comment 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-128">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="15aad-129">워크플로 도움말 파일 스크립팅</span><span class="sxs-lookup"><span data-stu-id="15aad-129">Script Workflow Help Files</span></span>

<span data-ttu-id="15aad-130">모듈에 포함 된 스크립트 워크플로는 XML 기반 도움말 파일로 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-130">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="15aad-131">도움말 파일의 이름에 대 한 기술 요구 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-131">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="15aad-132">그러나 스크립트 워크플로가 정의 된 스크립트 모듈에 대 한 도움말 파일의 이름을 지정 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-132">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="15aad-133">예:</span><span class="sxs-lookup"><span data-stu-id="15aad-133">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="15aad-134">다른 스크립팅된 명령과 달리 스크립트 워크플로에는 `.ExternalHelp` 주석 키워드가 필요 하지 않으므로 도움말 파일과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-134">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="15aad-135">대신 Windows PowerShell은 모듈 디렉터리의 UI 문화권 관련 하위 디렉터리에서 XML 기반 도움말 파일을 검색 하 고 모든 파일의 스크립트 워크플로에 대 한 도움말을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-135">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="15aad-136">`.ExternalHelp` 주석 키워드는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-136">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="15aad-137">@No__t-0 comment 키워드는 무시 되기 때문에 `Get-Help` cmdlet은 모듈에 포함 된 경우에만 스크립트 워크플로에 대 한 도움말을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15aad-137">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>