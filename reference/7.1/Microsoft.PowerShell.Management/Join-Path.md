---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/join-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Join-Path
ms.openlocfilehash: 4189201cd373d29e8ea8e88441376e0df902742e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211609"
---
# Join-Path

## 개요
경로와 하위 경로를 단일 경로로 결합합니다.

## SYNTAX

```
Join-Path [-Path] <String[]> [-ChildPath] <String> [[-AdditionalChildPath] <String[]>] [-Resolve]
 [-Credential <PSCredential>] [<CommonParameters>]
```

## 설명

`Join-Path`Cmdlet은 경로와 하위 경로를 단일 경로로 결합 합니다.
공급자가 경로 구분 기호를 제공합니다.

## 예제

### 예제 1: 경로를 하위 경로와 결합

```powershell
PS C:\> Join-Path -Path "path" -ChildPath "childpath"
```

```output
path\childpath
```

이 명령은 `Join-Path` 를 사용 하 여 경로를 childpath와 결합 합니다.

명령은 공급자에서 실행 되므로 경로를 `FileSystem` `\` 조인 하는 구분 기호를 제공 합니다.

### 예제 2: 디렉터리 구분 기호가 이미 포함 된 경로 결합

```powershell
PS C:\> Join-Path -Path "path\" -ChildPath "\childpath"
```

```output
path\childpath
```

기존 디렉터리 구분 기호 `\` 를 처리 하 고 `Path``ChildPath`

### 예제 3: 경로를 자식 경로에 조인 하 여 파일 및 폴더 표시

```powershell
Join-Path "C:\win*" "System*" -Resolve
```

이 명령은 C:\Win \* 경로 및 시스템 자식 경로를 조인 하 여 참조 되는 파일 및 폴더를 표시 합니다 \* .
과 동일한 파일 및 폴더를 표시 `Get-ChildItem` 하지만 각 항목의 정규화 된 경로를 표시 합니다.
이 명령에서는 `Path` 및 `ChildPath` 선택적 매개 변수 이름이 생략 됩니다.

### 예제 4: PowerShell 레지스트리 공급자와 Join-Path 사용

```powershell
PS HKLM:\> Join-Path -Path System -ChildPath *ControlSet* -Resolve
```

```output
HKLM:\System\ControlSet001
HKLM:\System\CurrentControlSet
```

이 명령은 `HKLM\System` 를 포함 하는 레지스트리 하위 키에 레지스트리 키를 표시 합니다 `ControlSet` .

`Resolve`매개 변수는 현재 공급자 경로에서 와일드 카드를 포함 하 여 조인 된 경로를 확인 하려고 시도 합니다.`HKLM:\`

### 예 5: 여러 경로 루트를 하위 경로와 결합

```powershell
Join-Path -Path C:, D:, E:, F: -ChildPath New
```

```output
C:\New
D:\New
E:\New
F:\New
```

이 명령은 `Join-Path` 를 사용 하 여 여러 경로 루트를 하위 경로와 결합 합니다.

> [!NOTE]
> 로 지정 된 드라이브가 `Path` 존재 해야 합니다. 그렇지 않으면 해당 항목의 조인이 실패 합니다.

### 예제 6: 파일 시스템 드라이브의 루트를 하위 경로와 결합

```powershell
Get-PSDrive -PSProvider filesystem | ForEach-Object {$_.root} | Join-Path -ChildPath "Subdir"
```

```output
C:\Subdir
D:\Subdir
```

이 명령은 콘솔에 있는 각 PowerShell 파일 시스템 드라이브의 루트를 Subdir 하위 경로와 결합 합니다.

이 명령은 cmdlet을 사용 하 여 `Get-PSDrive` FileSystem 공급자가 지 원하는 PowerShell 드라이브를 가져옵니다.
`ForEach-Object`문은 개체의 Root 속성만 선택 `PSDriveInfo` 하 고 지정 된 자식 경로와 결합 합니다.

출력은 컴퓨터의 PowerShell 드라이브에 C:\Program Files 디렉터리에 매핑된 드라이브가 포함 되어 있음을 보여 줍니다.

### 예제 7: 경로를 무한 개수에 결합

```powershell
Join-Path a b c d e f g
```

```Output
a\b\c\d\e\f\g
```

`AdditionalChildPath`매개 변수를 사용 하면 개수에 제한 없이 경로를 조인할 수 있습니다.

이 예제에서는 매개 변수 이름이 사용 되지 않으므로 "a"는에, " `Path` b"는 `ChildPath` 및 "c-g"에 바인딩합니다. `AdditionalChildPath`

## PARAMETERS

### -AdditionalChildPath

*Path* 매개 변수의 값에 추가할 추가 요소를 지정 합니다. `ChildPath`매개 변수는 여전히 필수 이며 지정 해야 합니다.

이 매개 변수는 `ValueFromRemainingArguments` 무제한 개수의 경로를 조인할 수 있도록 하는 속성을 사용 하 여 지정 됩니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ChildPath

매개 변수 값에 추가할 요소를 지정 합니다 `Path` .
와일드카드가 지원됩니다.
매개 변수 `ChildPath` 이름 ("ChildPath")은 선택 사항 이지만 매개 변수는 필수입니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.
> 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면 [Invoke 명령을](../Microsoft.PowerShell.Core/Invoke-Command.md)사용 합니다.

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

### -Path

하위 경로를 추가할 기본 경로를 하나 이상 지정합니다.
와일드카드가 지원됩니다.

값은 경로 `Path` 를 조인 하는 공급자를 결정 하 고 경로 구분 기호를 추가 합니다.
매개 변수 `Path` 이름 ("Path")은 선택 사항 이지만 매개 변수는 필수입니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -해결

이 cmdlet이 현재 공급자의 조인 된 경로를 확인 하려고 시도 함을 나타냅니다.

- 와일드 카드를 사용 하는 경우 cmdlet은 조인 된 경로와 일치 하는 모든 경로를 반환 합니다.
- 와일드 **카드를 사용 하지 않는** 경우 경로가 없으면 cmdlet이 오류가 발생 합니다.

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

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### System.String

이 cmdlet은 결과 경로를 포함 하는 문자열을 반환 합니다.

## 참고

경로 명사 (Path cmdlet)를 포함 하는 cmdlet은 경로 이름을 조작 하 고 모든 PowerShell 공급자가 해석할 수 있는 간결한 형식으로 이름을 반환 합니다. 이 cmdlet은 경로 이름의 전체 또는 일부를 특정 형식으로 표시하려는 프로그램 및 스크립트에 사용하도록 디자인되었습니다. Dirname, Normpath, Realpath, Join 또는 기타 경로 조작자를 사용할 때와 같은 방법으로 사용하면 됩니다.

`FileSystem`, 및 공급자를 포함 하 여 여러 공급자와 함께 path cmdlet을 사용할 수 있습니다 `Registry` `Certificate` .

이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다.
세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.
자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Convert-Path](Convert-Path.md)

[Resolve-Path](Resolve-Path.md)

[Split-Path](Split-Path.md)

[Test-Path](Test-Path.md)

[Get-PSProvider](Get-PSProvider.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-PSDrive](Get-PSDrive.md)

