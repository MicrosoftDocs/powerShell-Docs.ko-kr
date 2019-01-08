---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 파일, 폴더 및 레지스트리 키 작업
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403284"
---
# <a name="working-with-files-folders-and-registry-keys"></a>파일, 폴더 및 레지스트리 키 작업

Windows PowerShell에서는 명사 **Item**을 사용하여 Windows PowerShell 드라이브에 있는 항목을 나타냅니다. Windows PowerShell FileSystem 공급자를 처리할 때 **Item**은 파일, 폴더 또는 Windows PowerShell 드라이브일 수 있습니다. 이러한 항목을 나열하고 사용하는 것은 대부분의 관리 설정의 기본적인 작업이므로 이러한 작업에 대해 자세히 살펴보겠습니다.

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>파일, 폴더 및 레지스트리 키 열거(Get-ChildItem)

특정 위치에서 항목 모음을 가져오는 것은 그런 일반적인 작업이므로 **Get-ChildItem** cmdlet은 폴더와 같은 컨테이너 내에 있는 모든 항목을 반환하도록 특별히 설계되었습니다.

C:\\Windows 폴더에 직접 포함되어 있는 모든 파일과 폴더를 반환하려면 다음과 같이 입력합니다.

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

목록은 **Cmd.exe**에서 **dir** 명령을 입력하거나 UNIX 명령 셸에서 **ls** 명령을 입력할 때 표시되는 것과 비슷합니다.

**Get-ChildItem** cmdlet의 매개 변수를 사용하여 매우 복잡한 목록을 표시할 수 있습니다. 이제 몇 가지 시나리오를 살펴보겠습니다. 다음과 같이 입력하여 **Get-ChildItem** cmdlet의 구문을 표시할 수 있습니다.

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

이러한 매개 변수를 조합하거나 일치시켜서 사용자 지정 출력을 표시할 수 있습니다.

#### <a name="listing-all-contained-items--recurse"></a>모든 포함된 항목 나열(-Recurse)

Windows 폴더 내에 있는 항목과 하위 폴더에 포함된 모든 항목을 표시하려면 **Get-ChildItem**의 **Recurse** 매개 변수를 사용합니다. 목록에는 Windows 폴더 내의 모든 항목과 하위 폴더의 항목이 표시됩니다. 예:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a>이름별로 항목 필터링(-Name)

항목의 이름만 표시하려면 **Get-Childitem**의 **Name** 매개 변수를 사용합니다.

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a>숨겨진 항목을 강제로 나열(-Force)

일반적으로 파일 탐색기 또는 Cmd.exe에 표시되지 않는 항목은 **Get-ChildItem** 명령의 출력에 표시되지 않습니다. 숨겨진 항목을 표시하려면 **Get-ChildItem**의 **Force** 매개 변수를 사용합니다. 예:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

**Get-ChildItem** 명령의 일반적인 동작을 강제로 재정의할 수 있으므로 이 매개 변수의 이름은 Force입니다. Force는 cmdlet이 일반적으로 수행하지 않는 작업을 강제로 수행하는 데 널리 사용되는 매개 변수입니다. 단, 시스템 보안을 저해하는 작업은 수행하지 않습니다.

#### <a name="matching-item-names-with-wildcards"></a>와일드카드와 항목 이름 일치

**Get-ChildItem** 명령에서 나열할 항목의 경로에 와일드카드를 사용할 수 있습니다.

와일드카드 일치는 Windows PowerShell 엔진에서 처리되므로 와일드카드를 허용하는 모든 cmdlet은 동일한 표기법을 사용하고 일치 동작이 동일합니다. Windows PowerShell 와일드카드 표기법은 다음과 같습니다.

- 별표(\*)는 0개 이상의 모든 문자를 일치시킵니다.

- 물음표(?)는 정확히 한 문자를 일치시킵니다.

- 왼쪽 대괄호(\[) 문자와 오른쪽 대괄호(]) 문자는 일치시킬 문자를 묶습니다.

다음 예에서는 와일드카드 지정 방법을 보여 줍니다.

Windows 디렉터리에서 접미사 **.log**를 포함하고 기본 이름이 정확히 5자인 모든 파일을 찾으려면 다음 명령을 입력합니다.

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Windows 디렉터리에서 문자 **x**로 시작하는 모든 파일을 찾으려면 다음과 같이 입력합니다.

```powershell
Get-ChildItem -Path C:\Windows\x*
```

이름이 **x** 또는 **z**로 시작하는 모든 파일을 찾으려면 다음과 같이 입력합니다.

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a>항목 제외(-Exclude)

Get-ChildItem의 **Exclude** 매개 변수를 사용하여 특정 항목을 제외할 수 있습니다. 그러면 단일 문에서 복잡한 필터링을 수행할 수 있습니다.

예를 들어 System32 폴더에서 Windows 시간 서비스 DLL을 찾으려고 하지만 DLL 이름이 "W"로 시작하고 "32"가 포함되어 있다는 것만 알고 있다고 가정합니다.

**w\&#42;32\&#42;.dll**과 같은 문은 조건을 만족하는 모든 DLL을 찾지만, 이름에 "95" 또는 "16"을 포함하는 Windows 95 및 16비트 Windows 호환 DLL도 반환합니다. **Exclude** 매개 변수를 **\&#42;\[9516]\&#42;** 패턴과 함께 사용하여 이름에 이러한 숫자가 포함된 파일을 생략할 수 있습니다.

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

#### <a name="mixing-get-childitem-parameters"></a>Get-ChildItem 매개 변수 혼합

동일한 명령에 **Get-ChildItem** cmdlet의 여러 매개 변수를 사용할 수 있습니다. 매개 변수를 혼합하기 전에 와일드카드 일치에 대해 알고 있어야 합니다. 예를 들어 다음 명령은 결과를 반환하지 않습니다.

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Windows 폴더에 문자 "z"로 시작하는 DLL이 두 개 있지만 결과는 반환되지 않습니다.

와일드카드를 경로의 일부로 지정했기 때문에 결과가 반환되지 않습니다. 재귀적 명령이지만 **Get-ChildItem** cmdlet은 항목을 Windows 폴더에서 이름이 ".dll"로 끝나는 항목으로 제한합니다.

이름이 특정 패턴과 일치하는 파일에 대한 재귀 검색을 지정하려면 **-Include** 매개 변수를 사용합니다.

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```