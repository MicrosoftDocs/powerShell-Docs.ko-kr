---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ItemProperty
ms.openlocfilehash: b2c5b8596da085fab3af7a1545569dd65931a5f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215418"
---
# Get-ItemProperty

## 개요
지정된 항목의 속성을 가져옵니다.

## SYNTAX

### Path (기본값)

```
Get-ItemProperty [-Path] <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Get-ItemProperty -LiteralPath <String[]> [[-Name] <String[]>] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-UseTransaction] [<CommonParameters>]
```

## 설명

`Get-ItemProperty`Cmdlet은 지정 된 항목의 속성을 가져옵니다.
예를 들어이 cmdlet을 사용 하 여 파일 개체의 LastAccessTime 속성 값을 가져올 수 있습니다.
이 cmdlet을 사용 하 여 레지스트리 항목 및 해당 값을 볼 수도 있습니다.

## 예제

### 예 1: 특정 디렉터리에 대 한 정보 가져오기

이 명령은 "C:\Windows" 디렉터리에 대 한 정보를 가져옵니다.

```powershell
Get-ItemProperty C:\Windows
```

### 예 2: 특정 파일의 속성 가져오기

이 명령은 "C:\Test\Weather.xls" 파일의 속성을 가져옵니다.
결과를 cmdlet으로 파이프 하 여 `Format-List` 출력을 목록으로 표시 합니다.

```powershell
Get-ItemProperty C:\Test\Weather.xls | Format-List
```

### 예제 3: 레지스트리 하위 키에 레지스트리 항목의 값 이름 및 데이터 표시

이 명령은 "CurrentVersion" 레지스트리 하위 키에 포함 된 각 레지스트리 항목의 값 이름과 데이터를 표시 합니다.
명령에는 `HKLM:` 레지스트리의 "HKEY_LOCAL_MACHINE" 하이브에 매핑되는 라는 PowerShell 드라이브가 있어야 합니다.
기본적으로 PowerShell에서 해당 이름과 매핑을 가진 드라이브를 사용할 수 있습니다.
또는 공급자 이름으로 시작되고 그 뒤에 두 개의 콜론이 오는 대체

"Registry:: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion"입니다.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

### 예제 4: 레지스트리 하위 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기

이 명령은 "CurrentVersion" 레지스트리 하위 키에 있는 "ProgramFilesDir" 레지스트리 항목의 값 이름과 데이터를 가져옵니다.
이 명령은 **Path** 매개 변수를 사용 하 여 하위 키를 지정 하 고 name 매개 변수를 사용 하 여 항목의 값 이름을 지정 합니다.

이 명령은 뒤로 틱 또는 억음 악센트 기호 ()를 사용 하 여 \` 두 번째 줄에서 명령을 계속 합니다.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name "ProgramFilesDir"
```

### 예 5: 레지스트리 키에서 레지스트리 항목의 값 이름 및 데이터 가져오기

이 명령은 "PowerShellEngine" 레지스트리 키에 있는 레지스트리 항목의 값 이름과 데이터를 가져옵니다.
결과는 다음과 같은 샘플 출력에 표시됩니다.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\PowerShellEngine
```

```output
ApplicationBase         : C:\Windows\system32\WindowsPowerShell\v1.0\
ConsoleHostAssemblyName : Microsoft.PowerShell.ConsoleHost, Version=1.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, ProcessorArchitecture=msil
PowerShellVersion       : 2.0
RuntimeVersion          : v2.0.50727
CTPVersion              : 5
PSCompatibleVersion     : 1.0,2.0
```

### 예제 6: 레지스트리 값 및 데이터의 결과 가져오기, 서식 지정 및 표시

이 예제에서는 `Get-ItemProperty` 레지스트리 값 및 데이터를 쉽게 확인 하 고 결과를 쉽게 해석할 수 있도록 목록에서 명령의 출력에 서식을 지정 하는 방법을 보여 줍니다.

첫 번째 명령은 cmdlet을 사용 하 여 `Get-ItemProperty` **Microsoft PowerShell** 하위 키에 있는 레지스트리 항목을 가져옵니다.
이 하위 키는 PowerShell의 기본 셸에 대 한 옵션을 저장 합니다.
결과는 다음과 같은 샘플 출력에 표시됩니다.

출력은 "Path" 및 "Set-executionpolicy" 라는 두 개의 레지스트리 항목이 있음을 보여 줍니다.
레지스트리 키에 포함된 항목이 5개보다 적을 경우 기본적으로 테이블 형식으로 표시되지만 대체로 목록으로 보기가 더 쉽습니다.

두 번째 명령은 동일한 명령을 사용 `Get-ItemProperty` 합니다.
그러나이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 명령의 결과를 cmdlet으로 보냅니다 `Format-List` .
이 `Format-List` 명령은 ' * ' (모두) 값으로 Property 매개 변수를 사용 하 여 목록에 있는 개체의 모든 속성을 표시 합니다.
결과는 다음과 같은 샘플 출력에 표시됩니다.

결과 표시에는 "Path" 및 "Set-executionpolicy" 레지스트리 항목이 표시 되 고, 레지스트리 키 개체의 몇 가지 less 속성과 함께 표시 됩니다.
PS와 접두사로 시작 하는 다른 속성은 레지스트리 키를 나타내는 개체와 같은 PowerShell 사용자 지정 개체의 속성입니다.

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell
```

```output
Path                                                        ExecutionPolicy
----                                                        ---------------
C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe   RemoteSigned
```

```powershell
Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell | Format-List -Property *
```

```output
PSPath          : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds\Micro
soft.PowerShell
PSParentPath    : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Microsoft\PowerShell\1\ShellIds
PSChildName     : Microsoft.PowerShell
PSDrive         : HKLM
PSProvider      : Microsoft.PowerShell.Core\Registry
Path            : C:\Windows\system32\WindowsPowerShell\v1.0\powershell.exe
ExecutionPolicy : RemoteSigned
```

## PARAMETERS

### -Credential

이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.
기본값은 현재 사용자입니다.

"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .
사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

> [!WARNING]
> 이 매개 변수는 Windows PowerShell과 함께 설치된 모든 공급자에서 지원되지 않습니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

공급자의 형식 또는 언어로 필터를 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.

와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -포함

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.
경로 요소 또는 패턴(예: "*.txt")을 입력합니다.
와일드카드 문자를 사용할 수 있습니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LiteralPath

속성의 현재 위치에 대한 경로를 지정합니다.
**Path** 매개 변수와 달리 **LiteralPath** 값은 입력한 대로 사용됩니다.
어떠한 문자도 와일드카드로 해석되지 않습니다.
이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.
작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

검색할 속성의 이름을 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

항목의 경로를 지정합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -UseTransaction

활성 트랜잭션에 명령을 포함합니다.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 활성 트랜잭션에 명령 포함을 참조 하세요.
이 매개 변수는 트랜잭션이 진행 중인 경우에만 사용할 수 있습니다.
자세한 내용은 [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md)를 참조하세요.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-ItemProperty` .

## 출력

### System.string, System.string, System.web

`Get-ItemProperty` 가져오는 각 항목 속성에 대 한 개체를 반환 합니다.
개체 유형은 검색된 개체에 따라 달라집니다.
예를 들어 파일 시스템 드라이브에서는 파일 또는 폴더가 반환될 수 있습니다.

## 참고

`Get-ItemProperty`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면 ""을 입력 `Get-PSProvider` 합니다. 자세한 내용은 About_Providers를 참조하세요.

## 관련 링크

[Clear-ItemProperty](Clear-ItemProperty.md)

[Copy-ItemProperty](Copy-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Rename-ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)
