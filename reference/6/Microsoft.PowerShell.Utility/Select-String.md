---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/select-string?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Select-String
ms.openlocfilehash: 89880bc5ae45f442bea2d9c1f71d7df4cfa5e333
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "93219706"
---
# Select-String

## 개요
문자열 및 파일에서 텍스트를 찾습니다.

## SYNTAX

### File (기본값)

```
Select-String [-Pattern] <String[]> [-Path] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### Object

```
Select-String -InputObject <PSObject> [-Pattern] <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

### LiteralFile

```
Select-String [-Pattern] <String[]> -LiteralPath <String[]> [-SimpleMatch] [-CaseSensitive] [-Quiet]
 [-List] [-Include <String[]>] [-Exclude <String[]>] [-NotMatch] [-AllMatches]
 [-Encoding <Encoding>] [-Context <Int32[]>] [<CommonParameters>]
```

## 설명

`Select-String`Cmdlet은 입력 문자열 및 파일에서 텍스트 및 텍스트 패턴을 검색 합니다. `Select-String`UNIX의 경우 또는 Windows **grep** 에서 **findstr.exe** 와 비슷하게를 사용할 수 있습니다.

`Select-String` 는 텍스트 줄을 기반으로 합니다. 기본적으로 `Select-String` 는 각 줄에서 첫 번째 일치 항목을 찾은 다음 일치 하는 항목을 포함 하는 줄에 파일 이름, 줄 번호 및 모든 텍스트를 표시 합니다. 을 (를 `Select-String` ) 지정 하 여 줄 당 여러 개의 일치 항목을 찾거나, 일치 항목 앞뒤 텍스트를 표시 하거나, 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 표시할 수 있습니다.

`Select-String` 정규식 일치를 사용 하지만 지정 된 텍스트에 대 한 입력을 검색 하는 일치를 수행할 수도 있습니다.

`Select-String` 각 입력 파일의 첫 번째 일치 항목 뒤에 나오는 모든 텍스트 일치 항목을 표시 하거나 중지할 수 있습니다.
`Select-String` 지정 된 패턴과 일치 하지 않는 모든 텍스트를 표시 하는 데 사용할 수 있습니다.

`Select-String`유니코드 텍스트 파일을 검색 하는 경우와 같이 특정 문자 인코딩을 필요로 하도록 지정할 수도 있습니다. `Select-String` 는 BOM (바이트 순서 표시)을 사용 하 여 파일의 인코딩 형식을 검색 합니다. 파일에 BOM이 없으면 인코딩이 UTF8 이라고 가정 합니다.

## 예제

### 예 1: 대/소문자를 구분 하는 일치 찾기

이 예에서는 파이프라인을 통해 cmdlet에 전송 된 텍스트와 대/소문자를 구분 하는 일치를 수행 합니다 `Select-String` .

```powershell
'Hello', 'HELLO' | Select-String -Pattern 'HELLO' -CaseSensitive -SimpleMatch
```

텍스트 문자열 **Hello** 및 **hello** 는 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` .
`Select-String`**Pattern** 매개 변수를 사용 하 여 **HELLO** 를 지정 합니다. **CaseSensitive** 매개 변수는 사례가 대문자 패턴만 일치 하도록 지정 합니다. **SimpleMatch** 은 선택적 매개 변수 이며 패턴의 문자열이 정규식으로 해석 되지 않도록 지정 합니다.
`Select-String` PowerShell 콘솔에 **HELLO** 를 표시 합니다.

### 예제 2: 텍스트 파일에서 일치 항목 찾기

이 명령은 `.txt` 현재 디렉터리에 있는 파일 이름 확장명을 가진 모든 파일을 검색 합니다. 출력은 지정 된 문자열을 포함 하는 해당 파일의 줄을 표시 합니다.

```powershell
Get-Alias | Out-File -FilePath .\Alias.txt
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\*.txt -Pattern 'Get-'
```

```Output
Alias.txt:8:Alias            cat -> Get-Content
Alias.txt:28:Alias           dir -> Get-ChildItem
Alias.txt:43:Alias           gal -> Get-Alias
Command.txt:966:Cmdlet       Get-Acl
Command.txt:967:Cmdlet       Get-Alias
```

이 예제에서는 `Get-Alias` 및를 `Get-Command` cmdlet과 함께 사용 `Out-File` 하 여 현재 디렉터리에 두 개의 텍스트 파일 **Alias.txt** 및 **Command.txt** 를 만듭니다.

`Select-String` 는 **Path** 매개 변수를 별표 ( `*` ) 와일드 카드와 함께 사용 하 여 현재 디렉터리에서 파일 이름 확장명을 가진 모든 파일을 검색 `.txt` 합니다. **Pattern** 매개 변수는 **Get-** 과 일치 하는 텍스트를 지정 합니다. `Select-String` PowerShell 콘솔에 출력을 표시 합니다. 파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.

### 예제 3: 패턴 일치 찾기

이 예제에서는 지정 된 패턴과 일치 하는 항목을 찾기 위해 여러 파일을 검색 합니다. 패턴은 정규식 수량자를 사용 합니다. 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/About_Regular_Expressions.md)를 참조 하세요.

```powershell
Select-String -Path "$PSHOME\en-US\*.txt" -Pattern '\?'
```

```Output
C:\Program Files\PowerShell\6\en-US\default.help.txt:27:    beginning at https://go.microsoft.com/fwlink/?LinkID=108518.
C:\Program Files\PowerShell\6\en-US\default.help.txt:50:    or go to: https://go.microsoft.com/fwlink/?LinkID=210614
```

`Select-String`Cmdlet은 **경로** 와 **패턴** 의 두 매개 변수를 사용 합니다. **Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다. 경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` . **패턴** 매개 변수는 각 파일에서 물음표 ()와 일치 하도록 지정 합니다 `?` . 백슬래시 ( `\` )는 이스케이프 문자로 사용 되며 물음표 ( `?` )는 정규식 수량자 이므로 필요 합니다. `Select-String` PowerShell 콘솔에 출력을 표시 합니다. 파일 이름과 줄 번호는 **패턴** 매개 변수와 일치 하는 항목을 포함 하는 각 내용의 줄 앞에 옵니다.

### 예제 4: 함수에서 Select-String 사용

이 예에서는 PowerShell 도움말 파일에서 패턴을 검색 하는 함수를 만듭니다. 이 예에서는 함수가 PowerShell 세션에만 존재 합니다. PowerShell 세션이 닫히면 함수는 삭제 됩니다. 자세한 내용은 [about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)를 참조 하세요.

```
PS> Function Search-Help
>> {
>> $PSHelp = "$PSHOME\en-US\*.txt"
>> Select-String -Path $PSHelp -Pattern 'About_'
>> }
PS>

PS> Search-Help

C:\Program Files\PowerShell\6\en-US\default.help.txt:67:    The titles of conceptual topics begin with "About_".
C:\Program Files\PowerShell\6\en-US\default.help.txt:70:    Get-Help About_<topic-name>
C:\Program Files\PowerShell\6\en-US\default.help.txt:93:    Get-Help About_Modules : Displays help about PowerShell modules.
C:\Program Files\PowerShell\6\en-US\default.help.txt:97:    about_Updatable_Help
```

함수가 PowerShell 명령줄에 만들어집니다. 이 `Function` 명령은 **Search Help** 이름을 사용 합니다. **Enter** 키를 눌러 함수에 문을 추가 합니다. 프롬프트에서 `>>` 각 문을 추가 하 고 예제와 같이 **enter** 키를 누릅니다. 닫는 대괄호가 추가 되 면 PowerShell 프롬프트로 돌아갑니다.

함수는 두 개의 명령을 포함 합니다. `$PSHelp`변수는 PowerShell 도움말 파일에 대 한 경로를 저장 합니다. `$PSHOME` 는 디렉터리의 각 파일을 지정 하는 디렉터리 **en-us** 를 사용 하는 PowerShell 설치 디렉터리입니다 `*.txt` .

`Select-String`함수의 명령은 **Path** 및 **Pattern** 매개 변수를 사용 합니다. **Path** 매개 변수는 변수를 사용 하 여 `$PSHelp` 경로를 가져옵니다. **패턴** 매개 변수는 **About_** 문자열을 검색 조건으로 사용 합니다.

함수를 실행 하려면를 입력 `Search-Help` 합니다. 함수의 `Select-String` 명령은 PowerShell 콘솔에 출력을 표시 합니다.

### 예 5: Windows 이벤트 로그에서 문자열 검색

이 예에서는 Windows 이벤트 로그에서 문자열을 검색 합니다. 변수는 `$_` 파이프라인의 현재 개체를 나타냅니다. 자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

```powershell
$Events = Get-WinEvent -LogName Application -MaxEvents 50
$Events | Select-String -InputObject {$_.message} -Pattern 'Failed'
```

`Get-WinEvent`Cmdlet은 **LogName** 매개 변수를 사용 하 여 응용 프로그램 로그를 지정 합니다. **Maxevents** 매개 변수는 로그에서 50의 최신 이벤트를 가져옵니다. 로그 콘텐츠는 라는 변수에 저장 됩니다 `$Events` .

`$Events`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` . `Select-String`**InputObject** 매개 변수를 사용 합니다. `$_`변수는 현재 개체를 나타내고 `message` 는 이벤트의 속성입니다. **패턴** 매개 변수는 **실패** 문자열을,에서 일치 하는 항목을 검색 합니다 `$_.message` . `Select-String` PowerShell 콘솔에 출력을 표시 합니다.

### 예제 6: 하위 디렉터리에서 문자열 찾기

이 예에서는 디렉터리와 모든 하위 디렉터리에서 특정 텍스트 문자열을 검색 합니다.

```powershell
Get-ChildItem -Path C:\Windows\System32\*.txt -Recurse | Select-String -Pattern 'Microsoft' -CaseSensitive
```

`Get-ChildItem`**Path** 매개 변수를 사용 하 여 **를 \* 지정 합니다.** **재귀** 매개 변수는 하위 디렉터리를 포함 합니다. 개체는 파이프라인에서로 전송 됩니다 `Select-String` .

`Select-String` 는 **Pattern** 매개 변수를 사용 하 고 **Microsoft** 문자열을 지정 합니다. **CaseSensitive** 매개 변수는 문자열의 정확한 대/소문자를 비교 하는 데 사용 됩니다. `Select-String` PowerShell 콘솔에 출력을 표시 합니다.

> [!NOTE]
> 사용 권한에 따라 출력에 **액세스 거부** 메시지가 표시 될 수 있습니다.

### 예 7: 패턴과 일치 하지 않는 문자열 찾기

이 예제에서는 패턴과 일치 하지 않는 데이터 줄을 제외 하는 방법을 보여 줍니다.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get', 'Set'  -NotMatch
```

Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다. `Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다. **Pattern** 매개 변수는 **Get** 및 **Set** 을 검색 패턴으로 지정 합니다. **Notmatch** 매개 변수는 **Get** 및 **Set** 을 결과에서 제외 합니다.
`Select-String`**Get** 또는 **Set** 을 포함 하지 않는 PowerShell 콘솔의 출력을 표시 합니다.

### 예 8: 일치 전후 줄 찾기

이 예제에서는 일치 하는 패턴 앞뒤의 줄을 가져오는 방법을 보여 줍니다.

```powershell
Get-Command | Out-File -FilePath .\Command.txt
Select-String -Path .\Command.txt -Pattern 'Get-Computer' -Context 2, 3
```

```Output
  Command.txt:986:Cmdlet          Get-CmsMessage           6.1.0.0    Microsoft.PowerShell.Security
  Command.txt:987:Cmdlet          Get-Command              6.1.2.0    Microsoft.PowerShell.Core
> Command.txt:988:Cmdlet          Get-ComputerInfo         6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:990:Cmdlet          Get-Content              6.1.0.0    Microsoft.PowerShell.Management
  Command.txt:991:Cmdlet          Get-ControlPanelItem     3.1.0.0    Microsoft.PowerShell.Management
  Command.txt:992:Cmdlet          Get-Credential           6.1.0.0    Microsoft.PowerShell.Security
```

Cmdlet은 개체를에 `Get-Command` 파이프라인으로 보내 `Out-File` 현재 디렉터리에 **Command.txt** 파일을 만듭니다. `Select-String`**Path** 매개 변수를 사용 하 여 **Command.txt** 파일을 지정 합니다. **Pattern** 매개 변수는 **가져오기 컴퓨터** 를 검색 패턴으로 지정 합니다. **컨텍스트** 매개 변수는 앞과 뒤에 두 개의 값을 사용 하 고 출력에서 패턴 일치를 꺾쇠 괄호 ( `>` )로 표시 합니다. **Context** 매개 변수는 첫 번째 패턴 일치 앞에 두 줄을 출력 하 고, 마지막 패턴 일치 후에 세 줄을 출력 합니다.

### 예 9: 모든 패턴 일치 찾기

이 예제에서는 **Allmatches** 매개 변수가 텍스트 줄에서 각 패턴 일치 항목을 찾는 방법을 보여 줍니다. 기본적으로는 `Select-String` 텍스트 줄에서 첫 번째로 나타나는 패턴을 찾습니다. 이 예에서는 cmdlet에서 발견 된 개체 속성을 사용 `Get-Member` 합니다.

```
PS> $A = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell'

PS> $A

C:\Program Files\PowerShell\6\en-US\default.help.txt:3:    PowerShell Help System
C:\Program Files\PowerShell\6\en-US\default.help.txt:6:    Displays help about PowerShell cmdlets and concepts.
C:\Program Files\PowerShell\6\en-US\default.help.txt:9:    PowerShell Help describes PowerShell cmdlets

PS> $A.Matches

Groups   : {0}
Success  : True
Name     : 0
Captures : {0}
Index    : 4
Length   : 10
Value    : PowerShell

PS> $A.Matches.Length

8

PS> $B = Get-ChildItem -Path "$PSHOME\en-US\*.txt" | Select-String -Pattern 'PowerShell' -AllMatches

PS> $B.Matches.Length

9
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 합니다. **Path** 매개 변수는 `$PSHOME` PowerShell 디렉터리를 지정 하는 변수를 사용 합니다. 경로의 나머지 부분에는 **en-us** 하위 디렉터리가 포함 되 고 디렉터리의 각 파일을 지정 합니다 `*.txt` . `Get-ChildItem`개체는 변수에 저장 됩니다 `$A` . `$A`변수가 파이프라인에서 cmdlet으로 전송 됩니다 `Select-String` . `Select-String` 는 **Pattern** 매개 변수를 사용 하 여 각 파일에서 문자열 **PowerShell** 을 검색 합니다.

PowerShell 명령줄에서 `$A` 변수 내용이 표시 됩니다. 두 번의 문자열 **PowerShell** 이 포함 된 줄이 있습니다.

`$A.Matches`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 을 나열 합니다.

`$A.Matches.Length`속성은 각 줄에서 처음 발견 되는 패턴 **PowerShell** 수를 계산 합니다.

`$B`변수는 동일한 `Get-ChildItem` 및 `Select-String` cmdlet을 사용 하지만 **allmatches** 매개 변수를 추가 합니다. **Allmatches** 는 각 줄에서 각 패턴 **PowerShell** 의 발생을 찾습니다. 및 변수에 저장 된 개체 `$A` 는 `$B` 동일 합니다.

`$B.Matches.Length`각 줄에 대해 패턴 **PowerShell** 의 모든 발생이 계산 되기 때문에 속성은 늘어납니다.

## PARAMETERS

### -AllMatches

Cmdlet이 각 텍스트 줄에서 일치 하는 항목을 두 개 이상 검색 함을 나타냅니다. 이 매개 변수를 사용 하지 않으면는 `Select-String` 각 텍스트 줄에서 첫 번째 일치 항목만 찾습니다.

가 `Select-String` 텍스트 줄에서 일치 하는 항목을 여러 개 찾은 경우에도 해당 줄에 대해 하나의 **matchinfo** 개체만 가져오지만 개체의 **matches** 속성은 모든 일치 항목을 포함 합니다.

> [!NOTE]
> 이 매개 변수는 **SimpleMatch** 매개 변수와 함께 사용 하면 무시 됩니다. 모든 일치 항목을 반환 하려는 경우 검색 하는 패턴에 정규식 문자가 포함 되어 있으면 **SimpleMatch** 를 사용 하는 대신 해당 문자를 이스케이프 해야 합니다. 정규식 이스케이프에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md) 를 참조 하세요.

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

### -CaseSensitive

Cmdlet이 대/소문자를 구분 함을 나타냅니다. 기본적으로 일치는 대/소문자를 구분 하지 않습니다.

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

### -Context

패턴과 일치 하는 줄의 앞과 뒤에 지정 된 수의 줄을 캡처합니다.

이 매개 변수 값으로 하나의 숫자를 입력하면 해당 숫자가 일치하는 항목이 있는 줄 앞뒤로 캡처할 줄 수를 결정합니다. 값으로 숫자를 두 개 입력하면 첫 번째 숫자는 일치 항목 앞의 줄 수를 결정하고 두 번째 숫자는 일치 항목 뒤의 줄 수를 결정합니다. 예들 들어 `-Context 2,3`입니다.

기본 표시에서 일치 하는 줄이 `>` 표시의 첫 번째 열에 오른쪽 꺾쇠 괄호 () (ASCII 62)로 표시 됩니다. 표시되지 않은 줄은 컨텍스트입니다.

**컨텍스트** 매개 변수는에 의해 생성 된 개체의 수를 변경 하지 않습니다 `Select-String` .
`Select-String` 각 일치 항목에 대해 하나의 [Matchinfo](/dotnet/api/microsoft.powershell.commands.matchinfo) 개체를 생성 합니다. 컨텍스트는 개체의 **컨텍스트** 속성에 문자열 배열로 저장 됩니다.

`Select-String`명령의 출력이 파이프라인에서 다른 명령으로 전송 되 면 `Select-String` 수신 명령은 일치 하는 줄의 텍스트만 검색 합니다. 일치 하는 줄은 컨텍스트 줄의 텍스트가 아니라 **Matchinfo** 개체의 **line** 속성 값입니다. 결과적으로 **컨텍스트** 매개 변수는 수신 명령에서 유효 하지 않습니다 `Select-String` .

컨텍스트에 일치 항목이 포함 된 경우 각 일치 항목에 대 한 **Matchinfo** 개체에는 모든 컨텍스트 줄이 포함 되지만 겹치는 줄은 표시에 한 번만 나타납니다.

```yaml
Type: System.Int32[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `utf8NoBOM`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -제외

지정된 항목을 제외합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -포함

지정한 항목을 포함합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드가 지원됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

검색할 텍스트를 지정합니다. 텍스트가 포함된 변수를 입력하거나 텍스트를 가져오는 명령 또는 식을 입력하세요.

**InputObject** 매개 변수를 사용 하는 것은 파이프라인에서로 문자열을 보내는 것과는 다릅니다 `Select-String` .

둘 이상의 문자열을 cmdlet에 파이프 하면 `Select-String` 각 문자열에서 지정 된 텍스트를 검색 하 고 검색 텍스트가 포함 된 각 문자열을 반환 합니다.

**InputObject** 매개 변수를 사용 하 여 문자열 컬렉션을 전송 하는 경우는 `Select-String` 컬렉션을 결합 된 단일 문자열로 처리 합니다. `Select-String` 문자열에서 검색 텍스트를 찾은 경우 해당 문자열을 하나의 단위로 반환 합니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ObjectRaw, Object
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -목록

일치 하는 텍스트의 첫 번째 인스턴스만 각 입력 파일에서 반환 됩니다. 이는 정규식과 일치 하는 내용이 있는 파일 목록을 검색 하는 가장 효율적인 방법입니다.

기본적으로는 `Select-String` 찾은 각 일치 항목에 대해 **matchinfo** 개체를 반환 합니다.

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

### -LiteralPath

검색할 파일의 경로를 지정합니다. **LiteralPath** 매개 변수의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다. 자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NotMatch

**Notmatch** 매개 변수는 지정 된 패턴과 일치 하지 않는 텍스트를 찾습니다.

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

### -Path

검색할 파일의 경로를 지정 합니다. 와일드카드가 지원됩니다. 기본 위치는 로컬 디렉터리입니다.

디렉터리의 파일 (예:, 또는)을 지정 `log1.txt` `*.doc` `*.*` 합니다. 디렉터리만 지정하면 명령이 실패합니다.

```yaml
Type: System.String[]
Parameter Sets: File
Aliases:

Required: True
Position: 1
Default value: Local directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -패턴

각 줄에서 찾을 텍스트를 지정 합니다. 패턴 값은 정규식으로 처리 됩니다.

정규식에 대 한 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Quiet

Cmdlet이 **Matchinfo** 개체 대신 부울 값 (True 또는 False)을 반환 함을 나타냅니다. 패턴을 찾은 경우 값은 True입니다. 그렇지 않으면 False입니다.

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

### -SimpleMatch

Cmdlet이 정규식 일치 대신 단순 일치를 사용 함을 나타냅니다. 단순 일치에서는 `Select-String` **패턴** 매개 변수에서 텍스트의 입력을 검색 합니다. **패턴** 매개 변수의 값을 정규식 문으로 해석 하지 않습니다.

또한 **SimpleMatch** 를 사용 하면 반환 된 **Matchinfo** 개체의 **Matches** 속성이 비어 있습니다.

> [!NOTE]
> **Allmatches** 매개 변수와 함께이 매개 변수를 사용 하는 경우 **allmatches** 는 무시 됩니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

**ToString** 메서드가 있는 개체를로 파이프 할 수 있습니다 `Select-String` .

## 출력

### Microsoft.. MatchInfo 또는 system.string

기본적으로 출력은 찾은 각 일치 항목에 대해 하나의 **Matchinfo** 개체 집합입니다. **Quiet** 매개 변수를 사용 하는 경우 출력은 패턴을 찾을 수 있는지 여부를 나타내는 부울 값입니다.

## 참고

`Select-String` UNIX의 **grep** 또는 Windows의 **findstr.exe** 와 유사 합니다.

Cmdlet에 대 한 **sls** 별칭은 `Select-String` PowerShell 3.0에서 도입 되었습니다.

> [!NOTE]
> [PowerShell 명령에 대해 승인 된 동사](/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)에 따라 cmdlet에 대 한 공식 별칭 접두사는 `Select-*` 가 `sc` 아니라입니다 `sl` . 따라서에 대 한 적절 한 별칭은 `Select-String` `scs` 가 아니라 여야 합니다 `sls` . 이 규칙의 예외입니다.

을 사용 하려면 `Select-String` **패턴** 매개 변수의 값으로 찾을 텍스트를 입력 합니다. 검색할 텍스트를 지정 하려면 다음 조건을 사용 합니다.

- 따옴표 붙은 문자열에 텍스트를 입력 하 고로 파이프 `Select-String` 합니다.
- 텍스트 문자열을 변수에 저장 한 다음이 변수를 **InputObject** 매개 변수의 값으로 지정 합니다.
- 텍스트를 파일에 저장 하는 경우 **path** 매개 변수를 사용 하 여 파일 경로를 지정 합니다.

기본적으로는 `Select-String` **패턴** 매개 변수의 값을 정규식으로 해석 합니다. 자세한 내용은 [about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)를 참조 하세요. **SimpleMatch** 매개 변수를 사용 하 여 정규식 일치를 재정의할 수 있습니다. **SimpleMatch** 매개 변수는 입력에서 **Pattern** 매개 변수 값의 인스턴스를 찾습니다.

의 기본 출력은 `Select-String` 일치 항목에 대 한 자세한 정보를 포함 하는 **matchinfo** 개체입니다. **Matchinfo** 개체에는 **Filename** 및 **Line** 과 같은 속성이 있으므로이 개체의 정보는 파일에서 텍스트를 검색 하는 경우에 유용 합니다. 입력이 파일이 아닌 경우이 매개 변수의 값은 **InputStream** 입니다.

**Matchinfo** 개체의 정보가 필요 하지 않은 경우에는 **Quiet** 매개 변수를 사용 합니다. **Quiet** 매개 변수는 **matchinfo** 개체 대신 일치 하는 항목이 있는지 여부를 나타내는 부울 값 (True 또는 False)을 반환 합니다.

구를 일치 시키는 경우는 `Select-String` 시스템에 대해 설정 된 현재 문화권을 사용 합니다. 현재 문화권을 찾으려면 cmdlet을 사용 합니다 `Get-Culture` .

**Matchinfo** 개체의 속성을 찾으려면 다음 명령을 입력 합니다.

`Select-String -Path test.txt -Pattern 'test' | Get-Member | Format-List -Property *`

## 관련 링크

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md)

[about_Functions](../Microsoft.PowerShell.Core/About/about_Functions.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Regular_Expressions](../Microsoft.PowerShell.Core/About/about_Regular_Expressions.md)

[Get-Alias](Get-Alias.md)

[Get-ChildItem](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[Get-Command](../Microsoft.PowerShell.Core/Get-Command.md)

[Get-Member](Get-Member.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Out-File](Out-File.md)
