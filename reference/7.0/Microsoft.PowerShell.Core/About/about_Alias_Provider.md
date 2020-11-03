---
description: Alias
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_alias_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 별칭 공급자
ms.openlocfilehash: b143a7aea71fcc6227d6287a4f87b49262098efb
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223153"
---
# <a name="alias-provider"></a>별칭 공급자

## <a name="provider-name"></a>공급자 이름
Alias

## <a name="drives"></a>드라이브

`Alias:`

## <a name="capabilities"></a>기능

**ShouldProcess**

## <a name="short-description"></a>간단한 설명

PowerShell 별칭 및 해당 별칭이 나타내는 값에 대 한 액세스를 제공 합니다.

## <a name="detailed-description"></a>자세한 설명

Powershell **별칭** 공급자를 통해 powershell에서 별칭을 가져오고 추가, 변경 및 삭제할 수 있습니다.

별칭은 스크립트를 포함 하 여 cmdlet, 함수, 실행 파일의 대체 이름입니다. PowerShell에는 기본 제공 별칭 집합이 포함 되어 있습니다. 현재 세션과 PowerShell 프로필에 고유한 별칭을 추가할 수 있습니다.

**별칭** 드라이브는 별칭 개체만 포함 하는 플랫 네임 스페이스입니다.
별칭에는 하위 항목이 없습니다.

**별칭** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.

- [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location)
- [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location)
- [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Remove-Item](xref:Microsoft.PowerShell.Management.Remove-Item)
- [Clear-Item](xref:Microsoft.PowerShell.Management.Clear-Item)

PowerShell에는 별칭을 보고 변경할 수 있도록 설계 된 cmdlet 집합이 포함 되어 있습니다. **별칭** cmdlet을 사용 하는 경우 이름에 드라이브를 지정할 필요가 없습니다 `Alias:` . 이 문서에서는 **별칭** cmdlet 작업에 대해 다루지 않습니다.

- [Export-Alias](xref:Microsoft.PowerShell.Utility.Export-Alias)
- [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias)
- [Import-Alias](xref:Microsoft.PowerShell.Utility.Import-Alias)
- [New-Alias](xref:Microsoft.PowerShell.Utility.New-Alias)
- [Set-Alias](xref:Microsoft.PowerShell.Utility.Set-Alias)

## <a name="types-exposed-by-this-provider"></a>이 공급자가 노출 하는 형식

각 별칭은 [system.management.automation.aliasinfo](/dotnet/api/system.management.automation.aliasinfo) 클래스의 인스턴스입니다.

## <a name="navigating-the-alias-drive"></a>별칭 드라이브 탐색

**별칭** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Alias:` . 별칭을 사용 하려면 다음 명령을 사용 하 여 해당 위치를 드라이브로 변경할 수 있습니다 `Alias:` .

```powershell
Set-Location Alias:
```

파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다.

```powershell
Set-Location C:
```

다른 PowerShell 드라이브에서 별칭 공급자를 사용할 수도 있습니다. 다른 위치에서 별칭을 참조 하려면 `Alias:` 경로에 드라이브 이름을 사용 합니다.

> [!NOTE]
> PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다. `dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다. 및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.

### <a name="displaying-the-contents-of-the-alias-drive"></a>Alias: 드라이브의 내용 표시

이 명령은 현재 위치가 드라이브인 경우 모든 별칭 목록을 가져옵니다 `Alias:` . 와일드 카드 문자를 사용 하 여 `*` 현재 위치의 모든 내용을 표시 합니다.

```powershell
PS Alias:\> Get-Item -Path *
```

드라이브에서 `Alias:` `.` 현재 위치를 나타내는 점 및 `*` 현재 위치의 모든 항목을 나타내는 와일드 카드 문자는 동일한 효과를 가집니다. 예를 들어 `Get-Item -Path .` 또는 `Get-Item \*` 는 동일한 결과를 생성 합니다.

별칭 공급자는 컨테이너를 포함 하지 않으므로와 함께 사용할 경우 위의 명령이 동일한 결과를 가집니다 `Get-ChildItem` .

```powershell
Get-ChildItem -Path Alias:
```

### <a name="get-a-selected-alias"></a>선택한 별칭 가져오기

이 명령은 별칭을 가져옵니다 `ls` .
경로를 포함 하기 때문에 모든 PowerShell 드라이브에서 사용할 수 있습니다.

```powershell
Get-Item -Path Alias:ls
```

드라이브에 있는 경우 `Alias:` 경로에서 드라이브 이름을 생략할 수 있습니다.

공급자 경로에 달러 기호 ()를 접두사로 사용 하 여 별칭에 대 한 정의를 검색할 수도 있습니다 `$` .

```powershell
$Alias:ls
```

### <a name="get-all-aliases-for-a-specific-cmdlet"></a>특정 cmdlet에 대 한 모든 별칭 가져오기

이 명령은 cmdlet과 연결 된 별칭 목록을 가져옵니다 `Get-ChildItem` . Cmdlet 이름을 저장 하는 **Definition** 속성을 사용 합니다.

```powershell
Get-Item -Path Alias:* | Where-Object {$_.Definition -eq "Get-ChildItem"}
```

## <a name="creating-aliases"></a>별칭 만들기

### <a name="create-an-alias-from-the-alias-drive"></a>별칭: 드라이브에서 별칭을 만듭니다.

이 명령은 `serv` cmdlet에 대 한 별칭을 만듭니다 `Get-Service` . 현재 위치가 드라이브에 있기 때문에 `Alias:` `-Path` 매개 변수는 필요 하지 않습니다.

또한이 명령은 `-Options` 동적 매개 변수를 사용 하 여 별칭에 대 한 **AllScope** 옵션을 설정 합니다. `-Options`매개 변수는 `New-Item` 드라이브에 있는 경우에만 cmdlet에서 사용할 수 있습니다 `Alias:` . 점 ( `.` )은 별칭 드라이브인 현재 디렉터리를 나타냅니다.

```
PS Alias:\> New-Item -Path . -Name serv -Value Get-Service -Options "AllScope"
```

### <a name="create-an-alias-with-an-absolute-path"></a>절대 경로를 사용 하 여 별칭 만들기

명령을 호출하는 모든 항목에 대한 별칭을 만들 수 있습니다.
이 명령은 `np` 에 대 한 별칭을 만듭니다 `Notepad.exe` .

```powershell
New-Item -Path Alias:np -Value c:\windows\notepad.exe
```

### <a name="create-an-alias-to-a-new-function"></a>새 함수에 대 한 별칭 만들기

모든 함수에 대한 별칭을 만들 수 있습니다. 이 기능을 사용하여 cmdlet과 해당 매개 변수를 둘 다 포함하는 별칭을 만들 수 있습니다.

첫 번째 명령은 `CD32` 현재 디렉터리를 디렉터리로 변경 하는 함수를 만듭니다 `System32` . 두 번째 명령은 `go` 함수에 대 한 별칭을 만듭니다 `CD32` .

명령이 완료 되 면 또는 중 하나를 사용 하 여 함수를 호출할 수 있습니다 `CD32` `go` .

```powershell
function CD32 {Set-Location -Path c:\windows\system32}
Set-Item -Path Alias:go -Value CD32
```

## <a name="changing-aliases"></a>별칭 변경

### <a name="change-the-options-of-an-alias"></a>별칭의 옵션을 변경 합니다.

`Set-Item`Cmdlet을 `-Options` 동적 매개 변수와 함께 사용 하 여 별칭의 속성 값을 변경할 수 있습니다 `-Options` .

이 명령은 별칭에 대 한 **AllScope** 및 **ReadOnly** 옵션을 설정 합니다 `dir` . 이 명령은 `-Options` cmdlet의 동적 매개 변수를 사용 합니다 `Set-Item` . `-Options`매개 변수는 `Set-Item` **별칭** 또는 **함수** 공급자와 함께 사용할 때에서 사용할 수 있습니다.

```powershell
Set-Item -Path Alias:dir -Options "AllScope,ReadOnly"
```

### <a name="change-an-aliases-referenced-command"></a>참조 된 별칭 변경 명령

이 명령은 cmdlet을 사용 하 여 cmdlet 대신 cmdlet을 `Set-Item` 나타내도록 별칭을 변경 합니다 `gp` `Get-Process` `Get-ItemProperty` .
`-Force`별칭의 **Options** 속성 값 `gp` 이로 설정 되어 있기 때문에 매개 변수가 필요 합니다 `ReadOnly` . 명령이 드라이브 내에서 전송 되므로 `Alias:` 경로에 드라이브가 지정 되지 않습니다.

```powershell
Set-Item -Path gp -Value Get-Process -Force
```

변경 내용은 별칭과 명령 간의 연결을 정의하는 네 가지 속성에 영향을 줍니다. 변경의 결과를 보려면 다음 명령을 입력 합니다.

```powershell
Get-Item -Path gp | Format-List -Property *
```

### <a name="rename-an-alias"></a>별칭 이름 바꾸기

이 명령은 cmdlet을 사용 하 여 `Rename-Item` `popd` 별칭을로 변경 `pop` 합니다.

```powershell
Rename-Item -Path Alias:popd -NewName pop
```

## <a name="copying-an-alias"></a>별칭 복사

이 명령은 `pushd` `push` cmdlet에 대 한 새 별칭이 만들어지도록 별칭을 복사 합니다 `Push-Location` .

새 별칭이 만들어지면 해당 **Description** 속성의 값은 null입니다.
및 **옵션** 속성의 값은 `None` 입니다. 명령이 드라이브 내에서 실행 된 경우 `Alias:` 매개 변수 값에서 드라이브 이름을 생략할 수 있습니다 `-Path` .

```powershell
Copy-Item -Path Alias:pushd -Destination Alias:push
```

## <a name="deleting-an-alias"></a>별칭 삭제

이 명령은 `serv` 현재 세션에서 별칭을 삭제 합니다.
PowerShell 드라이브에서이 명령을 사용할 수 있습니다.

```powershell
Remove-Item -Path Alias:serv
```

이 명령은 "s"로 시작하는 별칭을 삭제합니다.
읽기 전용 별칭은 삭제되지 않습니다.

```powershell
Clear-Item -Path Alias:s*
```

### <a name="delete-read-only-aliases"></a>읽기 전용 별칭 삭제

이 명령은 현재 세션에서 모든 별칭을 삭제 합니다. 단, `Constant` 해당 **옵션** 속성에 대 한 값을 가진 별칭은 제외 합니다. `-Force`매개 변수를 사용 하면 **Options** 속성의 값이 인 별칭을 삭제할 수 있습니다 `ReadOnly` .

```powershell
Remove-Item Alias:* -Force
```

## <a name="dynamic-parameters"></a>동적 매개 변수

동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.

### <a name="options-systemmanagementautomationscopeditemoptions"></a>옵션 [ScopedItemOptions]

별칭의 **Options** 속성 값을 결정 합니다.

- **None** : 옵션이 없습니다. 이 값은 기본값입니다.
- **상수** : 별칭을 삭제할 수 없으며 해당 속성을 변경할 수 없습니다.
  **상수** 는 별칭을 만드는 경우에만 사용할 수 있습니다. 기존 별칭의 옵션을 **Constant** 로 변경할 수 없습니다.
- **비공개** : 별칭은 자식 범위가 아니라 현재 범위 에서만 볼 수 있습니다.
- **ReadOnly** : 별칭의 속성은 매개 변수를 사용 하는 경우를 제외 하 고 변경할 수 없습니다 `-Force` . 를 사용 하 여 별칭을 삭제할 수 있습니다 `Remove-Item` .
- **AllScope** : 별칭이 만들어진 모든 새 범위로 복사 됩니다.

#### <a name="cmdlets-supported"></a>Cmdlet 지원

- [New-Item](xref:Microsoft.PowerShell.Management.New-Item)
- [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a>파이프라인 사용

공급자 cmdlet은 파이프라인 입력을 허용 합니다. 파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.
공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.

## <a name="getting-help"></a>도움말 보기

Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.

파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path alias:
```

## <a name="see-also"></a>참고 항목

[about_Aliases](../About/about_Aliases.md)

[about_Providers](../About/about_Providers.md)
