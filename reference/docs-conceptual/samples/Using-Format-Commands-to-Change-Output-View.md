---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 형식 명령을 사용하여 출력 보기 변경
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: fba37b1d0479bf605d8f2171da27cd1bceb9976e
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293047"
---
# <a name="using-format-commands-to-change-output-view"></a>형식 명령을 사용하여 출력 보기 변경

Windows PowerShell에는 특정 개체에 대해 표시할 속성을 제어할 수 있는 일련의 cmdlet이 있습니다. 이러한 cmdlet의 이름은 모두 동사 **Format**으로 시작되며, 표시할 속성을 하나 이상 선택하는 데 사용할 수 있습니다.

**Format** cmdlet으로는 **Format-Wide**, **Format-List**, **Format-Table** 및 **Format-Custom**이 있습니다. 이 사용자 가이드에서는 **Format-Wide**, **Format-List** 및 **Format-Table** cmdlet에 대해서만 설명합니다.

각 Format cmdlet에는 표시할 특정 속성을 지정하지 않을 경우 사용되는 기본 속성이 있습니다. 또한 각 cmdlet은 동일한 매개 변수 이름인 **Property**를 사용하여 표시할 속성을 지정합니다. **Format-Wide**는 하나의 속성만 표시하기 때문에 해당 **Property** 매개 변수가 하나의 값만 사용하지만 **Format-List** 및 **Format-Table**의 Property 매개 변수는 속성 이름 목록을 사용합니다.

실행 중인 두 개의 Windows PowerShell 인스턴스에 **Get-Process -Name powershell** 명령을 사용하면 다음과 같은 내용이 출력됩니다.

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

이 섹션의 나머지 부분에서는 **Format** cmdlet을 사용하여 이 명령 출력의 표시 방법을 변경하는 방법을 설명합니다.

## <a name="using-format-wide-for-single-item-output"></a>Format-Wide를 사용하여 단일 항목 출력

기본적으로 `Format-Wide` cmdlet은 개체의 기본 속성만 표시합니다.
다음과 같이 각 개체와 연결된 정보는 하나의 열에 표시됩니다.

```powershell
Get-Command -Verb Format | Format-Wide
```

```output
Format-Custom                          Format-Hex
Format-List                            Format-Table
Format-Wide
```

다음과 같이 기본 속성이 아닌 속성을 지정할 수도 있습니다.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```output
Custom                                 Hex
List                                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a>열이 포함된 Format-Wide 표시 제어

`Format-Wide` cmdlet을 사용하면 한 번에 하나의 속성만 표시할 수 있습니다.
이 cmdlet은 한 줄에 하나의 요소만 표시되는 간단한 목록을 표시하는 데 유용합니다.
간단한 목록을 표시하려면 다음과 같이 입력하여 **Column** 매개 변수의 값을 1로 설정합니다.

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

## <a name="using-format-list-for-a-list-view"></a>Format-List를 사용하여 목록 보기

**Format-List** cmdlet은 다음과 같이 각 속성에 레이블이 지정되어 있고 이러한 각 속성이 별도의 줄에 표시되는 목록 형식으로 개체를 표시합니다.

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

다음과 같이 속성을 원하는 대로 지정할 수 있습니다.

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a>와일드카드와 함께 Format-List를 사용하여 자세한 정보 보기

**Format-List** cmdlet을 사용하면 와일드카드를 해당 **Property** 매개 변수의 값으로 사용할 수 있습니다. 이 경우 자세한 정보를 표시할 수 있습니다. 필요한 것보다 많은 정보가 개체에 포함되는 경우가 종종 있는데, 이는 Windows PowerShell이 기본적으로 모든 속성 값을 표시하지 않기 때문입니다. 개체의 속성을 모두 표시하려면 **Format-List -Property \&#42;** 명령을 사용합니다. 다음 명령은 단일 프로세스의 출력을 위해 60개 이상의 줄을 생성합니다.

```powershell
Get-Process -Name powershell | Format-List -Property *
```

**Format-List** 명령은 자세한 정보를 표시하는 데 유용하지만 많은 항목의 개요를 출력하려는 경우에는 대개 간단한 표 형식의 보기가 더 유용합니다.

## <a name="using-format-table-for-tabular-output"></a>Format-Table을 사용하여 표 형식으로 출력

속성 이름이 지정되지 않은 **Format-Table** cmdlet을 사용하여 **Get-Process** 명령의 출력 형식을 지정하면 형식을 지정하지 않고 이와 같은 작업을 수행할 때와 똑같은 내용이 출력됩니다. 그 이유는 대부분의 Windows PowerShell 개체와 마찬가지로 프로세스도 대개 표 형식으로 표시되기 때문입니다.

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

### <a name="improving-format-table-output-autosize"></a>Format-Table 출력 향상(AutoSize)

표 형식의 보기는 비교 가능한 많은 정보를 표시하는 데 유용하지만 열이 너무 좁아 데이터를 모두 표시할 수 없는 경우에는 정보를 해석하기 어려울 수 있습니다. 예를 들어 프로세스의 Path, ID, Name 및 Company를 표시하려고 하면 다음과 같이 프로세스의 Path 열과 Company 열의 출력이 잘립니다.

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

**Format-Table** 명령을 실행할 때 **AutoSize** 매개 변수를 지정하면 Windows PowerShell은 표시할 실제 데이터를 기준으로 열 너비를 계산합니다. 이렇게 하면 다음과 같이 **Path** 열은 읽을 수 있지만 Company 열은 여전히 잘린 채로 있습니다.

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

**Format-Table** cmdlet을 실행하면 여전히 데이터가 잘릴 수 있지만 화면 끝에 있는 데이터만 잘립니다. 마지막으로 표시되는 속성을 제외하고 속성에는 가장 긴 데이터 요소를 올바로 표시하는 데 필요한 충분한 크기가 지정됩니다. **Property** 값 목록에서 **Path**와 **Company**의 위치를 바꾸면 회사 이름은 보이지만 경로는 잘립니다.

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

**Format-Table** 명령은 속성 목록의 시작 부분에 더 가까이 있을수록 더 중요한 속성으로 간주하고 시작 부분에 가장 가까이 있는 속성을 완전히 표시하려고 합니다. **Format-Table** 명령은 속성을 모두 표시할 수 없는 경우 일부 열을 표시에서 제거하고 경고를 표시합니다. 다음과 같이 **Name**을 목록의 마지막 속성으로 지정하면 이 동작을 재현할 수 있습니다.

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

위의 출력에서는 목록에 맞게 조정하기 위해 ID 열이 잘리고 해당 열 머리글이 두 줄로 표시됩니다. 열 크기를 자동으로 조정해도 항상 원하는 대로 표시되지는 않습니다.

### <a name="wrapping-format-table-output-in-columns-wrap"></a>열에 Format-Table 출력 래핑(Wrap)

**Wrap** 매개 변수를 사용하여 긴 **Format-Table** 데이터를 해당 열 안에서 래핑할 수 있습니다. 다음과 같이 **Wrap** 매개 변수를 단독으로 사용하는 경우에도 **AutoSize**를 지정하지 않으면 기본 설정이 사용되기 때문에 예상되는 작업을 수행하지 않아도 됩니다.

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

**Wrap** 매개 변수를 단독으로 사용하면 프로세스 속도가 크게 느려지지 않는다는 이점이 있습니다. 큰 디렉터리 시스템의 파일을 반복해서 표시할 때 **AutoSize**를 사용하면 첫 번째 출력 항목을 표시할 때까지 매우 많은 시간이 걸리고 많은 메모리가 사용될 수 있습니다.

시스템 로드에 신경 쓰지 않아도 되는 경우에는 **AutoSize**가 **Wrap** 매개 변수와 함께 잘 작동합니다. **Wrap** 매개 변수 없이 **AutoSize**를 지정한 경우와 같이 초기 열에는 항상 하나의 줄에 항목을 표시하는 데 필요한 충분한 너비가 할당됩니다. 유일한 차이점은 다음과 같이 마지막 열이 필요에 따라 래핑된다는 것입니다.

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

가장 긴 열을 가장 먼저 지정하면 일부 열이 표시되지 않을 수 있으므로 가장 작은 데이터 요소를 가장 먼저 지정하는 것이 안전합니다. 다음 예제에서는 매우 긴 경로 요소를 가장 먼저 지정했기 때문에 래핑을 사용했지만 최종 **Name** 열이 여전히 표시되지 않습니다.

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

### <a name="organizing-table-output--groupby"></a>표 형식의 출력 구성(-GroupBy)

표 형식의 출력을 제어하는 데 사용할 수 있는 또 다른 유용한 매개 변수는 **GroupBy**입니다. 특히 긴 표 형식의 목록은 비교하기 어려울 수 있지만 **GroupBy** 매개 변수를 사용하면 속성 값을 기준으로 출력을 그룹화할 수 있습니다. 예를 들어 다음과 같이 프로세스를 더 쉽게 검사하기 위해 속성 목록에서 회사 값을 제거하여 해당 프로세스를 회사별로 그룹화할 수 있습니다.

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```