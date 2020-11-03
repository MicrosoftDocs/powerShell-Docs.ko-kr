---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Process
ms.openlocfilehash: 1880651719d030bd015a6f431fce60527b56aae5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210225"
---
# Get-Process

## 개요
로컬 컴퓨터에서 실행 중인 프로세스를 가져옵니다.

## SYNTAX

### 이름 (기본값)

```
Get-Process [[-Name] <String[]>] [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### NameWithUserName

```
Get-Process [[-Name] <String[]>] -IncludeUserName [<CommonParameters>]
```

### Id

```
Get-Process -Id <Int32[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### IdWithUserName

```
Get-Process -Id <Int32[]> -IncludeUserName [<CommonParameters>]
```

### InputObject

```
Get-Process -InputObject <Process[]> [-Module] [-FileVersionInfo] [<CommonParameters>]
```

### InputObjectWithUserName

```
Get-Process -InputObject <Process[]> -IncludeUserName [<CommonParameters>]
```

## 설명

`Get-Process`Cmdlet은 로컬 컴퓨터의 프로세스를 가져옵니다.

매개 변수가 없는 경우이 cmdlet은 로컬 컴퓨터의 모든 프로세스를 가져옵니다.
프로세스 이름 또는 PID (프로세스 ID)로 특정 프로세스를 지정 하거나 파이프라인을 통해 프로세스 개체를이 cmdlet으로 전달할 수도 있습니다.

기본적으로이 cmdlet은 프로세스에 대 한 자세한 정보가 있고 프로세스를 시작 및 중지할 수 있는 메서드를 지 원하는 프로세스 개체를 반환 합니다.
또한 cmdlet의 매개 변수를 사용 `Get-Process` 하 여 프로세스에서 실행 되는 프로그램에 대 한 파일 버전 정보를 가져오고 프로세스에서 로드 된 모듈을 가져올 수 있습니다.

## 예제

### 예 1: 로컬 컴퓨터의 모든 활성 프로세스 목록 가져오기

```powershell
Get-Process
```

이 명령은 로컬 컴퓨터에서 실행 중인 모든 활성 프로세스 목록을 가져옵니다.
각 열에 대 한 정의는 [참고](#notes) 섹션을 참조 하세요.

### 예제 2: 하나 이상의 프로세스에 대해 사용 가능한 모든 데이터 가져오기

```powershell
Get-Process winword, explorer | Format-List *
```

이 명령은 컴퓨터의 Winword 및 Explorer 프로세스에 대해 사용 가능한 모든 데이터를 가져옵니다.
**Name** 매개 변수를 사용 하 여 프로세스를 지정 하지만 선택적 매개 변수 이름은 생략 합니다.
파이프라인 연산자는 `|` 데이터를 cmdlet으로 전달 합니다 `Format-List` .이 Cmdlet은 `*` winword.exe 및 Explorer 프로세스 개체의 사용 가능한 모든 속성을 표시 합니다.

프로세스 ID로 프로세스를 식별할 수도 있습니다.
예를 들면 `Get-Process -Id 664, 2060` 입니다.

### 예제 3: 작업 집합이 지정 된 크기 보다 큰 모든 프로세스 가져오기

```powershell
Get-Process | Where-Object {$_.WorkingSet -gt 20000000}
```

이 명령은 작업 집합이 20MB보다 큰 프로세스를 모두 가져옵니다.
Cmdlet을 사용 하 여 `Get-Process`  실행 중인 모든 프로세스를 가져옵니다.
파이프라인 연산자는 `|` 프로세스 개체를 cmdlet으로 전달 합니다 `Where-Object` .이 Cmdlet은 **WorkingSet** 속성의 값이 2000만 바이트 보다 큰 개체만 선택 합니다.

**WorkingSet** 는 프로세스 개체의 많은 속성 중 하나입니다.
모든 속성을 보려면를 입력 `Get-Process | Get-Member` 합니다.
모든 수량 속성 값은 기본 표시에 킬로바이트 및 메가바이트 단위로 나열되더라도 기본적으로 바이트 단위입니다.

### 예 4: 우선 순위에 따라 그룹의 컴퓨터에 프로세스 나열

```powershell
$A = Get-Process
$A | Get-Process | Format-Table -View priority
```

이러한 명령은 우선 순위 클래스를 기준으로 컴퓨터의 프로세스를 그룹으로 나열 합니다.
첫 번째 명령은 컴퓨터의 모든 프로세스를 가져온 다음 변수에 저장 합니다 `$A` .

두 번째 명령은 변수에 저장 된 **프로세스** 개체를 cmdlet으로 파이프 `$A` `Get-Process` 한 다음 cmdlet에 파이프 하 여 `Format-Table` **우선 순위** 보기를 사용 하 여 프로세스 형식을 지정 합니다.

**우선 순위** 보기 및 다른 보기는 PowerShell 홈 디렉터리 ()의 types.ps1xml 형식 파일에 정의 되어 `$pshome` 있습니다.

### 예 5: 표준 Get-Process 출력 표시에 속성 추가

```powershell
Get-Process pwsh | Format-Table `
    @{Label = "NPM(K)"; Expression = {[int]($_.NPM / 1024)}},
    @{Label = "PM(K)"; Expression = {[int]($_.PM / 1024)}},
    @{Label = "WS(K)"; Expression = {[int]($_.WS / 1024)}},
    @{Label = "VM(M)"; Expression = {[int]($_.VM / 1MB)}},
    @{Label = "CPU(s)"; Expression = {if ($_.CPU) {$_.CPU.ToString("N")}}},
    Id, MachineName, ProcessName -AutoSize
```

```Output
NPM(K) PM(K) WS(K) VM(M) CPU(s)   Id MachineName ProcessName
------ ----- ----- ----- ------   -- ----------- -----------
     6 23500 31340   142 1.70   1980 .           pwsh
     6 23500 31348   142 2.75   4016 .           pwsh
    27 54572 54520   576 5.52   4428 .           pwsh
```

이 예제에서는 `Format-Table` 표준 출력 표시에 **MachineName** 속성을 추가 하는 명령을 제공 합니다 `Get-Process` .

### 예 6: 프로세스에 대 한 버전 정보 가져오기

```powershell
Get-Process pwsh -FileVersionInfo
```

```Output
ProductVersion   FileVersion      FileName
--------------   -----------      --------
6.1.2            6.1.2            C:\Program Files\PowerShell\6\pwsh.exe
```

이 명령은 **FileVersionInfo** 매개 변수를 사용 하 여 PowerShell 프로세스의 주 모듈인 pwsh.exe 파일에 대 한 버전 정보를 가져옵니다.

Windows Vista 이상에서 소유 하지 않은 프로세스를 사용 하 여이 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.

### 예 7: 지정 된 프로세스를 사용 하 여 로드 된 모듈 가져오기

```powershell
Get-Process SQL* -Module
```

이 명령은 **Module** 매개 변수를 사용 하 여 프로세스에 의해 로드 된 모듈을 가져옵니다.
이 명령은 이름이 SQL로 시작 하는 프로세스에 대 한 모듈을 가져옵니다.

사용자가 소유 하지 않은 프로세스를 사용 하 여 Windows Vista 및 이후 버전의 Windows에서이 명령을 실행 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.

### 예 8: 프로세스의 소유자 찾기

```powershell
Get-Process pwsh -IncludeUserName
```

```Output
Handles      WS(K)   CPU(s)     Id UserName            ProcessName
-------      -----   ------     -- --------            -----------
    782     132080     2.08   2188 DOMAIN01\user01     pwsh
```

이 명령은 프로세스의 소유자를 찾는 방법을 보여 줍니다.
Windows에서는 **Includeusername** 매개 변수에 관리자 권한 (관리자 권한으로 실행)이 필요 합니다.
출력은 소유자가 Domain01\user01.을 나타냅니다.

### 예 9: 자동 변수를 사용 하 여 현재 세션을 호스트 하는 프로세스 식별

```powershell
Get-Process pwsh
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21     105.95       4.33    1192  10 pwsh
    79    83.81     117.61       2.16   10580  10 pwsh
```

```powershell
Get-Process -Id $PID
```

```Output
NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
------    -----      -----     ------      --  -- -----------
    83    96.21      77.53       4.39    1192  10 pwsh
```

이러한 명령은 자동 변수를 사용 하 여 현재 PowerShell 세션을 호스트 하는 프로세스를 식별 하는 방법을 보여 줍니다 `$PID` .
이 방법을 사용 하 여 중지 하거나 닫을 수 있는 다른 PowerShell 프로세스와 호스트 프로세스를 구분할 수 있습니다.

첫 번째 명령은 현재 세션의 모든 PowerShell 프로세스를 가져옵니다.

두 번째 명령은 현재 세션을 호스트 하는 PowerShell 프로세스를 가져옵니다.

### 예 10: 주 창 제목이 있는 모든 프로세스를 가져와 테이블에 표시

```powershell
Get-Process | Where-Object {$_.mainWindowTitle} | Format-Table Id, Name, mainWindowtitle -AutoSize
```

이 명령은 주 창 제목이 있는 모든 프로세스를 가져온 다음 프로세스 ID 및 프로세스 이름과 함께 테이블에 표시합니다.

**MainWindowTitle** 속성은가 반환 하는 **프로세스** 개체의 여러 유용한 속성 중 하나일 뿐입니다 `Get-Process` .
모든 속성을 보려면 명령의 결과를 `Get-Process` cmdlet에 파이프 `Get-Member` `Get-Process | Get-Member` 합니다.

## PARAMETERS

### -FileVersionInfo

이 cmdlet이 프로세스에서 실행 되는 프로그램에 대 한 파일 버전 정보를 가져오는 것을 나타냅니다.

Windows Vista 이상 버전에서 소유 하지 않은 프로세스에 대해이 매개 변수를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.

원격 컴퓨터의 프로세스에 대 한 파일 버전 정보를 가져오려면 cmdlet을 사용 `Invoke-Command` 합니다.

이 매개 변수를 사용 하는 것은 각 프로세스 개체의 **FileVersionInfo** 속성을 가져오는 것과 같습니다.
이 매개 변수를 사용 하는 경우는 `Get-Process` 프로세스 개체가 아닌 **FileVersionInfo** 개체 **FileVersionInfo** 를 반환 합니다.
따라서와 같이 프로세스 개체가 필요한 cmdlet으로 명령의 출력을 파이프 할 수 없습니다 `Stop-Process` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases: FV, FVI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Id

PID(프로세스 ID)로 프로세스를 하나 이상 지정합니다.
여러 ID를 지정하려면 쉼표를 사용하여 ID를 구분합니다.
프로세스의 PID를 찾으려면를 입력 `Get-Process` 합니다.

```yaml
Type: System.Int32[]
Parameter Sets: Id, IdWithUserName
Aliases: PID

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -IncludeUserName

명령의 결과와 함께 **Process** 개체의 UserName 값이 반환 됨을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NameWithUserName, IdWithUserName, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

프로세스 개체를 하나 이상 지정합니다.
개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject, InputObjectWithUserName
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -모듈

이 cmdlet은 프로세스에 의해 로드 된 모듈을 가져옵니다.

Windows Vista 이상 버전에서 소유 하지 않은 프로세스에 대해이 매개 변수를 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 열어야 합니다.

원격 컴퓨터의 프로세스에서 로드 된 모듈을 가져오려면 cmdlet을 사용 합니다 `Invoke-Command` .

이 매개 변수는 각 프로세스 개체의 **Modules** 속성을 가져오는 것과 같습니다.
이 매개 변수를 사용 하는 경우이 cmdlet은 프로세스 개체가 아닌 **processmodule** 개체 **system.object** 를 반환 합니다.
따라서와 같이 프로세스 개체가 필요한 cmdlet으로 명령의 출력을 파이프 할 수 없습니다 `Stop-Process` .

동일한 명령에서 *Module* 및 **FileVersionInfo** 매개 변수를 모두 사용 하는 경우이 cmdlet은 모든 모듈의 파일 버전에 대 한 정보가 포함 된 **FileVersionInfo** 개체를 반환 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, Id, InputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

프로세스 이름으로 프로세스를 하나 이상 지정합니다.
쉼표로 구분하여 여러 프로세스 이름을 입력하고 와일드카드 문자를 사용할 수 있습니다.
매개 변수 이름("Name")은 선택 사항입니다.

```yaml
Type: System.String[]
Parameter Sets: Name, NameWithUserName
Aliases: ProcessName

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Diagnostics.Process

프로세스 개체를이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### FileVersionInfo, 시스템. i a. m a.

기본적으로이 cmdlet은 **system.web. Process** 개체를 반환 합니다.
**FileVersionInfo** 매개 변수를 사용 하는 경우 **FileVersionInfo** 개체를 반환 합니다.
**FileVersionInfo** 매개 변수 없이 **Module** 매개 변수를 사용 하는 경우에는 **system.object** 개체가 반환 됩니다.

## 참고

- 이 cmdlet을 기본 제공 별칭인 ps 및 gps로 참조할 수도 있습니다. 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
- 64 비트 버전의 Windows를 실행 하는 컴퓨터에서 64 비트 버전의 PowerShell은 64 비트 프로세스 모듈만 가져오고, 32 비트 버전의 PowerShell은 32 비트 프로세스 모듈만 가져옵니다.
- PowerShell에서 WMI (WMI(Windows Management Instrumentation)) Win32_Process 개체의 속성 및 메서드를 사용할 수 있습니다. 자세한 내용은 `Get-WmiObject` 및 WMI SDK를 참조 하십시오.
- 프로세스의 기본 표시는 다음 열을 포함하는 테이블입니다. 프로세스 개체의 모든 속성에 대 한 설명은 MSDN library의 [프로세스 속성](/dotnet/api/system.diagnostics.process) 을 참조 하세요.
  - Handles: 프로세스에서 연 핸들 수입니다.
  - NPM (K): 프로세스에서 사용 하는 비페이징 메모리의 양 (킬로바이트)입니다.
  - PM (K): 프로세스에서 사용 중인 페이징 가능한 메모리의 양 (킬로바이트)입니다.
  - WS (K): 프로세스의 작업 집합 크기 (kb)입니다.
    작업 집합은 프로세스에서 최근에 참조한 메모리 페이지로 구성됩니다.
  - VM (M): 프로세스에서 사용 하는 가상 메모리의 양 (메가바이트 단위)입니다.
    가상 메모리에는 디스크 페이징 파일의 스토리지가 포함됩니다.
  - CPU (s): 프로세스가 모든 프로세서에서 사용한 프로세서 시간의 양 (초)입니다.
  - ID: 프로세스의 PID (프로세스 ID)입니다.
  - ProcessName: 프로세스의 이름입니다.
    프로세스와 관련된 개념에 대한 설명은 도움말 및 지원 센터의 용어집 및 작업 관리자에 대한 도움말을 참조하세요.
- 에서 사용할 수 있는 프로세스의 기본 제공 대체 보기 `Format-Table` (예: **StartTime** 및 **Priority** )를 사용 하 고 고유한 보기를 디자인할 수도 있습니다.

## 관련 링크

[Debug-Process](Debug-Process.md)

[Get-Process](Get-Process.md)

[Start-Process](Start-Process.md)

[Stop-Process](Stop-Process.md)

[Wait-Process](Wait-Process.md)
