---
description: 레지스트리
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 레지스트리 공급자
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599741"
---
# <a name="registry-provider"></a>레지스트리 공급자

## <a name="provider-name"></a>공급자 이름

레지스트리

## <a name="drives"></a>드라이브

`HKLM:`, `HKCU:`

## <a name="capabilities"></a>기능

**Shouldprocess**, **UseTransactions**

## <a name="short-description"></a>간단한 설명

PowerShell에서 레지스트리 키, 항목 및 값에 대 한 액세스를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

PowerShell **레지스트리** 공급자를 사용 하 여 powershell에서 레지스트리 키, 항목 및 값을 가져오고 추가, 변경 및 삭제할 수 있습니다.

**레지스트리** 드라이브는 컴퓨터의 레지스트리 키와 하위 키를 포함 하는 계층적 네임 스페이스입니다. 레지스트리 항목 및 값은 이러한 계층 구조의 구성 요소가 아니라 각 키의 속성입니다.

**레지스트리** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

레지스트리 키는 [Microsoft Win32 RegistryKey](/dotnet/api/microsoft.win32.registrykey) 클래스의 인스턴스로 표시 됩니다. 레지스트리 항목은 [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) 클래스의 인스턴스로 표시 됩니다.

## <a name="navigating-the-registry-drives"></a>레지스트리 드라이브 탐색

**레지스트리** 공급자는 해당 데이터 저장소를 두 개의 기본 드라이브로 노출 합니다. HKEY_LOCAL_MACHINE 레지스트리 위치는 드라이브에 매핑되고 `HKLM:` HKEY_CURRENT_USER는 드라이브에 매핑됩니다 `HKCU:` . 레지스트리를 사용 하려면 `HKLM:` 다음 명령을 사용 하 여 해당 위치를 드라이브로 변경할 수 있습니다.

```powershell
Set-Location HKLM:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 **레지스트리** 공급자를 사용할 수도 있습니다. 다른 위치에서 레지스트리 키를 참조 하려면 경로에 드라이브 이름 ( `HKLM:` ,)을 사용 `HKCU:` 합니다. 백슬래시 ( \\ ) 또는 슬래시 (/)를 사용 하 여 **레지스트리** 드라이브의 수준을 표시 합니다.

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭이 고, `cd` 는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭이 고, `pwd` 은 (는 [) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

마지막 예제에서는 **레지스트리** 공급자를 탐색 하는 데 사용할 수 있는 다른 경로 구문을 보여 줍니다. 이 구문에서는 공급자 이름과 두 개의 콜론이 차례로 사용 `::` 됩니다. 이 구문을 사용 하면 매핑된 드라이브 이름 대신 전체 하이브 이름을 사용할 수 있습니다 `HKLM` .

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a>레지스트리 키의 내용 표시

레지스트리는 키, 하위 키 및 항목으로 나뉩니다. 레지스트리 구조에 대 한 자세한 내용은 [레지스트리 구조](/windows/desktop/sysinfo/structure-of-the-registry)를 참조 하세요.

**레지스트리** 드라이브에서 각 키는 컨테이너입니다. 키에는 원하는 수 만큼의 키가 포함 될 수 있습니다. 부모 키가 있는 레지스트리 키를 하위 키 라고 합니다. 를 사용 하 여 `Get-ChildItem` 레지스트리 키를 보고 `Set-Location` 키 경로를 탐색할 수 있습니다.

레지스트리 값은 레지스트리 키의 특성입니다. **레지스트리** 드라이브에서는 **항목 속성** 이라고 합니다. 레지스트리 키에는 자식 키와 항목 속성이 모두 포함 될 수 있습니다.

이 예에서는와의 차이가 `Get-Item` `Get-ChildItem` 표시 됩니다. `Get-Item`"스풀러" 레지스트리 키에서를 사용 하는 경우 해당 속성을 볼 수 있습니다.

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

각 레지스트리 키에는 하위 키도 있을 수 있습니다. `Get-Item`레지스트리 키에서를 사용 하는 경우 하위 키가 표시 되지 않습니다. `Get-ChildItem`이 cmdlet은 각 하위 키의 속성을 포함 하 여 "스풀러" 키의 자식 항목을 표시 합니다. 을 사용할 때는 부모 키 속성이 표시 되지 않습니다 `Get-ChildItem` .

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

이 `Get-Item` cmdlet은 현재 위치에서 사용할 수도 있습니다. 다음 예제에서는 "스풀러" 레지스트리 키로 이동 하 여 항목 속성을 가져옵니다.
점은 `.` 현재 위치를 나타내는 데 사용 됩니다.

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

이 섹션에서 설명 하는 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.

-[항목 가져오기](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

## <a name="viewing-registry-key-values"></a>레지스트리 키 값 보기

레지스트리 키 값은 각 레지스트리 키의 속성으로 저장 됩니다. `Get-ItemProperty`Cmdlet은 지정한 이름을 사용 하 여 레지스트리 키 속성을 봅니다. 결과는 사용자가 지정 하는 속성을 포함 하는 **PSCustomObject** 입니다.

다음 예에서는 cmdlet을 사용 하 여 `Get-ItemProperty` 모든 속성을 표시 합니다. 결과 개체를 변수에 저장 하면 원하는 속성 값에 액세스할 수 있습니다.

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

매개 변수의 값을 지정 `-Name` 하면 사용자가 지정 하는 속성이 선택 되 고 **PSCustomObject** 이 반환 됩니다.  다음 예제에서는 매개 변수를 사용할 때 출력의 차이점을 보여 줍니다 `-Name` .

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

PowerShell 5.0부터 `Get-ItemPropertyValue` cmdlet은 지정한 속성 값만 반환 합니다.

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Get-ItemPropertyValue](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a>레지스트리 키 값 변경

`Set-ItemProperty`Cmdlet은 레지스트리 키에 대 한 특성을 설정 합니다. 다음 예에서는 `Set-ItemProperty` 를 사용 하 여 스풀러 서비스 시작 유형을 수동으로 변경 합니다. 이 예에서는 cmdlet을 사용 하 여 **Starttype** 을 *자동* 으로 다시 변경 합니다 `Set-Service` .

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

각 레지스트리 키에는 *기본값이* 있습니다. 또는 중 하나를 사용 하 여 레지스트리 키에 대 한 *기본값* 을 변경할 수 있습니다 `Set-Item` `Set-ItemProperty` .

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a>레지스트리 키 및 값 만들기

`New-Item`Cmdlet은 사용자가 제공한 이름을 사용 하 여 레지스트리 키를 만듭니다.
`mkdir`Cmdlet을 내부적으로 호출 하는 함수를 사용할 수도 있습니다 `New-Item` .

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

Cmdlet을 사용 `New-ItemProperty` 하 여 지정 하는 레지스트리 키에 값을 만들 수 있습니다. 다음 예에서는 ContosoCompany 레지스트리 키에 새 DWORD 값을 만듭니다.

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> 허용 되는 다른 유형 값에 대해서는이 문서의 동적 매개 변수 섹션을 검토 합니다.

자세한 cmdlet 사용법은 [get-itemproperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)를 참조 하세요.

## <a name="copying-registry-keys-and-values"></a>레지스트리 키 및 값 복사

**레지스트리** 공급자에서 cmdlet을 사용 하 여 `Copy-Item` 레지스트리 키와 값을 복사 합니다. Cmdlet을 사용 `Copy-ItemProperty` 하 여 레지스트리 값만 복사 합니다.
다음 명령은 "Contoso" 레지스트리 키와 해당 속성을 지정 된 위치 "HKLM: \ Software\Fabrikam"에 복사 합니다.

`Copy-Item` 대상 키가 없는 경우 해당 키를 만듭니다. 대상 키가 있으면에서 `Copy-Item` 원본 키의 복제본을 대상 키의 자식 항목 (하위 키)으로 만듭니다.

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

다음 명령은 cmdlet을 사용 하 여 " `Copy-ItemProperty` Contoso" 키의 "서버" 값을 "Fabrikam" 키에 복사 합니다.

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a>레지스트리 키 및 값 이동

`Move-Item`및 `Move-ItemProperty` cmdlet은 "복사" 대응 항목 처럼 동작 합니다. 대상이 있으면에서 `Move-Item` 원본 키를 대상 키 아래로 이동 합니다. 대상 키가 없으면 원본 키가 대상 경로로 이동 합니다.

다음 명령은 "Contoso" 키를 "HKLM: \ \S\fabrikam" 경로로 이동 합니다.

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

이 명령은 "HKLM: \ SOFTWARE\ContosoCompany"의 모든 속성을 "HKLM: \ \S\fabrikam"으로 이동 합니다.

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

이 섹션에 사용 된 cmdlet에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a>레지스트리 키 및 값 이름 바꾸기

파일 및 폴더와 마찬가지로 레지스트리 키와 값의 이름을 바꿀 수 있습니다.
`Rename-Item` 레지스트리 키의 이름을 바꾸고 레지스트리 `Rename-ItemProperty` 값의 이름을 바꿉니다.

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a>보안 설명자 변경

및 cmdlet을 사용 하 여 레지스트리 키에 대 한 액세스를 제한할 수 있습니다 `Get-Acl` `Set-Acl` . 다음 예에서는 모든 권한이 있는 새 사용자를 "HKLM: \ \Ent\contoso" 레지스트리 키에 추가 합니다.

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

더 많은 예제 및 cmdlet 사용 세부 정보는 다음 문서를 참조 하세요.

- [Get-Acl](xref:Microsoft.PowerShell.Security.Get-Acl)
- [Set-Acl](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a>레지스트리 키 및 값 제거 및 지우기

**제거 항목** 을 사용 하 여 포함 된 항목을 제거할 수 있지만 항목에 다른 항목이 들어 있는 경우 제거를 확인 하는 메시지가 표시 됩니다. 다음 예에서는 "HKLM: \ SOFTWARE\Contoso" 키를 삭제 하려고 시도 합니다.

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

메시지를 표시 하지 않고 포함 된 항목을 삭제 하려면 `-Recurse` 매개 변수를 지정 합니다.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

"Hklm: \ software\contoso" 내에서 모든 항목을 제거 하 고 "HKLM: \ SOFTWARE\Contoso" 자체를 제거 하려는 경우 후행 백슬래시 `\` 와 와일드 카드를 사용 합니다.

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

이 명령은 "HKLM: \ ContosoTest \Contoso" 레지스트리 키에서 "" 레지스트리 값을 삭제 합니다.

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

`Clear-Item` 키에 대 한 레지스트리 값을 모두 지웁니다. 다음 예에서는 "HKLM: \ SOFTWARE\Contoso" 레지스트리 키에서 모든 값을 지웁니다. 특정 속성만 지우려면를 사용 `Clear-ItemProperty` 합니다.

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

더 많은 예제 및 cmdlet 사용 세부 정보는 다음 문서를 참조 하세요.

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

### <a name="type-microsoftwin32registryvaluekind"></a><RegistryValueKind를 입력>

레지스트리 값의 데이터 형식을 설정하거나 변경합니다. 기본값은 `String` (REG_SZ)입니다.

이 매개 변수는 [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet에서 제대로 작동합니다. 또한 레지스트리 드라이브의 [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet에도 사용할 수 있지만 효과는 없습니다.

|값 | 설명 |
| ---- | ----------- |
| `String` | null로 끝나는 문자열을 지정합니다. REG_SZ와 같습니다. |
| `ExpandString` | 확장 되지 않은를 포함 하는 null로 끝나는 문자열을 지정 합니다. |
|                | 다음 경우에 확장 되는 환경 변수에 대 한 참조 |
|                | 값이 검색 됩니다. REG_EXPAND_SZ와 같습니다. |
| `Binary` | 임의의 형식으로 된 이진 데이터를 지정합니다. REG_BINARY와 같습니다. |
| `DWord` | 32비트 이진수를 지정합니다. REG_DWORD와 같습니다. |
| `MultiString` | 에서 종료 하는 null로 끝나는 문자열의 배열을 지정 합니다. |
|               | 두 null 문자 REG_MULTI_SZ와 같습니다. |
| `QWord` | 64비트 이진수를 지정합니다. REG_QWORD와 같습니다. |
| `Unknown` | 지원 되지 않는 레지스트리 데이터 형식을 나타냅니다 (예:). |
|           | REG_RESOURCE_LIST. |

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다. 공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 `Get-Help` 파일 시스템 드라이브에서 명령을 실행 하거나 **Path** 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a>참고 항목

 [about_Providers](../About/about_Providers.md)

