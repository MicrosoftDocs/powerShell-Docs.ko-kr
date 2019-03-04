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
ms.openlocfilehash: 06281a1260dbdc120867fce89e6d5c8dd0754b87
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856669"
---
# <a name="naming-help-files"></a><span data-ttu-id="ab044-102">도움말 파일 이름 지정</span><span class="sxs-lookup"><span data-stu-id="ab044-102">Naming Help Files</span></span>

<span data-ttu-id="ab044-103">이 항목에서는 XML 기반 도움말 파일을 이름을 지정 하는 방법에 설명 하는 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-103">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ab044-104">이름 요구 사항 명령 유형 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-104">The name requirements differ for each command type.</span></span>
<span data-ttu-id="ab044-105">이 항목에서는 XML 기반 도움말 파일을 이름을 지정 하는 방법에 설명 하는 [Get-help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-105">This topic explains how to name an XML-based help file so that the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet can find it.</span></span> <span data-ttu-id="ab044-106">이름 요구 사항 명령 유형 마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-106">The name requirements differ for each command type.</span></span>

## <a name="cmdlet-help-files"></a><span data-ttu-id="ab044-107">Cmdlet 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="ab044-107">Cmdlet Help Files</span></span>

<span data-ttu-id="ab044-108">에 대 한 도움말 파일을 C# cmdlet은 cmdlet가 정의 된 어셈블리 이름을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-108">The help file for a C# cmdlet must be named for the assembly in which the cmdlet is defined.</span></span> <span data-ttu-id="ab044-109">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-109">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ab044-110">어셈블리 이름 형식은 중첩된 모듈 어셈블리가 있는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-110">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ab044-111">예를 들어를 [Get-winevent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet Microsoft.PowerShell.Diagnostics.dll 어셈블리에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-111">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ab044-112">합니다 `Get-Help` cmdlet에 대 한 도움말 항목을 찾습니다는 `Get-WinEvent` cmdlet 모듈 디렉터리에는 Microsoft.PowerShell.Diagnostics.dll help.xml 파일에만 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-112">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>
<span data-ttu-id="ab044-113">예를 들어를 [Get-winevent; PSITPro5_Diagnostic; ](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet Microsoft.PowerShell.Diagnostics.dll 어셈블리에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-113">For example, the [Get-WinEvent;PSITPro5_Diagnostic;](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent) cmdlet is defined in the Microsoft.PowerShell.Diagnostics.dll assembly.</span></span> <span data-ttu-id="ab044-114">합니다 `Get-Help` cmdlet에 대 한 도움말 항목을 찾습니다는 `Get-WinEvent` cmdlet 모듈 디렉터리에는 Microsoft.PowerShell.Diagnostics.dll help.xml 파일에만 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-114">The `Get-Help` cmdlet looks for a help topic for the `Get-WinEvent` cmdlet only in the Microsoft.PowerShell.Diagnostics.dll-help.xml file in the module directory.</span></span>

## <a name="provider-help-files"></a><span data-ttu-id="ab044-115">공급자 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="ab044-115">Provider Help files</span></span>

<span data-ttu-id="ab044-116">공급자가 정의 된 어셈블리에 대 한 Windows PowerShell 공급자에 대 한 도움말 파일을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-116">The help file for a Windows PowerShell provider must be named for the assembly in which the provider is defined.</span></span> <span data-ttu-id="ab044-117">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-117">Use the following file name format:</span></span>

```
<AssemblyName>.dll-help.xml
```

<span data-ttu-id="ab044-118">어셈블리 이름 형식은 중첩된 모듈 어셈블리가 있는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-118">The assembly name format is required even when the assembly is a nested module.</span></span>

<span data-ttu-id="ab044-119">예를 들어 인증서 공급자는 Microsoft.PowerShell.Security.dll 어셈블리에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-119">For example, the Certificate provider is defined in the Microsoft.PowerShell.Security.dll assembly.</span></span> <span data-ttu-id="ab044-120">`Get-Help` 모듈 디렉터리에는 Microsoft.PowerShell.Security.dll help.xml 파일에만 인증서 공급자에 대 한 cmdlet 도움말 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-120">The `Get-Help` cmdlet looks for a help topic for the Certificate provider only in the Microsoft.PowerShell.Security.dll-help.xml file in the module directory.</span></span>

## <a name="function-help-files"></a><span data-ttu-id="ab044-121">함수 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="ab044-121">Function Help Files</span></span>

<span data-ttu-id="ab044-122">함수를 사용 하 여 문서화할 수 [설명 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 또는 XML 도움말 파일에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-122">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ab044-123">함수는 XML 파일에 문서화 하는 경우 함수가 있어야는 `.ExternalHelp` 키워드 XML 파일을 사용 하 여 함수를 연결 하는 주석 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-123">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ab044-124">그렇지 않은 경우는 `Get-Help` cmdlet 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-124">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>
<span data-ttu-id="ab044-125">함수를 사용 하 여 문서화할 수 [설명 기반 도움말](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) 또는 XML 도움말 파일에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-125">Functions can be documented by using [comment-based help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help) or documented in an XML help file.</span></span> <span data-ttu-id="ab044-126">함수는 XML 파일에 문서화 하는 경우 함수가 있어야는 `.ExternalHelp` 키워드 XML 파일을 사용 하 여 함수를 연결 하는 주석 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-126">When the function is documented in an XML file, the function must have an `.ExternalHelp` comment keyword that associates the function with the XML file.</span></span> <span data-ttu-id="ab044-127">그렇지 않은 경우는 `Get-Help` cmdlet 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-127">Otherwise, the `Get-Help` cmdlet cannot find the help file.</span></span>

<span data-ttu-id="ab044-128">요구 사항은 없습니다 기술 이름에 대 한 도움말 파일을 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-128">There are no technical requirements for the name of a function help file.</span></span> <span data-ttu-id="ab044-129">그러나 함수 정의 되는 스크립트 모듈에 대 한 도움말 파일 이름을 지정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-129">However, a best practice is to name the help file for the script module in which the function is defined.</span></span> <span data-ttu-id="ab044-130">예를 들어, 다음 함수는 MyModule.psm1 파일에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-130">For example, the following function is defined in the MyModule.psm1 file.</span></span>

```csharp
#.ExternalHelp MyModule.psm1-help.xml
function Test-Function { ... }
```

## <a name="cim-command-help-files"></a><span data-ttu-id="ab044-131">CIM 명령 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="ab044-131">CIM Command Help Files</span></span>

<span data-ttu-id="ab044-132">CIM 명령 정의 되어 있는 CDXML 파일에 대 한 CIM 명령에 대 한 도움말 파일을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-132">The help file for a CIM command must be named for the CDXML file in which the CIM command is defined.</span></span> <span data-ttu-id="ab044-133">다음 파일 이름 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-133">Use the following file name format:</span></span>

```
<FileName>.cdxml-help.xml
```

<span data-ttu-id="ab044-134">CIM 명령은 중첩된 모듈을 모듈에 포함 될 수 있는 CDXML 파일에서 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-134">CIM commands are defined in CDXML files that can be included in modules as nested modules.</span></span> <span data-ttu-id="ab044-135">CIM 명령의 함수로 세션으로 가져오면 Windows PowerShell 추가 `.ExternalHelp` 키워드를 XML 도움말을 사용 하 여 함수를 연결 하는 함수 정의를 파일 주석 CIM 명령 정의 되어 있는 CDXML 파일 이름으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-135">When the CIM command is imported into the session as a function, Windows PowerShell adds an `.ExternalHelp` comment keyword to the function definition that associates the function with an XML help file that is named for the CDXML file in which the CIM command is defined.</span></span>

## <a name="script-workflow-help-files"></a><span data-ttu-id="ab044-136">스크립트 워크플로에 도움말 파일</span><span class="sxs-lookup"><span data-stu-id="ab044-136">Script Workflow Help Files</span></span>

<span data-ttu-id="ab044-137">스크립트 워크플로 모듈에 포함 된 XML 기반 도움말 파일에 문서화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-137">Script workflows that are included in modules can be documented in XML-based help files.</span></span> <span data-ttu-id="ab044-138">요구 사항은 없습니다 기술 이름에 대 한 도움말 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-138">There are no technical requirements for the name of the help file.</span></span> <span data-ttu-id="ab044-139">그러나 스크립트 워크플로에 정의 되는 스크립트 모듈에 대 한 도움말 파일 이름을 지정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-139">However, a best practice is to name the help file for the script module in which the script workflow is defined.</span></span> <span data-ttu-id="ab044-140">예:</span><span class="sxs-lookup"><span data-stu-id="ab044-140">For example:</span></span>

```
<ScriptModule>.psm1-help.xml
```

<span data-ttu-id="ab044-141">다른 스크립트 명령은 달리 스크립트 워크플로에 필요 하지 않습니다는 `.ExternalHelp` 도움말 파일에 연결할 키워드를 주석 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-141">Unlike other scripted commands, script workflows do not require an `.ExternalHelp` comment keyword to associate them with a help file.</span></span> <span data-ttu-id="ab044-142">대신 Windows PowerShell XML 기반 도움말 파일에 대 한 모듈 디렉터리의 UI Culture 별 하위 디렉터리를 검색 하 고 모든 파일의 스크립트 워크플로에 대 한 도움말을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-142">Instead, Windows PowerShell searches the UI-Culture-specific subdirectories of the module directory for XML-based help files and looks for help for the script workflow in all the files.</span></span> <span data-ttu-id="ab044-143">`.ExternalHelp` 주석 키워드는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-143">`.ExternalHelp` comment keyword are ignored.</span></span>

<span data-ttu-id="ab044-144">때문에 합니다 `.ExternalHelp` 주석 키워드가 무시 되는 `Get-Help` cmdlet 도움말을 찾을 수 스크립트 워크플로에 대 한 모듈에 포함 된 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab044-144">Because the `.ExternalHelp` comment keyword is ignored, the `Get-Help` cmdlet can find help for script workflows only when they are included in modules.</span></span>