---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 02/07/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionoption?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionOption
ms.openlocfilehash: d07942797bad3666a263e017fa8372e672936041
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600851"
---
# New-PSSessionOption

## 개요
PSSession에 대한 고급 옵션을 포함하는 개체를 만듭니다.

## SYNTAX

```
New-PSSessionOption [-MaximumRedirection <Int32>] [-NoCompression] [-NoMachineProfile] [-Culture <CultureInfo>]
 [-UICulture <CultureInfo>] [-MaximumReceivedDataSizePerCommand <Int32>] [-MaximumReceivedObjectSize <Int32>]
 [-OutputBufferingMode <OutputBufferingMode>] [-MaxConnectionRetryCount <Int32>]
 [-ApplicationArguments <PSPrimitiveDictionary>] [-OpenTimeout <Int32>] [-CancelTimeout <Int32>]
 [-IdleTimeout <Int32>] [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <AuthenticationMechanism>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [-IncludePortInSPN] [<CommonParameters>]
```

## 설명

`New-PSSessionOption`Cmdlet은 사용자 관리 세션 (**PSSession**)에 대 한 고급 옵션을 포함 하는 개체를 만듭니다. ,, 등의 **PSSession** 을 만드는 Cmdlet의 **sessionoption** 매개 변수 값으로 개체를 사용할 수 있습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` .

매개 변수가 없는 경우는 `New-PSSessionOption` 모든 옵션에 대 한 기본값을 포함 하는 개체를 생성 합니다. 모든 속성을 편집할 수 있으므로 결과 개체를 템플릿으로 사용하고 엔터프라이즈에 대한 표준 옵션 개체를 만들 수 있습니다.

기본 설정 변수에 세션 옵션 개체를 저장할 수도 있습니다 `$PSSessionOption` . 이 변수 값은 세션 옵션에 대한 새 기본값을 설정합니다. 세션에 대해 설정된 세션 옵션이 없을 경우 적용되며 세션 구성에서 설정된 옵션보다 우선하지만 세션을 만드는 cmdlet에서 세션 옵션 또는 세션 옵션 개체를 지정하여 재정의할 수 있습니다. 기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

세션을 만드는 cmdlet에 세션 옵션 개체를 사용할 경우 세션 옵션 값이 $PSSessionOption 기본 설정 변수 및 세션 구성에 설정된 세션의 기본값보다 우선합니다. 그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다. 세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.

## 예제

### 예 1: 기본 세션 옵션 만들기

이 명령은 모든 기본값을 포함 하는 세션 옵션 개체를 만듭니다.

```powershell
New-PSSessionOption
```

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

### 예 2: 세션 옵션 개체를 사용 하 여 세션 구성

이 예제에서는 세션 옵션 개체를 사용하여 세션을 구성하는 방법을 보여 줍니다.

```powershell
$pso = New-PSSessionOption -Culture "fr-fr" -MaximumReceivedObjectSize 10MB
New-PSSession -ComputerName Server01 -SessionOption $pso
```

첫 번째 명령은 새 세션 옵션 개체를 만들어 변수의 값에 저장 합니다 `$pso` . 두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` Server01 원격 컴퓨터에서 세션을 만듭니다. 이 명령은 변수의 값에 있는 session 옵션 개체를 `$pso` 명령의 **sessionoption** 매개 변수 값으로 사용 합니다.

### 예 3: 대화형 세션 시작

이 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01 컴퓨터와의 대화형 세션을 시작 합니다.

```powershell
Enter-PSSession -ComputerName Server01 -SessionOption (New-PSSessionOption -NoEncryption -NoCompression)
```

**Sessionoption** 매개 변수 값은 `New-PSSessionOption` **Noencryption** 및 **noencryption** 매개 변수를 포함 하는 명령입니다.

명령은 `New-PSSessionOption` 명령 전에 실행 되도록 괄호로 묶습니다 `Enter-PSSession` .

### 예제 4: 세션 옵션 개체 수정

이 예에서는 세션 옵션 개체를 수정할 수 있음을 보여 줍니다. 모든 속성에 읽기/쓰기 값이 있습니다.

```powershell
$a = New-PSSessionOption
$a.OpenTimeout
```

```Output
Days              : 0
Hours             : 0
Minutes           : 3
Seconds           : 0
Milliseconds      : 0
Ticks             : 1800000000
TotalDays         : 0.00208333333333333
TotalHours        : 0.05
TotalMinutes      : 3
TotalSeconds      : 180
TotalMilliseconds : 180000
```

```powershell
$a.UICulture = (Get-UICulture)
$a.OpenTimeout = (New-Timespan -Minutes 4)
$a.MaximumConnectionRedirectionCount = 1
$a
```

```Output
MaximumConnectionRedirectionCount : 1
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : IEConfig
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
Culture                           :
UICulture                         : en-US
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         :
ApplicationArguments              :
OpenTimeout                       : 00:04:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : 00:04:00
```

이 메서드를 사용하여 엔터프라이즈에 대한 표준 세션 개체를 만든 다음 특정 사용을 위해 이 개체의 사용자 지정 버전을 만들 수 있습니다.

### 예 5: 기본 설정 변수 만들기

이 명령은 `$PSSessionOption` 기본 설정 변수를 만듭니다.

```powershell
$PSSessionOption = New-PSSessionOption -OpenTimeOut 120000
```

`$PSSessionOption`기본 설정 변수는 세션에서 발생 하는 경우, 및 cmdlet을 사용 하 여 생성 된 세션의 옵션에 대 한 기본값을 설정 `New-PSSession` `Enter-PSSession` `Invoke-Command` 합니다.

`$PSSessionOption`모든 세션에서 변수를 사용할 수 있도록 하려면 powershell 세션 및 powershell 프로필에 추가 합니다.

기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.
프로필에 대한 자세한 내용은 [about_Profiles](About/about_Profiles.md)를 참조하세요.

### 예 6: 원격 세션 구성에 대 한 요구 사항 충족

이 예제에서는 **SessionOption** 개체를 사용하여 원격 세션 구성에 대한 요구 사항을 수행하는 방법을 보여 줍니다.

```powershell
$skipCN = New-PSSessionOption -SkipCNCheck
New-PSSession -ComputerName 171.09.21.207 -UseSSL -Credential Domain01\User01 -SessionOption $SkipCN
```

첫 번째 명령은 cmdlet을 사용 하 여 `New-PSSessionOption` **Skipcncheck** 속성이 있는 세션 옵션 개체를 만듭니다. 이 명령은 결과 세션 개체를 변수에 저장 합니다 `$skipCN` .

두 번째 명령은 cmdlet을 사용 하 여 `New-PSSession` 원격 컴퓨터에서 새 세션을 만듭니다. `$skipCN`Check 변수는 **sessionoption** 매개 변수 값에 사용 됩니다.

컴퓨터는 IP 주소로 식별 되므로 **ComputerName** 매개 변수 값이 SSL(SECURE SOCKETS LAYER) (SSL)에 사용 되는 인증서의 일반 이름과 일치 하지 않습니다. 따라서 **SkipCNCheck** 옵션은 필수입니다.

### 예 7: 원격 세션에서 인수를 사용할 수 있도록 설정

이 예에서는 cmdlet의 **Applicationarguments** 매개 변수를 사용 하 여 `New-PSSessionOption` 원격 세션에서 추가 데이터를 사용할 수 있도록 하는 방법을 보여 줍니다.

```powershell
$team = @{Team="IT"; Use="Testing"}
$TeamOption = New-PSSessionOption -ApplicationArguments $team
$s = New-PSSession -ComputerName Server01 -SessionOption $TeamOption
Invoke-Command -Session $s {$PSSenderInfo.ApplicationArguments}
```

```Output
Name                 Value
----                 -----
Team                 IT
Use                  Testing
PSVersionTable       {CLRVersion, BuildVersion, PSVersion, WSManStackVersion...}
```

```powershell
Invoke-Command -Session $s {
  if ($PSSenderInfo.ApplicationArguments.Use -ne "Testing") {
    .\logFiles.ps1
  }
  else {
    "Just testing."
  }
}
```

```Output
Just testing.
```

첫 번째 명령은 **팀** 과 **사용** 이라는 두 개의 키가 있는 해시 테이블을 만듭니다. 이 명령은 해시 테이블을 변수에 저장 합니다 `$team` . 해시 테이블에 대한 자세한 내용은 [about_Hash_Tables](about/about_Hash_Tables.md)를 참조하세요.

그런 다음 `New-PSSessionOption` **applicationarguments** 매개 변수를 사용 하는 cmdlet은 변수에 저장 된 세션 옵션 개체를 만듭니다 `$team` . 에서는 `New-PSSessionOption` 세션 옵션 개체를 만들 때 **applicationarguments** 매개 변수 값의 해시 테이블을 기본 사전으로 자동 변환 하므로 데이터를 원격 세션으로 안정적으로 전송할 수 있습니다.

`New-PSSession`Cmdlet은 Server01 컴퓨터에서 세션을 시작 합니다. **Sessionoption** 매개 변수를 사용 하 여 변수에 옵션을 포함 `$teamOption` 합니다.

`Invoke-Command`이 cmdlet은 변수의 데이터를 `$team` 원격 세션의 명령에서 사용할 수 있다는 것을 보여 줍니다. 자동 변수의 **Applicationarguments** 속성에 데이터가 나타납니다 `$PSSenderInfo` .

마지막에는 `Invoke-Command` 데이터를 사용 하는 방법이 나와 있습니다.

## PARAMETERS

### -ApplicationArguments

원격 세션으로 전송되는 기본 사전을 지정합니다. 세션 구성의 시작 스크립트를 포함 하 여 원격 세션의 명령 및 스크립트는 자동 변수의 **Applicationarguments** 속성에서이 사전을 찾을 수 있습니다 `$PSSenderInfo` . 이 매개 변수를 사용하여 데이터를 원격 세션으로 보낼 수 있습니다.

자세한 내용은 [about_Hash_Tables](about/about_Hash_Tables.md), [about_Session_Configurations](About/about_Session_Configurations.md)및 [about_Automatic_Variables](about/about_Automatic_Variables.md)를 참조 하세요.

```yaml
Type: System.Management.Automation.PSPrimitiveDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CancelTimeout

PowerShell이 종료 되기 전에 취소 작업 (CTRL + C)이 완료 될 때까지 대기 하는 시간을 결정 합니다.
값을 밀리초 단위로 입력하세요.

기본값은 60000(1분)입니다. 값이 0이면 시간 제한이 없으며 명령이 무기한 계속됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: CancelTimeoutMSec

Required: False
Position: Named
Default value: 60000
Accept pipeline input: False
Accept wildcard characters: False
```

### -문화권

세션에 사용할 문화권을 지정합니다. `<languagecode2>-<country/regioncode2>`형식 (예:)의 문화권 이름 `ja-JP` , **cultureinfo** 개체가 포함 된 변수 또는 **cultureinfo** 개체를 가져오는 명령을 입력 합니다.

기본값은 이며 `$Null` 운영 체제에 설정 된 문화권이 세션에 사용 됩니다.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IdleTimeout

원격 컴퓨터가 로컬 컴퓨터의 통신을 받지 못하는 경우 세션이 열린 상태로 유지 되는 기간을 결정 합니다. 하트 비트 신호를 포함 합니다. 간격이 만료되면 세션이 닫힙니다.

유휴 시간 제한 값은 세션의 연결을 끊고 다시 연결 하려는 경우에 매우 중요 합니다. 세션이 시간 초과되지 않은 경우에만 다시 연결할 수 있습니다.

값을 밀리초 단위로 입력하세요. 최소값은 60000(1분)입니다. 최대값은 세션 구성의 **MaxIdleTimeoutms** 속성 값입니다. 기본값-1은 유휴 시간 제한 값을 설정 하지 않습니다.

세션은 세션 옵션에 설정 된 유휴 시간 제한 (있는 경우)을 사용 합니다. (-1)가 설정 되지 않은 경우 세션은 세션 구성의 **IdleTimeoutMs** 속성 값 이나 WSMan 셸 시간 제한 값 ( `WSMan:\<ComputerName>\Shell\IdleTimeout` ) 중에서 가장 짧은 값을 사용 합니다.

세션 옵션에서 설정된 유휴 시간 제한이 세션 구성의 **MaxIdleTimeoutMs** 속성 값을 초과할 경우 세션을 만드는 명령이 실패합니다.

기본 **IdleTimeoutMs** 세션 구성의 값은 720만 밀리초 (2 시간) **입니다.** **MaxIdleTimeoutMs** 값은 2147483647 밀리초 ( \> 24 일)입니다. WSMan 셸 유휴 시간 제한 ()의 기본값은 `WSMan:\<ComputerName>\Shell\IdleTimeout` 720만 밀리초 (2 시간)입니다.

세션에서 연결을 끊거나 세션에 다시 연결할 때 세션의 유휴 시간 제한 값을 변경할 수도 있습니다. 자세한 내용은 `Disconnect-PSSession` 및 `Connect-PSSession`를 참조하세요.

Windows PowerShell 2.0에서 **IdleTimeout** 매개 변수의 기본값은 240000(4분)입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: IdleTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -IncludePortInSPN

Kerberos 인증에 사용 되는 SPN (서비스 사용자 이름)의 포트 번호를 포함 합니다 (예:) `HTTP://<ComputerName>:5985` . 이 옵션은 기본값이 아닌 SPN을 사용하는 클라이언트가 Kerberos 인증을 사용하는 원격 컴퓨터에 인증할 수 있도록 합니다.

Kerberos 인증을 지원하는 여러 서비스가 서로 다른 사용자 계정으로 실행되는 엔터프라이즈를 위한 옵션입니다. 예를 들어 Kerberos 인증을 허용 하는 IIS 응용 프로그램에서 컴퓨터 계정과 다른 사용자 계정에 기본 SPN을 등록 하도록 요구할 수 있습니다. 이러한 경우 PowerShell remoting은 컴퓨터 계정에 등록 된 SPN이 필요 하므로 Kerberos를 사용 하 여 인증할 수 없습니다. 이 문제를 해결 하기 위해 관리자는 다른 사용자 계정에 등록 된 **Setspn.exe** 를 사용 하는 등의 다양 한 spn을 만들 수 있으며 spn에 포트 번호를 포함 하 여 서로 구분할 수 있습니다.

자세한 내용은 [Setspn Overview](/previous-versions/windows/it-pro/windows-server-2003/cc773257(v=ws.10))를 참조 하십시오.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxConnectionRetryCount

네트워크 문제로 인해 현재 시도에 실패 하는 경우 PowerShell에서 대상 컴퓨터에 연결을 시도 하는 횟수를 지정 합니다. 기본값은 5입니다.

이 매개 변수는 PowerShell 버전 5.0에 추가 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedDataSizePerCommand

로컬 컴퓨터가 단일 명령으로 원격 컴퓨터에서 수신할 수 있는 최대 바이트 수를 지정합니다. 값을 바이트 단위로 입력합니다. 기본적으로 데이터 크기 제한은 없습니다.

이 옵션은 클라이언트 컴퓨터의 리소스를 보호하는 데 사용됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumReceivedObjectSize

로컬 컴퓨터가 원격 컴퓨터에서 수신할 수 있는 개체의 최대 크기를 지정합니다. 이 옵션은 클라이언트 컴퓨터의 리소스를 보호하는 데 사용됩니다. 값을 바이트 단위로 입력합니다.

Windows PowerShell 2.0에서 이 매개 변수를 생략하면 개체 크기 제한이 없습니다. Windows PowerShell 3.0부터 이 매개 변수를 생략할 경우 기본값은 200MB입니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 200 MB
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

연결에 실패 하기 전에 PowerShell에서 연결을 대체 URI (Uniform Resource Identifier)로 리디렉션하는 횟수를 결정 합니다. 기본값은 5입니다. 값 0은 모든 리디렉션을 차단합니다.

이 옵션은 세션을 만드는 명령에 **Allowredirection** 매개 변수가 사용 되는 경우에만 세션에서 사용 됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoCompression

세션에서 패킷 압축을 해제합니다. 압축하면 프로세서 주기가 더 많이 사용되지만 전송 속도가 빨라집니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoEncryption

데이터 암호화를 해제합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoMachineProfile

사용자의 Windows 사용자 프로필이 로드되지 않도록 합니다. 따라서 세션을 더 빨리 만들 수 있지만 사용자별 레지스트리 설정, 환경 변수와 같은 항목 및 인증서를 세션에서 사용할 수 없습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -OpenTimeout

클라이언트 컴퓨터가 세션 연결이 설정될 때까지 기다리는 기간을 결정합니다. 간격이 만료되면 연결 설정 명령이 실패합니다. 값을 밀리초 단위로 입력하세요.

기본값은 180000(3분)입니다. 값이 0이면 시간 제한이 없으며 명령이 무기한 계속됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OpenTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OperationTimeout

세션의 작업이 실행될 수 있는 최대 시간을 결정합니다. 간격이 만료되면 작업이 실패합니다. 값을 밀리초 단위로 입력하세요.

기본값은 180000(3분)입니다. 값이 0이면 시간 제한이 없으며 작업이 무기한 계속됩니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: 180000 (3 minutes)
Accept pipeline input: False
Accept wildcard characters: False
```

### -OutputBufferingMode

출력 버퍼가 가득 찰 경우 연결이 끊긴 세션에서 명령 출력을 관리하는 방법을 결정합니다.

출력 버퍼링 모드가 세션 또는 세션 구성에서 설정되지 않은 경우 기본값은 **Block** 입니다. 사용자가 세션에서 연결을 끊을 때 출력 버퍼링 모드를 변경할 수도 있습니다.

이 매개 변수를 생략 하는 경우 세션 옵션 개체의 **OutputBufferingMode** 값은 None입니다. **Block** 또는 **Drop** 값은 세션 구성에서 설정된 출력 버퍼링 모드 전송 옵션을 재정의합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 차단. 출력 버퍼가 가득 찰 경우 버퍼를 지울 때까지 실행이 일시 중단됩니다.
- Drop. 출력 버퍼가 가득 차도 실행이 계속됩니다. 새 출력이 저장되면 가장 오래된 출력을 버립니다.
- 없음 출력 버퍼링 모드를 지정하지 않습니다.

출력 버퍼링 모드 전송 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSTransportOption` .

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.Runspaces.OutputBufferingMode
Parameter Sets: (All)
Aliases:
Accepted values: None, Drop, Block

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -System.management.automation.remoting.proxyaccesstype

호스트 이름을 확인하는 데 사용되는 메커니즘을 결정합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- IEConfig
- WinHttpConfig
- 자동 검색
- NoProxyServer
- 없음

기본값은 None입니다.

이 매개 변수 값에 대 한 자세한 내용은 [System.management.automation.remoting.proxyaccesstype 열거형](/dotnet/api/system.management.automation.remoting.proxyaccesstype)을 참조 하세요.

```yaml
Type: System.Management.Automation.Remoting.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: None, IEConfig, WinHttpConfig, AutoDetect, NoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication

프록시 확인에 사용되는 인증 방법을 지정합니다. 이 매개 변수에 허용 되는 값은 **Basic**, **Digest** 및 **Negotiate** 입니다. 기본값은 **Negotiate** 입니다.

이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)를 참조 하세요.

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Negotiate
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

프록시 인증에 사용할 자격 증명을 지정합니다. **Pscredential** 개체를 포함 하는 변수 또는 **pscredential** 개체를 가져오는 명령 (예: 명령)을 입력 `Get-Credential` 합니다. 이 옵션을 설정하지 않으면 자격 증명이 지정되지 않습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck

HTTPS를 통해 연결할 때 클라이언트가 서버 인증서가 신뢰할 수 있는 CA (인증 기관)에 의해 서명 되었는지 확인 하지 않도록 지정 합니다.

이 옵션은 원격 컴퓨터가 물리적으로 안전하고 격리된 네트워크에 속해 있거나 원격 컴퓨터가 WinRM 구성에 신뢰할 수 있는 호스트로 나열되어 있는 경우와 같이 원격 컴퓨터를 다른 메커니즘으로 신뢰할 수 있는 경우에만 사용합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCNCheck

서버의 인증서 CN (일반 이름)이 서버의 호스트 이름과 일치할 필요가 없도록 지정 합니다. 이 옵션은 HTTPS 프로토콜을 사용하는 원격 작업에서만 사용됩니다.

신뢰할 수 있는 컴퓨터에 대해서만 이 옵션을 사용합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipRevocationCheck

서버 인증서의 해지 상태를 확인하지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -UICulture

세션에 사용할 UI 문화권을 지정합니다.

유효한 값은 다음과 같습니다.

- 형식의 문화권 이름 `<languagecode2>-<country/regioncode2>` (예:) `ja-JP`
- **CultureInfo** 개체를 포함 하는 변수입니다.
- **CultureInfo** 개체를 가져오는 명령 (예:)`Get-Culture`

기본값은 이며 `$null` , 세션을 만들 때 운영 체제에서 설정한 UI 문화권이 세션에 사용 됩니다.

```yaml
Type: System.Globalization.CultureInfo
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseUTF16

이 cmdlet은 UTF8 형식 대신 UTF16 형식으로 요청을 인코드 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### System.object.. a p.

## 참고

명령에서 **Sessionoption** 매개 변수를 사용 하 여 **PSSession** 을 만드는 경우 세션 옵션은 기본 설정 변수의 속성 값에 의해 결정 됩니다 `$PSSessionOption` (설정 된 경우). 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.

세션 구성 개체의 속성은 세션 구성에 대해 설정된 옵션과 해당 옵션 값에 따라 달라집니다. 또한 세션 구성 파일을 사용하는 세션 구성에는 추가 속성이 있습니다.

## 관련 링크

[Enter-PSSession](Enter-PSSession.md)

[Invoke-Command](Invoke-Command.md)

[New-PSSession](New-PSSession.md)
