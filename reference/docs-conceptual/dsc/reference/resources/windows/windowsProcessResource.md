---
ms.date: 07/16/2020
ms.topic: reference
title: DSC WindowsProcess 리소스
description: DSC WindowsProcess 리소스
ms.openlocfilehash: 3076e9cb857b78953c164253351b23e7da9b40c6
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93143010"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **WindowsProcess** 리소스에서는 대상 노드에서 프로세스를 구성하는 메커니즘을 제공 합니다.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>구문

```Syntax
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|인수 |프로세스에 그대로 전달할 인수의 문자열을 나타냅니다. 몇 개의 인수를 전달해야 하는 경우 모두 이 문자열에 넣습니다. |
|경로 |프로세스 실행 파일의 경로입니다. 실행 파일의 정규화된 경로가 아니라 파일 이름인 경우 DSC 리소스는 환경 `$env:Path` 변수를 검색하여 실행 파일을 찾습니다. 이 속성의 값이 정규화된 경로인 경우 DSC는 `$env:Path` 변수를 사용하여 파일을 찾지 않으며 경로가 없는 경우 오류가 발생합니다. 상대 경로는 허용되지 않습니다. |
|자격 증명 |프로세스를 시작하기 위한 자격 증명을 나타냅니다. |
|StandardErrorPath |표준 오류를 쓸 디렉터리 경로를 나타냅니다. 거기에 있던 기존 파일은 덮어씁니다. |
|StandardInputPath |표준 입력 위치를 나타냅니다. |
|StandardOutputPath |표준 출력을 쓸 위치를 나타냅니다. 거기에 있던 기존 파일은 덮어씁니다. |
|WorkingDirectory |프로세스에 대한 현재 작업 디렉터리로 사용할 위치를 나타냅니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |프로세스가 존재하는지 여부를 나타냅니다. 프로세스가 존재하도록 하려면 이 속성을 **Present** 로 설정합니다. 그렇지 않으면, **Absent** 로 설정합니다. 기본값은 **Present** 입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |
