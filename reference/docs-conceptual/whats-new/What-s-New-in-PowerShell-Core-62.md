---
title: PowerShell Core 6.2의 새로운 기능
description: PowerShell Core 6.2에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 03/28/2019
ms.openlocfilehash: 98dd97b064e11509bf97e68e0a312e6b34b5d2bc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "76995470"
---
# <a name="whats-new-in-powershell-core-62"></a><span data-ttu-id="54e43-103">PowerShell Core 6.2의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="54e43-103">What's New in PowerShell Core 6.2</span></span>

<span data-ttu-id="54e43-104">PowerShell Core 6.2 릴리스에서는 성능 향상, 버그 수정 및 품질을 개선하는 더 작은 cmdlet 및 언어 향상에 초점을 맞추었습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-104">The PowerShell Core 6.2 release focused on performance improvements, bug fixes, and smaller cmdlet and language enhancements that improve the quality.</span></span> <span data-ttu-id="54e43-105">전체 향상된 기능 목록을 보려면 GitHub의 자세한 [changelog](https://github.com/PowerShell/PowerShell/releases)를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="54e43-105">To see a full list of improvements, check out our detailed [changelogs](https://github.com/PowerShell/PowerShell/releases) on GitHub.</span></span>

## <a name="experimental-features"></a><span data-ttu-id="54e43-106">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="54e43-106">Experimental Features</span></span>

<span data-ttu-id="54e43-107">이전에 [실험적 기능][]에 대한 지원을 사용하도록 설정했습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-107">Previously, we enabled support for [Experimental Features][].</span></span> <span data-ttu-id="54e43-108">6\.2 릴리스에는 사용해 볼 수 있는 네 가지 실험적 기능이 있습니다. 기능을 향상하고 기능이 주류 상태로 홍보할 가치가 있는지 결정할 수 있도록 피드백을 제공해 주세요.</span><span class="sxs-lookup"><span data-stu-id="54e43-108">In the 6.2 release, we have four experimental features to try out. Please provide feedback so we can make improvements and to decide whether the feature is worth promoting to mainstream status.</span></span>

<span data-ttu-id="54e43-109">`Get-ExperimentalFeature`를 사용하여 사용 가능한 실험적 기능 목록을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-109">Use `Get-ExperimentalFeature` to get a list of available experimental features.</span></span> <span data-ttu-id="54e43-110">`Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature`를 사용하여 이 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-110">You can enable or disable these features with `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature`.</span></span>

### <a name="command-not-found-suggestions"></a><span data-ttu-id="54e43-111">명령을 찾을 수 없음 제안</span><span class="sxs-lookup"><span data-stu-id="54e43-111">Command Not Found Suggestions</span></span>

<span data-ttu-id="54e43-112">이 기능은 유사 일치를 사용하여 잘못 입력했을 수 있는 명령이나 cmdlet에 대한 제안을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-112">This feature uses fuzzy matching to find suggestions for commands or cmdlets you may have mistyped.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a><span data-ttu-id="54e43-113">예제</span><span class="sxs-lookup"><span data-stu-id="54e43-113">Example</span></span>

<span data-ttu-id="54e43-114">이 예제에서는 철자가 틀린 cmdlet 이름이 가능성이 가장 높은 제안부터 가장 낮은 제안까지 여러 제안에 유사 일치됩니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-114">In this example, the misspelled cmdlet name is fuzzy matched to several suggestions from most likely to least likely.</span></span>

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a><span data-ttu-id="54e43-115">암시적 원격 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="54e43-115">Implicit Remoting Batching</span></span>

<span data-ttu-id="54e43-116">파이프라인에서 [암시적 원격](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)을 사용하면 PowerShell에서는 파이프라인의 각 명령을 독립적으로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-116">When using [implicit remoting](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/) in a pipeline, PowerShell treats each command in the pipeline independently.</span></span> <span data-ttu-id="54e43-117">개체는 파이프라인 실행을 통해 클라이언트와 원격 시스템 사이에서 반복해서 직렬화 및 `de-serialized`됩니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-117">Objects are repeatedly serialized and `de-serialized` between the client and remote system over the execution of the pipeline.</span></span>

<span data-ttu-id="54e43-118">이 기능을 통해 PowerShell에서는 파이프라인을 분석하여 명령이 실행하기에 안전하고 대상 시스템에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-118">With this feature, PowerShell analyzes the pipeline to determine if the command is safe to run and it exists on the target system.</span></span> <span data-ttu-id="54e43-119">이에 해당하는 경우 PowerShell에서는 전체 파이프라인을 원격으로 실행하고 결과를 다시 클라이언트로만 직렬화 및 `de-serializes`합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-119">When true, PowerShell executes the entire pipeline remotely and only serializes and `de-serializes` the results back to the client.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

<span data-ttu-id="54e43-120">localhost를 통한 `Get-Process | Sort-Object`의 실제 테스트는 10~15초부터 20~30**밀리초**까지 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-120">A real-world test of `Get-Process | Sort-Object` over localhost decreases from 10-15 seconds to 20-30 **milliseconds**.</span></span> <span data-ttu-id="54e43-121">이 기능은 클라이언트에서만 사용하도록 설명하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-121">The feature only needs to be enabled on the client.</span></span> <span data-ttu-id="54e43-122">서버에서 변경할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-122">No changes are required on the server.</span></span>

### <a name="temp-drive"></a><span data-ttu-id="54e43-123">임시 드라이브</span><span class="sxs-lookup"><span data-stu-id="54e43-123">Temp Drive</span></span>

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

<span data-ttu-id="54e43-124">다른 운영 체제에서 PowerShell Core를 사용하는 경우 임시 디렉터리를 찾는 환경 변수가 Windows, macOS 및 Linux에서 서로 다른지 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-124">If you're using PowerShell Core on different operating systems, you'll discover that the environment variable for finding the temporary directory is different on Windows, macOS, and Linux!</span></span> <span data-ttu-id="54e43-125">이 기능을 통해 사용 중인 운영 체제의 임시 디렉터리에 자동으로 매핑되는 `Temp:`라는 [PSDrive][]를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-125">With this feature, you get a [PSDrive][] called `Temp:` that is automatically mapped to the temporary folder for the operating system you are using.</span></span>

#### <a name="example"></a><span data-ttu-id="54e43-126">예제</span><span class="sxs-lookup"><span data-stu-id="54e43-126">Example</span></span>

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

<span data-ttu-id="54e43-127">기본 파일 명령(예: Linux의 `ls`)은 PSDrive를 인식하지만 이 `Temp:` 드라이브를 인식하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-127">Be aware that native file commands (like `ls` on Linux) are not aware of PSDrives and won't see this `Temp:` drive.</span></span>

### <a name="abbreviation-expansion"></a><span data-ttu-id="54e43-128">약어 확장</span><span class="sxs-lookup"><span data-stu-id="54e43-128">Abbreviation Expansion</span></span>

<span data-ttu-id="54e43-129">PowerShell cmdlet에는 설명이 포함된 명사가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-129">PowerShell cmdlets are expected to have descriptive nouns.</span></span> <span data-ttu-id="54e43-130">이로 인해 입력하기 어려운 긴 이름이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-130">This results in long names that are more difficult to type.</span></span> <span data-ttu-id="54e43-131">이 기능을 사용하면 cmdlet의 대문자만 입력하고 탭 완성을 사용하여 일치 항목을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-131">This feature allows you to just type the uppercase characters of the cmdlet and use tab-completion to find a match.</span></span>

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a><span data-ttu-id="54e43-132">예제</span><span class="sxs-lookup"><span data-stu-id="54e43-132">Example</span></span>

```powershell
PS> i-arsavsf
```

<span data-ttu-id="54e43-133">Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 모듈이 설치되어 있고 Tab 키를 누르면 다음으로 자동 완성됩니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-133">If you hit tab, and have the Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) module installed, it will autocomplete to:</span></span>

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> <span data-ttu-id="54e43-134">이 기능은 대화형으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-134">This feature is intended to be used interactively.</span></span> <span data-ttu-id="54e43-135">cmdlet의 약어 형식은 실행할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-135">Abbreviated forms of cmdlets can't be executed.</span></span>
> <span data-ttu-id="54e43-136">이 기능은 별칭을 대체하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-136">This feature is not a replacement for aliases.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="54e43-137">주요 변경 내용</span><span class="sxs-lookup"><span data-stu-id="54e43-137">Breaking Changes</span></span>

- <span data-ttu-id="54e43-138">Windows PowerShell과 일치하도록 `Write-Output`의 `-NoEnumerate` 동작 수정</span><span class="sxs-lookup"><span data-stu-id="54e43-138">Fix `-NoEnumerate` behavior in `Write-Output` to be consistent with Windows PowerShell.</span></span> <span data-ttu-id="54e43-139">(#9069)</span><span class="sxs-lookup"><span data-stu-id="54e43-139">(#9069)</span></span>
- <span data-ttu-id="54e43-140">`Join-String -InputObject 1,2,3` 결과를 `1,2,3 | Join-String` 결과와 같게 만듭니다.(#8611)(@sethvs에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-140">Make `Join-String -InputObject 1,2,3` result equal to `1,2,3 | Join-String` result (#8611) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="54e43-141">`-Stable`을 `Sort-Object` 및 관련 테스트에 추가(#7862)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-141">Add `-Stable` to `Sort-Object` and related tests (#7862) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="54e43-142">초의 소수 부분을 허용하도록 `Start-Sleep` cmdlet 향상(#8537)(@Prototyyppi에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-142">Improve `Start-Sleep` cmdlet to accept fractional seconds (#8537) (Thanks @Prototyyppi!)</span></span>
- <span data-ttu-id="54e43-143">모든 문화권에서 OrdinalIgnoreCase를 `case-insensitive`로 사용하도록 해시 테이블 변경(#8566)</span><span class="sxs-lookup"><span data-stu-id="54e43-143">Change hashtable to use OrdinalIgnoreCase to be `case-insensitive` in all Cultures (#8566)</span></span>
- <span data-ttu-id="54e43-144">`Get-ChildItem` 출력에 바인딩되도록 `Import-Csv`에서 **LiteralPath** 수정(#8277)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-144">Fix **LiteralPath** in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-145">`Import-Csv`에서 큰따옴표가 사용되는 경우 더 이상 이름 없이 열을 건너뛰지 않음(#7899)(@Topping에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-145">No longer skips a column without name if double quote delimiter is used in `Import-Csv` (#7899) (Thanks @Topping!)</span></span>
- <span data-ttu-id="54e43-146">`Get-ExperimentalFeature`에 더 이상 `-ListAvailable` 스위치가 없음(#8318)</span><span class="sxs-lookup"><span data-stu-id="54e43-146">`Get-ExperimentalFeature` no longer has `-ListAvailable` switch (#8318)</span></span>
- <span data-ttu-id="54e43-147">이제 Debug 매개 변수가 `$DebugPreference`를 **Inquire** 대신 **Continue**로 설정함(#8195)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-147">Debug parameter now sets `$DebugPreference` to **Continue** instead of **Inquire** (#8195) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="54e43-148">pwsh와 함께 사용되는 리디렉션되고 인코딩되는 비대화형 명령에서 지정된 경우 `-OutputFormat` 사용(#8115)</span><span class="sxs-lookup"><span data-stu-id="54e43-148">Honor `-OutputFormat` if specified in non-interactive, redirected, encoded command used with pwsh (#8115)</span></span>
- <span data-ttu-id="54e43-149">GAC에서 로드하기 전에 모듈 기본 경로에서 어셈블리 로드(#8073)</span><span class="sxs-lookup"><span data-stu-id="54e43-149">Load assembly from module base path before trying to load from the GAC (#8073)</span></span>
- <span data-ttu-id="54e43-150">Linux 미리 보기 패키지에서 물결표 제거(#8244)</span><span class="sxs-lookup"><span data-stu-id="54e43-150">Remove tilde from Linux preview packages (#8244)</span></span>
- <span data-ttu-id="54e43-151">프로필 처리 앞으로 `-WorkingDirectory` 처리 이동(#8079)</span><span class="sxs-lookup"><span data-stu-id="54e43-151">Move processing of `-WorkingDirectory` before processing of profiles (#8079)</span></span>
- <span data-ttu-id="54e43-152">Unix에서 `PATHEXT` 환경 변수를 추가하지 않음(#7697)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-152">Do not add `PATHEXT` environment variable on Unix (#7697) (Thanks @iSazonov!)</span></span>

## <a name="known-issues"></a><span data-ttu-id="54e43-153">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="54e43-153">Known Issues</span></span>

- <span data-ttu-id="54e43-154">Windows IOT ARM 플랫폼의 원격 처리에는 모듈 로드 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54e43-154">Remoting on Windows IOT ARM platforms has an issue loading modules.</span></span> <span data-ttu-id="54e43-155">(#8053) 참조</span><span class="sxs-lookup"><span data-stu-id="54e43-155">See (#8053)</span></span>

## <a name="general-updates-and-fixes"></a><span data-ttu-id="54e43-156">일반 업데이트 및 수정</span><span class="sxs-lookup"><span data-stu-id="54e43-156">General Updates and Fixes</span></span>

- <span data-ttu-id="54e43-157">대/소문자를 구분하는 파일 시스템에서 파일 및 폴더의 대/소문자를 구분하지 않는 탭 완성 사용(#8128)</span><span class="sxs-lookup"><span data-stu-id="54e43-157">Enable case-insensitive tab completion for files and folders on case-sensitive filesystem (#8128)</span></span>
- <span data-ttu-id="54e43-158">PSVersionInfo.PSVersion 및 PSVersionInfo.PSEdition을 public으로 설정(#8054)(@KirkMunro에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-158">Make PSVersionInfo.PSVersion and PSVersionInfo.PSEdition public (#8054) (Thanks @KirkMunro!)</span></span>
- <span data-ttu-id="54e43-159">`catch{ }` 블록에서 `$_` / `$PSItem`의 형식 유추 추가(#8020)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-159">Add Type Inference for `$_` / `$PSItem` in `catch{ }` blocks (#8020) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="54e43-160">static 메서드 호출 형식 유추 수정(#8018)(@SeeminglyScience에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-160">Fix static method invocation type inference (#8018) (Thanks @SeeminglyScience!)</span></span>
- <span data-ttu-id="54e43-161">`Select-Object`, `Group-Object`, **PSObject** 및 **Hashtable**의 유추 형식 만들기(#7231)(@powercode에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-161">Create inferred types for `Select-Object`, `Group-Object`, **PSObject** and **Hashtable** (#7231) (Thanks @powercode!)</span></span>
- <span data-ttu-id="54e43-162">`ByRef-like` 형식 매개 변수가 포함된 호출 메서드 지원(#7721)</span><span class="sxs-lookup"><span data-stu-id="54e43-162">Support calling method with `ByRef-like` type parameters (#7721)</span></span>
- <span data-ttu-id="54e43-163">Windows PowerShell 모듈 경로가 이미 환경의 PSModulePath에 있는 경우 처리(#7727)</span><span class="sxs-lookup"><span data-stu-id="54e43-163">Handle the case where the Windows PowerShell module path is already in the environment's PSModulePath (#7727)</span></span>
- <span data-ttu-id="54e43-164">일반 텍스트를 저장하여 Windows가 아닌 환경에서도 `SecureString` cmdlet을 사용하도록 설정(#9199)</span><span class="sxs-lookup"><span data-stu-id="54e43-164">Enable `SecureString` cmdlets for non-Windows by storing the plain text (#9199)</span></span>
- <span data-ttu-id="54e43-165">securestring을 사용하여 clixml을 가져올 때 Windows가 아닌 환경에서 오류 메시지 개선(#7997)</span><span class="sxs-lookup"><span data-stu-id="54e43-165">Improve error message on non-Windows when importing clixml with securestring (#7997)</span></span>
- <span data-ttu-id="54e43-166">`Send-MailMessage`에 ReplyTo 매개 변수 추가(#8727)(@replicaJunction에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-166">Adding parameter ReplyTo to `Send-MailMessage` (#8727) (Thanks @replicaJunction!)</span></span>
- <span data-ttu-id="54e43-167">`Send-MailMessage`에 사용되지 않음 메시지 추가(#9178)</span><span class="sxs-lookup"><span data-stu-id="54e43-167">Add Obsolete message to `Send-MailMessage` (#9178)</span></span>
- <span data-ttu-id="54e43-168">WinRM이 없을 때 `localhost`에서 `Restart-Computer`가 작동하도록 수정(#9160)</span><span class="sxs-lookup"><span data-stu-id="54e43-168">Fix `Restart-Computer` to work on `localhost` when WinRM is not present (#9160)</span></span>
- <span data-ttu-id="54e43-169">PowerShell이 호스트될 때 `Start-Job`이 종료 오류를 throw하도록 설정(#9128)</span><span class="sxs-lookup"><span data-stu-id="54e43-169">Make `Start-Job` throw terminating error when PowerShell is being hosted (#9128)</span></span>
- <span data-ttu-id="54e43-170">ushort, uint, ulong 및 short 리터럴의 C# 스타일 형식 가속기 및 접미사 추가(#7813)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-170">Add C# style type accelerators and suffixes for ushort, uint, ulong, and short literals (#7813) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="54e43-171">숫자 리터럴의 새 접미사 추가 - [about_Numeric_Literals][] 참조(#7901)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-171">Added new suffixes for numeric literals - see [about_Numeric_Literals][] (#7901) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="54e43-172">SupportsShouldProcess가 'true'로 설정되지 않을 경우 영향 수준을 올바르게 보고(#8209)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-172">Correctly Report impact level when SupportsShouldProcess is not set to 'true' (#8209) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="54e43-173">웹 cmdlet에서 요청 문자 집합 문제 수정(#8742)(@markekraus에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-173">Fix Request Charset Issues in Web Cmdlets (#8742) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="54e43-174">웹 cmdlet에서 `100-continue` 예상 문제 수정(#8679)(@markekraus에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-174">Fix Expect `100-continue` issue with Web Cmdlets (#8679) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="54e43-175">웹 cmdlet에서 파일 차단 문제 수정(#7676)(@Claustn에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-175">Fix file blocking issue with web cmdlets (#7676) (Thanks @Claustn!)</span></span>
- <span data-ttu-id="54e43-176">`Invoke-RestMethod`에서 코드 페이지 구문 분석 문제 수정(#8694)(@markekraus에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-176">Fix code page parsing issue in `Invoke-RestMethod` (#8694) (Thanks @markekraus!)</span></span>
- <span data-ttu-id="54e43-177">`ConvertTo-Json`을 리팩터링하여 JsonObject.ConvertToJson을 공용 API로 공개(#8682)</span><span class="sxs-lookup"><span data-stu-id="54e43-177">Refactor `ConvertTo-Json` to expose JsonObject.ConvertToJson as a public API (#8682)</span></span>
- <span data-ttu-id="54e43-178">-Depth를 사용하여 `ConvertFrom-Json`에서 구성 가능한 최대 깊이 추가(#8199)(@louistio에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-178">Add configurable maximum depth in `ConvertFrom-Json` with -Depth (#8199) (Thanks @louistio!)</span></span>
- <span data-ttu-id="54e43-179">`ConvertTo-Json` cmdlet에서 EscapeHandling 매개 변수 추가(#7775)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-179">Add EscapeHandling parameter in `ConvertTo-Json` cmdlet (#7775) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-180">pwsh 및 `Enter-PSHostProcess`에 `-CustomPipeName` 추가(#8889)</span><span class="sxs-lookup"><span data-stu-id="54e43-180">Add `-CustomPipeName` to pwsh and `Enter-PSHostProcess` (#8889)</span></span>
- <span data-ttu-id="54e43-181">`New-Item`사용하여 Windows에서 상대 바로 가기 링크를 만들 수 있음(#8783)</span><span class="sxs-lookup"><span data-stu-id="54e43-181">Enable creating relative symbolic links on Windows with `New-Item` (#8783)</span></span>
- <span data-ttu-id="54e43-182">Windows 사용자가 개발자 모드에서 관리자 권한이 없어도 바로 가기 링크를 만들도록 허용(#8534)</span><span class="sxs-lookup"><span data-stu-id="54e43-182">Allow Windows users in developer mode to create symlinks without elevation (#8534)</span></span>
- <span data-ttu-id="54e43-183">`Write-Information`에서 `$null`을 사용할 수 있음(#8774)</span><span class="sxs-lookup"><span data-stu-id="54e43-183">Enable `Write-Information` to accept `$null` (#8774)</span></span>
- <span data-ttu-id="54e43-184">MAML 도움말 콘텐츠를 사용하여 고급 함수의 `Get-Help` 수정(#8353)</span><span class="sxs-lookup"><span data-stu-id="54e43-184">Fix `Get-Help` for advanced functions with MAML help content (#8353)</span></span>
- <span data-ttu-id="54e43-185">매개 변수를 하나만 선언할 경우 -Parameter를 사용하여 `Get-Help` PSTypeName 문제 수정(#8754)(@pougetat에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-185">Fix `Get-Help` PSTypeName issue with -Parameter when only one parameter is declared (#8754) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="54e43-186">주석 도움말을 위해 ScriptBlock에서 실행되는 `Get-Help`의 토큰 계산 수정</span><span class="sxs-lookup"><span data-stu-id="54e43-186">Token calculation fix for `Get-Help` executed on ScriptBlock for comment help.</span></span> <span data-ttu-id="54e43-187">(#8238)(@hubuk에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-187">(#8238) (Thanks @hubuk!)</span></span>
- <span data-ttu-id="54e43-188">문자열 배열을 허용하도록 `Get-Help` cmdlet -Parameter 매개 변수 변경(#8454)(@sethvs에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-188">Change `Get-Help` cmdlet -Parameter parameter so it accepts string arrays (#8454) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="54e43-189">해당 경로에 공백이 포함된 경우 PAGER 해결(#8571)(@pougetat에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-189">Resolve PAGER if its path contains spaces (#8571) (Thanks @pougetat!)</span></span>
- <span data-ttu-id="54e43-190">'help' 함수에서 `less`를 사용하여 종료 방법을 사용자에게 지시하도록 메시지 추가(#7998)</span><span class="sxs-lookup"><span data-stu-id="54e43-190">Add prompt to the use of `less` in the function 'help' to instruct user how to quit (#7998)</span></span>
- <span data-ttu-id="54e43-191">`Format-Hex` cmdlet에서 지원 enum 및 char 형식 추가(#8191)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-191">Add support enum and char types in `Format-Hex` cmdlet (#8191) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-192">`Format-Hex`에서 ShouldProcess 제거(#8178)</span><span class="sxs-lookup"><span data-stu-id="54e43-192">Remove ShouldProcess from `Format-Hex` (#8178)</span></span>
- <span data-ttu-id="54e43-193">`Format-Hex`에 새 Offset 및 Count 매개 변수를 추가하고 cmdlet을 리팩터링(#7877)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-193">Add new Offset and Count parameters to `Format-Hex` and refactor the cmdlet (#7877) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-194">`ConvertTo-Html`에서 'label'의 별칭 키로 'name' 허용, 정수로 'width'를 입력하도록 허용(#8426)(@mklement0에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-194">Allow 'name' as an alias key for 'label' in `ConvertTo-Html`, allow the 'width' entry to be an integer (#8426) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="54e43-195">scriptblock 기반 계산 속성이 `ConvertTo-Html`에서 다시 작동하도록 설정(#8427)(@mklement0에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-195">Make scriptblock based calculated properties work again in `ConvertTo-Html` (#8427) (Thanks @mklement0!)</span></span>
- <span data-ttu-id="54e43-196">파이프라인 입력에서 텍스트를 만드는 cmdlet `Join-String` 추가(#7660)(@powercode에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-196">Add cmdlet `Join-String` for creating text from pipeline input (#7660) (Thanks @powercode!)</span></span>
- <span data-ttu-id="54e43-197">`Join-String` cmdlet FormatString 매개 변수 논리 수정(#8449)(@sethvs에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-197">Fix `Join-String` cmdlet FormatString parameter logic (#8449) (Thanks @sethvs!)</span></span>
- <span data-ttu-id="54e43-198">원격에서 작동하도록 `Clear-Host`를 다시 using `$RAWUI` 및 clear로 변경(#8609)</span><span class="sxs-lookup"><span data-stu-id="54e43-198">Change `Clear-Host` back to using `$RAWUI` and clear to work over remoting (#8609)</span></span>
- <span data-ttu-id="54e43-199">`Clear-Host`를 간단하게 호출되는 `[console]::clear`로 변경하고 Unix에서 clear 별칭 제거(#8603)</span><span class="sxs-lookup"><span data-stu-id="54e43-199">Change `Clear-Host` to simply called `[console]::clear` and remove clear alias from Unix (#8603)</span></span>
- <span data-ttu-id="54e43-200">`Get-ChildItem` 출력에 바인딩되도록 `Import-Csv`에서 LiteralPath 수정(#8277)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-200">Fix LiteralPath in `Import-Csv` to bind to `Get-ChildItem` output (#8277) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-201">help 함수에서 AliasHelpInfo에 파서를 사용하면 안 됨(#8552)</span><span class="sxs-lookup"><span data-stu-id="54e43-201">help function shouldn't use pager for AliasHelpInfo (#8552)</span></span>
- <span data-ttu-id="54e43-202">`-UseMinimalHeader`를 `Start-Transcript`에 추가하여 스크립트 헤더 최소화(#8402)(@lukexjeremy에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-202">Add `-UseMinimalHeader` to `Start-Transcript` to minimize transcript header (#8402) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="54e43-203">`Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature` cmdlet 추가(#8318)</span><span class="sxs-lookup"><span data-stu-id="54e43-203">Add `Enable-ExperimentalFeature` and `Disable-ExperimentalFeature` cmdlets (#8318)</span></span>
- <span data-ttu-id="54e43-204">logman.exe를 사용할 수 있는 경우 **PSDiagnostics**에서 모든 cmdlet 공개(#8366)</span><span class="sxs-lookup"><span data-stu-id="54e43-204">Expose all cmdlets from **PSDiagnostics** if logman.exe is available (#8366)</span></span>
- <span data-ttu-id="54e43-205">`non-Windows` 플랫폼의 `New-PSDrive`에서 **Persist** 매개 변수 제거(#8291)(@lukexjeremy에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-205">Remove **Persist** parameter from `New-PSDrive` on `non-Windows` platform (#8291) (Thanks @lukexjeremy!)</span></span>
- <span data-ttu-id="54e43-206">`cd +` 지원 추가(#7206)(@bergmeister에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-206">Add support for `cd +` (#7206) (Thanks @bergmeister!)</span></span>
- <span data-ttu-id="54e43-207">\- 및 +라는 폴더에서 `Set-Location -LiteralPath`를 작동할 수 있음(#8089)</span><span class="sxs-lookup"><span data-stu-id="54e43-207">Enable `Set-Location -LiteralPath` to work with folders named - and + (#8089)</span></span>
- <span data-ttu-id="54e43-208">비어 있거나 `$null` 경로 값이 제공된 경우 `Test-Path`에서 `$false`를 반환함(#8080)(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-208">`Test-Path` returns `$false` when given an empty or `$null` path value (#8080) (Thanks @vexx32!)</span></span>
- <span data-ttu-id="54e43-209">경로가 공급자와 일치하지 않는 경우에도 동적 매개 변수를 반환할 수 있음(#7957)</span><span class="sxs-lookup"><span data-stu-id="54e43-209">Allow dynamic parameter to be returned even if path does not match any provider (#7957)</span></span>
- <span data-ttu-id="54e43-210">Unix 플랫폼에서 `Get-PSHostProcessInfo` 및 `Enter-PSHostProcess` 지원(#8232)</span><span class="sxs-lookup"><span data-stu-id="54e43-210">Support `Get-PSHostProcessInfo` and `Enter-PSHostProcess` on Unix platforms (#8232)</span></span>
- <span data-ttu-id="54e43-211">`Get-Content` cmdlet에서 할당 감소(#8103)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-211">Reduce allocations in `Get-Content` cmdlet (#8103) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-212">`Add-Content`가 콘텐츠를 작성하는 동안 다른 도구와 읽기 권한을 공유할 수 있음(#8091)</span><span class="sxs-lookup"><span data-stu-id="54e43-212">Enable `Add-Content` to share read access with other tools while writing content (#8091)</span></span>
- <span data-ttu-id="54e43-213">컨테이너를 대상으로 지정하는 경우 `Get/Add-Content`가 개선된 오류를 throw함(#7823)(@kvprasoon에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-213">`Get/Add-Content` throws improved error when targeting a container (#7823) (Thanks @kvprasoon!)</span></span>
- <span data-ttu-id="54e43-214">Add `-Name`, `-NoUserOverrides` 및 `-ListAvailable` 매개 변수를 `Get-Culture` cmdlet에 추가(#7702)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-214">Add `-Name`, `-NoUserOverrides` and `-ListAvailable` parameters to `Get-Culture` cmdlet (#7702) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-215">**Encoding** 매개 변수 완성을 위한 통합 특성 추가</span><span class="sxs-lookup"><span data-stu-id="54e43-215">Add unified attribute for completion for **Encoding** parameter.</span></span> <span data-ttu-id="54e43-216">(#7732)(@ThreeFive-O에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-216">(#7732) (Thanks @ThreeFive-O!)</span></span>
- <span data-ttu-id="54e43-217">**Encoding** 매개 변수에서 등록된 코드 페이지의 숫자 ID 및 이름 허용(#7636)(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-217">Allow numeric Ids and name of registered code pages in **Encoding** parameters (#7636) (Thanks @iSazonov!)</span></span>
- <span data-ttu-id="54e43-218">와일드카드 문자를 사용하여 `Rename-Item -Path` 수정(#7398)(@kwkam에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-218">Fix `Rename-Item -Path` with wildcard char (#7398) (Thanks @kwkam!)</span></span>
- <span data-ttu-id="54e43-219">`Start-Transcript`를 사용하고 파일이 있는 경우 삭제하는 대신 파일을 비움(#8131)(@paalbra에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-219">When using `Start-Transcript` and file exists, empty file rather than deleting (#8131) (Thanks @paalbra!)</span></span>
- <span data-ttu-id="54e43-220">명시적으로 **FileAccess.Read** 및 **FileShare.Read**를 사용하여 `Add-Type` 오픈 소스 파일 만들기(#7915)(@IISResetMe에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-220">Make `Add-Type` open source files with **FileAccess.Read** and **FileShare.Read** explicitly (#7915) (Thanks @IISResetMe!)</span></span>
- <span data-ttu-id="54e43-221">최신 Windows의 `Enter-PSSession -ContainerId` 수정(#7883)</span><span class="sxs-lookup"><span data-stu-id="54e43-221">Fix `Enter-PSSession -ContainerId` for the latest Windows (#7883)</span></span>
- <span data-ttu-id="54e43-222">**NestedModules** 속성이 `Test-ModuleManifest`에 의해 채워지도록 함(#7859)</span><span class="sxs-lookup"><span data-stu-id="54e43-222">Ensure **NestedModules** property gets populated by `Test-ModuleManifest` (#7859)</span></span>
- <span data-ttu-id="54e43-223">`%F` 사례를 `Get-Date` -UFormat에 추가(#7630)(@britishben에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-223">Add `%F` case to `Get-Date` -UFormat (#7630) (Thanks @britishben!)</span></span>
- <span data-ttu-id="54e43-224">종속성이 있는 서비스를 중지하도록 `Set-Service -Status Stopped` 수정(#5525)(@zhenggu에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="54e43-224">Fix `Set-Service -Status Stopped` to stop services with dependencies (#5525) (Thanks @zhenggu!)</span></span>

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[실험적 기능]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[Experimental Features]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
