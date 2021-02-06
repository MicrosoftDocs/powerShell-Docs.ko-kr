---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-random?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Random
ms.openlocfilehash: 4922124569550012223d441099dc94b228fd93d4
ms.sourcegitcommit: fa1a84c81e15f1ffac962110b0b4c850c1b173a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99601265"
---
# Get-Random

## 개요
난수를 가져오거나 컬렉션에서 개체를 임의로 선택합니다.

## SYNTAX

### RandomNumberParameterSet (기본값)

```
Get-Random [-SetSeed <Int32>] [[-Maximum] <Object>] [-Minimum <Object>] [-Count <Int32>] [<CommonParameters>]
```

### RandomListItemParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Count <Int32>] [<CommonParameters>]
```

### ShuffleParameterSet

```
Get-Random [-SetSeed <Int32>] [-InputObject] <Object[]> [-Shuffle] [<CommonParameters>]
```

## 설명

`Get-Random`Cmdlet은 임의로 선택 된 숫자를 가져옵니다. 개체의 컬렉션을에 제출 하면 `Get-Random` 컬렉션에서 임의로 선택 된 개체를 하나 이상 가져옵니다.

매개 변수 또는 입력을 사용 하지 않으면 `Get-Random` 명령에서 0 (영)과 **int32.maxvalue** (,) 사이의 임의로 선택 된 32 비트의 부호 없는 정수를 반환 `0x7FFFFFFF` `2,147,483,647` 합니다.

기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.

의 매개 변수를 사용 `Get-Random` 하 여 최소값과 최대값, 컬렉션에서 반환 되는 개체 수 또는 초기값을 지정할 수 있습니다.

> [!CAUTION]
> 초기값을 의도적으로 설정 하면 무작위로 반복 되는 동작이 발생 하지 않습니다. 명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .
>
> 이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다. 초기값을 기본값으로 다시 설정할 수 없습니다.

## 예제

### 예제 1: 임의의 정수 가져오기

이 명령은 0에서 **int32.maxvalue** 사이의 임의의 정수를 가져옵니다.

```powershell
Get-Random
```

```Output
3951433
```

### 예제 2:0에서 99 사이의 임의의 정수 가져오기

```powershell
Get-Random -Maximum 100
```

```Output
47
```

### 예 3:-100과 99 사이의 임의의 정수 가져오기

```powershell
Get-Random -Minimum -100 -Maximum 100
```

```Output
56
```

### 예제 4: 임의의 부동 소수점 숫자 가져오기

이 명령은 10.7 이상 20.92 미만인 임의의 부동 소수점 수를 가져옵니다.

```powershell
Get-Random -Minimum 10.7 -Maximum 20.93
```

```Output
18.08467273887
```

### 예 5: 배열에서 임의의 정수 가져오기

이 명령은 지정된 배열에서 임의로 선택된 숫자를 가져옵니다.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random
```

```Output
8
```

### 예제 6: 배열에서 임의의 정수 몇 개 가져오기

이 명령은 임의로 선택 된 세 개의 숫자를 배열에서 임의의 순서로 가져옵니다.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Count 3
```

```Output
3
1
13
```

### 예제 7: 전체 컬렉션 임의화

PowerShell 7.1부터 **무작위 매개 변수를 사용** 하 여 전체 컬렉션을 임의의 순서로 반환할 수 있습니다.

```powershell
1, 2, 3, 5, 8, 13 | Get-Random -Shuffle
```

```Output
2
3
5
1
8
13
```

### 예 8: 숫자가 아닌 임의의 값 가져오기

이 명령은 숫자가 아닌 컬렉션에서 임의의 값을 반환합니다.

```powershell
"red", "yellow", "blue" | Get-Random
```

```Output
yellow
```

### 예 9: SetSeed 매개 변수 사용

이 예제에서는 **SetSeed** 매개 변수를 사용할 경우의 결과를 보여 줍니다.

**Setseed** 는 무작위 동작을 생성 하므로 일반적으로 스크립트를 디버깅 하거나 분석 하는 경우와 같이 결과를 재현 하는 데만 사용 됩니다.

```powershell
# Commands with the default seed are pseudorandom
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

```powershell
# Commands with the same seed are not random
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100 -SetSeed 23
```

```Output
74
74
74
```

```powershell
# SetSeed results in a repeatable series
Get-Random -Maximum 100 -SetSeed 23
Get-Random -Maximum 100
Get-Random -Maximum 100
Get-Random -Maximum 100
```

```Output
74
56
84
46
```

### 예 10: 임의 파일 가져오기

이 명령은 `C:` 로컬 컴퓨터의 드라이브에서 무작위로 선택 된 50 파일 샘플을 가져옵니다.

```powershell
$Files = Get-ChildItem -Path C:\* -Recurse
$Sample = $Files | Get-Random -Count 50
```

### 예 11: 롤 박람회

이 예제는 공평 하 게 1200 시간을 롤백하고 결과를 계산 합니다. 첫 번째 명령은 `ForEach-Object` `Get-Random` 파이프 된 (1-6)에서에 대 한 호출을 반복 합니다. 결과는를 사용 하 여 값으로 그룹화 되 `Group-Object` 고가 있는 테이블로 형식이 지정 됩니다 `Select-Object` .

```powershell
1..1200 | ForEach-Object {
    1..6 | Get-Random
} | Group-Object | Select-Object Name,Count
```

```Output
Name Count
---- -----
1      206
2      199
3      196
4      226
5      185
6      188
```

### 예 12: Count 매개 변수 사용

이제 개체를로 파이프 하지 않고 **Count** 매개 변수를 사용할 수 있습니다 `Get-Random` .
다음 예제에서는 10 보다 작은 세 개의 난수를 가져옵니다.

```powershell
Get-Random -Count 3 -Maximum 10
```

```Output
9
0
8
```

### 예제 13: 빈 문자열이 나 $null를 사용 하 여 InputObject 매개 변수 사용

이 예제에서 **InputObject** 매개 변수는 빈 문자열 () 및를 포함 하는 배열을 지정 합니다 `''` `$null` .

```powershell
Get-Random -InputObject @('a','',$null)
```

`Get-Random` 는 `a` , 빈 문자열 또는을 반환 `$null` 합니다. 빈 문자열는 빈 줄로 표시 되 고 `$null` PowerShell 프롬프트로 돌아갑니다.

## PARAMETERS

### -개수

반환할 임의 개체 또는 숫자의 수를 지정 합니다. 기본값은 1입니다.

에서 사용 하는 경우 `InputObject` **Count** 값이 컬렉션의 개체 수를 초과 하면는 `Get-Random` 임의의 순서로 개체를 모두 반환 합니다.

```yaml
Type: System.Int32
Parameter Sets: RandomNumberParameterSet, RandomListItemParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InputObject

개체 컬렉션을 지정합니다. `Get-Random` 컬렉션에서 **Count** 로 지정 된 수까지 임의로 선택 된 개체를 임의의 순서로 가져옵니다. 개체, 개체가 포함된 변수, 개체를 가져오는 명령 또는 식을 입력하세요. 개체의 컬렉션을로 파이프 할 수도 있습니다 `Get-Random` .

PowerShell 7부터 **InputObject** 매개 변수는 빈 문자열 또는을 포함할 수 있는 배열을 허용 합니다 `$null` . 배열은 파이프라인 또는 **InputObject** 매개 변수 값으로 전송 될 수 있습니다.

```yaml
Type: System.Object[]
Parameter Sets: RandomListItemParameterSet, ShuffleParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -최대

난수의 최대값을 지정합니다. `Get-Random` 는 최대값 (같지 않음) 보다 작은 값을 반환 합니다. 정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다.

**Maximum** 값은 **Minimum** 값보다 커야 하며 같으면 안 됩니다. **Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.

64 비트 컴퓨터에서 **Minimum** 값이 32 비트 정수인 경우 **Maximum** 의 기본값은 **int32.maxvalue** 입니다.

**Minimum** 값이 double (부동 소수점 숫자) 이면 **Maximum** 의 기본값은 **int32.maxvalue** 입니다. 그렇지 않으면 기본값은 **int32.maxvalue** 입니다.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -최소

난수의 최소값을 지정합니다. 정수, 배정밀도 부동 소수점 수 또는 정수 또는 double로 변환할 수 있는 개체 (예: 숫자 문자열 ("100"))를 입력 합니다. 기본값은 0입니다.

**Minimum** 값은 **Maximum** 값보다 작아야 하며 같으면 안 됩니다. **Maximum** 또는 **Minimum** 값이 부동 소수점 숫자인 경우은 `Get-Random` 임의로 선택 된 부동 소수점 숫자를 반환 합니다.

```yaml
Type: System.Object
Parameter Sets: RandomNumberParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SetSeed

난수 생성기의 시드 값을 지정합니다. **Setseed** 를 사용 하는 경우 [cmdlet은 system.string 메서드를](/dotnet/api/system.random) 사용 하 여 암호화 되지 않은 의사 난수를 생성 합니다.

> [!CAUTION]
> 초기값을 설정 하면 불규칙 하지 않은 동작이 발생 합니다. 명령을 포함 하는 스크립트를 디버깅 하거나 분석 하는 경우와 같이 동작을 재현 하려는 경우에만 사용 해야 합니다 `Get-Random` .
>
> 이 초기값은 `Get-Random` **setseed** 를 다시 사용 하거나 세션을 닫을 때까지 현재 명령 및 현재 세션의 모든 후속 명령에 사용 됩니다. 초기값을 기본값으로 다시 설정할 수 없습니다.

```yaml
Type: System.Nullable`1[System.Int32]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -순서 섞기

전체 컬렉션을 임의의 순서로 반환 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ShuffleParameterSet
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

### System.Object

하나 이상의 개체를 파이프 할 수 있습니다. `Get-Random` 파이프 된 개체에서 임의로 값을 선택 합니다.

## 출력

### System.object, system.object, system.string

`Get-Random` 정수 또는 부동 소수점 숫자를 반환 하거나, 전송 된 컬렉션에서 임의로 선택 된 개체를 반환 합니다.

## 참고

기본적으로는 `Get-Random` [RandomNumberGenerator](/dotnet/api/system.security.cryptography.randomnumbergenerator) 클래스를 사용 하 여 암호화 보안 임의성을 생성 합니다.

`Get-Random` 는 항상 입력 값과 동일한 데이터 형식을 반환 하지 않습니다. 다음 표에서는 각 숫자 입력 형식에 대 한 출력 형식을 보여 줍니다.

| 입력 형식 | 출력 형식 |
| :--------: | :---------: |
|   SByte    |   Double    |
|    Byte    |   Double    |
|   Int16    |   Double    |
|   UInt16   |   Double    |
|   Int32    |    Int32    |
|   UInt32   |   Double    |
|   Int64    |    Int64    |
|   UInt64   |   Double    |
|   Double   |   Double    |
|   Single   |   Double    |

Windows PowerShell 3.0부터는 `Get-Random` 64 비트 정수를 지원 합니다. Windows PowerShell 2.0에서는 모든 값이 **system.object** 로 캐스팅 됩니다.

PowerShell 7부터 **RandomListItemParameterSet** 매개 변수 집합의 **InputObject** 매개 변수는 빈 문자열이 나를 포함 하는 배열을 허용 합니다 `$null` . 이전 PowerShell 버전에서는 **RandomNumberParameterSet** 매개 변수 집합의 **Maximum** 매개 변수만 빈 문자열 또는을 수락 `$null` 했습니다.

## 관련 링크

[RandomNumberGenerator ()](/dotnet/api/system.security.cryptography.randomnumbergenerator)

[. 무작위](/dotnet/api/system.random)
