---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/copy-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Copy-Item
ms.openlocfilehash: 393e0afafebf30e4b300c4200be6f9fa7a93bfc8
ms.sourcegitcommit: 33ac34789e86ffb4e7e69453ae38fc0bd24933dd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/26/2020
ms.locfileid: "93219762"
---
# Copy-Item

## 개요
위치 간에 항목을 복사합니다.

## SYNTAX

### Path (기본값)

```
Copy-Item [-Path] <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

### LiteralPath

```
Copy-Item -LiteralPath <String[]> [[-Destination] <String>] [-Container] [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Recurse] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm] [-FromSession <PSSession>] [-ToSession <PSSession>] [<CommonParameters>]
```

## 설명

`Copy-Item`Cmdlet은 한 위치에서 동일한 네임 스페이스의 다른 위치로 항목을 복사 합니다.
예를 들어 파일을 폴더에 복사할 수 있지만 인증서 드라이브에 파일을 복사할 수는 없습니다.

이 cmdlet은 복사 되는 항목을 잘라내거나 삭제 하지 않습니다. Cmdlet에서 복사할 수 있는 특정 항목은 항목을 노출 하는 PowerShell 공급자에 따라 달라 집니다. 예를 들어 파일 시스템 드라이브의 파일 및 디렉터리와 레지스트리 드라이브의 레지스트리 키 및 항목을 복사할 수 있습니다.

이 cmdlet은 동일한 명령에서 항목을 복사 하 고 이름을 바꿀 수 있습니다. 항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 입력 합니다. 항목의 이름을 바꾸고 복사 하지 않으려면 cmdlet을 사용 `Rename-Item` 합니다.

## 예제

### 예제 1: 지정 된 디렉터리에 파일 복사

이 예에서는 `mar1604.log.txt` 파일을 디렉터리에 복사 `C:\Presentation` 합니다. 원본 파일은 삭제 되지 않습니다.

```powershell
Copy-Item "C:\Wabash\Logfiles\mar1604.log.txt" -Destination "C:\Presentation"
```

### 예 2: 디렉터리 내용을 기존 디렉터리에 복사

이 예에서는 디렉터리의 내용을 `C:\Logfiles` 기존 디렉터리에 복사 `C:\Drawings` 합니다. `Logfiles`디렉터리가 복사 되지 않습니다.

디렉터리에 `Logfiles` 하위 디렉터리의 파일이 포함 된 경우 해당 하위 디렉터리는 파일 트리와 함께 그대로 복사 됩니다. 기본적으로 **Container** 매개 변수는 **True** 로 설정 되어 디렉터리 구조를 유지 합니다.

```powershell
Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings" -Recurse
```

> [!NOTE]
> 복사본에 디렉터리를 포함 해야 하는 경우 `Logfiles` 경로에서을 제거 합니다 `\*` . **Path**
> 다음은 그 예입니다. 
>
> `Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings" -Recurse`

### 예 3: 새 디렉터리에 디렉터리 및 콘텐츠 복사

이 예에서는 원본 디렉터리의 내용을 복사 `C:\Logfiles` 하 고 새 대상 디렉터리를 만듭니다. 새 대상 디렉터리는 `\Logs` 에 생성 됩니다 `C:\Drawings` .

원본 디렉터리의 이름을 포함 하려면 **예 2** 에 표시 된 것 처럼 기존 대상 디렉터리에 복사 합니다. 또는 원본 디렉터리와 동일한를 사용 하 여 새 대상 디렉터리의 이름을로 바꿉니다.

```powershell
Copy-Item -Path "C:\Logfiles" -Destination "C:\Drawings\Logs" -Recurse
```

> [!NOTE]
> **경로** 에이 포함 되어 있으면 `\*` 하위 디렉터리 트리를 비롯 한 모든 디렉터리의 파일 내용이 새 대상 디렉터리에 복사 됩니다. 다음은 그 예입니다. 
>
> `Copy-Item -Path "C:\Logfiles\*" -Destination "C:\Drawings\Logs" -Recurse`

### 예제 4: 파일을 지정 된 디렉터리에 복사 하 고 파일 이름을 바꿉니다.

이 예에서는 cmdlet을 사용 하 여 `Copy-Item` `Get-Widget.ps1` 디렉터리에서 디렉터리로 스크립트를 복사 `\\Server01\Share` `\\Server12\ScriptArchive` 합니다. 복사 작업의 일부로 명령은 항목 이름을에서 `Get-Widget.ps1` 로 변경 `Get-Widget.ps1.txt` 하므로 메일 메시지에 첨부할 수 있습니다.

```powershell
Copy-Item "\\Server01\Share\Get-Widget.ps1" -Destination "\\Server12\ScriptArchive\Get-Widget.ps1.txt"
```

### 예 5: 원격 컴퓨터에 파일 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `test.log` `D:\Folder001` `C:\Folder001_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더에서 원격 컴퓨터의 폴더로 복사 합니다 `$Session` . 원본 파일은 삭제 되지 않습니다.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "D:\Folder001\test.log" -Destination "C:\Folder001_Copy\" -ToSession $Session
```

### 예제 6: 원격 컴퓨터에 폴더 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `D:\Folder002` `C:\Folder002_Copy` 변수에 저장 된 세션 정보를 사용 하 여 원격 컴퓨터의 디렉터리에 폴더를 복사 합니다 `$Session` . **재귀** 스위치를 사용 하지 않고 하위 폴더 또는 파일은 복사 되지 않습니다.
작업은 `Folder002_Copy` 폴더가 아직 없는 경우 만듭니다.

```powershell
$Session = New-PSSession -ComputerName "Server02" -Credential "Contoso\User01"
Copy-Item "D:\Folder002\" -Destination "C:\Folder002_Copy\" -ToSession $Session
```

### 예 7: 원격 컴퓨터에 폴더의 전체 콘텐츠를 재귀적으로 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `D:\Folder003` `C:\Folder003_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더의 전체 내용을 원격 컴퓨터의 디렉터리에 복사 합니다 `$Session` . 하위 폴더는 파일 트리와 함께 그대로 복사 됩니다. 작업은 `Folder003_Copy` 폴더가 아직 없는 경우 만듭니다.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder003\" -Destination "C:\Folder003_Copy\" -ToSession $Session -Recurse
```

### 예 8: 원격 컴퓨터에 파일을 복사한 다음 파일 이름을 바꿉니다.

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `scriptingexample.ps1` `D:\Folder004` `C:\Folder004_Copy` 변수에 저장 된 세션 정보를 사용 하 여 폴더에서 원격 컴퓨터의 폴더로 복사 합니다 `$Session` . 복사 작업의 일부로 명령은 항목 이름을에서 `scriptingexample.ps1` 로 변경 `scriptingexample_copy.ps1` 하므로 메일 메시지에 첨부할 수 있습니다. 원본 파일은 삭제 되지 않습니다.

```powershell
$Session = New-PSSession -ComputerName "Server04" -Credential "Contoso\User01"
Copy-Item "D:\Folder004\scriptingexample.ps1" -Destination "C:\Folder004_Copy\scriptingexample_copy.ps1" -ToSession $Session
```

### 예 9: 로컬 컴퓨터에 원격 파일 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `test.log` `C:\MyRemoteData\` `D:\MyLocalData` 변수에 저장 된 세션 정보를 사용 하 여 원격에서 로컬 폴더로 복사 합니다 `$Session` . 원본 파일은 삭제 되지 않습니다.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\test.log" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 예 10: 원격 폴더의 전체 콘텐츠를 로컬 컴퓨터에 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `C:\MyRemoteData\scripts` `D:\MyLocalData` 변수에 저장 된 세션 정보를 사용 하 여 원격 폴더의 전체 콘텐츠를 로컬 폴더에 복사 합니다 `$Session` . Scripts 폴더에 하위 폴더의 파일이 포함 된 경우 해당 하위 폴더는 파일 트리와 함께 그대로 복사 됩니다.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\" -FromSession $Session
```

### 예 11: 로컬 컴퓨터에 원격 폴더의 전체 콘텐츠를 재귀적으로 복사

의 자격 증명을 사용 하 여 **Server01** 라는 원격 컴퓨터에 대 한 세션이 만들어지고 `Contoso\User01` 이라는 변수에 결과가 저장 됩니다 `$Session` .

`Copy-Item`Cmdlet은 `C:\MyRemoteData\scripts` `D:\MyLocalData\scripts` 변수에 저장 된 세션 정보를 사용 하 여 원격 폴더의 전체 콘텐츠를 로컬 폴더에 복사 합니다 `$Session` . **재귀** 매개 변수가 사용 되기 때문에이 작업은 스크립트 폴더를 만듭니다 (이미 존재 하지 않는 경우). Scripts 폴더에 하위 폴더의 파일이 포함 된 경우 해당 하위 폴더는 파일 트리와 함께 그대로 복사 됩니다.

```powershell
$Session = New-PSSession -ComputerName "Server01" -Credential "Contoso\User01"
Copy-Item "C:\MyRemoteData\scripts" -Destination "D:\MyLocalData\scripts" -FromSession $Session -Recurse
```

### 예 12: 폴더 트리에서 현재 폴더로 파일을 재귀적으로 복사

이 예에서는 다단계 폴더 구조에서 단일 플랫 폴더로 파일을 복사 하는 방법을 보여 줍니다.
처음 세 명령은 기존 폴더 구조와 두 파일의 내용 (두 이름 모두)을 보여 줍니다 `file3.txt` .

```powershell
PS C:\temp\test> (Get-ChildItem C:\temp\tree -Recurse).FullName
C:\temp\tree\subfolder
C:\temp\tree\file1.txt
C:\temp\tree\file2.txt
C:\temp\tree\file3.txt
C:\temp\tree\subfolder\file3.txt
C:\temp\tree\subfolder\file4.txt
C:\temp\tree\subfolder\file5.txt

PS C:\temp\test> Get-Content C:\temp\tree\file3.txt
This is file3.txt in the root folder

PS C:\temp\test> Get-Content C:\temp\tree\subfolder\file3.txt
This is file3.txt in the subfolder

PS C:\temp\test> Copy-Item -Path C:\temp\tree -Filter *.txt -Recurse -Container:$false
PS C:\temp\test> (Get-ChildItem . -Recurse).FullName
C:\temp\test\subfolder
C:\temp\test\file1.txt
C:\temp\test\file2.txt
C:\temp\test\file3.txt
C:\temp\test\file4.txt
C:\temp\test\file5.txt

PS C:\temp\test> Get-Content .\file3.txt
This is file3.txt in the subfolder
```

`Copy-Item`Cmdlet은 **Container** 매개 변수를로 설정 합니다 `$false` . 이렇게 하면 소스 폴더의 내용이 복사 되지만 폴더 구조는 유지 되지 않습니다. 동일한 이름을 가진 파일은 대상 폴더에서 덮어쓰여집니다.

## PARAMETERS

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

### -컨테이너

이 cmdlet은 복사 작업 중에 컨테이너 개체를 유지 함을 나타냅니다. 기본적으로 **Container** 매개 변수는 **True** 로 설정 됩니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: True
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

### -Destination

새 위치의 경로를 지정합니다. 기본값은 현재 디렉터리입니다.

복사할 항목의 이름을 바꾸려면 **Destination** 매개 변수 값에 새 이름을 지정 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
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

**Path** 매개 변수를 한정 하는 필터를 지정 합니다. [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) 공급자는 필터 사용을 지 원하는 유일한 설치 된 PowerShell 공급자입니다. [About_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md)에서 **FileSystem** 필터 언어의 구문을 찾을 수 있습니다.
필터는 다른 매개 변수 보다 더 효율적입니다. 공급자는 검색 된 후 개체를 PowerShell로 필터링 하는 대신 cmdlet이 개체를 가져올 때 해당 개체를 적용 하기 때문입니다.

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

이 cmdlet이 다른 방법으로는 변경할 수 없는 항목 (예: 읽기 전용 파일 또는 별칭)을 복사 함을 나타냅니다.

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

### -FromSession

원격 파일이 복사 되는 **PSSession** 개체를 지정 합니다. 이 매개 변수를 사용 하는 경우 **Path** 및 **LiteralPath** 매개 변수는 원격 컴퓨터의 로컬 경로를 참조 합니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

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
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환 합니다. 기본적으로이 cmdlet은 출력을 생성 하지 않습니다.

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

### -Path

복사할 항목의 경로를 문자열 배열로 지정 합니다. 와일드카드 문자를 사용할 수 있습니다.

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

### -재귀

이 cmdlet이 재귀적 복사를 수행 함을 나타냅니다.

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

### -ToSession

원격 파일이 복사 되는 **PSSession** 개체를 지정 합니다. 이 매개 변수를 사용 하는 경우 **대상** 매개 변수는 원격 컴퓨터의 로컬 경로를 참조 합니다.

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다. Cmdlet이 실행 되지 않습니다.

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

이 cmdlet은,,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` 및 `-WarningVariable` 등의 일반 매개 변수를 지원 합니다. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

이 cmdlet에 대 한 경로가 포함 된 문자열을 파이프 할 수 있습니다.

## 출력

### 없음 또는 복사한 항목을 나타내는 개체

**PassThru** 매개 변수를 사용 하는 경우이 cmdlet은 복사 된 항목을 나타내는 개체를 반환 합니다. 그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.

## 참고

이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면을 입력 `Get-PSProvider` 합니다. 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.

## 관련 링크

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Clear-Item](Clear-Item.md)

[Get-Item](Get-Item.md)

[Get-PSProvider](Get-PSProvider.md)

[Invoke-Item](Invoke-Item.md)

[Move-Item](Move-Item.md)

[New-Item](New-Item.md)

[Remove-Item](Remove-Item.md)

[Rename-Item](Rename-Item.md)

[Set-Item](Set-Item.md)

