---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC 보관 리소스
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077554"
---
# <a name="dsc-archive-resource"></a>DSC 보관 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

Windows PowerShell DSC(Desired State Configuration)의 보관 리소스는 특정 경로에서 보관(.zip) 파일의 압축을 푸는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>속성

|  속성  |  설명   |
|---|---|
| 대상| 보관 파일 내용을 추출해 놓을 위치를 지정합니다.|
| 경로| 보관 파일의 원본 경로를 지정합니다.|
| __Checksum__| 두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다. __Checksum__을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다. 유효한 값은 다음과 같습니다. SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none(기본값). __Validate__ 없이 __Checksum__을 지정하는 경우, 구성이 실패합니다.|
| Ensure| 보관 파일의 내용이 __Destination__에 있는지 확인할지 여부를 결정합니다. 내용이 있도록 하려면 이 속성을 __Present__으로 설정합니다. 내용이 없도록 하려면 이 속성을 __Absent__으로 설정합니다. 기본값은 __Present__입니다.|
| DependsOn | 이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 __ResourceType__일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다.|
| 유효성 검사| 보관 파일이 서명과 일치하는지 여부를 결정하려면 체크섬 속성을 사용합니다. 유효성 검사 없이 체크섬을 지정하면 구성이 실패합니다. 체크섬 없이 유효성 검사를 지정하면 기본적으로 SHA-256 체크섬이 사용됩니다.|
| Force| 특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다. Force 속성을 사용하면 이러한 오류가 무시됩니다. 기본값은 False입니다.|

## <a name="example"></a>예제

다음 예제에서는 보관 리소스를 사용하여 Test.zip이라는 보관 파일의 내용이 존재하고 지정된 대상에 압축이 풀리도록 하는 방법을 보여줍니다.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```