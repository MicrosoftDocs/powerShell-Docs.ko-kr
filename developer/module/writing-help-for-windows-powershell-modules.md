---
title: Windows PowerShell 모듈에 대 한 도움말 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2b58fa5-01bc-426c-a043-5c700d6578e9
caps.latest.revision: 16
ms.openlocfilehash: 443bf5f693d2ab161668de25a1097347826cb5c2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082037"
---
# <a name="writing-help-for-windows-powershell-modules"></a><span data-ttu-id="7f635-102">Windows PowerShell 모듈에 대한 도움말 작성</span><span class="sxs-lookup"><span data-stu-id="7f635-102">Writing Help for Windows PowerShell Modules</span></span>

<span data-ttu-id="7f635-103">Windows PowerShell 모듈 및 cmdlet, 공급자, 함수 및 스크립트와 같은 모듈 멤버를 모듈에 대 한 도움말 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-103">Windows PowerShell modules can include Help topics about the module and about the module members, such as cmdlets, providers, functions and scripts.</span></span> <span data-ttu-id="7f635-104">`Get-Help` cmdlet은 다른 Windows PowerShell 항목에 대 한 도움말을 표시 하 고 사용자가 사용할 표준 동일한 형식의 모듈 도움말 항목을 표시 `Get-Help` 명령 도움말 항목을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-104">The `Get-Help` cmdlet displays the module Help topics in the same format as it displays Help for other Windows PowerShell items, and users use standard `Get-Help` commands to get the Help topics.</span></span>

<span data-ttu-id="7f635-105">이 문서에서는 형식 및 모듈 도움말 항목의 올바른 배치를 설명 하 고 모듈 도움말 콘텐츠에 대 한 지침 제안 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-105">This document explains the format and correct placement of module Help topics, and it suggests guidelines for module Help content.</span></span>

## <a name="types-of-module-help"></a><span data-ttu-id="7f635-106">유형의 모듈 도움말</span><span class="sxs-lookup"><span data-stu-id="7f635-106">Types of Module Help</span></span>

<span data-ttu-id="7f635-107">모듈에는 다음과 같은 유형의 도움말 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-107">A module can include the following types of Help.</span></span>

- <span data-ttu-id="7f635-108">**Cmdlet 도움말**합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-108">**Cmdlet Help**.</span></span> <span data-ttu-id="7f635-109">모듈의 cmdlet을 설명 하는 도움말 항목 명령을 사용 하는 XML 파일 스키마는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-109">The Help topics that describe cmdlets in a module are XML files that use the command help schema</span></span>

- <span data-ttu-id="7f635-110">**공급자 도움말**합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-110">**Provider Help**.</span></span> <span data-ttu-id="7f635-111">모듈의 공급자를 설명 하는 도움말 항목 공급자를 사용 하는 XML 파일 스키마는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-111">The Help topics that describe providers in a module are XML files that use the provider help schema.</span></span>

- <span data-ttu-id="7f635-112">**함수 도움말**합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-112">**Function Help**.</span></span> <span data-ttu-id="7f635-113">스키마 또는 함수, 스크립트 또는 스크립트 모듈 내에서 주석 기반 도움말 항목 명령을 사용 하 여 XML 파일에서 도움말 모듈의 함수를 설명 하는 도움말 항목 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-113">The Help topics that describe functions in a module can be XML files that use the command help schema or comment-based Help topics within the function, or the script or script module</span></span>

- <span data-ttu-id="7f635-114">**도움말 스크립트**합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-114">**Script Help**.</span></span> <span data-ttu-id="7f635-115">모듈의 스크립트를 설명 하는 도움말 항목 스키마 또는 설명 기반 도움말 항목을 스크립트 또는 스크립트 모듈의 명령을 사용 하 여 XML 파일 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-115">The Help topics that describe scripts in a module can be XML files that use the command help schema or comment-based Help topics in the script or script module.</span></span>

- <span data-ttu-id="7f635-116">**개념 ("정보") 도움말**합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-116">**Conceptual ("About") Help**.</span></span> <span data-ttu-id="7f635-117">사용할 수 있습니다 ("정보") 도움말 항목에서는 개념적 모듈 및 해당 멤버를 설명 하 고 어떻게 멤버를 함께 사용할 수 있는 작업을 수행 하려면 설명.</span><span class="sxs-lookup"><span data-stu-id="7f635-117">You can use a conceptual ("about") Help topic to describe the module and its members and to explain how the members can be used together to perform tasks.</span></span> <span data-ttu-id="7f635-118">개념 도움말 항목은 유니코드 (utf-8) 인코딩을 사용 하 여 텍스트 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-118">Conceptual Help topics are text files with Unicode (UTF-8) encoding.</span></span> <span data-ttu-id="7f635-119">파일 이름을 사용 해야 합니다는 `about_<name>.help.txt` about_MyModule.help.txt 등의 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-119">The file name must use the `about_<name>.help.txt` format, such as about_MyModule.help.txt.</span></span> <span data-ttu-id="7f635-120">기본적으로 Windows PowerShell의 이러한 개념에 대 한 도움말 항목 100 개를 포함 하 고 다음 예제와 같이 형식이 지정 될 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-120">By default, Windows PowerShell includes over 100 of these conceptual About Help topics, and they are formatted like the following example.</span></span>

  ```
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
      Text-only references for further reading. Hyperlinks cannot work in the Windows PowerShell console.

  ```

## <a name="placement-of-module-help"></a><span data-ttu-id="7f635-121">모듈 도움말의 배치</span><span class="sxs-lookup"><span data-stu-id="7f635-121">Placement of Module Help</span></span>

<span data-ttu-id="7f635-122">`Get-Help` cmdlet 모듈 디렉터리의 언어별 하위 디렉터리에 모듈 도움말 항목 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-122">The `Get-Help` cmdlet looks for module Help topic files in language-specific subdirectories of the module directory.</span></span>

<span data-ttu-id="7f635-123">예를 들어 다음 디렉터리 구조 다이어그램 SampleModule 모듈에 대 한 도움말 항목의 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-123">For example, the following directory structure diagram shows the location of the Help topics for the SampleModule module.</span></span>

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
> <span data-ttu-id="7f635-124">예에서는  *\<ModulePath >* 자리 표시자 경로 중 하나를 나타내는 `PSModulePath` home\Documents\Modules $, $pshome\Modules 또는 사용자 지정 하는 사용자 지정 경로 같은 환경 변수를 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-124">In the example, the *\<ModulePath>* placeholder represents one of the paths in the `PSModulePath` environment variable, such as $home\Documents\Modules, $pshome\Modules, or a custom path that the user specifies.</span></span>

## <a name="getting-module-help"></a><span data-ttu-id="7f635-125">모듈 도움말</span><span class="sxs-lookup"><span data-stu-id="7f635-125">Getting Module Help</span></span>

<span data-ttu-id="7f635-126">사용자의 세션으로 모듈을 가져오면 해당 모듈에 대 한 도움말 항목이 모듈과 함께 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-126">When a user imports a module into a session, the Help topics for that module are imported into the session along with the module.</span></span> <span data-ttu-id="7f635-127">도움말 항목은 영향을 받지 않습니다 하지만 모듈 매니페스트에 FileList 키의 값에 도움말 항목 파일을 표시 하는 `Export-ModuleMember` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7f635-127">You can list the Help topic files in the value of the FileList key in the module manifest, but Help topics are not affected by the `Export-ModuleMember` cmdlet.</span></span>

<span data-ttu-id="7f635-128">다른 언어로 모듈 도움말 항목을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-128">You can provide module Help topics in different languages.</span></span> <span data-ttu-id="7f635-129">`Get-Help` cmdlet 국가 및 언어 옵션 제어판 항목에 현재 사용자에 대해 지정 된 언어로 모듈 도움말 항목을 자동으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-129">The `Get-Help` cmdlet automatically displays module Help topics in the language that is specified for the current user in the Regional and Language Options item in Control Panel.</span></span> <span data-ttu-id="7f635-130">Windows Vista 및 이후 버전의 Windows `Get-Help` Windows에 대해 설정할 언어 대체 (fallback) 표준에 따라 모듈 디렉터리의 언어별 하위 디렉터리에서 도움말 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-130">In Windows Vista and later versions of Windows, `Get-Help` searches for the Help topics in language-specific subdirectories of the module directory in accordance with the language fallback standards established for Windows.</span></span>

<span data-ttu-id="7f635-131">실행 되는 Windows PowerShell 3.0부터는 `Get-Help` cmdlet 또는 함수에 대 한 명령 모듈 자동 가져오기를 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-131">Beginning in Windows PowerShell 3.0, running a `Get-Help` command for a cmdlet or function triggers automatic importing of the module.</span></span> <span data-ttu-id="7f635-132">`Get-Help` cmdlet 도움말 항목의 내용을 모듈에 즉시 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-132">The `Get-Help` cmdlet immediately displays the contents of the help topics in the module.</span></span>

<span data-ttu-id="7f635-133">모듈에 도움말 항목이 포함 되지 않으며 사용자의 컴퓨터에서 모듈의 명령에 대 한 도움말 항목이 있습니다 경우 `Get-Help` 자동으로 생성 된 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-133">If the module does not contain help topics and there are no help topics for the commands in the module on the user's computer, `Get-Help` displays auto-generated help.</span></span> <span data-ttu-id="7f635-134">자동 생성 된 도움말 명령 구문, 매개 변수 및 입력 및 출력 유형, 포함 되지만 모든 설명을 포함 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-134">The auto-generated help includes the command syntax, parameters, and input and output types, but does not include any descriptions.</span></span> <span data-ttu-id="7f635-135">사용자가 사용 하도록 지시 하는 텍스트를 포함 하는 자동으로 생성 된 도움말을 `Update-Help` 인터넷 또는 파일 공유에서 명령에 대 한 도움말을 다운로드 하기 위한 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-135">The auto-generated help includes text that directs the user to try to use the `Update-Help` cmdlet to download help for the command from the Internet or a file share.</span></span> <span data-ttu-id="7f635-136">또한를 사용 하 여 권장 합니다 **Online** 의 매개 변수는 `Get-Help` cmdlet 도움말 항목의 온라인 버전을 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-136">It also recommends using the **Online** parameter of the `Get-Help` cmdlet to get the online version of the help topic.</span></span>

## <a name="supporting-updatable-help"></a><span data-ttu-id="7f635-137">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="7f635-137">Supporting Updatable Help</span></span>

<span data-ttu-id="7f635-138">사용자의 Windows PowerShell 3.0 및 Windows PowerShell의 이후 버전을 다운로드 하 고 인터넷 또는 로컬 파일 공유에서 모듈에 대 한 업데이트 된 도움말 파일을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-138">Users of Windows PowerShell 3.0 and later versions of Windows PowerShell can download and install updated help files for a module from the Internet or from a local file share.</span></span> <span data-ttu-id="7f635-139">합니다 `Update-Help` 및 `Save-Help` cmdlet 사용자의 관리 세부 정보를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-139">The `Update-Help` and `Save-Help` cmdlets hide the management details from the user.</span></span> <span data-ttu-id="7f635-140">실행 하는 사용자를 `Update-Help` cmdlet 사용 하 여는 `Get-Help` cmdlet은 Windows PowerShell 명령 프롬프트에서 모듈에 대 한 최신 도움말 파일을 읽을 수입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-140">Users run the `Update-Help` cmdlet and then use the `Get-Help` cmdlet to read the newest help files for the module at the Windows PowerShell command prompt.</span></span> <span data-ttu-id="7f635-141">사용자는 Windows 또는 Windows PowerShell을 다시 시작할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-141">Users do not need to restart Windows or Windows PowerShell.</span></span>

<span data-ttu-id="7f635-142">방화벽 및 인터넷 액세스 없이 이러한 보호는 사용자 수 업데이트 가능한 도움말도 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-142">Users behind firewalls and those without Internet access can use Updatable Help, as well.</span></span> <span data-ttu-id="7f635-143">인터넷을 사용 하 여 관리자가 사용 하 여 액세스 하는 `Save-Help` cmdlet을 다운로드 하 여 파일 공유에 최신 도움말 파일을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-143">Administrators with Internet access use the `Save-Help` cmdlet to download and install the newest help files to a file share.</span></span> <span data-ttu-id="7f635-144">사용자를 사용 하 여는 **경로** 의 매개 변수는 `Update-Help` cmdlet을 파일 공유에서 최신 도움말 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-144">Then, users use the **Path** parameter of the `Update-Help` cmdlet to get the newest help files from the file share.</span></span>

<span data-ttu-id="7f635-145">모듈 작성자는 모듈의 도움말 파일을 포함 하 고 업데이트할 수 있는 도움말 또는 도움말 파일을 업데이트 하 고, 모듈의 도움말 파일을 생략 하 고, 업데이트할 수 있는 도움말 사용 하 여 설치 하 고 업데이트를 사용 하 여 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-145">Module authors can include help files in the module and use Updatable Help to update the help files, or omit help files from the module and use Updatable Help both to install and to update them.</span></span>

<span data-ttu-id="7f635-146">업데이트할 수 있는 도움말에 대 한 자세한 내용은 참조 하세요. [업데이트 가능한 도움말 지원](./supporting-updatable-help.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-146">For more information about Updatable Help, see [Supporting Updatable Help](./supporting-updatable-help.md).</span></span>

## <a name="supporting-online-help"></a><span data-ttu-id="7f635-147">온라인 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="7f635-147">Supporting Online Help</span></span>

<span data-ttu-id="7f635-148">종종 모듈 도움말 항목의 온라인 버전의 컴퓨터에 파일에 의존 하는 도움말 업데이트 하는 사용자에 게 없거나 설치 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7f635-148">Users who cannot or do not install updated help files on their computers often rely on the online version of module help topics.</span></span> <span data-ttu-id="7f635-149">합니다 **Online** 의 매개 변수는 `Get-Help` cmdlet가 기본 인터넷 브라우저에서 cmdlet 또는 사용자에 대 한 고급 함수 도움말 항목의 온라인 버전을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-149">The **Online** parameter of the `Get-Help` cmdlet opens the online version of a cmdlet or advanced function help topic for the user in their default Internet browser.</span></span>

<span data-ttu-id="7f635-150">`Get-Help` cmdlet의 값을 사용 합니다 **HelpUri** 속성 cmdlet의 도움말 항목의 온라인 버전을 확인 하는 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-150">The `Get-Help` cmdlet uses the value of the **HelpUri** property of the cmdlet or function to find the online version of the help topic.</span></span>

<span data-ttu-id="7f635-151">Windows PowerShell 3.0 부터는 cmdlet 클래스에 HelpUri 특성을 정의 하 여 cmdlet 및 함수 도움말 항목의 온라인 버전을 확인 하는 사용자를 제공할 수 있습니다 또는 **HelpUri** 의 속성을 **CmdletBinding** 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-151">Beginning in Windows PowerShell 3.0, you can help users find the online version of cmdlet and function help topics by defining the HelpUri attribute on the cmdlet class or the **HelpUri** property of the **CmdletBinding** attribute.</span></span> <span data-ttu-id="7f635-152">특성의 값은 값을 **HelpUri** cmdlet 또는 함수의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-152">The value of the attribute is the value of the **HelpUri** property of the cmdlet or function.</span></span>

<span data-ttu-id="7f635-153">자세한 내용은 [온라인 도움말 지원](./supporting-online-help.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7f635-153">For more information, see [Supporting Online Help](./supporting-online-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f635-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f635-154">See Also</span></span>

[<span data-ttu-id="7f635-155">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="7f635-155">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)

[<span data-ttu-id="7f635-156">업데이트 가능한 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="7f635-156">Supporting Updatable Help</span></span>](./supporting-updatable-help.md)

[<span data-ttu-id="7f635-157">온라인 도움말 지원</span><span class="sxs-lookup"><span data-stu-id="7f635-157">Supporting Online Help</span></span>](./supporting-online-help.md)