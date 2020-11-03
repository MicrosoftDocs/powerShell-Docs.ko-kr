---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-unique?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Unique
ms.openlocfilehash: f0233e24e82ce5f0ef2113f65d19134833d75cb1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213010"
---
# Get-Unique

## 개요
정렬된 목록에서 고유한 항목을 반환합니다.

## SYNTAX

### AsString (기본값)

```
Get-Unique [-InputObject <PSObject>] [-AsString] [<CommonParameters>]
```

### UniqueByType

```
Get-Unique [-InputObject <PSObject>] [-OnType] [<CommonParameters>]
```

## 설명

`Get-Unique`이 cmdlet은 정렬 된 목록의 각 항목을 다음 항목과 비교 하 고, 중복을 제거 하 고, 각 항목의 인스턴스를 하나만 반환 합니다. cmdlet이 제대로 작동하려면 목록을 정렬해야 합니다.

`Get-Unique`은 대/소문자를 구분합니다. 따라서 문자의 대/소문자만 다른 문자열은 고유한 것으로 간주합니다.

## 예제

### 예제 1: 텍스트 파일에서 고유한 단어 가져오기

이러한 명령은 텍스트 파일에서 고유한 단어 수를 찾습니다.

```powershell
$A = $( foreach ($line in Get-Content C:\Test1\File1.txt) {
    $line.tolower().split(" ")
  }) | Sort-Object | Get-Unique
$A.count
```

첫 번째 명령은 File.txt 파일의 내용을 가져오고, 각 텍스트 줄을 소문자로 변경한 다음 공백(" ")에서 별도의 줄로 각 단어를 분할합니다. 그런 다음 결과 목록을 사전순 (기본값)으로 정렬 하 고 cmdlet을 사용 하 여 `Get-Unique` 중복 된 단어를 제거 합니다. 결과는 변수에 저장 됩니다 `$A` .

두 번째 명령은에서 문자열 컬렉션의 **Count** 속성을 사용 하 여 `$A` 에 있는 항목 수를 확인 합니다 `$A` .

### 예제 2: 배열에서 고유한 정수 가져오기

이 명령은 정수 집합의 고유한 멤버를 찾습니다.

```powershell
1,1,1,1,12,23,4,5,4643,5,3,3,3,3,3,3,3 | Sort-Object | Get-Unique
```

```Output
1
3
4
5
12
23
4643
```

첫 번째 명령은 명령줄에서 입력 한 정수 배열을 가져와이를 cmdlet으로 파이프 하 여 `Sort-Object` 정렬 한 다음이를 파이프 하 여 중복 된 항목을 제거 합니다 `Get-Unique` .

### 예제 3: 디렉터리에서 고유 개체 형식 가져오기

이 명령은 cmdlet을 사용 하 여 `Get-ChildItem` 파일 및 디렉터리를 포함 하는 로컬 디렉터리의 콘텐츠를 검색 합니다.

```powershell
Get-ChildItem | Sort-Object {$_.GetType()} | Get-Unique -OnType
```

파이프라인 연산자 (|)가 결과를 cmdlet으로 보냅니다 `Sort-Object` . `$_.GetType()`문은 **GetType** 메서드를 각 파일 또는 디렉터리에 적용 합니다. 그런 다음 `Sort-Object` 유형별로 항목을 정렬 합니다. 다른 파이프라인 연산자는 결과를로 보냅니다 `Get-Unique` . **Ontype** 매개 변수는 `Get-Unique` 각 형식의 하나의 개체만 반환 하도록 지시 합니다.

### 예제 4: 고유한 프로세스 가져오기

이 명령은 컴퓨터에서 실행되는 프로세스의 이름을 중복 항목을 제거하고 가져옵니다.

```powershell
Get-Process | Sort-Object | Select-Object processname | Get-Unique -AsString
```

`Get-Process`명령은 컴퓨터의 모든 프로세스를 가져옵니다. 파이프라인 연산자 (|)는 결과를에 전달 합니다 `Sort-Object` .이는 기본적으로 ProcessName에 의해 사전순으로 프로세스를 정렬 합니다. 결과는 cmdlet에 파이프 되어 `Select-Object` 각 개체의 ProcessName 속성 값만 선택 합니다. 그런 다음 결과를로 파이프 하 여 `Get-Unique` 중복 항목을 제거 합니다.

**Asstring** 매개 변수는 `Get-Unique` **ProcessName** 값을 문자열로 처리 하도록에 지시 합니다.
이 매개 변수를 사용 하지 않으면는 `Get-Unique` **ProcessName** 값을 개체로 처리 하 고 개체의 인스턴스 하나 즉, 목록의 첫 번째 프로세스 이름만 반환 합니다.

## PARAMETERS

### -AsString

이 cmdlet이 데이터를 문자열로 사용 함을 나타냅니다. 이 매개 변수를 사용 하지 않으면 데이터는 개체로 처리 되므로 동일한 형식의 개체 컬렉션을 파일 컬렉션과 같은에 제출할 때에는 `Get-Unique` 하나 (첫 번째)만 반환 합니다. 이 매개 변수를 사용하여 파일 이름과 같은 개체 속성의 고유한 값을 찾을 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

에 대 한 입력을 지정 합니다 `Get-Unique` . 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

이 cmdlet은 **InputObject** 를 사용 하 여 제출한 입력을 컬렉션으로 처리 합니다. 컬렉션의 개별 항목을 열거 하지 않습니다. 컬렉션은 단일 항목 이므로 **InputObject** 를 사용 하 여 제출한 입력은 항상 변경 되지 않은 상태로 반환 됩니다.

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

### -OnType

이 cmdlet은 각 형식의 하나의 개체만 반환 함을 나타냅니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UniqueByType
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

### System.web. PSObject

모든 형식의 개체를로 파이프 할 수 있습니다 `Get-Unique` .

## 출력

### System.web. PSObject

가 반환 하는 개체의 형식은 `Get-Unique` 입력에 의해 결정 됩니다.

## 참고

의 기본 제공 별칭인를 참조할 수도 있습니다 `Get-Unique` `gu` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.

목록을 정렬하려면 Sort-Object를 사용합니다. 의 **unique** 매개 변수를 사용 하 여 `Sort-Object` 목록에서 고유한 항목을 찾을 수도 있습니다.

## 관련 링크

[Select-Object](Select-Object.md)

[Sort-Object](Sort-Object.md)

