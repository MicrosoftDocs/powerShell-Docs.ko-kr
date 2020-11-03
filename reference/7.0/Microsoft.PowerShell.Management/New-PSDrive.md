---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-psdrive?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSDrive
ms.openlocfilehash: 71605d2c630cb456a44226ddbe2a99f92347b617
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210962"
---
# New-PSDrive

## 개요
임시 및 영구 매핑된 네트워크 드라이브를 만듭니다.

## SYNTAX

### 모두

```
New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Description <String>]
 [-Scope <String>] [-Persist] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## 설명

`New-PSDrive`Cmdlet은 네트워크 드라이브, 로컬 컴퓨터의 디렉터리, 레지스트리 키, 원격 컴퓨터의 파일 시스템 위치에 연결 된 영구 Windows 매핑된 네트워크 드라이브와 같이 데이터 저장소의 위치에 매핑되고 연결 된 임시 및 영구 드라이브를 만듭니다.

임시 드라이브는 현재 PowerShell 세션 및 현재 세션에서 만든 세션에만 존재 합니다. PowerShell에서 유효한 임의의 이름을 가질 수 있으며 모든 로컬 또는 원격 리소스에 매핑될 수 있습니다. 매핑된 네트워크 드라이브와 마찬가지로 임시 PowerShell 드라이브를 사용 하 여 연결 된 데이터 저장소의 데이터에 액세스할 수 있습니다. 를 사용 하 여 드라이브에 위치를 변경 하 `Set-Location` 고 또는을 사용 하 여 드라이브의 내용에 액세스할 수 있습니다 `Get-Item` `Get-ChildItem` .

임시 드라이브는 PowerShell에만 알려져 있으므로 파일 탐색기, WMI(Windows Management Instrumentation) (WMI), COM (구성 요소 개체 모델), Microsoft .NET 프레임 워크를 사용 하거나 **NET use** 와 같은 도구를 사용 하 여 액세스할 수 없습니다.

PowerShell 3.0에서에 추가 된 기능은 다음과 `New-PSDrive` 같습니다.

- 매핑된 네트워크 드라이브 의 **Persist** 매개 변수를 사용 `New-PSDrive` 하 여 Windows 매핑된 네트워크 드라이브를 만들 수 있습니다. 임시 PowerShell 드라이브와 달리 Windows 매핑된 네트워크 드라이브는 특정 세션에 국한 되지 않습니다. 이러한 파일은 Windows에 저장 되며 파일 탐색기 및 **net use** 와 같은 표준 windows 도구를 사용 하 여 관리할 수 있습니다. 매핑된 네트워크 드라이브는 드라이브 문자 이름을 가져야 하며 원격 파일 시스템 위치에 연결되어야 합니다. 명령의 범위가 로컬로 지정 되 고, 점 소싱이 없으면 **persist** 매개 변수는 명령이 실행 되는 범위를 벗어나 **PSDrive** 생성을 유지 하지 않습니다. `New-PSDrive`스크립트 내에서 실행 하는 경우 드라이브를 무기한으로 유지 하려면 스크립트를 점으로 원본으로 만들어야 합니다. 최상의 결과를 위해 새 드라이브를 무기한 유지 하려면 명령에 **Scope** 매개 변수를 추가 하 고 해당 값을 **Global** 로 설정 합니다. 점 소싱에 대 한 자세한 내용은 [about_Scripts](../Microsoft.PowerShell.Core/About/about_Scripts.md#script-scope-and-dot-sourcing)를 참조 하세요.
- 외부 드라이브. 외부 드라이브가 컴퓨터에 연결 되 면 PowerShell에서 자동으로 새 드라이브를 나타내는 **PSDrive** 를 파일 시스템에 추가 합니다. PowerShell을 다시 시작할 필요가 없습니다. 마찬가지로 컴퓨터에서 외부 드라이브의 연결이 끊어지면 PowerShell에서 제거 된 드라이브를 나타내는 **PSDrive** 를 자동으로 삭제 합니다.
- UNC (범용 명명 규칙) 경로에 대 한 자격 증명

**Root** 매개 변수 값이 UNC 경로 (예:) 인 경우 `\\Server\Share` **credential** 매개 변수 값에 지정 된 자격 증명을 사용 하 여 **PSDrive** 를 만듭니다. 그렇지 않으면 새 파일 시스템 드라이브를 만들 때 **자격 증명이** 유효 하지 않습니다.

일부 코드 샘플에서는 스 플랫를 사용 하 여 줄 길이를 줄이고 가독성을 향상 시킵니다. 자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.

## 예제

### 예 1: 네트워크 공유에 매핑된 임시 드라이브 만들기

이 예제에서는 네트워크 공유에 매핑된 임시 PowerShell 드라이브를 만듭니다.

```powershell
New-PSDrive -Name "Public" -PSProvider "FileSystem" -Root "\\Server01\Public"
```

```Output
Name       Provider      Root
----       --------      ----
Public     FileSystem    \\Server01\Public
```

`New-PSDrive`**Name** 매개 변수를 사용 하 여 명명 된 powershell 드라이브를 지정 하 `Public` 고 **psprovider** 매개 변수를 사용 하 여 powershell 공급자를 지정 `FileSystem` 합니다. **Root** 매개 변수는 네트워크 공유의 UNC 경로를 지정 합니다.

PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path Public:`

### 예 2: 로컬 디렉터리에 매핑된 임시 드라이브 만들기

이 예제에서는 로컬 컴퓨터의 디렉터리에 대 한 액세스를 제공 하는 임시 PowerShell 드라이브를 만듭니다.

```powershell
$parameters = @{
    Name = "MyDocs"
    PSProvider = "FileSystem"
    Root = "C:\Users\User01\Documents"
    Description = "Maps to my My Documents folder."
}
New-PSDrive @parameters
```

```Output
Name        Provider      Root
----        --------      ----
MyDocs      FileSystem    C:\Users\User01\Documents
```

스 플랫는 매개 변수 키 및 값을 만듭니다. **Name** 매개 변수는 드라이브 이름 **mydocs** 를 지정 합니다. **Psprovider** 매개 변수는 PowerShell 공급자를 지정 합니다 `FileSystem` . **Root** 로컬 컴퓨터의 디렉터리를 지정 합니다. **Description** 매개 변수는 드라이브의 용도를 설명 합니다. `New-PSDrive` splatted 매개 변수를 사용 하 여 `MyDocs` 드라이브를 만듭니다.

PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path MyDocs:`

### 예 3: 레지스트리 키에 대 한 임시 드라이브 만들기

이 예제에서는 레지스트리 키에 대 한 액세스를 제공 하는 임시 PowerShell 드라이브를 만듭니다. 레지스트리 키에 매핑되는 MyCompany 라는 드라이브를 만듭니다 `HKLM:\Software\MyCompany` .

```powershell
New-PSDrive -Name "MyCompany" -PSProvider "Registry" -Root "HKLM:\Software\MyCompany"
```

```Output
Name           Provider      Root
----           --------      ----
MyCompany      Registry      HKLM:\Software\MyCompany
```

`New-PSDrive`**Name** 매개 변수를 사용 하 여 명명 된 powershell 드라이브를 지정 하 `MyCompany` 고 **psprovider** 매개 변수를 사용 하 여 powershell 공급자를 지정 `Registry` 합니다. **Root** 매개 변수는 레지스트리 위치를 지정 합니다.

PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path MyCompany:`

### 예제 4: 자격 증명을 사용 하 여 영구 매핑된 네트워크 드라이브 만들기

이 예제에서는 도메인 서비스 계정의 자격 증명을 사용 하 여 인증 된 네트워크 드라이브를 매핑합니다.
자격 증명을 저장 하는 **PSCredential** 개체 및 암호를 **SecureString** 으로 저장 하는 방법에 대 한 자세한 내용은 **Credential** 매개 변수의 설명을 참조 하십시오.

```powershell
$cred = Get-Credential -Credential Contoso\ServiceAccount
New-PSDrive -Name "S" -Root "\\Server01\Scripts" -Persist -PSProvider "FileSystem" -Credential $cred
Net Use
```

```Output
Status       Local     Remote                    Network
---------------------------------------------------------
OK           S:        \\Server01\Scripts        Microsoft Windows Network
```

> [!NOTE]
> 스크립트에서 위의 코드 조각을 사용 하는 경우 **범위** 매개 변수 값을 "Global"로 설정 하 여 드라이브가 현재 범위를 벗어나 유지 되도록 하십시오.

`$cred`변수는 서비스 계정의 자격 증명을 포함 하는 **PSCredential** 개체를 저장 합니다. `Get-Credential`**SecureString** 에 저장 된 암호를 입력 하 라는 메시지를 표시 합니다.

`New-PSDrive` 여러 매개 변수를 사용 하 여 매핑된 네트워크 드라이브를 만듭니다. **이름** Windows에서 `S` 허용 하는 드라이브 문자를 지정 합니다. 및 **Root** `\\Server01\Scripts` 는 원격 컴퓨터의 위치로 정의 됩니다. **지속** 은 로컬 컴퓨터에 저장 되는 Windows 매핑된 네트워크 드라이브를 만듭니다. **Psprovider** 는 공급자를 지정 합니다 `FileSystem` . **자격 증명** 은 `$cred` 변수를 사용 하 여 인증을 위한 서비스 계정 자격 증명을 가져옵니다.

매핑된 드라이브는 PowerShell 세션, 파일 탐색기 및 **net use** 와 같은 도구를 사용 하 여 로컬 컴퓨터에서 볼 수 있습니다. PowerShell 세션에서 콘텐츠를 보려면 다음을 수행 합니다. `Get-ChildItem -Path S:`

### 예 5: 영구 및 임시 드라이브 만들기

이 예제에서는 영구 매핑된 네트워크 드라이브와 동일한 네트워크 공유에 매핑된 임시 PowerShell 드라이브 간의 차이점을 보여 줍니다.

PowerShell 세션을 닫은 다음 새 세션을 열면 임시를 `PSDrive:` 사용할 수 없지만 영구 `X:` 드라이브를 사용할 수 있습니다. 네트워크 드라이브를 매핑하는 데 사용할 방법을 결정 하는 경우 드라이브를 사용 하는 방법을 고려 합니다. 예를 들어 영구적인 지 여부 및 드라이브를 다른 Windows 기능에 표시 해야 하는지 여부입니다.

```powershell
# Create a temporary PowerShell drive called PSDrive:
# that's mapped to the \\Server01\Public network share.
New-PSDrive -Name "PSDrive" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Use the Persist parameter of New-PSDrive to create the X: mapped network drive,
# which is also mapped to the \\Server01\Public network share.
New-PSDrive -Persist -Name "X" -PSProvider "FileSystem" -Root "\\Server01\Public"

# Now, you can use the Get-PSDrive drive cmdlet to examine the two drives.
# The drives appear to be the same, although the network share name appears only
# in the root of the PSDrive: drive.
Get-PSDrive -Name "PSDrive", "X"
```

```Output
Name       Provider      Root
----       --------      ----

PsDrive    FileSystem    \\Server01\public
X          FileSystem    X:\
```

```powershell
# Get-Member cmdlet shows that the drives have the same object type,
# System.Management.Automation.PSDriveInfo.
Get-PSDrive "PSDrive", "x" | Get-Member
```

```Output
TypeName: System.Management.Automation.PSDriveInfo

Name                MemberType   Definition
----                ----------   ----------
CompareTo           Method       System.Int32 CompareTo(PSDriveInfo drive),
Equals              Method       System.Boolean Equals(Object obj),
GetHashCode         Method       System.Int32 GetHashCode()
...
```

```powershell
# Net Use and Get-CimInstance for the Win32_LogicalDisk class,
# and Win32_NetworkConnection class find only the persistent X: drive.
# PowerShell temporary drives are known only to PowerShell.
Net Use
Get-CimInstance Win32_LogicalDisk | Format-Table -Property DeviceID
Get-CimInstance Win32_NetworkConnection
```

```Output
Status       Local     Remote                    Network
--------------------------------------------------------
OK           X:        \\contoso-pc\data         Microsoft Windows Network

deviceid
--------
C:
D:
X:

LocalName    RemoteName              ConnectionState          Status
---------    ----------              ---------------          ------
X:           \\products\public       Disconnected             Unavailable
```

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

### -Credential

이 작업을 수행할 수 있는 권한이 있는 사용자 계정을 지정 합니다. 기본값은 현재 사용자입니다.

PowerShell 3.0부터 **Root** 매개 변수 값이 UNC 경로인 경우 자격 증명을 사용 하 여 파일 시스템 드라이브를 만들 수 있습니다.

**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` . 사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.

자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.

> [!NOTE]
> **Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### -Description

드라이브에 대한 간단한 텍스트 설명을 지정합니다. 문자열을 입력합니다.

모든 세션 드라이브에 대 한 설명을 보려면를 참조 하십시오 `Get-PSDrive | Format-Table Name, Description` .

특정 드라이브에 대 한 설명을 보려면을 입력 `(Get-PSDrive <DriveName>).Description` 합니다.

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

### -Name

새 드라이브의 이름을 지정합니다. 영구 매핑된 네트워크 드라이브의 경우 드라이브 문자를 사용 합니다. 임시 PowerShell 드라이브의 경우 드라이브 문자로 제한 되지 않으며 유효한 문자열을 사용 합니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -유지

이 cmdlet이 Windows 매핑된 네트워크 드라이브를 생성 함을 나타냅니다. **Persist** 매개 변수는 Windows 에서만 사용할 수 있습니다.

매핑된 네트워크 드라이브는 로컬 컴퓨터의 Windows에 저장됩니다. 이러한 파일은 세션에 한정 되지 않고 영구적 이며 파일 탐색기 및 기타 도구에서 보고 관리할 수 있습니다.

점 소싱을 사용 하지 않고 로컬로 명령 범위를 설정한 경우 **persist** 매개 변수는 명령을 실행 하는 범위를 벗어나 **PSDrive** 생성을 유지 하지 않습니다. `New-PSDrive`스크립트 내에서를 실행 하는 경우 새 드라이브를 무기한 유지 하려면 스크립트를 점으로 원본으로 만들어야 합니다. 최상의 결과를 위해 새 드라이브를 강제로 유지 하려면 **Scope** 매개 변수 값으로 **Global** 을 지정 하 고 명령에 **persist** 를 포함 합니다.

드라이브의 이름은 문자 (예: 또는) 여야 합니다 `D` `E` . **Root** 매개 변수 값은 다른 컴퓨터의 UNC 경로 여야 합니다. **Psprovider** 매개 변수의 값은 이어야 합니다 `FileSystem` .

Windows 매핑된 네트워크 드라이브의 연결을 끊으려면 cmdlet을 사용 `Remove-PSDrive` 합니다. Windows 매핑된 네트워크 드라이브 연결을 끊으면 매핑이 현재 세션에서 삭제될 뿐만 아니라 컴퓨터에서도 영구적으로 삭제됩니다.

매핑된 네트워크 드라이브는 특정 사용자 계정에만 적용됩니다. 다른 사용자의 자격 증명을 사용 하 여 다른 사용자의 자격 증명을 사용 하는 세션에서 만든 매핑된 드라이브는 다른 자격 증명을 사용 하 여 시작 된 세션

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -PSProvider

이러한 종류의 드라이브를 지 원하는 PowerShell 공급자를 지정 합니다.

예를 들어 드라이브가 네트워크 공유 또는 파일 시스템 디렉터리와 연결 된 경우 PowerShell 공급자는 `FileSystem` 입니다. 드라이브가 레지스트리 키와 연결 된 경우 공급자는 `Registry` 입니다.

임시 PowerShell 드라이브를 PowerShell 공급자와 연결할 수 있습니다. 매핑된 네트워크 드라이브는 공급자에만 연결할 수 있습니다 `FileSystem` .

PowerShell 세션에서 공급자 목록을 보려면 cmdlet을 사용 합니다 `Get-PSProvider` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -루트

PowerShell 드라이브가 매핑된 데이터 저장소 위치를 지정 합니다.

예를 들어와 같은 네트워크 공유 또는와 같은 `\\Server01\Public` `C:\Program Files` 레지스트리 키를 지정 `HKLM:\Software\Microsoft` 합니다.

임시 PowerShell 드라이브는 지원 되는 모든 공급자 드라이브의 로컬 또는 원격 위치에 연결할 수 있습니다. 매핑된 네트워크 드라이브는 원격 컴퓨터의 파일 시스템 위치에만 연결할 수 있습니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -범위

드라이브의 범위를 지정합니다. 이 매개 변수에 허용 되는 값은 **전역** , **로컬** 및 **스크립트** 이거나 현재 범위를 기준으로 하는 숫자입니다. 범위는 0에서 범위 수 까지입니다. 현재 범위 번호는 0이 고 해당 부모는 1입니다. 자세한 내용은 [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: True (ByPropertyName)
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

### 없음

이 cmdlet에 대 한 입력을 파이프라인으로 지정할 수 없습니다.

## 출력

### System.Management.Automation.PSDriveInfo

## 참고

`New-PSDrive` 는 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면를 사용 `Get-PSProvider` 합니다. 공급자에 대 한 자세한 내용은 [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)를 참조 하세요.

매핑된 네트워크 드라이브는 특정 사용자 계정에만 적용됩니다. 다른 사용자의 자격 증명을 사용 하 여 다른 사용자의 자격 증명을 사용 하는 세션에서 만든 매핑된 드라이브는 다른 자격 증명을 사용 하 여 시작 된 세션

## 관련 링크

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

[Get-Credential](../Microsoft.PowerShell.Security/Get-Credential.md)

[Get-PSDrive](Get-PSDrive.md)

[Remove-PSDrive](Remove-PSDrive.md)
