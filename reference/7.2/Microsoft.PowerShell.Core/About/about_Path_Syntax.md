---
description: PowerShell의 전체 및 상대 경로 이름 형식에 대해 설명 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_path_syntax?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Path_Syntax
ms.openlocfilehash: 9a95865d67dc15bf79762987622b702b14faf6c6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599780"
---
# <a name="about-path-syntax"></a>경로 구문 정보

## <a name="short-description"></a>간단한 설명
PowerShell의 전체 및 상대 경로 이름 형식에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

PowerShell 공급자를 통해 액세스할 수 있는 데이터 저장소의 모든 항목은 해당 경로 이름으로 고유 하 게 식별할 수 있습니다. 경로 이름은 항목 이름, 항목이 있는 컨테이너 및 하위 컨테이너 및 컨테이너에 액세스 하는 데 사용할 수 있는 PowerShell 드라이브의 조합입니다.

PowerShell에서 경로 이름은 정규화 된 두 가지 유형, 즉 정규화 된 유형 및 상대 유형 중 하나로 구분 됩니다. 정규화 된 경로 이름은 경로를 구성 하는 모든 요소로 구성 됩니다. 다음 구문은 정규화 된 경로 이름의 요소를 보여 줍니다.

```powershell
[<provider>::]<drive>:[\<container>[\<subcontainer>...]]\<item>
```

\<provider\>자리 표시자는 데이터 저장소에 액세스 하는 데 사용 하는 PowerShell 공급자를 나타냅니다. 예를 들어 파일 시스템 공급자를 사용 하면 컴퓨터의 파일 및 디렉터리에 액세스할 수 있습니다. 이 구문의 요소는 선택 사항이 며, 드라이브 이름이 모든 공급자에서 고유 하기 때문에 필요 하지 않습니다.

\<drive\>자리 표시자는 특정 powershell 공급자가 지 원하는 powershell 드라이브를 나타냅니다. FileSystem 공급자의 경우 PowerShell 드라이브는 시스템에 구성 된 Windows 드라이브에 매핑됩니다. 예를 들어 시스템에 A: drive와 C: 드라이브가 포함 된 경우 FileSystem 공급자는 PowerShell에서 동일한 드라이브를 만듭니다.

드라이브를 지정한 후에는 해당 항목을 포함 하는 컨테이너와 하위 컨테이너를 지정 해야 합니다. 컨테이너는 데이터 저장소에 있는 계층적 순서로 지정 해야 합니다. 즉, 부모 컨테이너에서 시작 하 고 해당 부모 컨테이너의 자식 컨테이너 등으로 시작 해야 합니다. 또한 각 컨테이너 앞에 백슬래시가와 야 합니다. PowerShell을 사용 하면 다른 PowerShells과의 호환성을 위해 슬래시를 사용할 수 있습니다.

컨테이너와 하위 컨테이너를 지정한 후에는 백슬래시 뒤에 항목 이름을 제공 해야 합니다. 예를 들어 C: \\ Windows System32 디렉터리에서 Shell.dll 파일의 정규화 된 경로 이름은 다음과 같습니다 \\ .

```powershell
C:\Windows\System32\Shell.dll
```

이 경우 컨테이너에 액세스 하는 드라이브는 C: 드라이브이 고, 최상위 컨테이너는 Windows이 고, 하위 컨테이너는 System32 (Windows 컨테이너 내에 있음)이 고, 항목은 Shell.dll입니다.

경우에 따라 정규화 된 경로 이름을 지정할 필요가 없으며 대신 상대 경로 이름을 사용할 수 있습니다. 상대 경로 이름은 현재 작업 위치를 기반으로 합니다. PowerShell을 사용 하면 현재 작업 위치를 기준으로 해당 위치에 따라 항목을 식별할 수 있습니다. 특수 문자를 사용 하 여 상대 경로 이름을 지정할 수 있습니다. 다음 표에서는 이러한 각 문자에 대해 설명 하 고 상대 경로 이름 및 정규화 된 경로 이름의 예를 제공 합니다. 이 표의 예는 C:\Windows. 설정 되는 현재 작업 디렉터리를 기준으로 합니다.

|기호|설명               |상대 경로    |전체 경로          |
|------|--------------------------|-----------------|-------------------|
|.     |현재 위치          |.\\ 컴퓨터        |c: \\ Windows \\ 시스템|
|..    |현재 위치의 부모|..\\ 프로그램 파일|c: \\ 프로그램 파일  |
|\     |현재의 드라이브 루트     |\\프로그램 파일  |c: \\ 프로그램 파일  |
|      |위치                  |                 |                   |
|없음을|특수 문자 없음     |시스템           |c: \\ Windows \\ 시스템|

명령에 경로 이름을 사용 하는 경우 정규화 된 경로 이름 또는 상대 경로를 사용 하는 것과 동일한 방식으로 해당 이름을 입력 합니다. 예를 들어 현재 작업 디렉터리는 C:\Windows.. 다음 Get-ChildItem 명령은 C:\Techdocs 디렉터리에 있는 모든 항목을 검색 합니다.

```powershell
Get-ChildItem \techdocs
```

백슬래시는 현재 작업 위치의 드라이브 루트를 사용 해야 함을 나타냅니다. 작업 디렉터리는 C: Windows 이므로 \\ 드라이브 루트는 c: 드라이브입니다. Techdocs 디렉터리는 루트에서 벗어나 있으므로 백슬래시로 지정 해야 합니다.

다음 명령을 사용 하 여 동일한 결과를 달성할 수 있습니다.

```powershell
Get-ChildItem c:\techdocs
```

정규화 된 경로 이름 또는 상대 경로 이름을 사용 하는지 여부에 관계 없이 경로 이름은 항목을 찾았지만 해당 항목이 다른 컨테이너의 다른 항목과 동일한 이름을 공유 하는 경우에도 항목을 고유 하 게 식별 하기 때문에 중요 합니다.

예를 들어 각각 Results.txt 라는 두 개의 파일이 있다고 가정 합니다.
첫 번째 파일은 C: \\ Techdocs 1 월 이라는 디렉터리에 \\ 있고, 두 번째 파일은 c: \\ Techdocs 2 월 이라는 디렉터리에 \\ 있습니다. 첫 번째 파일 (C: \\ Techdocs \\ JanResults.txt)의 경로 이름 \\ 및 두 번째 파일의 경로 이름 (c: \\ Techdocs \\ 2 월 \\Results.txt)을 사용 하 여 두 파일을 명확 하 게 구분할 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Locations](about_Locations.md)

