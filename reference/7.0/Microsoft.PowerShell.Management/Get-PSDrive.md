---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSDrive
ms.openlocfilehash: d404f0fdc82e3730f1f6a04d7f39d5988a3de7d6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210194"
---
# Get-PSDrive

## 개요
현재 세션의 드라이브를 가져옵니다.

## SYNTAX

### 이름 (기본값)

```
Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

### LiteralName

```
Get-PSDrive [-LiteralName] <String[]> [-Scope <String>] [-PSProvider <String[]>] [<CommonParameters>]
```

## 설명

`Get-PSDrive`Cmdlet은 현재 세션의 드라이브를 가져옵니다. 특정 드라이브를 가져오거나 세션의 모든 드라이브를 가져올 수 있습니다.

이 cmdlet은 다음과 같은 종류의 드라이브를 가져옵니다.

- 네트워크 공유에 매핑된 드라이브를 포함 하는 컴퓨터의 Windows 논리 드라이브
- PowerShell 공급자 (예: 인증서:, 함수: 및 별칭: 드라이브)가 노출 하는 드라이브와 Windows PowerShell 레지스트리 공급자가 노출 하는 HKLM: 및 HKCU: 드라이브입니다.
- New-PSDrive cmdlet을 사용 하 여 만드는 세션 지정 임시 드라이브 및 영구 매핑된 네트워크 드라이브

Windows PowerShell 3.0부터 cmdlet의 **Persist** 매개 변수는 `New-PSDrive` 로컬 컴퓨터에 저장 되어 다른 세션에서 사용할 수 있는 매핑된 네트워크 드라이브를 만들 수 있습니다. 자세한 내용은 PSDrive를 참조 하세요.

또한 Windows PowerShell 3.0부터는 외장형 드라이브가 컴퓨터에 연결되어 있으면 Windows PowerShell이 파일 시스템에 새 드라이브를 나타내는 PSDrive를 자동으로 추가합니다.
Windows PowerShell을 다시 시작하지 않아도 됩니다. 마찬가지로 컴퓨터에서 외장형 드라이브의 연결이 끊기면 Windows PowerShell에서 제거된 드라이브를 나타내는 PSDrive를 자동으로 삭제합니다.

## 예제

### 예 1: 현재 세션에서 드라이브 가져오기

```
PS C:\> Get-PSDrive

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
Alias                                  Alias
C                 202.06      23718.91 FileSystem    C:\
Cert                                   Certificate   \
D                1211.06     123642.32 FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
```

이 명령은 현재 세션에서 드라이브를 가져옵니다.

출력에는 하드 드라이브 (C:), CD-ROM 드라이브 (D:), Windows PowerShell 공급자가 제공 하는 드라이브 (Alias:, Cert:, Env:, Function:, HKCU:, HKLM: 및 Variable:)가 표시 됩니다.

### 예 2: 컴퓨터에서 드라이브 가져오기

```
PS C:\foo> Get-PSDrive D

Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
D                1211.06     123642.32 FileSystem    D:\
```

이 명령은 컴퓨터의 D: 드라이브를 가져옵니다. 여기서는 명령의 드라이브 문자 다음에 콜론이 붙는 형태입니다.

### 예 3: Windows PowerShell 파일 시스템 공급자에서 지원 되는 모든 드라이브 가져오기

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
```

이 명령은 Windows PowerShell 파일 시스템 공급자가 지원하는 모든 드라이브를 가져옵니다. 여기에는 고정 드라이브, 논리 파티션, 매핑된 네트워크 드라이브 및 New-PSDrive cmdlet을 사용 하 여 만든 임시 드라이브가 포함 됩니다.

### 예 4: 드라이브가 Windows PowerShell 드라이브 이름으로 사용 되 고 있는지 확인

```powershell
if (Get-PSDrive X -ErrorAction SilentlyContinue) {
    Write-Host 'The X: drive is already in use.'
} else {
    New-PSDrive -Name X -PSProvider Registry -Root HKLM:\SOFTWARE
}
```

이 명령은 Windows PowerShell 드라이브 이름으로 X 드라이브가 이미 사용되고 있는지를 확인합니다.
그렇지 않은 경우이 명령은 cmdlet을 사용 하 여 `New-PSDrive` HKLM: \ SOFTWARE 레지스트리 키에 매핑되는 임시 드라이브를 만듭니다.

### 예 5: 파일 시스템 드라이브의 형식 비교

```
PS C:\> Get-PSDrive -PSProvider FileSystem
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                                    A:\
C                 202.06      23718.91 FileSystem    C:\
D                1211.06     123642.32 FileSystem    D:\
G                 202.06        710.91 FileSystem    \\Music\GratefulDead
X                                      Registry      HKLM:\Network

PS C:\> net use
New connections will be remembered.
Status       Local     Remote                    Network
-------------------------------------------------------------------------------
OK           G:        \\Server01\Public         Microsoft Windows Network

PS C:\> [System.IO.DriveInfo]::GetDrives() | Format-Table
Name DriveType DriveFormat IsReady AvailableFreeSpace TotalFreeSpace TotalSize     RootDirectory VolumeLabel
---- --------- ----------- ------- ------------------ -------------- ---------     ------------- -----------
A:\    Network               False                                                 A:\
C:\      Fixed NTFS          True  771920580608       771920580608   988877418496  C:\           Windows
D:\      Fixed NTFS          True  689684144128       689684144128   1990045179904 D:\           Big Drive
E:\      CDRom               False                                                 E:\
G:\    Network NTFS          True      69120000           69120000       104853504 G:\           GratefulDead

PS N:\> Get-CimInstance -Class Win32_LogicalDisk

DeviceID DriveType ProviderName   VolumeName         Size          FreeSpace
-------- --------- ------------   ----------         ----          ---------
A:       4
C:       3                        Windows            988877418496  771926069248
D:       3                        Big!              1990045179904  689684144128
E:       5
G:       4         \\Music\GratefulDead              988877418496  771926069248


PS C:\> Get-CimInstance -Class Win32_NetworkConnection
LocalName RemoteName            ConnectionState Status
--------- ----------            --------------- ------
G:        \\Music\GratefulDead  Connected       OK
```

이 예제에서는에 표시 되는 파일 시스템 드라이브의 형식을 `Get-PSDrive` 다른 방법을 사용 하 여 표시 되는 형식과 비교 합니다. 이 예제에서는 Windows PowerShell에서 드라이브를 표시 하는 다양 한 방법을 보여 줍니다. New-PSDrive cmdlet을 사용 하 여 만든 세션별 드라이브는 Windows PowerShell 에서만 액세스할 수 있다는 것을 보여 줍니다.

첫 번째 명령은 `Get-PSDrive` 를 사용 하 여 세션의 모든 파일 시스템 드라이브를 가져옵니다. 여기에는 고정 드라이브 (C: 및 D:), 매핑된 네트워크 드라이브 (G:)가 이 매개 변수는의 **Persist** 매개 변수 `New-PSDrive` 및 PowerShell 드라이브 (T:)를 사용 하 여 `New-PSDrive` **Persist** 매개 변수 없이를 사용 하 여 만든입니다.

**Net use** 명령은 Windows 매핑된 네트워크 드라이브를 표시 합니다 .이 경우 G 드라이브만 표시 합니다. 에서 만든 X: 드라이브는 표시 되지 않습니다 `New-PSDrive` . G: 드라이브가 Music GratefulDead에도 매핑되어 있음을 보여 줍니다 \\ \\ \\ .

세 번째 명령은 Microsoft. NET Framework **System.IO.DriveInfo** 클래스의 **GetDrives** 메서드를 사용합니다. 이 명령은 드라이브 G:를 포함 하 여 Windows 파일 시스템 드라이브를 가져오지만에서 만든 드라이브는 가져오지 않습니다 `New-PSDrive` .

네 번째 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_LogicalDisk** 클래스의 인스턴스를 가져옵니다. A:, C:, D:, E: 및 G: 드라이브를 반환 하지만에서 만든 드라이브는 반환 하지 않습니다 `New-PSDrive` .

마지막 명령은 cmdlet을 사용 하 여 `Get-CimInstance` **Win32_NetworkConnection** 클래스의 인스턴스를 표시 합니다. **Net use** 와 마찬가지로에서 만든 영구 G: 드라이브만 반환 `New-PSDrive` 합니다.

## PARAMETERS

### -LiteralName

드라이브의 이름을 지정합니다.

**LiteralName** 값은 입력한 대로 사용됩니다. 어떠한 문자도 와일드카드로 해석되지 않습니다. 이름에 이스케이프 문자가 포함된 경우 경로를 작은따옴표로 묶어야 합니다. 작은따옴표는 Windows PowerShell이 어떤 문자도 이스케이프 시퀀스로 해석하지 않도록 지시합니다.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

이 cmdlet이 작업에서 가져오는 드라이브의 이름 또는 이름을 문자열 배열로 지정 합니다.
드라이브 이름이나 문자를 콜론(:) 없이 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

Windows PowerShell 공급자를 문자열 배열로 지정 합니다. 이 cmdlet은이 공급자가 지 원하는 드라이브만 가져옵니다. 공급자 이름(예: FileSystem, Registry 또는 Certificate)을 입력합니다.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

이 cmdlet이 드라이브를 가져오는 범위를 지정 합니다.

이 매개 변수에 허용되는 값은 다음과 같습니다.

- 전역
- 로컬
- 스크립트
- 현재 범위를 기준으로 하는 숫자 (0부터 범위 수까지, 여기서 0은 현재 범위이 고 1은 부모)입니다. "Local"이 기본값입니다.

자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 개체를 파이프할 수 없습니다.

## 출력

### System.Management.Automation.PSDriveInfo

이 cmdlet은 세션의 드라이브를 나타내는 개체를 반환 합니다.

## 참고

* 이 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면 cmdlet을 사용 합니다 `Get-PSProvider` . 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조하세요.
* New-PSDrive cmdlet의 **Persist** 매개 변수를 사용 하 여 만든 매핑된 네트워크 드라이브는 사용자 계정에만 적용 됩니다. 관리자 권한으로 실행 옵션을 사용 하거나 다른 사용자의 자격 증명을 사용 하 여 시작한 세션에서 사용자가 만든 매핑된 네트워크 드라이브는 명시적 자격 증명을 사용 하지 않거나 현재 사용자의 자격 증명을 사용 하 여 시작한 세션에서는 표시 되지 않습니다.

## 관련 링크

[New-PSDrive](New-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)

[Get-PSProvider](Get-PSProvider.md)
