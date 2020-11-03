---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: fcfb974a360c450f474ba97d65190b019860d8c4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210578"
---
# Test-Path

## 개요
경로의 모든 요소가 있는지를 확인합니다.

## SYNTAX

### Path (기본값)

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### LiteralPath

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## 설명

`Test-Path`Cmdlet은 경로의 모든 요소가 있는지 여부를 확인 합니다. `$True`모든 요소가 존재 하는 경우를 반환 하 고, `$False` 없는 경우를 반환 합니다. 경로 구문이 올바른지 여부와 경로가 컨테이너 또는 터미널 또는 리프 요소로 이어질 수 있는지 여부도 확인할 수 있습니다. `Path`가 공백 문자열 이면 `$False` 이 반환 됩니다. `Path`이 `$null` , 배열 `$null` 또는 빈 배열인 경우 종료 되지 않는 오류가 반환 됩니다.

## 예제

### 예제 1: 경로 테스트

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

이 명령은 경로의 모든 요소, 즉 C: 디렉터리, 문서 및 설정 디렉터리 및 DavidC 디렉터리를 확인 합니다. 누락 된 항목이 있으면 cmdlet에서을 반환 `$False` 합니다.
그 외의 경우 `$True`를 반환합니다.

### 예 2: 프로필 경로 테스트

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

이러한 명령은 PowerShell 프로필 경로를 테스트 합니다.

첫 번째 명령은 경로의 모든 요소가 있는지를 확인합니다. 두 번째 명령은 경로의 구문이 올바른지 확인합니다. 이 경우 경로는 이지만 `$False` 구문이 올바릅니다 `$True` . 이러한 명령은 프로필이 `$profile` 없는 경우에도 프로필 위치를 가리키는 자동 변수인를 사용 합니다.

자동 변수에 대한 자세한 내용은 about_Automatic_Variables를 참조하세요.

### 예제 3: 지정 된 형식 외에 파일이 있는지 확인

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

이 명령은 상용 빌딩 디렉터리에 있는 파일이 있는지 여부를 확인 합니다.

이 명령은 **path** 매개 변수를 사용 하 여 경로를 지정 합니다. 경로에 공백이 포함 되어 있기 때문에 경로는 따옴표로 묶여 있습니다. 경로 끝의 별표는 Commercial Building 디렉터리의 내용을 나타냅니다. 이와 같은 긴 경로를 사용 하 여 경로의 처음 몇 글자를 입력 한 다음 TAB 키를 사용 하 여 경로를 완성 합니다.

이 명령은 **Exclude** 매개 변수를 지정 하 여 평가에서 생략 되는 파일을 지정 합니다.

이 경우 디렉터리에는. 개의 dwg 파일만 있으므로 결과는 `$False` 입니다.

### 예제 4: 파일 확인

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

이 명령은 변수에 저장 된 경로가 파일로 이어질 지 여부를 확인 `$profile` 합니다. 이 경우 PowerShell 프로필은 파일 이기 때문에 `.ps1` cmdlet은을 반환 `$True` 합니다.

### 예 5: 레지스트리에서 경로 확인

이러한 명령은 `Test-Path` PowerShell 레지스트리 공급자와 함께를 사용 합니다.

첫 번째 명령은 시스템에서 **Microsoft PowerShell** 레지스트리 키의 레지스트리 경로가 올바른지 테스트 합니다. PowerShell이 올바르게 설치 된 경우 cmdlet은을 반환 `$True` 합니다.

> [!IMPORTANT]
> `Test-Path` 모든 PowerShell 공급자에서 제대로 작동 하지 않습니다. 예를 들어를 사용 `Test-Path` 하 여 레지스트리 키의 경로를 테스트할 수 있지만 레지스트리 항목의 경로를 테스트 하는 데 사용 하는 경우 `$False` 레지스트리 항목이 존재 하더라도 항상를 반환 합니다.

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### 예제 6: 파일이 지정 된 날짜 보다 최신인 경우 테스트

이 명령은 **Newerthan** 동적 매개 변수를 사용 하 여 컴퓨터의 "PowerShell.exe" 파일이 "7 월 13 2009" 보다 최신 인지 여부를 확인 합니다.

NewerThan 매개 변수는 파일 시스템 드라이브에서만 작동합니다.

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### 예 7: 값으로 null을 사용 하 여 경로 테스트

, 배열 또는 빈 배열에 대해 반환 된 오류는 `null` `null` 종료 되지 않는 오류입니다. 을 사용 하 여 표시 하지 않을 수 있습니다 `-ErrorAction SilentlyContinue` . 다음 예에서는 오류를 반환 하는 모든 사례를 보여 줍니다 `NullPathNotPermitted` .

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### 예 8: 값으로 공백을 사용 하 여 경로 테스트

매개 변수에 대 한 공백 또는 빈 문자열이 제공 되 면 `-Path` **False** 를 반환 합니다.
다음 예제에서는 공백과 빈 문자열을 보여 줍니다.

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다. 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

이 cmdlet이 생략 하는 항목을 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴(예: "*.txt")을 입력합니다. 와일드카드 문자를 사용할 수 있습니다.

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

### -Filter

공급자의 형식 또는 언어로 필터를 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 와일드 카드 문자를 포함 한 필터 구문은 공급자에 따라 달라 집니다. 필터는 개체를 검색 한 후 개체를 검색 하는 대신 개체를 검색할 때 공급자가 개체를 검색할 때 적용 하므로 다른 매개 변수 보다 더 효율적입니다.

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

이 cmdlet이 테스트할 경로를 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴(예: "*.txt")을 입력합니다. 와일드카드 문자를 사용할 수 있습니다.

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

### -IsValid

경로의 요소가 존재 하는지 여부에 관계 없이이 cmdlet이 경로 구문을 테스트 함을 나타냅니다. 이 cmdlet은 `$True` 경로 구문이 유효 하면를 반환 하 고 그렇지 않으면를 반환 `$False` 합니다.

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

### -LiteralPath

테스트할 경로를 지정합니다. **Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드 문자로 해석되지 않습니다. PowerShell에서 이스케이프 시퀀스로 해석할 수 있는 문자가 경로에 포함 된 경우에는 해석 되지 않도록 경로를 작은따옴표로 묶어야 합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -NewerThan

시간을 **DateTime** 개체로 지정 합니다.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -OlderThan

시간을 **DateTime** 개체로 지정 합니다.

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

테스트할 경로를 지정합니다. 와일드카드 문자를 사용할 수 있습니다. 경로에 공백이 포함된 경우 경로를 따옴표로 묶어야 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -PathType

경로에 있는 마지막 요소의 형식을 지정 합니다. 이 cmdlet은 `$True` 요소가 지정 된 형식이 면를 반환 하 고, 그렇지 않으면를 반환 `$False` 합니다. 이 매개 변수에 허용되는 값은 다음과 같습니다.

- 컨테이너.
  디렉터리 또는 레지스트리 키와 같이 다른 요소를 포함하는 요소입니다.
- 수준이.
  파일과 같이 다른 요소를 포함하지 않는 요소입니다.
- 일부.
  컨테이너 또는 리프입니다.

경로에서 마지막 요소가 특정 유형인지를 나타냅니다.

> [!CAUTION]
>
> 최대 PowerShell 버전 6.1.2에서 **IsValid** 및 **pathtype** 스위치를 함께 지정 하면 `Test-Path` cmdlet은 **pathtype** 스위치를 무시 하 고 경로 형식의 유효성을 검사 하지 않고 구문의 유효성만 검사 합니다.
>
> [#8607 문제](https://github.com/PowerShell/PowerShell/issues/8607)에 따라이 동작을 수정 하는 것이 이후 버전에서 변경 될 수 있습니다. **IsValid** 및 **pathtype** 스위치는 개별 매개 변수 집합에 속하므로 이러한 혼동을 피하기 위해 함께 사용할 수 없습니다.

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

경로를 포함 하지만 리터럴 경로를 포함 하지 않는 문자열을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.Boolean

이 cmdlet은 **부울** 값을 반환 합니다.

## 참고

경로 명사 ( **path** cmdlet **)를 포함** 하는 cmdlet은 경로 이름으로 작동 하며 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다. 이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다.
이러한 **이름은 다른 이름** , **Normpath** , **Realpath** , **Join** 또는 기타 경로 조작자를 사용할 때 사용할 수 있습니다.

는 `Test-Path` 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Convert-Path](Convert-Path.md)

[Join-Path](Join-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)
