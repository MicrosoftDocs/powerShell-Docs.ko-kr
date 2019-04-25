---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC on Nano Server 사용
ms.openlocfilehash: ac5eaf3885788f40e12e4f0a0f19025668280f7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079730"
---
# <a name="using-dsc-on-nano-server"></a>DSC on Nano Server 사용

> 적용 대상: Windows Powershell 5.0

**DSC on Nano Server**는 Windows Server 2016 미디어의 `NanoServer\Packages` 폴더에 있는 선택적 패키지입니다. 이 패키지는 **Microsoft-NanoServer-DSC-Package**를 **New-NanoServerImage** 함수의 **Packages** 매개 변수 값으로 지정하여 Nano Server에 대한 VHD를 만들 때 설치할 수 있습니다. 예를 들어 가상 컴퓨터에 대한 VHD를 만드는 경우 다음과 같은 명령을 사용합니다.

```powershell
New-NanoServerImage -Edition Standard -DeploymentType Guest -MediaPath f:\ -BasePath .\Base -TargetPath .\Nano1\Nano.vhd -ComputerName Nano1 -Packages Microsoft-NanoServer-DSC-Package
```

Nano Server 설치 및 사용과 PowerShell 원격으로 Nano Server를 관리하는 방법은 [Getting Started with Nano Server(Nano Server 시작)](/windows-server/get-started/getting-started-with-nano-server)를 참조하세요.

## <a name="dsc-features-available-on-nano-server"></a>Nano Server에서 사용할 수 있는 DSC 기능

Nano Server는 처음 사용자용 Windows Server에 비해 제한된 일부 API만 지원하기 때문에 당분간은 전체 SKU에서 동작하는 완전한 기능을 하는 패리티가 DSC on Nano Server에 없습니다. DSC on Nano Server는 개발 중이므로 아직 모든 기능이 완성되지 않았습니다.

다음 DSC 기능은 현재 Nano Server에서 사용할 수 있습니다.

밀어넣기 및 끌어오기 모드

- 다음을 포함하여 Windows Server 전체 버전에 있는 모든 DSC cmdlet:
- [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager)
- [Set-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager)
- [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug)
- [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug)
- [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)
- [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration)
- [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration)
- [Test-DscConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)
- [Publish-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration)
- [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration)
- [Restore-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Restore-DscConfiguration)
- [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument)
- [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus)
- [Invoke-DscResource](/powershell/module/PSDesiredStateConfiguration/Invoke-DscResource)
- [Find-DscResource](https://technet.microsoft.com/en-us/library/mt517874.aspx)
- [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)
- [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum)

- 구성 컴파일([DSC 구성](../configurations/configurations.md) 참조)

  **문제:** 구성 컴파일 중 암호 암호화([MOF 파일 보안](../pull-server/secureMOF.md) 참조)가 작동하지 않습니다.

- 메타 구성 컴파일([로컬 구성 관리자 구성](../managing-nodes/metaConfig.md) 참조)

- 사용자 컨텍스트에서 리소스 실행([사용자 자격 증명을 사용하여 DSC 실행(RunAs)](../configurations/runAsUser.md) 참조)

- 클래스 기반 리소스([PowerShell 클래스를 사용하여 사용자 지정 DSC 리소스 작성](../resources/authoringResourceClass.md) 참조)

- DSC 리소스 디버깅([DSC 리소스 디버그](../troubleshooting/debugResource.md) 참조)

  **문제:** 리소스가 PsDscRunAsCredential을 사용 중인 경우 작동하지 않습니다([사용자 자격 증명을 사용하여 DSC 실행](../configurations/runAsUser.md) 참조).

- [노드 간 종속성 지정](../configurations/crossNodeDependencies.md)

- [리소스 버전 관리](../configurations/sxsResource.md)

- 끌어오기 클라이언트(구성 및 리소스)([구성 이름을 사용하여 끌어오기 클라이언트 설정](../pull-server/pullClientConfigNames.md) 참조)

- [부분 구성(끌어오기 및 밀어넣기)](../pull-server/partialConfigs.md)

- [끌어오기 서버에 보고](../pull-server/reportServer.md)

- MOF 암호화

- 이벤트 로깅

- Azure 자동화 DSC 보고

- 올바르게 작동하는 리소스

- **Archive**
- **Environment**
- **File**
- **Log**
- **ProcessSet**
- **Registry**
- **Script**
- **WindowsPackageCab**
- **WindowsProcess**
- **WaitForAll**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)
- **WaitForAny**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)
- **WaitForSome**([노드 간 종속성 지정](../configurations/crossNodeDependencies.md) 참조)

- 부분적으로 작동하는 리소스
- **그룹**
- **GroupSet**

  **문제:** 특정 인스턴스를 두 번 호출하는 경우(동일한 구성을 두 번 실행) 위의 리소스가 실패합니다.

- **Service**
- **ServiceSet**

  **문제:** 서비스 시작/중지(상태) 서비스에 대해서만 작동합니다. 시작 유형, 자격 증명, 설명 등과 같은 다른 서비스 특성을 변경하려고 하면 실패합니다. 발생하는 오류는 다음과 같습니다.

  *유형[management.managementobject]을 찾을 수 없습니다. 이 유형이 포함된 어셈블리가 로드되어 있는지 검증하세요.*

- 작동하지 않는 리소스
- **User**

## <a name="dsc-features-not-available-on-nano-server"></a>Nano Server에서 사용할 수 없는 DSC 기능

다음 DSC 기능은 현재 Nano Server에서 사용할 수 없습니다.

- 암호화된 암호를 사용한 MOF 문서 암호 해독
- 끌어오기 서버--현재는 Nano Server에서 끌어오기 서버를 설정할 수 없습니다.
- 동작 기능 목록에 없는 모든 기능

## <a name="using-custom-dsc-resources-on-nano-server"></a>Nano Server에서 사용자 지정 DSC 리소스 사용

Nano Server에서 사용할 수 있는 Windows API 집합과 CLR 라이브러리가 한정되어 있기 때문에 Windows 전체 CLR 버전에서 동작하는 DSC 리소스가 Nano Server에서 동작하지 않을 수도 있습니다.
DSC 사용자 지정 리소스를 프로덕션 환경에 배포하기 전에 종단 간 테스트를 완료하세요.

## <a name="see-also"></a>참고 항목

- [Nano Server 시작](/windows-server/get-started/getting-started-with-nano-server)
