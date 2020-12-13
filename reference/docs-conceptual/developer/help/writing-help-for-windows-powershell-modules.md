---
ms.date: 04/10/2020
ms.topic: reference
title: PowerShell 모듈에 대한 도움말 작성
description: PowerShell 모듈에 대한 도움말 작성
ms.openlocfilehash: 3bef45c0dd8a7e63bc419bb3e5a7a1783810105b
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654647"
---
# <a name="writing-help-for-powershell-modules"></a><span data-ttu-id="683b0-103">PowerShell 모듈에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="683b0-103">Writing Help for PowerShell Modules</span></span>

<span data-ttu-id="683b0-104">PowerShell 모듈에는 모듈에 대 한 도움말 항목과 cmdlet, 공급자, 함수 및 스크립트와 같은 모듈 멤버가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-104">PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="683b0-105">`Get-Help`Cmdlet은 다른 PowerShell 항목에 대 한 도움말을 표시 하는 것과 같은 형식으로 모듈 도움말 항목을 표시 하 고, 사용자 `Get-Help` 는 표준 명령을 사용 하 여 도움말 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-105">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="683b0-106">이 문서에서는 모듈 도움말 항목의 형식 및 올바른 배치에 대해 설명 하 고 모듈 도움말 콘텐츠에 대 한 지침을 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-106">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="683b0-107">모듈 도움말 형식</span><span class="sxs-lookup"><span data-stu-id="683b0-107">Types of Module Help</span></span>

<span data-ttu-id="683b0-108">모듈에는 다음과 같은 유형의 도움말이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-108">A module can include the following types of Help.</span></span>

- <span data-ttu-id="683b0-109">**Cmdlet 도움말**.</span><span class="sxs-lookup"><span data-stu-id="683b0-109">**Cmdlet Help**.</span></span> <span data-ttu-id="683b0-110">모듈의 cmdlet에 대해 설명 하는 도움말 항목은 명령 도움말 스키마를 사용 하는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-110">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="683b0-111">**공급자 도움말**.</span><span class="sxs-lookup"><span data-stu-id="683b0-111">**Provider Help**.</span></span> <span data-ttu-id="683b0-112">모듈의 공급자를 설명 하는 도움말 항목은 공급자 도움말 스키마를 사용 하는 XML 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-112">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="683b0-113">**함수 도움말**.</span><span class="sxs-lookup"><span data-stu-id="683b0-113">**Function Help**.</span></span> <span data-ttu-id="683b0-114">모듈의 함수를 설명 하는 도움말 항목은 명령 도움말 스키마를 사용 하는 XML 파일 이거나 함수 내의 주석 기반 도움말 항목 또는 스크립트 또는 스크립트 모듈 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-114">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="683b0-115">**스크립트 도움말**.</span><span class="sxs-lookup"><span data-stu-id="683b0-115">**Script Help**.</span></span> <span data-ttu-id="683b0-116">모듈의 스크립트를 설명 하는 도움말 항목은 스크립트 또는 스크립트 모듈의 명령 도움말 스키마 또는 주석 기반 도움말 항목을 사용 하는 XML 파일 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-116">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="683b0-117">**개념 ("About") 도움말을 참조** 하십시오.</span><span class="sxs-lookup"><span data-stu-id="683b0-117">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="683b0-118">개념 ("about") 도움말 항목을 사용 하 여 모듈과 해당 멤버를 설명 하 고 멤버를 함께 사용 하 여 작업을 수행할 수 있는 방법을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-118">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span>
  <span data-ttu-id="683b0-119">개념 도움말 항목은 유니코드 (UTF-8) 인코딩을 사용 하는 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-119">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="683b0-120">파일 이름에는 형식을 사용 해야 합니다 `about_<name>.help.txt` `about_MyModule.help.txt` .</span><span class="sxs-lookup"><span data-stu-id="683b0-120">The filename must use the `about_<name>.help.txt` format, such as `about_MyModule.help.txt`.</span></span> <span data-ttu-id="683b0-121">기본적으로 PowerShell에는 이러한 개념 정보 도움말 항목의 100이 포함 되어 있으며 다음 예제와 같이 형식이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-121">By default, PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```Output
  TOPIC
      about_<subject or module name>

  SHORT DESCRIPTION
      A short, one-line description of the topic contents.

  LONG DESCRIPTION
      A detailed, full description of the subject or purpose of the module.

  EXAMPLES
      Examples of how to use the module or how the subject feature works in practice.

  KEYWORDS
      Terms or titles on which you might expect your users to search for the information in this topic.

  SEE ALSO
      Text-only references for further reading. Hyperlinks cannot work in the PowerShell console.

  ```

<span data-ttu-id="683b0-122">모든 스키마 파일은 폴더에서 찾을 수 있습니다 `$PSHOME\Schemas\PSMaml` .</span><span class="sxs-lookup"><span data-stu-id="683b0-122">All of the schema files can be found in the `$PSHOME\Schemas\PSMaml` folder.</span></span>

## <a name="placement-of-module-help"></a><span data-ttu-id="683b0-123">모듈 도움말 배치</span><span class="sxs-lookup"><span data-stu-id="683b0-123">Placement of Module Help</span></span>

<span data-ttu-id="683b0-124">Cmdlet은 모듈 `Get-Help` 디렉터리의 언어별 하위 디렉터리에서 모듈 도움말 항목 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-124">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="683b0-125">예를 들어 다음 디렉터리 구조 다이어그램은 SampleModule 모듈에 대 한 도움말 항목의 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-125">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

```
<ModulePath>
         \SampleModule
               \<en-US>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml
               \<fr-FR>
                     \about_SampleModule.help.txt
                     \SampleModule.dll-help.xml
                     \SampleNestedModule.dll-help.xml

```

> [!NOTE]
> <span data-ttu-id="683b0-126">이 예에서 `<ModulePath>` 자리 표시자는 환경 변수의 경로 중 하나 (예 `PSModulePath` : `$HOME\Documents\Modules` , `$PSHOME\Modules` 또는 사용자가 지정 하는 사용자 지정 경로)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-126">In the example, the `<ModulePath>` placeholder represents one of the paths in the `PSModulePath` environment variable, such as `$HOME\Documents\Modules`, `$PSHOME\Modules`, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="683b0-127">모듈 도움말 가져오기</span><span class="sxs-lookup"><span data-stu-id="683b0-127">Getting Module Help</span></span>

<span data-ttu-id="683b0-128">사용자가 모듈을 세션으로 가져오면 해당 모듈에 대 한 도움말 항목을 모듈과 함께 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-128">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="683b0-129">모듈 매니페스트의 FileList 키 값에 도움말 항목 파일을 나열할 수 있지만 도움말 항목은 cmdlet의 영향을 받지 않습니다 `Export-ModuleMember` .</span><span class="sxs-lookup"><span data-stu-id="683b0-129">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="683b0-130">다양 한 언어로 모듈 도움말 항목을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-130">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="683b0-131">이 `Get-Help` cmdlet은 제어판의 국가 및 언어 옵션 항목에서 현재 사용자에 대해 지정 된 언어로 모듈 도움말 항목을 자동으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-131">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="683b0-132">Windows Vista 이상 버전의에서는 `Get-Help` windows에 설정 된 언어 대체 표준에 따라 모듈 디렉터리의 언어별 하위 디렉터리에서 도움말 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-132">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="683b0-133">PowerShell 3.0부터 `Get-Help` cmdlet 또는 함수에 대해 명령을 실행 하면 모듈의 자동 가져오기가 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-133">Beginning in PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="683b0-134">`Get-Help`Cmdlet은 모듈에 있는 도움말 항목의 내용을 즉시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-134">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="683b0-135">모듈에 도움말 항목이 포함 되어 있지 않고 사용자 컴퓨터에 있는 모듈의 명령에 대 한 도움말 항목이 없으면 `Get-Help` 자동 생성 된 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-135">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="683b0-136">자동 생성 된 도움말에는 명령 구문, 매개 변수 및 입력 및 출력 형식이 포함 되어 있지만 설명이 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-136">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="683b0-137">자동 생성 된 도움말에는 사용자가 cmdlet을 사용 하 여 `Update-Help` 인터넷 또는 파일 공유에서 명령에 대 한 도움말을 다운로드 하도록 지시 하는 텍스트가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-137">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the internet or a file share.</span></span> <span data-ttu-id="683b0-138">또한 cmdlet의 **online** 매개 변수를 사용 하 여 `Get-Help` 온라인 버전의 도움말 항목을 가져오는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-138">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="683b0-139">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="683b0-139">Supporting Updatable Help</span></span>

<span data-ttu-id="683b0-140">Powershell 3.0 이상 버전의 사용자는 인터넷 이나 로컬 파일 공유에서 모듈에 대해 업데이트 된 도움말 파일을 다운로드 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-140">Users of PowerShell 3.0 and later versions of PowerShell can download and install updated help files for a module from the internet or from a local file share.</span></span> <span data-ttu-id="683b0-141">`Update-Help`및 `Save-Help` cmdlet은 사용자의 관리 세부 정보를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-141">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="683b0-142">사용자가 cmdlet을 실행 한 `Update-Help` 다음 cmdlet을 사용 `Get-Help` 하 여 PowerShell 명령 프롬프트에서 모듈에 대 한 최신 도움말 파일을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-142">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the PowerShell command prompt.</span></span>
<span data-ttu-id="683b0-143">사용자는 Windows 또는 PowerShell을 다시 시작할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-143">Users do not need to restart Windows or PowerShell.</span></span>

<span data-ttu-id="683b0-144">방화벽 뒤의 사용자와 인터넷에 액세스할 수 없는 사용자는 업데이트할 수 있는 도움말도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-144">Users behind firewalls and those without internet access can use Updatable Help, as well.</span></span>
<span data-ttu-id="683b0-145">인터넷에 액세스 하는 관리자는 cmdlet을 사용 `Save-Help` 하 여 최신 도움말 파일을 다운로드 하 여 파일 공유에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-145">Administrators with internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="683b0-146">그러면 사용자가 cmdlet의 **Path** 매개 변수를 사용 `Update-Help` 하 여 파일 공유에서 최신 도움말 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-146">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="683b0-147">모듈 작성자는 모듈에 도움말 파일을 포함 하 고 업데이트할 수 있는 도움말을 사용 하 여 도움말 파일을 업데이트 하거나 모듈에서 도움말 파일을 생략 하 고 업데이트할 수 있는 도움말을 사용 하 여 설치 하 고 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-147">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="683b0-148">업데이트할 수 있는 도움말에 대 한 자세한 내용은 업데이트할 수 있는 [도움말 지원](./supporting-updatable-help.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="683b0-148">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="683b0-149">온라인 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="683b0-149">Supporting Online Help</span></span>

<span data-ttu-id="683b0-150">업데이트 된 도움말 파일을 컴퓨터에 설치 하거나 설치할 수 없는 사용자는 종종 모듈 도움말 항목의 온라인 버전을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-150">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="683b0-151">Cmdlet의 **online** 매개 변수는 `Get-Help` 기본 인터넷 브라우저에서 사용자에 대 한 온라인 버전의 cmdlet 또는 고급 함수 도움말 항목을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-151">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default internet browser.</span></span>

<span data-ttu-id="683b0-152">`Get-Help`Cmdlet은 cmdlet 또는 함수의 **HelpUri** 속성 값을 사용 하 여 도움말 항목의 온라인 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-152">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="683b0-153">PowerShell 3.0부터 사용자는 cmdlet 클래스에서 HelpUri 특성을 정의 하거나 **Cmdletbinding** 특성의 **HelpUri** 속성을 정의 하 여 사용자가 cmdlet 및 함수 도움말 항목의 온라인 버전을 찾도록 도울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-153">Beginning in PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="683b0-154">특성의 값은 cmdlet 또는 함수의 **HelpUri** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="683b0-154">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="683b0-155">자세한 내용은 [온라인 도움말 지원](./supporting-online-help.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="683b0-155">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="683b0-156">참고 항목</span><span class="sxs-lookup"><span data-stu-id="683b0-156">See Also</span></span>

[<span data-ttu-id="683b0-157">PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="683b0-157">Writing a PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="683b0-158">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="683b0-158">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="683b0-159">온라인 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="683b0-159">Supporting Online Help</span></span>](./supporting-online-help.md)
