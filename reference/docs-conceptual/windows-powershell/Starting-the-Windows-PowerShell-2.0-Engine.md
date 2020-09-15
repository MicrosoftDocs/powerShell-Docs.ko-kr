---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 2.0 엔진 사용
ms.openlocfilehash: c5ac92159d63e5669643908016186ed32dfb46db
ms.sourcegitcommit: 3e343f005fe76960c998ef1869a1a093d37ef349
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85216025"
---
# <a name="using-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진 사용

Windows PowerShell은 이전 버전과 호환되도록 설계되었습니다. Windows PowerShell 2.0용으로 작성된 cmdlet, 공급자, 스냅인, 모듈 및 스크립트는 Windows PowerShell 신규 버전에서 문제없이 실행됩니다. 그러나 Microsoft .NET Framework 4에서는 런타임 활성화 정책이 변경됩니다.
Windows PowerShell 2.0용으로 작성하고 CLR(공용 언어 런타임) 2.0으로 컴파일한 Windows PowerShell 호스트 프로그램은 CLR 4.0(또는 그 이상)으로 컴파일한 Windows PowerShell 신규 버전에서는 수정해야 실행할 수 있습니다.

Windows PowerShell 2.0 엔진은 기존 스크립트 또는 호스트 프로그램이 Windows PowerShell 5.1과 호환되지 않아 실행할 수 없는 경우에만 사용됩니다. 대표적인 예는 이전 버전의 Exchange 또는 SQL Server 모듈입니다. 이러한 경우는 많지 않을 것으로 예상됩니다.

Windows PowerShell 2.0 엔진을 필요로 하는 대부분의 프로그램은 자동으로 엔진을 시작합니다. 이러한 지침은 엔진을 수동으로 시작해야 하는 드문 경우를 위해 포함되었습니다.

## <a name="deprecation-and-security-concerns"></a>사용 중단 및 보안 우려

Windows PowerShell 2.0은 2017년 8월 부로 사용 중단되었습니다. 자세한 내용은 [공지][]를 참조하세요.

Windows PowerShell 2.0에는 버전 3, 4, 5에서 추가된 강화 및 보안 기능 대부분이 존재하지 않습니다. 되도록 사용하지 않을 것을 강력하게 권장합니다. 자세한 내용은 [셸 및 스크립팅 언어 보안 비교][]와 [PowerShell ♥ the Blue Team][blueteam]을 참조하세요.

## <a name="installing-and-enabling-required-programs"></a>필요한 프로그램 설치 및 사용

Windows PowerShell 2.0 엔진을 시작하기 전에 Windows PowerShell 2.0 엔진과 Microsoft .NET Framework 3.5 서비스 팩 1을 사용하도록 설정합니다. 자세한 내용은 [Windows PowerShell 설치][]를 참조하세요.

Windows Management Framework 3.0 이상이 설치된 시스템에는 필요한 구성 요소가 모두 존재합니다. 추가 구성은 필요하지 않습니다. Windows Management Framework 설치에 대한 자세한 내용은 [WMF 설치 및 구성][]을 참조하세요.

## <a name="how-to-start-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진을 시작하는 방법

Windows PowerShell을 시작하는 경우 기본적으로 최신 버전이 시작됩니다. Windows PowerShell을 Windows PowerShell 2.0 엔진으로 시작하려면 `PowerShell.exe`의 Version 매개 변수를 사용합니다. Windows PowerShell 및 Cmd.exe를 비롯한 모든 명령 프롬프트에서 명령을 실행할 수 있습니다.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진과 원격 세션을 시작하는 방법

원격 세션으로 Windows PowerShell 2.0 엔진을 실행하려면 Windows PowerShell 2.0 엔진을 로드하는 원격 컴퓨터에서 세션 구성(엔드포인트라고도 함)을 만듭니다. 세션 구성은 원격 컴퓨터에 저장되며, Windows PowerShell 2.0 엔진을 사용하는 모든 권한 있는 사용자가 이용할 수 있습니다.

이는 일반적으로 시스템 관리자가 수행하는 고급 작업입니다.

다음 절차에서는 [Register-PSSessionConfiguration][] cmdlet의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하는 세션 구성을 만듭니다. [New-PSSessionConfigurationFile][] cmdlet의 **PowerShellVersion** 매개 변수를 사용하여 Windows PowerShell 2.0 엔진을 로드하는 세션에 대한 세션 구성 파일을 만들 수도 있으며, [Set-PSSessionConfiguration][] 매개 변수의 **PSVersion** 매개 변수를 통해 Windows PowerShell 2.0 엔진을 사용하도록 세션 구성을 변경할 수 있습니다.

세션 구성 파일에 대한 자세한 내용은 [about_Session_Configuration_Files][]를 참조하세요.
설치와 보안을 비롯한 세션 구성에 대한 자세한 내용은 [about_Session_Configurations][]를 참조하세요.

### <a name="to-start-a-remote-windows-powershell-20-session"></a>원격 Windows PowerShell 2.0 세션을 시작하려면

1. Windows PowerShell 2.0 엔진을 필요로 하는 세션 구성을 만들려면 `Register-PSSessionConfiguration` cmdlet의 **PSVersion** 매개 변수에 값 `2.0`을 사용합니다.
   연결의 "서버 쪽" 또는 수신 끝에 있는 컴퓨터에서 이 명령을 실행합니다.

   다음 샘플 명령은 Server01 컴퓨터에서 PS2 세션 구성을 만듭니다. 이 명령을 실행하려면 **관리자 권한으로 실행** 옵션을 사용하여 Windows PowerShell을 시작합니다.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 만들려면 New-PSSession cmdlet 같은 원격 세션을 만드는 cmdlet의 **ConfigurationName** 매개 변수를 사용합니다.

   세션 구성을 사용하는 세션이 시작되면 Windows PowerShell 2.0 엔진이 자동으로 세션에 로드됩니다.

   다음 명령은 PS2 세션 구성을 사용하는 Server01 컴퓨터에서 세션을 시작합니다. 이 명령은 세션을 `$s` 변수에 저장합니다.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하는 방법

Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작하려면 [Start-Job][] cmdlet의 **PSVersion** 매개 변수를 사용합니다.

다음 명령은 Windows PowerShell 2.0 엔진을 사용하여 백그라운드 작업을 시작합니다.

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

백그라운드 작업에 대한 자세한 내용은 [about_Jobs][]를 참조하세요.

<!-- link references -->
[공지]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[셸 및 스크립팅 언어 보안 비교]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Windows PowerShell 설치]: install/Installing-Windows-PowerShell.md
[WMF 설치 및 구성]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfigurationFile
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
