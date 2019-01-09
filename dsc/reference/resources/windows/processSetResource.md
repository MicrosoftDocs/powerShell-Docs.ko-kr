---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC ProcessSet 리소스
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047530"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess 리소스

_적용 대상: Windows PowerShell 5.0_

Windows PowerShell DSC(필요한 상태 구성)의 **ProcessSet** 리소스에서는 대상 노드에서 프로세스를 구성하는 메커니즘을 제공 합니다. 이 리소스는 `GroupName` 매개 변수에 지정된 각 그룹에 대해 [WindowsProcess 리소스](windowsProcessResource.md)를 호출하는 [복합 리소스](../../../resources/authoringResourceComposite.md)입니다.

## <a name="syntax"></a>구문

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>속성

| 속성 | 설명 |
| --- | --- |
| 인수| 프로세스에 그대로 전달할 인수를 포함하는 문자열입니다. 몇 개의 인수를 전달해야 하는 경우 모두 이 문자열에 넣습니다.|
| 경로| 프로세스 실행 파일의 경로입니다. 실행 파일의 정규화된 경로가 아니라 파일 이름인 경우 DSC 리소스는 환경 **Path** 변수(`$env:Path`)를 검색하여 파일을 찾습니다. 이 속성의 값이 정규화된 경로인 경우 DSC는 **Path** 환경 변수를 사용하여 파일을 찾지 않으며 경로가 없는 경우 오류가 발생합니다. 상대 경로는 허용되지 않습니다.|
| 자격 증명| 프로세스를 시작하기 위한 자격 증명을 나타냅니다.|
| Ensure| 프로세스가 존재하는지 여부를 지정합니다. 프로세스가 존재하도록 하려면 이 속성을 "Present"으로 설정합니다. 그렇지 않으면, "Absent"으로 설정합니다. 기본값은 "Present"입니다.|
| StandardErrorPath| 프로세스가 표준 오류를 쓰는 경로입니다. 거기에 있던 기존 파일은 덮어씁니다.|
| StandardInputPath| 프로세스가 표준 입력을 받는 스트림입니다.|
| StandardOutputPath| 프로세스가 표준 출력을 쓰는 파일의 경로입니다. 거기에 있던 기존 파일은 덮어씁니다.|
| WorkingDirectory| 프로세스에 대한 현재 작업 디렉터리로 사용되는 위치입니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 **ResourceName**이고 해당 형식이 **_ResourceType**일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|
