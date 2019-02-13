---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 향상된 DSC
ms.openlocfilehash: 92f82d62550e105a187fd7c0c58b49367c646a7e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679630"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="d4ea7-103">WMF 5.1에서 DSC(필요한 상태 구성)의 개선 사항</span><span class="sxs-lookup"><span data-stu-id="d4ea7-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="d4ea7-104">향상된 DSC 클래스 리소스</span><span class="sxs-lookup"><span data-stu-id="d4ea7-104">DSC class resource improvements</span></span>

<span data-ttu-id="d4ea7-105">WMF 5.1에서 다음과 같은 알려진 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="d4ea7-106">클래스 기반 DSC 리소스의 Get() 함수에서 복합/해시 테이블 형식을 반환하는 경우 Get-DscConfiguration에서 빈 값(null) 또는 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="d4ea7-107">DSC 구성에 RunAs 자격 증명이 사용된 경우 Get-DscConfiguration에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="d4ea7-108">복합 구성에서는 클래스 기반 리소스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="d4ea7-109">클래스 기반 리소스에 자체 형식의 속성이 있는 경우 Start-DscConfiguration이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="d4ea7-110">클래스 기반 리소스를 단독 리소스로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="d4ea7-111">향상된 DSC 리소스 디버깅</span><span class="sxs-lookup"><span data-stu-id="d4ea7-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="d4ea7-112">WMF 5.0에서 PowerShell 디버거는 클래스 기반 리소스 메서드(Get/Set/Test)에서 바로 중지되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span>
<span data-ttu-id="d4ea7-113">WMF 5.1에서는 디버거가 MOF 기반 리소스 메서드와 동일하게 클래스 기반 리소스 메서드에서 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="d4ea7-114">DSC 끌어오기 클라이언트가 TLS 1.1 및 TLS 1.2 지원</span><span class="sxs-lookup"><span data-stu-id="d4ea7-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="d4ea7-115">기존에 DSC 끌어오기 클라이언트는 HTTPS 연결을 통해 SSL3.0 및 TLS1.0만 지원했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span>
<span data-ttu-id="d4ea7-116">더 안전한 프로토콜을 사용하도록 하는 경우 끌어오기 클라이언트의 작동이 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span>
<span data-ttu-id="d4ea7-117">WMF 5.1에서는 DSC 끌어오기 클라이언트가 SSL 3.0을 더 이상 지원하지 않고 더 안전한 TLS 1.1 및 TLS 1.2 프로토콜을 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="d4ea7-118">향상된 끌어오기 서버 등록</span><span class="sxs-lookup"><span data-stu-id="d4ea7-118">Improved pull server registration</span></span>

<span data-ttu-id="d4ea7-119">이전 버전의 WMF에서는 ESENT 데이터베이스를 사용하는 동안 DSC 끌어오기 서버에 동시 등록/보고 요청을 하는 경우 LCM이 등록 및/또는 보고에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span>
<span data-ttu-id="d4ea7-120">이러한 경우 끌어오기 서버의 이벤트 로그에 "이미 사용 중인 인스턴스 이름" 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span>
<span data-ttu-id="d4ea7-121">이는 다중 스레드 시나리오에서 잘못된 패턴을 사용하여 ESENT 데이터베이스에 액세스하기 때문이었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-121">This was due to an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span>
<span data-ttu-id="d4ea7-122">WMF 5.1에서는 이 문제가 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-122">In WMF 5.1, this issue has been fixed.</span></span>
<span data-ttu-id="d4ea7-123">WMF 5.1에서는 동시 등록 또는 보고(ESENT 데이터베이스 포함)가 올바로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span>
<span data-ttu-id="d4ea7-124">이 문제는 ESENT 데이터베이스에만 적용되고 OLEDB 데이터베이스에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="d4ea7-125">ESENT 데이터베이스 인스턴스에 순환 로그 사용</span><span class="sxs-lookup"><span data-stu-id="d4ea7-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="d4ea7-126">이전 버전의 DSC-PullServer에서는 데이터베이스 인스턴스가 순환 로깅 없이 만들어지므로 ESENT 데이터베이스 로그 파일이 끌어오기 서버의 디스크 공간을 가득 채웠습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver becouse the database instance was being created without circular logging.</span></span> <span data-ttu-id="d4ea7-127">이 릴리스에서는 끌어오기 서버의 web.config를 사용하여 인스턴스의 순환 로깅 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="d4ea7-128">기본적으로 CircularLogging은 TRUE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-128">By default CircularLogging is set to TRUE.</span></span>

```
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="d4ea7-129">부분 구성 명명 규칙 끌어오기</span><span class="sxs-lookup"><span data-stu-id="d4ea7-129">Pull partial configuration naming convention</span></span>

<span data-ttu-id="d4ea7-130">이전 릴리스에서는 부분 구성에 대한 명명 규칙에 따라 끌어오기 서버/서비스의 MOF 파일 이름이 로컬 구성 관리자 설정에 지정된 부분 구성 이름과 일치하여 MOF 파일에 포함된 구성 이름과 일치해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-130">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="d4ea7-131">아래 스냅숏을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-131">See the snapshots below:</span></span>

- <span data-ttu-id="d4ea7-132">노드가 수신할 수 있는 부분 구성을 정의하는 로컬 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-132">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

![샘플 메타 구성](../images/MetaConfigPartialOne.png)

- <span data-ttu-id="d4ea7-134">샘플 부분 구성 정의</span><span class="sxs-lookup"><span data-stu-id="d4ea7-134">Sample partial configuration definition</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

- <span data-ttu-id="d4ea7-135">생성된 MOF 파일에 포함된 ‘ConfigurationName’</span><span class="sxs-lookup"><span data-stu-id="d4ea7-135">'ConfigurationName' embedded in the generated MOF file.</span></span>

![생성된 mof 파일 샘플](../images/PartialGeneratedMof.png)

- <span data-ttu-id="d4ea7-137">풀 구성 리포지토리의 FileName</span><span class="sxs-lookup"><span data-stu-id="d4ea7-137">FileName in the pull configuration repository</span></span>

![구성 리포지토리의 FileName](../images/PartialInConfigRepository.png)

<span data-ttu-id="d4ea7-139">Azure 자동화 서비스 이름은 MOF 파일을 `<ConfigurationName>.<NodeName>.mof`로 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-139">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="d4ea7-140">따라서 아래 구성은 PartialOne.localhost.mof로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-140">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

<span data-ttu-id="d4ea7-141">따라서 Azure 자동화 서비스에서 부분 구성 중 하나를 끌어올 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-141">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

```powershell
Configuration PartialOne
{
    Node('localhost')
    {
        File test
        {
            DestinationPath = "$env:TEMP\partialconfigexample.txt"
            Contents = 'Partial Config Example'
        }
    }
}
PartialOne
```

<span data-ttu-id="d4ea7-142">WMF 5.1에서는 끌어오기 서버/서비스의 부분 구성을 `<ConfigurationName>.<NodeName>.mof`로 명명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-142">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span>
<span data-ttu-id="d4ea7-143">또한 컴퓨터가 끌어오기 서버/서비스에서 단일 구성을 끌어오는 경우 끌어오기 서버 구성 리포지토리의 구성 파일에 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-143">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span>
<span data-ttu-id="d4ea7-144">이러한 명명 유연성을 통해 노드를 Azure Automation 서비스로 부분적으로 관리할 수 있습니다. 이 경우 노드의 일부 구성을 Azure Automation DSC에서 가져오고 부분 구성을 로컬로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-144">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

<span data-ttu-id="d4ea7-145">아래 메타 구성은 노드를 로컬뿐 아니라 Azure Automation 서비스에서 관리하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-145">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

```powershell
[DscLocalConfigurationManager()]
Configuration RegistrationMetaConfig
{
    Settings
    {
        RefreshFrequencyMins = 30
        RefreshMode = "PULL"
    }

    ConfigurationRepositoryWeb web
    {
        ServerURL =  $endPoint
        RegistrationKey = $registrationKey
        ConfigurationNames = $configurationName
    }

    # Partial configuration managed by Azure Automation service.
    PartialConfiguration PartialConfigurationManagedByAzureAutomation
    {
        ConfigurationSource = "[ConfigurationRepositoryWeb]Web"
    }

    # This partial configuration is managed locally.
    PartialConfiguration OnPremisesConfig
    {
        RefreshMode = "PUSH"
        ExclusiveResources = @("Script")
    }

}

RegistrationMetaConfig
Set-DscLocalConfigurationManager -Path .\RegistrationMetaConfig -Verbose
```

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="d4ea7-146">DSC 복합 리소스와 함께 PsDscRunAsCredential 사용</span><span class="sxs-lookup"><span data-stu-id="d4ea7-146">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="d4ea7-147">[*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser)을 DSC [복합](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) 리소스와 함께 사용할 수 있도록 지원을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-147">We have added support for using [*PsDscRunAsCredential*](https://msdn.microsoft.com/cs-cz/powershell/dsc/runasuser) with DSC [Composite](https://msdn.microsoft.com/powershell/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="d4ea7-148">이제 구성 내에서 복합 리소스를 사용할 때 PsDscRunAsCredential 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-148">You can now specify a value for PsDscRunAsCredential when using composite resources inside configurations.</span></span>
<span data-ttu-id="d4ea7-149">이 값을 지정할 경우 모든 리소스가 복합 리소스 내에서 RunAs 사용자로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-149">When specified, all resources run inside a composite resource as a RunAs user.</span></span>
<span data-ttu-id="d4ea7-150">복합 리소스가 다른 복합 리소스를 호출하는 경우에도 모든 리소스가 RunAs 사용자로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-150">If a composite resource calls another composite resource, all of its resources are also executed as RunAs user.</span></span>
<span data-ttu-id="d4ea7-151">RunAs 자격 증명은 복합 리소스 계층 구조의 모든 수준에 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-151">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span>
<span data-ttu-id="d4ea7-152">복합 리소스 내의 리소스가 PsDscRunAsCredential의 고유한 값을 지정하는 경우 구성 컴파일 중 병합 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-152">If any resource inside a composite resource specifies its own value for PsDscRunAsCredential, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="d4ea7-153">이 예제에서는 PSDesiredStateConfiguration 모듈에 포함된 [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) 복합 리소스와 함께 사용하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-153">This example shows usage with [WindowsFeatureSet](https://msdn.microsoft.com/powershell/wmf/dsc_newresources) composite resource included in PSDesiredStateConfiguration module.</span></span>

```powershell
Configuration InstallWindowsFeature
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    Node $AllNodes.NodeName
    {
        WindowsFeatureSet features
        {
            Name = @("Telnet-Client","SNMP-Service")
            Ensure = "Present"
            IncludeAllSubFeature = $true
            PsDscRunAsCredential = Get-Credential
        }
    }
}

$configData = @{
    AllNodes = @(
        @{
            NodeName             = 'localhost'
            PSDscAllowDomainUser = $true
            CertificateFile      = 'C:\publicKeys\targetNode.cer'
            Thumbprint           = '7ee7f09d-4be0-41aa-a47f-96b9e3bdec25'
        }
    )
}

InstallWindowsFeature -ConfigurationData $configData
```

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="d4ea7-154">DSC 모듈 및 구성 서명 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="d4ea7-154">DSC module and configuration signing validations</span></span>

<span data-ttu-id="d4ea7-155">DSC에서는 구성 및 모듈이 끌어오기 서버에서 관리되는 컴퓨터로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-155">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span>
<span data-ttu-id="d4ea7-156">끌어오기 서버가 손상되는 경우 공격자가 끌어오기 서버의 구성 및 모듈을 수정하고 모든 관리되는 노드로 배포하여 모든 노드를 손상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-156">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes, compromising all of them.</span></span>

<span data-ttu-id="d4ea7-157">WMF 5.1의 DSC에서는 카탈로그 및 구성(.MOF) 파일에 있는 디지털 서명의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-157">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span>
<span data-ttu-id="d4ea7-158">이 기능은 노드에서 신뢰할 수 있는 서명자가 서명하지 않았거나 신뢰할 수 있는 서명자가 서명한 후 변조된 구성 또는 모듈 파일을 실행하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-158">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="d4ea7-159">구성 및 모듈에 서명하는 방법</span><span class="sxs-lookup"><span data-stu-id="d4ea7-159">How to sign configuration and module</span></span>

***
* <span data-ttu-id="d4ea7-160">구성 파일 (합니다. Mof): 기존 PowerShell cmdlet [Set-authenticodesignature](https://technet.microsoft.com/library/hh849819.aspx) MOF 파일 서명을 지원 하도록 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-160">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) is extended to support signing of MOF files.</span></span>
* <span data-ttu-id="d4ea7-161">모듈 다음 단계를 사용 하 여 해당 모듈 카탈로그에 서명 하 여 모듈 서명을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-161">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
    1. <span data-ttu-id="d4ea7-162">카탈로그 파일을 만듭니다. 카탈로그 파일에는 암호화 해시 또는 지 문의 컬렉션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-162">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span>
       <span data-ttu-id="d4ea7-163">각 지문은 모듈에 포함된 파일에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-163">Each thumbprint corresponds to a file that is included in the module.</span></span>
       <span data-ttu-id="d4ea7-164">사용자가 모듈의 카탈로그 파일을 만들 수 있도록 지원하는 새로운 [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-164">The new cmdlet [New-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx), has been added to enable users to create a catalog file for their module.</span></span>
    2. <span data-ttu-id="d4ea7-165">카탈로그 파일에 서명 합니다. 사용 하 여 [Set-authenticodesignature](https://technet.microsoft.com/library/hh849819.aspx) 카탈로그 파일에 서명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-165">Sign the catalog file: Use [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) to sign the catalog file.</span></span>
    3. <span data-ttu-id="d4ea7-166">카탈로그 파일을 모듈 폴더 내에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-166">Place the catalog file inside the module folder.</span></span>
<span data-ttu-id="d4ea7-167">규칙에 따라 모듈 카탈로그 파일은 모듈과 이름이 같은 모듈 폴더에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-167">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="d4ea7-168">서명 유효성 검사를 사용하도록 설정하는 LocalConfigurationManager 설정</span><span class="sxs-lookup"><span data-stu-id="d4ea7-168">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="d4ea7-169">끌어오기</span><span class="sxs-lookup"><span data-stu-id="d4ea7-169">Pull</span></span>

<span data-ttu-id="d4ea7-170">노드의 LocalConfigurationManager는 현재 설정에 따라 모듈 및 구성의 서명 유효성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-170">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span>
<span data-ttu-id="d4ea7-171">기본적으로 서명 유효성 검사를 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-171">By default, signature validation is disabled.</span></span>
<span data-ttu-id="d4ea7-172">서명 유효성 검사를 사용하도록 설정하려면 아래 표시된 노드의 메타 구성 정의에 'SignatureValidation' 블록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-172">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PULL'
    }

    ConfigurationRepositoryWeb pullserver{
      ConfigurationNames = 'sql'
      ServerURL = 'http://localhost:8080/PSDSCPullServer/PSDSCPullServer.svc'
      AllowUnsecureConnection = $true
      RegistrationKey = 'd6750ff1-d8dd-49f7-8caf-7471ea9793fc' # Replace this with correct registration key.
    }
    SignatureValidation validations{
        # If the TrustedStorePath property is provided then LCM will use the custom path. Otherwise, the LCM will use default trusted store path (Cert:\LocalMachine\DSCStore) to find the signing certificate.
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType = 'Configuration','Module'         # This is a list of DSC artifacts, for which LCM need to verify their digital signature before executing them on the node.
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

<span data-ttu-id="d4ea7-173">노드에서 위의 메타 구성을 설정하면 다운로드된 구성 및 모듈에서 서명 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-173">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span>
<span data-ttu-id="d4ea7-174">로컬 구성 관리자는 다음 단계를 수행하여 디지털 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-174">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="d4ea7-175">구성 파일(.MOF)의 서명이 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-175">Verify the signature on a configuration file (.MOF) is valid.</span></span>
   <span data-ttu-id="d4ea7-176">5.1에서 MOF 서명 유효성 검사를 지원하도록 확장된 PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-176">It uses the PowerShell cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx), which is extended in 5.1 to support MOF signature validation.</span></span>
2. <span data-ttu-id="d4ea7-177">서명자에게 권한을 부여한 인증 기관을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-177">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="d4ea7-178">구성의 모듈/리소스 종속성을 임시 위치로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-178">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="d4ea7-179">모듈 내에 포함된 카탈로그의 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-179">Verify the signature of the catalog included inside the module.</span></span>
    * <span data-ttu-id="d4ea7-180">`<moduleName>.cat` 파일을 찾고 [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx) cmdlet을 사용하여 해당 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-180">Find a `<moduleName>.cat` file and verify its signature using the cmdlet  [Get-AuthenticodeSignature](https://technet.microsoft.com/library/hh849805.aspx).</span></span>
    * <span data-ttu-id="d4ea7-181">서명자를 인증한 인증 기관을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-181">Verify the certification authority that authenticated the signer is trusted.</span></span>
    * <span data-ttu-id="d4ea7-182">새 [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx) cmdlet을 사용하여 모듈의 콘텐츠가 변조되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-182">Verify the content of the modules has not been tampered using the new cmdlet [Test-FileCatalog](https://technet.microsoft.com/library/cc732148.aspx).</span></span>
5. <span data-ttu-id="d4ea7-183">모듈을 $env:ProgramFiles\WindowsPowerShell\Modules\에 설치</span><span class="sxs-lookup"><span data-stu-id="d4ea7-183">Install-Module to $env:ProgramFiles\WindowsPowerShell\Modules\\</span></span>
6. <span data-ttu-id="d4ea7-184">구성 처리</span><span class="sxs-lookup"><span data-stu-id="d4ea7-184">Process configuration</span></span>

> <span data-ttu-id="d4ea7-185">참고: 모듈 카탈로그 및 구성의 서명 유효성 검사는 시스템에 구성을 처음으로 적용할 때나 모듈을 다운로드하여 설치할 때만 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-185">Note: Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
<span data-ttu-id="d4ea7-186">일관성 검사에서는 Current.mof 또는 해당 모듈 종속성의 서명 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-186">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span>
<span data-ttu-id="d4ea7-187">끌어오기 서버에서 끌어온 구성에 서명이 되어 있지 않은 등 어느 단계에서든 유효성 검사가 실패하면 구성 처리가 종료되고 아래와 같은 오류가 표시되며 모든 임시 파일이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-187">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![샘플 오류 출력 구성](../images/PullUnsignedConfigFail.png)

<span data-ttu-id="d4ea7-189">마찬가지로 카탈로그에 서명이 되어 있지 않은 모듈을 끌어오면 다음 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-189">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![샘플 오류 출력 모듈](../images/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="d4ea7-191">푸시</span><span class="sxs-lookup"><span data-stu-id="d4ea7-191">Push</span></span>

<span data-ttu-id="d4ea7-192">푸시를 사용하여 전달된 구성은 노드로 전달되기 전에 해당 소스에서 변조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-192">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span>
<span data-ttu-id="d4ea7-193">로컬 구성 관리자는 푸시되거나 게시된 구성에 대해 비슷한 서명 유효성 검사 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-193">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span>
<span data-ttu-id="d4ea7-194">다음은 푸시에 대한 서명 유효성 검사의 완전한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-194">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="d4ea7-195">노드에서 서명 유효성 검사를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-195">Enable signature validation on the node.</span></span>

```powershell
[DSCLocalConfigurationManager()]
Configuration EnableSignatureValidation
{
    Settings
    {
        RefreshMode = 'PUSH'
    }
    SignatureValidation validations{
        TrustedStorePath = 'Cert:\LocalMachine\DSCStore'
        SignedItemType =  'Configuration','Module'
    }

}
EnableSignatureValidation
Set-DscLocalConfigurationManager -Path .\EnableSignatureValidation -Verbose
```

- <span data-ttu-id="d4ea7-196">샘플 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-196">Create a sample configuration file.</span></span>

```powershell
# Sample configuration
Configuration Test
{

    File foo
    {
        DestinationPath =  "$env:TEMP\signingTest.txt"
        Contents = "ABC"
    }
}
Test
```

- <span data-ttu-id="d4ea7-197">서명되지 않은 구성 파일을 노드로 푸시해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-197">Try pushing the unsigned configuration file in to the node.</span></span>

```powershell
Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
```

![ErrorUnsignedMofPushed](../images/PushUnsignedMof.png)

- <span data-ttu-id="d4ea7-199">코드 서명 인증서를 사용하여 구성 파일에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-199">Sign the configuration file using code-signing certificate.</span></span>

![SignMofFile](../images/SignMofFile.png)

- <span data-ttu-id="d4ea7-201">서명된 MOF 파일을 푸시해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d4ea7-201">Try pushing the signed MOF file.</span></span>

![SignMofFile](../images/PushSignedMof.png)
