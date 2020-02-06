---
ms.date: 02/03/2020
keywords: powershell,core
title: PowerShell 6.0의 알려진 문제
ms.openlocfilehash: e9550e3db53865cfc2713d1d80665cced6f0d47a
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996114"
---
# <a name="known-issues-for-powershell-60"></a>PowerShell 6.0의 알려진 문제

## <a name="known-issues-for-powershell-on-non-windows-platforms"></a>비 Windows 플랫폼에서 PowerShell의 알려진 문제

Linux 및 macOS의 PowerShell 알파 릴리스는 대부분 작동하지만 몇 가지 중요한 제한 사항과 유용성 문제가 있습니다. Linux 및 macOS의 PowerShell 베타 릴리스는 알파 릴리스보다 더 기능이 뛰어나고 안정적이지만, 여전히 일부 기능이 없고 버그를 포함할 수 있습니다. 경우에 따라 이러한 문제는 단순히 아직 수정되지 않은 버그입니다. ls, cp 등의 기본 별칭으로 식별되는 기타 경우에서는 Microsoft의 선택과 관련해서 커뮤니티의 피드백에 귀를 기울이고 있습니다.

참고: 여러 기본 하위 시스템의 유사성 때문에 Linux 및 macOS의 PowerShell은 기능과 버그 둘 다에서 동일한 완성도를 공유하는 경향이 있습니다. 아래에 언급된 경우를 제외하고 이 섹션의 문제는 두 운영 체제에 모두 적용됩니다.

### <a name="case-sensitivity-in-powershell"></a>PowerShell의 대/소문자 구분

지금까지 PowerShell은 몇 가지 예외를 제외하고 대/소문자를 구분하지 않았습니다. UNIX 유사 운영 체제에서는 파일 시스템이 대체로 대/소문자를 구분하므로 PowerShell도 파일 시스템의 표준을 준수합니다. 이러한 변화는 명확하거나 명확하지 않은 여러 가지 방식으로 나타납니다.

#### <a name="directly"></a>직접

- PowerShell에서 파일을 지정할 때 올바른 대/소문자를 사용해야 합니다.

#### <a name="indirectly"></a>간접적

- 스크립트가 모듈을 로드하려고 할 때 모듈 이름의 대/소문자가 올바르지 않으면 모듈이 로드되지 않습니다. 모듈이 참조된 이름이 실제 파일 이름과 일치하지 않을 경우, 이로 인해 기존 스크립트에서 문제가 발생할 수 있습니다.
- 파일 이름 대/소문자가 잘못된 경우 탭 완성이 자동으로 완료되지 않습니다. 완성할 조각의 대/소문자가 올바르게 지정되어야 합니다. 형식 이름 및 형식 멤버 완성의 경우 완성 기능에서 대/소문자를 구분하지 않습니다.

### <a name="ps1-file-extensions"></a>.PS1 파일 확장명

PowerShell 스크립트는 `.ps1`로 끝나야 인터프리터가 현재 프로세스에서 스크립트를 로드 및 실행하는 방법을 해석할 수 있습니다. 현재 프로세스에서 스크립트를 실행하는 것이 PowerShell의 일반적인 예상 동작입니다. `.ps1` 확장명이 없는 스크립트에 `#!` 매직 넘버를 추가할 수 있지만, 이로 인해 스크립트가 새 PowerShell 인스턴스에서 실행되므로 개체를 교환할 때 스크립트가 올바르게 작동할 수 없게 됩니다. 참고: `bash` 또는 다른 셸에서 PowerShell 스크립트를 실행할 때는 적합한 동작일 수 있습니다.

### <a name="missing-command-aliases"></a>명령 별칭 누락

Linux/macOS에서는 기본 명령의 “편리한 별칭”인 `ls`, `cp`, `mv`, `rm`, `cat`, `man`, `mount`, `ps`가 제거되었습니다. Windows의 PowerShell에서는 사용자 편의를 위해 Linux 명령 이름에 매핑되는 별칭 집합을 제공합니다. 이러한 별칭이 Linux/macOS 배포의 기본 PowerShell에서 제거되었으므로, 경로를 지정하지 않고 네이티브 실행 파일을 실행할 수 있습니다.

이 변화에는 장/단점이 있습니다. 별칭을 제거할 경우, 네이티브 명령 환경이 PowerShell 사용자에게 노출되지만, 네이티브 명령은 개체 대신 문자열을 반환하기 때문에 셸의 기능이 감소합니다.

> [!NOTE]
> PowerShell 팀이 원하는 피드백은 바로 이 영역에 대한 것입니다. 선호하는 해결 방법은 무엇인가요?
> 현재 상태대로 유지하는 것이 나을까요, 아니면 편리한 별칭을 다시 추가하는 것이 나을까요? [문제 #929](https://github.com/PowerShell/PowerShell/issues/929)를 참조하세요.

### <a name="missing-wildcard-globbing-support"></a>와일드카드 지원 누락

현재, PowerShell은 Windows의 기본 제공 cmdlet 및 Linux의 cmdlet과 외부 명령 또는 이진에 대해서만 와일드카드 확장을 수행합니다. 따라서 `ls
*.txt`와 같은 명령은 별표가 파일 이름과 일치하도록 확장되지 않으므로 실패합니다. `ls (gci *.txt | % name)` 또는 더 간단하게 `ls`에 해당하는 PowerShell 기본 제공 구문을 사용하여 `gci *.txt`를 수행하면 이 문제를 해결할 수 있습니다.

Linux/macOS의 와일드카드 환경을 개선하는 방법에 대한 피드백을 제공하려면 [#954](https://github.com/PowerShell/PowerShell/issues/954)를 참조하세요.

### <a name="net-framework-vs-net-core-framework"></a>.NET Framework 및 .NET Core Framework

Linux/macOS의 PowerShell은 Microsoft Windows의 전체 .NET Framework 하위 집합인 .NET Core를 사용합니다. PowerShell을 통해 기본 프레임워크 형식, 메서드 등에 직접 액세스하기 때문에 이러한 차이는 중요합니다. 그 결과로, Windows에서 실행되는 스크립트가 프레임워크의 차이로 인해 비 Windows 플랫폼에서는 실행되지 않을 수 있습니다. .NET Core Framework에 대한 자세한 내용은 [dotnetfoundation](https://dotnetfoundation.org/)을 참조하세요.

[.NET Standard 2.0](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)이 도입되면서, .NET Core 2.0에서는 전체 .NET Framework에 있는 기존의 여러 형식과 메서드를 다시 가져옵니다. 따라서 PowerShell Core에서 기존의 여러 Windows PowerShell 모듈을 수정 없이 로드할 수 있습니다. [여기](https://github.com/PowerShell/PowerShell/projects/4)에서 .NET Standard 2.0 관련 작업을 확인할 수 있습니다.

### <a name="redirection-issues"></a>리디렉션 문제

입력 리디렉션은 모든 플랫폼의 PowerShell에서 지원되지 않습니다.
[문제 #1629](https://github.com/PowerShell/PowerShell/issues/1629)

`Get-Content`를 사용하여 파일 내용을 파이프라인에 씁니다.

기본 UTF-8 인코딩을 사용하는 경우 리디렉션된 출력에는 유니코드 BOM(바이트 순서 표시)이 포함됩니다. BOM을 예상하지 않는 유틸리티를 사용하거나 파일에 추가하는 경우 BOM으로 인해 문제가 발생합니다. BOM이 없는 ASCII 텍스트를 작성하려면 `-Encoding Ascii`을 사용합니다.

> [!Note]
> 모든 플랫폼에 걸쳐 PowerShell Core의 인코딩 환경 개선에 대한 피드백을 제공하려면 [RFC0020](https://github.com/PowerShell/PowerShell-RFC/issues/71)을 참조하세요. BOM 없이 UTF-8을 지원하기 위해 노력하고 있으며 여러 플랫폼에서 다양한 cmdlet의 인코딩 기본값이 변경될 수 있습니다.

### <a name="job-control"></a>작업 제어

Linux/macOS의 PowerShell에는 작업 제어 지원이 없습니다.
`fg` 및 `bg` 명령을 사용할 수 없습니다.

작업 제어가 지원될 때까지, 모든 플랫폼에서 작동하는 [PowerShell 작업](/powershell/module/microsoft.powershell.core/about/about_jobs)을 사용할 수 있습니다.

### <a name="remoting-support"></a>원격 지원

현재, PowerShell Core는 macOS 및 Linux의 기본 인증과 Linux의 NTLM 기반 인증을 사용하여 WSMan을 통한 PowerShell 원격(PSRP)을 지원합니다. Kerberos 기반 인증은 지원되지 않습니다.

WSMan 기반 원격 작업은 [psl-omi-provider](https://github.com/PowerShell/psl-omi-provider) 리포지토리에서 수행되고 있습니다.

PowerShell Core는 모든 플랫폼(Windows, macOS 및 Linux)에서 SSH를 통한 PowerShell 원격(PSRP)도 지원합니다. 프로덕션에서 현재 지원되지는 않지만, [여기](../learn/remoting/SSH-Remoting-in-PowerShell-Core.md)에서 설정 방법을 자세히 알아볼 수 있습니다.

### <a name="just-enough-administration-jea-support"></a>JEA(Just-Enough-Administration) 지원

제한된 관리(JEA) 원격 엔드포인트를 만드는 기능은 Linux/macOS의 PowerShell에서 현재 사용할 수 없습니다. 이 기능은 현재 6.0의 범위에 없으며, 상당한 디자인 작업이 필요하므로 6.0 이후에 고려될 예정입니다.

### <a name="sudo-exec-and-powershell"></a>`sudo`, `exec` 및 PowerShell

PowerShell은 대부분의 명령(예: Python 또는 Ruby)을 메모리에서 실행하므로 PowerShell 기본 제공 기능에서 바로 sudo를 사용할 수 없습니다. 물론, sudo에서 `pwsh`을 실행할 수는 있습니다. sudo를 사용하여 PowerShell 내에서 PowerShell cmdlet을 실행해야 하는 경우(예: `sudo Set-Date 8/18/2016`), `sudo pwsh Set-Date 8/18/2016`을 수행합니다. 마찬가지로, PowerShell 기본 제공 기능을 바로 실행할 수도 없습니다. 대신, `exec pwsh item_to_exec`를 수행해야 합니다.

이 문제는 [#3232](https://github.com/PowerShell/PowerShell/issues/3232)의 일부로 추적되고 있습니다.

### <a name="missing-cmdlets"></a>cmdlet 누락

PowerShell에서 일반적으로 사용할 수 있는 많은 명령(cmdlet)이 Linux/macOS에서는 사용할 수 없습니다. 대부분의 경우 이러한 명령은 해당 플랫폼에서 의미가 없습니다(예: 레지스트리 등의 Windows 특정 기능). 서비스 제어 명령(Get/Start/Stop-Service) 등의 기타 명령은 있지만 작동하지 않습니다. 향후 릴리스에서는 손상된 cmdlet을 수정하고 시간에 따라 새 cmdlet을 추가하여 이러한 문제를 해결할 수 있습니다.

### <a name="command-availability"></a>명령 가용성

다음 표에는 Linux/macOS의 PowerShell에서 작동하지 않는 것으로 알려진 명령이 나와 있습니다.

|명령|작동 상태|메모|
|--------|-----------------|-----|
|`Get-Service`, `New-Service`, `Restart-Service`, `Resume-Service`, `Set-Service`, `Start-Service`, `Stop-Service`, `Suspend-Service`|사용할 수 없음.|이러한 명령은 인식되지 않습니다. 이 문제는 향후 릴리스에서 해결되어야 합니다.|
|`Get-Acl`, `Get-AuthenticodeSignature`, `Get-CmsMessage`, `New-FileCatalog`, `Protect-CmsMessage`, `Set-Acl`, `Set-AuthenticodeSignature`, `Test-FileCatalog`, `Unprotect-CmsMessage`|사용할 수 없습니다.|이러한 명령은 인식되지 않습니다. 이 문제는 향후 릴리스에서 해결되어야 합니다.|
|`Wait-Process`|사용 가능하지만 제대로 작동하지 않습니다. |예를 들어, `Start-Process gvim -PassThru | Wait-Process`는 작동하지 않고, 프로세스를 기다리지 못합니다.|
|`Connect-PSSession`, `Disable-PSRemoting`, `Disable-PSSessionConfiguration`, `Disconnect-PSSession`, `Enable-PSRemoting`, `Enable-PSSessionConfiguration`, `Get-PSSessionCapability`, `Get-PSSessionConfiguration`, `New-PSSessionConfigurationFile`, `Receive-PSSession`, `Register-PSSessionConfiguration`, `Set-PSSessionConfiguration`, `Test-PSSessionConfigurationFile`, `Unregister-PSSessionConfiguration`|사용할 수 없음.|이러한 명령은 인식되지 않습니다. 이 문제는 향후 릴리스에서 해결되어야 합니다.|
|`Get-Event`, `New-Event`, `Register-EngineEvent`, `Remove-Event`, `Unregister-Event`|사용 가능하지만, 사용할 수 있는 이벤트 원본이 없습니다.|PowerShell 이벤트 명령이 있지만, 명령과 함께 사용되는 대부분의 이벤트 원본(예: System.Timers.Timer)은 Linux에서 사용할 수 없으므로 알파 릴리스에서는 명령이 아무 소용도 없습니다.|
|`Set-ExecutionPolicy`|사용 가능하지만 작동하지 않습니다.|이 플랫폼에서 지원되지 않는다는 메시지를 반환합니다. 실행 정책은 사용자가 값비싼 실수를 하지 않도록 방지하는 사용자 중심 “안전 벨트”입니다. 보안 경계가 아닙니다.|
|`New-PSSessionOption`, `New-PSTransportOption`|사용 가능하지만 `New-PSSession`은 작동하지 않습니다.|`New-PSSessionOption` 및 `New-PSTransportOption`은 현재 `New-PSSession`이 작동하는 상태에서 작동하는지 확인되지 않았습니다.|
