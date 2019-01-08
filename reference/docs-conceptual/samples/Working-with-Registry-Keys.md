---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 레지스트리 키 작업
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: a9d08f2f6b5803980dec45a4e266ad66879c8c8d
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403475"
---
# <a name="working-with-registry-keys"></a>레지스트리 키 작업

레지스트리 키는 Windows PowerShell 드라이브에 있는 항목이므로 레지스트리 키에 대한 작업 수행은 파일 및 폴더 작업과 매우 유사합니다. 한 가지 중요한 차이점은 레지스트리 기반 Windows PowerShell 드라이브의 모든 항목은 파일 시스템 드라이브의 폴더와 같이 컨테이너라는 점입니다. 그러나 레지스트리 항목 및 연결된 값은 고유한 항목이 아니라 항목의 속성입니다.

### <a name="listing-all-subkeys-of-a-registry-key"></a>레지스트리 키의 모든 하위 키 표시

**Get-ChildItem**을 사용하여 레지스트리 키 바로 아래에 있는 항목을 모두 볼 수 있습니다. 선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다. 예를 들어 다음 명령은 HKEY_CURRENT_USER 레지스트리 하이브에 해당하는 Windows PowerShell 드라이브 HKCU: 바로 아래에 있는 항목을 보여 줍니다.

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

이러한 키는 레지스트리 편집기(Regedit.exe)의 HKEY_CURRENT_USER에 표시되는 최상위 키입니다.

레지스트리 공급자 이름(뒤에 "**::**"이 옴)을 지정하여 레지스트리 경로를 지정할 수도 있습니다. 레지스트리 공급자의 전체 이름은 **Microsoft.PowerShell.Core\\Registry**이지만 **Registry**로 줄일 수 있습니다. 다음 명령은 HKCU: 바로 아래에 있는 내용을 보여 줍니다.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

이 명령은 Cmd.exe의 **DIR** 명령이나 UNIX 셸의 **ls**를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다. 포함된 항목을 모두 보려면 **Recurse** 매개 변수를 지정해야 합니다. HKCU에 있는 모든 레지스트리 키를 보려면 다음 명령을 사용합니다. 이 작업은 완료하는 데 시간이 많이 걸릴 수 있습니다.

```powershell
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem**은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 복잡한 필터링 기능을 수행할 수 있지만 이러한 변수는 일반적으로 이름을 기반으로 합니다. **Where-Object** cmdlet을 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다. 다음 명령은 HKCU:\\Software 내에서 정확히 한 개의 하위 키와 네 개의 값을 갖는 모든 키를 찾습니다.

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>키 복사

**Copy-Item**을 사용하여 복사를 수행합니다. 다음 명령은 "CurrentVersion"라는 새 키를 만들 때 HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion 및 모든 속성을 HKCU:\\에 복사합니다.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

레지스트리 편집기나 **Get-ChildItem**을 사용하여 새 키를 검사하면 포함된 하위 키가 새 위치에 복사되지 않은 것을 확인할 수 있습니다. 컨테이너의 내용을 모두 복사하려면 **Recurse** 매개 변수를 지정해야 합니다. 위의 복사 명령을 재귀적으로 실행하려면 다음 명령을 사용합니다.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

파일 시스템 복사를 위해 이전부터 사용하던 다른 도구를 계속 사용할 수 있습니다. 예를 들어 reg.exe, regini.exe 및 regedit.exe 같은 레지스트리 편집 도구와 WScript.Shell 및 WMI의 StdRegProv 클래스와 같이 레지스트리 편집을 지원하는 COM 개체를 Windows PowerShell에서 사용할 수 있습니다.

### <a name="creating-keys"></a>키 만들기

레지스트리에서 새 키를 만드는 것은 파일 시스템에서 새 항목을 만드는 것보다 간단합니다. 모든 레지스트리 키가 컨테이너이므로 항목 유형을 지정할 필요 없이 다음과 같이 명시적 경로만 지정하면 됩니다.

```powershell
New-Item -Path hkcu:\software_DeleteMe
```

다음과 같이 공급자 기반 경로를 사용하여 키를 지정할 수도 있습니다.

```powershell
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>키 삭제

기본적으로 항목 삭제는 모든 공급자에 대해 동일하게 수행됩니다. 다음 명령은 항목을 제거합니다.

```powershell
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>특정 키 아래에 있는 모든 키 제거

**Remove-Item**을 사용하면 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다. 예를 들어 앞에서 만든 HKCU:\\CurrentVersion 하위 키를 삭제하려고 하면 다음과 같은 메시지가 나타납니다.

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

확인 메시지 없이 포함된 항목을 삭제하려면 다음과 같이 **-Recurse** 매개 변수를 지정합니다.

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

또한 HKCU:\\CurrentVersion은 제거하지 않고 HKCU:\\CurrentVersion 안에 들어 있는 항목만 모두 제거하려면 다음 명령을 사용하면 됩니다.

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```