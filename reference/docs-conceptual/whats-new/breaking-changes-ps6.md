---
ms.date: 05/17/2018
keywords: powershell,core
title: PowerShell 6.0의 주요 변경 내용
ms.openlocfilehash: d477a9b27e8d5df6653ee40f8b606879b60a80c7
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655449"
---
# <a name="breaking-changes-for-powershell-60"></a>PowerShell 6.0의 주요 변경 내용

## <a name="features-no-longer-available-in-powershell-core"></a>PowerShell Core에서 더 이상 사용할 수 없는 기능

### <a name="powershell-workflow"></a>PowerShell 워크플로

[PowerShell][workflow]는 [Windows WF(Workflow Foundation)][workflow-foundation]을 토대로 빌드되는 Windows PowerShell의 기능으로, 장기 실행 또는 병렬 처리 작업을 위한 강력한 Runbook을 만들 수 있습니다.

.NET Core에 Windows Workflow Foundation 지원이 없으므로 PowerShell Core에서는 이후에도 PowerShell 워크플로를 지원하지 않을 것입니다.

앞으로 PowerShell 워크플로 없이도 PowerShell 언어에서 네이티브 병렬 처리/동시성을 사용할 수 있기를 바랍니다.

[workflow]: https://docs.microsoft.com/powershell/scripting/core-powershell/workflows-guide
[workflow-foundation]: https://docs.microsoft.com/dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a>사용자 지정 스냅인

[PowerShell 스냅인][snapin]은 PowerShell 커뮤니티에서 널리 사용되지 않는 PowerShell 모듈의 선행 작업입니다.

스냅인 지원이 복잡하고 커뮤니티에서 많이 사용되지 않으므로 PowerShell Core에서는 사용자 지정 스냅인을 더 이상 지원하지 않습니다.

이로 인해, 현재 Windows와 Windows Server의 `ActiveDirectory` 및 `DnsClient` 모듈이 중단됩니다.

[snapin]: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a>WMI v1 cmdlet

두 개의 WMI 기반 모듈 집합을 지원하는 것은 복잡하므로 PowerShell Core에서는 WMI v1 cmdlet이 제거되었습니다.

- `Get-WmiObject`
- `Invoke-WmiMethod`
- `Register-WmiEvent`
- `Set-WmiInstance`

대신, 동일한 기능과 함께 새로운 기능과 새롭게 디자인된 구문을 제공하는 CIM(WMI v2라고도 함) cmdlet을 사용하는 것이 좋습니다.

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a>Microsoft.PowerShell.LocalAccounts

지원되지 않는 API를 사용하는 `Microsoft.PowerShell.LocalAccounts`는 더 나은 해결 방법을 찾을 때까지 PowerShell Core에서 제거되었습니다.

### <a name="-counter-cmdlets"></a>`*-Counter` cmdlet

지원되지 않는 API를 사용하는 `*-Counter`는 더 나은 해결 방법을 찾을 때까지 PowerShell Core에서 제거되었습니다.

## <a name="enginelanguage-changes"></a>엔진/언어 변경 내용

### <a name="rename-powershellexe-to-pwshexe-5101httpsgithubcompowershellpowershellissues5101"></a>`powershell.exe`의 이름을 `pwsh.exe`로 바꿈 [#5101](https://github.com/PowerShell/PowerShell/issues/5101)

Windows PowerShell과 구분하여, Windows에서 PowerShell Core를 가리키는 확실한 방법을 사용자에게 제공하기 위해 PowerShell Core 이진이 Windows에서는 `pwsh.exe`, 비 Windows 플랫폼에서는 `pwsh`로 변경되었습니다.

약식 이름도 비 Windows 플랫폼의 셸 이름 지정과 일치합니다.

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193httpsgithubcompowershellpowershellissues5193"></a>출력에 줄 바꿈을 삽입하지 않음(테이블 제외) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)

이전에는 출력이 콘솔 너비에 맞게 조정되고 콘솔의 끝 너비에 줄 바꿈이 추가되었으므로 터미널의 크기를 조정할 경우, 출력의 서식이 예상대로 재지정되지 않았습니다. 열 맞춤 상태를 유지하려면 줄 바꿈이 필요하므로 테이블에는 이 변경 내용이 적용되지 않았습니다.

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432httpsgithubcompowershellpowershellissues5432"></a>값 형식 요소 유형을 포함하는 컬렉션에 대한 null 요소 검사 건너뜀 [#5432](https://github.com/PowerShell/PowerShell/issues/5432)

`Mandatory` 매개 변수와 `ValidateNotNull` 및 `ValidateNotNullOrEmpty` 특성에서, 컬렉션의 요소 유형이 값 형식인 경우 null 요소 검사를 건너뜁니다.

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369httpsgithubcompowershellpowershellissues5369"></a>ASCII가 아니라 `UTF-8 NoBOM` 인코딩을 사용하도록 `$OutputEncoding` 변경 [#5369](https://github.com/PowerShell/PowerShell/issues/5369)

이전 인코딩인 ASCII(7비트)에서는 출력이 잘못 변경되는 경우가 있었습니다. 이 변경은 `UTF-8 NoBOM`을 기본값으로 설정하기 위한 것으로, 대부분의 도구 및 운영 체제에서 지원되는 인코딩을 사용하여 유니코드 출력을 보존합니다.

### <a name="remove-allscope-from-most-default-aliases-5268httpsgithubcompowershellpowershellissues5268"></a>대부분의 기본 별칭에서 `AllScope` 제거 [#5268](https://github.com/PowerShell/PowerShell/issues/5268)

범위를 빨리 만들 수 있도록 `AllScope`가 대부분의 기본 별칭에서 제거되었습니다. 자주 사용하는 몇 가지 별칭에 대해서는 조회 속도가 더 빠른 `AllScope`가 유지되었습니다.

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113httpsgithubcompowershellpowershellissues5113"></a>`-Verbose` 및 `-Debug`가 더 이상 `$ErrorActionPreference`를 재정의하지 않음 [#5113](https://github.com/PowerShell/PowerShell/issues/5113)

이전에는 `-Verbose` 또는 `-Debug`가 지정된 경우 `$ErrorActionPreference`의 동작을 재정의했습니다. 이 변경으로, `-Verbose` 및 `-Debug`가 더 이상 `$ErrorActionPreference`의 동작에 영향을 주지 않습니다.

## <a name="cmdlet-changes"></a>cmdlet 변경 내용

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320httpsgithubcompowershellpowershellissues5320"></a>반환된 데이터가 없을 때 Invoke-RestMethod에서 유용한 정보를 반환하지 않음 [#5320](https://github.com/PowerShell/PowerShell/issues/5320)

API에서 `null`만 반환하는 경우 Invoke-RestMethod에서 이 값을 `$null`이 아니라 `"null"` 문자열로 직렬화했습니다. 이 변경으로, `Invoke-RestMethod`의 논리가 유효한 단일 값 JSON `null` 리터럴을 `$null`로 올바르게 직렬화하도록 수정됩니다.

### <a name="remove--computername-from--computer-cmdlets-5277httpsgithubcompowershellpowershellissues5277"></a>`*-Computer` cmdlet에서 `-ComputerName` 제거 [#5277](https://github.com/PowerShell/PowerShell/issues/5277)

CoreFX의 RPC 원격 관련 문제로 인해(특히 비 Windows 플랫폼) PowerShell에서 일관성 있는 원격 경험을 보장하기 위해 `-ComputerName` 매개 변수가 `\*-Computer` cmdlet에서 제거되었습니다. cmdlet을 원격으로 실행하는 대체 방법으로 `Invoke-Command`를 사용합니다.

### <a name="remove--computername-from--service-cmdlets-5090httpsgithubcompowershellpowershellissues5094"></a>`*-Service` cmdlet에서 `-ComputerName` 제거 [#5090](https://github.com/PowerShell/PowerShell/issues/5094)

일관성 있는 PSRP 사용을 권장하기 위해 `-ComputerName` 매개 변수가 `*-Service` cmdlet에서 제거되었습니다.

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197httpsgithubcompowershellpowershellissues5197"></a>`a*b`가 실제로 존재하지 않을 경우 `Get-Item -LiteralPath a*b`에서 오류를 반환하도록 수정 [#5197](https://github.com/PowerShell/PowerShell/issues/5197)

이전에는 `-LiteralPath`에 와일드카드를 지정할 경우, `-Path`와 동일하게 처리되고, 와일드카드를 통해 파일을 찾지 못할 경우 자동으로 종료되었습니다. 올바른 동작은 파일이 존재하지 않을 경우 오류가 발생하도록 `-LiteralPath`가 리터럴이 되어야 합니다. `-Literal`과 함께 사용된 와일드카드를 리터럴로 처리하도록 변경되었습니다.

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134httpsgithubcompowershellpowershellissues5134"></a>형식 정보가 CSV에 있는 경우 `Import-Csv`에서 가져올 때 `PSTypeNames`를 적용해야 함 [#5134](https://github.com/PowerShell/PowerShell/issues/5134)

이전에는 `ConvertFrom-Csv`를 사용하여 `TypeInformation`을 가져오고, `Export-CSV`를 사용하여 내보낸 개체가 형식 정보를 보존하지 않았습니다. 이 변경으로, CSV 파일에서 사용 가능한 경우 형식 정보가 `PSTypeNames` 멤버에 추가됩니다.

### <a name="-notypeinformation-should-be-default-on-export-csv-5131httpsgithubcompowershellpowershellissues5131"></a>`Export-Csv`에서 `-NoTypeInformation`이 기본값이어야 함 [#5131](https://github.com/PowerShell/PowerShell/issues/5131)

이 변경은 형식 정보를 포함하는 `Export-CSV`의 기본 동작에 대한 고객 피드백을 반영하기 위한 것입니다.

이전에는 cmdlet에서 개체의 형식 이름을 포함하는 주석을 첫째 줄로 출력했습니다. 대부분의 도구에서 인식되지 않으므로 이 주석을 기본적으로 표시하지 않도록 변경되었습니다. 이전 동작을 유지하려면 `-IncludeTypeInformation`을 사용합니다.

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112httpsgithubcompowershellpowershellissues5112"></a>`-Credential`이 암호화되지 않은 연결을 통해 전송될 경우 웹 cmdlet에서 경고해야 함 [#5112](https://github.com/PowerShell/PowerShell/issues/5112)

HTTP를 사용하는 경우 암호를 포함하는 콘텐츠가 일반 텍스트로 전송됩니다. 이 변경은 이 동작을 기본적으로 허용하지 않고 자격 증명이 비보안 방식으로 전달될 경우 오류를 반환하기 위한 것입니다. 사용자는 `-AllowUnencryptedAuthentication` 스위치를 사용하여 이 변경을 무시할 수 있습니다.

## <a name="api-changes"></a>API 변경 내용

### <a name="remove-addtypecommandbase-class-5407httpsgithubcompowershellpowershellissues5407"></a>`AddTypeCommandBase` 클래스 제거 [#5407](https://github.com/PowerShell/PowerShell/issues/5407)

성능 향상을 위해 `AddTypeCommandBase` 클래스가 `Add-Type`에서 제거되었습니다. 이 클래스는 Add-Type cmdlet에서만 사용되며 사용자에게 영향을 주면 안 됩니다.

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080httpsgithubcompowershellpowershellissues5080"></a>`System.Text.Encoding` 형식이 되도록 `-Encoding` 매개 변수와 cmdlet 통합 [#5080](https://github.com/PowerShell/PowerShell/issues/5080)

`-Encoding` 값 `Byte`가 파일 시스템 공급자 cmdlet에서 제거되었습니다. 이제 새 매개 변수 `-AsByteStream`을 사용하여 바이트 스트림이 입력으로 필요한 경우나 출력이 바이트 스트림인 경우를 지정합니다.

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055httpsgithubcompowershellpowershellissues5055"></a>비어 있는 null `-UFormat` 매개 변수에 대해 더 나은 오류 메시지 추가 [#5055](https://github.com/PowerShell/PowerShell/issues/5055)

이전에는 빈 형식 문자열을 `-UFormat`에 전달할 때 도움이 되지 않는 오류 메시지가 표시되었습니다. 더 자세한 설명을 포함하는 오류가 추가되었습니다.

### <a name="clean-up-console-code-4995httpsgithubcompowershellpowershellissues4995"></a>콘솔 코드 정리 [#4995](https://github.com/PowerShell/PowerShell/issues/4995)

다음 기능은 PowerShell Core에서 지원되지 않아 제거되었으며, Windows PowerShell에 대한 레거시 이유로 존재하기 때문에 지원을 추가할 플랜이 없습니다. `-psconsolefile` 스위치 및 코드, `-importsystemmodules` 스위치 및 코드, 글꼴 변경 코드

### <a name="removed-runspaceconfiguration-support-4942httpsgithubcompowershellpowershellissues4942"></a>`RunspaceConfiguration` 지원 제거 [#4942](https://github.com/PowerShell/PowerShell/issues/4942)

이전에는 API를 사용하여 프로그래밍 방식으로 PowerShell Runspace를 만들 때 레거시 [`RunspaceConfiguration`][runspaceconfig] 또는 최신 [`InitialSessionState`][iss]를 사용할 수 있었습니다. 이 변경으로, `RunspaceConfiguration` 지원이 제거되었으며 `InitialSessionState`만 지원됩니다.

[runspaceconfig]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: https://docs.microsoft.com/dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923httpsgithubcompowershellpowershellissues4923"></a>`CommandInvocationIntrinsics.InvokeScript`에서 인수를 `$args`가 아니라 `$input`에 바인딩함 [#4923](https://github.com/PowerShell/PowerShell/issues/4923)

잘못된 매개 변수 위치로 인해 인수가 아니라 입력으로 인수가 전달되었습니다.

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903httpsgithubcompowershellpowershellissues4903"></a>`Get-Help`에서 지원되지 않는 `-showwindow` 스위치 제거 [#4903](https://github.com/PowerShell/PowerShell/issues/4903)

`-showwindow`는 CoreCLR에서 지원되지 않는 WPF를 사용합니다.

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866httpsgithubcompowershellpowershellissues4866"></a>`Remove-Item`의 레지스트리 경로에 *를 사용할 수 있도록 허용 [#4866](https://github.com/PowerShell/PowerShell/issues/4866)

이전에는 `-LiteralPath`에 와일드카드를 지정할 경우, `-Path`와 동일하게 처리되고, 와일드카드를 통해 파일을 찾지 못할 경우 자동으로 종료되었습니다. 올바른 동작은 파일이 존재하지 않을 경우 오류가 발생하도록 `-LiteralPath`가 리터럴이 되어야 합니다. `-Literal`과 함께 사용된 와일드카드를 리터럴로 처리하도록 변경되었습니다.

### <a name="fix-set-service-failing-test-4802httpsgithubcompowershellpowershellissues4802"></a>`Set-Service` 실패 테스트 수정 [#4802](https://github.com/PowerShell/PowerShell/issues/4802)

이전에는 `New-Service -StartupType foo`를 사용할 경우, `foo`가 무시되고 기본 시작 유형으로 서비스가 생성되었습니다. 이 변경은 잘못된 시작 유형에 대해 명시적으로 오류를 throw하기 위한 것입니다.

### <a name="rename-isosx-to-ismacos-4700httpsgithubcompowershellpowershellissues4700"></a>`$IsOSX`의 이름을 `$IsMacOS`로 바꿈 [#4700](https://github.com/PowerShell/PowerShell/issues/4700)

PowerShell의 이름 지정은 Microsoft의 이름 지정과 일치하는 동시에 OSX가 아니라 Apple의 macOS 사용을 준수해야 합니다. 그러나 가독성과 일관성을 위해 파스칼식 대/소문자를 유지하고 있습니다.

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573httpsgithubcompowershellpowershellissues4573"></a>잘못된 스크립트가 -File에 전달될 경우 일관성 있는 오류 메시지 작성, 모호한 인수가 전달될 경우 더 나은 오류 작성 [#4573](https://github.com/PowerShell/PowerShell/issues/4573)

Unix 규칙에 맞게 `pwsh.exe`의 종료 코드 변경

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302httpsgithubcompowershellpowershellissues4302-4303httpsgithubcompowershellpowershellissues4303"></a>`Diagnostics` 모듈의 cmdlet 및 `LocalAccount` 제거 [#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)

지원되지 않는 API 때문에 `Diagnostics` 모듈의 `Counter` cmdlet 및 `LocalAccounts` 모듈이 더 나은 해결 방법을 찾을 때까지 제거되었습니다.

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036httpsgithubcompowershellpowershellissues4036"></a>bool 매개 변수로 PowerShell 스크립트를 실행할 경우, 작동하지 않음 [#4036](https://github.com/PowerShell/PowerShell/issues/4036)

이전에는 powershell.exe(현재 `pwsh.exe`)를 사용하여 `-File`로 PowerShell 스크립트를 실행할 경우, $true/$false를 매개 변수 값으로 전달할 수 없었습니다. 매개 변수에 대한 구문 분석된 값으로 $true/$false 지원이 추가되었습니다. 현재 문서화된 구문이 작동하지 않으므로 스위치 값도 지원됩니다.

### <a name="remove-clrversion-property-from-psversiontable-4027httpsgithubcompowershellpowershellissues4027"></a>`$PSVersionTable`에서 `ClrVersion` 속성 제거 [#4027](https://github.com/PowerShell/PowerShell/issues/4027)

`$PSVersionTable`의 `ClrVersion` 속성은 CoreCLR에서 유용하지 않습니다. 최종 사용자는 호환성을 확인하기 위해 이 값을 사용하면 안 됩니다.

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019httpsgithubcompowershellpowershellissues4019"></a>`powershell.exe`에 대한 위치 지정 매개 변수를 `-Command`에서 `-File`로 변경 [#4019](https://github.com/PowerShell/PowerShell/issues/4019)

비 Windows 플랫폼에서 PowerShell의 구조를 사용할 수 있게 합니다. 즉, Unix 기반 시스템에서 `pwsh`를 명시적으로 호출하지 않고 PowerShell을 자동으로 호출하는 스크립트 실행 파일을 만들 수 있습니다. 이제 `-File`을 지정하지 않고 `powershell foo.ps1` 또는 `powershell fooScript`와 같은 작업을 수행할 수도 있습니다. 그러나 이 변경으로, 이제 `powershell.exe Get-Command`와 같은 작업을 수행할 때 `-c` 또는 `-Command`를 명시적으로 지정해야 합니다.

### <a name="implement-unicode-escape-parsing-3958httpsgithubcompowershellpowershellissues3958"></a>유니코드 이스케이프 구문 분석 구현 [#3958](https://github.com/PowerShell/PowerShell/issues/3958)

`` `u#### `` 또는 `` `u{####} ``이 해당 유니코드 문자로 변환됩니다. 리터럴 `` `u ``를 출력하려면 backtick을 이스케이프합니다(``` ``u ```).

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940httpsgithubcompowershellpowershellissues3940"></a>비 Windows 플랫폼에서 `New-ModuleManifest` 인코딩을 `UTF8NoBOM`으로 변경 [#3940](https://github.com/PowerShell/PowerShell/issues/3940)

이전에는 `New-ModuleManifest`에서 BOM을 포함하는 UTF-16으로 psd1 매니페스트를 만들어 Linux 도구에서 문제가 발생했습니다. 호환성이 손상되는 이 변경으로, 비 Windows 플랫폼에서 `New-ModuleManifest`의 인코딩이 UTF(BOM 없음)로 변경됩니다.

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780httpsgithubcompowershellpowershellissues3780"></a>`Get-ChildItem`이 바로 가기 링크로 재귀되지 않도록 방지 (#1875) [#3780](https://github.com/PowerShell/PowerShell/issues/3780)

이 변경으로, `Get-ChildItem`이 Unix `ls -r` 및 Windows `dir /s` 네이티브 명령과 더 일치하게 됩니다. 언급한 명령과 유사하게, 이 cmdlet은 재귀되는 동안 찾은 디렉터리에 대한 바로 가기 링크를 표시하지만 해당 디렉터리로 재귀되지 않습니다.

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706httpsgithubcompowershellpowershellissues3706"></a>반환된 줄에 구분 기호를 포함하지 않도록 `Get-Content -Delimiter` 수정 [#3706](https://github.com/PowerShell/PowerShell/issues/3706)

이전에는 `Get-Content -Delimiter`를 사용하여 생성된 출력에서 구분 기호를 제거하기 위해 데이터를 추가로 처리해야 했기 때문에 불편하고 일관성이 없었습니다. 이 변경으로, 반환된 줄에서 구분 기호가 제거됩니다.

### <a name="implement-format-hex-in-c-3320httpsgithubcompowershellpowershellissues3320"></a>C#에서 Format-Hex 구현 [#3320](https://github.com/PowerShell/PowerShell/issues/3320)

이제 `-Raw` 매개 변수가 “no-op”(아무 작업도 안 함)입니다. 앞으로는 모든 출력이 해당 형식의 모든 바이트를 포함하는 숫자 표현으로 표시됩니다(이 변경 이전에는 `-Raw` 매개 변수가 공식적으로 수행한 작업).

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319httpsgithubcompowershellpowershellissues3319"></a>기본 셸인 PowerShell이 스크립트 명령에서 작동하지 않음 [#3319](https://github.com/PowerShell/PowerShell/issues/3319)

Unix에서는 셸이 대화형 셸을 나타내는 `-i`를 허용하는 것이 규칙이며, 많은 도구가 이 동작을 기대하고(예를 들어, PowerShell을 기본 셸로 설정하는 경우 `script`) `-i` 스위치로 셸을 호출합니다. 이전에는 `-i`를 `-inputformat`의 약식으로 사용할 수 있었다는 점에서 이 변경으로 호환성이 손상됩니다. 이제 `-in`을 사용해야 합니다.

### <a name="typo-fix-in-get-computerinfo-property-name-3167httpsgithubcompowershellpowershellissues3167"></a>Get-ComputerInfo 속성 이름의 오타 수정 [#3167](https://github.com/PowerShell/PowerShell/issues/3167)

`BiosSerialNumber`가 `BiosSeralNumber`로 잘못 표기되었으며 올바른 맞춤법으로 변경되었습니다.

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024httpsgithubcompowershellpowershellissues3024"></a>`Get-StringHash` 및 `Get-FileHash` cmdlet 추가 [#3024](https://github.com/PowerShell/PowerShell/issues/3024)

이 변경은 일부 해시 알고리즘이 CoreFX에서 지원되지 않아 더 이상 사용할 수 없기 때문입니다.

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672httpsgithubcompowershellpowershellissues2672"></a>$null을 전달할 때 오류가 아니라 모든 개체가 반환되는, `Get-*` cmdlet에 대한 유효성 검사 추가 [#2672](https://github.com/PowerShell/PowerShell/issues/2672)

다음 중 하나에 `$null`을 전달하면 이제 오류가 throw됩니다.

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482httpsgithubcompowershellpowershellissues2482"></a>`Import-Csv`에서 W3C 확장 로그 파일 형식 지원 추가 [#2482](https://github.com/PowerShell/PowerShell/issues/2482)

이전에는 `Import-Csv` cmdlet을 사용하여 W3C 확장 로그 형식의 로그 파일을 직접 가져올 수 없었으며, 추가 작업이 필요했습니다. 이 변경으로, W3C 확장 로그 형식이 지원됩니다.

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035httpsgithubcompowershellpowershellissues2035"></a>PS 함수에서 `ValueFromRemainingArguments`의 매개 변수 바인딩 문제 [#2035](https://github.com/PowerShell/PowerShell/issues/2035)

이제 `ValueFromRemainingArguments`에서 그 자체가 배열인 단일 값이 아니라 배열로 값을 반환합니다.

### <a name="buildversion-is-removed-from-psversiontable-1415httpsgithubcompowershellpowershellissues1415"></a>`$PSVersionTable`에서 `BuildVersion` 제거 [#1415](https://github.com/PowerShell/PowerShell/issues/1415)

`$PSVersionTable`에서 `BuildVersion` 속성이 제거되었습니다. 이 속성은 Windows 빌드 버전에 연결되어 있었습니다. 대신 `GitCommitId`를 사용하여 PowerShell Core의 정확한 빌드 버전을 검색하는 것이 좋습니다.

### <a name="changes-to-web-cmdlets"></a>웹 cmdlet 변경 내용

웹 cmdlet의 기본 .NET API가 `System.Net.Http.HttpClient`로 변경되었습니다. 이 변경은 많은 이점을 제공합니다. 그러나 Internet Explorer와의 상호 운용성이 없다는 점과 결부되어, 이 변경으로 인해 `Invoke-WebRequest` 및 `Invoke-RestMethod` 내에서 호환성이 손상되는 여러 가지 변경이 발생했습니다.

- 이제 `Invoke-WebRequest`에서 기본 HTML 구문 분석만 지원합니다. `Invoke-WebRequest`는 항상 `BasicHtmlWebResponseObject` 개체를 반환합니다. `ParsedHtml` 및 `Forms` 속성이 제거되었습니다.
- 이제 `BasicHtmlWebResponseObject.Headers` 값이 `String`이 아니라 `String[]`입니다.
- 이제 `BasicHtmlWebResponseObject.BaseResponse`가 `System.Net.Http.HttpResponseMessage` 개체입니다.
- 이제 웹 cmdlet 예외의 `Response` 속성이 `System.Net.Http.HttpResponseMessage` 개체입니다.
- 이제 엄격한 RFC 헤더 구문 분석이 `-Headers` 및 `-UserAgent` 매개 변수의 기본값입니다. 이 설정은 `-SkipHeaderValidation`을 사용하여 무시할 수 있습니다.
- `file://` 및 `ftp://` URI 체계가 더 이상 지원되지 않습니다.
- `System.Net.ServicePointManager` 설정이 더 이상 적용되지 않습니다.
- 현재 macOS에서 사용할 수 있는 인증서 기반 인증은 없습니다.
- `http://` URI를 통해 `-Credential`을 사용하면 오류가 발생합니다. 오류를 표시하지 않으려면 `https://` URI를 사용하거나 `-AllowUnencryptedAuthentication` 매개 변수를 제공합니다.
- `-MaximumRedirection` 이제 리디렉션을 시도 마지막 리디렉션 결과 반환 하는 대신 제공 된 제한을 초과 하면 종료 오류를 생성 합니다.
