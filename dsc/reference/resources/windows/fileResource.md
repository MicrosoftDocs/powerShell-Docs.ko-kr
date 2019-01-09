---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047772"
---
# <a name="dsc-file-resource"></a>DSC 파일 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(필요한 상태 구성)의 파일 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다.

>**참고:** **MatchSource** 속성이 **$false**(기본값)로 설정된 경우 복사할 콘텐츠는 구성을 처음으로 적용할 때 캐시됩니다.
>이후 구성을 적용할 때 **SourcePath**로 지정된 경로에서 업데이트된 파일 및/또는 폴더가 있는지 확인하지 않습니다. 구성을 적용할 때마다 **SourcePath**에 파일 및/또는 폴더에 대한 업데이트가 있는지 확인하려면 **MatchSource**를 **$true**로 설정합니다.

## <a name="syntax"></a>구문
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>속성

|  속성  |  설명   |
|---|---|
| DestinationPath| 파일 또는 디렉터리에 대한 상태를 확인하려는 위치를 나타냅니다.|
| 특성| 대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태를 지정합니다.|
| 체크섬| 두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형을 나타냅니다. __Checksum__을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다. 유효한 값은 다음과 같습니다. Sha-1, SHA-256, SHA-512, createdDate, modifiedDate 합니다.|
| 콘텐츠| 특정 문자열과 같이 파일의 내용을 지정합니다.|
| 자격 증명| 이러한 액세스가 필요한 경우 소스 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명을 나타냅니다.|
| Ensure| 파일이나 디렉터리가 있는지를 나타냅니다. 파일 또는 디렉터리가 존재하지 않도록 하려면 이 속성을 "Absent"으로 설정합니다. 파일 또는 디렉터리가 존재하도록 하려면 이 속성을 "Present"으로 설정합니다. 기본값은 "Present"입니다.|
| Force| 특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다. Force 속성을 사용하면 이러한 오류가 무시됩니다. 기본값은 __$false__입니다.|
| Recurse| 하위 디렉터리가 포함되어 있는지를 나타냅니다. 하위 디렉터리가 포함되도록 하려면 이 속성을 __$true__로 설정합니다. 기본값은 __$false__입니다. **참고**: 이 속성은 Type 속성은 디렉터리에 설정 된 경우에 유효 합니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 __ResourceName__이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|
| SourcePath| 파일 또는 폴더 리소스를 복사해 올 소스 경로를 나타냅니다.|
| 유형| 구성되는 리소스가 디렉터리인지 또는 파일인지를 나타냅니다. 리소스가 디렉터리임을 나타내려면 이 속성을 "Directory"로 설정합니다. 리소스가 파일을 나타내려면 이 속성을 "File"로 설정합니다. 기본값은 "File"입니다.|
| MatchSource| 기본값 __$false__로 설정되면, 소스의 파일이 모두(예: 파일 A, B 및 C) 구성이 처음 적용된 대상에 추가됩니다. 새 파일(D)이 소스에 추가되면, 구성이 나중에 다시 적용되는 경우에도 이 파일은 대상에 추가되지 않습니다. 값이 __$true__이면, 구성이 적용될 때마다 나중에 소스(예: 이 예의 파일 D)에서 발견되는 새 파일이 대상에 추가됩니다. 기본값은 **$false**입니다.|

## <a name="example"></a>예제

다음 예제에서는 파일 리소스를 사용하여 소스 컴퓨터(예: "끌어오기" 서버)에서 경로가 `C:\Users\Public\Documents\DSCDemo\DemoSource`인 디렉터리가 대상 노드에도 있도록(모든 하위 디렉터리와 함께) 하는 방법을 보여 줍니다. 또한 완료되면 로그에 확인 메시지도 쓰고 로깅 작업 전에 파일 검사 작업이 실행되도록 하는 구문도 포함합니다.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```