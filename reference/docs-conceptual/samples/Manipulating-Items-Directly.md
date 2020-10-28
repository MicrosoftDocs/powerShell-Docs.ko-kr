---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 직접 항목 조작
description: PowerShell은 로컬 및 원격 컴퓨터에서 항목을 관리하는 데 도움이 되는 여러 cmdlet을 제공합니다. 항목은 파일 시스템, 레지스트리, 인증서 등과 같은 PowerShell 공급자가 제공하는 개체입니다.
ms.openlocfilehash: 20132b63a8ff4ef24b1d8346066315dbb053e59c
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500320"
---
# <a name="manipulating-items-directly"></a>직접 항목 조작

Windows PowerShell 드라이브에 표시되는 요소(예: 파일 시스템 드라이브의 파일 및 폴더, Windows PowerShell 레지스트리 드라이브의 레지스트리 키)를 Windows PowerShell에서는 *항목* 이라고 합니다. 이러한 항목 작업을 위한 cmdlet은 이름에 명사 **Item** 이 포함되어 있습니다.

**Get-Command -Noun Item** 명령의 출력에는 9개의 Windows PowerShell 항목 cmdlet이 표시됩니다.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a>새 항목 만들기(New-Item)

파일 시스템에서 새 항목을 만들려면 **New-Item** cmdlet을 사용합니다. 항목 경로에 **Path** 매개 변수를 포함하고, 값이 "file" 또는 "directory"인 **ItemType** 매개 변수를 포함합니다.

예를 들어 C:\\Temp 디렉터리에서 "New.Directory"라는 새 디렉터리를 만들려면 다음과 같이 입력합니다.

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

파일을 만들려면 **ItemType** 매개 변수의 값을 "file"로 변경합니다. 예를 들어 New.Directory 디렉터리에서 "file1.txt" 파일을 만들려면 다음과 같이 입력합니다.

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

동일한 기술을 사용하여 새 레지스트리 키를 만들 수 있습니다. Windows 레지스트리에 있는 항목 유형만 키이므로 레지스트리 키는 쉽게 만들 수 있습니다. 레지스트리 항목은 *properties* 항목입니다. 예를 들어 CurrentVersion 하위 키에서 "_Test" 키를 만들려면 다음과 같이 입력합니다.

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

레지스트리 경로를 입력할 때 Windows PowerShell 드라이브 이름에 콜론( **:** )을 포함해야 합니다(예: HKLM: 및 HKCU:). 콜론이 없을 경우 Windows PowerShell에서는 경로의 드라이브 이름을 인식하지 못합니다.

## <a name="why-registry-values-are-not-items"></a>레지스트리 값이 항목이 아닌 이유

**Get-ChildItem** cmdlet을 사용하여 레지스트리 키에서 항목을 찾을 경우 실제 레지스트리 항목 또는 값이 표시되지 않습니다.

예를 들어 **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** 레지스트리 키에는 일반적으로 시스템을 시작할 때 실행되는 애플리케이션을 나타내는 여러 레지스트리 항목이 포함되어 있습니다.

하지만 **Get-ChildItem** 을 사용하여 키의 하위 항목을 찾을 경우 키의 **OptionalComponents** 하위 키만 표시됩니다.

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

레지스트리 항목을 항목으로 처리하면 편리하지만 레지스트리 항목의 경로를 고유하게 지정할 수 없습니다. **Run** 레지스트리 하위 키와 **Run** 하위 키의 **(Default)** 레지스트리 항목 간에 경로 표기법이 구분되지 않습니다. 또한 레지스트리 항목 이름에 백슬래시( **\\** ) 문자를 사용할 수 있으므로, 레지스트리 항목이 항목인 경우 경로 표기법을 사용하여 **Windows\\CurrentVersion\\Run** 레지스트리 항목을 해당 경로에 있는 하위 키와 구분할 수 없습니다.

## <a name="renaming-existing-items-rename-item"></a>기존 항목 이름 바꾸기(Rename-Item)

파일 또는 폴더의 이름을 변경하려면 **Rename-Item** cmdlet을 사용합니다. 다음 명령은 **file1.txt** 파일의 이름을 **fileOne.txt** 로 변경합니다.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

**Rename-Item** cmdlet은 파일 또는 폴더의 이름을 변경할 수 있지만 항목을 이동할 수 없습니다. 다음 명령은 파일을 New.Directory 디렉터리에서 Temp 디렉터리로 이동하므로 실패합니다.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>항목 이동(Move-Item)

파일 또는 폴더를 이동하려면 **Move-Item** cmdlet을 사용합니다.

예를 들어 다음 명령은 New.Directory 디렉터리를 C:\\temp 디렉터리에서 C: 드라이브의 루트로 이동합니다. 항목이 이동되었는지 확인하려면 **Move-Item** cmdlet의 **PassThru** 매개 변수를 포함합니다. **Passthru** 가 없을 경우 **Move-Item** cmdlet은 결과를 표시하지 않습니다.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>항목 복사(Copy-Item)

다른 셸에서의 복사 작업에 대해 잘 알고 있는 경우 Windows PowerShell의 **Copy-Item** cmdlet 동작이 특이함을 알 수 있습니다. 항목을 한 위치에서 다른 위치로 이동할 경우 Copy-Item은 기본적으로 해당 내용을 복사합니다.

예를 들어 **New.Directory** 디렉터리를 C: 드라이브에서 C:\\temp 디렉터리로 복사할 경우 명령은 성공하지만 New.Directory 디렉터리의 파일이 복사되지 않습니다.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

**C:\\temp\\New.Directory** 의 내용을 표시하면 파일이 포함되지 않은 것을 확인할 수 있습니다.

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

**Copy-Item** cmdlet이 새 위치에 내용을 복사하지 않는 이유는 무엇인가요?

**Copy-Item** cmdlet은 제네릭으로 설계되었으므로, 파일 및 폴더를 복사하는 데 사용되지 않습니다. 또한 파일 및 폴더를 복사할 때 포함된 항목은 제외하고 컨테이너만 복사할 수 있습니다.

폴더의 모든 내용을 복사하려면 명령에 **Copy-Item** cmdlet의 **Recurse** 매개 변수를 포함합니다. 내용을 포함하지 않고 디렉터리를 이미 복사한 경우 **Force** 매개 변수를 추가하여 빈 폴더를 덮어쓸 수 있습니다.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a>항목 삭제(Remove-Item)

파일 및 폴더를 삭제하려면 **Remove-Item** cmdlet을 사용합니다. 되돌릴 수 없는 중요한 변경을 수행하는 Windows PowerShell cmdlet(예: **Remove-Item** )은 명령을 입력할 때 종종 확인 메시지를 표시합니다. 예를 들어 **New.Directory** 제거하려는 경우 폴더에 파일이 포함되어 있으므로 명령을 확인하는 메시지가 표시됩니다.

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

**예** 가 기본 응답이므로 폴더와 해당 파일을 삭제하려면 **Enter** 키를 누릅니다. 확인하지 않고 폴더를 제거하려면 **-Recurse** 매개 변수를 사용합니다.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>항목 실행(Invoke-Item)

Windows PowerShell에서는 **Invoke-Item** cmdlet을 사용하여 파일 또는 폴더에 대한 기본 작업을 수행합니다. 이 기본 작업은 레지스트리에 있는 기본 애플리케이션 처리기에 의해 결정되며, 파일 탐색기에서 항목을 두 번 클릭하는 경우와 효과는 동일합니다.

예를 들어 다음 명령을 실행한다고 가정합니다.

```powershell
Invoke-Item C:\WINDOWS
```

C:\\Windows 폴더를 두 번 클릭한 것처럼 C:\\Windows에 있는 탐색기 창이 나타납니다.

Windows Vista 이전 시스템에서 **Boot.ini** 파일을 호출할 경우:

```powershell
Invoke-Item C:\boot.ini
```

.ini 파일 형식이 메모장과 연결되어 있는 경우 boot.ini 파일이 메모장에서 열립니다.
