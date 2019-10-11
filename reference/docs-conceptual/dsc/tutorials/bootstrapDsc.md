---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: 초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성
ms.openlocfilehash: f9634c330832e23fb2c6f08c5b299b55a5505ac9
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954610"
---
# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>초기 부팅 시 DSC를 사용하여 가상 컴퓨터 구성

> [!IMPORTANT]
> 적용 대상: Windows Powershell 5.0

## <a name="requirements"></a>요구 사항

> [!NOTE]
> PowerShell 4.0에서는 이 항목에서 설명하는 **DSCAutomationHostEnabled** 레지스트리 키를 사용할 수 없습니다.
> PowerShell 4.0에서 초기 부팅 시 새 가상 컴퓨터를 구성하는 방법에 대한 자세한 내용은 [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/)(초기 부팅 시 DSC를 사용하여 컴퓨터를 자동으로 구성하고 싶나요?)을 참조하세요.

이러한 예제를 실행하려면 다음이 필요합니다.

- 작업할 부팅 가능한 VHD. [TechNet Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016)에서 Windows Server 2016 평가판이 포함된 ISO를 다운로드할 수 있습니다.
  ISO 이미지에서 VHD를 만드는 방법에 지침은 [Creating Bootable Virtual Hard Disks](/previous-versions/windows/it-pro/windows-7/gg318049(v=ws.10))(부팅 가능한 가상 하드 디스크 만들기)에서 확인할 수 있습니다.
- Hyper-V 사용하도록 설정한 호스트 컴퓨터. 자세한 내용은 [Hyper-V 개요](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831531(v=ws.11))를 참조하세요.

  DSC를 사용하면 초기 부팅 시 컴퓨터에서 소프트웨어 설치 및 구성을 자동화할 수 있습니다.
  이렇게 하려면 구성 MOF 문서 또는 메타 구성을 부팅 가능한 미디어(예: VHD)에 삽입하여 초기 부팅 과정 중 실행되게 합니다.
  이 동작은 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System` 아래에 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키로 지정합니다.
  기본적으로 이 키의 값은 2이며, 이 경우 DSC가 부팅 시 실행될 수 있습니다.

  부팅 시 DSC가 실행되지 않게 하려면 [DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md) 레지스트리 키 값을 0으로 설정합니다.

- 구성 MOF 문서를 VHD에 삽입
- DSC 메타 구성을 VHD에 삽입
- 부팅 시 DSC를 사용하지 않도록 설정

> [!NOTE]
> `Pending.mof` 및 `MetaConfig.mof` 모두를 컴퓨터에 동시에 삽입할 수 있습니다.
> 두 파일 모두 있는 경우 `MetaConfig.mof`에 지정된 설정이 우선합니다.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>구성 MOF 문서를 VHD에 삽입

초기 부팅 시 구성을 시행하려면 컴파일된 구성 MOF 문서를 VHD에 `Pending.mof` 파일로 삽입할 수 있습니다.
**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 컴퓨터가 처음으로 부팅할 때 DSC에서 `Pending.mof`에 정의된 구성을 적용합니다.

이 예제에서는 새 컴퓨터에 IIS를 설치하는 다음 구성을 사용합니다.

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>구성 MOF 문서를 VHD에 삽입하려면

1. 구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다. 예:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 구성(**SampleIISInstall**)을 PowerShell 스크립트(.ps1) 파일로 저장합니다.

3. PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.

4. 다음 PowerShell 명령을 실행하여 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).

   ```powershell
   . .\SampleIISInstall.ps1
   SampleIISInstall
   ```

5. 그러면 `localhost.mof` 파일이 `SampleIISInstall`이라는 폴더에 만들어집니다.
   이 파일을 `Pending.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다. 예:

   ```powershell
       Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
   ```

6. [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다. 예:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

7. DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.

초기 부팅 및 운영 체제 설치 후에 IIS가 설치됩니다.
이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>DSC 메타 구성을 VHD에 삽입

또한 메타 구성([LCM(로컬 구성 관리자) 구성](../managing-nodes/metaConfig.md) 참조)을 VHD에 `MetaConfig.mof` 파일로 삽입하여 초기 부팅 시 구성을 가져오도록 컴퓨터를 구성할 수도 있습니다.
**DSCAutomationHostEnabled** 레지스트리 키가 2(기본값)로 설정된 경우 컴퓨터가 처음으로 부팅할 때 DSC에서 `MetaConfig.mof`에 정의된 구성을 LCM에 적용합니다.
메타 구성에서 LCM이 끌어오기 서버로부터 구성을 가져오도록 지정하는 경우 컴퓨터에서는 초기 부팅 시 해당 끌어오기 서버로부터 구성을 가져오려고 합니다.
DSC 끌어오기 서버 설정에 대한 자세한 내용은 [DSC 웹 끌어오기 서버 설정](../pull-server/pullServer.md)을 참조하세요.

이 예제에서는 이전 섹션에 설명된 구성(**SampleIISInstall**) 및 다음 메타 구성을 모두 사용합니다.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>메타 구성 MOF 문서를 VHD에 삽입하려면

1. 메타 구성을 삽입할 VHD를 [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 탑재합니다. 예:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. [웹 DSC 끌어오기 서버를 설정](../pull-server/pullServer.md)하고, **SampleIISInstall** 구성을 적절한 폴더에 저장합니다.

3. PowerShell 5.0 이상을 실행하는 컴퓨터에서 위의 메타 구성(**PullClientBootstrap**)을 PowerShell 스크립트(.ps1) 파일로 저장합니다.

4. PowerShell 콘솔에서 .ps1 파일을 저장한 폴더로 이동합니다.

5. 다음 PowerShell 명령을 실행하여 메타 구성 MOF 문서를 컴파일합니다(DSC 구성 컴파일에 대한 자세한 내용은 [DSC 구성](../configurations/configurations.md) 참조).

   ```powershell
   . .\PullClientBootstrap.ps1
   PullClientBootstrap
   ```

6. 그러면 `localhost.meta.mof` 파일이 `PullClientBootstrap`이라는 폴더에 만들어집니다.
   이 파일을 `MetaConfig.mof`로 이름을 바꾸고 [Move-item](/powershell/module/microsoft.powershell.management/move-item) cmdlet을 사용하여 VHD에서 적절한 위치로 이동합니다.

   ```powershell
   Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\System32\Configuration\MetaConfig.mof
   ```

7. [Dismount-VHD](/powershell/module/hyper-v/dismount-vhd) cmdlet을 호출하여 VHD를 분리합니다. 예:

   ```powershell
   Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

8. DSC MOF 문서를 설치한 VHD를 사용하여 VM을 만듭니다.

초기 부팅 및 운영 체제 설치 후에 DSC가 끌어오기 서버로부터 구성을 가져오면 IIS가 설치됩니다.
이 작업은 [Get-WindowsFeature](/powershell/module/servermanager/get-windowsfeature) cmdlet을 호출하여 확인할 수 있습니다.

## <a name="disable-dsc-at-boot-time"></a>부팅 시 DSC를 사용하지 않도록 설정

기본적으로 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System\DSCAutomationHostEnabled` 키 값은 2로 설정되며, 이 경우 컴퓨터가 보류 중이거나 현재 상태이면 DSC 구성을 실행할 수 있습니다. 초기 부팅 시 구성이 실행되지 않게 하려면 이 키 값을 0으로 설정해야 합니다.

1. [Mount-VHD](/powershell/module/hyper-v/mount-vhd) cmdlet을 호출하여 VHD를 탑재합니다. 예:

   ```powershell
   Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
   ```

2. `reg load`를 호출하여 VHD에서 레지스트리 `HKLM\Software` 하위 키를 로드합니다.

   ```powershell
   reg load HKLM\Vhd E:\Windows\System32\Config\Software`
   ```

3. PowerShell 레지스트리 공급자를 사용하여 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`으로 이동합니다.

   ```powershell
   Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies\System`
   ```

4. `DSCAutomationHostEnabled` 값을 0으로 변경합니다.

   ```powershell
   Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
   ```

5. 다음 명령을 실행하여 레지스트리를 언로드합니다.

   ```powershell
   [gc]::Collect()
   reg unload HKLM\Vhd
   ```

## <a name="see-also"></a>참고 항목

[DSC 구성](../configurations/configurations.md)

[DSCAutomationHostEnabled 레지스트리 키](DSCAutomationHostEnabled.md)

[LCM(로컬 구성 관리자) 구성](../managing-nodes/metaConfig.md)

[DSC 웹 끌어오기 서버 설정](../pull-server/pullServer.md)
