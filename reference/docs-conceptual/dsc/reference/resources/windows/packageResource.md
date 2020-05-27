---
ms.date: 09/20/2019
keywords: dsc,powershell,configuration,setup
title: DSC 패키지 리소스
ms.openlocfilehash: ff2eae712b4117da9bca915f52e18caed7c4885d
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559933"
---
# <a name="dsc-package-resource"></a>DSC 패키지 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

Windows PowerShell DSC(필요한 상태 구성)의 **Package** 리소스에서는 대상 노드에서 Windows Installer나 setup.exe 패키지와 같은 패키지를 설치하거나 제거하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ ReturnCode = [UInt32[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|속성 |특정 상태가 되게 할 패키지의 이름을 나타냅니다. |
|경로 |패키지가 있는 경로 나타냅니다. |
|ProductId |패키지를 고유하게 식별하는 제품 ID를 나타냅니다. |
|인수 |제공된 대로 패키지에 전달할 인수 문자열을 나열합니다. |
|자격 증명 |원격 소스에 있는 패키지에 액세스할 수 있도록 합니다. 이 속성은 패키지를 설치하는 데 사용되지 않습니다. 패키지는 항상 로컬 시스템에 설치합니다. |
|LogPath |패키지를 설치하거나 제거하기 위해 공급자가 로그 파일을 저장하도록 하려는 전체 경로를 나타냅니다. |
|ReturnCode |예상된 반환 코드를 나타냅니다. 실제 반환 코드가 여기에 제공된 예상 값과 일치하지 않는 경우 구성에서 오류를 반환하게 됩니다. |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |패키지가 설치되어 있는지 여부를 나타냅니다. 패키지가 설치되어 있지 않도록 하려면(또는 설치되어 있다면 패키지를 제거) 이 속성을 **Absent**로 설정합니다. 패키지가 설치되어 있도록 하려면 이 속성을 **Present**로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="example"></a>예제

이 예제에서는 지정된 경로에 있고 지정된 제품 ID를 갖는 .msi 설치 관리자를 실행합니다.

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```
