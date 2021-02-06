---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Item
ms.openlocfilehash: 4c247513ab06f1bcba648a62969fb7d458e0d35d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599957"
---
# New-Item

## 개요
새 항목을 만듭니다.

## SYNTAX

### pathSet (기본값)

```
New-Item [-Path] <String[]> [-ItemType <String>] [-Value <Object>] [-Force] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### nameSet

```
New-Item [[-Path] <String[]>] -Name <String> [-ItemType <String>] [-Value <Object>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`New-Item`Cmdlet은 새 항목을 만들고 해당 값을 설정 합니다. 만들 수 있는 항목의 형식은 항목의 위치에 따라 달라 집니다. 예를 들어 파일 시스템에서는 `New-Item` 파일 및 폴더를 만듭니다. 레지스트리에서 `New-Item` 레지스트리 키와 항목을 만듭니다.

`New-Item` 또한에서 만드는 항목의 값을 설정할 수 있습니다. 예를 들어 새 파일을 만들 때는 `New-Item` 파일에 초기 콘텐츠를 추가할 수 있습니다.

## 예제

### 예제 1: 현재 디렉터리에 파일 만들기

이 명령은 현재 디렉터리에 "testfile1.txt" 라는 텍스트 파일을 만듭니다. **Path** 매개 변수 값의 점 ('. ')은 현재 디렉터리를 나타냅니다. **Value** 매개 변수 뒤에 오는 따옴표로 묶인 텍스트는 파일에 내용으로 추가 됩니다.

```powershell
New-Item -Path . -Name "testfile1.txt" -ItemType "file" -Value "This is a text string."
```

### 예제 2: 디렉터리 만들기

이 명령은 드라이브에 "Logfiles" 라는 디렉터리를 만듭니다 `C:` . **ItemType** 매개 변수는 새 항목이 파일 또는 기타 파일 시스템 개체가 아닌 디렉터리 임을 지정 합니다.

```powershell
New-Item -Path "c:\" -Name "logfiles" -ItemType "directory"
```

### 예제 3: 프로필 만들기

이 명령은 변수에 의해 지정 된 경로에 PowerShell 프로필을 만듭니다 `$profile` .

프로필을 사용 하 여 PowerShell을 사용자 지정할 수 있습니다. `$profile` 는 "CurrentUser/CurrentHost" 프로필의 경로와 파일 이름을 저장 하는 자동 (기본 제공) 변수입니다. PowerShell에서 경로와 파일 이름을 저장 하는 경우에도 기본적으로 프로필은 존재 하지 않습니다.

이 명령에서 변수는 `$profile` 파일의 경로를 나타냅니다. **ItemType** 매개 변수는 명령이 파일을 생성 하도록 지정 합니다. **Force** 매개 변수를 사용 하면 경로의 디렉터리가 없는 경우에도 프로필 경로에 파일을 만들 수 있습니다.

프로필을 만든 후 프로필에 별칭, 함수 및 스크립트를 입력 하 여 셸을 사용자 지정할 수 있습니다.

자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md) 및 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.

```powershell
New-Item -Path $profile -ItemType "file" -Force
```

### 예제 4: 다른 디렉터리에 디렉터리 만들기

이 예제에서는 "C:\PS-Test" 디렉터리에 새 Scripts 디렉터리를 만듭니다.

새 디렉터리 항목인 "Scripts"의 이름은 **name** 값에 지정 되지 않고 **Path** 매개 변수 값에 포함 됩니다. 구문과 같이 두 명령 형식 모두 유효합니다.

```powershell
New-Item -ItemType "directory" -Path "c:\ps-test\scripts"
```

### 예 5: 여러 파일 만들기

이 예제에서는 두 개의 다른 디렉터리에 파일을 만듭니다. **Path** 는 여러 문자열을 사용 하므로 여러 항목을 만드는 데 사용할 수 있습니다.

```powershell
New-Item -ItemType "file" -Path "c:\ps-test\test.txt", "c:\ps-test\Logs\test.log"
```

### 예제 6: 와일드 카드를 사용 하 여 여러 디렉터리에 파일 만들기

`New-Item`Cmdlet은 **Path** 매개 변수에서 와일드 카드를 지원 합니다. 다음 명령은 `temp.txt` **Path** 매개 변수에서 와일드 카드에 의해 지정 된 모든 디렉터리에 파일을 만듭니다.

```powershell
Get-ChildItem -Path C:\Temp\
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d-----        5/15/2019   6:45 AM        1   One
d-----        5/15/2019   6:45 AM        1   Two
d-----        5/15/2019   6:45 AM        1   Three
```

```powershell
New-Item -Path * -Name temp.txt -ItemType File | Select-Object FullName
```

```Output
FullName
--------
C:\Temp\One\temp.txt
C:\Temp\Three\temp.txt
C:\Temp\Two\temp.txt
```

`Get-ChildItem`Cmdlet은 디렉터리 아래에 세 개의 디렉터리를 표시 합니다 `C:\Temp` . Cmdlet은 와일드 카드를 사용 하 여 `New-Item` `temp.txt` 현재 디렉터리의 모든 디렉터리에 파일을 만듭니다. `New-Item`Cmdlet은 `Select-Object` 새로 만든 파일의 경로를 확인 하기 위해 파이프 하 여 만든 항목을 출력 합니다.

### 예 7: 파일이 나 폴더에 대 한 바로 가기 링크 만들기

이 예제에서는 현재 폴더의 Notice.txt 파일에 대 한 바로 가기 링크를 만듭니다.

```powershell
$link = New-Item -ItemType SymbolicLink -Path .\link -Target .\Notice.txt
$link | Select-Object LinkType, Target
```

```Output
LinkType     Target
--------     ------
SymbolicLink {.\Notice.txt}
```

이 예제에서 **Target** 은 **값** 매개 변수에 대 한 별칭입니다. 기호화 된 링크의 대상은 상대 경로일 수 있습니다. PowerShell v 6.2 이전에는 대상이 정규화 된 경로 여야 합니다.

PowerShell 7.1부터 이제 상대 경로를 사용 하 여 Windows의 폴더에 대 한 **값인 symboliclink** 를 만들 수 있습니다.

### 예 8:-Force 매개 변수를 사용 하 여 폴더 다시 만들기 시도

이 예제에서는 안에 파일이 있는 폴더를 만듭니다. 그런 다음를 사용 하 여 동일한 폴더를 만듭니다 `-Force` . 폴더를 덮어쓰지는 않지만 파일을 그대로 만든 상태로 기존 폴더 개체를 반환 합니다.

```powershell
PS> New-Item -Path .\TestFolder -ItemType Directory
PS> New-Item -Path .\TestFolder\TestFile.txt -ItemType File

PS> New-Item -Path .\TestFolder -ItemType Directory -Force

    Directory: C:\
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----         5/1/2020   8:03 AM                TestFolder

PS> Get-ChildItem .\TestFolder\

    Directory: C:\TestFolder
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:03 AM              0 TestFile.txt
```

### 예 9:-Force 매개 변수를 사용 하 여 기존 파일 덮어쓰기

이 예에서는 값을 사용 하 여 파일을 만든 다음를 사용 하 여 파일을 다시 만듭니다 `-Force` . 이렇게 하면 기존 파일이 덮어쓰므로 length 속성에서 볼 수 있는 것 처럼 내용이 손실 됩니다.

```powershell
PS> New-Item ./TestFile.txt -ItemType File -Value 'This is just a test file'

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM             24 TestFile.txt

New-Item ./TestFile.txt -ItemType File -Force

    Directory: C:\Source\Test
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/1/2020   8:32 AM              0 TestFile.txt
```

> [!NOTE]
> 스위치와 함께를 사용 하 여 `New-Item` `-Force` 레지스트리 키를 만드는 경우 명령은 파일을 덮어쓸 때와 동일 하 게 동작 합니다. 레지스트리 키가 이미 있는 경우 키와 모든 속성 및 값은 빈 레지스트리 키로 덮어쓰여집니다.

## PARAMETERS

### -Credential

> [!NOTE]
> 이 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다. 이 cmdlet을 실행할 때 다른 사용자를 가장 하거나 자격 증명을 상승 시키려면를 사용 `Invoke-Command` 합니다.

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

### -Force

이 cmdlet이 기존 읽기 전용 항목을 쓰는 항목을 강제로 만들도록 합니다. 구현은 공급자에 따라 다릅니다. **Force** 매개 변수를 사용 하는 경우에도 cmdlet은 보안 제한을 재정의할 수 없습니다.

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

### -ItemType

새 항목의 공급자별 유형을 지정합니다. 이 매개 변수의 사용 가능한 값은 현재 사용 중인 공급자에 따라 달라 집니다.

위치가 드라이브에 있는 경우 `FileSystem` 다음 값을 사용할 수 있습니다.

- 파일
- 디렉터리
- 값인 symboliclink
- 분기 동기화
- Hardlink create

> [!NOTE]
> `SymbolicLink`Windows에서 형식을 만들려면 관리자 권한 상승이 필요 합니다. 그러나 개발자 모드를 사용 하는 Windows 10 (빌드 14972 이상)에서는 더 이상 사용 권한 상승을 사용 하 여 기호 링크를 만들 필요가 없습니다.

드라이브에 `Certificate` 다음과 같은 값을 지정할 수 있습니다.

- 인증서 공급자
- 인증서
- 스토어
- StoreLocation

자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Type

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

새 항목의 이름을 지정합니다. **Name** 또는 **path** 매개 변수 값에서 새 항목의 이름을 지정 하 고 **이름** 또는 **경로** 값에 새 항목의 경로를 지정할 수 있습니다. **Name** 매개 변수를 사용 하 여 전달 된 항목 이름은 **Path** 매개 변수의 값을 기준으로 생성 됩니다.

```yaml
Type: System.String
Parameter Sets: nameSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

새 항목의 위치 경로를 지정 합니다. **경로** 를 생략할 경우 기본값은 현재 위치입니다. **이름** 에 새 항목의 이름을 지정 하거나 **경로** 에 포함할 수 있습니다. **Name** 매개 변수를 사용 하 여 전달 된 항목 이름은 **Path** 매개 변수의 값을 기준으로 생성 됩니다.

이 cmdlet의 경우 **Path** 매개 변수는 다른 Cmdlet의 **LiteralPath** 매개 변수와 유사 하 게 작동 합니다.
와일드 카드 문자는 해석 되지 않습니다. 모든 문자는 위치의 공급자에 전달 됩니다. 공급자는 모든 문자를 지원 하지 않을 수 있습니다. 예를 들어, 별표 () 문자를 포함 하는 파일 이름을 만들 수 없습니다 `*` .

```yaml
Type: System.String[]
Parameter Sets: pathSet
Aliases:

Required: True (pathSet), False (nameSet)
Position: 0
Default value: Current location
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Value

새 항목의 값을 지정합니다. 값을로 파이프 할 수도 있습니다 `New-Item` .

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases: Target

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Object

새 항목의 값을이 cmdlet으로 파이프 할 수 있습니다.

## 출력

### System.Object

이 cmdlet은 만든 항목을 반환 합니다.

## 참고

`New-Item` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PsProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[Clear-Item](Clear-Item.md)

[Copy-Item](Copy-Item.md)

[Get-Item](Get-Item.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

