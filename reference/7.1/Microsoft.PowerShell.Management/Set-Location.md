---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 02/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-location?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Location
ms.openlocfilehash: 0c511ea30d55c1e6949f687c81d1edef809546fc
ms.sourcegitcommit: fe1e20f8523e3663d68546093aaf3670182337b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2020
ms.locfileid: "93219570"
---
# Set-Location

## 개요
현재 작업 위치를 지정된 위치로 설정합니다.

## SYNTAX

### Path (기본값)

```
Set-Location [[-Path] <String>] [-PassThru] [<CommonParameters>]
```

### LiteralPath

```
Set-Location -LiteralPath <String> [-PassThru] [<CommonParameters>]
```

### 스택

```
Set-Location [-PassThru] [-StackName <String>] [<CommonParameters>]
```

## 설명

`Set-Location`Cmdlet은 작업 위치를 지정 된 위치로 설정 합니다. 해당 위치는 디렉터리, 하위 디렉터리, 레지스트리 위치 또는 공급자 경로일 수 있습니다.

PowerShell 6.2 `-` `+` 은 **Path** 매개 변수의 값으로 및에 대 한 지원을 추가 했습니다. PowerShell은 및를 사용 하 여 액세스할 수 있는 최근 20 개 위치의 기록을 유지 관리 `-` `+` 합니다. 이 목록은 **Stackname** 매개 변수를 사용 하 여 액세스 하는 위치 스택과는 독립적입니다.

## 예제

### 예제 1: 현재 위치 설정

```
PS C:\> Set-Location -Path "HKLM:\"
PS HKLM:\>
```

이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `HKLM:` .

### 예 2: 현재 위치를 설정 하 고 해당 위치를 표시 합니다.

```
PS C:\> Set-Location -Path "Env:\" -PassThru
```

```Output
Path
----
Env:\

PS Env:\>
```

이 명령은 현재 위치를 드라이브의 루트로 설정 합니다 `Env:` . **PassThru** 매개 변수를 사용 하 여 PowerShell에서 위치를 나타내는 **pathinfo** 개체를 반환 하도록 지시 합니다 `Env:\` .

### 예 3: 위치를 C: 드라이브의 현재 위치로 설정

```powershell
PS C:\Windows\> Set-Location HKLM:\
PS HKLM:\> Set-Location C:
PS C:\Windows\>
```

첫 번째 명령은 `HKLM:` 레지스트리 공급자에 있는 드라이브의 루트로 위치를 설정 합니다.
두 번째 명령은 `C:` 파일 시스템 공급자에서 드라이브의 현재 위치로 위치를 설정 합니다.
드라이브 이름이 백슬래시 없이 형식으로 지정 된 경우 `<DriveName>:` cmdlet은 PSDrive의 현재 위치로 위치를 설정 합니다.
PSDrive use 명령에서 현재 위치를 가져옵니다 `Get-Location -PSDrive <DriveName>` .

### 예제 4: 현재 위치를 명명 된 스택으로 설정

```
PS C:\> Push-Location -Path 'C:\Program Files\PowerShell\' -StackName "Paths"
PS C:\Program Files\PowerShell\> Set-Location -StackName "Paths"
PS C:\Program Files\PowerShell\> Get-Location -Stack
```

```Output
Path
----
C:\
```

첫 번째 명령은 현재 위치를 경로 스택에 추가 합니다.
두 번째 명령은 경로 위치 스택을 현재 위치 스택으로 설정 합니다.
세 번째 명령은 현재 위치 스택의 위치를 표시 합니다.

`*-Location`명령에 다른 위치 스택이 지정 되지 않은 경우 cmdlet은 현재 위치 스택을 사용 합니다. 위치 스택에 대 한 자세한 [내용은 참고를 참조 하세요.](#notes)

### 예 5: 또는를 사용 하 여 위치 기록 탐색 `+``-`

```
PS C:\> Set-Location -Path $env:SystemRoot
PS C:\Windows> Set-Location -Path Cert:\
PS Cert:\> Set-Location -Path HKLM:\
PS HKLM:\>

# Navigate back through the history using "-"
PS HKLM:\> Set-Location -Path -
PS Cert:\> Set-Location -Path -
PS C:\Windows>

# Navigate using the Set-Location alias "cd" and the implicit positional Path parameter
PS C:\Windows> cd -
PS C:\> cd +
PS C:\Windows> cd +
PS Cert:\>
```

별칭을 사용 하 여 `cd -` 또는 `cd +` 터미널에서 위치 기록을 탐색 하는 쉬운 방법입니다. 로 이동 하는 방법에 대 한 자세한 내용은 `-` / `+` **Path** 매개 변수를 참조 하세요.

## PARAMETERS

### -LiteralPath

위치의 경로를 지정 합니다. **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

위치를 나타내는 **Pathinfo** 개체를 반환 합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

새 작업 위치의 경로를 지정 합니다. 경로를 제공 하지 않으면 기본적으로 `Set-Location` 현재 사용자의 홈 디렉터리를 사용 합니다. 와일드 카드를 사용 하는 경우 cmdlet은 와일드 카드 패턴과 일치 하는 첫 번째 경로를 선택 합니다.

PowerShell은 사용자가 설정한 최근 20 개 위치의 기록을 보관 합니다. **Path** 매개 변수 값이 문자 이면 `-` 새 작업 위치가 기록의 이전 작업 위치 (있는 경우)가 됩니다. 마찬가지로 값이 `+` 문자인 경우 새 작업 위치가 기록의 다음 작업 위치가 됩니다 (있는 경우). 이는 `Pop-Location` `Push-Location` 기록이 스택을 제외 하 고 암시적으로 추적 되며 수동으로 제어 되지 않는다는 점을 제외 하 고는 및를 사용 하는 것과 비슷합니다. 현재 기록 목록을 볼 수 있는 방법은 없습니다.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -StackName

이 cmdlet이 현재 위치 스택을 만드는 기존 위치 스택 이름을 지정 합니다. 위치 스택 이름을 입력합니다. 이름 없는 기본 위치 스택을 나타내려면 `$null` 또는 빈 문자열 ()을 입력 `""` 합니다.

`*-Location` **Stackname** 매개 변수를 사용 하 여 다른 스택을 지정 하지 않는 한 cmdlet은 현재 스택에서 작동 합니다. 위치 스택에 대 한 자세한 내용은 참고를 참조 [하세요.](#notes)

```yaml
Type: System.String
Parameter Sets: Stack
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### None, System.web. PathInfo, System.web. PathInfoStack

**PassThru** 매개 변수를 지정 하지 않으면이 cmdlet은 출력을 생성 하지 않습니다. **PassThru** 와 **Path** 또는 **LiteralPath** 를 함께 사용 하면 새 위치를 나타내는 **pathinfo** 개체가 생성 됩니다. **Stackname** 과 함께 **PassThru** 를 사용 하면 새 스택 컨텍스트를 나타내는 **pathinfostack** 개체가 생성 됩니다.

## 참고

PowerShell은 프로세스 당 여러 runspace를 지원 합니다. 각 runspace에는 자체의 _현재 디렉터리가_ 있습니다.
와는 다릅니다 `[System.Environment]::CurrentDirectory` . 이 동작은 명시적 디렉터리 경로를 제공 하지 않고 .NET Api를 호출 하거나 네이티브 응용 프로그램을 실행할 때 문제가 될 수 있습니다.

Location cmdlet이 프로세스 차원의 현재 디렉터리를 설정 했더라도 다른 runspace가 언제 든 지 변경 될 수 있으므로이를 종속 시킬 수 없습니다. 현재 runspace와 관련 된 현재 작업 디렉터리를 사용 하 여 경로 기반 작업을 수행 하려면 location cmdlet을 사용 해야 합니다.

`Set-Location`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/about/about_Providers.md)를 참조하세요.

스택은 가장 최근에 추가한 항목만 액세스할 수 있는 마지막으로 시작 된 목록입니다. 사용하는 순서대로 스택에 항목을 추가한 다음 사용을 위해 역순으로 검색합니다. PowerShell을 사용 하 여 공급자 위치를 위치 스택에 저장할 수 있습니다. PowerShell은 이름 없는 기본 위치 스택을 만듭니다. 명명 된 위치 스택을 여러 개 만들 수 있습니다. 스택 이름을 지정 하지 않으면 PowerShell은 현재 위치 스택을 사용 합니다. 기본적으로 이름 없는 기본 위치는 현재 위치 스택입니다. 하지만 cmdlet을 사용 `Set-Location` 하 여 현재 위치 스택을 변경할 수 있습니다.

위치 스택을 관리 하려면 다음과 `*-Location` 같이 cmdlet을 사용 합니다.

- 위치 스택에 위치를 추가 하려면 cmdlet을 사용 `Push-Location` 합니다.

- 위치 스택에서 위치를 가져오려면 cmdlet을 사용 `Pop-Location` 합니다.

- 현재 위치 스택의 위치를 표시 하려면 cmdlet의 **stack** 매개 변수를 사용 합니다 `Get-Location` . 명명 된 위치 스택의 위치를 표시 하려면의 **Stackname** 매개 변수를 사용 `Get-Location` 합니다.

- 새 위치 스택을 만들려면의 **Stackname** 매개 변수를 사용 `Push-Location` 합니다. 존재 하지 않는 스택을 지정 하면에서 `Push-Location` 스택을 만듭니다.

- 위치 스택을 현재 위치 스택으로 설정 하려면의 **Stackname** 매개 변수를 사용 `Set-Location` 합니다.

이름 없는 기본 위치 스택은 현재 위치 스택인 경우에만 완전히 액세스할 수 있습니다.
명명 된 위치 스택을 현재 위치 스택으로 만들면 `Push-Location` 또는 cmdlet을 사용 `Pop-Location` 하 여 기본 스택에서 항목을 추가 하거나 가져올 수 없으며 cmdlet을 사용 하 여 `Get-Location` 명명 되지 않은 스택의 위치를 표시할 수 없습니다. 명명 되지 않은 스택을 현재 스택으로 만들려면 cmdlet의 **Stackname** 매개 변수를 `Set-Location` 값 `$null` 이나 빈 문자열 ()로 사용 `""` 합니다.

## 관련 링크

[Get-Location](Get-Location.md)

[Pop-Location](Pop-Location.md)

[Push-Location](Push-Location.md)

