---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-childitem?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-ChildItem
ms.openlocfilehash: c29a938fc73b8b69ea1bbf96f12f5d42d16f79bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217658"
---
# Get-ChildItem

## 개요

하나 이상의 지정된 위치에서 항목 및 하위 항목을 가져옵니다.

## SYNTAX

### Items (기본값)

```
Get-ChildItem [[-Path] <string[]>] [[-Filter] <string>] [-Include <string[]>] [-Exclude <string[]>]
 [-Recurse] [-Depth <uint32>] [-Force] [-Name] [-Attributes <FlagsExpression[FileAttributes]>]
 [-FollowSymlink] [-Directory] [-File] [-Hidden] [-ReadOnly] [-System] [<CommonParameters>]
```

### LiteralItems

```
Get-ChildItem [[-Filter] <string>] -LiteralPath <string[]> [-Include <string[]>]
 [-Exclude <string[]>] [-Recurse] [-Depth <uint32>] [-Force] [-Name]
 [-Attributes <FlagsExpression[FileAttributes]>] [-FollowSymlink] [-Directory] [-File] [-Hidden]
 [-ReadOnly] [-System] [<CommonParameters>]
```

## 설명

`Get-ChildItem`Cmdlet은 하나 이상의 지정 된 위치에 있는 항목을 가져옵니다. 항목이 컨테이너인 경우 컨테이너 내에 있는 항목(하위 항목)을 가져옵니다. **재귀** 매개 변수를 사용 하 여 모든 자식 컨테이너의 항목을 가져오고 **Depth** 매개 변수를 사용 하 여 수준 수를 재귀적으로 제한할 수 있습니다.

`Get-ChildItem` 빈 디렉터리를 표시 하지 않습니다. 명령에 `Get-ChildItem` **Depth** 또는 **재귀** 매개 변수가 포함 되어 있으면 빈 디렉터리가 출력에 포함 되지 않습니다.

위치는 `Get-ChildItem` PowerShell 공급자가에 노출 합니다. 위치는 파일 시스템 디렉터리, 레지스트리 하이브 또는 인증서 저장소 일 수 있습니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 예제

### 예제 1: 파일 시스템 디렉터리에서 자식 항목 가져오기

이 예제에서는 파일 시스템 디렉터리에서 자식 항목을 가져옵니다. 파일 이름 및 하위 디렉터리 이름이 표시 됩니다. 빈 위치의 경우 명령이 출력을 반환 하지 않고 PowerShell 프롬프트로 돌아갑니다.

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test` .
`Get-ChildItem` PowerShell 콘솔에서 파일 및 디렉터리를 표시 합니다.

```powershell
Get-ChildItem -Path C:\Test
```

```Output
   Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     08:29                Logs
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

기본적으로 `Get-ChildItem` 는 모드 ( **특성** ), **LastWriteTime** , 파일 크기 ( **길이** ) 및 항목의 **이름을** 나열 합니다. **Mode** 속성의 문자는 다음과 같이 해석 될 수 있습니다.

- `l` 링크나
- `d` 디렉터리나
- `a` 보관
- `r` (읽기 전용)
- `h` 은선제거
- `s` (시스템).

모드 플래그에 대 한 자세한 내용은 [about_Filesystem_Provider](../microsoft.powershell.core/about/about_filesystem_provider.md#attributes-flagsexpression)를 참조 하세요.

### 예제 2: 디렉터리에서 자식 항목 이름 가져오기

이 예제에서는 디렉터리에 있는 항목의 이름만 나열 합니다.

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test` . **Name** 매개 변수는 지정 된 경로에서 파일 또는 디렉터리 이름만 반환 합니다.

```powershell
Get-ChildItem -Path C:\Test -Name
```

```Output
Logs
anotherfile.txt
Command.txt
CreateTestFile.ps1
ReadOnlyFile.txt
```

### 예제 3: 현재 디렉터리 및 하위 디렉터리의 자식 항목 가져오기

이 예제에서는 현재 디렉터리와 해당 하위 디렉터리에 있는 .txt 파일을 표시 **합니다** .

```powershell
Get-ChildItem -Path C:\Test\*.txt -Recurse -Force
```

```Output
    Directory: C:\Test\Logs\Adirectory

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile4.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile4.txt

    Directory: C:\Test\Logs\Backup

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 ATextFile.txt
-a----        2/12/2019     15:50             20 LogFile3.txt

    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/12/2019     16:16             20 Afile.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a-h--        2/12/2019     15:52             22 hiddenfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여를 지정 `C:\Test\*.txt` 합니다. **Path** 는 별표 ( `*` ) 와일드 카드를 사용 하 여 파일 이름 확장명을 가진 모든 파일을 지정 `.txt` 합니다. **재귀** 매개 변수는 **디렉터리:** 제목에 표시 된 것 처럼 **경로** 디렉터리에서 해당 하위 디렉터리를 검색 합니다. **Force** 매개 변수는 모드가 h 인 등의 숨겨진 파일을 표시 합니다 `hiddenfile.txt` . **h**

### 예제 4: Include 매개 변수를 사용 하 여 자식 항목 가져오기

이 예에서는 `Get-ChildItem` **Include** 매개 변수를 사용 하 여 **Path** 매개 변수로 지정 된 디렉터리에서 특정 항목을 찾습니다.

```powershell
# When using the -Include parameter, if you don't include an asterisk in the path
# the command returns no output.
Get-ChildItem -Path C:\Test\ -Include *.txt
```

```Output

```

```powershell
Get-ChildItem -Path C:\Test\* -Include *.txt
```

```Output
    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **C:\Test** 디렉터리를 지정 합니다. **Path** 매개 변수에는 `*` 디렉터리의 내용을 지정 하는 후행 별표 () 와일드 카드가 포함 되어 있습니다.
**Include** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 파일 확장명이 **.txt** 인 모든 파일을 지정 합니다.

**Include** 매개 변수를 사용 하는 경우 **경로** 매개 변수는 후행 별표 ( `*` ) 와일드 카드를 사용 하 여 디렉터리의 내용을 지정 해야 합니다. 예들 들어 `-Path C:\Test\*`입니다.

- **재귀** 매개 변수를 명령에 추가 하는 경우 `*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다. **재귀** 매개 변수는 **Path** 디렉터리와 해당 하위 디렉터리에서 항목을 가져옵니다. 예를 들어 `-Path C:\Test\ -Recurse -Include *.txt`
- 후행 별표 ()가 `*` **Path** 매개 변수에 포함 되지 않은 경우 명령이 출력을 반환 하지 않고 PowerShell 프롬프트로 돌아갑니다. 예들 들어 `-Path C:\Test\`입니다.

### 예 5: Exclude 매개 변수를 사용 하 여 자식 항목 가져오기

예제의 출력은 디렉터리 **C:\Test\Logs** 의 내용을 보여 줍니다. 출력은 **Exclude** 및 **재귀** 매개 변수를 사용 하는 다른 명령에 대 한 참조입니다.

```powershell
Get-ChildItem -Path C:\Test\Logs
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Adirectory
d-----        2/15/2019     08:28                AnEmptyDirectory
d-----        2/15/2019     13:21                Backup
-a----        2/12/2019     16:16             20 Afile.txt
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

```powershell
Get-ChildItem -Path C:\Test\Logs\* -Exclude A*
```

```Output
    Directory: C:\Test\Logs

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/15/2019     13:21                Backup
-a----        2/13/2019     13:26             20 LogFile1.txt
-a----        2/12/2019     16:24             23 systemlog1.log
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 디렉터리를 지정 합니다 `C:\Test\Logs` .
**Exclude** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 또는로 시작 하는 **A** 파일 또는 **a** 디렉터리를 출력에서 제외 합니다.

**Exclude** 매개 변수를 사용 하는 경우 `*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다. 예를 들어 `-Path C:\Test\Logs` 또는 `-Path C:\Test\Logs\*`입니다.

- 후행 별표 ()가 `*` **path** 매개 변수에 포함 되지 않은 경우 **path** 매개 변수의 내용이 표시 됩니다. 예외는 **Exclude** 매개 변수의 값과 일치 하는 파일 이름 또는 하위 디렉터리 이름입니다.
- `*` **Path** 매개 변수에 후행 별표 ()가 포함 된 경우이 명령은 **path** 매개 변수의 하위 디렉터리에 루트로 합니다. 예외는 **Exclude** 매개 변수의 값과 일치 하는 파일 이름 또는 하위 디렉터리 이름입니다.
- **재귀 매개 변수가** 명령에 추가 되 면 **Path** 매개 변수에 후행 별표 ()가 포함 되어 있는지 여부에 관계 없이 재귀 출력이 동일 합니다 `*` .

### 예제 6: 레지스트리 하이브에 레지스트리 키 가져오기

이 예제에서는에서 모든 레지스트리 키를 가져옵니다 `HKEY_LOCAL_MACHINE\HARDWARE` .

`Get-ChildItem`**Path** 매개 변수를 사용 하 여 레지스트리 키를 지정 합니다 `HKLM:\HARDWARE` . 레지스트리 키의 hive 경로와 최상위 수준은 PowerShell 콘솔에 표시 됩니다.

자세한 내용은 [about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)를 참조 하세요.

```powershell
Get-ChildItem -Path HKLM:\HARDWARE
```

```Output
    Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name             Property
----             --------
ACPI
DESCRIPTION
DEVICEMAP
RESOURCEMAP
UEFI
```

```powershell
Get-ChildItem -Path HKLM:\HARDWARE -Exclude D*
```

```Output
   Hive: HKEY_LOCAL_MACHINE\HARDWARE

Name                           Property
----                           --------
ACPI
RESOURCEMAP
```

첫 번째 명령은 레지스트리 키의 내용을 보여 줍니다 `HKLM:\HARDWARE` . **Exclude** 매개 변수는 `Get-ChildItem` 로 시작 하는 하위 키를 반환 하지 않도록에 지시 합니다 `D*` . 현재 **Exclude** 매개 변수는 항목 속성이 아닌 하위 키 에서만 작동 합니다.

### 예 7: 코드 서명 기관을 사용 하 여 모든 인증서 가져오기

이 예제에서는 코드 서명 기관이 있는 PowerShell **Cert:** 드라이브에 있는 각 인증서를 가져옵니다.

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **Cert:** provider를 지정 합니다. **재귀** 매개 변수는 **경로** 및 해당 하위 디렉터리에 지정 된 디렉터리를 검색 합니다. **Codesigningcert** 매개 변수는 코드 서명 기관이 있는 인증서만 가져옵니다.

```powershell
Get-ChildItem -Path Cert:\* -Recurse -CodeSigningCert
```

인증서 공급자 및 Cert: 드라이브에 대 한 자세한 내용은 [about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)를 참조 하세요.

### 예 8: Depth 매개 변수를 사용 하 여 항목 가져오기

이 예제에서는 디렉터리와 해당 하위 디렉터리에 있는 항목을 표시 합니다. **Depth** 매개 변수는 재귀에 포함할 하위 디렉터리 수준 수를 결정 합니다. 빈 디렉터리는 출력에서 제외 됩니다.

```powershell
Get-ChildItem -Path C:\Parent -Depth 2
```

```Output
    Directory: C:\Parent

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level1
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:24                SubDir_Level2
-a----        2/13/2019     08:55             26 file.txt

    Directory: C:\Parent\SubDir_Level1\SubDir_Level2

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        2/14/2019     10:22                SubDir_Level3
-a----        2/13/2019     08:55             26 file.txt
```

`Get-ChildItem`Cmdlet은 **Path** 매개 변수를 사용 하 여 **c:\parent** 를 지정 합니다. **Depth** 매개 변수는 두 개의 재귀 수준을 지정 합니다. `Get-ChildItem`**Path** 매개 변수 및 두 개의 하위 디렉터리 수준에 지정 된 디렉터리의 내용을 표시 합니다.

### 예 9: 하드 링크 정보 가져오기

PowerShell 6.2에서 하드 링크 정보를 가져오기 위해 대체 뷰가 추가 되었습니다.

```powershell
Get-ChildItem -Path C:\PathContainingHardLink | Format-Table -View childrenWithHardLink
```

### 예 9: 실험적 기능 PSUnixFileStat에 대 한 출력

Unix 시스템의 PowerShell 7에서 실험적 기능 **PSUnixFileStat** 는 unix와 비슷한 출력을 제공 합니다.

```powershell
PS> Get-ChildItem /etc/r*
```

```Output
    Directory: /etc

UnixMode   User Group    LastWriteTime Size Name
--------   ---- -----    ------------- ---- ----
drwxr-xr-x root wheel  9/30/2019 19:19  128 racoon
-rw-r--r-- root wheel  9/26/2019 18:20 1560 rc.common
-rw-r--r-- root wheel  7/31/2017 17:30 1560 rc.common~previous
-rw-r--r-- root wheel  9/27/2019 20:34 5264 rc.netboot
lrwxr-xr-x root wheel  11/8/2019 15:35   22 resolv.conf -> /private/var/run/resolv.conf
-rw-r--r-- root wheel 10/23/2019 17:41    0 rmtab
-rw-r--r-- root wheel 10/23/2019 17:41 1735 rpc
-rw-r--r-- root wheel  7/25/2017 18:37 1735 rpc~previous
-rw-r--r-- root wheel 10/23/2019 18:42  891 rtadvd.conf
-rw-r--r-- root wheel  8/24/2017 21:54  891 rtadvd.conf~previous
```

이제 출력의 일부인 새 속성은 다음과 같습니다.

- 모든 수 **x 모드** 는 Unix 시스템에 표시 되는 파일 사용 권한입니다.
- **사용자** 가 파일 소유자입니다.
- **그룹이 그룹 소유자입니다.**
- **크기** 는 Unix 시스템에 표시 되는 파일 또는 디렉터리의 크기입니다.

## 매개 변수

### -특성

지정된 특성을 갖는 파일 및 폴더를 가져옵니다. 이 매개 변수는 모든 특성을 지원하며 복잡한 특성 조합을 지정할 수 있도록 합니다.

예를 들어 암호화되거나 압축된 비시스템 파일(디렉터리 아님)을 가져오려면 다음과 같이 입력하세요.

`Get-ChildItem -Attributes !Directory+!System+Encrypted, !Directory+!System+Compressed`

일반적으로 사용 되는 특성이 있는 파일 및 폴더를 찾으려면 **attributes** 매개 변수를 사용 합니다. 또는 매개 변수 **디렉터리** , **파일** , **숨김** , **읽기 전용** 및 **시스템** 입니다.

**Attributes** 매개 변수는 다음 속성을 지원 합니다.

- **보관**
- **Compressed**
- **디바이스**
- **디렉터리**
- **암호화됨**
- **숨김**
- **및 Itystream**
- **보통**
- **NoScrubData**
- **NotContentIndexed**
- **라인인**
- **읽기 전용**
- **ReparsePoint**
- **SparseFile**
- **시스템**
- **임시**

이러한 특성에 대 한 설명은 [Fileattributes 열거](/dotnet/api/system.io.fileattributes)를 참조 하세요.

특성을 결합 하려면 다음 연산자를 사용 합니다.

- `!` 나타내지
- `+` 하거나
- `,` 디스크나

연산자와 해당 특성 사이에 공백을 사용 하지 마십시오. 쉼표 뒤에 공백이 허용 됩니다.

공통 특성의 경우 다음 약어를 사용 합니다.

- `D` 디렉터리나
- `H` 은선제거
- `R` (읽기 전용)
- `S` 컴퓨터

```yaml
Type: System.Management.Automation.FlagsExpression`1[System.IO.FileAttributes]
Parameter Sets: (All)
Aliases:
Accepted values: Archive, Compressed, Device, Directory, Encrypted, Hidden, IntegrityStream, Normal, NoScrubData, NotContentIndexed, Offline, ReadOnly, ReparsePoint, SparseFile, System, Temporary

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -깊이

이 매개 변수는 PowerShell 5.0에 추가 되었으며 재귀의 깊이를 제어할 수 있습니다. 기본적으로는 `Get-ChildItem` 부모 디렉터리의 내용을 표시 합니다. **Depth** 매개 변수는 재귀에 포함 된 하위 디렉터리 수준 수를 결정 하 고 내용을 표시 합니다.

예를 들어에는 `Depth 2` **Path** 매개 변수의 디렉터리, 첫 번째 수준의 하위 디렉터리 및 하위 디렉터리의 두 번째 수준이 포함 됩니다. 기본적으로 디렉터리 이름과 파일 이름은 출력에 포함 됩니다.

> [!NOTE]
> PowerShell 또는 **cmd.exe** 의 Windows 컴퓨터에서 **tree.com** 명령을 사용 하 여 디렉터리 구조에 대 한 그래픽 보기를 표시할 수 있습니다.

```yaml
Type: System.UInt32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Directory

디렉터리 목록을 가져오려면 **directory 매개 변수를 사용** 하거나 **Directory** 속성에 **Attributes** 매개 변수를 사용 합니다. **디렉터리** 에는 **재귀** 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ad, d

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -제외

이 cmdlet이 작업에서 제외 하는 속성 또는 속성을 문자열 배열로 지정 합니다.
이 매개 변수 값은 **Path** 매개 변수를 한정합니다. 경로 요소 또는 패턴 (예: 또는)을 입력 `*.txt` `A*` 합니다. 와일드카드 문자가 허용됩니다.

`*` **Path** 매개 변수의 후행 별표 ()는 선택 사항입니다. 예를 들어 `-Path C:\Test\Logs` 또는 `-Path C:\Test\Logs\*`입니다. 후행 별표 ( `*` )가 포함 된 경우 명령은 **Path** 매개 변수의 하위 디렉터리에 루트로. 별표 ()를 사용 하지 않으면 `*` **Path** 매개 변수의 콘텐츠가 표시 됩니다. 자세한 내용은 예 5 및 메모 섹션에 포함 되어 있습니다.

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

### -File

파일 목록을 가져오려면 **File** 매개 변수를 사용 합니다. **파일** 에는 **재귀** 매개 변수를 사용할 수 있습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: af

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Filter

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [파일 시스템](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터를 지 원하는 유일한 설치 된 PowerShell 공급자입니다. 필터는 다른 매개 변수 보다 더 효율적입니다. 공급자는 검색 된 개체를 PowerShell에서 필터링 하는 대신 개체를 가져올 때 필터를 적용 합니다. 필터 문자열은 파일을 열거 하기 위해 .NET API에 전달 됩니다. API는 `*` 및 `?` 와일드 카드만 지원 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -FollowSymlink

기본적으로 cmdlet은 `Get-ChildItem` 재귀 중에 발견 된 디렉터리에 대 한 기호화 된 링크를 표시 하지만 재귀는 표시 하지 않습니다. **FollowSymlink** 매개 변수를 사용 하 여 해당 기호화 된 링크를 대상으로 하는 디렉터리를 검색 합니다. **FollowSymlink** 는 동적 매개 변수 이며 **FileSystem** 공급자 에서만 지원 됩니다.

이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.

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

### -Force

사용자가 숨겨진 또는 시스템 파일과 같이 다른 방법으로는 액세스할 수 없는 항목을 cmdlet에서 가져올 수 있습니다. **Force** 매개 변수는 보안 제한을 재정의 하지 않습니다. 구현은 공급자 간에 차이가 있습니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

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

### -Hidden

**숨겨진 항목만** **가져오려면 hidden 속성** 을 사용 하 여 Hidden 매개 변수 또는 **Attributes** 매개 변수를 사용 합니다. 기본적으로는 `Get-ChildItem` 숨겨진 항목을 표시 하지 않습니다. **Force** 매개 변수를 사용 하 여 숨겨진 항목을 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ah, h

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
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

### -LiteralPath

하나 이상의 위치에 대한 경로를 지정합니다. **LiteralPath** 의 값은 입력 한 대로 사용 됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요. 작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.

자세한 내용은 [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)를 참조 하세요.

```yaml
Type: System.String[]
Parameter Sets: LiteralItems
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

위치의 항목 이름만 가져옵니다. 출력은 파이프라인에서 다른 명령으로 전송할 수 있는 문자열 개체입니다. 와일드카드가 지원됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Path

하나 이상의 위치에 대한 경로를 지정합니다. 와일드 카드가 허용 됩니다. 기본 위치는 현재 디렉터리 ()입니다 `.` .

```yaml
Type: System.String[]
Parameter Sets: Items
Aliases:

Required: False
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -ReadOnly

읽기 전용 항목만 가져오려면 **readonly** 매개 변수 또는 **Attributes** 매개 변수 **readonly** 속성을 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ar

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -재귀

지정된 위치와 해당 위치의 모든 하위 항목에서 항목을 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: s

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -System

시스템 파일 및 디렉터리만 가져옵니다. 시스템 파일 및 폴더만 가져오려면 **system** 매개 변수 또는 **Attributes** 매개 변수 **시스템** 속성을 사용 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: as

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

경로를 포함 하는 문자열을로 파이프 할 수 있습니다 `Get-ChildItem` .

## 출력

### System.Object

을 반환 하는 개체의 형식은 `Get-ChildItem` 공급자 드라이브 경로의 개체에 의해 결정 됩니다.

### System.String

**Name** 매개 변수를 사용 하는 경우는 `Get-ChildItem` 개체 이름을 문자열로 반환 합니다.

## 참고

- `Get-ChildItem` 는 기본 제공 별칭,, 및 중 하나를 사용 하 여 실행할 수 있습니다 `ls` `dir` `gci` . 자세한 내용은 [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md)를 참조 하세요.
- `Get-ChildItem` 숨겨진 항목은 기본적으로 가져오지 않습니다. 숨겨진 항목을 가져오려면 **Force** 매개 변수를 사용합니다.
- `Get-ChildItem`Cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다.
  자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[about_Certificate_Provider](../Microsoft.PowerShell.Security/About/about_Certificate_Provider.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[about_Registry_Provider](../Microsoft.PowerShell.Core/About/about_Registry_Provider.md)

[ForEach-Object](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Get-Alias](../Microsoft.PowerShell.Utility/Get-Alias.md)

[Get-Item](Get-Item.md)

[Get-Location](Get-Location.md)

[Get-Process](Get-Process.md)

[Get-PSProvider](Get-PSProvider.md)

[Split-Path](Split-Path.md)

