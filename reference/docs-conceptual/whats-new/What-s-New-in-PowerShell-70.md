---
title: PowerShell 7.0의 새로운 기능
description: PowerShell 7.0에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 03/04/2020
ms.openlocfilehash: 313ed2b663262b57abd52bfc7378e1f4661dc03a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808404"
---
# <a name="whats-new-in-powershell-70"></a>PowerShell 7.0의 새로운 기능

PowerShell 7.0은 서로 다른 환경 및 하이브리드 클라우드를 관리하도록 빌드된 오픈 소스 플랫폼 간 (Windows, macOS 및 Linux) 버전입니다.

이 릴리스에서는 다음과 같은 다양한 새로운 기능이 도입되었습니다.

- `ForEach-Object -Parallel`을 사용한 파이프라인 병렬 처리
- 새 연산자:
  - 삼항 연산자: `a ? b : c`
  - 파이프라인 체인 연산자: `||` 및 `&&`
  - Null 조건 연산자: `??` 및 `??=`
- 오류 조사를 용이하게 하는 간소화된 동적 오류 보기 및 `Get-Error` cmdlet
- 사용자가 암시적 Windows PowerShell 세션에서 모듈을 가져올 수 있는 호환성 계층
- 자동 새 버전 알림
- PowerShell 7에서 직접 DSC 리소스를 호출하는 기능(실험적)

기능 및 수정 사항의 전체 목록을 보려면 [changelogs](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.0.md)를 참조하세요.

## <a name="where-can-i-install-powershell"></a>PowerShell은 어디에 설치할 수 있나요?

PowerShell 7은 현재 다음과 같은 x64 운영 체제를 지원합니다.

- Windows 8.1 및 10
- Windows Server 2012, 2012 R2, 2016, 2019
- macOS 10.13 이상 버전
- Red Hat Enterprise Linux(RHEL) / CentOS 7
- Fedora 30 이상 버전
- Debian 9
- Ubuntu LTS 16.04 이상 버전
- Alpine Linux 3.8 이상 버전

또한 PowerShell 7.0은 Debian, Ubuntu 및 ARM64 Alpine Linux의 ARM32 및 ARM64 버전을 지원합니다.

기본 운영 체제 [Windows](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7), [macOS](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) 또는 [Linux](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7)에 대한 설치 지침을 확인하세요.

공식적으로 지원되는 것은 아니지만 커뮤니티는 [Arch](https://aur.archlinux.org/packages/powershell/) 및 Kali Linux에 대한 패키지도 제공했습니다.

> [!NOTE]
> Debian 10 및 CentOS 8은 현재 WinRM 원격을 지원하지 않습니다. SSH 기반 원격을 설정하는 방법에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7)을 참조하세요.

지원되는 운영 체제 및 지원 주기에 대한 최신 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle?view=powershell-7)를 참조하세요.

## <a name="running-powershell-7"></a>PowerShell 7 실행

PowerShell 7은 Windows PowerShell과 별도로 디렉터리에 설치됩니다.
이를 통해 Windows PowerShell 5.1과 함께 PowerShell 7을 나란히 실행할 수 있습니다. PowerShell Core 6.x의 경우 PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.

- PowerShell 7은 `%programfiles%\PowerShell\7`에 설치됩니다.
- `%programfiles%\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.

PowerShell 7 설치 관리자 패키지는 이전 버전의 PowerShell Core 6.x를 업그레이드합니다.

- Windows의 PowerShell Core 6.x: `%programfiles%\PowerShell\6`이 `%programfiles%\PowerShell\7`로 대체됩니다.
- Linux: `/opt/microsoft/powershell/6`이 `/opt/microsoft/powershell/7`로 대체됩니다.
- macOS: `/usr/local/microsoft/powershell/6`이 `/usr/local/microsoft/powershell/7`로 대체됩니다.

> [!NOTE]
> Windows PowerShell에서 PowerShell을 시작하는 실행 파일의 이름은 `powershell.exe`입니다. 버전 6 이상에서는 실행 파일 이름이 Side-by-Side 실행을 지원하도록 변경되었습니다. PowerShell 7을 시작하는 새 실행 파일 이름은 `pwsh.exe`입니다. 미리 보기 빌드는 7-preview 디렉터리 아래에 `pwsh` 대신 `pwsh-preview`로 그대로 유지됩니다.

## <a name="improved-backwards-compatibility-with-windows-powershell"></a>Windows PowerShell과의 이전 버전 호환성 개선

PowerShell 7.0은 .NET Core 3.1로 전환하여 기존 Windows PowerShell 모듈과 훨씬 향상된 이전 버전 호환성을 지원합니다. 여기에는 Windows의 일부로 제공되는 다양한 역할 관리 모듈뿐만 아니라 Windows에서 `Out-GridView` 및 `Show-Command` 같은 GUI 기능이 필요한 많은 모듈이 포함됩니다.

Windows의 경우 새 스위치 매개 변수 **UseWindowsPowerShell**이 `Import-Module`에 추가됩니다. 이 스위치는 로컬 Windows PowerShell 프로세스를 사용하여 해당 모듈에 포함된 모든 cmdlet을 암시적으로 실행하는 PowerShell 7의 프록시 모듈을 만듭니다. 자세한 내용은 [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7)을 참조하세요.

Microsoft 모듈에서 PowerShell 7.0을 사용하는 방법에 대한 자세한 내용은 [모듈 호환성 표](https://aka.ms/PSModuleCompat)를 참조하세요.

## <a name="parallel-execution-added-to-foreach-object"></a>ForEach-Object에 병렬 실행 추가

컬렉션의 항목을 반복하는 `ForEach-Object` cmdlet은 이제 새로운 **Parallel** 매개 변수를 사용하여 병렬 처리를 기본 제공합니다.

기본적으로 병렬 스크립트 블록은 병렬 작업을 시작한 호출자의 현재 작업 디렉터리를 사용합니다.

다음 예제에서는 로컬 Windows 컴퓨터에 있는 5개의 시스템 로그에서 5만 개의 로그 항목을 검색합니다.

```powershell
$logNames = 'Security','Application','System','Windows PowerShell','Microsoft-Windows-Store/Operational'

$logEntries = $logNames | ForEach-Object -Parallel {
    Get-WinEvent -LogName $_ -MaxEvents 10000
} -ThrottleLimit 5

$logEntries.Count

50000
```

**Parallel** 매개 변수는 각 입력 로그 이름에 대해 병렬로 실행되는 스크립트 블록을 지정합니다.

새로운 **ThrottleLimit** 매개 변수는 지정된 시간에 동시에 실행되는 스크립트 블록 수를 제한합니다. 기본값은 5입니다.

`$_` 변수를 사용하여 스크립트 블록 내의 현재 입력 개체를 나타냅니다. `$using:` 범위를 사용하여 실행 중인 스크립트 블록에 변수 참조를 전달합니다.

자세한 내용은 [ForEach-Object](/powershell/module/microsoft.powershell.core/foreach-object?view=powershell-7)를 참조하세요.

## <a name="ternary-operator"></a>삼항 연산자

PowerShell 7.0에는 단순화된 `if-else` 문처럼 동작하는 삼항 연산자가 도입되었습니다.
PowerShell의 삼항 연산자는 C# 삼항 연산자 구문에서 유사하게 모델링됩니다.

```
<condition> ? <if-true> : <if-false>
```

조건 식이 항상 평가되고 그 결과가 **부울**로 변환되어 다음에 평가되는 분기를 결정합니다.

- `<condition>` 식이 true인 경우 `<if-true>` 식이 실행됩니다.
- `<condition>` 식이 false인 경우 `<if-false>` 식이 실행됩니다.

다음은 그 예입니다.

```powershell
$message = (Test-Path $path) ? "Path exists" : "Path not found"
```

이 예제에서는 경로가 존재하는 경우 **Path exists**가 표시됩니다. 경로가 존재하지 않는 경우 **Path not found**가 표시됩니다.

자세한 내용은 [About If](/powershell/module/microsoft.powershell.core/about/about_if?view=powershell-7)를 참조하세요.

## <a name="pipeline-chain-operators"></a>파이프라인 체인 연산자

PowerShell 7은 `&&` 및 `||` 연산자를 구현하여 조건부로 파이프라인을 연결합니다. 이러한 연산자는 PowerShell에서 "파이프라인 체인 연산자"로 알려져 있으며 **Bash** 및 **Zsh**와 같은 셸에서 AND 및 OR 목록과 비슷하고 Windows 명령 셸(**cmd.exe**)에서 조건 처리 기호와 비슷합니다.

`&&` 연산자는 왼쪽 파이프라인이 성공한 경우 오른쪽 파이프라인을 실행합니다. 반대로, `||` 연산자는 왼쪽 파이프라인이 실패한 경우 오른쪽 파이프라인을 실행합니다.

> [!NOTE]
> 이러한 연산자는 `$?` 및 `$LASTEXITCODE` 변수를 사용하여 파이프라인이 실패했는지 확인합니다. 이렇게 하면 cmdlet 또는 함수뿐만 아니라 네이티브 명령과 함께 사용할 수 있습니다.

여기서는 첫 번째 명령이 성공하고 두 번째 명령이 실행됩니다.

```powershell
Write-Output 'First' && Write-Output 'Second'
```

```Output
First
Second
```

여기서는 첫 번째 명령이 실패하고 두 번째 명령이 실행되지 않습니다.

```powershell
Write-Error 'Bad' && Write-Output 'Second'
```

```Output
Write-Error: Bad
```

여기서는 첫 번째 명령이 성공하고 두 번째 명령이 실행되지 않습니다.

```powershell
Write-Output 'First' || Write-Output 'Second'
```

```Output
First
```

여기서는 첫 번째 명령이 실패했으므로 두 번째 명령이 실행됩니다.

```powershell
Write-Error 'Bad' || Write-Output 'Second'
```

```Output
Write-Error 'Bad'
Second
```

자세한 내용은 [파이프라인 체인 연산자](/powershell/module/microsoft.powershell.core/about/about_pipeline_chain_operators?view=powershell-7)를 참조하세요.

## <a name="null-coalescing-assignment-and-conditional-operators"></a>Null 병합, 할당 및 조건 연산자

PowerShell 7에는 Null 병합 연산자 `??`, Null 조건 할당 `??=`, Null 조건 멤버 액세스 연산자 `?.` 및 `?[]`가 포함되어 있습니다.

### <a name="null-coalescing-operator-"></a>Null 병합 연산자 ??

Null 병합 연산자 `??`는 null이 아닌 경우 왼쪽 피연산자의 값을 반환합니다.
그렇지 않으면 오른쪽 피연산자를 계산하고 그 결과를 반환합니다. `??` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.

```powershell
$x = $null
$x ?? 100
100
```

다음 예제에서는 오른쪽 피연산자가 평가되지 않습니다.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ?? (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-assignment-operator-"></a>Null 조건 할당 연산자 ??=

Null 조건 할당 연산자 `??=`는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우에만 오른쪽 피연산자의 값을 왼쪽 피연산자에 할당합니다. `??=` 연산자는 왼쪽 피연산자가 null이 아닌 것으로 평가되는 경우 오른쪽 피연산자를 계산하지 않습니다.

```powershell
$x = $null
$x ??= 100
$x
100
```

다음 예제에서는 오른쪽 피연산자가 평가되지 않습니다.

```powershell
[string] $todaysDate = '1/10/2020'
$todaysDate ??= (Get-Date).ToShortDateString()
1/10/2020
```

### <a name="null-conditional-member-access-operators--and--experimental"></a>Null 조건 멤버 액세스 ?. 및 ?[] (실험적)

> [!NOTE]
> **PSNullConditionalOperators**라는 실험적 기능입니다. 자세한 내용은 [실험적 기능](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)을 참조하세요.

Null 조건 연산자는 해당 피연산자가 null이 아닌 것으로 평가되는 경우에만 멤버 액세스 `?.` 또는 요소 액세스 `?[]`를 해당 피연산자로 사용할 수 있습니다. 그렇지 않으면 null을 반환합니다.

> [!NOTE]
> PowerShell을 사용하면 `?`를 변수 이름에 포함할 수 있으므로 이러한 연산자를 사용하려면 변수 이름의 공식적인 사양이 필요합니다. 따라서 `{}`를 `${a}`와 같이 변수 이름 주위에 사용하거나 `?`이 변수 이름의 일부인 경우(`${a?}`)에 사용해야 합니다.

다음 예제에서는 멤버 속성 **Status**의 값이 반환됩니다.

```powershell
$Service = Get-Service -Name 'bits'
${Service}?.status
Stopped
```

다음 예제에서는 멤버 이름 **Status**에 액세스하지 않고 null을 반환합니다.

```powershell
$service = $Null
${Service}?.status
```

마찬가지로 `?[]`를 사용하여 요소 값이 반환됩니다.

```powershell
$a = 1..10
${a}?[0]
1
```

피연산자가 null이면 요소에 액세스하지 않고 null이 반환됩니다.

```powershell
$a = $null
${a}?[0]
```

자세한 내용은 [About_Operators](/powershell/module/microsoft.powershell.core/about/about_operators?view=powershell-7)를 참조하세요.

## <a name="new-view-conciseview-and-cmdlet-get-error"></a>새로운 보기 ConciseView 및 cmdlet Get-Error

PowerShell 7.0에서는 새로운 기본 보기 **ConciseView**를 사용하여 대화형 및 스크립트 오류를 쉽게 읽을 수 있도록 오류 메시지의 표시 기능이 향상되었습니다. 보기는 기본 설정 변수 `$ErrorView`를 통해 사용자가 선택할 수 있습니다.

**ConciseView**를 사용하는 경우, 오류가 스크립트 또는 파서에서 발생하지 않은 한 다음과 같은 한 줄 오류 메시지입니다.

```powershell
Get-Childitem -Path c:\NotReal
```

```Output
Get-ChildItem: Cannot find path 'C:\NotReal' because it does not exist
```

스크립트를 실행하는 동안 오류가 발생하거나 구문 분석 오류가 발생하는 경우, PowerShell은 오류, 포인터 및 해당 줄에서 오류 위치를 표시하는 오류 메시지를 포함하는 여러 줄 오류 메시지를 반환합니다. 터미널이 ANSI 색 이스케이프 시퀀스(VT100)을 지원하지 않는 경우 색은 표시되지 않습니다.

![스크립트의 오류 표시](./media/What-s-New-in-PowerShell-70/myscript-error.png)

PowerShell 7의 기본 보기는 **ConciseView**입니다. 이전의 기본 보기는 **NormalView**였으며 기본 설정 변수 `$ErrorView`를 설정하여 선택할 수 있습니다.
 
```powershell
$ErrorView = 'NormalView' # Sets the error view to NormalView
$ErrorView = 'ConciseView' # Sets the error view to ConciseView
```

> [!NOTE]
> 새로운 속성 **ErrorAccentColor**가 `$Host.PrivateData`에 추가되어 오류 메시지의 강조 색 변경을 지원합니다.

새로운 cmdlet `Get-Error`는 원하는 경우 정규화된 오류에 대한 전체 세부 보기를 제공합니다.
기본적으로 이 cmdlet은 발생한 마지막 오류의 내부 예외를 비롯한 전체 세부 정보를 표시합니다.

![Get-Error의 표시](./media/What-s-New-in-PowerShell-70/myscript-geterror.png)

`Get-Error` cmdlet은 기본 제공 변수 `$Error`를 사용하여 파이프라인으로부터 입력을 지원합니다.
`Get-Error`는 파이핑되는 오류를 모두 표시합니다.

```powershell
$Error | Get-Error
```

`Get-Error` cmdlet은 **Newest** 매개 변수를 지원하므로 현재 세션에서 표시하려는 오류 수를 지정할 수 있습니다.

```powershell
Get-Error -Newest 3 # Displays the lst three errors that occurred in the session
```

자세한 내용은 [Get-Error](/powershell/module/microsoft.powershell.utility/get-error?view=powershell-7)를 참조하세요.

## <a name="new-version-notification"></a>새 버전 알림

PowerShell 7은 업데이트 알림을 사용하여 PowerShell 업데이트가 있음을 사용자에게 알립니다.
PowerShell은 하루 한 번 온라인 서비스를 쿼리하여 최신 버전을 사용할 수 있는지 확인합니다.

> [!NOTE]
> 업데이트 확인은 지정된 24시간 동안 첫 번째 세션 중에 발생합니다. 성능상의 이유로 업데이트 확인은 세션 시작 3초 후에 시작됩니다. 알림은 후속 세션이 시작될 때만 표시됩니다.

기본적으로 PowerShell은 버전/분기에 따라 두 가지 알림 채널 중 하나를 구독합니다. 지원되는 GA(일반 공급) 버전의 PowerShell은 업데이트된 GA 릴리스에 대한 알림만 반환합니다. 미리 보기 및 RC(릴리스 후보) 릴리스는 미리 보기, RC 및 GA 릴리스에 대한 업데이트 알림을 제공합니다.

업데이트 알림 동작은 `$Env:POWERSHELL_UPDATECHECK` 환경 변수를 사용하여 변경할 수 있습니다. 지원되는 값은 다음과 같습니다.

- **Default**는 `$Env:POWERSHELL_UPDATECHECK`을 정의 하지 않는 것과 같습니다.
  - GA 릴리스는 GA 릴리스 업데이트를 알림
  - 미리 보기/RC 릴리스는 GA 및 미리 보기 릴리스 업데이트를 알림
- **Off**는 업데이트 알림 기능을 해제합니다.
- **LTS**는 LTS(장기 서비스) GA 릴리스 업데이트만 알립니다.

> [!NOTE]
> 환경 변수 `$Env:POWERSHELL_UPDATECHECK`는 처음으로 설정될 때까지 존재하지 않습니다.

`LTS` 릴리스만 버전 알림을 설정하려면

```powershell
$Env:POWERSHELL_UPDATECHECK = 'LTS'
```

버전 알림을 `Default` 동작으로 설정하려면

```powershell
$Env:POWERSHELL_UPDATECHECK = 'Default'
```

자세한 내용은 [업데이트 알림](/powershell/module/microsoft.powershell.core/about/about_update_notifications?view=powershell-7)을 참조하세요.

## <a name="new-dsc-resource-support-with-invoke-dscresource-experimental"></a>Invoke-DSCResource를 사용한 새로운 DSC 리소스 지원(실험적)

> [!NOTE]
> **PSDesiredStateConfiguration.InvokeDscResource**라는 실험적 기능입니다. 자세한 내용은 [실험적 기능](/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7)을 참조하세요.

`Invoke-DscResource` cmdlet은 지정된 PowerShell DSC(Desired State Configuration) 리소스의 메서드를 실행합니다.

이 cmdlet은 구성 문서를 만들지 않고 DSC 리소스를 직접 호출합니다. 이 cmdlet을 사용하면 구성 관리 제품이 DSC 리소스를 사용하여 Windows 또는 Linux를 관리할 수 있습니다. 이 cmdlet을 사용하면 디버깅을 사용하도록 설정한 상태에서 DSC 엔진이 실행 중일 때에도 리소스를 디버그할 수 있습니다.

이 명령은 Log라는 리소스의 **Set** 메서드를 호출하고 **Message** 속성을 지정합니다.

```powershell
Invoke-DscResource -Name Log -Method Set -ModuleName PSDesiredStateConfiguration -Property @{
  Message = 'Hello World'
}
```

자세한 내용은 [Invoke-DSCResource](/powershell/module/psdesiredstateconfiguration/invoke-dscresource?view=powershell-7)를 참조하세요.

## <a name="breaking-changes-and-improvements"></a>주요 변경 내용 및 개선 사항

### <a name="breaking-changes"></a>주요 변경 내용

- 업데이트 알림이 LTS 및 기본 채널을 지원(#11132)
- Windows PowerShell에서와 같은 방식으로 작동하도록 Test-Connection을 업데이트(#10697)(@vexx32에게 감사드립니다!)
- Preserve $? - ParenExpression, SubExpression 및 ArrayExpression(#11040)
- Start-Job에서 작업 디렉터리를 현재 디렉터리로 설정(#10920)(@iSazonov에게 감사드립니다!)
- 세션 내 문화권 변경에서 $PSCulture를 일관되게 반영(#10138)(@iSazonov에게 감사드립니다!)

### <a name="engine-updates-and-fixes"></a>엔진 업데이트 및 수정

- 원격 시나리오용 중단점 API 기능을 향상(#11312)
- 다른 Runspace로 누수되는 PowerShell 클래스 정의를 수정(#11273)
- 7\.0.0-Preview1에 추가된 FirstOrDefault 기본 형식으로 인한 서식 지정 재발 문제를 수정(#11258)
- PS7 원격 분석에서 추적할 Microsoft 모듈을 추가(#10751)
- 승인된 기능을 비 실험적으로 설정(#11303)
- 해당하는 경우 TargetObject를 사용하도록 ConciseView를 업데이트(#11075)
- CompletionCompleters 공용 메서드에서 NullReferenceException을 수정(#11274)
- 비 Windows 플랫폼에 대한 아파트 스레드 상태 검사를 수정(#11301)
- 프로세스 및 컴퓨터 환경 변수를 연결하는 PSModulePath 설정을 업데이트(#11276)
- .NET Core를 3.1.0으로 변경(#11260)
- $env:PATH 앞에서 $PSHOME 검색을 수정(#11141)
- pwsh가 $env:PSModulePath를 상속하고 powershell.exe를 올바르게 시작하도록 설정(#11057)
- .NET Core 3.1 미리 보기 1로 이동(#10798)
- 파일 시스템 공급자에서 재분석 태그 검사를 리팩터링(#10431)(@iSazonov에게 감사드립니다!)
- 스크립트 로깅에서 CR 및 새 줄을 0x23CE 문자로 바꿈(#10616)
- AppDomain.CurrentDomain.ProcessExit에서 이벤트 처리기를 등록 취소하여 리소스 누수 문제를 수정(#10626)
- 디버그, 오류, 정보, 진행률, 자세한 정보 표시 또는 경고 메시지가 생성될 때 디버거로 중단되도록 ActionPreference.Break 지원을 추가(#8205)(@KirkMunro에게 감사드립니다!)
- .CPL 확장명을 지정하지 않고 PowerShell Core 내에서 제어판 추가 기능을 시작하도록 허용 (#9828)
- -split 연산자(#8960)에서 음수 지원(@ece-jacob-scott에게 감사드립니다!)

### <a name="general-cmdlet-updates-and-fixes"></a>일반 Cmdlet 업데이트 및 수정

- UnixStat 실험적 기능에서 파일 변경 날짜를 설정하기 위해 Raspbian 문제를 수정(#11313)
- ConvertFrom-SecureString에 -AsPlainText를 추가(#11142)
- WinCompat에 대한 WindowsPS 버전 검사를 추가(#11148)
- 일부 WinCompat 시나리오에서 오류 보고를 수정(#11259)
- 네이티브 이진 해결 프로그램 추가(#11032)(@iSazonov에게 감사드립니다!)
- CJK 문자를 올바르게 적용하도록 문자 너비 계산을 업데이트(#11262)
- macOS에 대한 Unblock-File 추가(#11137)
- Get-PSCallStack에서 재발 문제를 수정(#11210)(@iSazonov에게 감사드립니다!)
- Job cmdlet을 사용할 때 ScheduledJob 모듈 자동 로딩을 제거(#11194)
- Get-Error cmdlet에 OutputType을 추가하고 기존 typenames를 유지(#10856)
- SupportsVirtualTerminal 속성에서 null 참조를 수정(#11105)
- Get-WinEvent에서 제한 확인을 추가(#10648)(@iSazonov에게 감사드립니다!)
- StopUpstreamCommandsException 변수가 채워지지 않도록 명령 런타임을 수정(#10840)
- 네이티브 명령에 대해 출력 인코딩을 [Console]::OutputEncoding으로 설정(#10824)
- 예제에서 여러 줄 코드 블록을 지원(#10776)(@Greg-Smulko에게 감사드립니다!)
- Select-String cmdlet에 Culture 매개 변수를 추가(#10943)(@iSazonov에게 감사드립니다!)
- 후행 백슬래시를 포함하는 Start-Job 작업 디렉터리를 수정(#11041)
- ConvertFrom-Json: 기본적으로 컬렉션을 래핑 해제(#10861)(@danstur에게 감사드립니다!)
- -CaseSensitive 및-AsHashtable 스위치를 사용하여 Group-Object cmdlet용 해시 테이블에서 대/소문자 구분(#11030)(@vexx32에게 감사드립니다!)
- 올바른 대/소문자를 가지도록 경로를 다시 작성할 때 파일을 열거할 수 없으면 예외 처리(#11014)
- myCommand 대신 작업을 표시하도록 ConciseView를 수정(#11007)
- 웹 cmdlet이 HTTP 오류 상태를 무시하도록 허용(#10466)(@vdamewood에게 감사드립니다!)
- Get-Command에 대한 둘 이상의 CommandInfo 파이핑을 수정(#10929).
- Windows용 Get-Counter cmdlet 추가(#10933)
- ConvertTo-Json이 [AutomationNull]::Value 및 [NullString]::Value를 $null로 처리하도록 설정(#10957)
- SSH 원격에 대한 ipv6 주소에서 대괄호 제거(#10968)
- pwsh에 보낸 명령이 공백만 있는 경우 충돌 해결(#10977)
- 플랫폼 간 Get-Clipboard 및 Set-Clipboard 추가(#10340)
- 파일 시스템 개체의 원래 경로 설정을 불필요한 후행 슬래시를 포함하지 않도록 수정(#10959)
- ConvertTo-Json에 $null을 지원(#10947)
- Windows에 Out-Printer 명령을 다시 추가(#10906)
- 공백을 포함하는 Start-Job -WorkingDirectory를 수정(#10951)
- PSConfiguration.cs 설정에 Null을 가져올 때 기본 값을 반환(#10963)(@iSazonov에게 감사드립니다!)
- IO 예외를 종료되지 않는 것으로 처리(#10950)
- GraphicalHost 어셈블리를 추가하여 Out-GridView, Show-Command 및 Get-Help -ShowWindow를 사용(#10899)
- Get-HotFix에서 파이프라인을 통해 ComputerName을 가져옴(#10852)(@kvprasoon에게 감사드립니다!)
- 일반 매개 변수를 사용 가능한 것으로 표시하도록 매개 변수에 대한 탭 완성을 수정(#10850)
- GetCorrectCasedPath()을 수정하여 First()를 호출하기 전에 시스템 파일 항목이 반환되는지 먼저 확인(#10930)
- Start-Job에서 작업 디렉터리를 현재 디렉터리로 설정(#10920)(@iSazonov에게 감사드립니다!)
- TabExpansion2를 -CursorColumn을 요구하지 않고 $InputScript.Length로 처리하도록 변경(#10849)
- 호스트가 화면의 행 또는 열을 반환하지 않을 수 있는 경우를 처리(#10938)
- 강조 색을 지원하지 않는 호스트에서 강조 색 사용을 수정(#10937)
- Update-List 명령을 다시 추가(#10922)
- Clear-RecycleBin의 FWLink ID를 업데이트(#10925)
- 탭 완성 도중 파일 특성을 읽을 수 없는 경우 파일 건너뛰기(#10910)
- Windows에서 Clear-RecycleBin을 다시 추가(#10909)
- 출력에 VT 이스케이프 시퀀스를 포함할지 여부를 제어하는 `$env:__SuppressAnsiEscapeSequences`를 추가(#10814)
- -NoEmphasize 매개 변수를 추가하여 Select-String 출력을 색으로 구분(#8963)(@derek-xia에게 감사드립니다!)
- Get-HotFix cmdlet을 다시 추가(#10740)
- PowerShell을 호스트하는 애플리케이션에서 Add-Type을 사용할 수 있도록 설정(#10587)
- LanguagePrimitives.IsNullLike()에서 보다 효과적인 평가 순서를 사용(#10781)(@vexx32에게 감사드립니다!)
- Format-Hex에서 복합 컬렉션 파이프된 입력과 입력의 파이프된 스트림의 처리를 향상(#8674)(@vexx32에게 감사드립니다!)
- SSHConnection 해시 테이블에서 값이 필요한 형식과 일치하지 않는 경우 형식 변환을 사용(#10720)(@SeeminglyScience에게 감사드립니다!)
- -TotalCount가 설정된 경우 Get-Content -ReadCount 0 동작을 수정(#10749)(@eugenesmlv에게 감사드립니다!)
- Get-WinEvent에서 액세스 거부 오류 메시지를 수정(#10639)(@iSazonov에게 감사드립니다!)
- 열거형 또는 형식 제약된 변수 할당에 탭 완성을 사용(#10646)
- 서식 지정 문제를 일으키는 사용하지 않는 SourceLength 원격 속성을 제거(#10765)
- ConvertFrom-StringData에 -Delimiter 매개 변수를 추가(#10665)(@steviecoaster에게 감사드립니다!)
- SSH에서 Invoke-Command를 사용하는 경우 ScriptBlock에 대한 위치 매개 변수를 추가(#10721)(@machgo에게 감사드립니다!)
- 여러 줄이지만 ConciseView에 대한 스크립트 이름이 없는 경우 줄 컨텍스트 정보를 표시(#10746)
- 파일 시스템 공급자에 대한 \\wsl$\ 경로 지원을 추가(#10674)
- 파서에서 누락된 TokenKind.QuestionMark용 토큰 텍스트를 추가(#10706)
- 각 ForEach-Object -Parallel 실행 스크립트의 현재 작업 디렉터리를 호출하는 스크립트와 동일한 위치로 설정 (#10672)
- FindFirstStreamW 및 FindNextStreamW API에 대해 api-ms-win-core-file-l1-2-2.dll을 Kernell32.dll로 바꿈(#10680)(@iSazonov에게 감사드립니다!)
- StrictMode를 더 허용하도록 도움말 서식 스크립트를 조정(#10563)
- New-Service에 SecurityDescriptorSDDL 매개 변수를 추가(#10483)(@kvprasoon에게 감사드립니다!)
- Test-Connection에서 정보 출력을 제거하고 ping 사용을 통합(#10478)(@vexx32에게 감사드립니다!)
- 액세스하지 않고 특수 재분석 지점 읽기(#10662)(@iSazonov에게 감사드립니다!)
- Clear-Host 출력을 터미널로 디렉션(#10681)(@iSazonov에게 감사드립니다!)
- Format-Table 및 -Property를 사용하여 그룹화를 위한 줄 바꿈을 다시 추가(#10653)
- Get-Random의 -InputObject에서 [ValidateNotNullOrEmpty]를 제거하여 빈 문자열을 허용(#10644)
- 제안 시스템 문자열 간격 알고리즘에서 대/소문자를 구분 안 함(#10549)(@iSazonov에게 감사드립니다!)
- ForEach-Object -Parallel 입력 처리에서 null 참조 예외를 수정(#10577)
- PowerShell Core 그룹 정책 정의를 추가(#10468)
- Composability 시나리오에서 사용되는 XTPUSHSGR/XTPOPSGR VT 컨트롤 시퀀스를 지원하도록 콘솔 호스트를 업데이트 (#10208)
- Start-Job에 WorkingDirectory 매개 변수를 추가(#10324)(@davinci26에게 감사드립니다!)
- 중단점 변경 내용을 호스트 runspace 디버거로 잘못 복제하는 이벤트 처리기를 제거(#10503)(@KirkMunro에게 감사드립니다!)
- Microsoft.PowerShell.Commands.NativeMethods P/Invoke API에서 api-ms-win-core-job-12-1-0.dll을 Kernell32.dll로 바꿈(#10417)(@iSazonov에게 감사드립니다!)
- 변수 할당 및 -OutVariable에서 New-Service에 대한 잘못된 출력을 수정(#10444)(@kvprasoon에게 감사드립니다!)
- 공백을 포함하는 종료 코드, 명령줄 매개 변수 및 경로와 관련된 전역 도구 문제를 해결(#10461)
- OneDrive로 재귀를 수정 - SafeFindHandle 형식을 사용하도록 FindFirstFileEx()를 변경(#10405)
- NVDA 화면 판독기가 활성 상태일 때 Windows에서 PSReadLine 자동 로드 건너뛰기(#10385)
- 7\.0.0.0에 대한 기본 제공 PowerShell 모듈 버전을 확대(#10356)
- Add-Type에서 이름이 같은 형식이 이미 있을 경우 오류 throw를 추가(#9609)(@iSazonov에게 감사드립니다!)

### <a name="performance"></a>성능

- Parser.SaveError애서 closure 사용을 금지(#11006)
- 새 Regex 인스턴스를 만들 때 캐싱을 향상(#10657)(@iSazonov에게 감사드립니다!)
- types.ps1xml, typesV3.ps1xml and GetEvent.types.ps1xml에서 PowerShell 기본 제공 형식 데이터 처리를 향상(#10898)
- PSConfiguration.ReadValueFromFile을 더 빠르고 더 메모리 효율적으로 업데이트(#10839)
- runspace 초기화를 위해 약간의 성능 개선을 추가(#10569)(@iSazonov에게 감사드립니다!)
- 일반적으로 사용되는 시나리오에서 ForEach-Object 속도를 개선하고(#10454) 많은 runspace에서 ForEach-Object -Parallel 성능 문제를 수정(#10455)

### <a name="code-cleanup"></a>코드 정리

- Microsoft 표준에 맞게 주석 및 요소 텍스트를 변경(#11304)
- Compiler.cs에서 스타일 문제를 정리(#10368)(@iSazonov에게 감사드립니다!)
- CommaDelimitedStringCollection에 사용되지 않는 형식 변환기를 제거(#11000)(@iSazonov에게 감사드립니다!)
- InitialSessionState.cs의 스타일을 정리(#10865)(@iSazonov에게 감사드립니다!)
- PSSession 클래스에 대해 코드 정리(#11001)
- 작동하지 않는 기능 'Get-Help가 처음 실행될 때 Get-Help에서 Update-Help를 실행'을 제거(#10974)
- 스타일 문제를 수정(#10998)(@iSazonov에게 감사드립니다!)
- 정리: 기본 제공 형식 별칭을 사용(#10882)(@iSazonov에게 감사드립니다!)
- 사용하지 않는 설정 키 ConsolePrompting을 제거하고 ExecutionPolicy 설정을 쿼리할 때 불필요한 문자열 생성을 방지(#10985)
- 일별 빌드에 대한 업데이트 알림 확인을 사용하지 않도록 설정(#10903)(@bergmeister에게 감사드립니다!)
- #10338에서 손실된 디버깅 API를 복구(#10808)
- 더 이상 사용되지 않는 WorkflowJobSourceAdapter 참조를 제거(#10326)(@KirkMunro에게 감사드립니다!)
- PreserveSig 특성을 수정하여 점프 목록 코드에서 COM 인터페이스를 정리(#9899)(@weltkante에게 감사드립니다!)
- -Ia가 -InformationAction common 매개 변수용 별칭이 아닌 이유를 설명하는 주석을 추가(#10703)(@KirkMunro에게 감사드립니다!)
- InvokeCommandCmdlet.cs의 이름을 InvokeExpressionCommand.cs로 변경(#10659)(@kilasuit에게 감사드립니다!)
- 업데이트 알림과 관련된 경미한 코드 정리를 추가(#10698)
- 원격 설치 스크립트에서 사용되지 않는 워크플로 논리를 제거(#10320)(@KirkMunro에게 감사드립니다!)
- 적절한 대/소문자를 사용하도록 도움말 형식을 업데이트(#10678)(@tnieto88에게 감사드립니다!)
- 지난달의 커밋에서 발생하는 CodeFactor 스타일 문제를 정리(#10591)(@iSazonov에게 감사드립니다!)
- PSTernaryOperator 실험적 기능에 대한 설명에서 오타를 수정(#10586)(@bergmeister에게 감사드립니다!)
- ActionPreference.Suspend 열거형 값을 지원되지 않는 예약된 상태로 전환하고 기본 설정 변수에서 ActionPreference.Ignore 사용에 대한 제한을 제거(#10317)(@KirkMunro에게 감사드립니다!)
- ArrayList를 List\<T>로 바꿔 기능 변경 없이 코드를 더 읽기 쉽고 안정적으로 개선(#10333)(@iSazonov에게 감사드립니다!)
- TestConnectionCommand 코드 스타일을 수정(#10439)(@vexx32에게 감사드립니다!)
- AutomationEngine을 정리하고 불필요한 SetSessionStateDrive 메서드 호출을 제거(#10416)(@iSazonov에게 감사드립니다!)
- ConvertTo-Csv 및 ConvertFrom-Csv에 대한 기본 ParameterSetName의 이름을 다시 Delimiter로 변경(#10425)

### <a name="tools"></a>도구

- VS에서 빌드되는 SDKToUse 속성에 대한 기본 설정을 추가(#11085)
- Install-Powershell.ps1: MSI 설치를 사용하기 위한 매개 변수를 추가(#10921)(@MJECloud에게 감사드립니다!)
- install-powershell.ps1용 기본 예제를 추가(#10914)(@kilasuit에게 감사드립니다!)
- Install-PowerShellRemoting.ps1을 사용하여 PowerShellHome 매개 변수에서 빈 문자열을 처리(#10526)(@Orca88에게 감사드립니다!)
- install-powershell.sh에서 /etc/lsb-release를 /etc/os-release로 전환(#10773)(@Himura2la에게 감사드립니다!)
- Windows에서 pwsh.exe 및 pwsh 일별 버전을 확인(#10738)(@centreboard에게 감사드립니다!)
- installpsh-osx.sh에서 불필요한 탭을 제거(#10752)
- 이미 설치된 일별 빌드를 확인하도록 install-powershell.ps1를 업데이트(#10489)

### <a name="tests"></a>테스트

- 안정적이지 않은 DSC 테스트를 보류(#11131)
- 해시 테이블의 키를 올바르게 확인하도록 stringdata 테스트를 수정(#10810)
- 테스트 모듈 언로드(#11061)(@iSazonov에게 감사드립니다!)
- 테스트 URL 재시도 간격을 확대(#11015)
- 테스트 작업을 정확하게 설명하도록 테스트를 업데이트 (#10928)(@romero126에게 감사드립니다!)
- 신뢰도가 낮은 테스트 TestAppDomainProcessExitEvenHandlerNotLeaking을 임시로 건너뜀(#10827)
- 이벤트 처리기 누수 테스트를 안정적으로 개선(#10790)
- CI YAML에서 대/소문자 구분 동기화(#10767)(@RDIL에게 감사드립니다!)
- 이벤트 처리기 누수 문제 해결을 위한 테스트를 추가(#10768)
- Get-ChildItem 테스트를 추가(#10507)(@iSazonov에게 감사드립니다!)
- 정확도를 위해 테스트의 모호한 언어를 스위치에서 매개 변수로 바꿈(#10666)(@romero126에게 감사드립니다!)
- ForEach-Object -Parallel 테스트에 실험적 확인을 추가(#10354)(@KirkMunro에게 감사드립니다!)
- Alpine 유효성 검사에 대한 테스트를 업데이트(#10428)

### <a name="build-and-package-improvements"></a>빌드 및 패키지 개선 사항

- 조정 패키지 빌드에 대한 Nuget 패키지 서명을 수정(#11316)
- PowerShell 갤러리 및 NuGet에서 종속성 업데이트(#11323)
- Microsoft.ApplicationInsights를 2.11.0에서 2.12.0으로 변경(#11305)
- Microsoft.CodeAnalysis.CSharp를 3.3.1에서 3.4.0으로 변경(#11265)
- Debian 10 및 11용 패키지를 업데이트(#11236)
- RC 이전에 실험적 기능만 활성화(#11162)
- macOS 최소 버전 업데이트(#11163)
- NJsonSchema를 10.0.27에서 10.0.28로 변경(#11170)
- Preview.5의 README.md 및 metadata.json에서 링크를 업데이트(#10854)
- PowerShell이 소유한 규정 준수 테스트용 파일 선택(#10837)
- win7x86 msix 패키지 빌드를 허용 (내부 10515)
- 의미 체계 버전을 NormalizeVersion 함수에 전달하도록 허용(#11087)
- .NET Core 프레임워크를 3.1-preview.3으로 변경(#11079)
- /src/Modules에서 PSReadLine을 2.0.0-beta5에서 2.0.0-beta6으로 변경(#11078)
- Newtonsoft.Json을 12.0.2에서 12.0.3으로 변경(#11037)(#11038)
- Debian 10, 11 및 CentOS 8 패키지 추가(#11028)
- ReleaseDate 필드를 사용하여 Build-Info Json 파일을 업로드(#10986)
- .NET Core 프레임워크를 3.1-preview.2로 변경(#10993)
- x86 MSIX 패키지 빌드를 사용(#10934)
- build.psm1에서 dotnet SDK 설치 스크립트 URL을 업데이트(#10927)
- Markdig.Signed를 0.17.1에서 0.18.0으로 변경(#10887)
- ThreadJob을 2.0.1에서 2.0.2으로 변경(#10886)
- MS Store 요구 사항을 충족하도록 AppX Manifest 및 Packaging 모듈을 업데이트(#10878)
- PowerShell SDK용 패키지 참조를 preview.5로 업데이트(내부 10295)
- ThirdPartyNotices.txt를 업데이트(#10834)
- Microsoft.PowerShell.Native를 7.0.0-preview.3으로 업데이트(#10826)
- Microsoft.ApplicationInsights를 2.10.0에서 2.11.0으로 변경(#10608)
- NJsonSchema를 10.0.24에서 10.0.27로 변경(#10756)
- 빌드 시스템에 MacPorts 지원을 추가(#10736)(@Lucius-Q-User에게 감사드립니다!)
- PackageManagement를 1.4.4에서 1.4.5로 변경(#10728)
- NJsonSchema를 10.0.23에서 10.0.24로 변경(#10635)
- MSI에서 클라이언트/서버 원격 분석을 구분하는 환경 변수를 추가(#10612)
- PSDesiredStateConfiguration을 2.0.3에서 2.0.4로 변경(#10603)
- Microsoft.CodeAnalysis.CSharp를 3.2.1에서 3.3.1로 변경(#10607)
- .Net Core 3.0 RTM으로 업데이트(#10604)(@bergmeister에게 감사드립니다!)
- Microsoft Store 요구 사항에 맞게 MSIX 패키지 버전을 업데이트(#10588)
- PowerShellGet 버전을 2.2에서 2.2.1로 변경(#10382)
- PackageManagement 버전을 1.4.3에서 1.4.4로 변경(#10383)
- 7\.0.0-preview.4용 README.md 및 metadata.json을 업데이트(#10011)
- .NET Core 3.0 버전을 미리 보기 9에서 RC1로 업그레이드(#10552)(@bergmeister에게 감사드립니다!)
- ExperimentalFeature 목록 생성을 수정(내부 9996)
- PSReadLine 버전을 2.0.0-beta4에서 2.0.0-beta5로 변경(#10536)
- 릴리스 태그를 설정하는 릴리스 빌드 스크립트를 수정
- Microsoft.PowerShell.Native 버전을 7.0.0-preview.2로 업데이트(#10519)
- Netcoreapp3.0 preview9로 업그레이드(#10484)(@bergmeister에게 감사드립니다!)
- 일별 조정 빌드가 일별 빌드임을 인식(#10464)
- 결합된 패키지 빌드를 업데이트하여 일별 빌드를 릴리스(#10449)
- appveyor 참조를 제거(#10445)(@RDIL에게 감사드립니다!)
- NJsonSchema 버전을 10.0.22에서 10.0.23으로 변경(#10421)
- Alpine에 대한 일부 종속성에 필요하므로 linux-x64 빌드 폴더 삭제를 제거(#10407)

### <a name="documentation-and-help-content"></a>설명서 및 도움말 콘텐츠

- 변경 로그를 릴리스당 단일 로그로 리팩터링(#11165)
- PowerShell 7 온라인 도움말 문서용 FWLinks를 수정(#11071)
- CONTRIBUTING.md를 업데이트(#11096)(@mklement0에게 감사드립니다!)
- README.md에서 설치 문서 링크를 수정(#11083)
- install-powershell.ps1 스크립트에 예제를 추가(#11024)(@kilasuit에게 감사드립니다!)
- CHANGELOG.md에서 Select-String 강조 및 Import-DscResource를 수정(#10890)
- powershell-beginners-guide.md에서 만료된 링크를 제거(#10926)
- 안정적 및 서비스 변경 로그를 병합(#10527)
- 빌드 문서에서 사용된 .NET 버전을 업데이트(#10775)(@Greg-Smulko에게 감사드립니다!)
- powershell-beginners-guide.md에서 링크를 MSDN에서 docs.microsoft.com으로 바꿈(#10778)(@iSazonov에게 감사드립니다!)
- 끊어진 DSC 개요 링크 수정(#10702)
- Support_Question.md를 업데이트하여 Stack Overflow에 다른 커뮤니티 리소스로 연결(#10638)(@mklement0에게 감사드립니다!)
- 배포 요청 템플릿에 프로세서 아키텍처 추가(#10661)
- PowerShell 학습 문서에 새로운 PowerShell MoL 도서 추가(#10602)
- v6.1.6 및 v6.2.3 릴리스용 README.md와 메타데이터를 업데이터(#10523)
- README.md에서 오타를 수정(#10465)(@vedhasp에게 감사드립니다!)
- 학습 리소스 문서에 PSKoans 모듈에 대한 참조를 추가(#10369)(@vexx32에게 감사드립니다!)
- 7\.0.0-preview.3용 README.md 및 metadata.json을 업데이트(#10393)
