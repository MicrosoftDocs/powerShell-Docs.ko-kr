---
title: PowerShell 7.1의 새로운 기능
description: PowerShell 7.1에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577210"
---
# <a name="whats-new-in-powershell-71"></a>PowerShell 7.1의 새로운 기능

2020년 11월 11일에 PowerShell 7.1의 일반 공급을 [발표](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/)했습니다. PowerShell 7.0에 구축된 토대를 기반으로 하여 커뮤니티에서 보고된 문제에 초점을 맞춘 노력을 통해 다수의 개선 사항 및 수정 사항을 포함합니다. Microsoft에서는 PowerShell을 안정적이고 성능이 뛰어난 플랫폼으로 유지하기 위해 최선을 다하고 있습니다.

PowerShell 7.1에는 다음과 같은 기능, 업데이트, 호환성이 손상되는 변경이 포함되어 있습니다.

- 예측 IntelliSense를 포함하는 PSReadLine 2.1.0
- PowerShell 7.1이 Microsoft Store에 게시됨
- ARM64 지원과 함께 새 OS 버전용으로 업데이트된 설치 프로그램 패키지
- 4개의 새로운 실험적 기능 및 2개의 실험적 기능이 기본 기능으로 승격됨
- 유용성 향상을 위한 몇 가지 호환성이 손상되는 변경

전체 변경 내용 목록은 GitHub 리포지토리에서 [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md)를 참조하세요.

## <a name="psreadline-210"></a>PSReadLine 2.1.0

PowerShell 7.1에는 PSReadLine 2.1.0도 포함되어 있습니다. 이 버전은 예측 IntelliSense를 포함합니다. 예측 IntelliSense 기능에 대한 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/)를 참조하세요.

## <a name="microsoft-store-installer-package"></a>Microsoft Store 설치 프로그램 패키지

PowerShell 7.1이 Microsoft Store에 게시되었습니다. 이 PowerShell 릴리스는 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 웹 사이트 또는 Windows의 Microsoft Store 애플리케이션에서 찾을 수 있습니다.

Microsoft Store 패키지의 이점:

- Windows 10에 바로 기본 제공되는 자동 업데이트
- Intune 및 SCCM과 같은 기타 소프트웨어 배포 메커니즘과 통합

> [!NOTE]
> `$PSHOME`에 저장된 시스템 수준 구성 설정은 수정할 수 없습니다. 여기에는 WSMAN 구성이 포함됩니다. 그러므로 원격 세션에서 PowerShell의 저장소 기반 설치에 연결할 수 없습니다. 사용자 수준 구성 및 SSH 원격 기능을 지원합니다.

## <a name="other-installers"></a>다른 설치 프로그램

지원되는 운영 체제 및 지원 주기에 대한 최신 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle)를 참조하세요.

기본 운영 체제에 대한 설치 지침을 확인하세요.

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

또한 PowerShell 7.1은 Debian, Ubuntu 및 ARM64 Alpine Linux의 ARM32 및 ARM64 버전을 지원합니다.

공식적으로 지원되는 것은 아니지만 커뮤니티는 [Arch](https://aur.archlinux.org/packages/powershell/) 및 Kali Linux에 대한 패키지도 제공했습니다.

> [!NOTE]
> Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine, ARM은 현재 WinRM 원격 기능을 지원하지 않습니다. SSH 기반 원격을 설정하는 방법에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조하세요.

## <a name="experimental-features"></a>실험적 기능

실험적 기능에 대한 자세한 내용은 [실험적 기능 사용](../learn/experimental-features.md)을 참조하세요.

이제 이 릴리스에서는 다음과 같은 실험적 기능이 기본 기능입니다.

- [PSNullConditionalOperators](../learn/experimental-features.md#psnullconditionaloperators)
- [PSUnixFileStat](../learn/experimental-features.md#psunixfilestat)

이 릴리스에는 다음과 같은 실험적 기능이 추가되었습니다.

- [Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - PowerShell 7.1은 이 실험적 기능을 확장하여 **Runspace** 매개 변수를 모든 `*-PSBreakpoint` cmdlet에 추가합니다. **Runspace** 매개 변수는 지정된 Runspace에서 중단점과 상호 작용할 **Runspace** 개체를 지정합니다.

- [PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - 이 기능을 사용하면 PowerShell 경로 구문을 지원하지 않는 네이티브 명령에 PowerShell 공급자 경로를 전달할 수 있습니다.

- [PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - `-replace` 연산자 문의 왼쪽 피연산자가 문자열이 아닌 경우 해당 피연산자는 문자열로 변환됩니다. 기능을 사용하도록 설정하면, 변환에서 문자열 변환용 문화권 설정이 사용되지 않습니다.

- [PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel)은 향후 예측 IntelliSense 플러그 인을 지원하기 위한 토대를 마련합니다.

## <a name="breaking-changes-and-improvements"></a>주요 변경 내용 및 개선 사항

- 네이티브 명령이 `stderr`에 쓸 때 `$false`가 되지 않도록 `$?` 수정([#13395](https://github.com/PowerShell/PowerShell/pull/13395))

  실패를 표시하지 않고 네이티브 명령이 `stderr`에 쓰는 것은 일반적입니다.
  이 변경에 따라, 네이티브 명령에 0이 아닌 종료 코드가 있는 경우에만 `$?`가 `$false`로 설정됩니다. 이 변경 내용은 실험적 기능 `PSNotApplyErrorActionToStderr`과 관련이 없습니다.

- `$ErrorActionPreference`가 네이티브 명령의 `stderr` 출력에 영향을 주지 않도록 설정([#13361](https://github.com/PowerShell/PowerShell/pull/13361))

  실패를 표시하지 않고 네이티브 명령이 `stderr`에 쓰는 것은 일반적입니다.
  이 변경에 따라, `stderr` 출력이 **ErrorRecord** 개체에서 계속 캡처되지만, 네이티브 명령에서 **ErrorRecord** 가 제공되는 경우 런타임이 더 이상 `$ErrorActionPreference`에 적용되지 않습니다.

- `Get-Date`에서 `-FromUnixTime` 이름을 `-UnixTimeSeconds`로 변경하여 Unix 시간 입력을 허용([#13084](https://github.com/PowerShell/PowerShell/pull/13084))(@aetos382에게 감사드립니다!)

  `-FromUnixTime` 매개 변수가 7.1-preview.2 중에 추가되었습니다. 매개 변수의 이름이 데이터 형식과 좀 더 일치하도록 변경되었습니다. 이 매개 변수는 1970년 1월 1일, 0:00:00 이후의 시간(초)을 나타내는 정수 값을 사용합니다.

  이 예에서는 Unix 시간(1970-01-01 0:00:00 이후의 초로 표시됨)을 DateTime으로 변환합니다.

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- 명시적으로 지정된 명명된 매개 변수가 해시 테이블 스플래팅의 동일한 매개 변수를 대체하도록 허용(#13162)

  이 변경에 따라, 스플래팅의 명명된 매개 변수는 매개 변수 목록의 끝으로 이동하며 명시적으로 지정된 명명된 매개 변수가 모두 바인딩된 후에 바인딩됩니다. 지정된 명명된 매개 변수를 찾을 수 없는 경우 간단한 함수에 대한 매개 변수 바인딩이 오류를 throw하지 않습니다. 알 수 없는 명명된 매개 변수는 간단한 함수의 `$args` 매개 변수에 바인딩됩니다. 스플래팅이 인수 목록의 끝으로 이동하면 `$args`에서 매개 변수가 표시되는 순서가 변경됩니다.

  예를 들면 다음과 같습니다.

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  이전 동작에서 **MyPath** 는 인수 목록에서 세 번째 인수이므로 `-Path`에 바인딩되지 않습니다. ## 따라서 결국 `Blah = "World"`와 함께 ‘$args’에 채워집니다.

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  이 변경에 따라, `@hash`의 인수가 인수 목록의 끝으로 이동합니다. **MyPath** 는 목록의 첫 번째 인수가 되기 때문에 `-Path`에 바인딩됩니다.

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- 스위치 매개 변수 `-Qualifier`가 `Split-Path`에 대해 위치를 지정하지 않도록 설정([#12960](https://github.com/PowerShell/PowerShell/pull/12960))(@yecril71pl에게 감사드립니다!)

- 지정되지 않은 경우 작업 디렉터리를 `Start-Process`에 대한 리터럴 경로로 확인([#11946](https://github.com/PowerShell/PowerShell/pull/11946))(@NoMoreFood에게 감사드립니다!)

- 웹 cmdlet의 `-OutFile` 매개 변수가 `-LiteralPath`처럼 작동하도록 설정([#11701](https://github.com/PowerShell/PowerShell/pull/11701))(@iSazonov에게 감사드립니다!)

- `BigInteger` 숫자 리터럴에 대한 문자열 매개 변수 바인딩을 수정([#11634](https://github.com/PowerShell/PowerShell/pull/11634))(@vexx32에게 감사드립니다!)

- Windows에서 `Start-Process`는 현재 세션의 모든 환경 변수를 사용하여 프로세스 환경을 만들고, `-UseNewEnvironment`는 새 기본 프로세스 환경을 만듦([#10830](https://github.com/PowerShell/PowerShell/pull/10830))(@iSazonov에게 감사드립니다!)

- `ScriptBlock`을 대리자로 변환할 때 `PSObject`에서 반환 결과를 래핑하지 않음([#10619](https://github.com/PowerShell/PowerShell/pull/10619))

  C# 컨텍스트에서 사용할 대리자 형식으로 `ScriptBlock`을 변환하는 경우 `PSObject`에서 결과를 래핑하면 불필요한 문제가 발생합니다.

  - 값이 대리자 반환 형식으로 변환되면 `PSObject`는 기본적으로 래핑 해제됩니다. 따라서 `PSObject`는 필요하지 않습니다.
  - 대리자 반환 형식이 `object`인 경우 C# 코드에서 사용할 수 있도록 `PSObject`에 래핑됩니다.

  이 변경 이후에는 반환된 개체가 기본 개체가 됩니다.
