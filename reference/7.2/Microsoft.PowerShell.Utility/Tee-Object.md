---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/tee-object?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Tee-Object
ms.openlocfilehash: 5fd1ff9760cbddeb0c5c29052caf0f36d6d760d0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602669"
---
# Tee-Object

## 개요
명령 출력을 파일 또는 변수에 저장하고 파이프라인으로도 보냅니다.

## SYNTAX

### File (기본값)

```
Tee-Object [-InputObject <PSObject>] [-FilePath] <String> [-Append] [<CommonParameters>]
```

### LiteralFile

```
Tee-Object [-InputObject <PSObject>] -LiteralPath <String> [<CommonParameters>]
```

### 변수

```
Tee-Object [-InputObject <PSObject>] -Variable <String> [<CommonParameters>]
```

## 설명

`Tee-Object`Cmdlet은 출력을 리디렉션합니다. 즉, 명령의 출력을 두 방향으로 전송 합니다 (예: 문자 T). 이 명령은 출력을 파일 또는 변수에 저장하고 파이프라인으로도 보냅니다. `Tee-Object`이 파이프라인에서 마지막 명령이 면 명령 출력이 프롬프트에 표시 됩니다.

## 예제

### 예제 1: 파일 및 콘솔에 프로세스 출력

이 예제에서는 컴퓨터에서 실행 중인 프로세스 목록을 가져와 그 결과를 파일로 보냅니다.
두 번째 경로를 지정하지 않았으므로 해당 프로세스가 콘솔에 표시됩니다.

```powershell
Get-Process | Tee-Object -FilePath "C:\Test1\testfile2.txt"
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)    Id ProcessName
-------  ------    -----      ----- -----   ------    -- -----------
83       4     2300       4520    39     0.30    4032 00THotkey
272      6     1400       3944    34     0.06    3088 alg
81       3      804       3284    21     2.45     148 ApntEx
81       4     2008       5808    38     0.75    3684 Apoint
...
```

### 예제 2: 변수를 변수로 출력 `Select-Object`

이 예제에서는 컴퓨터에서 실행 중인 프로세스 목록을 가져와 `$proc` 변수에 저장 한 다음로 파이프 `Select-Object` 합니다.

```powershell
Get-Process notepad | Tee-Object -Variable proc | Select-Object processname,handles
```

```Output
ProcessName                              Handles
-----------                              -------
notepad                                  43
notepad                                  37
notepad                                  38
notepad                                  38
```

`Select-Object`Cmdlet은 **ProcessName** 및 **Handles** 속성을 선택 합니다. 변수에는에 `$proc` 의해 반환 되는 기본 정보가 포함 됩니다 `Get-Process` .

### 예 3: 두 개의 로그 파일에 시스템 파일 출력

이 예에서는 두 개의 로그 파일 (누적 파일과 현재 파일)에 시스템 파일의 목록을 저장 합니다.

```powershell
Get-ChildItem -Path D: -File -System -Recurse |
  Tee-Object -FilePath "c:\test\AllSystemFiles.txt" -Append |
    Out-File c:\test\NewSystemFiles.txt
```

이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` D: 드라이브에서 시스템 파일에 대 한 재귀 검색을 수행 합니다. 파이프라인 연산자 (|)는 목록을 `Tee-Object` AllSystemFiles.txt 파일에 추가 하 고 파이프라인의 목록을 파이프라인으로 전달 하 여 `Out-File` NewSystemFiles.txt 파일에 목록을 저장 합니다.

## PARAMETERS

### -추가

Cmdlet이 지정 된 파일에 출력을 추가 함을 나타냅니다. 이 매개 변수를 지정하지 않으면 새 내용이 경고 없이 파일의 기존 내용을 대체합니다.

이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: File
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilePath

이 cmdlet이 개체를 와일드 카드 문자에 저장 하도록 허용 하지만 단일 파일로 확인 해야 하는 파일을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: File
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -InputObject

저장 및 표시할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를로 파이프 할 수도 있습니다 `Tee-Object` .

에 **inputobject** 매개 변수를 사용 하는 경우 `Tee-Object` 명령 결과를로 파이프 하는 대신 `Tee-Object` **inputobject** 값은 값이 컬렉션인 경우에도 단일 개체로 처리 됩니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

이 cmdlet이 개체를 저장 하는 파일을 지정 합니다. **FilePath** 와 달리 **LiteralPath** 매개 변수 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

```yaml
Type: System.String
Parameter Sets: LiteralFile
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Variable

Cmdlet이 개체를 저장 하는 변수를 지정 합니다. 앞에 달러 기호 ()를 사용 하지 않고 변수 이름을 입력 `$` 합니다.

```yaml
Type: System.String
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.web. PSObject

개체를로 파이프 할 수 있습니다 `Tee-Object` .

## 출력

### System.web. PSObject

`Tee-Object` 는 리디렉션되는 개체를 반환 합니다.

## 참고

`Out-File`Cmdlet 또는 리디렉션 연산자를 사용할 수도 있습니다 .이 연산자는 출력을 파일에 저장 하지만 파이프라인으로는 보내지 않습니다.

PowerShell 6부터 `Tee-Object` 은 파일에 쓸 때 BOM LESS utf-8 인코딩을 사용 합니다. 다른 인코딩이 필요한 경우에는 `Out-File` **encoding** 매개 변수와 함께 cmdlet을 사용 합니다.

## 관련 링크

[Compare-Object](Compare-Object.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Group-Object](Group-Object.md)

[Measure-Object](Measure-Object.md)

[New-Object](New-Object.md)

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

[Where-Object](../Microsoft.PowerShell.Core/Where-Object.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

