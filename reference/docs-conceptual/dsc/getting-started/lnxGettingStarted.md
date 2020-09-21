---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Linux용 DSC(필요한 상태 구성) 시작
ms.openlocfilehash: 64657dda04fa2df97fa2ad7c7a5c2d15b66a270a
ms.sourcegitcommit: 4bb44f183dcbfa8dced57f075812e02d3b45fd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86301338"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a><span data-ttu-id="e6bfb-103">Linux용 DSC(필요한 상태 구성) 시작</span><span class="sxs-lookup"><span data-stu-id="e6bfb-103">Get started with Desired State Configuration (DSC) for Linux</span></span>

<span data-ttu-id="e6bfb-104">이 항목에서는 Linux용 PowerShell DSC(필요한 상태 구성) 사용 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Linux.</span></span> <span data-ttu-id="e6bfb-105">DSC에 대한 일반적인 내용은 [Windows PowerShell 필요한 상태 구성 시작](../overview/overview.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-linux-operation-system-versions"></a><span data-ttu-id="e6bfb-106">지원되는 Linux 운영 체제 버전</span><span class="sxs-lookup"><span data-stu-id="e6bfb-106">Supported Linux operation system versions</span></span>

<span data-ttu-id="e6bfb-107">다음의 Linux 운영 체제 버전이 Linux용 DSC에 의해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-107">The following Linux operating system versions are supported by DSC for Linux.</span></span>

- <span data-ttu-id="e6bfb-108">CentOS 5, 6 및 7(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-108">CentOS 5, 6, and 7 (x86/x64)</span></span>
- <span data-ttu-id="e6bfb-109">Debian GNU/Linux 6, 7 및 8(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-109">Debian GNU/Linux 6, 7 and 8 (x86/x64)</span></span>
- <span data-ttu-id="e6bfb-110">Oracle Linux 5, 6 및 7(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-110">Oracle Linux 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e6bfb-111">Red Hat Enterprise Linux Server 5, 6 및 7(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-111">Red Hat Enterprise Linux Server 5, 6 and 7 (x86/x64)</span></span>
- <span data-ttu-id="e6bfb-112">SUSE Linux Enterprise Server 10, 11 및 12(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-112">SUSE Linux Enterprise Server 10, 11 and 12 (x86/x64)</span></span>
- <span data-ttu-id="e6bfb-113">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS(x86/x64)</span><span class="sxs-lookup"><span data-stu-id="e6bfb-113">Ubuntu Server 12.04 LTS, 14.04 LTS, 16.04 LTS (x86/x64)</span></span>

## <a name="installing-dsc-for-linux"></a><span data-ttu-id="e6bfb-114">Linux용 DSC 설치</span><span class="sxs-lookup"><span data-stu-id="e6bfb-114">Installing DSC for Linux</span></span>

<span data-ttu-id="e6bfb-115">Linux용 DSC를 설치하려면 먼저 [OMI(개방형 관리 인프라)](https://github.com/Microsoft/omi)를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-115">You must install the [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi) before installing DSC for Linux.</span></span>

### <a name="installing-omi"></a><span data-ttu-id="e6bfb-116">OMI 설치</span><span class="sxs-lookup"><span data-stu-id="e6bfb-116">Installing OMI</span></span>

<span data-ttu-id="e6bfb-117">Linux용 필요한 상태 구성을 사용하려면 OMI(개방형 관리 인프라) CIM 서버 버전 1.0.8.1 이상이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-117">Desired State Configuration for Linux requires the Open Management Infrastructure (OMI) CIM server, version 1.0.8.1 or later.</span></span> <span data-ttu-id="e6bfb-118">OMI는 Open Group: [Open Management Infrastructure (OMI)(개방형 관리 인프라)](https://github.com/Microsoft/omi)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-118">OMI can be downloaded from The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).</span></span>

<span data-ttu-id="e6bfb-119">OMI를 설치하려면 Linux 시스템(.rpm 또는.deb)과 OpenSSL 버전(ssl_098 또는 ssl_100) 및 아키텍처(x64/x86)에 적절한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-119">To install OMI, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e6bfb-120">RPM 패키지는 CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server 및 Oracle Linux에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-120">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e6bfb-121">DEB 패키지는 Debian GNU/Linux 및 Ubuntu 서버에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-121">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e6bfb-122">ssl_098 패키지는 OpenSSL 0.9.8이 설치된 컴퓨터에 적합하고, ssl_100 패키지는 OpenSSL 1.0이 설치된 컴퓨터에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-122">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="e6bfb-123">설치된 OpenSSL 버전을 확인하려면 `openssl version` 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-123">To determine the installed OpenSSL version, run the command `openssl version`.</span></span>

<span data-ttu-id="e6bfb-124">CentOS 7 x64 시스템에 OMI를 설치하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-124">Run the following command to install OMI on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a><span data-ttu-id="e6bfb-125">DSC 설치</span><span class="sxs-lookup"><span data-stu-id="e6bfb-125">Installing DSC</span></span>

<span data-ttu-id="e6bfb-126">Linux용 DSC는 [here(여기)](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-126">DSC for Linux is available for download [here](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/tag/v1.1.1-294).</span></span>

<span data-ttu-id="e6bfb-127">DSC를 설치하려면 Linux 시스템(.rpm 또는.deb)과 OpenSSL 버전(ssl_098 또는 ssl_100) 및 아키텍처(x64/x86)에 적절한 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-127">To install DSC, install the package that is appropriate for your Linux system (.rpm or .deb) and OpenSSL version (ssl_098 or ssl_100), and architecture (x64/x86).</span></span> <span data-ttu-id="e6bfb-128">RPM 패키지는 CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server 및 Oracle Linux에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-128">RPM packages are appropriate for CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server, and Oracle Linux.</span></span> <span data-ttu-id="e6bfb-129">DEB 패키지는 Debian GNU/Linux 및 Ubuntu 서버에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-129">DEB packages are appropriate for Debian GNU/Linux and Ubuntu Server.</span></span> <span data-ttu-id="e6bfb-130">ssl_098 패키지는 OpenSSL 0.9.8이 설치된 컴퓨터에 적합하고, ssl_100 패키지는 OpenSSL 1.0이 설치된 컴퓨터에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-130">The ssl_098 packages are appropriate for computers with OpenSSL 0.9.8 installed while the ssl_100 packages are appropriate for computers with OpenSSL 1.0 installed.</span></span>

> [!NOTE]
> <span data-ttu-id="e6bfb-131">설치된 OpenSSL 버전을 확인하려면 openssl version 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-131">To determine the installed OpenSSL version, run the command openssl version.</span></span>

<span data-ttu-id="e6bfb-132">CentOS 7 x64 시스템에 DSC를 설치하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-132">Run the following command to install DSC on a CentOS 7 x64 system.</span></span>

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`

## <a name="using-dsc-for-linux"></a><span data-ttu-id="e6bfb-133">Linux용 DSC 사용</span><span class="sxs-lookup"><span data-stu-id="e6bfb-133">Using DSC for Linux</span></span>

<span data-ttu-id="e6bfb-134">다음 섹션에서는 Linux 컴퓨터에서 DSC 구성을 만들고 실행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-134">The following sections explain how to create and run DSC configurations on Linux computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="e6bfb-135">구성 MOF 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="e6bfb-135">Creating a configuration MOF document</span></span>

<span data-ttu-id="e6bfb-136">Windows PowerShell 구성 키워드는 Windows 컴퓨터와 마찬가지로 Linux 컴퓨터용 구성을 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-136">The Windows PowerShell Configuration keyword is used to create a configuration for Linux computers, just like for Windows computers.</span></span> <span data-ttu-id="e6bfb-137">다음 단계에서는 Windows PowerShell을 사용한 Linux 컴퓨터용 구성 문서 작성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-137">The following steps describe the creation of a configuration document for a Linux computer using Windows PowerShell.</span></span>

1. <span data-ttu-id="e6bfb-138">nx 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-138">Import the nx module.</span></span> <span data-ttu-id="e6bfb-139">nx Windows PowerShell 모듈은 Linux용 DSC를 위한 기본 제공 리소스에 대한 스키마를 포함하며, 로컬 컴퓨터에 설치되어 구성에 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-139">The nx Windows PowerShell module contains the schema for Built-In resources for DSC for Linux, and must be installed to your local computer and imported in the configuration.</span></span>

   - <span data-ttu-id="e6bfb-140">nx 모듈을 설치하려면 nx 모듈 디렉터리를 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` 또는 `$PSHOME\Modules`에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-140">To install the nx module, copy the nx module directory to either `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` or `$PSHOME\Modules`.</span></span> <span data-ttu-id="e6bfb-141">nx 모듈은 Linux용 DSC 설치 패키지에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-141">The nx module is included in the DSC for Linux installation package.</span></span> <span data-ttu-id="e6bfb-142">구성에서 nx 모듈을 가져오려면 `Import-DSCResource` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-142">To import the nx module in your configuration, use the `Import-DSCResource` command:</span></span>

   ```powershell
   Configuration ExampleConfiguration{

    Import-DSCResource -Module nx

   }
   ```

2. <span data-ttu-id="e6bfb-143">구성을 정의하고 구성 문서를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-143">Define a configuration and generate the configuration document:</span></span>

   ```powershell
   Configuration ExampleConfiguration
   {
        Import-DscResource -Module nx

        Node  "linuxhost.contoso.com"
        {
            nxFile ExampleFile 
            {
                DestinationPath = "/tmp/example"
                Contents = "hello world `n"
                Ensure = "Present"
                Type = "File"
            }
        }
   }

   ExampleConfiguration -OutputPath:"C:\temp"
   ```

### <a name="push-the-configuration-to-the-linux-computer"></a><span data-ttu-id="e6bfb-144">구성을 Linux 컴퓨터에 밀어넣기</span><span class="sxs-lookup"><span data-stu-id="e6bfb-144">Push the configuration to the Linux computer</span></span>

<span data-ttu-id="e6bfb-145">구성 문서(MOF 파일)를 [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet을 사용하여 Linux 컴퓨터에 밀어넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-145">Configuration documents (MOF files) can be pushed to the Linux computer using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e6bfb-146">원격으로 Linux 컴퓨터에 [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) 또는 [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlet과 함께 이 cmdlet을 사용하려면 CIMSession을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-146">In order to use this cmdlet, along with the [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration), or [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) cmdlets, remotely to a Linux computer, you must use a CIMSession.</span></span> <span data-ttu-id="e6bfb-147">CIMSession을 Linux 컴퓨터에 만드는 데에는 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-147">The [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet is used to create a CIMSession to the Linux computer.</span></span>

<span data-ttu-id="e6bfb-148">다음 코드는 Linux용 DSC를 위한 CIMSession을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-148">The following code shows how to create a CIMSession for DSC for Linux.</span></span>

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName "root" -Message "Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl $true -SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl $true
$Sess=New-CimSession -Credential $credential -ComputerName $Node -Port 5986 -Authentication basic -SessionOption $opt -OperationTimeoutSec 90
```

> [!NOTE]
> <span data-ttu-id="e6bfb-149">"밀어넣기" 모드의 경우, 사용자 자격 증명은 Linux 컴퓨터 상의 루트 사용자여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-149">For "Push" mode, the user credential must be the root user on the Linux computer.</span></span>
> <span data-ttu-id="e6bfb-150">Linux용 DSC에는 SSL/TLS 연결만 지원되며, `New-CimSession`은 $true로 설정된 –UseSSL 매개 변수와 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-150">Only SSL/TLS connections are supported for DSC for Linux, the `New-CimSession` must be used with the –UseSSL parameter set to $true.</span></span>
> <span data-ttu-id="e6bfb-151">OMI(DSC용)에서 사용하는 SSL 인증서는 속성이 pemfile 및 keyfile인 `/etc/opt/omi/conf/omiserver.conf` 파일에 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-151">The SSL certificate used by OMI (for DSC) is specified in the file: `/etc/opt/omi/conf/omiserver.conf` with the properties: pemfile and keyfile.</span></span>
> <span data-ttu-id="e6bfb-152">이 인증서를 [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet을 실행 중인 Windows 컴퓨터에서 신뢰하지 않을 때에는 CIMSession 옵션 `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`을 사용하여 인증서 유효성 검사를 무시하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-152">If this certificate is not trusted by the Windows computer that you are running the [New-CimSession](/powershell/module/CimCmdlets/New-CimSession) cmdlet on, you can choose to ignore certificate validation with the CIMSession Options: `-SkipCACheck $true -SkipCNCheck $true -SkipRevocationCheck $true`</span></span>

<span data-ttu-id="e6bfb-153">Linux 노드에 DSC 구성을 밀어 넣으려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-153">Run the following command to push the DSC configuration to the Linux node.</span></span>

`Start-DscConfiguration -Path:"C:\temp" -CimSession $Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a><span data-ttu-id="e6bfb-154">끌어오기 서버로 구성 배포</span><span class="sxs-lookup"><span data-stu-id="e6bfb-154">Distribute the configuration with a pull server</span></span>

<span data-ttu-id="e6bfb-155">구성은 Windows 컴퓨터와 마찬가지로 끌어오기 서버로 Linux 컴퓨터에 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-155">Configurations can be distributed to a Linux computer with a pull server, just like for Windows computers.</span></span> <span data-ttu-id="e6bfb-156">끌어오기 서버 사용에 대한 지침이 필요하면 [Windows PowerShell 필요한 상태 구성 끌어오기 서버](../pull-server/pullServer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-156">For guidance on using a pull server, see [Windows PowerShell Desired State Configuration Pull Servers](../pull-server/pullServer.md).</span></span> <span data-ttu-id="e6bfb-157">추가 정보 및 끌어오기 서버와 함께 Linux 컴퓨터를 사용하는 것과 관련된 제한 사항에 대해서는 Linux용 필요한 상태 구성에 대한 릴리스 정보를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-157">For additional information and limitations related to using Linux computers with a pull server, see the Release Notes for Desired State Configuration for Linux.</span></span>

### <a name="working-with-configurations-locally"></a><span data-ttu-id="e6bfb-158">로컬에서 구성 사용</span><span class="sxs-lookup"><span data-stu-id="e6bfb-158">Working with configurations locally</span></span>

<span data-ttu-id="e6bfb-159">Linux용 DSC는 로컬 Linux 컴퓨터의 구성으로 작업하는 스크립트를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-159">DSC for Linux includes scripts to work with configuration from the local Linux computer.</span></span> <span data-ttu-id="e6bfb-160">이 스크립트는 `/opt/microsoft/dsc/Scripts`에 있으며 다음 내용을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-160">These scripts are locate in `/opt/microsoft/dsc/Scripts` and include the following:</span></span>

- <span data-ttu-id="e6bfb-161">GetDscConfiguration.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-161">GetDscConfiguration.py</span></span>

<span data-ttu-id="e6bfb-162">컴퓨터에 적용된 현재 구성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-162">Returns the current configuration applied to the computer.</span></span> <span data-ttu-id="e6bfb-163">Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-163">Similar to the Windows PowerShell cmdlet `Get-DscConfiguration` cmdlet.</span></span>

`# sudo ./GetDscConfiguration.py`

- <span data-ttu-id="e6bfb-164">GetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-164">GetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e6bfb-165">컴퓨터에 적용된 현재 메타 구성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-165">Returns the current meta-configuration applied to the computer.</span></span> <span data-ttu-id="e6bfb-166">[Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-166">Similar to the cmdlet [Get-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager) cmdlet.</span></span>

`# sudo ./GetDscLocalConfigurationManager.py`

- <span data-ttu-id="e6bfb-167">InstallModule.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-167">InstallModule.py</span></span>

<span data-ttu-id="e6bfb-168">사용자 지정 DSC 리소스 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-168">Installs a custom DSC resource module.</span></span> <span data-ttu-id="e6bfb-169">모듈 공유 개체 라이브러리 및 스키마 MOF 파일을 포함하는 .zip 파일의 경로가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-169">Requires the path to a .zip file containing the module shared object library and schema MOF files.</span></span>

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

- <span data-ttu-id="e6bfb-170">RemoveModule.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-170">RemoveModule.py</span></span>

<span data-ttu-id="e6bfb-171">사용자 지정 DSC 리소스 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-171">Removes a custom DSC resource module.</span></span> <span data-ttu-id="e6bfb-172">제거할 모듈의 이름이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-172">Requires the name of the module to remove.</span></span>

`# sudo ./RemoveModule.py cnx_Resource`

- <span data-ttu-id="e6bfb-173">StartDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-173">StartDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e6bfb-174">구성 MOF 파일을 컴퓨터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-174">Applies a configuration MOF file to the computer.</span></span> <span data-ttu-id="e6bfb-175">[Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-175">Similar to the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span> <span data-ttu-id="e6bfb-176">적용할 구성 MOF의 경로가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-176">Requires the path to the configuration MOF to apply.</span></span>

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

- <span data-ttu-id="e6bfb-177">SetDscLocalConfigurationManager.py</span><span class="sxs-lookup"><span data-stu-id="e6bfb-177">SetDscLocalConfigurationManager.py</span></span>

<span data-ttu-id="e6bfb-178">메타 구성 MOF 파일을 컴퓨터에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-178">Applies a Meta Configuration MOF file to the computer.</span></span> <span data-ttu-id="e6bfb-179">[Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-179">Similar to the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span> <span data-ttu-id="e6bfb-180">적용할 메타 구성 MOF의 경로가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-180">Requires the path to the Meta Configuration MOF to apply.</span></span>

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a><span data-ttu-id="e6bfb-181">Linux용 PowerShell 필요한 상태 구성 로그 파일</span><span class="sxs-lookup"><span data-stu-id="e6bfb-181">PowerShell Desired State Configuration for Linux Log Files</span></span>

<span data-ttu-id="e6bfb-182">Linux용 DSC 메시지용으로 다음 로그 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-182">The following log files are generated for DSC for Linux messages.</span></span>

|<span data-ttu-id="e6bfb-183">로그 파일</span><span class="sxs-lookup"><span data-stu-id="e6bfb-183">Log file</span></span>|<span data-ttu-id="e6bfb-184">디렉터리</span><span class="sxs-lookup"><span data-stu-id="e6bfb-184">Directory</span></span>|<span data-ttu-id="e6bfb-185">설명</span><span class="sxs-lookup"><span data-stu-id="e6bfb-185">Description</span></span>|
|---|---|---|
|<span data-ttu-id="e6bfb-186">**omiserver.log**</span><span class="sxs-lookup"><span data-stu-id="e6bfb-186">**omiserver.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="e6bfb-187">OMI CIM 서버의 작업에 관한 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-187">Messages relating to the operation of the OMI CIM server.</span></span>|
|<span data-ttu-id="e6bfb-188">**dsc.log**</span><span class="sxs-lookup"><span data-stu-id="e6bfb-188">**dsc.log**</span></span>|`/var/opt/omi/log`|<span data-ttu-id="e6bfb-189">LCM(로컬 구성 관리자)의 작업 및 DSC 리소스 작업에 대한 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="e6bfb-189">Messages relating to the operation of the Local Configuration Manager (LCM) and DSC resource operations.</span></span>|
