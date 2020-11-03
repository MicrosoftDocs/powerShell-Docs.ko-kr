---
description: PowerShell에서 스크립트를 실행 하 고 작성 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scripts
ms.openlocfilehash: f91319db98ac3108f3a780814a0e80bdf5bc6f4c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223258"
---
# <a name="about-scripts"></a>스크립트 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 스크립트를 실행 하 고 작성 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

스크립트는 하나 이상의 PowerShell 명령을 포함 하는 일반 텍스트 파일입니다.
PowerShell 스크립트에는 `.ps1` 파일 확장명이 있습니다.

스크립트를 실행 하는 것은 cmdlet 실행과 매우 비슷합니다. 스크립트의 경로와 파일 이름을 입력 하 고 매개 변수를 사용 하 여 데이터를 전송 하 고 옵션을 설정 합니다. 컴퓨터 또는 다른 컴퓨터의 원격 세션에서 스크립트를 실행할 수 있습니다.

스크립트를 작성 하면 나중에 사용할 수 있도록 명령을 저장 하 고 다른 사용자와 쉽게 공유할 수 있습니다. 가장 중요 한 점은 스크립트 경로와 파일 이름을 입력 하 여 명령을 실행할 수 있다는 것입니다. 스크립트는 파일의 단일 명령 처럼 간단할 수도 있고 복잡 한 프로그램의 경우에만 사용할 수도 있습니다.

스크립트에는 `#Requires` 특수 주석, 매개 변수 사용, 데이터 섹션 지원, 보안을 위한 디지털 서명 등의 추가 기능이 있습니다.
스크립트 및 스크립트의 함수에 대 한 도움말 항목을 작성할 수도 있습니다.

## <a name="how-to-run-a-script"></a>스크립트를 실행 하는 방법

Windows에서 스크립트를 실행 하려면 먼저 기본 PowerShell 실행 정책을 변경 해야 합니다. 실행 정책은 비 Windows 플랫폼에서 실행 되는 PowerShell에는 적용 되지 않습니다.

기본 실행 정책 인은 `Restricted` 로컬 컴퓨터에서 작성 하는 스크립트를 포함 하 여 모든 스크립트가 실행 되지 않도록 합니다. 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.

실행 정책은 레지스트리에 저장 되므로 각 컴퓨터에서 한 번만 변경 해야 합니다.

실행 정책을 변경 하려면 다음 절차를 따르십시오.

명령 프롬프트에 다음을 입력합니다.

```powershell
Set-ExecutionPolicy AllSigned
```

또는

```powershell
Set-ExecutionPolicy RemoteSigned
```

변경 내용은 즉시 적용 됩니다.

스크립트를 실행 하려면 스크립트 파일의 전체 이름 및 전체 경로를 입력 합니다.

예를 들어 C:\Scripts 디렉터리에서 Get-ServiceLog.ps1 스크립트를 실행 하려면 다음을 입력 합니다.

```powershell
C:\Scripts\Get-ServiceLog.ps1
```

현재 디렉터리에서 스크립트를 실행 하려면 현재 디렉터리에 대 한 경로를 입력 하거나, 점을 사용 하 여 현재 디렉터리를 표시 한 다음 경로 백슬래시 ()를 사용 `.\` 합니다.

예를 들어 로컬 디렉터리에서 ServicesLog.ps1 스크립트를 실행 하려면 다음을 입력 합니다.

```powershell
.\Get-ServiceLog.ps1
```

스크립트에 매개 변수가 있는 경우 스크립트 파일 이름 뒤에 매개 변수 및 매개 변수 값을 입력 합니다.

예를 들어 다음 명령은 Get-ServiceLog 스크립트의 ServiceName 매개 변수를 사용 하 여 WinRM 서비스 활동의 로그를 요청 합니다.

```powershell
.\Get-ServiceLog.ps1 -ServiceName WinRM
```

보안 기능인 PowerShell은 파일 탐색기에서 스크립트 아이콘을 두 번 클릭 하거나 스크립트가 현재 디렉터리에 있는 경우에도 전체 경로 없이 스크립트 이름을 입력할 때 스크립트를 실행 하지 않습니다. PowerShell에서 명령 및 스크립트를 실행 하는 방법에 대 한 자세한 내용은 [about_Command_Precedence](about_Command_Precedence.md)를 참조 하세요.

### <a name="run-with-powershell"></a>PowerShell을 사용하여 실행

PowerShell 3.0부터 파일 탐색기에서 스크립트를 실행할 수 있습니다.

"PowerShell에서 실행" 기능을 사용 하려면 다음을 수행 합니다.

파일 탐색기를 실행 하 고 스크립트 파일 이름을 마우스 오른쪽 단추로 클릭 한 다음 "PowerShell에서 실행"을 선택 합니다.

"PowerShell에서 실행" 기능은 필수 매개 변수가 없는 스크립트를 실행 하 고 출력을 명령 프롬프트로 반환 하지 않도록 설계 되었습니다.

자세한 내용은 [about_Run_With_PowerShell](about_Run_With_PowerShell.md)을 참조하세요.

### <a name="running-scripts-on-other-computers"></a>다른 컴퓨터에서 스크립트 실행

하나 이상의 원격 컴퓨터에서 스크립트를 실행 하려면 cmdlet의 **FilePath** 매개 변수를 사용 합니다 `Invoke-Command` .

**FilePath** 매개 변수 값으로 스크립트의 경로와 파일 이름을 입력 합니다. 스크립트는 로컬 컴퓨터나 로컬 컴퓨터에서 액세스할 수 있는 디렉터리에 있어야 합니다.

다음 명령은 `Get-ServiceLog.ps1` Server01 및 Server02 라는 원격 컴퓨터에서 스크립트를 실행 합니다.

```powershell
Invoke-Command -ComputerName Server01,Server02 -FilePath `
  C:\Scripts\Get-ServiceLog.ps1
```

## <a name="get-help-for-scripts"></a>스크립트에 대 한 도움말 보기

Get-Help cmdlet은 스크립트와 cmdlet 및 다른 유형의 명령에 대 한 도움말 항목을 가져옵니다. 스크립트에 대 한 도움말 항목을 보려면를 입력 한 `Get-Help` 다음 스크립트의 경로와 파일 이름을 입력 합니다. 스크립트 경로가 `Path` 환경 변수에 있는 경우 경로를 생략할 수 있습니다.

예를 들어 ServicesLog.ps1 스크립트에 대 한 도움말을 보려면 다음을 입력 합니다.

```powershell
get-help C:\admin\scripts\ServicesLog.ps1
```

## <a name="how-to-write-a-script"></a>스크립트를 작성 하는 방법

스크립트에는 단일 명령, 파이프라인을 사용 하는 명령, 함수 및 If 문과 For 루프와 같은 제어 구조를 포함 하는 모든 유효한 PowerShell 명령이 포함 될 수 있습니다.

스크립트를 작성 하려면 텍스트 편집기에서 새 파일을 열고 명령을 입력 한 다음 파일 확장명이 올바른 파일 이름으로 파일에 저장 `.ps1` 합니다.

다음 예에서는 현재 시스템에서 실행 되는 서비스를 가져와서 로그 파일에 저장 하는 간단한 스크립트를 소개 합니다. 현재 날짜에서 로그 파일 이름을 만듭니다.

```powershell
$date = (get-date).dayofyear
get-service | out-file "$date.log"
```

이 스크립트를 만들려면 텍스트 편집기나 스크립트 편집기를 열고 다음 명령을 입력 한 다음 이라는 파일에 저장 `ServiceLog.ps1` 합니다.

### <a name="parameters-in-scripts"></a>스크립트의 매개 변수

스크립트에서 매개 변수를 정의 하려면 Param 문을 사용 합니다. `Param`문은 주석과 문을 제외 하 고 스크립트의 첫 번째 문 이어야 합니다 `#Require` .

스크립트 매개 변수는 함수 매개 변수 처럼 작동 합니다. 매개 변수 값은 스크립트의 모든 명령에 사용할 수 있습니다. 매개 변수 특성 및 명명 된 인수를 포함 하 여 함수 매개 변수의 모든 기능을 스크립트 에서도 사용할 수 있습니다.

스크립트를 실행할 때 스크립트 사용자는 스크립트 이름 뒤에 매개 변수를 입력 합니다.

다음 예에서는 `Test-Remote.ps1` **ComputerName** 매개 변수가 있는 스크립트를 보여 줍니다. 두 스크립트 함수는 모두 **ComputerName** 매개 변수 값에 액세스할 수 있습니다.

```powershell
param ($ComputerName = $(throw "ComputerName parameter is required."))

function CanPing {
   $error.clear()
   $tmp = test-connection $computername -erroraction SilentlyContinue

   if (!$?)
       {write-host "Ping failed: $ComputerName."; return $false}
   else
       {write-host "Ping succeeded: $ComputerName"; return $true}
}

function CanRemote {
    $s = new-pssession $computername -erroraction SilentlyContinue

    if ($s -is [System.Management.Automation.Runspaces.PSSession])
        {write-host "Remote test succeeded: $ComputerName."}
    else
        {write-host "Remote test failed: $ComputerName."}
}

if (CanPing $computername) {CanRemote $computername}
```

이 스크립트를 실행 하려면 스크립트 이름 뒤에 매개 변수 이름을 입력 합니다. 다음은 그 예입니다. 

```powershell
C:\PS> .\test-remote.ps1 -computername Server01

Ping succeeded: Server01
Remote test failed: Server01
```

Param 문과 함수 매개 변수에 대 한 자세한 내용은 [about_Functions](about_Functions.md) 및 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.

### <a name="writing-help-for-scripts"></a>스크립트에 대 한 도움말 작성

다음 두 가지 방법 중 하나를 사용 하 여 스크립트에 대 한 도움말 항목을 작성할 수 있습니다.

- 스크립트에 대 한 Comment-Based 도움말

  주석에 특수 키워드를 사용 하 여 도움말 항목을 만듭니다. 스크립트에 대 한 주석 기반 도움말을 만들려면 스크립트 파일의 시작 부분이 나 끝 부분에 주석을 배치 해야 합니다. 주석 기반 도움말에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요.

- 스크립트에 대 한 XML-Based 도움말

  일반적으로 cmdlet에 대해 생성 되는 형식과 같은 XML 기반 도움말 항목을 만듭니다. 도움말 항목을 여러 언어로 번역 하는 경우 XML 기반 도움말이 필요 합니다.

스크립트를 XML 기반 도움말 항목과 연결 하려면를 사용 합니다. ExternalHelp 도움말 주석 키워드입니다. ExternalHelp 키워드에 대 한 자세한 내용은 [about_Comment_Based_Help](about_Comment_Based_Help.md)를 참조 하세요. XML 기반 도움말에 대 한 자세한 내용은 [Cmdlet 도움말을 작성 하는 방법](/powershell/scripting/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조 하십시오.

### <a name="returning-an-exit-value"></a>종료 값 반환

기본적으로 스크립트는 스크립트가 종료 될 때 종료 상태를 반환 하지 않습니다. 문을 사용 하 여 `exit` 스크립트에서 종료 코드를 반환 해야 합니다. 기본적으로 문은를 `exit` 반환 `0` 합니다. 숫자 값을 제공 하 여 다른 종료 상태를 반환할 수 있습니다. 0이 아닌 종료 코드는 일반적으로 오류를 신호로 보냅니다.

Windows에서는와 사이의 숫자가 모두 `[int]::MinValue` `[int]::MaxValue` 허용 됩니다.


PowerShell에서 `exit` 문은 변수의 값을 설정 `$LASTEXITCODE` 합니다. Windows 명령 셸 (cmd.exe)에서 exit 문은 환경 변수의 값을 설정 합니다 `%ERRORLEVEL%` .

숫자가 아니거나 플랫폼별 범위를 벗어난 인수는의 값으로 변환 됩니다 `0` .

## <a name="script-scope-and-dot-sourcing"></a>스크립트 범위 및 점 소싱

각 스크립트는 자체 범위에서 실행 됩니다. 스크립트에 생성 된 함수, 변수, 별칭 및 드라이브는 스크립트 범위에만 존재 합니다. 이러한 항목이 나 스크립트를 실행 하는 범위에서 해당 값에 액세스할 수 없습니다.

다른 범위에서 스크립트를 실행 하려면 전역 또는 로컬과 같은 범위를 지정 하거나 스크립트를 원본으로 지정할 수 있습니다.

점 소싱 기능을 사용 하면 스크립트 범위 대신 현재 범위에서 스크립트를 실행할 수 있습니다. 점 소스인 스크립트를 실행 하는 경우 스크립트의 명령은 명령 프롬프트에서 입력 한 것 처럼 실행 됩니다. 스크립트에서 만드는 함수, 변수, 별칭 및 드라이브는 작업 하는 범위에 생성 됩니다. 스크립트를 실행 한 후에는 생성 된 항목을 사용 하 여 세션에서 해당 값에 액세스할 수 있습니다.

스크립트를 원본으로 만들려면 스크립트 경로 앞에 점 (.)과 공백을 입력 합니다.

다음은 그 예입니다.

```powershell
. C:\scripts\UtilityFunctions.ps1
```

또는

```powershell
. .\UtilityFunctions.ps1
```

스크립트가 실행 된 후에는 `UtilityFunctions.ps1` 스크립트에서 만드는 함수와 변수가 현재 범위에 추가 됩니다.

예를 들어 `UtilityFunctions.ps1` 스크립트는 `New-Profile` 함수와 변수를 만듭니다 `$ProfileName` .

```powershell
#In UtilityFunctions.ps1

function New-Profile
{
  Write-Host "Running New-Profile function"
  $profileName = split-path $profile -leaf

  if (test-path $profile)
    {write-error "Profile $profileName already exists on this computer."}
  else
    {new-item -type file -path $profile -force }
}
```

스크립트를 `UtilityFunctions.ps1` 자체 스크립트 범위에서 실행 하는 경우 스크립트를 `New-Profile` `$ProfileName` 실행 하는 동안에만 함수와 변수가 존재 합니다. 스크립트가 종료 되 면 다음 예제와 같이 함수와 변수가 제거 됩니다.

```powershell
C:\PS> .\UtilityFunctions.ps1

C:\PS> New-Profile
The term 'new-profile' is not recognized as a cmdlet, function, operable
program, or script file. Verify the term and try again.
At line:1 char:12
+ new-profile <<<<
   + CategoryInfo          : ObjectNotFound: (new-profile:String) [],
   + FullyQualifiedErrorId : CommandNotFoundException

C:\PS> $profileName
C:\PS>
```

스크립트의 소스를 표시 하 고 실행 하면 스크립트는 `New-Profile` 범위에서 함수 및 변수를 `$ProfileName` 세션에 만듭니다. 스크립트를 실행 한 후에는 `New-Profile` 다음 예제와 같이 세션에서 함수를 사용할 수 있습니다.

```powershell
C:\PS> . .\UtilityFunctions.ps1

C:\PS> New-Profile

    Directory: C:\Users\juneb\Documents\WindowsPowerShell

    Mode    LastWriteTime     Length Name
    ----    -------------     ------ ----
    -a---   1/14/2009 3:08 PM      0 Microsoft.PowerShellISE_profile.ps1

C:\PS> $profileName
Microsoft.PowerShellISE_profile.ps1
```

범위에 대 한 자세한 내용은 about_Scopes를 참조 하세요.

## <a name="scripts-in-modules"></a>모듈의 스크립트

모듈은 하나의 단위로 배포할 수 있는 관련 된 PowerShell 리소스 집합입니다. 모듈을 사용 하 여 스크립트, 함수 및 기타 리소스를 구성할 수 있습니다. 모듈을 사용 하 여 코드를 다른 사람에 게 배포 하 고 신뢰할 수 있는 소스에서 코드를 가져올 수도 있습니다.

스크립트를 모듈에 포함 하거나 스크립트와 지원 리소스를 완전히 또는 주로 구성 하는 모듈인 스크립트 모듈을 만들 수 있습니다. 스크립트 모듈은 .psm1 파일 확장명을 사용 하는 스크립트 일 뿐입니다.

모듈에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.

## <a name="other-script-features"></a>기타 스크립트 기능

PowerShell에는 스크립트에서 사용할 수 있는 많은 유용한 기능이 있습니다.

- `#Requires` -문을 사용 하 여 `#Requires` 지정 된 모듈 또는 스냅인과 지정 된 버전의 PowerShell 없이 스크립트가 실행 되지 않도록 할 수 있습니다. 자세한 내용은 about_Requires를 참조 하세요.

- `$PSCommandPath` -실행 중인 스크립트의 전체 경로와 이름을 포함 합니다. 이 매개 변수는 모든 스크립트에서 유효 합니다. 이 자동 변수는 PowerShell 3.0에서 도입 되었습니다.

- `$PSScriptRoot` -스크립트가 실행 되는 디렉터리를 포함 합니다. PowerShell 2.0에서이 변수는 스크립트 모듈 () 에서만 사용할 수 `.psm1` 있습니다.
  PowerShell 3.0부터 모든 스크립트에서 유효 합니다.

- `$MyInvocation` - `$MyInvocation` 자동 변수는 현재 스크립트에 대 한 정보를 포함 하 여 시작 또는 "호출"에 대 한 정보를 포함 합니다. 이 변수와 해당 속성을 사용 하 여 스크립트를 실행 하는 동안 스크립트에 대 한 정보를 가져올 수 있습니다. 예를 들면 `$MyInvocation` 입니다. MyCommand. Path 변수는 스크립트의 경로와 파일 이름을 포함 합니다. `$MyInvocation`. 줄에는 모든 매개 변수 및 값을 포함 하 여 스크립트를 시작 하는 명령이 포함 되어 있습니다.

  PowerShell 3.0부터에는 `$MyInvocation` 현재 스크립트를 호출 하거나 호출 하는 스크립트에 대 한 정보를 제공 하는 두 개의 새 속성이 있습니다. 이러한 속성의 값은 호출자 또는 호출자가 스크립트인 경우에만 채워집니다.

  - **Pscommandpath** 에는 현재 스크립트를 호출 하거나 호출한 스크립트의 전체 경로 및 이름이 포함 됩니다.

  - **Psscriptroot** 에는 현재 스크립트를 호출 하거나 호출한 스크립트의 디렉터리가 포함 되어 있습니다.

  `$PSCommandPath` `$PSScriptRoot` 현재 스크립트에 대 한 정보를 포함 하는 및 자동 변수와 달리, **pscommandpath** 및 해당 변수의 **pscommandpath** 속성은 `$MyInvocation` 현재 스크립트를 호출한 스크립트에 대 한 정보를 포함 합니다.

- 데이터 섹션-키워드를 사용 `Data` 하 여 스크립트의 논리에서 데이터를 구분할 수 있습니다. 데이터 섹션도 지역화를 용이 하 게 만들 수 있습니다. 자세한 내용은 [about_Data_Sections](about_Data_Sections.md) 및 [about_Script_Internationalization](about_Script_Internationalization.md)를 참조 하세요.

- 스크립트 서명-스크립트에 디지털 서명을 추가할 수 있습니다. 실행 정책에 따라 디지털 서명을 사용 하 여 안전 하지 않은 명령을 포함할 수 있는 스크립트 실행을 제한할 수 있습니다. 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md) 및 [about_Signing](about_Signing.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Command_Precedence](about_Command_Precedence.md)

[about_Comment_Based_Help](about_Comment_Based_Help.md)

[about_Execution_Policies](about_Execution_Policies.md)

[about_Functions](about_Functions.md)

[about_Modules](about_Modules.md)

[about_Profiles](about_Profiles.md)

[about_Requires](about_Requires.md)

[about_Run_With_PowerShell](about_Run_With_PowerShell.md)

[about_Scopes](about_Scopes.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Signing](about_Signing.md)

[Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command)
