---
title: PowerShell Core 6.2의 새로운 기능
description: PowerShell Core 6.2에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 03/28/2019
ms.openlocfilehash: 2f5f5d11ba46d53966093c5e3ed6d0c7d47308d0
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737137"
---
# <a name="whats-new-in-powershell-core-62"></a>PowerShell Core 6.2의 새로운 기능

PowerShell Core 6.2 릴리스에서는 성능 향상, 버그 수정 및 품질을 개선하는 더 작은 cmdlet 및 언어 향상에 초점을 맞추었습니다. 전체 향상된 기능 목록을 보려면 GitHub의 자세한 [changelog](https://github.com/PowerShell/PowerShell/releases)를 확인하세요.

## <a name="experimental-features"></a>실험적 기능

이전에 [실험적 기능][]에 대한 지원을 사용하도록 설정했습니다. 6\.2 릴리스에는 사용해 볼 수 있는 네 가지 실험적 기능이 있습니다. 기능을 향상하고 기능이 주류 상태로 홍보할 가치가 있는지 결정할 수 있도록 피드백을 제공해 주세요.

`Get-ExperimentalFeature`를 사용하여 사용 가능한 실험적 기능 목록을 확인합니다. `Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature`를 사용하여 이 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.

### <a name="command-not-found-suggestions"></a>명령을 찾을 수 없음 제안

이 기능은 유사 일치를 사용하여 잘못 입력했을 수 있는 명령이나 cmdlet에 대한 제안을 찾습니다.

```powershell
Enable-ExperimentalFeature -Name PSCommandNotFoundSuggestion
```

#### <a name="example"></a>예제

이 예제에서는 철자가 틀린 cmdlet 이름이 가능성이 가장 높은 제안부터 가장 낮은 제안까지 여러 제안에 유사 일치됩니다.

```powershell
Get-Commnd
```

```Output
Get-Commnd : The term 'Get-Commnd' is not recognized as the name of a cmdlet, function, script file, or operable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ Get-Commnd
+ ~~~~~~~~~~
+ CategoryInfo          : ObjectNotFound: (Get-Commnd:String) [], CommandNotFoundException
+ FullyQualifiedErrorId : CommandNotFoundException


Suggestion [4,General]: The most similar commands are: Get-Command, Get-Content, Get-Job, Get-Module, Get-Event, Get-Host, Get-Member, Get-Item, Set-Content.
```

### <a name="implicit-remoting-batching"></a>암시적 원격 일괄 처리

파이프라인에서 [암시적 원격](https://devblogs.microsoft.com/scripting/remoting-the-implicit-way/)을 사용하면 PowerShell에서는 파이프라인의 각 명령을 독립적으로 처리합니다. 개체는 파이프라인 실행을 통해 클라이언트와 원격 시스템 사이에서 반복해서 직렬화 및 `de-serialized`됩니다.

이 기능을 통해 PowerShell에서는 파이프라인을 분석하여 명령이 실행하기에 안전하고 대상 시스템에 있는지 확인합니다. 이에 해당하는 경우 PowerShell에서는 전체 파이프라인을 원격으로 실행하고 결과를 다시 클라이언트로만 직렬화 및 `de-serializes`합니다.

```powershell
Enable-ExperimentalFeature -Name PSImplicitRemotingBatching
```

localhost를 통한 `Get-Process | Sort-Object`의 실제 테스트는 10~15초부터 20~30**밀리초**까지 감소합니다. 이 기능은 클라이언트에서만 사용하도록 설명하면 됩니다. 서버에서 변경할 필요가 없습니다.

### <a name="temp-drive"></a>임시 드라이브

```powershell
Enable-ExperimentalFeature -Name PSTempDrive
```

다른 운영 체제에서 PowerShell Core를 사용하는 경우 임시 디렉터리를 찾는 환경 변수가 Windows, macOS 및 Linux에서 서로 다른지 살펴보겠습니다. 이 기능을 통해 사용 중인 운영 체제의 임시 디렉터리에 자동으로 매핑되는 `Temp:`라는 [PSDrive][]를 가져옵니다.

#### <a name="example"></a>예제

```powershell
PS> "Hello World!" > Temp:/hello.txt
PS> Get-Content Temp:/hello.txt
Hello World!
```

기본 파일 명령(예: Linux의 `ls`)은 PSDrive를 인식하지만 이 `Temp:` 드라이브를 인식하지 않습니다.

### <a name="abbreviation-expansion"></a>약어 확장

PowerShell cmdlet에는 설명이 포함된 명사가 있어야 합니다. 이로 인해 입력하기 어려운 긴 이름이 생성됩니다. 이 기능을 사용하면 cmdlet의 대문자만 입력하고 탭 완성을 사용하여 일치 항목을 찾을 수 있습니다.

```powershell
Enable-ExperimentalFeature -Name PSUseAbbreviationExpansion
```

#### <a name="example"></a>예제

```powershell
PS> i-arsavsf
```

Azure PowerShell [Az](https://www.powershellgallery.com/packages/Az) 모듈이 설치되어 있고 Tab 키를 누르면 다음으로 자동 완성됩니다.

```Output
PS> Import-AzRecoveryServicesAsrVaultSettingsFile
```

> [!NOTE]
> 이 기능은 대화형으로 사용할 수 있습니다. cmdlet의 약어 형식은 실행할 수 없습니다.
> 이 기능은 별칭을 대체하지 않습니다.

## <a name="breaking-changes"></a>주요 변경 내용

- Windows PowerShell과 일치하도록 `Write-Output`의 `-NoEnumerate` 동작 수정 (#9069)
- `Join-String -InputObject 1,2,3` 결과를 `1,2,3 | Join-String` 결과와 같게 만듭니다.(#8611)(@sethvs에게 감사드립니다!)
- `-Stable`을 `Sort-Object` 및 관련 테스트에 추가(#7862)(@KirkMunro에게 감사드립니다!)
- 초의 소수 부분을 허용하도록 `Start-Sleep` cmdlet 향상(#8537)(@Prototyyppi에게 감사드립니다!)
- 모든 문화권에서 OrdinalIgnoreCase를 `case-insensitive`로 사용하도록 해시 테이블 변경(#8566)
- `Get-ChildItem` 출력에 바인딩되도록 `Import-Csv`에서 **LiteralPath** 수정(#8277)(@iSazonov에게 감사드립니다!)
- `Import-Csv`에서 큰따옴표가 사용되는 경우 더 이상 이름 없이 열을 건너뛰지 않음(#7899)(@Topping에게 감사드립니다!)
- `Get-ExperimentalFeature`에 더 이상 `-ListAvailable` 스위치가 없음(#8318)
- 이제 Debug 매개 변수가 `$DebugPreference`를 **Inquire** 대신 **Continue**로 설정함(#8195)(@KirkMunro에게 감사드립니다!)
- pwsh와 함께 사용되는 리디렉션되고 인코딩되는 비대화형 명령에서 지정된 경우 `-OutputFormat` 사용(#8115)
- GAC에서 로드하기 전에 모듈 기본 경로에서 어셈블리 로드(#8073)
- Linux 미리 보기 패키지에서 물결표 제거(#8244)
- 프로필 처리 앞으로 `-WorkingDirectory` 처리 이동(#8079)
- Unix에서 `PATHEXT` 환경 변수를 추가하지 않음(#7697)(@iSazonov에게 감사드립니다!)

## <a name="known-issues"></a>알려진 문제

- Windows IOT ARM 플랫폼의 원격 처리에는 모듈 로드 문제가 있습니다. (#8053) 참조

## <a name="general-updates-and-fixes"></a>일반 업데이트 및 수정

- 대/소문자를 구분하는 파일 시스템에서 파일 및 폴더의 대/소문자를 구분하지 않는 탭 완성 사용(#8128)
- PSVersionInfo.PSVersion 및 PSVersionInfo.PSEdition을 public으로 설정(#8054)(@KirkMunro에게 감사드립니다!)
- `catch{ }` 블록에서 `$_` / `$PSItem`의 형식 유추 추가(#8020)(@vexx32에게 감사드립니다!)
- static 메서드 호출 형식 유추 수정(#8018)(@SeeminglyScience에게 감사드립니다!)
- `Select-Object`, `Group-Object`, **PSObject** 및 **Hashtable**의 유추 형식 만들기(#7231)(@powercode에게 감사드립니다!)
- `ByRef-like` 형식 매개 변수가 포함된 호출 메서드 지원(#7721)
- Windows PowerShell 모듈 경로가 이미 환경의 PSModulePath에 있는 경우 처리(#7727)
- 일반 텍스트를 저장하여 Windows가 아닌 환경에서도 `SecureString` cmdlet을 사용하도록 설정(#9199)
- securestring을 사용하여 clixml을 가져올 때 Windows가 아닌 환경에서 오류 메시지 개선(#7997)
- `Send-MailMessage`에 ReplyTo 매개 변수 추가(#8727)(@replicaJunction에게 감사드립니다!)
- `Send-MailMessage`에 사용되지 않음 메시지 추가(#9178)
- WinRM이 없을 때 `localhost`에서 `Restart-Computer`가 작동하도록 수정(#9160)
- PowerShell이 호스트될 때 `Start-Job`이 종료 오류를 throw하도록 설정(#9128)
- ushort, uint, ulong 및 short 리터럴의 C# 스타일 형식 가속기 및 접미사 추가(#7813)(@vexx32에게 감사드립니다!)
- 숫자 리터럴의 새 접미사 추가 - [about_Numeric_Literals][] 참조(#7901)(@vexx32에게 감사드립니다!)
- SupportsShouldProcess가 'true'로 설정되지 않을 경우 영향 수준을 올바르게 보고(#8209)(@vexx32에게 감사드립니다!)
- 웹 cmdlet에서 요청 문자 집합 문제 수정(#8742)(@markekraus에게 감사드립니다!)
- 웹 cmdlet에서 `100-continue` 예상 문제 수정(#8679)(@markekraus에게 감사드립니다!)
- 웹 cmdlet에서 파일 차단 문제 수정(#7676)(@Claustn에게 감사드립니다!)
- `Invoke-RestMethod`에서 코드 페이지 구문 분석 문제 수정(#8694)(@markekraus에게 감사드립니다!)
- `ConvertTo-Json`을 리팩터링하여 JsonObject.ConvertToJson을 공용 API로 공개(#8682)
- -Depth를 사용하여 `ConvertFrom-Json`에서 구성 가능한 최대 깊이 추가(#8199)(@louistio에게 감사드립니다!)
- `ConvertTo-Json` cmdlet에서 EscapeHandling 매개 변수 추가(#7775)(@iSazonov에게 감사드립니다!)
- pwsh 및 `Enter-PSHostProcess`에 `-CustomPipeName` 추가(#8889)
- `New-Item`사용하여 Windows에서 상대 바로 가기 링크를 만들 수 있음(#8783)
- Windows 사용자가 개발자 모드에서 관리자 권한이 없어도 바로 가기 링크를 만들도록 허용(#8534)
- `Write-Information`에서 `$null`을 사용할 수 있음(#8774)
- MAML 도움말 콘텐츠를 사용하여 고급 함수의 `Get-Help` 수정(#8353)
- 매개 변수를 하나만 선언할 경우 -Parameter를 사용하여 `Get-Help` PSTypeName 문제 수정(#8754)(@pougetat에게 감사드립니다!)
- 주석 도움말을 위해 ScriptBlock에서 실행되는 `Get-Help`의 토큰 계산 수정 (#8238)(@hubuk에게 감사드립니다!)
- 문자열 배열을 허용하도록 `Get-Help` cmdlet -Parameter 매개 변수 변경(#8454)(@sethvs에게 감사드립니다!)
- 해당 경로에 공백이 포함된 경우 PAGER 해결(#8571)(@pougetat에게 감사드립니다!)
- 'help' 함수에서 `less`를 사용하여 종료 방법을 사용자에게 지시하도록 메시지 추가(#7998)
- `Format-Hex` cmdlet에서 지원 enum 및 char 형식 추가(#8191)(@iSazonov에게 감사드립니다!)
- `Format-Hex`에서 ShouldProcess 제거(#8178)
- `Format-Hex`에 새 Offset 및 Count 매개 변수를 추가하고 cmdlet을 리팩터링(#7877)(@iSazonov에게 감사드립니다!)
- `ConvertTo-Html`에서 'label'의 별칭 키로 'name' 허용, 정수로 'width'를 입력하도록 허용(#8426)(@mklement0에게 감사드립니다!)
- scriptblock 기반 계산 속성이 `ConvertTo-Html`에서 다시 작동하도록 설정(#8427)(@mklement0에게 감사드립니다!)
- 파이프라인 입력에서 텍스트를 만드는 cmdlet `Join-String` 추가(#7660)(@powercode에게 감사드립니다!)
- `Join-String` cmdlet FormatString 매개 변수 논리 수정(#8449)(@sethvs에게 감사드립니다!)
- 원격에서 작동하도록 `Clear-Host`를 다시 using `$RAWUI` 및 clear로 변경(#8609)
- `Clear-Host`를 간단하게 호출되는 `[console]::clear`로 변경하고 Unix에서 clear 별칭 제거(#8603)
- `Get-ChildItem` 출력에 바인딩되도록 `Import-Csv`에서 LiteralPath 수정(#8277)(@iSazonov에게 감사드립니다!)
- help 함수에서 AliasHelpInfo에 파서를 사용하면 안 됨(#8552)
- `-UseMinimalHeader`를 `Start-Transcript`에 추가하여 스크립트 헤더 최소화(#8402)(@lukexjeremy에게 감사드립니다!)
- `Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature` cmdlet 추가(#8318)
- logman.exe를 사용할 수 있는 경우 **PSDiagnostics**에서 모든 cmdlet 공개(#8366)
- `non-Windows` 플랫폼의 `New-PSDrive`에서 **Persist** 매개 변수 제거(#8291)(@lukexjeremy에게 감사드립니다!)
- `cd +` 지원 추가(#7206)(@bergmeister에게 감사드립니다!)
- \- 및 +라는 폴더에서 `Set-Location -LiteralPath`를 작동할 수 있음(#8089)
- 비어 있거나 `$null` 경로 값이 제공된 경우 `Test-Path`에서 `$false`를 반환함(#8080)(@vexx32에게 감사드립니다!)
- 경로가 공급자와 일치하지 않는 경우에도 동적 매개 변수를 반환할 수 있음(#7957)
- Unix 플랫폼에서 `Get-PSHostProcessInfo` 및 `Enter-PSHostProcess` 지원(#8232)
- `Get-Content` cmdlet에서 할당 감소(#8103)(@iSazonov에게 감사드립니다!)
- `Add-Content`가 콘텐츠를 작성하는 동안 다른 도구와 읽기 권한을 공유할 수 있음(#8091)
- 컨테이너를 대상으로 지정하는 경우 `Get/Add-Content`가 개선된 오류를 throw함(#7823)(@kvprasoon에게 감사드립니다!)
- Add `-Name`, `-NoUserOverrides` 및 `-ListAvailable` 매개 변수를 `Get-Culture` cmdlet에 추가(#7702)(@iSazonov에게 감사드립니다!)
- **Encoding** 매개 변수 완성을 위한 통합 특성 추가 (#7732)(@ThreeFive-O에게 감사드립니다!)
- **Encoding** 매개 변수에서 등록된 코드 페이지의 숫자 ID 및 이름 허용(#7636)(@iSazonov에게 감사드립니다!)
- 와일드카드 문자를 사용하여 `Rename-Item -Path` 수정(#7398)(@kwkam에게 감사드립니다!)
- `Start-Transcript`를 사용하고 파일이 있는 경우 삭제하는 대신 파일을 비움(#8131)(@paalbra에게 감사드립니다!)
- 명시적으로 **FileAccess.Read** 및 **FileShare.Read**를 사용하여 `Add-Type` 오픈 소스 파일 만들기(#7915)(@IISResetMe에게 감사드립니다!)
- 최신 Windows의 `Enter-PSSession -ContainerId` 수정(#7883)
- **NestedModules** 속성이 `Test-ModuleManifest`에 의해 채워지도록 함(#7859)
- `%F` 사례를 `Get-Date` -UFormat에 추가(#7630)(@britishben에게 감사드립니다!)
- 종속성이 있는 서비스를 중지하도록 `Set-Service -Status Stopped` 수정(#5525)(@zhenggu에게 감사드립니다!)

<!-- Link references -->
[about_Numeric_Literals]: /powershell/module/Microsoft.PowerShell.Core/About/about_numeric_literals
[실험적 기능]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
[PSDrive]: /powershell/module/microsoft.powershell.management/new-psdrive
