---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 보관 리소스
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954770"
---
# <a name="dsc-archive-resource"></a>DSC 보관 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 보관 리소스는 특정 경로에서 보관(.zip) 파일의 압축을 푸는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |설명 |
|---|---|
|대상 |보관 파일 내용을 추출해 놓을 위치를 지정합니다. |
|경로 |보관 파일의 원본 경로를 지정합니다. |
|체크섬 |두 파일이 동일한 것인지 결정할 때 사용할 형식을 정의합니다. **Checksum**을 지정하지 않은 경우 비교에 파일 또는 디렉터리 이름만 사용됩니다. 유효한 값은 다음과 같습니다. **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. **Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다. |
|Force |특정 파일 작업(예: 파일 덮어쓰기나 비어 있지 않은 디렉터리 삭제)을 수행하면 오류가 발생합니다. **Force** 속성을 사용하면 이러한 오류가 무시됩니다. 기본값은 **False**입니다. |
|유효성 검사| 보관 파일이 서명과 일치하는지 여부를 결정하려면 **체크섬** 속성을 사용합니다. **Validate** 없이 **Checksum**을 지정하는 경우, 구성이 실패합니다. **체크섬** 없이 **유효성 검사**를 지정하면 기본적으로 _SHA-256_ **체크섬**이 사용됩니다. |

## <a name="common-properties"></a>공용 속성

|속성 |설명 |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |보관 파일의 내용이 **Destination**에 있는지 확인할지 여부를 결정합니다. 내용이 있도록 하려면 이 속성을 **Present**으로 설정합니다. 내용이 없도록 하려면 이 속성을 **Absent**으로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

다음 예제에서는 Archive 리소스를 사용하여 `Test.zip`이라는 보관 파일의 내용이 존재하고 지정된 대상에 압축이 풀리도록 하는 방법을 보여줍니다.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```