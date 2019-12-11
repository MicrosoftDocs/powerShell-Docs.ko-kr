---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.x 릴리스 정보
ms.openlocfilehash: 3fc712dbcbe184c60ae248b260c8f6800f111fdd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416512"
---
# <a name="windows-management-framework-wmf-5x-release-notes"></a><span data-ttu-id="cd089-103">WMF(Windows Management Framework) 5.x 릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="cd089-103">Windows Management Framework (WMF) 5.x Release Notes</span></span>

## <a name="wmf-50-changes"></a><span data-ttu-id="cd089-104">WMF 5.0 변경 내용</span><span class="sxs-lookup"><span data-stu-id="cd089-104">WMF 5.0 Changes</span></span>

- <span data-ttu-id="cd089-105">PowerShell 5.0에서는 새 구조적 **정보** 스트림 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-105">PowerShell 5.0 adds a new structured **Information** stream</span></span>
- <span data-ttu-id="cd089-106">4개의 새 DSC 리소스를 포함하는 DSC의 개선 사항:</span><span class="sxs-lookup"><span data-stu-id="cd089-106">Improvements to DSC including four new DSC resources:</span></span>
  - <span data-ttu-id="cd089-107">WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="cd089-107">WindowsFeatureSet</span></span>
  - <span data-ttu-id="cd089-108">WindowsOptionalFeatureSet</span><span class="sxs-lookup"><span data-stu-id="cd089-108">WindowsOptionalFeatureSet</span></span>
  - <span data-ttu-id="cd089-109">ServiceSet</span><span class="sxs-lookup"><span data-stu-id="cd089-109">ServiceSet</span></span>
  - <span data-ttu-id="cd089-110">ProcessSet</span><span class="sxs-lookup"><span data-stu-id="cd089-110">ProcessSet</span></span>
- <span data-ttu-id="cd089-111">PowerShell 원격을 통해 역할 기반 관리를 가능하게 하는 충분한 관리 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-111">Added Just Enough Administration to enable role-based administration through PowerShell remoting</span></span>
- <span data-ttu-id="cd089-112">PowerShell 5.0에서 사용자 정의 클래스 및 열거형을 포함하도록 언어 확장</span><span class="sxs-lookup"><span data-stu-id="cd089-112">PowerShell 5.0 extends the language to include user-defined classes and enumerations</span></span>
- <span data-ttu-id="cd089-113">PowerShell ISE의 디버깅 기능 향상 및 원격 디버깅 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-113">Improved debugging features in PowerShell ISE and added remote debugging</span></span>
- <span data-ttu-id="cd089-114">PowerShellGet 및 PackageManagement 모듈 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-114">Added the PowerShellGet and PackageManagement modules</span></span>
- <span data-ttu-id="cd089-115">PowerShell 스크립트 로깅 및 스크립트 향상</span><span class="sxs-lookup"><span data-stu-id="cd089-115">Enhanced PowerShell script logging and transcripts</span></span>
- <span data-ttu-id="cd089-116">암호화 메시지 구문 cmdlet 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-116">Add Cryptographic Message Syntax cmdlets</span></span>
- <span data-ttu-id="cd089-117">WMF 5.0에 Windows용 NetworkSwitchManager 모듈 포함</span><span class="sxs-lookup"><span data-stu-id="cd089-117">WMF 5.0 includes the NetworkSwitchManager module for Windows</span></span>
- <span data-ttu-id="cd089-118">Microsoft.PowerShell.ODataUtils 모듈 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-118">Added the Microsoft.PowerShell.ODataUtils module</span></span>
- <span data-ttu-id="cd089-119">SIL(소프트웨어 인벤토리 로깅) 지원 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-119">Added support for Software Inventory Logging (SIL)</span></span>
- <span data-ttu-id="cd089-120">사용자 요청 및 문제에 대한 응답으로 신규 또는 업데이트 cmdlet 제공</span><span class="sxs-lookup"><span data-stu-id="cd089-120">Sever new or update cmdlets in response to user requests and issues</span></span>

## <a name="wmf-51-changes"></a><span data-ttu-id="cd089-121">WMF 5.1 변경 내용</span><span class="sxs-lookup"><span data-stu-id="cd089-121">WMF 5.1 Changes</span></span>

<span data-ttu-id="cd089-122">WMF 5.1에는 Windows Server 2016과 함께 릴리스된 PowerShell, WMI, WinRM 및 SIL(소프트웨어 인벤토리 로깅) 구성 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-122">WMF 5.1 includes the PowerShell, WMI, WinRM, and Software Inventory Logging (SIL) components that were released with Windows Server 2016.</span></span> <span data-ttu-id="cd089-123">WMF 5.1은 Windows 7, Windows 8.1, Windows Server 2008 R2, 2012 및 2012 R2에 설치할 수 있으며 WMF 5.0보다 개선된 여러 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-123">WMF 5.1 can be installed on Windows 7, Windows 8.1, Windows Server 2008 R2, 2012, and 2012 R2, and provides several improvements over WMF 5.0 including:</span></span>

- <span data-ttu-id="cd089-124">새로운 cmdlet</span><span class="sxs-lookup"><span data-stu-id="cd089-124">New cmdlets</span></span>
- <span data-ttu-id="cd089-125">서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항</span><span class="sxs-lookup"><span data-stu-id="cd089-125">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="cd089-126">PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가</span><span class="sxs-lookup"><span data-stu-id="cd089-126">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="cd089-127">DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항</span><span class="sxs-lookup"><span data-stu-id="cd089-127">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="cd089-128">끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상</span><span class="sxs-lookup"><span data-stu-id="cd089-128">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="cd089-129">다양한 사용자 요청 및 문제에 대한 응답</span><span class="sxs-lookup"><span data-stu-id="cd089-129">Responses to a number of user requests and issues</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd089-130">Windows Server 2008 또는 Windows 7에 WMF 5.1을 설치하기 전에 WMF 3.0이 설치되어 있지 않은지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-130">Before you install WMF 5.1 on Windows Server 2008 or Windows 7, confirm that WMF 3.0 isn't installed.</span></span> <span data-ttu-id="cd089-131">자세한 내용은 [Windows Server 2008 R2 SP1 및 Windows 7 SP1에 대한 WMF 5.1 필수 조건](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd089-131">For more information, see [WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1](../setup/install-configure.md#wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1).</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="cd089-132">PowerShell 버전</span><span class="sxs-lookup"><span data-stu-id="cd089-132">PowerShell Editions</span></span>

<span data-ttu-id="cd089-133">버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-133">Starting with version 5.1, PowerShell is available in different editions that denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="cd089-134">**Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-134">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="cd089-135">**Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-135">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="learn-more-about-using-powershell-editions"></a><span data-ttu-id="cd089-136">PowerShell 버전 사용 방법에 대한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="cd089-136">Learn more about using PowerShell Editions</span></span>

- [<span data-ttu-id="cd089-137">$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인</span><span class="sxs-lookup"><span data-stu-id="cd089-137">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="cd089-138">PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링</span><span class="sxs-lookup"><span data-stu-id="cd089-138">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="cd089-139">호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지</span><span class="sxs-lookup"><span data-stu-id="cd089-139">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="cd089-140">특정 PowerShell 버전에 대한 모듈의 호환성 선언</span><span class="sxs-lookup"><span data-stu-id="cd089-140">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

## <a name="module-analysis-cache"></a><span data-ttu-id="cd089-141">모듈 분석 캐시</span><span class="sxs-lookup"><span data-stu-id="cd089-141">Module Analysis Cache</span></span>

<span data-ttu-id="cd089-142">WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-142">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="cd089-143">기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-143">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="cd089-144">일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-144">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="cd089-145">캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-145">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="cd089-146">이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-146">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="cd089-147">PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-147">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="cd089-148">파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-148">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="cd089-149">이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-149">This sets the path to an invalid device.</span></span> <span data-ttu-id="cd089-150">PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-150">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="cd089-151">캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-151">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="cd089-152">때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-152">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="cd089-153">이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-153">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="cd089-154">모듈 버전 지정</span><span class="sxs-lookup"><span data-stu-id="cd089-154">Specifying module version</span></span>

<span data-ttu-id="cd089-155">WMF 5.1에서 `using module`은 PowerShell에서 다른 모듈 관련 생성과 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-155">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="cd089-156">이전에는 특정 모듈 버전을 지정할 수 없었습니다. 따라서 여러 버전이 있는 경우 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-156">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="cd089-157">WMF 5.1에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-157">In WMF 5.1:</span></span>

- <span data-ttu-id="cd089-158">[ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)(ModuleSpecification 생성자(해시 테이블))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-158">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

  <span data-ttu-id="cd089-159">이 해시 테이블은 `Get-Module -FullyQualifiedName`과 형식이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-159">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="cd089-160">**예:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="cd089-160">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="cd089-161">모듈의 여러 버전이 있는 경우 PowerShell에서는 `Import-Module`과 **동일한 해결 논리**를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-161">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="cd089-162">Pester의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="cd089-162">Improvements to Pester</span></span>

<span data-ttu-id="cd089-163">WMF 5.1에서는 PowerShell과 함께 제공되는 Pester 버전이 3.3.5에서 3.4.0으로 업데이트되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-163">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0.</span></span>
<span data-ttu-id="cd089-164">이 업데이트는 Nano Server에서 Pester가 더 잘 동작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-164">This update enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="cd089-165">GitHub 리포지토리에서 [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md)를 검사하여 Pest의 변경 내용을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd089-165">You can review the changes in Pest by inspecting the [ChangeLog](https://github.com/pester/Pester/blob/master/CHANGELOG.md) in the GitHub repository.</span></span>
