---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Windows PowerShell 드라이브 관리
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215514"
---
# <a name="managing-windows-powershell-drives"></a>Windows PowerShell 드라이브 관리

*Windows PowerShell 드라이브*는 Windows PowerShell의 파일 시스템 드라이브처럼 사용자가 액세스할 수 있는 데이터 저장소 위치입니다. Windows PowerShell 공급자가 파일 시스템 드라이브(C: 및 D: 포함), 레지스트리 드라이브(HKCU: 및 HKLM:), 인증서 드라이브(Cert:) 등과 같은 일부 드라이브를 만들고, 사용자는 자신의 Windows PowerShell 드라이브를 만들 수 있습니다. 이러한 드라이브는 매우 유용하지만 Windows PowerShell 내에서만 사용할 수 있습니다. 파일 탐색기, Cmd.exe 등과 같은 다른 Windows 도구를 사용하여 이 드라이브에 액세스할 수 없습니다.

Windows PowerShell에서는 Windows PowerShell 드라이브 작업을 위한 명령에 명사 **PSDrive**를 사용합니다. Windows PowerShell 세션의 Windows PowerShell 드라이브 목록을 보려면 **Get-PSDrive** cmdlet을 사용합니다.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

표시되는 드라이브는 시스템의 드라이브에 따라 다르지만 목록은 위에 표시된 **Get-PSDrive** 명령의 출력과 비슷합니다.

파일 시스템 드라이브는 Windows PowerShell 드라이브의 하위 집합입니다. 공급자 열의 FileSystem 항목으로 파일 시스템 드라이브를 식별할 수 있습니다. Windows PowerShell FileSystem 공급자는 Windows PowerShell의 파일 시스템 드라이브를 지원합니다.

**Get-PSDrive** cmdlet의 구문을 보려면 **Get-Command** 명령을 **Syntax** 매개 변수와 함께 입력합니다.

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

**PSProvider** 매개 변수를 사용하면 특정 공급자가 지원하는 Windows PowerShell 드라이브만 표시할 수 있습니다. 예를 들어 Windows PowerShell FileSystem 공급자가 지원하는 Windows PowerShell 드라이브만 표시하려면 **Get-PSDrive** 명령을 **PSProvider** 매개 변수 및 **FileSystem** 값과 함께 입력합니다.

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

레지스트리 하이브를 나타내는 Windows PowerShell 드라이브를 보려면 **PSProvider** 매개 변수를 사용하여 Windows PowerShell 레지스트리 공급자가 지원하는 Windows PowerShell 드라이브만 표시합니다.

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

표준 위치 cmdlet을 Windows PowerShell 드라이브와 함께 사용할 수도 있습니다.

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>새 Windows PowerShell 드라이브 추가(New-PSDrive)

**New-PSDrive** 명령을 사용하여 자체 Windows PowerShell 드라이브를 추가할 수 있습니다. **New-PSDrive** 명령의 구문을 가져오려면 **Get-Command** 명령을 **Syntax** 매개 변수와 함께 입력합니다.

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

새 Windows PowerShell 드라이브를 만들려면 다음과 같은 세 가지 매개 변수를 제공해야 합니다.

- 드라이브의 이름(모든 유효한 Windows PowerShell 이름 사용 가능)

- PSProvider(파일 시스템 위치의 경우 "FileSystem", 레지스트리 위치의 경우 "Registry" 사용)

- 루트(새 드라이브의 루트 경로)

예를 들어 컴퓨터의 Microsoft Office 애플리케이션을 포함하는 폴더에 매핑되는 "Office" 드라이브를 만들 수 있습니다(예: **C:\\Program Files\\Microsoft Office\\OFFICE11**). 드라이브를 만들려면 다음 명령을 입력합니다.

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> 일반적으로 경로는 대/소문자를 구분하지 않습니다.

모든 Windows PowerShell 드라이브를 나타낼 때와 마찬가지로 이름 뒤에 콜론( **:** )을 사용하여 새 Windows PowerShell 드라이브를 나타냅니다.

Windows PowerShell 드라이브를 사용하면 많은 작업을 훨씬 간편하게 수행할 수 있습니다. 예를 들어 Windows 레지스트리의 가장 중요한 일부 키는 매우 긴 경로를 사용하여 액세스하기 번거롭고 기억하기 어렵습니다. 중요 구성 정보는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion** 아래에 있습니다. CurrentVersion 레지스트리 키의 항목을 보고 변경하려면 다음과 같이 입력하여 해당 키의 루트로 사용할 Windows PowerShell 드라이브를 만들 수 있습니다.

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

그런 다음 다른 드라이브와 마찬가지로 위치를 **cvkey:** 드라이브로 변경할 수 있습니다.

```
PS> cd cvkey:
```

또는:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

New-PsDrive cmdlet은 현재 Windows PowerShell 세션에만 새 드라이브를 추가합니다. 따라서 Windows PowerShell 창을 닫으면 새 드라이브가 손실됩니다. Windows PowerShell 드라이브를 저장하려면 Export-Console cmdlet을 사용하여 현재 Windows PowerShell 세션을 내보낸 다음 PowerShell.exe **PSConsoleFile** 매개 변수를 사용하여 가져옵니다. 또는 새 드라이브를 Windows PowerShell 프로필에 추가합니다.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Windows PowerShell 드라이브 삭제(Remove-PSDrive)

**Remove-PSDrive** cmdlet을 사용하여 Windows PowerShell에서 드라이브를 삭제할 수 있습니다. **Remove-PSDrive** cmdlet은 사용하기 쉽습니다. 특정 Windows PowerShell 드라이브를 삭제하려면 Windows PowerShell 드라이브 이름을 제공합니다.

예를 들어 **Office:** Windows PowerShell 드라이브를 추가한 경우(**New-PSDrive** 항목 참조) 다음과 같이 입력하여 해당 드라이브를 삭제할 수 있습니다.

```powershell
Remove-PSDrive -Name Office
```

**cvkey:** Windows PowerShell 드라이브(**New-PSDrive** 항목에도 표시됨)를 삭제하려면 다음 명령을 사용합니다.

```powershell
Remove-PSDrive -Name cvkey
```

Windows PowerShell 드라이브는 쉽게 삭제할 수 있지만 드라이브 내에서는 삭제할 수 없습니다. 예:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Windows PowerShell 외부 드라이브 추가 및 제거

Windows PowerShell은 Windows에서 추가되거나 제거된 파일 시스템 드라이브(매핑되는 네트워크 드라이브, 연결된 USB 드라이브, WSH(Windows 스크립트 호스트) 스크립트에서 **net use** 명령 또는 **WScript.NetworkMapNetworkDrive** 및 **RemoveNetworkDrive** 메서드를 사용하여 삭제한 드라이브 등)를 검색합니다.
