---
ms.date: 07/16/2020
keywords: dsc,powershell,configuration,setup
title: DSC 레지스트리 리소스
ms.openlocfilehash: da4be9152a58d9945051f9c811270e871612ca0d
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463621"
---
# <a name="dsc-registry-resource"></a>DSC 레지스트리 리소스

> 적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.x

PowerShell DSC(필요한 상태 구성)의 **레지스트리** 리소스에서는 대상 노드에 있는 레지스트리 키와 값을 관리하는 메커니즘을 제공합니다.

## <a name="syntax"></a>구문

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>속성

|속성 |Description |
|---|---|
|키 |특정 상태를 확인하려는 레지스트리 키의 경로를 나타냅니다. 이 경로는 하이브를 포함해야 합니다. |
|ValueName |레지스트리 값의 이름을 나타냅니다. 레지스트리 키를 추가하거나 제거하려면 **ValueType** 또는 **ValueData**를 지정하지 않고 이 속성을 빈 문자열로 지정합니다. 레지스트리 키의 기본값을 수정하거나 제거하려면 **ValueType** 또는 **ValueData**도 지정하고 이 속성을 빈 문자열로 지정합니다. |
|Force |지정된 레지스트리 키가 있을 경우, **Force**를 사용하면 새 값으로 덮어씁니다. 하위 키가 포함된 레지스트리 키를 삭제하는 경우에는 이 속성을 `$true`로 지정해야 합니다. |
|Hex |데이터가 16진수 형식으로 표현될 것인지 여부를 나타냅니다. 지정하는 경우 DWORD/QWORD 값 데이터가 16진수 형식으로 표시됩니다. 다른 형식에 대해서는 유효하지 않습니다. 기본값은 `$false`입니다. |
|ValueData |레지스트리 값에 대한 데이터입니다. |
|ValueType |값의 형식을 나타냅니다. 지원되는 형식은 다음과 같습니다. **문자열**(REG_SZ), **이진**(REG-BINARY), **Dword**(32-bit REG_DWORD), **Qword**(64-bit REG_QWORD), **MultiString**(REG_MULTI_SZ), **ExpandString**(REG_EXPAND_SZ). |

## <a name="common-properties"></a>공용 속성

|속성 |Description |
|---|---|
|DependsOn |이 리소스를 구성하려면 먼저 다른 리소스의 구성을 실행해야 함을 나타냅니다. 예를 들어, 먼저 실행하려는 리소스 구성 스크립트 블록의 ID가 ResourceName이고 해당 형식이 ResourceType일 경우, 이 속성을 사용하기 위한 구문은 `DependsOn = "[ResourceType]ResourceName"`입니다. |
|Ensure |키와 값의 존재 여부를 나타냅니다. 존재하도록 하려면 이 속성을 **Present**로 설정합니다. 존재하지 않도록 하려면 이 속성을 **Absent**로 설정합니다. 기본값은 **Present**입니다. |
|PsDscRunAsCredential |전체 리소스를 실행하기 위한 자격 증명을 설정합니다. |

> [!NOTE]
> **PsDscRunAsCredential** 공용 속성은 다른 자격 증명의 컨텍스트에서 DSC 리소스를 실행할 수 있도록 WMF 5.0에 추가되었습니다. 자세한 내용은 [ DSC 리소스로 자격 증명 사용](../../../configurations/runasuser.md)을 참조하세요.

## <a name="examples"></a>예

### <a name="example-1-ensure-specified-value-and-data-under-specified-registry-key"></a>예제 1: 지정된 값과 데이터가 지정된 레지스트리 키에 있는지 확인

이 예에서는 "ExampleKey1" 라는 키에 속하는 레지스트리 값 "TestValue"가 `HKEY\_LOCAL\_MACHINE` 하이브에 있고 데이터 "TestData"가 있는지 확인합니다.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey1"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

### <a name="example-2-ensure-specified-registry-key-exists"></a>예제 2: 지정된 레지스트리 키가 존재하는지 확인

이 예제에서는 "ExampleKe2"라는 키가 **HKEY\_LOCAL\_MACHINE** 하이브에 있는지 확인합니다.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey2"
        ValueName   = ""
    }
}
```

> [!NOTE]
> `HKEY_CURRENT_USER` 하이브에서 레지스트리 설정을 변경하려면 구성이 시스템이 아닌 사용자 자격 증명을 사용하여 실행되어야 합니다. **PsDscRunAsCredential** 속성을 사용하여 구성에 대한 사용자 자격 증명을 지정할 수 있습니다. 예제는 [사용자 자격 증명을 사용하여 DSC 실행](../../../configurations/runAsUser.md)을 참조하세요.
