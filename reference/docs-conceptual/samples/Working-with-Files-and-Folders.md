---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 파일 및 폴더 작업
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058933"
---
# <a name="working-with-files-and-folders"></a>파일 및 폴더 작업

Windows PowerShell 드라이브를 탐색하고 드라이브 항목을 조작하는 것은 Windows의 실제 디스크 드라이브에 있는 파일 및 폴더를 조작하는 것과 유사합니다. 이 섹션에서는 PowerShell을 사용하여 특정 파일 및 폴더 조작 작업을 처리하는 방법을 설명합니다.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>폴더 내의 모든 파일 및 폴더 표시

**Get-ChildItem**을 사용하여 폴더 바로 아래에 있는 항목을 모두 볼 수 있습니다. 선택적 **Force** 매개 변수를 추가하면 숨겨진 항목이나 시스템 항목을 볼 수도 있습니다. 예를 들어 다음 명령은 Windows의 실제 C 드라이브와 마찬가지로 Windows PowerShell C 드라이브 바로 아래에 있는 내용을 보여 줍니다.

```powershell
Get-ChildItem -Path C:\ -Force
```

이 명령은 Cmd.exe의 **DIR** 명령이나 UNIX 셸의 **ls**를 사용하는 것과 매우 유사한 방법으로 바로 아래에 포함된 항목만 보여 줍니다. 포함된 항목을 모두 보려면 **-Recurse** 매개 변수도 지정해야 합니다. 작업을 완료하는 데 시간이 많이 걸릴 수 있습니다. C 드라이브에 있는 모든 항목을 표시하려면 다음과 같이 입력합니다.

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem**은 **Path**, **Filter**, **Include** 및 **Exclude** 매개 변수로 항목을 필터링할 수 있지만 이러한 변수는 일반적으로 이름을 기반으로 합니다. **Where-Object**를 사용하여 항목의 다른 속성을 기반으로 복잡한 필터링을 수행할 수 있습니다.

다음 명령은Program Files 폴더 내에서 2005년 10월 1일 이후 마지막으로 수정되었고 1MB보다 작거나 10MB보다 크지 않은 모든 실행 파일을 찾습니다.

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>파일 및 폴더 복사

**Copy-Item**을 사용하여 복사를 수행합니다. 다음 명령은 C:\\boot.ini를 C:\\boot.bak에 백업합니다.

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

대상 파일이 이미 있는 경우 복사가 실패합니다. 기존 파일을 덮어쓰려면 다음과 같이 **Force** 매개 변수를 사용합니다.

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

이 명령은 대상 파일이 읽기 전용인 경우에도 작동합니다.

폴더 복사도 동일한 방식으로 작동합니다. 이 명령은 다음과 같이 C:\\temp\\test1 폴더를 c:\\temp\\DeleteMe라는 새 폴더로 재귀적으로 복사합니다.

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

선택한 항목을 복사할 수도 있습니다. 다음 명령은 c:\\data의 임의 위치에 포함된 모든 .txt 파일을 c:\\temp\\text로 복사합니다.

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

다른 도구를 사용하여 계속 파일 시스템 복사를 수행할 수 있습니다. Windows PowerShell에서는 **Scripting.FileSystemObject**와 같은 XCOPY, ROBOCOPY 및 COM 개체를 모두 사용할 수 있습니다. 예를 들어 다음과 같이 Windows 스크립트 호스트인 **Scripting.FileSystem COM** 클래스를 사용하여 C:\\boot.ini를 C:\\boot.bak에 백업할 수 있습니다.

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>파일 및 폴더 만들기

새 항목 만들기는 Windows PowerShell 공급자에서 동일한 방식으로 작동합니다. Windows PowerShell 공급자에 한 가지 이상의 항목 유형이 있는 경우 항목 유형을 지정해야 합니다. 예를 들어 FileSystem Windows PowerShell 공급자는 디렉터리와 파일을 구별합니다.

이 명령은 다음과 같이 C:\\temp\\New Folder라는 새 폴더를 만듭니다.

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

이 명령은 C:\\temp\\New Folder\\file.txt라는 새 빈 파일을 만듭니다.

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>폴더 내의 모든 파일 및 폴더 제거

**Remove-Item**을 사용하면 포함된 항목을 제거할 수 있지만 이 항목에 다른 항목이 들어 있는 경우 제거를 확인하는 메시지가 나타납니다. 예를 들어 다른 항목이 들어 있는 C:\\temp\\DeleteMe라는 폴더를 삭제하려는 경우 다음과 같이 삭제하기 전에 확인 메시지가 나타납니다.

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

폴더에 들어 있는 각 항목에 대해 이 메시지가 나타나지 않게 하려면 다음과 같이 **Recurse** 매개 변수를 지정합니다.

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Windows 액세스 드라이브로 로컬 폴더 매핑

**subst** 명령을 사용하여 로컬 폴더를 매핑할 수도 있습니다. 다음 명령은 루트가 로컬 Program Files 디렉터리인 로컬 드라이브 P:를 만듭니다.

```powershell
subst p: $env:programfiles
```

그러면 네트워크 드라이브와 마찬가지로 **subst**를 사용하여 Windows PowerShell에 매핑된 드라이브가 Windows PowerShell 셸에 즉시 나타납니다.

## <a name="reading-a-text-file-into-an-array"></a>텍스트 파일을 배열로 읽어오기

일반적으로 텍스트 데이터는 개별 데이터 요소로 취급되는 별도의 줄이 포함된 파일에 저장됩니다. **Get-Content** cmdlet을 사용하여 다음과 같이 한 단계에서 전체 파일을 읽을 수 있습니다.

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content**는 파일에서 읽은 데이터를 한 줄에 하나의 요소가 표시된 배열로 취급합니다. 다음과 같이 반환된 내용의 **Length**를 확인하면 이를 확인할 수 있습니다.

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

이 명령은 정보 목록을 Windows PowerShell로 직접 가져오는 경우 가장 유용합니다. 예를 들어 파일의 각 줄에 하나의 이름을 사용하여 컴퓨터 이름 또는 IP 주소 목록을 C:\\temp\\domainMembers.txt 파일에 저장할 수 있습니다. 다음과 같이 **Get-Content**를 사용하면 파일 내용을 검색하고 검색 내용을 **$Computers** 변수에 삽입할 수 있습니다.

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

그러면 각 요소에 있는 컴퓨터 이름이 배열로 **$Computers**에 포함됩니다.
