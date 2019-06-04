---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077333"
---
# <a name="dsc-file-resource"></a>DSC 파일 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

PowerShell DSC(Desired State Configuration)의 파일 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다. **DestinationPath** 및 **SourcePath**는 둘 다 대상 노드에서 액세스할 수 있어야 합니다.

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

|속성       |설명                                                                   |필수|Default|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|확인하려는 대상 노드의 위치는 `Present` 또는 `Absent`입니다.|예|아니요|
|특성     |대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태입니다. 유효한 값은 **Archive**, **Hidden**, **ReadOnly** 및 **System**입니다.|아니요|없음|
|체크섬      |두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형입니다. 유효한 값은 다음과 같습니다. SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|아니요|파일 또는 디렉터리 이름만 비교됩니다.|
|콘텐츠       |`File` 형식과 함께 사용할 경우에만 유효합니다. Ensure에 대한 콘텐츠가 대상 파일에서 `Present` 또는 `Absent`임을 나타냅니다. |아니요|없음|
|자격 증명     |원본 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명입니다.|아니요|대상 노드의 컴퓨터 계정입니다. (*참고 참조*)|
|Ensure         |대상 파일 또는 디렉터리의 필요한 상태입니다. |아니요|**있음**|
|Force          |오류가 발생하는 액세스 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 재정의합니다.|아니요|`$false`|
|Recurse        |`Directory` 형식과 함께 사용할 경우에만 유효합니다. 모든 하위 디렉터리에 대한 상태 작업을 재귀적으로 수행합니다.|아니요|`$false`|
|DependsOn      |지정된 리소스에서 종속성을 설정합니다. 이 리소스는 종속 리소스를 성공적으로 실행한 후에만 실행됩니다. 구문 `"[ResourceType]ResourceName"`을 사용하여 종속 리소스를 지정할 수 있습니다. [about_DependsOn](../../../configurations/resource-depends-on.md) 참조|아니요|없음|
|SourcePath     |파일 또는 폴더 리소스를 복사할 원본 경로입니다.|아니요|없음|
|유형           |구성되는 리소스 종류입니다. 유효한 값은 `Directory` 및 `File`입니다.|아니요|`File`|
|MatchSource    |리소스가 초기 복사 후에 소스 디렉터리에 추가된 새 파일을 모니터링해야 하는지 여부를 결정합니다. `$true` 값은 초기 복사 후에 새 원본 파일을 대상으로 복사해야 함을 나타냅니다. `$False`로 설정하면 리소스가 소스 디렉터리의 콘텐츠를 캐시하고 초기 복사 후에 추가된 모든 파일을 무시합니다.|아니요|`$false`|

> [!WARNING]
> `Credential` 또는 `PSRunAsCredential`(PS V.5)의 값을 지정하지 않으면 리소스는 대상 노드의 컴퓨터 계정을 사용하여 `SourcePath`에 액세스합니다.  `SourcePath`가 UNC 공유이면 이 액세스로 인해 "액세스 거부" 오류가 발생합니다. 이에 따라 권한이 설정되어 있는지 확인하거나, `Credential` 또는 `PSRunAsCredential` 속성을 사용하여 사용해야 하는 계정을 지정하세요.

## <a name="present-vs-absent"></a>Present 및 Absent

각 DSC 리소스는 `Ensure` 속성에 대해 지정하는 값에 따라 다른 작업을 수행합니다. 위의 속성에 대해 지정하는 값에 따라 수행되는 상태 작업이 결정됩니다.

### <a name="existence"></a>존재 여부

`DestinationPath`만 지정하면 리소스는 경로가 있는지(`Present`) 또는 없는지(`Absent`) 여부를 확인합니다.

### <a name="copy-operations"></a>복사 작업

**Directory**의 `Type` 값을 사용하여 `SourcePath` 및 `DestinationPath`를 지정하면 리소스는 소스 디렉터리를 대상 경로에 복사합니다. `Recurse`, `Force` 및 `MatchSource` 속성은 수행되는 복사 작업 유형을 변경하지만, `Credential`은 소스 디렉터리에 액세스하는 데 사용할 계정을 결정합니다.

### <a name="limitations"></a>제한 사항

`DestinationPath`와 함께 `Attributes` 속성에 `ReadOnly` 값을 지정한 경우 `Ensure = "Present"`는 지정된 경로를 만들지만, `Contents`는 파일의 콘텐츠를 설정합니다.  `Absent` 상태 작업은 `Attributes` 속성을 완전히 무시하고 지정된 경로에 있는 모든 파일을 제거합니다.

## <a name="example"></a>예제

다음 예제에서는 파일 리소스를 사용하여 끌어오기 서버에서 대상 노드로 디렉터리 및 해당 하위 디렉터리를 복사합니다. 작업이 성공하면 로그 리소스는 이벤트 로그에 확인 메시지를 기록합니다.

소스 디렉터리는 끌어오기 서버에서 공유되는 UNC 경로(`\\PullServer\DemoSource`)입니다. `Recurse` 속성을 사용하면 하위 디렉터리도 모두 복사됩니다.

> [!IMPORTANT]
> 대상 노드의 LCM은 기본적으로 로컬 시스템 계정의 컨텍스트에서 실행됩니다. **SourcePath**에 액세스 권한을 부여하려면 대상 노드의 컴퓨터 계정에 적절한 권한을 제공합니다. **Credential** 및 **PSDSCRunAsCredential**(v5)은 둘 다 LCM이 **SourcePath**에 액세스하는 데 사용하는 컨텍스트를 변경합니다. **SourcePath**를 액세스하는 데 사용될 계정에도 액세스 권한을 부여해야 합니다.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

DSC에서 **자격 증명**을 사용하는 방법에 대한 자세한 내용은 [사용자로 실행](../../../configurations/runAsUser.md) 또는 [구성 데이터 자격 증명](../../../configurations/configDataCredentials.md)을 참조하세요.
