---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212058"
---
# Export-Console

## 개요
현재 세션의 스냅인 이름을 콘솔 파일로 내보냅니다.

## SYNTAX

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명
**Export-Console** cmdlet은 현재 세션의 windows powershell 스냅인 이름을 windows powershell 콘솔 파일 (. .psc1)로 내보냅니다.
이 cmdlet을 사용하여 이후의 세션에서 사용하기 위해 스냅인을 저장할 수 있습니다.

.Psc1 콘솔 파일의 스냅인을 세션에 추가 하려면 Cmd.exe 또는 다른 Windows PowerShell 세션을 사용 하 여 명령줄에서 Windows PowerShell (Powershell.exe)을 시작한 다음 Powershell.exe의 *PSConsoleFile* 매개 변수를 사용 하 여 콘솔 파일을 지정 합니다.

Windows PowerShell 스냅인에 대한 자세한 내용은 about_PSSnapins를 참조하세요.

## 예제

### 예 1: 현재 세션에서 스냅인의 이름 내보내기

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 Windows PowerShell 설치 폴더의 ConsoleS1 폴더에 있는 .psc1 파일로 내보냅니다 $pshome 합니다.

### 예 2: 스냅인의 이름을 가장 최근의 콘솔 파일로 내보내기

```
PS C:\> Export-Console
```

이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 현재 세션에서 가장 최근에 사용된 Windows PowerShell 콘솔 파일로 내보냅니다.
또한 이전 파일 내용을 덮어씁니다.

현재 세션 중에 콘솔 파일을 내보내지 않은 경우 작업을 계속할 권한과 파일 이름을 확인하는 메시지가 차례로 표시됩니다.

### 예제 3: 스냅인 추가 및 스냅인 이름 내보내기

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

이 명령은 NewPSSnapin Windows PowerShell 스냅인을 현재 세션에 추가하고 현재 세션의 Windows PowerShell 스냅인 이름을 콘솔 파일로 내보낸 다음 이 파일을 사용하여 Windows PowerShell 세션을 시작합니다.

첫 번째 명령은 **add-pssnapin** cmdlet을 사용 하 여 NewPSSnapin 스냅인을 현재 세션에 추가 합니다.
해당 시스템에 등록된 Windows PowerShell 스냅인만 추가할 수 있습니다.

두 번째 명령은 Windows PowerShell 스냅인 이름을 NewPSSnapinConsole.psc1 파일로 내보냅니다.

세 번째 명령은 NewPSSnapinConsole.psc1 파일을 사용하여 Windows PowerShell을 시작합니다.
콘솔 파일에 Windows PowerShell 스냅인 이름이 포함되기 때문에 현재 세션에서 스냅인의 공급자 및 cmdlet을 사용할 수 있습니다.

### 예제 4: 지정 된 위치로 스냅인 이름 내보내기

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

이 명령은 현재 세션의 Windows PowerShell 스냅인 이름을 현재 디렉터리의 Console01.psc1 파일로 내보냅니다.

두 번째 명령은 Console01.psc1 파일의 내용을 메모장에 표시합니다.

### 예 5: 업데이트할 콘솔 파일 결정

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

이 예제에서는 $ConsoleFileName 자동 변수를 사용 하 여 *Path* 매개 변수 값 없이 **Export-console** 을 사용 하는 경우 업데이트 되는 콘솔 파일을 확인 하는 방법을 보여 줍니다.

첫 번째 명령은 PowerShell.exe의 *PSConsoleFile* 매개 변수를 사용 하 여 console01.psc1 .psc1 파일을 사용 하 여 Windows PowerShell을 엽니다.

두 번째 명령은 **add-pssnapin** cmdlet을 사용 하 여 MySnapin Windows PowerShell 스냅인을 현재 세션에 추가 합니다.

세 번째 명령은 **export-Console** cmdlet을 사용 하 여 세션에 있는 모든 Windows PowerShell 스냅인의 이름을 newconsole 파일로 내보냅니다.

네 번째 명령은 $ConsoleFileName 변수를 표시 합니다.
가장 최근에 사용 된 콘솔 파일을 포함 합니다.
샘플 출력에는 NewConsole.ps1이 가장 최근에 사용된 파일로 표시됩니다.

다섯 번째 명령은 SnapIn03을 현재 콘솔에 추가합니다.

여섯 번째 명령은 *Path* 매개 변수 없이 **Export-Console** cmdlet을 사용 합니다.
이 명령은 현재 세션의 모든 Windows PowerShell 스냅인 이름을 가장 최근에 사용된 파일인 NewConsole.psc1로 내보냅니다.

## PARAMETERS

### -Force
파일에 읽기 전용 특성이 있는 경우에도이 cmdlet이 경고 없이 콘솔 파일의 데이터를 덮어쓰도록 지정 합니다.
명령이 완료 되 면 읽기 전용 특성이 변경 되 고 다시 설정 되지 않습니다.

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

### -NoClobber
이 cmdlet이 기존 콘솔 파일을 덮어쓰지 않음을 나타냅니다.
기본적으로 지정 된 경로에서 파일이 발생 하면 **내보내기 콘솔** 은 경고 없이 파일을 덮어씁니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
콘솔 파일(*.psc1)의 경로 및 파일 이름을 지정합니다.
선택적 경로 및 이름을 입력 합니다.
와일드카드 문자는 사용할 수 없습니다.

파일 이름만 지정 하는 경우에는 **Export-Console** 에서 해당 이름과 .psc1 파일 이름 확장명을 가진 파일을 현재 디렉터리에 만듭니다.

이 매개 변수는 *PSConsoleFile* 매개 변수를 사용 하 여 Windows PowerShell을 열었거나 현재 세션 중에 콘솔 파일을 내보내지 않은 경우에 필요 합니다.
*NoClobber* 매개 변수를 사용 하 여 현재 콘솔 파일을 덮어쓰지 않도록 하는 경우에도이 매개 변수를 사용 해야 합니다.

이 매개 변수를 생략 하면 **내보내기 콘솔이** 이 세션에서 가장 최근에 사용 된 콘솔 파일을 덮어씁니다.
가장 최근에 사용 된 콘솔 파일의 경로는 $ConsoleFileName 자동 변수 값에 저장 됩니다.
자세한 내용은 about_Automatic_Variables를 참조하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm
cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String
이 cmdlet에 경로 문자열을 파이프 하 여 지정할 수 있습니다.

## 출력

### System.object
이 cmdlet은 내보낸 별칭을 포함 하는 파일을 만듭니다.

## 참고

* 콘솔 파일(.psc1)을 사용하여 세션을 시작하는 경우 콘솔 파일의 이름이 $ConsoleFileName 자동 변수에 자동으로 저장됩니다. **내보내기-콘솔** 의 *Path* 매개 변수를 사용 하 여 새 콘솔 파일을 지정할 때 $ConsoleFileName의 값이 업데이트 됩니다. 콘솔 파일을 사용 하지 않으면 $ConsoleFileName에 값 ($Null)이 없습니다.

  Windows PowerShell 콘솔 파일을 새 세션에서 사용하려면 다음 구문을 사용하여 Windows PowerShell을 시작하세요.

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  Add-PSSnapin 명령을 Windows PowerShell 프로필에 추가하여 이후 세션을 위해 Windows PowerShell 스냅인을 저장할 수도 있습니다.
자세한 내용은 about_Profiles를 참조하세요.


## 관련 링크

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
