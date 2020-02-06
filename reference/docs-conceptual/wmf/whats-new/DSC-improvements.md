---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 향상된 DSC
ms.openlocfilehash: d9339ec9f316c4a32c5fa6cb2360c077973ee334
ms.sourcegitcommit: ea7d87a7a56f368e3175219686dfa2870053c644
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76818110"
---
# <a name="improvements-in-desired-state-configuration-dsc-in-wmf-51"></a><span data-ttu-id="d7c2c-103">WMF 5.1에서 DSC(필요한 상태 구성)의 개선 사항</span><span class="sxs-lookup"><span data-stu-id="d7c2c-103">Improvements in Desired State Configuration (DSC) in WMF 5.1</span></span>

## <a name="dsc-class-resource-improvements"></a><span data-ttu-id="d7c2c-104">향상된 DSC 클래스 리소스</span><span class="sxs-lookup"><span data-stu-id="d7c2c-104">DSC class resource improvements</span></span>

<span data-ttu-id="d7c2c-105">WMF 5.1에서 다음과 같은 알려진 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-105">In WMF 5.1, we have fixed the following known issues:</span></span>

- <span data-ttu-id="d7c2c-106">클래스 기반 DSC 리소스의 Get() 함수에서 복합/해시 테이블 형식을 반환하는 경우 Get-DscConfiguration에서 빈 값(null) 또는 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-106">Get-DscConfiguration may return empty values (null) or errors if a complex/hash table type is returned by Get() function of a class-based DSC resource.</span></span>
- <span data-ttu-id="d7c2c-107">DSC 구성에 RunAs 자격 증명이 사용된 경우 Get-DscConfiguration에서 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-107">Get-DscConfiguration returns error if RunAs credential is used in DSC configuration.</span></span>
- <span data-ttu-id="d7c2c-108">복합 구성에서는 클래스 기반 리소스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-108">Class-based resource cannot be used in a composite configuration.</span></span>
- <span data-ttu-id="d7c2c-109">클래스 기반 리소스에 자체 형식의 속성이 있는 경우 Start-DscConfiguration이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-109">Start-DscConfiguration hangs if class-based resource has a property of its own type.</span></span>
- <span data-ttu-id="d7c2c-110">클래스 기반 리소스를 단독 리소스로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-110">Class-based resource cannot be used as an exclusive resource.</span></span>

## <a name="dsc-resource-debugging-improvements"></a><span data-ttu-id="d7c2c-111">향상된 DSC 리소스 디버깅</span><span class="sxs-lookup"><span data-stu-id="d7c2c-111">DSC resource debugging improvements</span></span>

<span data-ttu-id="d7c2c-112">WMF 5.0에서 PowerShell 디버거는 클래스 기반 리소스 메서드(Get/Set/Test)에서 바로 중지되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-112">In WMF 5.0, the PowerShell debugger did not stop at the class-based resource method (Get/Set/Test) directly.</span></span> <span data-ttu-id="d7c2c-113">WMF 5.1에서는 디버거가 MOF 기반 리소스 메서드와 동일하게 클래스 기반 리소스 메서드에서 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-113">In WMF 5.1, the debugger stops at the class-based resource method in the same way as for MOF-based resources methods.</span></span>

## <a name="dsc-pull-client-supports-tls-11-and-tls-12"></a><span data-ttu-id="d7c2c-114">DSC 끌어오기 클라이언트가 TLS 1.1 및 TLS 1.2 지원</span><span class="sxs-lookup"><span data-stu-id="d7c2c-114">DSC pull client supports TLS 1.1 and TLS 1.2</span></span>

<span data-ttu-id="d7c2c-115">기존에 DSC 끌어오기 클라이언트는 HTTPS 연결을 통해 SSL3.0 및 TLS1.0만 지원했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-115">Previously, the DSC pull client only supported SSL3.0 and TLS1.0 over HTTPS connections.</span></span> <span data-ttu-id="d7c2c-116">더 안전한 프로토콜을 사용하도록 하는 경우 끌어오기 클라이언트의 작동이 중지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-116">When forced to use more secure protocols, the pull client would stop functioning.</span></span> <span data-ttu-id="d7c2c-117">WMF 5.1에서는 DSC 끌어오기 클라이언트가 SSL 3.0을 더 이상 지원하지 않고 더 안전한 TLS 1.1 및 TLS 1.2 프로토콜을 추가로 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-117">In WMF 5.1, the DSC pull client no longer supports SSL 3.0 and adds support for the more secure TLS 1.1 and TLS 1.2 protocols.</span></span>

## <a name="improved-pull-server-registration"></a><span data-ttu-id="d7c2c-118">향상된 끌어오기 서버 등록</span><span class="sxs-lookup"><span data-stu-id="d7c2c-118">Improved pull server registration</span></span>

<span data-ttu-id="d7c2c-119">이전 버전의 WMF에서는 ESENT 데이터베이스를 사용하는 동안 DSC 끌어오기 서버에 동시 등록/보고 요청을 하는 경우 LCM이 등록 및/또는 보고에 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-119">In the earlier versions of WMF, simultaneous registrations/reporting requests to a DSC pull server while using the ESENT database would lead to LCM failing to register and/or report.</span></span> <span data-ttu-id="d7c2c-120">이러한 경우 끌어오기 서버의 이벤트 로그에 "이미 사용 중인 인스턴스 이름" 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-120">In such cases, the event logs on the pull server has the error "Instance Name already in use."</span></span> <span data-ttu-id="d7c2c-121">이는 다중 스레드 시나리오에서 잘못된 패턴을 사용하여 ESENT 데이터베이스에 액세스하기 때문이었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-121">This was caused by an incorrect pattern being used to access the ESENT database in a multi-threaded scenario.</span></span> <span data-ttu-id="d7c2c-122">WMF 5.1에서는 이 문제가 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-122">In WMF 5.1, this issue has been fixed.</span></span> <span data-ttu-id="d7c2c-123">WMF 5.1에서는 동시 등록 또는 보고(ESENT 데이터베이스 포함)가 올바로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-123">Concurrent registrations or reporting (involving ESENT database) works fine in WMF 5.1.</span></span> <span data-ttu-id="d7c2c-124">이 문제는 ESENT 데이터베이스에만 적용되고 OLEDB 데이터베이스에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-124">This issue is applicable only to the ESENT database and does not apply to the OLEDB database.</span></span>

## <a name="enable-circular-log-on-esent-database-instance"></a><span data-ttu-id="d7c2c-125">ESENT 데이터베이스 인스턴스에 순환 로그 사용</span><span class="sxs-lookup"><span data-stu-id="d7c2c-125">Enable Circular log on ESENT database instance</span></span>

<span data-ttu-id="d7c2c-126">이전 버전의 DSC-PullServer에서는 데이터베이스 인스턴스가 순환 로깅 없이 만들어지므로 ESENT 데이터베이스 로그 파일이 끌어오기 서버의 디스크 공간을 가득 채웠습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-126">In eariler version of DSC-PullServer, the ESENT database log files were filling up the disk space of the pullserver because the database instance was being created without circular logging.</span></span> <span data-ttu-id="d7c2c-127">이 릴리스에서는 끌어오기 서버의 web.config를 사용하여 인스턴스의 순환 로깅 동작을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-127">In this release, you have the option to control the circular logging behavior of the instance using the web.config of the pullserver.</span></span> <span data-ttu-id="d7c2c-128">기본적으로 CircularLogging은 TRUE로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-128">By default CircularLogging is set to TRUE.</span></span>

```xml
<appSettings>
    <add key="dbprovider" value="ESENT" />
    <add key="dbconnectionstr" value="C:\Program Files\WindowsPowerShell\DscService\Devices.edb" />
    <add key="CheckpointDepthMaxKB" value="512" />
    <add key="UseCircularESENTLogs" value="TRUE" />
  </appSettings>
```

## <a name="wow64-support-for-configuration-keyword"></a><span data-ttu-id="d7c2c-129">WOW64에서 구성 키워드 지원</span><span class="sxs-lookup"><span data-stu-id="d7c2c-129">WOW64 support for Configuration Keyword</span></span>

<span data-ttu-id="d7c2c-130">이제 64비트 컴퓨터의 WOW64에서 `Configuration` 키워드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-130">The `Configuration` keyword is now supported in WOW64 on a 64-bit computer.</span></span> <span data-ttu-id="d7c2c-131">즉, 64비트 컴퓨터에서 실행되는 Windows PowerShell ISE(x86) 같은 32비트 프로세스 내에서 DSC 구성을 정의하고 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-131">This means that a DSC configuration can be defined and compiled within a 32-bit process such as Windows PowerShell ISE (x86) running on a 64-bit computer.</span></span>

## <a name="pull-partial-configuration-naming-convention"></a><span data-ttu-id="d7c2c-132">부분 구성 명명 규칙 끌어오기</span><span class="sxs-lookup"><span data-stu-id="d7c2c-132">Pull partial configuration naming convention</span></span>

<span data-ttu-id="d7c2c-133">이전 릴리스에서는 부분 구성에 대한 명명 규칙에 따라 끌어오기 서버/서비스의 MOF 파일 이름이 로컬 구성 관리자 설정에 지정된 부분 구성 이름과 일치하여 MOF 파일에 포함된 구성 이름과 일치해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-133">In the previous release, the naming convention for a partial configuration was that the MOF file name in the pull server/service should match the partial configuration name specified in the local configuration manager settings that in turn must match the configuration name embedded in the MOF file.</span></span>

<span data-ttu-id="d7c2c-134">아래 스냅샷을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-134">See the snapshots below:</span></span>

- <span data-ttu-id="d7c2c-135">노드가 수신할 수 있는 부분 구성을 정의하는 로컬 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-135">Local configuration settings which defines a partial configuration that a node is allowed to receive.</span></span>

  ![샘플 메타 구성](../images/DSC-improvements/MetaConfigPartialOne.png)

- <span data-ttu-id="d7c2c-137">샘플 부분 구성 정의</span><span class="sxs-lookup"><span data-stu-id="d7c2c-137">Sample partial configuration definition</span></span>

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

- <span data-ttu-id="d7c2c-138">생성된 MOF 파일에 포함된 ‘ConfigurationName’</span><span class="sxs-lookup"><span data-stu-id="d7c2c-138">'ConfigurationName' embedded in the generated MOF file.</span></span>

  ![생성된 mof 파일 샘플](../images/DSC-improvements/PartialGeneratedMof.png)

- <span data-ttu-id="d7c2c-140">풀 구성 리포지토리의 FileName</span><span class="sxs-lookup"><span data-stu-id="d7c2c-140">FileName in the pull configuration repository</span></span>

  ![구성 리포지토리의 FileName](../images/DSC-improvements/PartialInConfigRepository.png)

  <span data-ttu-id="d7c2c-142">Azure 자동화 서비스 이름은 MOF 파일을 `<ConfigurationName>.<NodeName>.mof`로 생성했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-142">Azure Automation service name generated MOF files as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="d7c2c-143">따라서 아래 구성은 PartialOne.localhost.mof로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-143">So the configuration below compiles to PartialOne.localhost.mof.</span></span>

  <span data-ttu-id="d7c2c-144">따라서 Azure 자동화 서비스에서 부분 구성 중 하나를 끌어올 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-144">This made it impossible to pull one of your partial configuration from Azure Automation service.</span></span>

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

  <span data-ttu-id="d7c2c-145">WMF 5.1에서는 끌어오기 서버/서비스의 부분 구성을 `<ConfigurationName>.<NodeName>.mof`로 명명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-145">In WMF 5.1, a partial configuration in the pull server/service can be named as `<ConfigurationName>.<NodeName>.mof`.</span></span> <span data-ttu-id="d7c2c-146">또한 컴퓨터가 끌어오기 서버/서비스에서 단일 구성을 끌어오는 경우 끌어오기 서버 구성 리포지토리의 구성 파일에 원하는 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-146">Moreover, if a machine is pulling a single configuration from a pull server/service then the configuration file on the pull server configuration repository can have any file name.</span></span> <span data-ttu-id="d7c2c-147">이러한 명명 유연성을 통해 노드를 Azure Automation 서비스로 부분적으로 관리할 수 있습니다. 이 경우 노드의 일부 구성을 Azure Automation DSC에서 가져오고 부분 구성을 로컬로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-147">This naming flexibility allows you to manage your nodes partially by Azure Automation service, where some configuration for your node is coming from Azure Automation DSC and with a partial configuration that you manage locally.</span></span>

  <span data-ttu-id="d7c2c-148">아래 메타 구성은 노드를 로컬뿐 아니라 Azure Automation 서비스에서 관리하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-148">The metaconfiguration below sets up a node to be managed both locally as well as by Azure Automation service.</span></span>

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

## <a name="using-psdscrunascredential-with-dsc-composite-resources"></a><span data-ttu-id="d7c2c-149">DSC 복합 리소스와 함께 PsDscRunAsCredential 사용</span><span class="sxs-lookup"><span data-stu-id="d7c2c-149">Using PsDscRunAsCredential with DSC composite resources</span></span>

<span data-ttu-id="d7c2c-150">[PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser)을 DSC [복합](/powershell/scripting/dsc/authoringresourcecomposite) 리소스와 함께 사용할 수 있도록 지원을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-150">We have added support for using [PsDscRunAsCredential](/powershell/scripting/dsc/configurations/runAsUser) with DSC [Composite](/powershell/scripting/dsc/authoringresourcecomposite) resources.</span></span>

<span data-ttu-id="d7c2c-151">이제 구성 내에서 복합 리소스를 사용할 때 **PsDscRunAsCredential** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-151">You can now specify a value for **PsDscRunAsCredential** when using composite resources inside configurations.</span></span> <span data-ttu-id="d7c2c-152">이 값을 지정할 경우 모든 리소스가 복합 리소스 내에서 RunAs 사용자로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-152">When specified, all resources run inside a composite resource as a RunAs user.</span></span> <span data-ttu-id="d7c2c-153">복합 리소스가 다른 복합 리소스를 호출하는 경우에도 해당 리소스가 모두 RunAs 사용자로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-153">If a composite resource calls another composite resource, all those resources are also executed as RunAs user.</span></span> <span data-ttu-id="d7c2c-154">RunAs 자격 증명은 복합 리소스 계층 구조의 모든 수준에 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-154">RunAs credentials are propagated to any level of the composite resource hierarchy.</span></span> <span data-ttu-id="d7c2c-155">복합 리소스 내의 리소스가 **PsDscRunAsCredential**의 고유한 값을 지정하는 경우 구성 컴파일 중 병합 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-155">If any resource inside a composite resource specifies its own value for **PsDscRunAsCredential**, a merge error results during configuration compilation.</span></span>

<span data-ttu-id="d7c2c-156">이 예제에서는 PSDesiredStateConfiguration 모듈에 포함된 [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) 복합 리소스와 함께 사용하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-156">This example shows usage with the [WindowsFeatureSet](/powershell/scripting/dsc/reference/resources/windows/windowsfeaturesetresource) composite resource included in PSDesiredStateConfiguration module.</span></span>

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

## <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="d7c2c-157">구성에서 동일한 중복 리소스 허용</span><span class="sxs-lookup"><span data-stu-id="d7c2c-157">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="d7c2c-158">DSC는 구성 내에서 충돌하는 리소스 정의를 허용하거나 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-158">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="d7c2c-159">충돌을 해결하려고 하지 않고 단순히 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-159">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="d7c2c-160">구성 다시 사용이 복합 리소스 등을 통해 더 많이 활용되면 충돌이 더 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-160">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="d7c2c-161">충돌하는 리소스 정의가 동일하면 DSC가 지능적이어서 이를 허용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-161">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="d7c2c-162">이 릴리스에서는 정의가 동일한 리소스 인스턴스가 여러 개 있어도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-162">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="d7c2c-163">이전 릴리스에서는 'Web-Server' 역할을 설치하려는 WindowsFeature FE_IIS와 WindowsFeature Worker_IIS 인스턴스 간의 충돌로 인해 컴파일이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-163">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="d7c2c-164">이러한 두 구성에서 구성하려는 *모든* 속성이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-164">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="d7c2c-165">이러한 두 리소스의 *모든* 속성이 동일하므로 이제 컴파일이 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-165">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="d7c2c-166">두 리소스 간에 다른 속성이 있으면 동일한 것으로 간주되지 않고 컴파일이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-166">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail.</span></span>

## <a name="dsc-module-and-configuration-signing-validations"></a><span data-ttu-id="d7c2c-167">DSC 모듈 및 구성 서명 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="d7c2c-167">DSC module and configuration signing validations</span></span>

<span data-ttu-id="d7c2c-168">DSC에서는 구성 및 모듈이 끌어오기 서버에서 관리되는 컴퓨터로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-168">In DSC, configurations and modules are distributed to managed computers from the pull server.</span></span> <span data-ttu-id="d7c2c-169">끌어오기 서버가 손상되는 경우 공격자가 끌어오기 서버의 구성 및 모듈을 수정하여 모든 관리형 노드로 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-169">If the pull server is compromised, an attacker can potentially modify the configurations and modules on the pull server and have it distributed to all managed nodes.</span></span>

<span data-ttu-id="d7c2c-170">WMF 5.1의 DSC에서는 카탈로그 및 구성(.MOF) 파일에 있는 디지털 서명의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-170">In WMF 5.1, DSC supports validating the digital signatures on catalog and configuration (.MOF) files.</span></span> <span data-ttu-id="d7c2c-171">이 기능은 노드에서 신뢰할 수 있는 서명자가 서명하지 않았거나 신뢰할 수 있는 서명자가 서명한 후 변조된 구성 또는 모듈 파일을 실행하지 못하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-171">This feature prevents nodes from executing configurations or module files which are not signed by a trusted signer or which have been tampered with after they have been signed by trusted signer.</span></span>

### <a name="how-to-sign-configuration-and-module"></a><span data-ttu-id="d7c2c-172">구성 및 모듈에 서명하는 방법</span><span class="sxs-lookup"><span data-stu-id="d7c2c-172">How to sign configuration and module</span></span>

- <span data-ttu-id="d7c2c-173">구성 파일(.MOF): 기존 PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature)가 MOF 파일 서명을 지원하도록 확장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-173">Configuration Files (.MOFs): The existing PowerShell cmdlet [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) is extended to support signing of MOF files.</span></span>
- <span data-ttu-id="d7c2c-174">모듈: 다음 단계에 따라 해당 모듈 카탈로그에 서명하여 모듈 서명을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-174">Modules: Signing of modules is done by signing the corresponding module catalog using the following steps:</span></span>
  1. <span data-ttu-id="d7c2c-175">카탈로그 파일 만들기: 카탈로그 파일에는 암호화 해시 또는 지문의 컬렉션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-175">Create a catalog file: A catalog file contains a collection of cryptographic hashes or thumbprints.</span></span> <span data-ttu-id="d7c2c-176">각 지문은 모듈에 포함된 파일에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-176">Each thumbprint corresponds to a file that is included in the module.</span></span> <span data-ttu-id="d7c2c-177">사용자가 모듈의 카탈로그 파일을 만들 수 있도록 지원하는 새로운 [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog) cmdlet이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-177">The new cmdlet [New-FileCatalog](/powershell/module/microsoft.powershell.security/new-filecatalog), has been added to enable users to create a catalog file for their module.</span></span>
  2. <span data-ttu-id="d7c2c-178">카탈로그 파일에 서명: [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature)를 사용하여 카탈로그 파일에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-178">Sign the catalog file: Use [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) to sign the catalog file.</span></span>
  3. <span data-ttu-id="d7c2c-179">카탈로그 파일을 모듈 폴더 내에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-179">Place the catalog file inside the module folder.</span></span> <span data-ttu-id="d7c2c-180">규칙에 따라 모듈 카탈로그 파일은 모듈과 이름이 같은 모듈 폴더에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-180">By convention, module catalog file should be placed under the module folder with the same name as the module.</span></span>

### <a name="localconfigurationmanager-settings-to-enable-signing-validations"></a><span data-ttu-id="d7c2c-181">서명 유효성 검사를 사용하도록 설정하는 LocalConfigurationManager 설정</span><span class="sxs-lookup"><span data-stu-id="d7c2c-181">LocalConfigurationManager settings to enable signing validations</span></span>

#### <a name="pull"></a><span data-ttu-id="d7c2c-182">끌어오기</span><span class="sxs-lookup"><span data-stu-id="d7c2c-182">Pull</span></span>

<span data-ttu-id="d7c2c-183">노드의 LocalConfigurationManager는 현재 설정에 따라 모듈 및 구성의 서명 유효성 검사를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-183">The LocalConfigurationManager of a node performs signing validation of modules and configurations based on its current settings.</span></span> <span data-ttu-id="d7c2c-184">기본적으로 서명 유효성 검사를 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-184">By default, signature validation is disabled.</span></span> <span data-ttu-id="d7c2c-185">서명 유효성 검사를 사용하도록 설정하려면 아래 표시된 노드의 메타 구성 정의에 'SignatureValidation' 블록을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-185">Signature validation can enabled by adding the ‘SignatureValidation’ block to the meta-configuration definition of the node as shown below:</span></span>

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

<span data-ttu-id="d7c2c-186">노드에서 위의 메타 구성을 설정하면 다운로드된 구성 및 모듈에서 서명 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-186">Setting the above metaconfiguration on a node enables signature validation on downloaded configurations and modules.</span></span> <span data-ttu-id="d7c2c-187">로컬 구성 관리자는 다음 단계를 수행하여 디지털 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-187">The Local Configuration Manager performs the following steps to verify the digital signatures.</span></span>

1. <span data-ttu-id="d7c2c-188">`Get-AuthenticodeSignature` cmdlet을 사용하여 구성 파일(.MOF)의 서명이 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-188">Verify the signature on a configuration file (.MOF) is valid using the `Get-AuthenticodeSignature` cmdlet.</span></span>
2. <span data-ttu-id="d7c2c-189">서명자에게 권한을 부여한 인증 기관을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-189">Verify the certificate authority that authorized the signer is trusted.</span></span>
3. <span data-ttu-id="d7c2c-190">구성의 모듈/리소스 종속성을 임시 위치로 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-190">Download module/resource dependencies of the configuration to a temp location.</span></span>
4. <span data-ttu-id="d7c2c-191">모듈 내에 포함된 카탈로그의 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-191">Verify the signature of the catalog included inside the module.</span></span>
   - <span data-ttu-id="d7c2c-192">`<moduleName>.cat` 파일을 찾고 `Get-AuthenticodeSignature`를 사용하여 해당 서명을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-192">Find a `<moduleName>.cat` file and verify its signature using `Get-AuthenticodeSignature`.</span></span>
   - <span data-ttu-id="d7c2c-193">서명자를 인증한 인증 기관을 신뢰할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-193">Verify the certification authority that authenticated the signer is trusted.</span></span>
   - <span data-ttu-id="d7c2c-194">새 `Test-FileCatalog` cmdlet을 사용하여 모듈의 콘텐츠가 변조되지 않았는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-194">Verify the content of the modules has not been tampered using the new cmdlet `Test-FileCatalog`.</span></span>
5. <span data-ttu-id="d7c2c-195">`$env:ProgramFiles\WindowsPowerShell\Modules\`에 대한 `Install-Module`</span><span class="sxs-lookup"><span data-stu-id="d7c2c-195">`Install-Module` to `$env:ProgramFiles\WindowsPowerShell\Modules\`</span></span>
6. <span data-ttu-id="d7c2c-196">구성 처리</span><span class="sxs-lookup"><span data-stu-id="d7c2c-196">Process configuration</span></span>

> [!NOTE]
> <span data-ttu-id="d7c2c-197">모듈 카탈로그 및 구성의 서명 유효성 검사는 시스템에 구성을 처음으로 적용할 때나 모듈을 다운로드하여 설치할 때만 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-197">Signature validation on module-catalog and configuration is only performed when the configuration is applied to the system for the first time or when the module is downloaded and installed.</span></span>
> <span data-ttu-id="d7c2c-198">일관성 검사에서는 Current.mof 또는 해당 모듈 종속성의 서명 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-198">Consistency runs do not validate the signature of Current.mof or its module dependencies.</span></span> <span data-ttu-id="d7c2c-199">끌어오기 서버에서 끌어온 구성에 서명이 되어 있지 않은 등 어느 단계에서든 유효성 검사가 실패하면 구성 처리가 종료되고 아래와 같은 오류가 표시되며 모든 임시 파일이 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-199">If verification has failed at any stage, for instance, if the configuration pulled from the pull server is unsigned, then processing of the configuration terminates with the error shown below and all temporary files are deleted.</span></span>

![샘플 오류 출력 구성](../images/DSC-improvements/PullUnsignedConfigFail.png)

<span data-ttu-id="d7c2c-201">마찬가지로 카탈로그에 서명이 되어 있지 않은 모듈을 끌어오면 다음 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-201">Similarly, pulling a module whose catalog is not signed results in the following error:</span></span>

![샘플 오류 출력 모듈](../images/DSC-improvements/PullUnisgnedCatalog.png)

#### <a name="push"></a><span data-ttu-id="d7c2c-203">밀어넣기</span><span class="sxs-lookup"><span data-stu-id="d7c2c-203">Push</span></span>

<span data-ttu-id="d7c2c-204">푸시를 사용하여 전달된 구성은 노드로 전달되기 전에 해당 소스에서 변조될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-204">A configuration delivered by using push might be tampered with at its source before it delivered to the node.</span></span> <span data-ttu-id="d7c2c-205">로컬 구성 관리자는 푸시되거나 게시된 구성에 대해 비슷한 서명 유효성 검사 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-205">The Local Configuration Manager performs similar signature validation steps for pushed or published configuration(s).</span></span> <span data-ttu-id="d7c2c-206">다음은 푸시에 대한 서명 유효성 검사의 완전한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-206">Below is a complete example of signature validation for push.</span></span>

- <span data-ttu-id="d7c2c-207">노드에서 서명 유효성 검사를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-207">Enable signature validation on the node.</span></span>

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

- <span data-ttu-id="d7c2c-208">샘플 구성 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-208">Create a sample configuration file.</span></span>

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

- <span data-ttu-id="d7c2c-209">서명되지 않은 구성 파일을 노드로 푸시해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-209">Try pushing the unsigned configuration file in to the node.</span></span>

  ```powershell
  Start-DscConfiguration -Path .\Test -Wait -Verbose -Force
  ```

  ![ErrorUnsignedMofPushed](../images/DSC-improvements/PushUnsignedMof.png)

- <span data-ttu-id="d7c2c-211">코드 서명 인증서를 사용하여 구성 파일에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-211">Sign the configuration file using code-signing certificate.</span></span>

  ![SignMofFile](../images/DSC-improvements/SignMofFile.png)

- <span data-ttu-id="d7c2c-213">서명된 MOF 파일을 푸시해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="d7c2c-213">Try pushing the signed MOF file.</span></span>

  ![PushSignedMofFile](../images/DSC-improvements/PushSignedMof.png)
