---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: b6a8d0f68717849711a794c9482e03d4ea081e1d
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692654"
---
# Get-Content

## 개요
지정된 위치에 있는 항목의 내용을 가져옵니다.

## SYNTAX

### Path (기본값)

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### LiteralPath

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## 설명

`Get-Content`Cmdlet은 파일의 텍스트 또는 함수의 내용과 같이 경로에 지정 된 위치에 있는 항목의 내용을 가져옵니다. 파일의 경우 콘텐츠는 한 번에 한 줄씩 읽고 개체의 컬렉션을 반환 하며, 각 개체는 내용 줄을 나타냅니다.

PowerShell 3.0부터는 `Get-Content` 항목의 시작 또는 끝에서 지정 된 개수의 줄을 가져올 수도 있습니다.

## 예제

### 예제 1: 텍스트 파일의 내용 가져오기

이 예제에서는 현재 디렉터리에 있는 파일의 내용을 가져옵니다. `LineNumbers.txt`파일의 형식에 100 줄이 포함 되어 있습니다 .이 줄은 **X** 이며 여러 예제에서 사용 됩니다.

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

배열 값 1-100은 파이프라인에서 cmdlet으로 전송 됩니다 `ForEach-Object` . `ForEach-Object` cmdlet과 함께 스크립트 블록을 사용 하 여 `Add-Content` 파일을 만듭니다 `LineNumbers.txt` . 변수는 `$_` 각 개체가 파이프라인 아래로 전송 될 때 배열 값을 나타냅니다. `Get-Content`Cmdlet은 **Path** 매개 변수를 사용 하 여 파일을 지정 하 `LineNumbers.txt` 고 PowerShell 콘솔에 콘텐츠를 표시 합니다.

### 예 2: 반환 Get-Content 줄 수 제한

이 명령은 파일의 처음 5 개 줄을 가져옵니다. **TotalCount** 매개 변수는 처음 5 개 줄의 콘텐츠를 가져오는 데 사용 됩니다. 이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### 예제 3: 텍스트 파일에서 특정 콘텐츠 줄 가져오기

이 명령은 파일에서 특정 개수의 줄을 가져온 다음 해당 콘텐츠의 마지막 줄만 표시 합니다. **TotalCount** 매개 변수는 처음 25 줄의 콘텐츠를 가져옵니다. 이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

`Get-Content`다음 단계로 이동 하기 전에 명령이 완료 되도록 괄호 안에 명령이 래핑됩니다. `Get-Content`줄의 배열을 반환 합니다 .이를 통해 괄호 뒤에 인덱스 표기법을 추가 하 여 특정 줄 번호를 검색할 수 있습니다. 이 경우 `[-1]` 인덱스는 검색 된 줄 25 개 줄의 반환 된 배열에서 마지막 인덱스를 지정 합니다.

### 예제 4: 텍스트 파일의 마지막 줄 가져오기

이 명령은 파일의 첫 번째 줄과 마지막 내용의 줄을 가져옵니다. 이 예에서는 `LineNumbers.txt` 예 1에서 만든 파일을 사용 합니다.

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

이 예제에서는 cmdlet을 사용 하 여 `Get-Item` 파일을 매개 변수로 파이프 할 수 있음을 보여 줍니다 `Get-Content` . **Tail** 매개 변수는 파일의 마지막 줄을 가져옵니다. 이 메서드는 모든 줄을 검색 하 고 인덱스 표기법을 사용 하는 것 보다 빠릅니다 `[-1]` .

### 예 5: 대체 데이터 스트림의 내용 가져오기

이 예에서는 **Stream** 매개 변수를 사용 하 여 Windows NTFS 볼륨에 저장 된 파일에 대 한 대체 데이터 스트림의 내용을 가져오는 방법을 설명 합니다. 이 예제에서는 cmdlet을 `Set-Content` 사용 하 여 라는 파일에 샘플 콘텐츠를 만듭니다 `Stream.txt` .

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

**Stream** 매개 변수는 [FileSystem 공급자](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring)의 동적 매개 변수입니다.
기본적으로는 `Get-Content` 기본 또는 스트림에서 데이터만 검색 `:$DATA` 합니다. **스트림은** 특성, 보안 설정 또는 기타 데이터와 같은 숨겨진 데이터를 저장 하는 데 사용할 수 있습니다. 자식 항목을 포함 하지 않고 디렉터리에 저장할 수도 있습니다.

### 예제 6: 원시 콘텐츠 가져오기

이 예제의 명령은 문자열 배열 대신 파일의 내용을 하나의 문자열로 가져옵니다. 기본적으로 **원시** 동적 매개 변수를 사용 하지 않으면 콘텐츠는 줄 바꿈 구분 문자열의 배열로 반환 됩니다. 이 예제에서는 `LineNumbers.txt` 예제에서 만든 파일을 사용 합니다.
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### 예 7: Get-Content에서 필터 사용

Cmdlet에 대 한 필터를 지정할 수 있습니다 `Get-Content` . 필터를 사용 하 여 **path** 매개 변수를 한 정하는 경우 후행 별표 ()를 포함 하 여 `*` 경로의 내용을 나타내야 합니다.

다음 명령은 `*.log` 디렉터리에 있는 모든 파일의 내용을 가져옵니다 `C:\Temp` .

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### 예 8: 파일 콘텐츠를 바이트 배열로 가져오기

이 예제에서는 파일의 내용을 단일 개체로 가져오는 방법을 보여 줍니다 `[byte[]]` .

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

첫 번째 명령은 **AsByteStream** 매개 변수를 사용 하 여 파일에서 바이트 스트림을 가져옵니다.
**원시** 매개 변수는 바이트가로 반환 되도록 `[System.Byte[]]` 합니다. **원시** 매개 변수가 없는 경우 반환 값은 바이트 스트림으로 서 PowerShell에서로 해석 됩니다 `[System.Object[]]` .

## PARAMETERS

### -Path

가 콘텐츠를 가져오는 항목의 경로를 지정 합니다 `Get-Content` . 와일드카드 문자를 사용할 수 있습니다. 경로는 컨테이너가 아니라 항목의 경로여야 합니다. 예를 들어 디렉터리의 경로가 아니라 하나 이상의 파일 경로를 지정해야 합니다.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

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

### -ReadCount

파이프라인을 통해 한 번에 보낼 내용의 줄 수를 지정합니다. 기본값은 1입니다.
값 0은 한 번에 모든 내용을 보냅니다.

이 매개 변수는 표시되는 내용을 변경하는 대신 내용을 표시하는 데 걸리는 시간에 영향을 줍니다. **ReadCount** 값이 증가하면 첫 번째 줄을 반환하는 데 걸리는 시간이 증가하지만 전체 작업 시간은 감소합니다. 이렇게 하면 큰 항목에 크게 차이가 있을 수 있습니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -TotalCount

파일이 나 다른 항목의 시작 부분에서 줄 수를 지정 합니다. 기본값은 -1(모든 줄)입니다.

**TotalCount** 매개 변수 이름 또는 해당 별칭 ( **First** 또는 **Head**)을 사용할 수 있습니다.

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Tail

파일이 나 다른 항목의 끝에서 줄 수를 지정 합니다. **Tail** 매개 변수 이름 또는 해당 별칭 ( **Last**)을 사용할 수 있습니다. 이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Filter

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다. [About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.
필터는 다른 매개 변수 보다 더 효율적입니다. cmdlet이 개체가 검색 된 후 개체를 필터링 하는 대신 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

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

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `"*.txt"` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다.

경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다.
와일드카드 문자를 사용할 수 있습니다.

**Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

### -Force

**Force** 는 읽기 전용 특성을 재정의 하거나 디렉터리를 만들어 파일 경로를 완성 합니다. **Force** 매개 변수는 파일 사용 권한을 변경 하거나 보안 제한을 재정의 하려고 하지 않습니다.

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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -구분 기호

`Get-Content`에서 읽는 동안 파일을 개체로 나누는 데 사용 하는 구분 기호를 지정 합니다. 기본값은 `\n` 줄 끝 문자입니다. 텍스트 파일을 읽을 때는 `Get-Content` 각각 줄 끝 문자로 끝나는 문자열 개체의 컬렉션을 반환 합니다. 파일에 존재 하지 않는 구분 기호를 입력 하면는 `Get-Content` 전체 파일을 구분 되지 않은 단일 개체로 반환 합니다.

이 매개 변수를 사용 하 여 파일 구분 기호를 구분 기호로 지정 하 여 많은 파일을 더 작은 파일로 분할할 수 있습니다. 구분 기호는 보존되고(삭제되지 않음) 각 파일 섹션의 마지막 항목이 됩니다.

**Delimiter** 는 **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

> [!NOTE]
> 현재 **구분 기호** 매개 변수 값이 빈 문자열인 경우는 `Get-Content` 아무것도 반환 하지 않습니다. 이것은 알려진 문제입니다. 를 적용 하 여 `Get-Content` 전체 파일을 구분 되지 않은 단일 문자열로 반환 합니다. 파일에 존재 하지 않는 값을 입력 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### -Wait

모든 기존 줄이 출력 된 후 파일을 열어 둡니다. 대기 하는 동안는 `Get-Content` 초당 파일을 확인 하 고 새 줄 (있는 경우)을 출력 합니다. **Ctrl + C** 를 눌러 **Wait** 를 중단할 수 있습니다. 파일이 삭제 되 면 대기가 종료 되 고,이 경우 종료 되지 않는 오류가 보고 됩니다.

**Wait** 는 파일 시스템 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` . 이 매개 변수는 파일 시스템 드라이브에만 작동합니다. **Wait** 는 **Raw** 와 함께 사용할 수 없습니다.

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

### -Raw

줄 바꿈 문자를 무시 하 고 줄바꿈가 유지 된 상태로 파일의 전체 내용을 하나의 문자열로 반환 합니다. 기본적으로 파일의 줄 바꿈 문자는 입력을 문자열 배열로 구분 하는 구분 기호로 사용 됩니다. 이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.

**Raw** 는 **FileSystem** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .이 매개 변수는 파일 시스템 드라이브 에서만 작동 합니다.

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

### -Encoding

대상 파일의 인코딩 유형을 지정합니다. 기본값은 `utf8NoBOM`입니다.

이 매개 변수에 허용 되는 값은 다음과 같습니다.

- `ascii`: ASCII (7 비트) 문자 집합에 대 한 인코딩을 사용 합니다.
- `bigendianunicode`: 빅 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `bigendianutf32`: 빅 endian 바이트 순서를 사용 하 여 u t f-32 형식으로 인코딩합니다.
- `oem`: MS-DOS 및 콘솔 프로그램에 기본 인코딩을 사용 합니다.
- `unicode`: 작은 endian 바이트 순서를 사용 하 여 UTF-16 형식으로 인코딩합니다.
- `utf7`: UTF-7 형식으로 인코딩합니다.
- `utf8`: UTF-8 형식으로 인코딩합니다.
- `utf8BOM`: 바이트 순서 표시 (BOM)를 사용 하 여 UTF-8 형식으로 인코딩합니다.
- `utf8NoBOM`: BOM (바이트 순서 표시) 없이 UTF-8 형식으로 인코딩합니다.
- `utf32`: U t f-32 형식으로 인코딩합니다.

Encoding은 **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .
이 매개 변수는 파일 시스템 드라이브 에서만 사용할 수 있습니다.

이진 파일을 읽고 이진 파일에 쓸 때 **AsByteStream** 매개 변수를 사용 하 고 **readcount** 매개 변수에 0 값을 사용 합니다. **Readcount** 값이 0 이면 단일 읽기 작업에서 전체 파일을 읽습니다. 기본 **Readcount** 값인 1은 각 읽기 작업에서 1 바이트를 읽고 각 바이트를 별도의 개체로 변환 합니다. 이렇게 하면 `Set-Content` **AsByteStream** 매개 변수를 사용 하지 않는 한 cmdlet을 사용 하 여 파일에 바이트를 쓸 때 오류가 발생 합니다.

PowerShell 6.2부터 **Encoding** 매개 변수를 사용 하 여 등록 된 코드 페이지의 숫자 id (예: `-Encoding 1251` ) 또는 등록 된 코드 페이지의 문자열 이름을 사용할 수도 있습니다 (예: `-Encoding "windows-1251"` ). 자세한 내용은 [인코딩에](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2)대 한 .net 설명서를 참조 하세요.

> [!NOTE]
> **U t f-7** _은 더 이상 사용 하지 않는 것이 좋습니다. PowerShell 7.1에서는 `utf7` _ *Encoding** 매개 변수에 대해를 지정 하는 경우 경고가 기록 됩니다.

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### -스트림

> [!NOTE]
> 이 매개 변수는 Windows 에서만 사용할 수 있습니다.

파일에서 지정된 대체 NTFS 파일 스트림의 내용을 가져옵니다. 스트림 이름을 입력합니다.
와일드카드는 지원되지 않습니다.

**스트림은** **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Content` .
이 매개 변수는 Windows 시스템의 파일 시스템 드라이브 에서만 작동 합니다. 이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsByteStream

콘텐츠를 바이트 스트림으로 읽도록 지정 합니다. **AsByteStream** 매개 변수는 Windows PowerShell 6.0에서 도입 되었습니다.

**AsByteStream** 매개 변수를 **Encoding** 매개 변수와 함께 사용 하는 경우 경고가 발생 합니다. **AsByteStream** 매개 변수는 인코딩을 무시 하 고 출력은 바이트 스트림으로 반환 됩니다.

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

### System.Int64, System.String[], System.Management.Automation.PSCredential

읽기 수, 총 개수, 경로 또는 자격 증명을로 파이프 할 수 있습니다 `Get-Content` .

## 출력

### System.string, System.string

`Get-Content` 문자열 또는 바이트를 반환 합니다. 출력 형식은 입력으로 지정 하는 콘텐츠 형식에 따라 달라 집니다.

## 참고

`Get-Content`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 공급자를 가져오려면 cmdlet을 사용 합니다 `Get-PSProvider` . 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Add-Content](Add-Content.md)

[Clear-Content](Clear-Content.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-PSProvider](Get-PSProvider.md)

[Set-Content](Set-Content.md)
