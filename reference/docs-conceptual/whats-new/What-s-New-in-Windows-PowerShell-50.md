---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 5.0의 새로운 기능
ms.openlocfilehash: dba016546fe034684f6b7afe43ec2e7a1b793d96
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978205"
---
# <a name="whats-new-in-windows-powershell-50"></a>Windows PowerShell 5.0의 새로운 기능

Windows PowerShell 5.0에는 용도를 확장하고, 사용 편의성을 높이며, Windows 기반 환경을 더욱 쉽고 종합적으로 제어하고 관리하는 데 사용할 수 있는 중요한 새 기능이 포함되어 있습니다.

Windows PowerShell 5.0은 이전 버전과 호환됩니다. Windows PowerShell 4.0, Windows PowerShell 3.0 및 Windows PowerShell 2.0용으로 설계된 cmdlet, 공급자, 모듈, 스냅인, 함수 및 프로필은 일반적으로 Windows PowerShell 5.0에서 변경 없이 사용할 수 있습니다.

## <a name="installing-windows-powershell"></a>Windows PowerShell 설치

Windows PowerShell 5.0은 Windows Server 2016 Technical Preview 및 Windows에 기본적으로 설치되어 있습니다.
10.

Windows Server 2012 R2, Windows 8.1 Enterprise 또는 Windows 8.1 Pro에서 Windows PowerShell 5.0을 설치하려면 [Windows Management Framework 5.0 Preview](https://aka.ms/wmf5download)를 다운로드하여 설치합니다. Windows Management Framework 5.0을 설치하기 전에 다운로드 정보를 확인하고 모든 시스템 요구 사항을 충족해야 합니다.

## <a name="in-this-topic"></a>항목 내용

- [KB 3000850의 Windows PowerShell 4.0 DSC 업데이트](#windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850)
- [Windows PowerShell 5.0의 새로운 기능](#new-features-in-windows-powershell-50)
- [Windows PowerShell 4.0의 새로운 기능](#new-features-in-windows-powershell-40)
- [Windows PowerShell 3.0의 새로운 기능](#new-features-in-windows-powershell-30)

## <a name="windows-powershell-40-updates-in-november-2014-update-rollup-kb-3000850"></a>2014년 11월 업데이트 롤업의 Windows PowerShell 4.0 업데이트(KB 3000850)

[Windows RT 8.1, Windows 8.1 및 Windows Server 2012 R2용 2014년 11월 업데이트 롤업](https://support.microsoft.com/kb/3000850/)(KB 3000850)에서는 Windows PowerShell 4.0의 다양한 Windows PowerShell DSC(필요한 상태 구성) 업데이트 및 향상 기능을 사용할 수 있습니다. Windows PowerShell에서 `Get-Hotfix -Id KB3000850`을 실행하여 KB 3000850이 시스템에 설치되어 있는지 확인할 수 있습니다.

- [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) 모듈의 기존 cmdlet에 대한 업데이트
  - [Get-DscResource](/powershell/module/PSDesiredStateConfiguration)가 더 빠릅니다(특히 ISE에서).
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration)에 마지막으로 적용된 구성을 다시 적용하는 새 매개 변수 -UseExisting이 있습니다.
  - [Start-DscConfiguration](/powershell/module/PSDesiredStateConfiguration) - Force가 수정되었습니다.
  - [Get DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration)가 엔진 상태에 대한 보다 유용한 정보를 표시합니다.
  - 이제 [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration)이 True 또는 False와 함께 컴퓨터 이름을 반환합니다.
  - 이제 [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration)에서 UNC 경로를 지원합니다.

- [PSDesiredStateConfiguration](/powershell/module/PSDesiredStateConfiguration) 모듈의 새 cmdlet
  - [Update-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Update-DscConfiguration): 주문형 끌어오기 서버 검사를 수행합니다.
  - [Stop-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration): 이미 실행 중인 구성을 중지합니다.
  - [Remove-DscConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument): 다양한 단계(보류 중, 이전 또는 현재)에서 구성 문서를 제거할 수 있습니다.

- 향상된 언어
  - 이제 DependsOn이 복합 리소스를 지원합니다.
  - 이제 DependsOn이 리소스 인스턴스 이름에서 숫자를 지원합니다.
  - 비어 있는 것으로 평가된 노드 식에서 더 이상 오류가 발생하지 않습니다.
  - 노드 식이 비어 있는 것으로 평가될 경우 발생하는 오류가 해결되었습니다.
  - 이제 구성을 호출하는 구성이 Windows PowerShell 콘솔에서 작동합니다.

- 향상된 끌어오기 모드
  - 이제 끌어오기 모드에서 모든 ZIP 파일을 지원합니다.
  - 이제 **AllowModuleOverwrite**가 올바르게 작동합니다.

- 향상된 복원력
  - 새 **DebugMode**를 사용하면 리소스 모듈을 다시 로드할 수 있습니다.
  - 구성 오류가 발생할 경우 pending.mof 파일이 삭제되지 않습니다.
  - 이제 메타 구성 설정이 손상되었을 때 LCM(로컬 구성 관리자)의 복원력이 향상되었습니다.

- 향상된 진단
  - LCM이 타이머를 사용자가 지정한 설정이 아닌 다른 설정으로 지정하면 경고가 표시됩니다.
  - 이제 오류 로그 파일에 Windows PowerShell 리소스에 대한 호출 스택이 포함됩니다.

- 향상된 유연성
  - LocalConfigurationManager 리소스에 **ActionAfterReboot**라는 새 속성이 있습니다.
    - ContinueConfiguration(기본값): 대상 노드가 다시 시작된 후에 자동으로 구성을 다시 시작합니다.
    - StopConfiguration: 노드가 다시 시작된 후에 자동으로 구성을 다시 시작하지 않습니다.
  - 이제 일관성 실행이 PULL 작업보다 더 자주 발생하거나 그 반대의 경우가 발생할 수 있습니다.
  - 버전 관리 지원: 이제 DSC가 최신 클라이언트에서 생성된 문서를 인식합니다([WMF 5.0](https://aka.ms/wmf5download)에 포함).

- 향상된 오류 방지
  - 이제 구성을 적용하기 전에 모듈 버전이 적용됩니다.
  - 이제 Get-, Set- 또는 Test-TargetResource 호출에 대해 **DebugPreference**가 올바르게 설정됩니다.

- 향상된 자격 증명 처리
  - 이제 **Certificate**와 **PSDscAllowPlainTextPassword**를 둘 다 지정할 경우 인증서가 사용됩니다.
  - Get-TargetResource에 대해서도 자격 증명의 암호가 해독됩니다.
  - 메타 구성 자격 증명이 암호화 및 암호 해독됩니다.
  - 이제 PSCredentials가 포함된 개체에 있을 때 암호가 해독됩니다.

- 향상된 기본 제공 리소스
  - 패키지 리소스
    - 더 이상 잘못된 패키지를 설치하지 않습니다(로컬 또는 웹 소스).
    - 이제 HTTPS를 지원합니다.
  - 이제 [패키지 리소스](/powershell/scripting/dsc/reference/resources/windows/packageresource)에 HTTPS 지원이 있습니다.
  - 이제 [보관 리소스](/powershell/scripting/dsc/reference/resources/windows/archiveresource)에서 자격 증명을 지원합니다.

## <a name="new-features-in-windows-powershell-50"></a>Windows PowerShell 5.0의 새로운 기능

- [Windows PowerShell의 새로운 기능](#new-features-in-windows-powershell)
- [Windows PowerShell 필요한 상태 구성의 새로운 기능](#new-features-in-windows-powershell-desired-state-configuration)
- [Windows PowerShell ISE의 새로운 기능](#new-features-in-windows-powershell-ise)
- [Windows PowerShell 웹 서비스의 새로운 기능](#new-features-in-windows-powershell-web-services-management-odata-iis-extension)
- [Windows PowerShell 5.0의 중요한 버그 수정](#notable-bug-fixes-in-windows-powershell-50)

### <a name="new-features-in-windows-powershell"></a>Windows PowerShell의 새로운 기능

- Windows PowerShell 5.0 이상에서는 다른 개체 지향 프로그래밍 언어와 유사한 형식 구문 및 의미 체계를 사용하여 클래스를 통해 개발할 수 있습니다. **Class**, **Enum** 및 기타 키워드가 새로운 기능을 지원하기 위해 Windows PowerShell 언어에 추가되었습니다.
  클래스 작업에 대한 자세한 내용은 about_Classes를 참조하세요.

- Windows PowerShell 5.0에서는 스크립트와 해당 호출자(또는 호스팅 환경) 간에 구조화된 데이터를 전송하는 데 사용할 수 있는 새 구조화된 정보 스트림이 도입되었습니다. 이제 Write-Host를 사용하여 출력을 정보 스트림으로 내보낼 수 있습니다. 정보 스트림은 PowerShell.Streams, 작업, 예약된 작업 및 워크플로에 대해서도 작동합니다. 정보 스트림을 지원하는 기능은 다음과 같습니다.
  - Windows PowerShell에서 명령에 대한 정보 스트림 데이터를 처리하는 방법을 지정할 수 있는 새 Write-Information cmdlet. Write-Host는 Write-Information의 래퍼입니다. 또한 Write-Information은 지원되는 워크플로 활동입니다.
  - 두 개의 새 일반 매개 변수인 InformationVariable 및 InformationAction을 통해 명령의 정보 스트림을 표시하는 방법을 결정할 수 있습니다. InformationAction에 유효한 값은 SilentlyContinue, Stop, Continue, Inquire, Ignore 또는 Suspend이고, 기본값은 SilentlyContinue입니다. InformationVariable은 명령의 Write-Host 데이터를 저장하려는 변수의 이름으로 문자열을 지정합니다.
  - 새 기본 설정 변수인 InformationPreference는 Windows PowerShell 세션의 정보 스트림 데이터에 대한 기본 설정을 지정합니다. 기본값은 SilentlyContinue입니다.
  - 두 개의 새 워크플로 일반 매개 변수인 PSInformation 및 InformationAction이 추가되었습니다.
  - Format-Table 명령을 사용하는 경우 이제 스트림을 통해 전달되는 처음 300ms의 데이터를 평가하여 테이블 열의 형식이 자동으로 지정됩니다.

- [Microsoft Research](https://research.microsoft.com/)와 협업으로 새 ConvertFrom-String cmdlet이 추가되었습니다. ConvertFrom-String을 사용하면 텍스트 문자열 콘텐츠에서 구조화된 개체를 추출하고 구문 분석할 수 있습니다. 자세한 내용은 ConvertFrom-String을 참조하세요.
- 새 Convert-String cmdlet은 -Example 매개 변수에 제공하는 예제에 따라 테스트 형식을 자동으로 지정합니다.
- 새 Microsoft.PowerShell.Archive 모듈에 포함된 cmdlet을 사용하면 파일 및 폴더를 보관(ZIP이라고도 함) 파일에 압축하고, 기존 ZIP 파일에서 파일을 추출하고, ZIP 파일을 내부에 압축된 파일의 최신 버전으로 업데이트할 수 있습니다.
- 새 PackageManagement 모듈을 사용하면 인터넷에서 소프트웨어 패키지를 검색하고 설치할 수 있습니다.
  PackageManagement(이전의 OneGet) 모듈은 Windows 패키지 관리를 단일 Windows PowerShell 인터페이스와 통합하는 기존 패키지 관리자(패키지 공급자라고도 함)의 관리자 또는 멀티플렉서입니다.
- 새 PowerShellGet 모듈을 사용하면 [PowerShell 갤러리](https://www.powershellgallery.com/) 또는 내부 모듈 리포지토리에서 Register-PSRepository cmdlet을 실행하여 설정할 수 있는 모듈과 DSC 리소스를 찾고 설치, 게시 및 업데이트할 수 있습니다.
- -Force 매개 변수를 추가하지 않을 경우 기본적으로 Get-Member 결과에 멤버(속성 또는 메서드)가 표시되지 않도록 지정하기 위해 새 언어 키워드인 **Hidden**이 추가되었습니다.
  멤버가 표시되어야 하는 컨텍스트가 아닐 경우 숨김으로 표시된 속성이나 메서드는 IntelliSense 결과에도 표시되지 않습니다. 예를 들어 자동 변수 $This는 클래스 메서드에 있을 경우 숨겨진 멤버를 표시해야 합니다.
- New-Item, Remove-Item 및 Get-ChildItem이 [바로 가기 링크](https://en.wikipedia.org/wiki/Symbolic_link) 만들기 및 관리를 지원하도록 향상되었습니다. New-Item의 **ItemType** 매개 변수가 새 값인 **SymbolicLink**를 허용합니다. 이제 New-Item cmdlet을 실행하여 한 줄에 바로 가기 링크를 만들 수 있습니다.
- Get-ChildItem에 있는 새 –Depth 매개 변수를 –Recurse 매개 변수와 함께 사용하면 재귀를 제한할 수 있습니다. 예를 들어 Get-ChildItem –Recurse –Depth 2는 현재 폴더, 현재 폴더 내의 모든 자식 폴더 및 자식 폴더 내의 모든 폴더에서 결과를 반환합니다.
- 이제 Copy-Item을 사용하여 Windows PowerShell 세션 간에 파일이나 폴더를 복사할 수 있으므로 원격 컴퓨터(Nano 서버를 실행하며 다른 인터페이스가 없는 컴퓨터 포함)에 연결된 세션에 파일을 복사할 수 있습니다. 파일을 복사하려면 PSSession ID를 새 -FromSession 및 -ToSession 매개 변수의 값으로 지정하고 –Path 및 –Destination을 추가하여 각각 원래 경로와 대상을 지정합니다. 예를 들면 Copy-Item -Path c:\\myFile.txt -ToSession $s -Destination d:\\destinationFolder와 같습니다.
- Windows PowerShell 기록이 콘솔 호스트(**powershell.exe**)뿐 아니라 모든 호스팅 애플리케이션(예: Windows PowerShell ISE)에 적용되도록 향상되었습니다. 시스템 차원의 기록 사용을 포함한 기록 옵션은 관리 템플릿\Windows 구성 요소\Windows PowerShell에 있는 **PowerShell 기록 켜기** 그룹 정책 설정을 사용하도록 설정하여 구성할 수 있습니다.
- 새로운 세부 스크립트 추적 기능을 사용하면 시스템에서 Windows PowerShell 스크립트 사용을 자세히 추적하고 분석할 수 있습니다. 세부 스크립트 추적을 사용하도록 설정하면 Windows PowerShell에서 모든 스크립트 블록을 ETW(Windows용 이벤트 추적) 이벤트 로그 **Microsoft-Windows-PowerShell/Operational**에 로깅합니다.
- Windows PowerShell 5.0 이상에서는 새 암호화 메시지 구문 cmdlet이 [RFC5652](https://tools.ietf.org/html/rfc5652) 문서에 기록된 대로 메시지를 암호로 보호하기 위해 IETF 표준 형식을 사용하는 콘텐츠의 암호화 및 암호 해독을 지원합니다. Get-CmsMessage, Protect-CmsMessage 및 Unprotect-CmsMessage cmdlet이 [Microsoft.PowerShell.Security](/powershell/module/Microsoft.PowerShell.Security) 모듈에 추가되었습니다.
- [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 모듈의 새 cmdlet인 Get-Runspace, Debug-Runspace, Get-RunspaceDebug, Enable-RunspaceDebug 및 Disable-RunspaceDebug를 사용하면 Runspace에 디버그 옵션을 설정하고 Runspace에서 디버깅을 시작 및 중지할 수 있습니다. 임의의 Runspace(즉, Windows PowerShell 콘솔 또는 Windows PowerShell ISE 세션의 기본 Runspace가 아닌 Runspace)를 디버그하기 위해 Windows PowerShell에서는 스크립트에 중단점을 설정하고, 디버거를 연결하여 Runspace 스크립트를 디버그할 수 있을 때까지 추가된 중단점이 스크립트 실행을 중지하도록 할 수 있습니다. 임의의 Runspace에 대한 중첩된 디버깅 지원이 Runspace에 대한 Windows PowerShell 스크립트 디버거에 추가되었습니다.
- 새 Format-Hex cmdlet이 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 모듈에 추가되었습니다.
  Format-Hex을 사용하면 텍스트 또는 이진 데이터를 16진수 형식으로 볼 수 있습니다.
- Get-Clipboard 및 Set-Clipboard cmdlet이 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 모듈에 추가되었습니다. 두 cmdlet을 사용하면 Windows PowerShell 세션과의 콘텐츠 전송을 쉽게 수행할 수 있습니다. 클립보드 cmdlet은 이미지, 오디오 파일, 파일 목록 및 텍스트를 지원합니다.
- 새 Clear-RecycleBin cmdlet이 [Microsoft.PowerShell.Management](/powershell/module/Microsoft.PowerShell.Management) 모듈에 추가되었습니다. 이 cmdlet은 외장형 드라이브를 포함하는 고정 드라이브의 휴지통을 비웁니다. 기본적으로 cmdlet의 ConfirmImpact 속성이 ConfirmImpact.High로 설정되어 있으므로 Clear-RecycleBin 명령을 확인하라는 메시지가 표시됩니다.
- 새 New-TemporaryFile cmdlet을 사용하면 스크립팅의 일부로 임시 파일을 만들 수 있습니다. 기본적으로 새 임시 파일은 ```C:\Users\<user name>\AppData\Local\Temp```에 생성됩니다.
- 이제 Out-File, Add-Content 및 Set-Content cmdlet에 출력 뒤에 오는 새 줄을 생략하는 새 –NoNewline 매개 변수가 있습니다.
- New-Guid cmdlet은 .NET Framework Guid 클래스를 이용하여 스크립트나 DSC 리소스를 작성할 때 유용한 GUID를 생성합니다.
- 파일 버전 정보는 특히 파일이 패치된 후 잘못될 수 있으므로 FileInfo 개체에 대한 새 FileVersionRaw 및 ProductVersionRaw 스크립트 속성을 사용할 수 있습니다. 예를 들어 다음 명령을 실행하여 powershell.exe의 이러한 속성 값을 표시할 수 있습니다. 여기서 $pid는 Windows PowerShell의 실행 중 세션에 대한 프로세스 ID를 포함합니다. `Get-Process -Id $pid -FileVersionInfo | Format-List *version* -Force`
- 새 Enter-PSHostProcess 및 Exit-PSHostProcess cmdlet을 사용하면 Windows PowerShell 콘솔에서 실행 중인 현재 프로세스와 별개인 프로세스에서 Windows PowerShell 스크립트를 디버그할 수 있습니다. Enter-PSHostProcess를 실행하여 특정 프로세스 ID를 입력하거나 연결한 다음 Get-Runspace를 실행하여 프로세스 내의 활성 Runspace를 반환합니다. 프로세스 내에서 스크립트 디버그를 마쳤으면 Exit-PSHostProcess를 실행하여 프로세스에서 분리합니다.
- 새 Wait-Debugger cmdlet이 [Microsoft.PowerShell.Utility](/powershell/module/Microsoft.PowerShell.Utility) 모듈에 추가되었습니다. Wait-Debugger를 실행하면 스크립트에서 다음 문을 실행하기 전에 디버거에서 스크립트를 중지할 수 있습니다.
- 이제 Windows PowerShell 워크플로 디버거에서 명령 또는 탭 완성 기능을 지원하며 중첩된 워크플로 함수를 디버그할 수 있습니다. 이제 **Ctrl+Break**를 눌러 실행 중인 스크립트, 로컬 및 원격 세션, 워크플로 스크립트에서 디버거를 시작할 수 있습니다.
- Windows PowerShell 워크플로, 백그라운드 및 원격 세션에서 실행되는 작업에 대해 실행 중인 작업 스크립트를 디버그할 수 있도록 Debug-Job cmdlet이 [Microsoft.PowerShell.Core](/powershell/module/Microsoft.PowerShell.Core) 모듈에 추가되었습니다.
- Windows PowerShell 작업에 대해 새 AtBreakpoint 상태가 추가되었습니다. AtBreakpoint 상태는 작업이 중단점 설정을 포함하는 스크립트를 실행하고 스크립트가 중단점에 도달했을 때 적용됩니다. 디버그 중단점에서 작업이 중지되면 Debug-Job cmdlet을 실행하여 작업을 디버그해야 합니다.
- Windows PowerShell 5.0에서는 $PSModulePath의 동일한 폴더에서 단일 Windows PowerShell 모듈의 여러 버전에 대한 지원을 구현합니다. 모듈의 원하는 버전을 가져올 수 있도록 RequiredVersion 속성이 ModuleSpecification 클래스에 추가되었습니다. 이 속성은 ModuleVersion 속성과 함께 사용할 수 없습니다. 이제 RequiredVersion이 Get-Module, Import-Module 및 Remove-Module cmdlet에 대한 FullyQualifiedName 매개 변수 값의 일부로 지원됩니다.
- 이제 Test-ModuleManifest cmdlet을 실행하여 모듈 버전 유효성 검사를 수행할 수 있습니다.
- 이제 Get-Command cmdlet의 결과에 Version 열이 표시됩니다. 새 Version 속성이 CommandInfo 클래스에 추가되었습니다. Get-Command는 동일한 모듈의 여러 버전에 포함된 명령을 보여 줍니다. 또한 Version 속성은 CmdletInfo의 파생 클래스인 CmdletInfo 및 ApplicationInfo의 일부입니다.
- Get-Command에는 ShowCommand 정보를 PSObjects로 반환하는 새 매개 변수 -ShowCommandInfo가 있습니다. 이 매개 변수는 Windows PowerShell ISE에서 Windows PowerShell 원격 기능을 사용하여 Show-Command를 실행할 때 특히 유용한 기능입니다. –ShowCommandInfo 매개 변수는 Microsoft.PowerShell.Utility 모듈의 기존 Get-SerializedCommand 함수를 대체하지만 하위 수준 스크립팅을 지원하기 위해 Get-SerializedCommand 스크립트를 계속 사용할 수 있습니다.
- 새 Get-ItemPropertyValue cmdlet을 사용하면 점 표기법을 사용하지 않고 속성 값을 가져올 수 있습니다. 예를 들어 이전 Windows PowerShell 릴리스에서는 다음 명령을 실행하여 PowerShellEngine 레지스트리 키의 Application Base 속성 값을 가져올 수 있습니다. **(Get-ItemProperty -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase).ApplicationBase** Windows PowerShell 5.0 이상에서는 **Get-ItemPropertyValue -Path HKLM:\\SOFTWARE\\Microsoft\\PowerShell\\3\\PowerShellEngine -Name ApplicationBase**를 실행할 수 있습니다.
- 이제 Windows PowerShell 콘솔이 Windows PowerShell ISE와 같이 구문 색 지정을 사용합니다.
- 새 NetworkSwitch 모듈에 포함된 cmdlet을 사용하면 스위치, VLAN(가상 LAN) 및 기본 계층 2 네트워크 스위치 포트 구성을 Windows Server 2012 R2 로고 인증 네트워크 스위치에 적용할 수 있습니다.
- 단일 모듈의 여러 버전을 저장할 수 있도록 FullyQualifiedName 매개 변수가 Import-Module 및 Remove-Module cmdlet에 추가되었습니다.
- Save-Help, Update-Help, Import-PSSession, Export-PSSession 및 Get-Command에 ModuleSpecification 형식의 새로운 매개 변수인 FullyQualifiedModule이 있습니다. 정규화된 이름으로 모듈을 지정하려면 이 매개 변수를 추가합니다.
- **$PSVersionTable.PSVersion** 값이 5.0으로 업데이트되었습니다.
- WMF 5.0(PowerShell 5.0)에는 **Pester** 모듈이 포함됩니다. Pester는 PowerShell에 대한 단위 테스트 프레임워크입니다. 스크립트에 대한 테스트를 만들 수 있는 몇 가지 간단한 사용 키워드를 제공합니다.

### <a name="new-features-in-windows-powershell-desired-state-configuration"></a>Windows PowerShell 필요한 상태 구성의 새로운 기능

- Windows PowerShell의 향상된 언어 기능을 사용하면 클래스를 통해 Windows PowerShell DSC(필요한 상태 구성) 리소스를 정의할 수 있습니다. 이제 Import-DscResource가 진정한 동적 키워드입니다. Windows PowerShell이 지정된 모듈의 루트 모듈을 구문 분석하여 DscResource 특성이 포함된 클래스를 검색합니다. 이제 클래스를 사용하여 모듈 폴더의 MOF 파일 또는 DSCResource 하위 폴더가 필요하지 않은 DSC 리소스를 정의할 수 있습니다. Windows PowerShell 모듈 파일에 여러 가지 DSC 리소스 클래스가 포함될 수 있습니다.
- 새 ThrottleLimit 매개 변수가 PSDesiredStateConfiguration 모듈의 다음 cmdlet에 추가되었습니다. 동시에 명령을 실행할 대상 컴퓨터 또는 디바이스 수를 지정하려면 ThrottleLimit 매개 변수를 추가합니다.
  - Get-DscConfiguration
  - Get-DscConfigurationStatus
  - Get DscLocalConfigurationManager
  - Restore-DscConfiguration
  - Test-DscConfiguration
  - Compare-DscConfiguration
  - Publish-DscConfiguration
  - Set-DscLocalConfigurationManager
  - Start-DscConfiguration
  - Update-DscConfiguration
- 중앙 집중식 DSC 오류 보고를 사용하면 자세한 오류 정보가 이벤트 로그에 기록될 뿐 아니라 나중에 분석하기 위해 중앙 위치로 보낼 수 있습니다. 이 중앙 위치를 사용하여 해당 환경의 모든 서버에 대해 발생한 DSC 구성 오류를 저장할 수 있습니다. 메타 구성에서 보고서 서버를 정의하면 모든 오류가 보고서 서버로 전송된 후 데이터베이스에 저장됩니다. 끌어오기 서버에서 구성을 가져올 대상 노드를 구성했는지 여부에 관계없이 이 기능을 설정할 수 있습니다.
- 향상된 Windows PowerShell ISE를 사용하여 DSC 리소스를 쉽게 작성할 수 있습니다. 이제 다음을 수행할 수 있습니다.
  - **구성** 블록이나 **노드** 블록 내 빈 줄에 **Ctrl+Space**를 입력하여 해당 블록 내의 모든 DSC 리소스 나열
  - **열거형** 형식인 리소스 속성 자동 완성
  - 구성에 있는 다른 리소스 인스턴스에 따라 DSC 리소스의 **DependsOn** 속성 자동 완성
  - 리소스 속성 값의 탭 완성 기능 향상
- 이제 사용자가 노드 블록에 **PSDscRunAsCredential** 특성을 추가하여 지정된 자격 증명 집합으로 리소스를 실행할 수 있습니다. 예를 들면 PSDscRunAsCredential = Get-Credential Contoso\\DscUser와 같습니다. 이 기능은 Windows Installer 및 실행 가능한 설치 관리자를 실행하거나, 사용자별 레지스트리 하이브에 액세스하거나, 현재 사용자 컨텍스트 외부에서 다른 작업을 수행하는 구성을 만드는 데 유용합니다.
- **Configuration** 키워드에 대해 32비트(x86 기반) 지원이 추가되었습니다.
- 이제 생성된 구성 함수에 \[CmdletBinding()]을 추가하여 정의된 DSC 구성에 대한 사용자 지정 도움말 지원이 Windows PowerShell에 포함됩니다.
- 새 **DscLocalConfigurationManager** 특성은 DSC 로컬 구성 관리자를 구성하는 데 사용되는 구성 블록을 메타 구성으로 지정합니다. 이 특성은 DSC 로컬 구성 관리자를 구성하는 항목만 포함하도록 구성을 제한합니다. 처리하는 동안 이 구성은 \*.meta.mof 파일을 생성하며, 이 파일은 Set-DscLocalConfigurationManager cmdlet을 실행하여 적절한 대상 노드로 전송됩니다.
- 이제 Windows PowerShell 5.0에서 부분 구성이 허용됩니다. 구성 문서를 조각으로 노드에 전달할 수 있습니다. 노드에서 여러 조각의 구성 문서를 받으려면 노드의 로컬 구성 관리자를 먼저 설정하여 필요한 조각을 지정해야 합니다.
- 컴퓨터 간 동기화는 Windows PowerShell 5.0의 DSC에 추가된 새로운 기능입니다. 이제 기본 제공 WaitFor\* 리소스(**WaitForAll**, **WaitForAny** 및 **WaitForSome**)를 사용하여 외부 오케스트레이션 없이 구성 실행 중 컴퓨터 간에 종속성을 지정할 수 있습니다. 이러한 리소스는 WS-Man 프로토콜을 통한 CIM 연결을 사용하여 노드 간 동기화를 제공합니다.
  구성은 다른 컴퓨터의 특정 리소스 상태가 변경될 때까지 대기할 수 있습니다.
- 새로운 위임 보안 기능인 JEA(Just Enough Administration)는 DSC 및 Windows PowerShell 제약 Runspace를 이용하여 의도적이든 아니든 간에 직원에 의한 데이터 손실이나 손상으로부터 기업을 보호합니다. xJEA DSC 리소스를 다운로드할 수 있는 위치 등 JEA에 대한 자세한 내용은 [Just Enough Administration](/powershell/scripting/learn/remoting/jea/overview)을 참조하세요.
- 다음과 같은 새 cmdlet이 PSDesiredStateConfiguration 모듈에 추가되었습니다.
  - 새 Get-DscConfigurationStatus cmdlet은 대상 노드에서 구성 상태에 대한 고급 정보를 가져옵니다. 마지막 구성이나 모든 구성의 상태를 가져올 수 있습니다.
  - 새 Compare-DscConfiguration cmdlet은 지정된 구성과 하나 이상 대상 노드의 실제 상태를 비교합니다.
  - 새 Publish-DscConfiguration cmdlet은 구성 MOF 파일을 대상 노드에 복사하지만 구성을 적용하지는 않습니다. 이 구성은 다음 일관성 검사 중이나 Update-DscConfiguration cmdlet을 실행할 때 적용됩니다.
  - 새 Test-DscConfiguration cmdlet을 사용하면 결과로 생성된 구성이 필요한 구성과 일치하는지 확인할 수 있습니다. 구성이 필요한 구성과 일치하면 True가 반환되고, 실제 구성이 필요한 구성과 일치하지 않으면 False가 반환됩니다.
  - 새 Update-DscConfiguration cmdlet은 구성을 강제로 처리합니다. 로컬 구성 관리자가 끌어오기 모드인 경우 cmdlet은 구성을 적용하기 전에 끌어오기 서버에서 가져옵니다.

### <a name="new-features-in-windows-powershell-ise"></a>Windows PowerShell ISE의 새로운 기능

- 이제 편집할 파일이 저장되어 있는 컴퓨터에서 원격 세션을 시작한 다음, 원격 컴퓨터에서 **PSEdit \<경로 및 파일 이름\>** 을 실행하기 위해 Enter-PSSession을 실행하여 Windows PowerShell ISE의 로컬 복사본에서 원격 Windows PowerShell 스크립트와 파일을 편집할 수 있습니다. 이 기능을 사용하면 Windows PowerShell ISE를 실행할 수 없는 Windows Server의 Server Core 설치 옵션에 저장되어 있는 Windows PowerShell 파일을 쉽게 편집할 수 있습니다.
- 이제 Windows PowerShell ISE에서 Start-Transcript cmdlet이 지원됩니다.
- 이제 Windows PowerShell ISE에서 원격 스크립트를 디버그할 수 있습니다.
- 새 메뉴 명령인 **모두 중단**(Ctrl+B)은 로컬 스크립트와 원격으로 실행 중인 스크립트 둘 다에 대해 디버거를 시작합니다.

### <a name="new-features-in-windows-powershell-web-services-management-odata-iis-extension"></a>Windows PowerShell 웹 서비스의 새로운 기능(관리 OData IIS 확장)

- Windows PowerShell 5.0부터 새 [Microsoft.PowerShell.OdataUtils](/powershell/module/microsoft.powershell.odatautils) 모듈에 있는 Export-ODataEndpointProxy cmdlet을 실행하여 지정된 OData 엔드포인트가 노출하는 기능에 따라 Windows PowerShell cmdlet 집합을 생성할 수 있습니다.

### <a name="notable-bug-fixes-in-windows-powershell-50"></a>Windows PowerShell 5.0의 중요한 버그 수정

- Windows PowerShell 5.0에는 COM 개체로 작업할 때 성능 향상에 도움이 되는 새로운 COM 구현이 포함되어 있습니다. 효과를 보여 주는 동영상 데모를 보려면 [Com_Perf_Improvements](https://1drv.ms/1qu3UPZ)를 참조하세요.
- Windows PowerShell 세션의 첫 번째 탭 완성 성능이 훨씬 향상되어 탭 완성 시간이 거의 500ms만큼 단축되었습니다.

## <a name="new-features-in-windows-powershell-40"></a>Windows PowerShell 4.0의 새로운 기능

Windows PowerShell 4.0은 이전 버전과 호환됩니다. Windows PowerShell 3.0 및 Windows PowerShell 2.0용으로 설계된 cmdlet, 공급자, 모듈, 스냅인, 스크립트, 함수 및 프로필은 Windows PowerShell 4.0에서 변경 없이 사용할 수 있습니다.

Windows 8.1 및 Windows Server 2012 R2에서는 Windows PowerShell 4.0이 기본적으로 설치됩니다. Windows 7 SP1 또는 Windows Server 2008 R2에 Windows PowerShell 4.0을 설치하려면 [Windows Management Framework 4.0](https://www.microsoft.com/download/details.aspx?id=40855)을 다운로드하여 설치합니다. Windows Management Framework 4.0을 설치하기 전에 다운로드 정보를 확인하고 모든 시스템 요구 사항을 충족해야 합니다.

- [Windows PowerShell의 새로운 기능](#new-features-in-windows-powershell-1)
- [Windows PowerShell ISE(통합 스크립팅 환경)의 새로운 기능](#new-features-in-windows-powershell-integrated-scripting-environment-ise)
- [Windows PowerShell 워크플로의 새로운 기능](#new-features-in-windows-powershell-workflow)
- [Windows PowerShell 웹 서비스의 새로운 기능](#new-features-in-windows-powershell-web-services)
- [Windows PowerShell 웹 액세스의 새로운 기능](#new-features-in-windows-powershell-web-access)
- [Windows PowerShell 4.0의 중요한 버그 수정](#notable-bug-fixes-in-windows-powershell-40)

Windows PowerShell 4.0에는 다음과 같은 새로운 기능이 있습니다.

### <a name="new-features-in-windows-powershell"></a><a name="new-features-in-windows-powershell-1" />Windows PowerShell의 새로운 기능

- **Windows PowerShell DSC**(필요한 상태 구성)는 Windows PowerShell 4.0에서 소프트웨어 서비스와 해당 서비스가 실행되는 환경에 대한 구성 데이터를 배포 및 관리하는 데 사용되는 새로운 관리 시스템입니다. DSC에 대한 자세한 내용은 [Windows PowerShell 필요한 상태 구성 시작](/powershell/scripting/dsc/getting-started/wingettingstarted)을 참조하세요.
- 이제 **Save-Help**를 사용하여 원격 컴퓨터에 설치되는 모듈에 대한 도움말을 저장할 수 있습니다. Save-Help를 사용하여 인터넷에 연결된 클라이언트에서 도움말 모듈을 다운로드한 다음(도움말이 필요한 일부 모듈은 반드시 설치해야 함) 저장된 도움말을 인터넷에 액세스할 수 없는 원격 컴퓨터 또는 원격 공유 폴더에 복사할 수 있습니다.
- 원격 컴퓨터에서 실행 중인 스크립트와 Windows PowerShell 워크플로를 디버그할 수 있도록 Windows PowerShell 디버거가 향상되었습니다. 이제 Windows PowerShell 명령줄 또는 Windows PowerShell ISE에서 Windows PowerShell 워크플로를 스크립트 수준으로 디버그할 수 있습니다. 이제 원격 세션을 통해 Windows PowerShell 스크립트(스크립트 워크플로 포함)를 디버그할 수 있습니다. 원격 디버깅 세션은 연결이 끊어졌다가 나중에 다시 연결하면 Windows PowerShell 원격 세션을 통해 유지됩니다.
- **Register-ScheduledJob** 및 **Set-ScheduledJob**의 **RunNow** 매개 변수를 사용하면 **Trigger** 매개 변수를 사용하여 작업에 대한 즉시 시작 날짜와 시간을 설정할 필요가 없습니다.
- 이제 **Invoke-RestMethod** 및 **Invoke-WebRequest**에서 Headers 매개 변수를 사용하여 모든 헤더를 설정할 수 있습니다. 이 매개 변수는 이전에도 있었지만 예외 또는 오류를 발생하는 웹 cmdlet의 여러 매개 변수 중 하나였습니다.
- **Get-Module**에 **ModuleSpecification\[]** 형식의 새로운 매개 변수인 **FullyQualifiedName**이 있습니다. 이제 Get-Module의 **FullyQualifiedName** 매개 변수에서 모듈의 이름, 버전 및 GUID(선택 사항)를 사용하여 모듈을 지정할 수 있습니다.
- Windows Server 2012 R2에 대한 기본 실행 정책 설정은 **RemoteSigned**입니다. Windows 8.1에서는 기본 설정이 변경되지 않았습니다.
- Windows PowerShell 4.0 이상에서는 동적 메서드 이름을 사용한 메서드 호출이 지원됩니다.
  변수를 사용하여 메서드 이름을 저장한 다음 변수를 호출하여 메서드를 동적으로 호출할 수 있습니다.
- **PSElapsedTimeoutSec** 워크플로 일반 매개 변수로 지정한 시간 제한 기간이 경과해도 비동기 워크플로는 더 이상 삭제되지 않습니다.
- 새 매개 변수 **RepeatIndefinitely**가 **New-JobTrigger** 및 **Set-JobTrigger** cmdlet에 추가되었습니다. 이 매개 변수를 사용하면 예약된 작업을 무기한 동안 되풀이해서 실행하기 위해 **RepetitionDuration** 매개 변수에 **TimeSpan.MaxValue** 값을 지정할 필요가 없습니다.
- **Passthru** 매개 변수가 **Enable-JobTrigger** 및 **Disable-JobTrigger** cmdlet에 추가되었습니다. Passthru 매개 변수는 명령에서 만들었거나 수정한 개체를 표시합니다.
- **Add-Computer** 및 **Remove-Computer** cmdlet에서 작업 그룹을 지정하는 매개 변수 이름이 이제 일치합니다. 이제 두 cmdlet 모두 **WorkgroupName** 매개 변수를 사용합니다.
- 새 일반 매개 변수 **PipelineVariable**이 추가되었습니다. PipelineVariable을 사용하여 파이프된 명령의 결과 또는 파이프된 명령의 일부를 나머지 파이프라인을 통해 전달할 수 있는 변수로 저장할 수 있습니다.
- 이제 메서드 구문을 사용한 컬렉션 필터링이 지원됩니다. 즉, Where() 또는 Where-Object의 경우처럼 메서드 호출로 서식 지정된 간소화된 구문을 사용하여 개체 모음을 필터링할 수 있습니다. 다음은 이에 대한 예입니다. (Get-Process).where({$_.Name -match 'powershell'})
- **Get-Process** cmdlet에는 **IncludeUserName**이라는 새 스위치 매개 변수가 있습니다.
- 지정된 파일에 대한 여러 형식 중 하나로 파일 해시를 반환하는 새 **Get-FileHash** cmdlet이 추가되었습니다.
- Windows PowerShell 4.0에서는 모듈의 매니페스트에서 **DefaultCommandPrefix** 키를 사용하거나 사용자가 **Prefix** 매개 변수를 사용하여 모듈을 가져올 경우 모듈의 **ExportedCommands** 속성은 모듈의 명령을 접두사와 함께 표시합니다. 모듈의 정규화된 구문 ModuleName\\CommandName을 사용하여 명령을 실행할 경우 명령 이름에 접두사를 포함해야 합니다.
- **$PSVersionTable.PSVersion** 값이 4.0으로 업데이트되었습니다.
- **Where()** 연산자 동작이 변경되었습니다. `Collection.Where('property -match name')`은 더 이상 `"Property -CompareOperator Value"` 형식의 문자열 식을 허용하지 않습니다.
  그러나 **Where()** 연산자는 scriptblock 형식의 문자열 식을 허용합니다. 이 연산자는 여전히 지원됩니다.

### <a name="new-features-in-windows-powershell-integrated-scripting-environment-ise"></a>Windows PowerShell ISE(통합 스크립팅 환경)의 새로운 기능

- Windows PowerShell ISE에서는 Windows PowerShell 워크플로 디버깅과 원격 스크립트 디버깅을 모두 지원합니다.
- Windows PowerShell 필요한 상태 구성 공급자 및 구성에 대한 IntelliSense 지원이 추가되었습니다.

### <a name="new-features-in-windows-powershell-workflow"></a>Windows PowerShell 워크플로의 새로운 기능

- System Center Orchestrator에 사용된 것과 같은 반복 파이프라인 즉, 스트리밍을 사용하여 섞어서 실행하지 않고 왼쪽에서 오른쪽으로 실행하는 파이프라인의 컨텍스트에서 새 **PipelineVariable** 일반 매개 변수에 대한 지원이 추가되었습니다.
- 현재 runspace에 없는 명령을 사용하는 경우처럼 탭 완성 시나리오를 벗어나서 작동하도록 매개 변수 바인딩이 크게 향상되었습니다.
- 사용자 지정 컨테이너 활동 지원이 Windows PowerShell 워크플로에 추가되었습니다. 활동 매개 변수가 **Activity**, **Activity\[]** 형식(또는 활동의 제네릭 컬렉션)이고 사용자가 스크립트 블록을 인수로 제공한 경우 Windows PowerShell 워크플로는 일반 Windows PowerShell 스크립트-워크플로 컴파일을 사용할 때와 마찬가지로 스크립트 블록을 XAML로 변환합니다.
- 충돌이 발생한 후에 Windows PowerShell 워크플로는 관리되는 노드에 자동으로 다시 연결됩니다.
- 이제 **ThrottleLimit** 속성을 사용하여 **Foreach -Parallel** 활동 문을 제한할 수 있습니다.
- **ErrorAction** 일반 매개 변수는 워크플로에 국한되는 새 유효한 값 **Suspend**가 있습니다.
- 이제 활성 세션, 진행 중인 작업 및 보류 중인 작업이 없는 경우 워크플로 엔드포인트가 자동으로 닫힙니다. 자동 종료 조건이 충족될 경우 이 기능은 워크플로 서버 역할을 하는 컴퓨터의 리소스를 절약합니다.

### <a name="new-features-in-windows-powershell-web-services"></a>Windows PowerShell 웹 서비스의 새로운 기능

- cmdlet을 실행하는 중에 Windows PowerShell 웹 서비스(PSWS, 관리 OData IIS 확장이라고도 함)에서 오류가 발생할 경우 자세한 오류 메시지가 호출자에게 반환됩니다. 또한 오류 코드는 [Microsoft Azure REST API 오류 코드 지침](/rest/api/storageservices/Common-REST-API-Error-Codes)을 따릅니다.
- 이제 엔드포인트에서 API 버전을 정의하고 특정 API 버전을 강제로 사용할 수 있습니다. 클라이언트와 서버의 버전이 일치하지 않을 경우 항상 클라이언트와 서버 모두에 오류가 표시됩니다.
- 스키마에서 누락된 필드에 대한 값을 자동으로 생성하여 디스패치 스키마 관리를 간소화했습니다. 디스패치 스키마가 없는 경우에도 유용한 시작점으로 생성됩니다.
- Windows PowerShell의 **PSTypeConverter**와 비슷하게 동작하여 기본 생성자가 아닌 다른 생성자를 사용하는 형식을 지원하도록 PSWS의 형식 처리가 향상되었습니다. 따라서 PSWS에서 복잡한 형식을 사용할 수 있습니다.
- 이제 쿼리를 실행하는 동안 PSWS에서 연결된 인스턴스를 확장할 수 있습니다. 대용량 이진 콘텐츠(예: 이미지, 오디오, 비디오)의 경우 높은 전송 비용이 발생하므로 인코딩하지 않고 이진 데이터를 전송하는 것이 좋습니다. PSWS에서는 인코딩하지 않고 전송하기 위해 명명된 리소스 스트림을 사용합니다.
  명명된 리소스 스트림은 **Edm.Stream** 형식 엔터티의 속성입니다. 각 명명된 리소스 스트림에서는 GET 또는 UPDATE 작업에 대해 별도의 URI를 사용합니다.
- 이제 OData 작업을 사용하여 리소스에서 CRUD(Create, Read, Update, Delete) 이외의 메서드를 호출할 수 있습니다. HTTP POST 요청을 작업에 대해 정의된 URI에 전송하여 작업을 호출할 수 있습니다. 작업에 대한 매개 변수를 POST 요청의 본문에 정의되어 있습니다.
- Microsoft Azure 지침을 준수하려면 모든 URL을 간소화해야 합니다. **Key As Segment**에 포함된 변경에 따라 단일 키를 세그먼트로 표시할 수 있습니다. 앞에 표시된 것처럼 여러 키 값을 사용하는 참조에서는 쉼표로 구분된 값을 괄호로 묶어서 표기해야 합니다.
- 이 PSWS 이전 릴리스에서는 만들기, 업데이트 또는 삭제 작업을 수행하려면 최상위 리소스에서 Post, Put 또는 Delete를 호출해야 했습니다. 이 PSWS 릴리스의 새로운 기능인 포함된 리소스 작업을 사용하면 동일한 리소스에 직접 연결하지 않은 상태에서도 해당 리소스가 포함된 경우와 동일한 결과를 얻을 수 있습니다.

### <a name="new-features-in-windows-powershell-web-access"></a>Windows PowerShell 웹 액세스의 새로운 기능

- 웹 기반 Windows PowerShell 웹 액세스 콘솔에서 기존 세션에 대한 연결을 끊었다가 다시 연결할 수 있습니다. 웹 기반 콘솔에서 **저장** 단추를 사용하면 세션을 삭제하지 않고 세션에서 연결을 끊었다가 나중에 세션에 다시 연결할 수 있습니다.
- 기본 매개 변수를 로그인 페이지에 표시할 수 있습니다. 기본 매개 변수를 표시하려면 **web.config** 파일에서 로그인 페이지의 **옵션 연결 설정** 영역에 표시되는 모든 설정에 대한 값을 구성합니다. **web.config** 파일을 사용하여 두 번째 또는 대체 자격 증명 집합을 제외한 모든 옵션 연결 설정을 구성할 수 있습니다.
- Windows Server 2012 R2에서 Windows PowerShell 웹 액세스에 대한 권한 부여 규칙을 원격으로 관리할 수 있습니다. 이제 **Add-PswaAuthorizationRule** 및 **Test-PswaAuthorizationRule** cmdlet에는 관리자가 원격 컴퓨터 또는 Windows PowerShell 웹 액세스 세션에서 권한 부여 규칙을 관리하는 데 사용할 수 있는 Credential 매개 변수가 포함되어 있습니다.
- 이제 세션마다 새로운 브라우저 탭을 사용하여 단일 브라우저 세션에 여러 Windows PowerShell 웹 액세스 세션을 포함할 수 있습니다. 웹 기반 Windows PowerShell 콘솔에서 새 세션에 연결하기 위해 더 이상 새 브라우저 세션을 열 필요가 없습니다.

### <a name="notable-bug-fixes-in-windows-powershell-40"></a>Windows PowerShell 4.0의 중요한 버그 수정

- 이제 **Get-Counter**가 프랑스어 버전 Windows에서 아포스트로피 문자를 포함하는 카운터를 반환할 수 있습니다.
- 이제 역직렬화된 개체에서 **GetType** 메서드를 볼 수 있습니다.
- 이제 필요한 경우 **#Requires** 문을 사용하여 관리자 액세스 권한을 요청할 수 있습니다.
- 이제 **Import-Csv** cmdlet이 빈 줄을 무시합니다.
- **Invoke-WebRequest** 명령을 실행 중일 때 Windows PowerShell ISE에서 너무 많은 메모리를 사용하는 문제가 수정되었습니다.
- 이제 **Get-Module**이 **Version** 열에 모듈 버전을 표시합니다.
- Remove-Item –Recurse는 이제 예상대로 하위 폴더에서 항목을 제거합니다.
- **UserName** 속성이 **Get-Process** 출력 개체에 추가되었습니다.
- 이제 **Invoke-RestMethod** cmdlet이 사용 가능한 모든 결과를 반환합니다.
- 이제 해시 테이블에 아직 액세스하지 않은 경우에도 **Add-Member**가 해시 테이블에 적용됩니다.
- 속성 값이 null이거나 비어 있는 경우에 **Select-Object –Expand**가 더 이상 실패하거나 예외를 생성하지 않습니다.
- 이제 개체에서 **ComputerName** 속성을 가져오는 다른 명령과 함께 **Get-Process**를 파이프라인에서 사용할 수 있습니다.
- 이제 **ConvertTo-Json** 및 **ConvertFrom-Json**이 큰따옴표 안의 용어를 허용하고 해당 오류 메시지를 지역화할 수 있습니다.
- 이제 **Get-Job**이 새 세션에서도 완료된 예약 작업을 모두 반환합니다.
- Windows PowerShell 4.0에서 **FileSystem** 공급자를 사용하여 VHD 탑재 및 탑재 해제 문제를 수정했습니다. 이제 Windows PowerShell에서 동일한 세션에 탑재된 새로운 드라이브를 검색할 수 있습니다.
- 이제 작업 유형을 사용하기 위해 더 이상 **ScheduledJob** 또는 **Workflow** 모듈을 명시적으로 로드할 필요가 없습니다.
- 중첩된 워크플로를 정의하는 워크플로를 가져오는 프로세스의 성능이 향상되어, 이제 프로세스가 더 빨라졌습니다.

## <a name="new-features-in-windows-powershell-30"></a>Windows PowerShell 3.0의 새로운 기능

Windows PowerShell 3.0에는 다음과 같은 새로운 기능이 있습니다.

- [Windows PowerShell 워크플로](#windows-powershell-workflow)
- [Windows PowerShell 웹 액세스](#windows-powershell-web-access)
- [Windows PowerShell ISE의 새로운 기능](#new-windows-powershell-ise-features)
- [Microsoft .NET Framework 4.0 지원](#support-for-microsoft-net-framework-4)
- [Windows 사전 설치 환경 지원](#support-for-windows-preinstallation-environment)
- [연결이 끊긴 세션](#disconnected-sessions)
- [강력한 세션 연결](#robust-session-connectivity)
- [업데이트할 수 있는 도움말 시스템](#updatable-help-system)
- [향상된 온라인 도움말](#enhanced-online-help)
- [CIM 통합](#cim-integration)
- [세션 구성 파일](#session-configuration-files)
- [예약된 작업 및 작업 스케줄러 통합](#scheduled-jobs-and-task-scheduler-integration)
- [Windows PowerShell 언어 향상](#windows-powershell-language-enhancements)
- [새로운 핵심 Cmdlet](#new-core-cmdlets)
- [기존 핵심 Cmdlet 및 공급자에서 향상된 기능](#improvements-to-existing-core-cmdlets-and-providers)
- [원격 모듈 가져오기 및 검색](#remote-module-import-and-discovery)
- [고급 탭 완성](#enhanced-tab-completion)
- [모듈 자동 로드](#module-auto-loading)
- [모듈 환경 향상](#module-experience-improvements)
- [간소화된 명령 검색](#simplified-command-discovery)
- [향상된 로깅, 진단 및 그룹 정책 지원](#improved-logging-diagnostics-and-group-policy-support)
- [서식 지정 및 출력 향상](#formatting-and-output-improvements)
- [향상된 콘솔 호스트 환경](#enhanced-console-host-experience)
- [새 Cmdlet 및 호스팅 API](#new-cmdlet-and-hosting-apis)
- [성능 향상](#performance-improvements)
- [RunAs 및 공유 호스트 지원](#runas-and-shared-host-support)
- [특수 문자 처리 기능 향상](#special-character-handling-improvements)

### <a name="windows-powershell-workflow"></a>Windows PowerShell 워크플로

Windows PowerShell 워크플로를 통해 Windows PowerShell에서 Windows Workflow Foundation의 강력한 기능을 사용할 수 있습니다.
XAML 또는 Windows PowerShell 언어로 워크플로를 작성한 후 cmdlet을 실행할 때처럼 워크플로를 실행할 수 있습니다. `Get-Command` cmdlet은 워크플로 명령을 가져오고 `Get-Help` cmdlet은 워크플로에 대한 도움말을 가져옵니다.

워크플로는 장기적으로 자주 병렬 실행 가능하고, 반복, 중단, 일시 중단 및 다시 시작 가능한 다중 컴퓨터 관리 활동의 시퀀스입니다. 네트워크 중단, Windows 다시 시작, 정전 등과 같은 의도적이거나 우연적인 중단으로부터 워크플로를 다시 시작할 수 있습니다.

또한 워크플로는 이식 가능합니다. 즉, 워크플로는 XAML 파일로 내보내거나 XAML 파일에서 가져올 수 있습니다. 위임된 IT 사용자나 하위 IT 사용자는 사용자 지정 세션 구성을 통해 워크플로 또는 워크플로 내의 활동을 실행할 수 있습니다.

다음은 Windows PowerShell 워크플로의 이점입니다.

- 순차화된 장기 실행 작업의 자동화.
- **장기 실행 작업 원격 모니터링**. 활동의 상태 및 진행률을 언제든지 볼 수 있습니다.
- **다중 컴퓨터 관리.** 동시에 수백 개의 관리되는 노드에서 작업을 워크플로로 실행합니다.
  Windows PowerShell 워크플로에는 다중 컴퓨터 관리 시나리오를 지원하는 일반 관리 매개 변수의 기본 제공 라이브러리(예: **PSComputerName**)가 포함되어 있습니다.
- **복잡한 프로세스의 단일 작업 실행.** 전체 엔드투엔드 시나리오를 단일 워크플로로 구현하는 관련 스크립트를 결합할 수 있습니다.
- **지속성**: 워크플로를 처음부터 다시 시작하지 않고 마지막 지속성 작업 또는 검사점에서 워크플로를 다시 시작할 수 있도록 작성자가 정의한 특정 지점에서 워크플로를 저장하거나 검사점을 지정합니다.
- **견고성.** 자동화된 오류 복구. 워크플로가 계획되거나 계획되지 않은 다시 시작 후에 유지됩니다. 워크플로 실행을 일시 중지한 다음 마지막 지속성 지점에서 워크플로를 다시 시작할 수 있습니다.
  워크플로 작성자는 하나 이상의 관리되는 노드에서 오류가 발생한 경우 특정 활동을 다시 실행하도록 지정할 수 있습니다.
- **연결을 끊고, 다시 연결하여 연결이 끊긴 세션에서 실행할 수 있습니다.** 사용자는 워크플로 서버에서 연결하고 연결을 끊을 수 있지만 워크플로는 지속적으로 실행됩니다. 워크플로를 중단하지 않고 클라이언트 컴퓨터에서 로그오프하거나 클라이언트 컴퓨터를 다시 시작하고 다른 컴퓨터에서 워크플로 실행을 모니터링할 수 있습니다.
- **일정 예약.** Windows PowerShell cmdlet 또는 스크립트처럼 워크플로 작업을 예약할 수 있습니다.
- **워크플로 및 연결 제한.** 워크플로 실행 및 노드 연결을 제한하여 확장성 및 고가용성 시나리오를 지원할 수 있습니다.

### <a name="windows-powershell-web-access"></a>Windows PowerShell 웹 액세스

Windows PowerShell 웹 액세스는 웹 기반 콘솔에서 Windows PowerShell 명령 및 스크립트를 실행할 수 있는 Windows Server 2012 기능입니다. 웹 기반 콘솔을 사용하는 디바이스에서는 Windows PowerShell, 원격 관리 소프트웨어 또는 브라우저 플러그 인 설치가 필요하지 않습니다. 올바르게 구성된 Windows PowerShell 웹 액세스 게이트웨이와 JavaScript를 지원하고 쿠키를 적용하는 클라이언트 디바이스 브라우저만 있으면 됩니다.

자세한 내용은 [Windows PowerShell 웹 액세스 배포](/powershell/scripting/components/web-access/install-and-use-windows-powershell-web-access)를 참조하세요.

### <a name="new-windows-powershell-ise-features"></a>Windows PowerShell ISE의 새로운 기능

Windows PowerShell 3.0의 경우 Windows PowerShell ISE(통합 스크립팅 환경)에 IntelliSense, Show-명령 창, 통합 콘솔 창, 코드 조작, 중괄호 일치, 섹션 확장/축소, 자동 저장, 최근 항목 목록, 서식 있는 복사, 블록 복사, Windows PowerShell 스크립트 워크플로 작성 전체 지원 등과 같은 많은 새로운 기능이 있습니다. 자세한 내용은 [about_Windows_PowerShell_ISE](/powershell/module/microsoft.powershell.core/about/about_windows_powershell_ise)를 참조하세요.

### <a name="support-for-microsoft-net-framework-4"></a>Microsoft .NET Framework 4 지원

Windows PowerShell은 Common Language Runtime 4.0을 기반으로 합니다. Cmdlet, 스크립트 및 워크플로 작성자는 Windows PowerShell의 새로운 Microsoft .NET Framework 4 클래스를 애플리케이션 호환성 및 배포, 관리되는 확장 프레임워크, 병렬 계산, 네트워킹, Windows Communication Foundation, Windows Workflow Foundation 등과 같은 기능과 함께 사용할 수 있습니다.

### <a name="support-for-windows-preinstallation-environment"></a>Windows 사전 설치 환경 지원

Windows PowerShell 3.0은 Windows 8용 Windows PE(Windows 사전 설치 환경) 4.0의 선택적 구성 요소입니다. Windows PE는 운영 체제가 없는 컴퓨터를 시작하고 Windows 설치를 준비하는 최소 운영 체제입니다. Windows PE를 사용하면 하드 드라이브의 파티션을 추가하여 포맷하고, 디스크 이미지를 컴퓨터에 복사하고, 네트워크 공유에서 Windows 설치 프로그램을 시작할 수 있습니다.
Windows PE에서 Windows PowerShell 3.0을 사용하여 배포, 진단 및 복구 시나리오를 관리할 수 있습니다.

### <a name="disconnected-sessions"></a>연결이 끊긴 세션

Windows PowerShell 3.0 이상에서는 New-PSSession cmdlet을 사용하여 만든 지속성 사용자 관리 세션("PSSessions")이 원격 컴퓨터에 저장됩니다. 따라서 만들어진 세션에 더 이상 종속되지 않습니다.

이제 세션에서 실행 중인 명령을 중단하지 않고 세션 연결을 끊을 수 있습니다. 세션을 닫고 컴퓨터를 종료할 수 있습니다. 나중에 동일한 컴퓨터나 다른 컴퓨터의 다른 세션에서 세션에 다시 연결할 수 있습니다.

이제 다른 컴퓨터의 다른 세션에서 시작된 경우에도 `Get-PSSession` cmdlet의 **ComputerName** 매개 변수가 컴퓨터에 연결하는 모든 사용자 세션을 가져옵니다. 세션에 연결하고, 명령의 결과를 가져오고, 새 명령을 시작하고, 세션 연결을 끊을 수 있습니다.

연결이 끊긴 세션 기능을 지원하기 위해 새 cmdlet(`Disconnect-PSSession`, `Connect-PSSession` 및 `Receive-PSSession` 등)을 추가하였고, PSSessions을 관리하는 cmdlet에 새 매개 변수(예: `Invoke-Command` cmdlet의 **InDisconnectedSession** 매개 변수)를 추가하였습니다.

연결이 끊긴 세션 기능은 연결의 시작 끝("클라이언트")과 종료 끝("서버")의 컴퓨터에서 모두 Windows PowerShell 3.0을 실행하고 있는 경우에만 지원됩니다.

### <a name="robust-session-connectivity"></a>강력한 세션 연결

Windows PowerShell 3.0은 클라이언트와 서버 사이의 예기치 못한 연결 끊김을 감지하여 다시 연결하여 자동으로 다시 실행하려고 시도합니다. 할당된 시간 내에 클라이언트/서버 연결을 다시 설정할 수 없는 경우 사용자에게 알림 메시지를 표시하고 세션 연결을 끊습니다. 다시 연결하는 동안 Windows PowerShell에서 사용자에게 지속적으로 피드백을 제공합니다.

InvokeCommand를 사용하여 연결이 끊긴 세션을 시작한 경우 Windows PowerShell에서는 쉽게 다시 연결하여 다시 실행할 수 있도록 연결이 끊긴 세션에 대한 작업을 만듭니다.

이러한 기능은 더 안정적이고 복구 가능한 원격 환경을 제공하여 사용자가 워크플로와 같은 강력한 세션이 필요한 장기적으로 실행되는 작업을 수행할 수 있도록 지원합니다.

### <a name="updatable-help-system"></a>업데이트할 수 있는 도움말 시스템

이제 모듈에서 cmdlet에 대해 업데이트된 도움말 파일을 다운로드할 수 있습니다. `Update-Help` cmdlet은 최신 도움말 파일을 식별하여 인터넷에서 다운로드한 후 압축을 풀어 확인합니다. 그런 다음, 이 파일을 모듈의 해당 언어별 디렉터리에 설치합니다.

업데이트된 도움말 파일을 사용하려면 `Get-Help`를 입력합니다. Windows 또는 Windows PowerShell을 다시 시작하지 않아도 됩니다. $pshome 디렉터리의 모듈에 대한 도움말을 업데이트하려면 "관리자 권한으로 실행" 옵션을 사용하여 Windows PowerShell을 시작합니다.

인터넷에 연결할 수 없거나 방화벽 뒤에 있는 사용자를 지원하기 위해 새 `Save-Help` cmdlet은 도움말 파일을 파일 시스템 디렉터리(예: 파일 공유)에 다운로드합니다. 그러면 사용자는 `Update-Help` cmdlet을 사용하여 파일 공유에서 업데이트된 도움말 파일을 가져올 수 있습니다.

`Update-Help` cmdlet을 사용하여 지원되는 모든 UI 문화권의 모든 또는 특정 모듈에 대한 도움말 파일을 업데이트할 수 있습니다. `Update-Help` 명령을 Windows PowerShell 프로필에 넣을 수도 있습니다.
기본적으로 Windows PowerShell에서는 매일 두 번 이상 모듈에 대한 도움말 파일을 다운로드합니다.

Windows 8 및 Windows Server 2012 모듈에는 도움말 파일이 포함되어 있지 않습니다. 최신 도움말 파일을 다운로드하려면 `Update-Help`를 입력합니다. 자세한 내용을 보려면 `Get-Help`(매개 변수 제외)를 입력하거나 [about_Updatable_Help](/powershell/module/microsoft.powershell.core/about/about_Updatable_Help)를 참조하세요.

cmdlet에 대한 도움말 파일이 컴퓨터에 설치되어 있지 않은 경우 이제 `Get-Help` cmdlet은 자동 생성된 도움말을 표시합니다. 자동 생성된 도움말에는 `Update-Help` cmdlet을 사용하여 도움말 파일을 다운로드하기 위한 명령 구문과 지침이 포함되어 있습니다.

모든 모듈 작성자는 해당 모듈에 대해 업데이트할 수 있는 도움말을 지원할 수 있습니다. 모듈에 도움말 파일을 포함하고 업데이트할 수 있는 도움말을 사용하여 도움말을 업데이트하거나 도움말 파일을 생략하고 업데이트할 수 있는 도움말을 사용하여 도움말을 설치할 수 있습니다. 업데이트할 수 있는 도움말을 지원하는 방법에 대한 자세한 내용은 [업데이트 가능한 도움말 지원](/powershell/scripting/developer/module/supporting-updatable-help)을 참조하세요.

### <a name="enhanced-online-help"></a>향상된 온라인 도움말

Windows PowerShell 온라인 도움말은 모든 사용자에게 중요한 리소스이지만 업데이트된 도움말 파일을 설치하지 않았거나 설치할 수 없는 사용자에게 특히 중요합니다.

Windows PowerShell cmdlet에 대한 온라인 도움말을 가져오려면 다음과 같이 입력합니다.

```
Get-Help <cmdlet-name> -Online
```

Windows PowerShell에서는 도움말 항목의 온라인 버전을 기본 인터넷 브라우저에서 엽니다.

Windows PowerShell 3.0의 **Get-Help -Online** 기능은 이제 cmdlet에 대한 도움말 파일을 컴퓨터에 설치하지 않은 경우에도 작동하므로 훨씬 더 강력해졌습니다. **Get-Help -Online** 기능은 cmdlet의 HelpUri 속성 및 고급 기능에서 온라인 도움말 항목에 대한 URI를 가져옵니다.

```
PS C:\>(Get-Command Get-ScheduledJob).HelpUri
https://go.microsoft.com/fwlink/?LinkID=223923
```

Windows PowerShell 3.0 이상에서 C# cmdlet 작성자는 cmdlet 클래스에서 **HelpUri** 특성을 만들어서 **HelpUri** 속성을 채울 수 있습니다. 고급 기능의 작성자는 **CmdletBinding** 특성에서 **HelpUri** 속성을 정의할 수 있습니다. **HelpUri** 속성 값은 "http" 또는 "https"로 시작해야 합니다.

XML 기반 cmdlet 도움말 파일의 첫 번째 관련 링크 또는 함수의 명령 기반 도움말의 .Link 지시어에 **HelpUri** 값을 포함할 수도 있습니다.

온라인 도움말 지원에 대한 자세한 내용은 Microsoft Docs에서 [온라인 도움말 지원](/powershell/scripting/developer/module/supporting-online-help)을 참조하세요.

### <a name="cim-integration"></a>CIM 통합

Windows PowerShell 3.0에서는 이기종 시스템 간에 관리 정보를 교환할 수 있도록 시스템, 네트워크, 애플리케이션 및 서비스에 대한 관리 정보의 일반 정의를 제공하는 CIM(Common Information Model)을 지원합니다. Windows PowerShell 3.0에서는 새 CIM 클래스 또는 기존 CIM 클래스를 기반으로 Windows PowerShell cmdlet 작성, cmdlet 정의 XML 파일 기반 명령, CIM .NET Framework 지원을 비롯한 CIM을 지원합니다. API, CIM 관리 cmdlet 및 WMI 2.0 공급자.

### <a name="session-configuration-files"></a>세션 구성 파일

Windows PowerShell 3.0 이상에서는 파일을 사용하여 사용자 지정 세션 구성을 설계할 수 있습니다.
새 세션 구성 파일을 사용하여 세션 구성을 사용하는 세션 환경을 결정할 수 있습니다(예: 세션에 로드되는 모듈, 스크립트 및 서식 파일, 사용할 수 있는 cmdlet 및 언어 요소, 실행할 수 있는 모듈 및 스크립트, 표시할 수 있는 변수).

사용자가 특정 모듈에서만 cmdlet을 실행할 수 있는 세션을 설계하거나, 전체 언어를 사용하고 모든 모듈에 액세스하고 고급 작업을 수행하는 스크립트에 액세스할 수 있는 세션을 설계할 수 있습니다.

이전 버전의 Windows PowerShell에서는 C# 프로그램 또는 복잡한 시작 스크립트를 작성할 수 있는 사용자만 이 수준의 컨트롤을 사용할 수 있습니다. 이제 컴퓨터에서 Administrators 그룹의 모든 구성원은 구성 파일을 사용하여 세션 구성을 사용자 지정할 수 있습니다.

세션 구성 파일을 만들려면 `New-PSSessionConfigurationFile` cmdlet을 사용하세요. 세션 구성 파일을 세션 구성에 적용하려면 `Register-PSSessionConfiguration` 또는 Set-PSSessionConfiguration cmdlet을 사용합니다.

자세한 내용은 [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configuration_files) 및 `New-PSSessionConfigurationFile`을 참조하세요.

### <a name="scheduled-jobs-and-task-scheduler-integration"></a>예약된 작업 및 작업 스케줄러 통합

이제 Windows PowerShell 백그라운드 작업을 예약하고 Windows PowerShell 및 작업 스케줄러에서 해당 작업을 관리할 수 있습니다.

Windows PowerShell에서 예약된 작업은 Windows PowerShell 백그라운드 작업 및 작업 스케줄러 작업의 유용한 하이브리드입니다.

Windows PowerShell 백그라운드 작업과 마찬가지로 예약된 작업은 백그라운드에서 비동기적으로 실행됩니다.
완료한 예약된 작업 인스턴스는 작업 cmdlet(예: `Start-Job` 및 `Get-Job`)을 사용하여 관리할 수 있습니다.

작업 스케줄러 작업과 마찬가지로 일회성 또는 되풀이 일정을 따르거나 작업 또는 이벤트에 대한 응답으로 예약된 작업을 실행할 수 있습니다. 작업 스케줄러에서 예약된 작업을 표시 및 관리하고, 필요에 따라 예약된 작업을 사용 또는 사용하지 않도록 지정하고, 예약된 작업을 템플릿으로 실행하거나 사용하고, 작업이 시작되는 조건을 설정할 수 있습니다.

예약된 작업은 관리하는 데 필요한 사용자 지정된 cmdlet 집합과 함께 제공됩니다. cmdlet을 사용하여 예약된 작업을 작성, 편집 또는 관리하거나 사용하지 않도록 지정한 다음 다시 사용하도록 지정하고, 예약된 작업 트리거를 만들고, 예약된 작업 옵션을 설정할 수 있습니다.

예약된 작업에 대한 자세한 내용은 [about_Scheduled_Jobs](/powershell/module/psscheduledjob/about/about_scheduled_jobs?view=powershell-5.1)를 참조하세요.

### <a name="windows-powershell-language-enhancements"></a>Windows PowerShell 언어 향상

Windows PowerShell 3.0에는 언어를 간소하고 용이하며 일반 오류를 방지하도록 설계된 다양한 기능이 포함되어 있습니다. 향상된 기능으로는 property 열거형, 스칼라 개체에 대한 count 및 length 속성, 새로운 리디렉션 연산자, $Using 범위 한정자, PSItem 자동 변수, 유연한 스크립트 서식, 변수 특성, 간소화된 특성 인수, 숫자 명령 이름, Stop-Parsing 연산자, 향상된 배열 스플랫, 새로운 비트 연산자, 순서가 지정된 사전, PSCustomObject 캐스팅, 향상된 설명 기반 도움말 등이 있습니다.

### <a name="new-core-cmdlets"></a>새로운 핵심 Cmdlet

예약된 작업, 연결이 끊긴 세션, CIM 통합, 업데이트할 수 있는 도움말 시스템 등을 관리하는 cmdlet을 포함하여 새로운 cmdlet이 Windows PowerShell 핵심 설치에 추가되었습니다.

|                           |                                 |
| ------------------------- | ------------------------------- |
| Add-JobTrigger            | New-JobTrigger                  |
| Connect-PSSession         | New-PSSessionConfigurationFile  |
| ConvertFrom-Json          | New-PSTransportOption           |
| ConvertTo-Json            | New-PSWorkflowExecutionOption   |
| Disable-JobTrigger        | New-PSWorkflowSession           |
| Disable-ScheduledJob      | New-ScheduledJobOption          |
| Disconnect-PSSession      | New-WinEvent                    |
| Enable-JobTrigger         | Receive-PSSession               |
| Enable-ScheduledJob       | Register-CimIndicationEvent     |
| Get-CimAssociatedInstance | Register-ScheduledJob           |
| Get-CimClass              | Remove-CimInstance              |
| Get-CimInstance           | Remove-CimSession               |
| Get-CimSession            | Remove-TypeData                 |
| Get-ControlPanelItem      | Rename-Computer                 |
| Get-IseSnippet            | Resume-Job                      |
| Get-JobTrigger            | Save-Help                       |
| Get-ScheduledJob          | Set-CimInstance                 |
| Get-ScheduledJobOption    | Set-JobTrigger                  |
| Get-TypeData              | Set-ScheduledJob                |
| Import-IseSnippet         | Set-ScheduledJobOption          |
| Invoke-AsWorkflow         | Show-Command                    |
| Invoke-CimMethod          | Show-ControlPanelItem           |
| Invoke-RestMethod         | Suspend-Job                     |
| Invoke-WebRequest         | Test-PSSessionConfigurationFile |
| New-CimInstance           | Unblock-File                    |
| New-CimSession            | Unregister-ScheduledJob         |
| New-CimSessionOption      | Update-Help                     |
| New-IseSnippet            |                                 |

### <a name="improvements-to-existing-core-cmdlets-and-providers"></a>기존 핵심 Cmdlet 및 공급자에서 향상된 기능

Windows PowerShell 3.0에는 간소화된 구문을 포함하여 기존 cmdlet에 대한 새로운 기능 및 다음 cmdlet에 대한 새로운 매개 변수가 포함되어 있습니다. 컴퓨터 cmdlet, CSV cmdlet, Get-ChildItem, Get-Command, Get-Content, Get-History, Measure-Object, 보안 cmdlets, Select-Object, Select-String, Split-Path, Start-Process, Tee-Object, Test-Connection, Add-Member, WMI cmdlet.

Windows PowerShell 공급자가 크게 향상되었습니다. 예를 들어 인증서 공급자가 웹 호스팅을 위한 SSL(Secure Socket Layer) 인증서 관리를 지원하고, 파일 시스템 드라이브에서 자격 증명, 지속성 네트워크 드라이브, 대체 데이터 스트림 등을 지원합니다.

### <a name="remote-module-import-and-discovery"></a>원격 모듈 가져오기 및 검색

Windows PowerShell 3.0에서는 원격 컴퓨터에서 모듈 검색, 가져오기 및 암시적 원격 기능을 확장합니다. 모듈 cmdlet은 원격 컴퓨터에서 모듈을 가져오고 Windows PowerShell 원격 작업을 사용하여 모듈을 원격 컴퓨터 또는 로컬 컴퓨터로 가져옵니다. 새 CIM 세션을 지원하므로 CIM 및 WMI를 사용하여 원격 컴퓨터에서 암시적으로 실행되는 명령을 로컬 컴퓨터로 가져와서 비 Windows 컴퓨터를 관리할 수 있습니다.

자세한 내용은 `Get-Module` 및 `Import-Module` cmdlet에 대한 도움말 항목을 참조하세요.

### <a name="enhanced-tab-completion"></a>고급 탭 완성

Windows PowerShell 콘솔의 탭 완성 기능은 이제 cmdlet의 이름, 매개 변수, 매개 변수 값, 열거형, .NET Frameworks 유형, COM 개체, 숨김 디렉터리 등을 완성합니다.
메모리 내 구문 분석 트리, 중간선 탭 완성 등을 비롯한 더 많은 시나리오를 지원하도록 새로운 구문 분석기 및 추상 구문 트리를 기반으로 탭 완성 기능을 완전히 다시 작성했습니다.

### <a name="module-auto-loading"></a>모듈 자동 로드

이제 `Get-Command` cmdlet은 컴퓨터에 설치된 모든 모듈에서 모든 cmdlet 및 기능을 가져옵니다. 이는 모듈을 현재 세션으로 가져오지 않은 경우에도 마찬가지입니다.

필요한 cmdlet을 가져올 때 모듈을 가져오지 않고 해당 cmdlet을 즉시 사용할 수 있습니다.
이제 모듈에서 cmdlet을 사용할 때 Windows PowerShell 모듈을 자동으로 가져옵니다. 더 이상 cmdlet을 사용하기 위해 모듈을 검색하여 가져올 필요가 없습니다.

명령에서 cmdlet을 사용하거나, 와일드카드 없이 cmdlet에 대한 `Get-Command`를 실행하거나, 와일드카드 없이 cmdlet에 대한 `Get-Help`를 실행하여 모듈 자동 가져오기를 트리거합니다.

**$PSModuleAutoLoadingPreference** 기본 설정 변수를 사용하여 모듈 자동 가져오기를 사용하거나 사용하지 않도록 설정하고 구성할 수 있습니다.

자세한 내용은 [about_Modules](/powershell/module/microsoft.powershell.core/about/about_modules), [about_Preference_Variables](/powershell/module/microsoft.powershell.core/about/about_Preference_Variables), `Get-Command` 및 `Import-Module` cmdlet에 대한 도움말 항목을 참조하세요.

### <a name="module-experience-improvements"></a>모듈 환경 향상

Windows PowerShell 3.0에서는 다음과 같은 새로운 기능을 비롯하여 모듈에 대한 고급 기능을 지원합니다.

1. 개별 모듈에 대한 모듈 로깅(LogPipelineExecutionDetails) 및 새로운 "모듈 로깅 켜기" 그룹 정책 설정
2. 모듈 매니페스트에서 값을 노출하는 확장된 모듈 개체
3. 모든 유형의 명령을 결합하는 모듈의 새 **ExportedCommands** 속성(중첩된 모듈 포함)
4. 사용 가능한 가져오지 않은 모듈 검색 기능 향상(예: 동일한 명령에서 **Path** 및 **ListAvailable** 매개 변수 허용)
5. 모듈 코드를 변경하지 않고 이름 충돌을 방지하는 모듈 매니페스트의 새로운 **DefaultCommandPrefix** 키.
6. 향상된 모듈 요구 사항(예: 버전 및 GUID를 포함하는 정규화된 필수 모듈, 필수 모듈 자동으로 가져오기)
7. 더 조용해지고 간소화된 `New-ModuleManifest` cmdlet 작업.
8. &#35;Requires에 대한 새 **Module** 매개 변수
9. 향상된 `Import-Module` cmdlet(**MinimumVersion** 및 **RequiredVersion** 매개 변수와 함께 사용).

### <a name="simplified-command-discovery"></a>간소화된 명령 검색

세션에서 사용할 수 있는 명령을 검색하기 위해 더 이상 모든 모듈을 가져올 필요가 없습니다. Windows PowerShell 3.0에서 `Get-Command` cmdlet은 모든 설치된 모듈에서 모든 명령을 가져옵니다. 명령을 사용하는 경우 명령을 내보내는 모듈을 세션으로 자동으로 가져옵니다.

새 `Show-Command` cmdlet은 초보자를 위해 특별히 설계되었습니다. 창에서 명령을 검색할 수 있습니다. 모듈별로 모든 명령 또는 필터를 보고, 단추를 클릭하여 모듈을 가져오고, 텍스트 상자 및 드롭다운 목록을 사용하여 유효한 명령을 구성한 다음 창을 닫지 않고 명령을 복사하거나 실행할 수 있습니다.

### <a name="improved-logging-diagnostics-and-group-policy-support"></a>향상된 로깅, 진단 및 그룹 정책 지원

Windows PowerShell 3.0에서는 ETW(Event Tracing in Windows) 로그, 모듈의 편집 가능한 **LogPipelineExecutionDetails** 속성, "모듈 로깅 켜기" 그룹 정책 설정 등을 지원하여 명령과 모듈에 대한 로깅 및 추적 지원을 강화했습니다. 이제 로그 속성을 표시하여 로그 정보에서 매개 변수 값을 가져올 수 있습니다.

### <a name="formatting-and-output-improvements"></a>서식 지정 및 출력 향상

새 서식 및 출력 기능 향상으로 모든 Windows PowerShell 사용자의 효율성이 향상되었습니다. 향상된 기능으로는 모든 스트림의 출력 리디렉션, Format.ps1xml 파일을 사용하지 않고 형식을 동적으로 추가하는 향상된 Update-Type cmdlet, 사용자 지정 개체의 기본 서식 속성, **PSCustomObject** 형식, WMI 개체 및 이기종 개체에 대해 향상된 서식, 메서드 오버로드 지원 등이 있습니다.

### <a name="enhanced-console-host-experience"></a>향상된 콘솔 호스트 환경

Windows PowerShell 콘솔 호스트 프로그램의 Windows PowerShell 3.0에는 기본적으로 단일 스레드 아파트를 비롯한 새로운 기능이 포함되어 있습니다. 파일 탐색기의 새로운 "PowerShell에서 실행" 옵션을 사용하면 마우스 오른쪽 단추로 클릭하여 무제한 세션에서 스크립트를 실행할 수 있습니다. 새로운 콘솔 호스트 시작 로직은 Windows PowerShell을 더 빠르게 실행하고 새 글꼴을 사용하여 친숙한 콘솔 창 환경을 개인 설정할 수 있습니다.

### <a name="new-cmdlet-and-hosting-apis"></a>새 Cmdlet 및 호스팅 API

새 Cmdlet API 및 Hosting API는 공용 AST(고급 구문 트리) API와, 파이프라인 페이징, 중첩된 파이프라인, runspace 풀 탭 완성, Windows RT, 사용하지 않는 cmdlet 특성, FunctionInfo 개체의 Verb 및 Noun 속성 등을 위한 API를 포함합니다.

### <a name="performance-improvements"></a>성능 향상

Windows PowerShell은 새로운 언어 구문 분석기를 지원하여 성능이 크게 향상되었습니다. 이 언어 구문 분석기는 .NET Framework 4의 DLR(Dynamic Runtime Language)에 기반을 두어 구축되었고, 런타임 스크립트 컴파일, 엔진 가독성 향상, 네트워크 공유 검색 시 성능 향상을 위한 `Get-ChildItem` 알고리즘 변경 등의 이점도 함께 제공합니다.

### <a name="runas-and-shared-host-support"></a>RunAs 및 공유 호스트 지원

Windows PowerShell 3.0에서는 RunAs 및 공유 호스트 기능을 지원합니다.

세션 구성 사용자는 Windows PowerShell 워크플로용으로 설계된 *RunAs* 기능을 사용하여 공유 사용자 계정 사용 권한으로 실행되는 세션을 만들 수 있습니다. 그러면 낮은 권한의 사용자가 특정 명령과 스크립트를 관리자 권한으로 실행할 수 있으므로 관리자가 아닌 사용자를 Administrators 그룹에 추가할 필요가 없습니다.

**SharedHost** 기능을 사용하면 여러 컴퓨터에서 여러 명의 사용자가 워크플로 세션에 동시에 연결하여 워크플로의 진행률을 모니터링할 수 있습니다. 사용자가 한 컴퓨터에서 워크플로를 시작한 다음 원본 컴퓨터에서 세션 연결을 끊지 않고 다른 컴퓨터에서 워크플로 세션에 연결할 수 있습니다. 사용자는 동일한 권한으로 동일한 세션 구성을 사용하고 있어야 합니다. 자세한 내용은 Windows PowerShell 워크플로 시작에서 "Windows PowerShell 워크플로 실행"을 참조하세요.

### <a name="special-character-handling-improvements"></a>특수 문자 처리 기능 향상

특수 문자를 해석하고 올바르게 처리하도록 Windows PowerShell 3.0 기능을 향상하기 위해 경로에서 특수 문자를 처리하는 **LiteralPath** 매개 변수는 **Path** 매개 변수를 사용하는 거의 모든 cmdlet(새 `Update-Help` 및 `Save-Help` cmdlet 포함)에서 유효합니다. 또한 구문 분석기에는 파일 이름과 경로의 억음 악센트 문자(\`) 및 대괄호 처리 기능 향상을 위한 특수 논리가 포함되어 있습니다.

## <a name="see-also"></a>참고 항목

- [about_Windows_PowerShell_5.0](/previous-versions/powershell/module/microsoft.powershell.core/about/about_windows_powershell_5.0?view=powershell-5.0)
- [Windows PowerShell](https://go.microsoft.com/fwlink/?LinkID=107116)
