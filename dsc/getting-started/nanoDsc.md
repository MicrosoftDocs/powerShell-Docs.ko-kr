---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC on Nano Server 사용
ms.openlocfilehash: fb826455c21833ae4c8dc2ecd731ffce6bf7eaba
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734603"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="5b37e-103">DSC on Nano Server 사용</span><span class="sxs-lookup"><span data-stu-id="5b37e-103">Using DSC on Nano Server</span></span>

> <span data-ttu-id="5b37e-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="5b37e-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="5b37e-105">**DSC on Nano Server**는 Windows Server 2016 미디어의 `NanoServer\Packages` 폴더에 있는 선택적 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-105">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="5b37e-106">이 패키지는 **Microsoft-NanoServer-DSC-Package**를 **New-NanoServerImage** 함수의 **Packages** 매개 변수 값으로 지정하여 Nano Server에 대한 VHD를 만들 때 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-106">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="5b37e-107">예를 들어 가상 컴퓨터에 대한 VHD를 만드는 경우 다음과 같은 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-107">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="5b37e-108">Nano Server 설치 및 사용과 PowerShell 원격으로 Nano Server를 관리하는 방법은 [Getting Started with Nano Server(Nano Server 시작)](/windows-server/get-started/getting-started-with-nano-server)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5b37e-108">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="5b37e-109">Nano Server에서 사용할 수 있는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="5b37e-109">DSC features available on Nano Server</span></span>

<span data-ttu-id="5b37e-110">Nano Server는 처음 사용자용 Windows Server에 비해 제한된 일부 API만 지원하기 때문에 당분간은 전체 SKU에서 동작하는 완전한 기능을 하는 패리티가 DSC on Nano Server에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-110">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="5b37e-111">DSC on Nano Server는 개발 중이므로 아직 모든 기능이 완성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-111">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="5b37e-112">다음 DSC 기능은 현재 Nano Server에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-112">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="5b37e-113">밀어넣기 및 끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="5b37e-113">Both push and pull modes</span></span>

- <span data-ttu-id="5b37e-114">다음을 포함하여 Windows Server 전체 버전에 있는 모든 DSC cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5b37e-114">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="5b37e-115">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5b37e-115">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="5b37e-116">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="5b37e-116">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="5b37e-117">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="5b37e-117">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="5b37e-118">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="5b37e-118">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="5b37e-119">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-119">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="5b37e-120">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-120">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="5b37e-121">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-121">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="5b37e-122">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-122">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="5b37e-123">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-123">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="5b37e-124">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-124">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="5b37e-125">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b37e-125">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="5b37e-126">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="5b37e-126">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="5b37e-127">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="5b37e-127">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="5b37e-128">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="5b37e-128">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="5b37e-129">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="5b37e-129">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource?view=powershell-6)
- [<span data-ttu-id="5b37e-130">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="5b37e-130">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="5b37e-131">New-DSCCheckSum</span><span class="sxs-lookup"><span data-stu-id="5b37e-131">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="5b37e-132">구성 컴파일([DSC 구성](../configurations/configurations.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-132">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="5b37e-133">**문제:** 구성 컴파일 중 암호 암호화([MOF 파일 보안](../pull-server/secureMOF.md) 참조)가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-133">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="5b37e-134">메타 구성 컴파일([로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-134">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="5b37e-135">사용자 컨텍스트에서 리소스 실행([사용자 자격 증명을 사용하여 DSC 실행(RunAs)](../configurations/runAsUser.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-135">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="5b37e-136">클래스 기반 리소스([PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](/previous-versions//dn948461(v=technet.10)) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-136">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="5b37e-137">DSC 리소스 디버깅([DSC 리소스 디버그](../troubleshooting/debugResource.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-137">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="5b37e-138">**문제:** 리소스가 PsDscRunAsCredential을 사용 중인 경우 작동하지 않습니다([사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="5b37e-138">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="5b37e-139">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="5b37e-139">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="5b37e-140">리소스 버전 관리</span><span class="sxs-lookup"><span data-stu-id="5b37e-140">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="5b37e-141">끌어오기 클라이언트(구성 및 리소스)([구성 이름을 사용하여 끌어오기 클라이언트 설정](../pull-server/pullClientConfigNames.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-141">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="5b37e-142">부분 구성(끌어오기 및 밀어넣기)</span><span class="sxs-lookup"><span data-stu-id="5b37e-142">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="5b37e-143">끌어오기 서버에 보고</span><span class="sxs-lookup"><span data-stu-id="5b37e-143">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="5b37e-144">MOF 암호화</span><span class="sxs-lookup"><span data-stu-id="5b37e-144">MOF encryption</span></span>

- <span data-ttu-id="5b37e-145">이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="5b37e-145">Event logging</span></span>

- <span data-ttu-id="5b37e-146">Azure 자동화 DSC 보고</span><span class="sxs-lookup"><span data-stu-id="5b37e-146">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="5b37e-147">올바르게 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="5b37e-147">Resources that are fully functional</span></span>

- <span data-ttu-id="5b37e-148">**Archive**</span><span class="sxs-lookup"><span data-stu-id="5b37e-148">**Archive**</span></span>
- <span data-ttu-id="5b37e-149">**Environment**</span><span class="sxs-lookup"><span data-stu-id="5b37e-149">**Environment**</span></span>
- <span data-ttu-id="5b37e-150">**File**</span><span class="sxs-lookup"><span data-stu-id="5b37e-150">**File**</span></span>
- <span data-ttu-id="5b37e-151">**Log**</span><span class="sxs-lookup"><span data-stu-id="5b37e-151">**Log**</span></span>
- <span data-ttu-id="5b37e-152">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="5b37e-152">**ProcessSet**</span></span>
- <span data-ttu-id="5b37e-153">**Registry**</span><span class="sxs-lookup"><span data-stu-id="5b37e-153">**Registry**</span></span>
- <span data-ttu-id="5b37e-154">**Script**</span><span class="sxs-lookup"><span data-stu-id="5b37e-154">**Script**</span></span>
- <span data-ttu-id="5b37e-155">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="5b37e-155">**WindowsPackageCab**</span></span>
- <span data-ttu-id="5b37e-156">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="5b37e-156">**WindowsProcess**</span></span>
- <span data-ttu-id="5b37e-157">**WaitForAll**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-157">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="5b37e-158">**WaitForAny**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-158">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
- <span data-ttu-id="5b37e-159">**WaitForSome**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="5b37e-159">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="5b37e-160">부분적으로 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="5b37e-160">Resources that are partially functional</span></span>
- <span data-ttu-id="5b37e-161">**그룹**</span><span class="sxs-lookup"><span data-stu-id="5b37e-161">**Group**</span></span>
- <span data-ttu-id="5b37e-162">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="5b37e-162">**GroupSet**</span></span>

  <span data-ttu-id="5b37e-163">**문제:** 특정 인스턴스를 두 번 호출하는 경우(동일한 구성을 두 번 실행) 위의 리소스가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-163">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

- <span data-ttu-id="5b37e-164">**Service**</span><span class="sxs-lookup"><span data-stu-id="5b37e-164">**Service**</span></span>
- <span data-ttu-id="5b37e-165">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="5b37e-165">**ServiceSet**</span></span>

  <span data-ttu-id="5b37e-166">**문제:** 서비스 시작/중지(상태) 서비스에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-166">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="5b37e-167">시작 유형, 자격 증명, 설명 등과 같은 다른 서비스 특성을 변경하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-167">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="5b37e-168">발생하는 오류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-168">The error thrown is similar to:</span></span>

  <span data-ttu-id="5b37e-169">*유형[management.managementobject]을 찾을 수 없습니다. 이 유형이 포함된 어셈블리가 로드되어 있는지 검증하세요.*</span><span class="sxs-lookup"><span data-stu-id="5b37e-169">*Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.*</span></span>

- <span data-ttu-id="5b37e-170">작동하지 않는 리소스</span><span class="sxs-lookup"><span data-stu-id="5b37e-170">Resources that are not functional</span></span>
- <span data-ttu-id="5b37e-171">**User**</span><span class="sxs-lookup"><span data-stu-id="5b37e-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="5b37e-172">Nano Server에서 사용할 수 없는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="5b37e-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="5b37e-173">다음 DSC 기능은 현재 Nano Server에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="5b37e-174">암호화된 암호를 사용한 MOF 문서 암호 해독</span><span class="sxs-lookup"><span data-stu-id="5b37e-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="5b37e-175">끌어오기 서버--현재는 Nano Server에서 끌어오기 서버를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="5b37e-176">동작 기능 목록에 없는 모든 기능</span><span class="sxs-lookup"><span data-stu-id="5b37e-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="5b37e-177">Nano Server에서 사용자 지정 DSC 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="5b37e-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="5b37e-178">Nano Server에서 사용할 수 있는 Windows API 집합과 CLR 라이브러리가 한정되어 있기 때문에 Windows 전체 CLR 버전에서 동작하는 DSC 리소스가 Nano Server에서 동작하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5b37e-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="5b37e-179">DSC 사용자 지정 리소스를 프로덕션 환경에 배포하기 전에 엔드투엔드 테스트를 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="5b37e-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b37e-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5b37e-180">See Also</span></span>

- [<span data-ttu-id="5b37e-181">Nano Server 시작</span><span class="sxs-lookup"><span data-stu-id="5b37e-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
