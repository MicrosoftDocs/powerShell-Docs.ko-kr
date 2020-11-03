---
description: Windows PowerShell에 대 한 그룹 정책 설정에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_group_policy_settings?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Group_Policy_Settings
ms.openlocfilehash: e55db2000f63170d7aef82a7b7223c6998b24602
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223465"
---
# <a name="about-group-policy-settings"></a><span data-ttu-id="6ae9a-104">그룹 정책 설정 정보</span><span class="sxs-lookup"><span data-stu-id="6ae9a-104">About Group Policy Settings</span></span>

## <a name="short-description"></a><span data-ttu-id="6ae9a-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="6ae9a-105">Short description</span></span>
<span data-ttu-id="6ae9a-106">Windows PowerShell에 대 한 그룹 정책 설정에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-106">Describes the Group Policy settings for Windows PowerShell</span></span>

## <a name="long-description"></a><span data-ttu-id="6ae9a-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-107">Long description</span></span>

<span data-ttu-id="6ae9a-108">Windows PowerShell에는 엔터프라이즈 환경에서 Windows 컴퓨터에 대 한 일관 된 구성 값을 정의 하는 데 도움이 되는 그룹 정책 설정이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-108">Windows PowerShell includes Group Policy settings to help you define consistent configuration values for Windows computers in an enterprise environment.</span></span>

<span data-ttu-id="6ae9a-109">PowerShell 그룹 정책 설정의 그룹 정책 경로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-109">The PowerShell Group Policy settings are in the following Group Policy paths:</span></span>

```
Computer Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell

User Configuration\
  Administrative Templates\
    Windows Components\
      Windows PowerShell
```

<span data-ttu-id="6ae9a-110">사용자 구성 경로의 그룹 정책 설정은 컴퓨터 구성 경로의 그룹 정책 설정 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-110">Group policy settings in the User Configuration path take precedence over Group Policy settings in the Computer Configuration path.</span></span>

<span data-ttu-id="6ae9a-111">정책은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-111">The policies are as follows:</span></span>

- <span data-ttu-id="6ae9a-112">모듈 로깅 설정: 모듈의 **LogPipelineExecutionDetails** 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-112">Turn on Module Logging: Sets the **LogPipelineExecutionDetails** property of modules.</span></span>
- <span data-ttu-id="6ae9a-113">PowerShell 스크립트 블록 로깅 켜기: 모든 PowerShell 스크립트의 자세한 로깅을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-113">Turn on PowerShell Script Block Logging: Enables detailed logging of all PowerShell scripts.</span></span>
- <span data-ttu-id="6ae9a-114">스크립트 실행 켜기: PowerShell 실행 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-114">Turn on Script Execution: Sets the PowerShell execution policy.</span></span>
- <span data-ttu-id="6ae9a-115">PowerShell 기록 켜기: PowerShell 명령의 입력 및 출력을 텍스트 기반 기록으로 캡처하는 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-115">Turn on PowerShell Transcription: enables capturing of input and output of PowerShell commands into text-based transcripts.</span></span>
- <span data-ttu-id="6ae9a-116">의 기본 원본 경로 설정 `Update-Help` : 업데이트할 수 있는 도움말의 원본을 인터넷이 아닌 디렉터리로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-116">Set the default source path for `Update-Help`: Sets the source for Updatable Help to a directory, not the Internet.</span></span>

<span data-ttu-id="6ae9a-117">다른 템플릿을 가져오고 그룹 정책을 구성 하는 방법에 대 한 자세한 내용은 [Windows에서 그룹 정책 관리 템플릿 용 중앙 저장소를 만들고 관리 하는 방법][gpstore]을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-117">For more information about acquiring other templates and configuring Group policy, see [How to create and manage the Central Store for Group Policy Administrative Templates in Windows][gpstore].</span></span>

## <a name="turn-on-module-logging"></a><span data-ttu-id="6ae9a-118">모듈 로깅 켜기</span><span class="sxs-lookup"><span data-stu-id="6ae9a-118">Turn on module logging</span></span>

<span data-ttu-id="6ae9a-119">**모듈 로깅** 설정 정책 설정은 선택한 PowerShell 모듈에 대 한 로깅을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-119">The **Turn on Module Logging** policy setting turns on logging for selected PowerShell modules.</span></span> <span data-ttu-id="6ae9a-120">설정은 영향을 받는 모든 컴퓨터의 모든 세션에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-120">The setting is effective in all sessions on all affected computers.</span></span>

<span data-ttu-id="6ae9a-121">이 정책 설정을 사용 하도록 설정 하 고 하나 이상의 모듈을 지정 하는 경우 지정 된 모듈에 대 한 파이프라인 실행 이벤트가 이벤트 뷰어의 Windows PowerShell 로그에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-121">If you enable this policy setting and specify one or more modules, pipeline execution events for the specified modules are recorded in the Windows PowerShell log in Event Viewer.</span></span>

<span data-ttu-id="6ae9a-122">이 정책 설정을 사용 하지 않도록 설정 하면 모든 PowerShell 모듈에 대해 실행 이벤트 로깅을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-122">If you disable this policy setting, logging of execution events is disabled for all PowerShell modules.</span></span>

<span data-ttu-id="6ae9a-123">이 정책 설정이 구성 되지 않은 경우 각 모듈의 **LogPipelineExecutionDetails** 속성은 모듈의 실행 이벤트를 기록할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-123">If this policy setting is not configured, the **LogPipelineExecutionDetails** property of each module determines whether the execution events of a module are logged.</span></span> <span data-ttu-id="6ae9a-124">기본적으로 모든 모듈의 **LogPipelineExecutionDetails** 속성은 False로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-124">By default, the **LogPipelineExecutionDetails** property of all modules is set to False.</span></span>

<span data-ttu-id="6ae9a-125">모듈에 대 한 모듈 로깅을 설정 하려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-125">To turn on module logging for a module, use the following command format.</span></span> <span data-ttu-id="6ae9a-126">모듈을 세션으로 가져와야 합니다. 설정은 현재 세션 에서만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-126">The module must be imported into the session and the setting is effective only in the current session.</span></span>

```powershell
Import-Module <Module-Name>
(Get-Module <Module-Name>).LogPipelineExecutionDetails = $true
```

<span data-ttu-id="6ae9a-127">특정 컴퓨터의 모든 세션에 대 한 모듈 로깅을 설정 하려면 이전 명령을 ' 모든 사용자 ' PowerShell 프로필 ()에 추가 `$Profile.AllUsersAllHosts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-127">To turn on module logging for all sessions on a particular computer, add the previous commands to the 'All Users' PowerShell profile (`$Profile.AllUsersAllHosts`).</span></span>

<span data-ttu-id="6ae9a-128">모듈 로깅에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-128">For more information about module logging, see [about_Modules](about_Modules.md).</span></span>

## <a name="turn-on-powershell-script-block-logging"></a><span data-ttu-id="6ae9a-129">PowerShell 스크립트 블록 로깅 켜기</span><span class="sxs-lookup"><span data-stu-id="6ae9a-129">Turn on PowerShell script block logging</span></span>

<span data-ttu-id="6ae9a-130">**Powershell 스크립트 블록 로깅** 설정 정책 설정을 사용 하면 모든 powershell 스크립트 입력을 Microsoft-Windows-Powershell/운영 이벤트 로그에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-130">The **Turn on PowerShell Script Block Logging** policy setting enables logging of all PowerShell script input to the Microsoft-Windows-PowerShell/Operational event log.</span></span> <span data-ttu-id="6ae9a-131">이 정책 설정을 사용 하도록 설정 하는 경우 PowerShell Core는 대화형으로 호출 되었는지 아니면 자동화를 통해 명령, 스크립트 블록, 함수 및 스크립트의 처리를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-131">If you enable this policy setting, PowerShell Core will log the processing of commands, script blocks, functions, and scripts - whether invoked interactively, or through automation.</span></span>

<span data-ttu-id="6ae9a-132">이 정책 설정을 사용하지 않도록 설정하면 PowerShell 스크립트 입력 기록이 비활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-132">If you disable this policy setting, logging of PowerShell script input is disabled.</span></span> <span data-ttu-id="6ae9a-133">스크립트 블록 호출 로깅을 사용하도록 설정하면 명령, 스크립트 블록, 함수 또는 스크립트의 호출을 시작하거나 중지할 때 PowerShell에서는 이벤트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-133">If you enable the Script Block Invocation Logging, PowerShell additionally logs events when invocation of a command, script block, function, or script starts or stops.</span></span> <span data-ttu-id="6ae9a-134">호출 로깅을 사용하도록 설정하면 많은 양의 이벤트 로그가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-134">Enabling Invocation Logging generates a high volume of event logs.</span></span>

## <a name="turn-on-script-execution"></a><span data-ttu-id="6ae9a-135">스크립트 실행 켜기</span><span class="sxs-lookup"><span data-stu-id="6ae9a-135">Turn on script execution</span></span>

<span data-ttu-id="6ae9a-136">**스크립트 실행 설정** 정책 설정은 실행할 수 있는 스크립트를 결정 하는 컴퓨터 및 사용자에 대 한 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-136">The **Turn on Script Execution** policy setting sets the execution policy for computers and users, which determines which scripts are permitted to run.</span></span>

<span data-ttu-id="6ae9a-137">정책 설정을 사용 하도록 설정 하는 경우 다음 정책 설정 중에서 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-137">If you enable the policy setting, you can select from among the following policy settings.</span></span>

- <span data-ttu-id="6ae9a-138">**서명 된 스크립트만 허용** 을 사용 하면 신뢰할 수 있는 게시자가 서명한 스크립트만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-138">**Allow only signed scripts** allows scripts to execute only if they are signed by a trusted publisher.</span></span> <span data-ttu-id="6ae9a-139">이 정책 설정은 AllSigned 실행 정책과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-139">This policy setting is equivalent to the AllSigned execution policy.</span></span>

- <span data-ttu-id="6ae9a-140">**로컬 스크립트 및 원격 서명 된 스크립트를 허용** 하면 모든 로컬 스크립트가 실행 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-140">**Allow local scripts and remote signed scripts** allows all local scripts to run.</span></span> <span data-ttu-id="6ae9a-141">인터넷에서 시작 되는 스크립트는 신뢰할 수 있는 게시자가 서명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-141">Scripts that originate from the Internet must be signed by a trusted publisher.</span></span> <span data-ttu-id="6ae9a-142">이 정책 설정은 RemoteSigned 실행 정책과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-142">This policy setting is equivalent to the RemoteSigned execution policy.</span></span>

- <span data-ttu-id="6ae9a-143">**모든 스크립트 허용** 을 사용 하면 모든 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-143">**Allow all scripts** allows all scripts to run.</span></span> <span data-ttu-id="6ae9a-144">이 정책 설정은 무제한 실행 정책과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-144">This policy setting is equivalent to the Unrestricted execution policy.</span></span>

<span data-ttu-id="6ae9a-145">이 정책 설정을 사용 하지 않도록 설정 하면 스크립트를 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-145">If you disable this policy setting, no scripts are allowed to run.</span></span> <span data-ttu-id="6ae9a-146">이 정책 설정은 제한 된 실행 정책과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-146">This policy setting is equivalent to the Restricted execution policy.</span></span>

<span data-ttu-id="6ae9a-147">이 정책 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 cmdlet에 의해 컴퓨터 또는 사용자에 대해 설정 된 실행 정책에서 `Set-ExecutionPolicy` 스크립트 실행이 허용 되는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-147">If you disable or do not configure this policy setting, the execution policy that is set for the computer or user by the `Set-ExecutionPolicy` cmdlet determines whether scripts are permitted to run.</span></span> <span data-ttu-id="6ae9a-148">기본값은 제한 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-148">The default value is Restricted.</span></span>

<span data-ttu-id="6ae9a-149">자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-149">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

## <a name="turn-on-powershell-transcription"></a><span data-ttu-id="6ae9a-150">Powershell 기록을 켭니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-150">Turn on powershell transcription</span></span>

<span data-ttu-id="6ae9a-151">**Powershell 기록 설정** 정책 설정을 사용 하 여 powershell 핵심 명령의 입력 및 출력을 텍스트 기반 성적 증명서로 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-151">The **Turn on PowerShell Transcription** policy setting lets you capture the input and output of PowerShell Core commands into text-based transcripts.</span></span> <span data-ttu-id="6ae9a-152">이 정책 설정을 사용 하도록 설정 하는 경우 powershell core는 powershell core 및 PowerShell Core 엔진을 활용 하는 다른 모든 응용 프로그램에 대 한 기록 로깅을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-152">If you enable this policy setting, PowerShell Core will enable transcription logging for PowerShell Core and any other applications that leverage the PowerShell Core engine.</span></span> <span data-ttu-id="6ae9a-153">기본적으로 PowerShell Core는 각 사용자의 내 문서 디렉터리에 ' PowerShell_transcript '을 포함 하는 파일 이름, 시작 된 컴퓨터 이름 및 시간을 포함 하는 기록 출력을 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-153">By default, PowerShell Core will record transcript output to each users' My Documents directory, with a file name that includes 'PowerShell_transcript', along with the computer name and time started.</span></span>
<span data-ttu-id="6ae9a-154">이 정책을 사용 하도록 설정 하는 것은 각 PowerShell Core 세션에서 Start-Transcript cmdlet을 호출 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-154">Enabling this policy is equivalent to calling the Start-Transcript cmdlet on each PowerShell Core session.</span></span>

<span data-ttu-id="6ae9a-155">이 정책 설정을 사용 하지 않도록 설정 하는 경우 기록이 cmdlet을 Start-Transcript 통해를 사용할 수 있지만 PowerShell 기반 응용 프로그램의 기록 로깅은 기본적으로 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-155">If you disable this policy setting, transcription logging of PowerShell-based applications is disabled by default, although transcripting can still be enabled through the Start-Transcript cmdlet.</span></span>

<span data-ttu-id="6ae9a-156">OutputDirectory 설정을 사용 하 여 공유 위치에 대 한 기록 로깅을 사용 하도록 설정 하는 경우 사용자가 다른 사용자 또는 컴퓨터의 성적 증명서를 보지 못하도록 해당 디렉터리에 대 한 액세스를 제한 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-156">If you use the OutputDirectory setting to enable transcription logging to a shared location, be sure to limit access to that directory to prevent users from viewing the transcripts of other users or computers.</span></span>

## <a name="set-the-default-source-path-for-update-help"></a><span data-ttu-id="6ae9a-157">Update-Help에 대 한 기본 원본 경로 설정</span><span class="sxs-lookup"><span data-stu-id="6ae9a-157">Set the default source path for Update-Help</span></span>

<span data-ttu-id="6ae9a-158">**Update-help에 대 한 기본 원본 경로 설정** 정책 설정은 Cmdlet의 **SourcePath** 매개 변수에 대 한 기본값을 설정 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="6ae9a-158">The **Set the Default Source Path for Update-Help** policy setting sets a default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span>
<span data-ttu-id="6ae9a-159">이 설정은 사용자가 cmdlet을 사용 하 여 `Update-Help` 인터넷에서 도움말 파일을 다운로드 하지 못하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-159">This setting prevents users from using the `Update-Help` cmdlet to download help files from the Internet.</span></span>

> [!NOTE]
> <span data-ttu-id="6ae9a-160">이 그룹 정책 설정은 **컴퓨터 구성** 및 **사용자 구성** 아래에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-160">This Group Policy setting appears under **Computer Configuration** and **User Configuration**.</span></span> <span data-ttu-id="6ae9a-161">그러나 **컴퓨터 구성** 에서 그룹 정책 설정만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-161">However, only the Group Policy setting under **Computer Configuration** is effective.</span></span> <span data-ttu-id="6ae9a-162">**사용자 구성** 에서 그룹 정책 설정은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-162">The Group Policy setting under **User Configuration** is ignored.</span></span>

<span data-ttu-id="6ae9a-163">`Update-Help`Cmdlet은 PowerShell 모듈에 대 한 최신 도움말 파일을 다운로드 하 여 설치 하 고 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-163">The `Update-Help` cmdlet downloads and installs the newest help files for PowerShell modules and installs them on the computer.</span></span> <span data-ttu-id="6ae9a-164">기본적으로에서는 `Update-Help` 모듈에 지정 된 인터넷 위치에서 새 도움말 파일을 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-164">By default, `Update-Help` downloads new help files from an Internet location specified by the module.</span></span>

<span data-ttu-id="6ae9a-165">그러나 cmdlet을 사용 하 여 `Save-Help` 네트워크 공유와 같은 파일 시스템 위치에 최신 도움말 파일을 다운로드 한 다음 cmdlet을 사용 `Update-Help` 하 여 파일 시스템 위치에서 도움말 파일을 가져오고 컴퓨터에 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-165">However, you can use the `Save-Help` cmdlet to download the newest help files to a file system location, such as a network share, and then use the `Update-Help` cmdlet to get the help files from the file system location and install them on the computer.</span></span> <span data-ttu-id="6ae9a-166">Cmdlet의 **SourcePath** 매개 변수는 `Update-Help` 파일 시스템 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-166">The **SourcePath** parameter of the `Update-Help` cmdlet specifies the file system location.</span></span>

<span data-ttu-id="6ae9a-167">**Sourcepath** 매개 변수에 기본값을 제공 하면이 그룹 정책 설정이 모든 명령에 **sourcepath** 매개 변수를 암시적으로 추가 합니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="6ae9a-167">By providing a default value for the **SourcePath** parameter, this Group Policy setting implicitly adds the **SourcePath** parameter to all `Update-Help` commands.</span></span> <span data-ttu-id="6ae9a-168">사용자는 다른 파일 시스템 위치를 입력 하 여 기본값으로 지정 된 특정 파일 시스템 위치를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-168">Users can override the particular file system location specified as the default value by entering a different file system location.</span></span>
<span data-ttu-id="6ae9a-169">그러나 명령에서 **SourcePath** 매개 변수를 제거할 수는 없습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="6ae9a-169">But they cannot remove the **SourcePath** parameter from the `Update-Help` command.</span></span>

<span data-ttu-id="6ae9a-170">이 정책 설정을 사용 하도록 설정 하는 경우 **SourcePath** 매개 변수의 기본값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-170">If you enable this policy setting, you can specify a default value for the **SourcePath** parameter.</span></span> <span data-ttu-id="6ae9a-171">파일 시스템 위치를 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-171">Enter a file system location.</span></span>

<span data-ttu-id="6ae9a-172">이 정책 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 cmdlet의 **SourcePath** 매개 변수에 대 한 기본값이 없습니다 `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="6ae9a-172">If this policy setting is disabled or not configured, there is no default value for the **SourcePath** parameter of the `Update-Help` cmdlet.</span></span> <span data-ttu-id="6ae9a-173">사용자는 인터넷 이나 모든 파일 시스템 위치에서 도움말을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-173">Users can download help from the Internet or from any file system location.</span></span>

<span data-ttu-id="6ae9a-174">자세한 내용은 [about_Updatable_Help](about_Updatable_Help.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ae9a-174">For more information, see [about_Updatable_Help](about_Updatable_Help.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="6ae9a-175">키워드</span><span class="sxs-lookup"><span data-stu-id="6ae9a-175">Keywords</span></span>

<span data-ttu-id="6ae9a-176">about_Group_Policies about_GroupPolicy</span><span class="sxs-lookup"><span data-stu-id="6ae9a-176">about_Group_Policies about_GroupPolicy</span></span>

## <a name="see-also"></a><span data-ttu-id="6ae9a-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ae9a-177">See also</span></span>

[<span data-ttu-id="6ae9a-178">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="6ae9a-178">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="6ae9a-179">about_Modules</span><span class="sxs-lookup"><span data-stu-id="6ae9a-179">about_Modules</span></span>](about_Modules.md)

[<span data-ttu-id="6ae9a-180">about_Updatable_Help</span><span class="sxs-lookup"><span data-stu-id="6ae9a-180">about_Updatable_Help</span></span>](about_Updatable_Help.md)

[<span data-ttu-id="6ae9a-181">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="6ae9a-181">Get-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Get-ExecutionPolicy)

[<span data-ttu-id="6ae9a-182">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="6ae9a-182">Set-ExecutionPolicy</span></span>](xref:Microsoft.PowerShell.Security.Set-ExecutionPolicy)

[<span data-ttu-id="6ae9a-183">Get-Module</span><span class="sxs-lookup"><span data-stu-id="6ae9a-183">Get-Module</span></span>](xref:Microsoft.PowerShell.Core.Get-Module)

[<span data-ttu-id="6ae9a-184">Update-Help</span><span class="sxs-lookup"><span data-stu-id="6ae9a-184">Update-Help</span></span>](xref:Microsoft.PowerShell.Core.Update-Help)

[<span data-ttu-id="6ae9a-185">Save-Help</span><span class="sxs-lookup"><span data-stu-id="6ae9a-185">Save-Help</span></span>](xref:Microsoft.PowerShell.Core.Save-Help)

<!-- link references -->
[gpstore]: https://support.microsoft.com/help/3087759
