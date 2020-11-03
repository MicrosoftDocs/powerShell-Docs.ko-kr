---
description: '`enum`문은 열거형을 선언 하는 데 사용 됩니다. 열거형은 열거자 목록 이라고 하는 명명 된 레이블 집합으로 구성 된 고유 형식입니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/27/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_enum?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Enum
ms.openlocfilehash: 9cd4f60db2903bc4ede6b0c3ad738b3137b87191
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223882"
---
# <a name="about-enum"></a>열거형 정보

## <a name="short-description"></a>간단한 설명
`enum`문은 열거형을 선언 하는 데 사용 됩니다. 열거형은 열거자 목록 이라고 하는 명명 된 레이블 집합으로 구성 된 고유 형식입니다.

## <a name="long-description"></a>자세한 설명

`enum`문을 사용 하면 강력한 형식의 레이블 집합을 만들 수 있습니다. 이 열거형은 맞춤법 오류를 구문 분석 하거나 확인 하지 않고도 코드에서 사용할 수 있습니다.

열거형은 내부적으로 시작 값이 0 인 정수로 표시 됩니다. 목록의 첫 번째 레이블에 값 0이 할당 됩니다. 나머지 레이블은 연속 숫자를 사용 하 여 할당 됩니다.

정의에서 레이블에는 임의의 정수 값이 지정 될 수 있습니다. 할당 된 값이 없는 레이블은 다음 정수 값을 사용 합니다.

## <a name="syntax-basic"></a>구문 (기본)

```syntax
enum <enum-name> {
    <label> [= <int-value>]
    ...
}
```

## <a name="usage-example"></a>사용 예제

다음 예제에서는 미디어 파일로 볼 수 있는 개체의 열거형을 보여 줍니다. 정의는,,의 내부 값에 명시적 값을 할당 합니다 `music` `picture` `video` . 명시적 할당 바로 다음에 오는 레이블은 다음 정수 값을 가져옵니다. 동의어는 다른 레이블에 같은 값을 할당 하 여 만들 수 있습니다. 에 대해 생성 된 값,, 또는를 참조 하십시오 `ogg` `oga` `mogg` `jpg` `jpeg` `mpg` `mpeg` .

```powershell
enum MediaTypes {
    unknown
    music = 10
    mp3
    aac
    ogg = 15
    oga = 15
    mogg = 15
    picture = 20
    jpg
    jpeg = 21
    png
    video = 40
    mpg
    mpeg = 41
    avi
    m4v
}
```

`GetEnumNames()`메서드는 열거형의 레이블 목록을 반환 합니다.

```powershell
[MediaTypes].GetEnumNames()
unknown
music
mp3
aac
ogg
oga
mogg
picture
jpg
jpeg
png
video
mpg
mpeg
avi
m4v
```

`GetEnumValues()`메서드는 열거형 값 목록을 반환 합니다.

```powershell
[MediaTypes].GetEnumValues()
unknown
music
mp3
aac
oga
oga
oga
picture
jpeg
jpeg
png
video
mpeg
mpeg
avi
m4v
```

**참고** : getenumnames () 및 Getenumnames ()는 동일한 결과를 반환 하는 것 처럼 보입니다.
그러나 내부적으로 PowerShell은 값을 레이블로 변경 합니다. 목록을 신중 하 게 읽으면 `oga` 및 `mogg` 가 ' 이름 가져오기 ' 결과 아래에 설명 되어 있지만,, 및에 대 한 유사한 출력에는 표시 되지 않습니다 `jpg` `jpeg` `mpg` `mpeg` .

```powershell
[MediaTypes].GetEnumName(15)
oga

[MediaTypes].GetEnumNames() | ForEach-Object {
  "{0,-10} {1}" -f $_,[int]([MediaTypes]::$_)
}
unknown    0
music      10
mp3        11
aac        12
ogg        15
oga        15
mogg       15
picture    20
jpg        21
jpeg       21
png        22
video      40
mpg        41
mpeg       41
avi        42
m4v        43
```

## <a name="enumerations-as-flags"></a>플래그로 열거형

열거형은 비트 플래그의 컬렉션으로 정의 될 수 있습니다.
여기서, 지정 된 지점에서 열거형은 하나 이상의 해당 플래그를 설정 하는 것을 나타냅니다.

제대로 작동 하는 플래그를 나타내는 열거형의 경우 각 레이블의 값이 2의 거듭제곱 이어야 합니다.

## <a name="syntax-flags"></a>구문 (flags)

```syntax
[Flags()] enum <enum-name> {
    <label 0> [= 1]
    <label 1> [= 2]
    <label 2> [= 4]
    <label 3> [= 8]
    ...
}
```

## <a name="flags-usage-example"></a>Flags 사용 예

다음 예에서는 *Fileattributes* 열거형을 만듭니다.

```powershell
[Flags()] enum FileAttributes {
    Archive = 1
    Compressed = 2
    Device = 4
    Directory = 8
    Encrypted = 16
    Hidden = 32
}

[FileAttributes]$file1 = [FileAttributes]::Archive
[FileAttributes]$file1 +=[FileAttributes]::Compressed
[FileAttributes]$file1 +=  [FileAttributes]::Device
"file1 attributes are: $file1"

[FileAttributes]$file2 = [FileAttributes]28 ## => 16 + 8 + 4
"file2 attributes are: $file2"
```

```output
file1 attributes are: Archive, Compressed, Device
file2 attributes are: Device, Directory, Encrypted
```

특정가 설정 되었는지 테스트 하려면 이진 비교 연산자를 사용할 수 있습니다 `-band` . 이 예제에서는의 값에 있는 **장치** 및 **보관** 특성을 테스트 합니다 `$file2` .

```
PS > ($file2 -band [FileAttributes]::Device) -eq [FileAttributes]::Device
True

PS > ($file2 -band [FileAttributes]::Archive) -eq [FileAttributes]::Archive
False
```
