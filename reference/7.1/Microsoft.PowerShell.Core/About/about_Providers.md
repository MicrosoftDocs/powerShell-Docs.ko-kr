---
description: PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다. 데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/27/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_providers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Providers
ms.openlocfilehash: 08ea1679516b58e326eeb3d90fc1aaef4e983a34
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93224033"
---
# <a name="about-providers"></a>공급자 정보

## <a name="short-description"></a>간단한 설명
PowerShell 공급자가 명령줄에서 다른 방법으로 쉽게 액세스할 수 없는 데이터 및 구성 요소에 대 한 액세스를 제공 하는 방법을 설명 합니다.
데이터는 파일 시스템 드라이브와 비슷한 일관 된 형식으로 제공 됩니다.

## <a name="long-description"></a>자세한 설명입니다.

PowerShell 공급자는 보기 및 관리를 용이 하 게 하는 특수 한 데이터 저장소에 대 한 액세스를 제공 하는 .NET 프로그램입니다. 데이터는 드라이브에 표시 되며 하드 디스크 드라이브와 같은 경로에 있는 데이터에 액세스 합니다. 공급자가 지 원하는 기본 제공 cmdlet 중 하나를 사용 하 여 공급자 드라이브의 데이터를 관리할 수 있습니다. 데이터에 대해 특별히 디자인 된 사용자 지정 cmdlet을 사용할 수 있습니다.

공급자는 기본 제공 cmdlet에 동적 매개 변수를 추가할 수도 있습니다. 이러한 매개 변수는 공급자 데이터와 함께 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

## <a name="built-in-providers"></a>기본 제공 공급자

PowerShell에는 다양 한 유형의 데이터 저장소에 액세스 하는 데 사용할 수 있는 기본 제공 공급자 집합이 포함 되어 있습니다.

| 공급자   |   개 드라이브  |OutputType                                                    |
|----------- |------------ |--------------------------------------------------------------|
|Alias       |별칭:       |System.management.automation.aliasinfo.                        |
|인증서 |인증서:        |Microsoft.powershell.commands.x509storelocation.               |
|            |             |System.Security.Cryptography.X509Certificates.X509Certificate2|
|Environment |Env:         |DictionaryEntry                            |
|FileSystem  |C: (*)       |System.object                                            |
|            |             |System.io.directoryinfo                                       |
|함수    |함수:    |System.object를 관리 합니다.                     |
|레지스트리    |HKLM: HKCU:  |Microsoft Win32 RegistryKey                                   |
|변수    |변수:    |System.object입니다.                       |
|WSMan       |WSMan:       |에서 wsmanconfigcontainerelement가.        |

(*) 파일 시스템 드라이브는 각 시스템 마다 다릅니다.

사용자 고유의 PowerShell 공급자를 만들 수도 있으며, 다른 사용자가 개발 하는 공급자를 설치할 수도 있습니다. 세션에서 사용할 수 있는 공급자를 나열 하려면 다음을 입력 합니다.

```powershell
Get-PSProvider
```

## <a name="installing-and-removing-providers"></a>공급자 설치 및 제거

공급자는 일반적으로 PowerShell 모듈을 통해 설치 됩니다. 모듈을 가져오면 해당 공급자가 세션으로 로드 됩니다. 기본 제공 공급자를 제거할 수 없습니다. 다른 모듈에 의해 로드 된 공급자를 제거할 수 있습니다.

Cmdlet을 사용 하 여 현재 세션에서 공급자를 언로드할 수 있습니다 `Remove-Module` . 이 cmdlet은 공급자를 제거 하지 않지만 해당 공급자를 세션에서 사용할 수 없게 만듭니다.

Cmdlet을 사용 하 여 `Remove-PSDrive` 현재 세션에서 드라이브를 제거할 수도 있습니다. 드라이브의이 데이터는 영향을 받지 않지만 해당 세션에서 더 이상 드라이브를 사용할 수 없습니다.

## <a name="viewing-providers"></a>공급자 보기

컴퓨터에서 PowerShell 공급자를 보려면 다음을 입력 합니다.

```powershell
Get-PSProvider
```

출력에는 기본 제공 공급자와 세션에 추가한 공급자가 나열 됩니다.

## <a name="the-provider-cmdlets"></a>공급자 cmdlet

다음 cmdlet은 모든 공급자가 제공 하는 데이터에 사용할 수 있도록 설계 되었습니다. 동일한 방식으로 동일한 cmdlet을 사용 하 여 공급자가 노출 하는 다양 한 데이터 형식을 관리할 수 있습니다. 한 공급자의 데이터를 관리 하는 방법을 학습 한 후에는 모든 공급자의 데이터와 동일한 절차를 사용할 수 있습니다.

예를 들어 `New-Item` cmdlet은 새 항목을 만듭니다. `C:` **FileSystem** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 파일이 나 폴더를 만들 수 있습니다. **레지스트리** 공급자가 지 원하는 드라이브에서를 사용 `New-Item` 하 여 새 레지스트리 키를 만들 수 있습니다. 드라이브에서를 `Alias:` 사용 `New-Item` 하 여 새 별칭을 만들 수 있습니다.

다음 cmdlet에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```
Get-Help <cmdlet-name> -Detailed
```

### <a name="childitem-cmdlets"></a>ChildItem cmdlet

- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

### <a name="content-cmdlets"></a>콘텐츠 Cmdlet

- [Add-Content](xref:Microsoft.PowerShell.Management.Add-Content)
- [Clear-Content](xref:Microsoft.PowerShell.Management.Clear-Content)
- [Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)
- [Set-Content](xref:Microsoft.PowerShell.Management.Set-Content)

### <a name="item-cmdlets"></a>항목 Cmdlet

- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)
- [Copy-Item](xref:Microsoft.PowerShell.Management.Copy-Item)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [Invoke-Item](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [Move-Item](xref:Microsoft.PowerShell.Management.Move-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Rename-Item](xref:Microsoft.PowerShell.Management.Rename-Item)
- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

### <a name="itemproperty-cmdlets"></a>Get-itemproperty cmdlet

- [Clear-ItemProperty](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [Copy-ItemProperty](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)
- [Get-ItemProperty](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [Move-ItemProperty](xref:Microsoft.PowerShell.Management.Move-ItemProperty)
- [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty)
- [Remove-ItemProperty](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [Rename-ItemProperty](xref:Microsoft.PowerShell.Management.Rename-ItemProperty)
- [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

### <a name="location-cmdlets"></a>위치 cmdlet

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Pop-Location](xref:Microsoft.PowerShell.Management.Pop-Location)
- [Push-Location](xref:Microsoft.PowerShell.Management.Push-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)

### <a name="path-cmdlets"></a>경로 cmdlet

- [Join-Path](xref:Microsoft.PowerShell.Management.Join-Path)
- [Convert-Path](xref:Microsoft.PowerShell.Management.Convert-Path)
- [Split-Path](xref:Microsoft.PowerShell.Management.Split-Path)
- [Resolve-Path](xref:Microsoft.PowerShell.Management.Resolve-Path)
- [Test-Path](xref:Microsoft.PowerShell.Management.Test-Path)

### <a name="psdrive-cmdlets"></a>PSDrive cmdlet

- [Get-PSDrive](xref:Microsoft.PowerShell.Management.Get-PSDrive)
- [New-PSDrive](xref:Microsoft.PowerShell.Management.New-PSDrive)
- [Remove-PSDrive](xref:Microsoft.PowerShell.Management.Remove-PSDrive)

### <a name="psprovider-cmdlets"></a>PSProvider Cmdlet

- [Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

## <a name="viewing-provider-data"></a>공급자 데이터 보기

공급자의 주요 장점은 친숙 하 고 일관 된 방식으로 데이터를 노출 한다는 것입니다. 데이터 프레젠테이션용 모델은 파일 시스템 드라이브입니다.

공급자를 사용 하면 파일 시스템의 데이터와 동일한 방법으로 데이터 저장소의 항목을 보고, 탐색 하 고, 변경할 수 있습니다. 데이터 저장소는 지원 되는 드라이브의 이름을 통해 액세스 됩니다.

Cmdlet의 기본 표시에 드라이브가 나열 `Get-PSProvider` 되지만 cmdlet을 사용 하 여 공급자 드라이브에 대 한 정보를 가져올 수 있습니다 `Get-PSDrive` . 예를 들어 Function: drive의 모든 속성을 가져오려면 다음을 입력 합니다.

```powershell
Get-PSDrive Function | Format-List *
```

파일 시스템 드라이브에 있는 것 처럼 공급자 드라이브의 데이터를 확인 하 고 이동할 수 있습니다.

공급자 드라이브의 내용을 보려면 Get-Item 또는 Get-ChildItem cmdlet을 사용 합니다. 드라이브 이름 뒤에 콜론 (:)을 입력 합니다. 예를 들어 Alias: 드라이브의 내용을 보려면 다음을 입력 합니다.

```powershell
Get-Item alias:
```

경로에 드라이브 이름을 포함 하 여 다른 드라이브의 모든 드라이브에서 데이터를 보고 관리할 수 있습니다. 예를 들어 다른 드라이브의 HKLM: 드라이브에서 HKLM\Software 레지스트리 키를 보려면 다음을 입력 합니다.

```powershell
Get-ChildItem HKLM:\SOFTWARE\
```

드라이브를 열려면 Set-Location cmdlet을 사용 합니다. 드라이브 경로를 지정할 때는 콜론을 명심 하십시오. 예를 들어, 위치를 Cert: 드라이브의 루트 디렉터리로 변경 하려면 다음을 입력 합니다.

```powershell
Set-Location cert:
```

그런 다음, Cert: 드라이브의 내용을 보려면 다음을 입력 합니다.

```powershell
Get-ChildItem
```

## <a name="moving-through-hierarchical-data"></a>계층적 데이터 이동

하드 디스크 드라이브와 마찬가지로 공급자 드라이브를 통해 이동할 수 있습니다.
데이터가 항목 내 항목의 계층 구조에 정렬 되어 있는 경우 백슬래시 ()를 사용 `\` 하 여 자식 항목을 표시 합니다. 이때 다음 형식을 사용합니다.

```
drive:\location\child-location\...
```

예를 들어 HKLM\Software 레지스트리 키에 대 한 위치를 변경 하려면 다음과 같은 Set-Location 명령을 입력 합니다.

```powershell
Set-Location HKLM:\SOFTWARE\
```

정규화 된 이름의 요소에 공백이 포함 된 경우 이름을 큰따옴표 ()로 묶어야 합니다 `"` . 다음 예에서는 공백이 포함 된 정규화 된 경로를 보여 줍니다.

```
"C:\Program Files\Internet Explorer\iexplore.exe"
```

위치에 대 한 상대 참조를 사용할 수도 있습니다. 점 ( `.` )은 현재 위치를 나타냅니다. 예를 들어 레지스트리 키에 있는 경우 `HKLM:\Software\Microsoft` 키에 레지스트리 하위 키를 나열 하려면 `HKLM:\Software\Microsoft\PowerShell` 다음 명령을 입력 합니다.

```powershell
Get-ChildItem .\PowerShell
```

또한 이중 점 ( `..` )은 현재 위치 바로 위의 디렉터리나 컨테이너를 참조 합니다. 이중 점 ( `..` )을 사용 하 여 공급자 계층 구조를 탐색할 수 있습니다.

```
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters\> cd ..\..\LanmanWorkstation\Parameters
PS HKLM:\SYSTEM\CurrentControlSet\Services\LanmanWorkstation\Parameters>
```

## <a name="provider-home"></a>공급자 홈

공급자에는 또한 **홈** 위치가 있습니다.  이 위치는 공급자가 지 원하는 모든에서 공유 `PSDrives` 합니다. 공급자의 **Home** 속성을 확인 하 여 검색할 수 있습니다.

```powershell
Get-PSProvider | Format-Table Name, Home
```

```Output
Name        Home
----        ----
Registry
Alias
Environment
FileSystem  C:\Users\username
Function
Variable
Certificate
```

**FileSystem** 공급자는 **홈** 에 대 한 기본값을 가진 유일한 공급자입니다. 와 동일한 값 `$Home` 입니다. 자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.

속성을 사용 하 여 현재 세션에 대 한 공급자의 **홈** 디렉터리를 설정할 수 있습니다.

```powershell
(Get-PSProvider FileSystem).Home = "C:\"
```

`~`문자를 사용 하 여 공급자의 홈 디렉터리를 나타낼 수 있습니다.
공급자에 **홈** 위치가 설정 되어 있지 않으면 오류가 표시 됩니다.

```powershell
Cert:\> Set-Location ~
```

```Output
Set-Location : Home location for this provider isn't set. To set the home
location, call "(get-psprovider 'Certificate').Home = 'path'".
At line:1 char:1
+ Set-Location ~
+ ~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Set-Location],
                              PSInvalidOperationException
...
```

## <a name="finding-dynamic-parameters"></a>동적 매개 변수 찾기

동적 매개 변수는 공급자가 cmdlet에 추가 하는 cmdlet 매개 변수입니다. 이러한 매개 변수는 cmdlet이 추가 된 공급자와 함께 사용 되는 경우에만 사용할 수 있습니다.

예를 들어, `Cert:` 드라이브는 **Codesigningcert** 매개 변수를 및 cmdlet에 추가 합니다 `Get-Item` `Get-ChildItem` . 이 매개 변수는 `Get-Item` 드라이브에서 또는를 사용할 때만 사용할 수 있습니다 `Get-ChildItem` `Cert:` .

공급자가 지 원하는 동적 매개 변수의 목록은 공급자에 대 한 도움말 파일을 참조 하십시오. 형식:

```
Get-Help <provider-name>
```

다음은 그 예입니다. 

```powershell
Get-Help certificate
```

## <a name="learning-about-providers"></a>공급자에 대해 알아보기

모든 공급자 데이터가 드라이브에 표시 되 고 동일한 방법을 사용 하 여 이동 하는 경우에도 유사성은 중지 됩니다. 공급자가 제공 하는 데이터 저장소는 Active Directory 위치 및 Microsoft Exchange Server 사서함과 다를 수 있습니다.

개별 PowerShell 공급자에 대 한 자세한 내용을 보려면 다음을 입력 하십시오.

```
Get-Help <ProviderName>
```

다음은 그 예입니다. 

```powershell
Get-Help registry
```

공급자에 대 한 도움말 항목 목록을 보려면 다음을 입력 하십시오.

```powershell
Get-Help * -Category Provider
```

## <a name="see-also"></a>참고 항목

[about_Locations](about_Locations.md)

[about_Path_Syntax](about_Path_Syntax.md)

