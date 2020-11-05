---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC on Nano Server 사용
description: DSC는 Windows Nano Server용 VHD를 만들 때 설치할 수 있는 선택적 패키지입니다.
ms.openlocfilehash: 18585323359abd85515d4db194dae4adbad7c3d8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647078"
---
# <a name="using-dsc-on-nano-server"></a><span data-ttu-id="187ac-104">DSC on Nano Server 사용</span><span class="sxs-lookup"><span data-stu-id="187ac-104">Using DSC on Nano Server</span></span>

> <span data-ttu-id="187ac-105">적용 대상: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="187ac-105">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="187ac-106">**DSC on Nano Server** 는 Windows Server 2016 미디어의 `NanoServer\Packages` 폴더에 있는 선택적 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-106">**DSC on Nano Server** is an optional package in the `NanoServer\Packages` folder of the Windows Server 2016 media.</span></span> <span data-ttu-id="187ac-107">이 패키지는 **Microsoft-NanoServer-DSC-Package** 를 **New-NanoServerImage** 함수의 **Packages** 매개 변수 값으로 지정하여 Nano Server에 대한 VHD를 만들 때 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-107">The package can be installed when you create a VHD for a Nano Server by specifying **Microsoft-NanoServer-DSC-Package** as the value of the **Packages** parameter of the **New-NanoServerImage** function.</span></span> <span data-ttu-id="187ac-108">예를 들어 가상 컴퓨터에 대한 VHD를 만드는 경우 다음과 같은 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-108">For example, if you are creating a VHD for a virtual machine, the command would look like the following:</span></span>

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

<span data-ttu-id="187ac-109">Nano Server 설치 및 사용과 PowerShell 원격으로 Nano Server를 관리하는 방법은 [Getting Started with Nano Server(Nano Server 시작)](/windows-server/get-started/getting-started-with-nano-server)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="187ac-109">For information about installing and using Nano Server, as well as how to manage Nano Server with PowerShell Remoting, see [Getting Started with Nano Server](/windows-server/get-started/getting-started-with-nano-server).</span></span>

## <a name="dsc-features-available-on-nano-server"></a><span data-ttu-id="187ac-110">Nano Server에서 사용할 수 있는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="187ac-110">DSC features available on Nano Server</span></span>

<span data-ttu-id="187ac-111">Nano Server는 처음 사용자용 Windows Server에 비해 제한된 일부 API만 지원하기 때문에 당분간은 전체 SKU에서 동작하는 완전한 기능을 하는 패리티가 DSC on Nano Server에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-111">Because Nano Server supports only a limited set of APIs compared to a full version of Windows Server, DSC on Nano Server does not have full functional parity with DSC running on full SKUs for the time being.</span></span> <span data-ttu-id="187ac-112">DSC on Nano Server는 개발 중이므로 아직 모든 기능이 완성되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-112">DSC on Nano Server is in active development and is not yet feature complete.</span></span>

<span data-ttu-id="187ac-113">다음 DSC 기능은 현재 Nano Server에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-113">The following DSC features are currently available on Nano Server:</span></span>

<span data-ttu-id="187ac-114">밀어넣기 및 끌어오기 모드</span><span class="sxs-lookup"><span data-stu-id="187ac-114">Both push and pull modes</span></span>

- <span data-ttu-id="187ac-115">다음을 포함하여 Windows Server 전체 버전에 있는 모든 DSC cmdlet:</span><span class="sxs-lookup"><span data-stu-id="187ac-115">All DSC cmdlets that exist on a full version of Windows Server, including the following:</span></span>
- [<span data-ttu-id="187ac-116">Get DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="187ac-116">Get-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [<span data-ttu-id="187ac-117">Set-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="187ac-117">Set-DscLocalConfigurationManager</span></span>](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [<span data-ttu-id="187ac-118">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="187ac-118">Enable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [<span data-ttu-id="187ac-119">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="187ac-119">Disable-DscDebug</span></span>](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [<span data-ttu-id="187ac-120">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-120">Start-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [<span data-ttu-id="187ac-121">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-121">Stop-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [<span data-ttu-id="187ac-122">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-122">Get-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [<span data-ttu-id="187ac-123">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-123">Test-DscConfiguration</span></span>](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [<span data-ttu-id="187ac-124">Publish-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-124">Publish-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [<span data-ttu-id="187ac-125">Update-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-125">Update-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [<span data-ttu-id="187ac-126">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="187ac-126">Restore-DscConfiguration</span></span>](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [<span data-ttu-id="187ac-127">Remove-DscConfigurationDocument</span><span class="sxs-lookup"><span data-stu-id="187ac-127">Remove-DscConfigurationDocument</span></span>](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [<span data-ttu-id="187ac-128">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="187ac-128">Get-DscConfigurationStatus</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [<span data-ttu-id="187ac-129">Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="187ac-129">Invoke-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [<span data-ttu-id="187ac-130">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="187ac-130">Find-DscResource</span></span>](/powershell/module/powershellget/find-dscresource)
- [<span data-ttu-id="187ac-131">Get-DscResource</span><span class="sxs-lookup"><span data-stu-id="187ac-131">Get-DscResource</span></span>](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [<span data-ttu-id="187ac-132">New-DSCCheckSum</span><span class="sxs-lookup"><span data-stu-id="187ac-132">New-DscChecksum</span></span>](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- <span data-ttu-id="187ac-133">구성 컴파일([DSC 구성](../configurations/configurations.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-133">Compiling configurations (see [DSC configurations](../configurations/configurations.md))</span></span>

  <span data-ttu-id="187ac-134">**문제:** 구성 컴파일 중 암호 암호화( [MOF 파일 보안](../pull-server/secureMOF.md) 참조)가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-134">**Issue:** Password encryption (see [Securing the MOF File](../pull-server/secureMOF.md)) during configuration compilation doesn't work.</span></span>

- <span data-ttu-id="187ac-135">메타 구성 컴파일([로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-135">Compiling metaconfigurations (see [Configuring the Local Configuration Manager](../managing-nodes/metaConfig.md))</span></span>

- <span data-ttu-id="187ac-136">사용자 컨텍스트에서 리소스 실행([사용자 자격 증명을 사용하여 DSC 실행(RunAs)](../configurations/runAsUser.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-136">Running a resource under user context (see [Running DSC with user credentials (RunAs)](../configurations/runAsUser.md))</span></span>

- <span data-ttu-id="187ac-137">클래스 기반 리소스([PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](/previous-versions//dn948461(v=technet.10)) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-137">Class-based resources (see [Writing a custom DSC resource with PowerShell classes](/previous-versions//dn948461(v=technet.10)))</span></span>

- <span data-ttu-id="187ac-138">DSC 리소스 디버깅([DSC 리소스 디버그](../troubleshooting/debugResource.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-138">Debugging of DSC resources (see [Debugging DSC resources](../troubleshooting/debugResource.md))</span></span>

  <span data-ttu-id="187ac-139">**문제:** 리소스가 PsDscRunAsCredential을 사용 중인 경우 작동하지 않습니다([사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md) 참조).</span><span class="sxs-lookup"><span data-stu-id="187ac-139">**Issue:** Doesn't work if a resource is using PsDscRunAsCredential (see [Running DSC with user credentials](../configurations/runAsUser.md))</span></span>

- [<span data-ttu-id="187ac-140">노드 간 종속성 지정</span><span class="sxs-lookup"><span data-stu-id="187ac-140">Specifying cross-node dependencies</span></span>](../configurations/crossNodeDependencies.md)

- [<span data-ttu-id="187ac-141">리소스 버전 관리</span><span class="sxs-lookup"><span data-stu-id="187ac-141">Resource versioning</span></span>](../configurations/sxsResource.md)

- <span data-ttu-id="187ac-142">끌어오기 클라이언트(구성 및 리소스)([구성 이름을 사용하여 끌어오기 클라이언트 설정](../pull-server/pullClientConfigNames.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-142">Pull client (configurations & resources) (see [Setting up a pull client using configuration names](../pull-server/pullClientConfigNames.md))</span></span>

- [<span data-ttu-id="187ac-143">부분 구성(끌어오기 및 밀어넣기)</span><span class="sxs-lookup"><span data-stu-id="187ac-143">Partial configurations (pull & push)</span></span>](../pull-server/partialConfigs.md)

- [<span data-ttu-id="187ac-144">끌어오기 서버에 보고</span><span class="sxs-lookup"><span data-stu-id="187ac-144">Reporting to pull server</span></span>](../pull-server/reportServer.md)

- <span data-ttu-id="187ac-145">MOF 암호화</span><span class="sxs-lookup"><span data-stu-id="187ac-145">MOF encryption</span></span>

- <span data-ttu-id="187ac-146">이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="187ac-146">Event logging</span></span>

- <span data-ttu-id="187ac-147">Azure 자동화 DSC 보고</span><span class="sxs-lookup"><span data-stu-id="187ac-147">Azure Automation DSC reporting</span></span>

- <span data-ttu-id="187ac-148">올바르게 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="187ac-148">Resources that are fully functional</span></span>

  - <span data-ttu-id="187ac-149">**보관**</span><span class="sxs-lookup"><span data-stu-id="187ac-149">**Archive**</span></span>
  - <span data-ttu-id="187ac-150">**환경**</span><span class="sxs-lookup"><span data-stu-id="187ac-150">**Environment**</span></span>
  - <span data-ttu-id="187ac-151">**파일**</span><span class="sxs-lookup"><span data-stu-id="187ac-151">**File**</span></span>
  - <span data-ttu-id="187ac-152">**Log**</span><span class="sxs-lookup"><span data-stu-id="187ac-152">**Log**</span></span>
  - <span data-ttu-id="187ac-153">**ProcessSet**</span><span class="sxs-lookup"><span data-stu-id="187ac-153">**ProcessSet**</span></span>
  - <span data-ttu-id="187ac-154">**레지스트리**</span><span class="sxs-lookup"><span data-stu-id="187ac-154">**Registry**</span></span>
  - <span data-ttu-id="187ac-155">**스크립트**</span><span class="sxs-lookup"><span data-stu-id="187ac-155">**Script**</span></span>
  - <span data-ttu-id="187ac-156">**WindowsPackageCab**</span><span class="sxs-lookup"><span data-stu-id="187ac-156">**WindowsPackageCab**</span></span>
  - <span data-ttu-id="187ac-157">**WindowsProcess**</span><span class="sxs-lookup"><span data-stu-id="187ac-157">**WindowsProcess**</span></span>
  - <span data-ttu-id="187ac-158">**WaitForAll** ([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-158">**WaitForAll** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="187ac-159">**WaitForAny** ([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-159">**WaitForAny** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>
  - <span data-ttu-id="187ac-160">**WaitForSome** ([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="187ac-160">**WaitForSome** (see [Specifying cross-node dependencies](../configurations/crossNodeDependencies.md))</span></span>

- <span data-ttu-id="187ac-161">부분적으로 작동하는 리소스</span><span class="sxs-lookup"><span data-stu-id="187ac-161">Resources that are partially functional</span></span>

  - <span data-ttu-id="187ac-162">**그룹**</span><span class="sxs-lookup"><span data-stu-id="187ac-162">**Group**</span></span>
  - <span data-ttu-id="187ac-163">**GroupSet**</span><span class="sxs-lookup"><span data-stu-id="187ac-163">**GroupSet**</span></span>

    <span data-ttu-id="187ac-164">**문제:** 특정 인스턴스를 두 번 호출하는 경우(동일한 구성을 두 번 실행) 위 리소스가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-164">**Issue:** Above resources fail if specific instance is called twice (running the same configuration twice)</span></span>

  - <span data-ttu-id="187ac-165">**서비스**</span><span class="sxs-lookup"><span data-stu-id="187ac-165">**Service**</span></span>
  - <span data-ttu-id="187ac-166">**ServiceSet**</span><span class="sxs-lookup"><span data-stu-id="187ac-166">**ServiceSet**</span></span>

    <span data-ttu-id="187ac-167">**문제:** 서비스 시작/중지(상태)에 대해서만 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-167">**Issue:** Only works for starting/stopping (status) service.</span></span> <span data-ttu-id="187ac-168">시작 유형, 자격 증명, 설명 등과 같은 다른 서비스 특성을 변경하려고 하면 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-168">Fails, if one tries to change other service attributes like startuptype, credentials, description etc..</span></span> <span data-ttu-id="187ac-169">발생하는 오류는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-169">The error thrown is similar to:</span></span>

    ```
    Cannot find type [management.managementobject]: verify that the assembly containing this type is loaded.
    ```

- <span data-ttu-id="187ac-170">작동하지 않는 리소스</span><span class="sxs-lookup"><span data-stu-id="187ac-170">Resources that are not functional</span></span>

  - <span data-ttu-id="187ac-171">**사용자**</span><span class="sxs-lookup"><span data-stu-id="187ac-171">**User**</span></span>

## <a name="dsc-features-not-available-on-nano-server"></a><span data-ttu-id="187ac-172">Nano Server에서 사용할 수 없는 DSC 기능</span><span class="sxs-lookup"><span data-stu-id="187ac-172">DSC features not available on Nano Server</span></span>

<span data-ttu-id="187ac-173">다음 DSC 기능은 현재 Nano Server에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-173">The following DSC features are not currently available on Nano Server:</span></span>

- <span data-ttu-id="187ac-174">암호화된 암호를 사용한 MOF 문서 암호 해독</span><span class="sxs-lookup"><span data-stu-id="187ac-174">Decrypting MOF document with encrypted password(s)</span></span>
- <span data-ttu-id="187ac-175">끌어오기 서버--현재는 Nano Server에서 끌어오기 서버를 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-175">Pull Server--you cannot currently set up a pull server on Nano Server</span></span>
- <span data-ttu-id="187ac-176">동작 기능 목록에 없는 모든 기능</span><span class="sxs-lookup"><span data-stu-id="187ac-176">Anything that is not in the list of feature works</span></span>

## <a name="using-custom-dsc-resources-on-nano-server"></a><span data-ttu-id="187ac-177">Nano Server에서 사용자 지정 DSC 리소스 사용</span><span class="sxs-lookup"><span data-stu-id="187ac-177">Using custom DSC resources on Nano Server</span></span>

<span data-ttu-id="187ac-178">Nano Server에서 사용할 수 있는 Windows API 집합과 CLR 라이브러리가 한정되어 있기 때문에 Windows 전체 CLR 버전에서 동작하는 DSC 리소스가 Nano Server에서 동작하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="187ac-178">Due to a limited sets of Windows APIs and CLR libraries available on Nano Server, DSC resources that work on the full CLR version of Windows do not necessarily work on Nano Server.</span></span>
<span data-ttu-id="187ac-179">DSC 사용자 지정 리소스를 프로덕션 환경에 배포하기 전에 엔드투엔드 테스트를 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="187ac-179">Complete end-to-end testing before deploying any DSC custom resources to a production environment.</span></span>

## <a name="see-also"></a><span data-ttu-id="187ac-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="187ac-180">See Also</span></span>

- [<span data-ttu-id="187ac-181">Nano Server 시작</span><span class="sxs-lookup"><span data-stu-id="187ac-181">Getting Started with Nano Server</span></span>](/windows-server/get-started/getting-started-with-nano-server)
