---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: 레지스트리 키 작업
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736848"
---
# <a name="working-with-registry-keys"></a>레지스트리 키 작업

레지스트리 키는 PowerShell 드라이브에 있는 항목이므로 레지스트리 키에 대한 작업 수행은 파일 및 폴더 작업과 매우 유사합니다. 한 가지 중요한 차이점은 레지스트리 기반 PowerShell 드라이브의 모든 항목은 파일 시스템 드라이브의 폴더와 같이 컨테이너라는 점입니다. 그러나 레지스트리 항목 및 연결된 값은 고유한 항목이 아니라 항목의 속성입니다.

## <a name="listing-all-subkeys-of-a-registry-key"></a>레지스트리 키의 모든 하위 키 표시

`Get-ChildItem`을 사용하여 레지스트리 키 바로 아래에 있는 항목을 모두 볼 수 있습니다. 선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다. 예를 들어 다음 명령은 `HKEY_CURRENT_USER` 레지스트리 하이브에 해당하는 Windows PowerShell 드라이브 `HKCU:` 바로 아래에 있는 항목을 보여 줍니다.

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

이러한 키는 레지스트리 편집기(Regedit.exe)의 `HKEY_CURRENT_USER`에 표시되는 최상위 키입니다.

레지스트리 공급자 이름(뒤에 `::`이 옴)을 지정하여 레지스트리 경로를 지정할 수도 있습니다. 레지스트리 공급자의 전체 이름이 `Microsoft.PowerShell.Core\Registry`가 되지만 `Registry`로만 줄일 수 있습니다. 다음 명령은 `HKCU:` 바로 아래에 있는 내용을 보여 줍니다.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

이 명령은 **Cmd.exe**의 `DIR` 명령이나 UNIX 셸의 `ls`를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다. 포함된 항목을 모두 보려면 **Recurse** 매개 변수를 지정해야 합니다. `HKCU:`의 모든 레지스트리 키를 나열하려면 다음 명령을 사용합니다.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem`은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 복잡한 필터링 기능을 수행할 수 있지만 이러한 변수는 일반적으로 이름을 기준으로 합니다. `Where-Object` cmdlet을 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다. 다음 명령은 `HKCU:\Software` 내에서 정확히 한 개의 하위 키와 네 개의 값을 갖는 모든 키를 찾습니다.

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>키 복사

`Copy-Item`을 사용하여 복사를 수행합니다. 다음 예제에서는 `HKLM:\SOFTWARE\Microsoft\Windows\`의 `CurrentVersion` 하위 키와 모든 속성을 `HKCU:\`로 복사합니다.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

레지스트리 편집기나 `Get-ChildItem`을 사용하여 새 키를 검사하면 포함된 하위 키가 새 위치에 복사되지 않은 것을 확인할 수 있습니다. 컨테이너의 내용을 모두 복사하려면 **Recurse** 매개 변수를 지정해야 합니다. 위의 복사 명령을 재귀적으로 실행하려면 다음 명령을 사용합니다.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

파일 시스템 복사를 위해 이전부터 사용하던 다른 도구를 계속 사용할 수 있습니다. 예를 들어 **reg.exe**, **regini.exe**, **regedit.exe** 같은 레지스트리 편집 도구와 **WScript.Shell** 및 WMI의 **StdRegProv** 클래스와 같이 레지스트리 편집을 지원하는 COM 개체를 Windows PowerShell에서 사용할 수 있습니다.

## <a name="creating-keys"></a>키 만들기

레지스트리에서 새 키를 만드는 것은 파일 시스템에서 새 항목을 만드는 것보다 간단합니다. 모든 레지스트리 키가 컨테이너이므로 항목 유형을 지정할 필요 없이 다음과 같이 명시적 경로만 지정하면 됩니다.

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

다음과 같이 공급자 기반 경로를 사용하여 키를 지정할 수도 있습니다.

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>키 삭제

기본적으로 항목 삭제는 모든 공급자에 대해 동일하게 수행됩니다. 다음 명령은 항목을 제거합니다.

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>특정 키 아래에 있는 모든 키 제거

`Remove-Item`을 사용하면 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다. 예를 들어 앞에서 만든 `HKCU:\CurrentVersion` 하위 키를 삭제하려고 하면 다음과 같은 메시지가 나타납니다.

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

확인 메시지 없이 포함된 항목을 삭제하려면 다음과 같이 **Recurse** 매개 변수를 지정합니다.

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

`HKCU:\CurrentVersion` 내에서 모든 항목을 제거하지만 `HKCU:\CurrentVersion` 자체는 제거하지 않으려는 경우 다음을 대신 사용할 수 있습니다.

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
