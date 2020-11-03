---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-item?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Item
ms.openlocfilehash: 07f8da5e6101b1d9bb1971b3c77b9747c0080a23
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210481"
---
# Get-Item

## 개요
지정된 위치에 있는 항목을 가져옵니다.

## SYNTAX

### Path (기본값)

```
Get-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

### LiteralPath

```
Get-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Force] [-Credential <PSCredential>] [-Stream <String[]>] [<CommonParameters>]
```

## 설명

`Get-Item`Cmdlet은 지정 된 위치에 있는 항목을 가져옵니다. 와일드 카드 문자 ()를 사용 하 여 `*` 항목의 모든 내용을 요청 하지 않는 한 해당 위치에 있는 항목의 내용을 가져오지 않습니다.

이 cmdlet은 PowerShell 공급자가 여러 유형의 데이터 저장소를 탐색 하는 데 사용 됩니다.

## 예제

### 예 1: 현재 디렉터리 가져오기

이 예제에서는 현재 디렉터리를 가져옵니다. 점 ('. ')은 현재 위치에 있는 항목 (내용 아님)을 나타냅니다.

```powershell
Get-Item .
```

```output
Directory: C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006  10:01 AM            ps-test
```

### 예 2: 현재 디렉터리에 있는 모든 항목 가져오기

이 예제에서는 현재 디렉터리에 있는 모든 항목을 가져옵니다. 와일드 카드 문자 ( `*` )는 현재 항목의 모든 내용을 나타냅니다.

```powershell
Get-Item *
```

```output
Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----         7/26/2006   9:29 AM            Logs
d----         7/26/2006   9:26 AM            Recs
-a---         7/26/2006   9:28 AM         80 date.csv
-a---         7/26/2006  10:01 AM         30 filenoext
-a---         7/26/2006   9:30 AM      11472 process.doc
-a---         7/14/2006  10:47 AM         30 test.txt
```

### 예 3: 드라이브의 현재 디렉터리 가져오기

이 예제에서는 드라이브의 현재 디렉터리를 가져옵니다 `C:` . 검색할 대상 개체는 디렉터리(디렉터리의 내용이 아님)만 나타냅니다.

```powershell
Get-Item C:\
```

### 예제 4: 지정 된 드라이브에서 항목 가져오기

이 예제에서는 드라이브의 항목을 가져옵니다 `C:` . 와일드 카드 문자 ( `*` )는 컨테이너 뿐만 아니라 컨테이너의 모든 항목을 나타냅니다.

```powershell
Get-Item C:\*
```

PowerShell에서 일반적인 대신 단일 별표 ()를 사용 `*` 하 여 콘텐츠를 가져옵니다 `*.*` . 형식은 문자 그대로 해석 되므로 `*.*` 점이 없는 디렉터리나 파일 이름을 검색 하지 못합니다.

### 예 5: 지정 된 디렉터리에서 속성 가져오기

이 예에서는 디렉터리의 **LastAccessTime** 속성을 가져옵니다 `C:\Windows` . **LastAccessTime** 은 파일 시스템 디렉터리의 속성 중 하나에 불과합니다. 디렉터리의 모든 속성을 보려면를 입력 `(Get-Item <directory-name>) | Get-Member` 합니다.

```powershell
(Get-Item C:\Windows).LastAccessTime
```

### 예제 6: 레지스트리 키 내용 표시

이 예제에서는 **Microsoft PowerShell** 레지스트리 키의 내용을 보여 줍니다. PowerShell 레지스트리 공급자와 함께이 cmdlet을 사용 하 여 레지스트리 키와 하위 키를 가져올 수 있지만 cmdlet을 사용 `Get-ItemProperty` 하 여 레지스트리 값과 데이터를 가져와야 합니다.

```powershell
Get-Item HKLM:\Software\Microsoft\Powershell\1\Shellids\Microsoft.Powershell\
```

### 예제 7: 제외 된 디렉터리의 항목 가져오기

이 예제에서는 Windows 디렉터리에서 점 ()이 포함 된 항목 `.` 을 가져오지만로 시작 하지 않는 항목을 가져옵니다 `w*` . 이 예제는 경로에 `*` 항목의 내용을 지정 하는 와일드 카드 문자 ()가 포함 된 경우에만 작동 합니다.

```powershell
Get-Item C:\Windows\*.* -Exclude "w*"
```

### 예 8: hardlink create 정보 가져오기

PowerShell 6.2에서 hardlink create 정보를 가져오기 위해 대체 뷰가 추가 되었습니다. Hardlink create 정보를 가져오려면 출력을로 파이프 합니다. `Format-Table -View childrenWithHardlink`

```powershell
Get-Item -Path C:\PathWhichIsAHardLink | Format-Table -View childrenWithHardlink
```

### 예 9: 실험적 기능 PSUnixFileStat에 대 한 출력

Unix 시스템의 PowerShell 7에서 실험적 기능 **PSUnixFileStat** 는 unix와 비슷한 출력을 제공 합니다.

```powershell
PS> Get-Item /Users
```

```Output
    Directory: /

UnixMode    User  Group   LastWriteTime      Size  Name
--------    ----  -----   -------------      ----  ----
drwxr-xr-x  root  admin   12/20/2019 11:46   192   Users
```

이제 출력의 일부인 새 속성은 다음과 같습니다.

- 모든 수 **x 모드** 는 Unix 시스템에 표시 되는 파일 사용 권한입니다.
- **사용자** 가 파일 소유자입니다.
- **그룹이 그룹 소유자입니다.**
- **크기** 는 Unix 시스템에 표시 되는 파일 또는 디렉터리의 크기입니다.

## PARAMETERS

### -스트림

파일에서 지정된 대체 NTFS 파일 스트림을 가져옵니다. 스트림 이름을 입력합니다. 와일드카드가 지원됩니다. 모든 스트림을 가져오려면 별표 ()를 사용 `*` 합니다. 이 매개 변수는 폴더에서 유효 하지 않습니다.

**스트림은** **파일 시스템** 공급자가 cmdlet에 추가 하는 동적 매개 변수입니다 `Get-Item` .
이 매개 변수는 파일 시스템 드라이브에만 작동합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No alternate file streams
Accept pipeline input: False
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
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -제외

이 cmdlet이 작업에서 제외 하는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Exclude** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [파일 시스템](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터를 지 원하는 유일한 설치 된 PowerShell 공급자입니다. 필터는 다른 매개 변수 보다 더 효율적입니다. 공급자는 검색 된 개체를 PowerShell에서 필터링 하는 대신 개체를 가져올 때 필터를 적용 합니다. 필터 문자열은 파일을 열거 하기 위해 .NET API에 전달 됩니다. API는 `*` 및 `?` 와일드 카드만 지원 합니다.

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

### -Force

이 cmdlet은 숨겨진 항목과 같이 다른 방법으로는 액세스할 수 없는 항목을 가져옵니다.
구현은 공급자에 따라 다릅니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요. **Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -포함

이 cmdlet이 작업에 포함 하는 항목 또는 항목을 문자열 배열로 지정 합니다. 이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예:)을 입력 `*.txt` 합니다. 와일드카드 문자를 사용할 수 있습니다. **Include** 매개 변수는 명령에와 같이 항목의 내용이 포함 된 경우에만 적용 됩니다 `C:\Windows\*` . 여기서 와일드 카드 문자는 디렉터리의 내용을 지정 합니다 `C:\Windows` .

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

### -Path

항목의 경로를 지정합니다. 이 cmdlet은 지정 된 위치에 있는 항목을 가져옵니다. 와일드카드 문자를 사용할 수 있습니다. 이 매개 변수는 필수 이지만 매개 변수 이름 **경로** 는 선택 사항입니다.

점 ()을 사용 `.` 하 여 현재 위치를 지정 합니다. 와일드 카드 문자 ( `*` )를 사용 하 여 현재 위치의 모든 항목을 지정 합니다.

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

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### System.Object

이 cmdlet은 가져오는 개체를 반환 합니다. 경로의 개체 유형에 따라 유형이 결정됩니다.

## 참고

이 cmdlet은 해당 내용이 아닌 항목만 가져오기 때문에 **재귀** 매개 변수가 없습니다.
항목의 내용을 재귀적으로 가져오려면를 사용 `Get-ChildItem` 합니다.

레지스트리를 탐색 하려면이 cmdlet을 사용 하 여 레지스트리 키와 `Get-ItemProperty` 레지스트리 값 및 데이터를 가져옵니다. 레지스트리 값은 레지스트리 키의 속성으로 간주됩니다.
  
이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[Get-ChildItem](Get-ChildItem.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Get-PSProvider](Get-PSProvider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
