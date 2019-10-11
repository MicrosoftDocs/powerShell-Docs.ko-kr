---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 파일 리소스
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954680"
---
# <a name="dsc-file-resource"></a>DSC 파일 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **File** 리소스에서는 대상 노드에 있는 파일 및 폴더를 관리하는 메커니즘을 제공합니다. **DestinationPath** 및 **SourcePath**는 둘 다 대상 노드에서 액세스할 수 있어야 합니다.

## <a name="syntax"></a>구문

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |설명 |
|---|---|
|DestinationPath |확인하려는 대상 노드의 위치는 **Ensure** 상태의 **Present** 또는 **Absent**입니다. |
|특성 |대상으로 지정된 파일 또는 디렉터리에 대한 특성의 필요한 상태입니다. 유효한 값은 _Archive_, _Hidden_, _ReadOnly_ 및 _System_입니다. |
|체크섬 |두 파일이 동일한 것인지 결정할 때 사용할 체크섬 유형입니다. 유효한 값은 다음과 같습니다. **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|콘텐츠 |**Type** **File** 형식과 함께 사용할 경우에만 유효합니다. **Ensure**에 대한 콘텐츠가 대상 파일에서 **Present** 또는 **Absent**임을 나타냅니다. |
|자격 증명 |원본 파일과 같은 리소스에 액세스하는 데 필요한 자격 증명입니다. |
|Force |오류가 발생하는 액세스 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 재정의합니다. 기본값은 `$false`입니다. |
|Recurse |**Type** **Directory** 형식과 함께 사용할 경우에만 유효합니다. 모든 하위 디렉터리에 대한 상태 작업을 재귀적으로 수행합니다. 기본값은 `$false`입니다. |
|SourcePath |파일 또는 폴더 리소스를 복사할 원본 경로입니다. |
|유형 |구성되는 리소스 종류입니다. 유효한 값은 **Directory** 및 **File**입니다. 기본값은 **File**입니다. |
|MatchSource |리소스가 초기 복사 후에 소스 디렉터리에 추가된 새 파일을 모니터링해야 하는지 여부를 결정합니다. `$true` 값은 초기 복사 후에 새 원본 파일을 대상으로 복사해야 함을 나타냅니다. `$false`로 설정하면 리소스가 소스 디렉터리의 콘텐츠를 캐시하고 초기 복사 후에 추가된 모든 파일을 무시합니다. 기본값은 `$false`입니다. |

> [!WARNING]
> **Credential** 또는 **PSRunAsCredential**의 값을 지정하지 않으면 리소스는 대상 노드의 컴퓨터 계정을 사용하여 **SourcePath**에 액세스합니다. **SourcePath**가 UNC 공유이면 이 액세스로 인해 "액세스 거부" 오류가 발생합니다. 이에 따라 권한이 설정되어 있는지 확인하거나, **Credential** 또는 **PSRunAsCredential** 속성을 사용하여 사용해야 하는 계정을 지정하세요.

## <a name="common-properties"></a>공용 속성

|속성 |설명 |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |**Destination**에서 파일 및**콘텐츠**가 존재하는지 여부를 확인합니다. 해당 파일이 존재하도록 하려면 이 속성을 **Present**로 설정합니다. 내용이 없도록 하려면 이 속성을 **Absent**으로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

### <a name="additional-information"></a>추가 정보

- **DestinationPath**만 지정하면 리소스는 경로가 있는지(**Present**일 경우) 또는 없는지(**Absent**일 경우) 여부를 확인합니다.
- **Directory**의 **Type** 값을 사용하여 **SourcePath** 및 **DestinationPath**를 지정하면 리소스는 소스 디렉터리를 대상 경로에 복사합니다. **Recurse**, **Force** 및 **MatchSource** 속성은 수행되는 복사 작업 유형을 변경하지만, **Credential**은 소스 디렉터리에 액세스하는 데 사용할 계정을 결정합니다.
- **DestinationPath**와 함께 **Attributes** 속성에 대해 **ReadOnly** 값을 지정한 경우 **Ensure** **Present**는 지정된 경로를 만들고, **Contents**는 파일의 콘텐츠를 설정할 것입니다. **Ensure** **Absent** 설정은 **Attributes** 속성을 완전히 무시하고 지정된 경로에 있는 모든 파일을 제거합니다.

## <a name="example"></a>예제

다음 예제에서는 파일 리소스를 사용하여 끌어오기 서버에서 대상 노드로 디렉터리 및 해당 하위 디렉터리를 복사합니다. 작업이 성공하면 로그 리소스는 이벤트 로그에 확인 메시지를 기록합니다.

소스 디렉터리는 끌어오기 서버에서 공유되는 UNC 경로(`\\PullServer\DemoSource`)입니다. **Recurse** 속성을 사용하면 하위 디렉터리도 모두 복사됩니다.

> [!IMPORTANT]
> 대상 노드의 LCM은 기본적으로 로컬 시스템 계정의 컨텍스트에서 실행됩니다. **SourcePath**에 액세스 권한을 부여하려면 대상 노드의 컴퓨터 계정에 적절한 권한을 제공합니다. **Credential** 및 **PSDSCRunAsCredential**은 둘 다 LCM이 **SourcePath**에 액세스하는 데 사용하는 컨텍스트를 변경합니다. **SourcePath**를 액세스하는 데 사용될 계정에도 액세스 권한을 부여해야 합니다.

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