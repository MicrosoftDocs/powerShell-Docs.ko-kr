---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 현재 위치 관리
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030191"
---
# <a name="managing-current-location"></a>현재 위치 관리

파일 탐색기에서 폴더 시스템을 탐색할 경우 일반적으로 특정 작업 위치 즉, 현재 열려 있는 폴더에 위치합니다. 현재 폴더에서 항목을 클릭하여 쉽게 조작할 수 있습니다. 명령줄 인터페이스(예: Cmd.exe)의 경우 특정 파일과 동일한 폴더에 있을 경우 파일의 전체 경로를 지정하지 않고 상대적으로 짧은 이름을 지정하여 파일에 액세스할 수 있습니다. 현재 디렉터리를 작업 디렉터리라고 합니다.

Windows PowerShell에서는 명사 **Location**을 사용하여 작업 디렉터리를 나타내고 cmdlet 패밀리를 구현하여 위치를 조사 및 조작합니다.

## <a name="getting-your-current-location-get-location"></a>현재 위치 가져오기(Get-Location)

현재 디렉터리 위치의 경로를 확인하려면 **Get-Location** 명령을 입력합니다.

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Get-Location cmdlet은 BASH 셸의 **pwd** 명령과 비슷합니다. Set-Location cmdlet은 Cmd.exe의 **cd** 명령과 비슷합니다.

## <a name="setting-your-current-location-set-location"></a>현재 위치 설정(Set-Location)

**Get-Location** 명령은 **Set-Location** 명령과 함께 사용됩니다. **Set-Location** 명령을 사용하여 현재 디렉터리 위치를 지정할 수 있습니다.

```powershell
Set-Location -Path C:\Windows
```

명령을 입력해도 명령의 효과에 대한 직접적인 피드백이 수신되지 않습니다. 출력이 항상 유용한 것은 아니므로 작업을 수행하는 대부분의 Windows PowerShell 명령은 출력을 거의 또는 전혀 생성하지 않습니다. **Set-Location** 명령을 입력할 때 디렉터리가 성공적으로 변경되었는지 확인하려면 **Set-Location** 명령을 입력할 때 **-PassThru** 매개 변수를 포함합니다.

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Windows PowerShell에서 **-PassThru** 매개 변수를 많은 Set 명령과 함께 사용하여 기본 출력이 없는 경우에 결과에 대한 정보를 반환할 수 있습니다.

대부분의 UNIX 및 Windows 명령 셸에서와 동일한 방법으로 현재 위치를 기준으로 경로를 지정할 수 있습니다. 상대 경로에 대한 표준 표기법에서 점( **.** )은 현재 폴더를 나타내고, 이중 점( **..** )은 현재 위치의 부모 디렉터리를 나타냅니다.

예를 들어 **C:\\Windows** 폴더에 있는 경우 점( **.** )은 **C:\\Windows**를 나타내고 이중 점( **..** )은 **C:** 를 나타냅니다. 다음과 같이 입력하여 현재 위치에서 C: 드라이브의 루트로 변경할 수 있습니다.

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

이 기술은 파일 시스템 드라이브가 아닌 Windows PowerShell 드라이브(예: **HKLM:** )에서 사용됩니다. 다음과 같이 입력하여 현재 위치를 레지스트리의 HKLM\\Software 키로 설정할 수 있습니다.

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

그런 다음 상대 경로를 사용하여 디렉터리 위치를 부모 디렉터리(Windows PowerShell HKLM: 드라이브의 루트)로 변경할 수 있습니다.

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

Set-Location을 입력하거나 Set-Location에 대한 기본 제공 Windows PowerShell 별칭(cd, chdir, sl)을 사용할 수 있습니다. 예:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>최근 위치 저장 및 다시 호출(Push-Location 및 Pop-Location)

위치를 변경할 때 이전 위치를 추적하여 해당 위치로 돌아갈 수 있습니다. Windows PowerShell의 **Push-Location** cmdlet은 확인한 디렉터리 경로의 순차적 기록("스택")을 만듭니다. 따라서 보조 **Pop-Location** cmdlet을 사용하여 디렉터리 경로 기록의 이전 단계로 돌아갈 수 있습니다.

예를 들어 Windows PowerShell은 일반적으로 사용자의 홈 디렉터리에서 시작합니다.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> 단어 *스택*은 .NET Framework를 비롯한 다양한 프로그래밍 설정에서 특별한 의미로 사용됩니다. 항목의 물리적 스택과 마찬가지로 스택에 넣은 마지막 항목을 스택에서 첫 번째 항목으로 끌어올 수 있습니다. 항목을 스택에 추가하는 것을 구어체로 항목을 스택에 "푸시"한다고 합니다. 항목을 스택에서 끌어오는 것을 구어체로 항목을 스택에서 "꺼낸"다고 합니다.

현재 위치를 스택에 푸시한 다음 Local Settings 폴더로 이동하려면 다음과 같이 입력합니다.

```powershell
Push-Location -Path "Local Settings"
```

이제 다음과 같이 입력하여 Local Settings 위치를 스택으로 푸시하고 Temp 폴더로 이동할 수 있습니다.

```powershell
Push-Location -Path Temp
```

**Get-Location** 명령을 입력하여 디렉터리가 변경되었는지 확인할 수 있습니다.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

그런 다음 **Pop-Location** 명령을 입력하여 최근에 방문한 디렉터리로 바로 이동하고 **Get-Location** 명령을 입력하여 변경을 확인할 수 있습니다.

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

**Set-Location** cmdlet에서와 마찬가지로 **Pop-Location** cmdlet을 입력할 때 **-PassThru** 매개 변수를 포함하여 입력한 디렉터리를 표시할 수 있습니다.

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

Location cmdlet을 네트워크 경로와 함께 사용할 수도 있습니다. FS01 서버와 Public이라는 공유가 있는 경우 다음과 같이 입력하여 위치를 변경할 수 있습니다.

```powershell
Set-Location \\FS01\Public
```

또는

```powershell
Push-Location \\FS01\Public
```

**Push-Location** 및 **Set-Location** 명령을 사용하여 위치를 사용 가능한 드라이브로 변경할 수 있습니다. 예를 들어 드라이브 문자가 D인 로컬 CD-ROM 드라이브에 데이터 CD가 들어 있는 경우 **Set-Location D:** 명령을 입력하여 위치를 CD 드라이브로 변경할 수 있습니다.

드라이브가 비어 있으면 다음과 같은 오류 메시지가 표시됩니다.

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

명령줄 인터페이스를 사용하는 경우 파일 탐색기를 사용하여 사용 가능한 물리적 드라이브를 찾는 데 어려움이 있습니다. 또한 파일 탐색기에는 모든 Windows PowerShell 드라이브가 표시되지 않습니다. Windows PowerShell에서는 Windows PowerShell 드라이브를 조작하는 다양한 명령을 제공합니다. 이에 대해서는 다음에 살펴보겠습니다.
