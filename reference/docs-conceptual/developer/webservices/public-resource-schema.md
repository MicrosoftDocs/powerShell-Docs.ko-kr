---
title: 공용 리소스 스키마 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: 52244ee7496b99e11f0306e93728736fc9c51be5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564706"
---
# <a name="public-resource-schema"></a>공용 리소스 스키마

관리 OData는 MOF를 사용 하 여 리소스 및 해당 속성을 정의 합니다. 관리 OData 엔터티의 속성은 기본 cmdlet에서 반환 된 관리 되는 형식의 속성에 직접 해당 합니다.

## <a name="defining-a-resource"></a>리소스 정의

각 리소스는 Windows PowerShell cmdlet에서 반환 되는 개체에 해당 합니다. 공용 리소스 MOF 파일에서 클래스를 선언 하 여 리소스를 정의 합니다. 클래스는 개체의 속성에 해당 하는 속성으로 구성 됩니다. 예를 들어 다음 예제에서 [system.object](/dotnet/api/System.Diagnostics.Process) 클래스는 다음 MOF로 표시 됩니다.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

각 속성 이름 앞에는 데이터 형식이 있습니다. 이 예제의 데이터 형식은 .NET Framework의 기본 CLR 데이터 형식에 해당 하지만 속성은 나중에 설명 하는 다른 리소스나 복합 형식에 대 한 참조일 수도 있습니다.

`Key`한정자는 속성이 리소스 인스턴스를 고유 하 게 식별 하는 데 사용 됨을 나타냅니다. 리소스에는 두 개 이상의 키가 있을 수 있습니다.

`Required`한정자는 속성이 필요 함을 나타냅니다. 속성이 한정자를 사용 하 여 레이블이 지정 된 경우 필요한 것으로 `Key` 간주 되며 `Required` 한정자는 필요 하지 않습니다.

### <a name="complex-data-types"></a>복합 데이터 형식

엔터티의 속성에는 복잡 한 데이터 형식이 있을 수 있습니다. 복합 데이터 형식은 C 프로그래밍 언어의 구조체와 마찬가지로 다른 형식으로 구성 된 형식입니다. 다음 예제와 같이 복합 형식은 MOF 파일에서 한정자를 사용 하는 클래스로 선언 됩니다 `ComplexType` .

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

엔터티 속성을 복합 형식으로 선언 하려면 `string` `EmbeddedInstance` 복합 형식의 이름을 포함 하 여 한정자를 사용 하 여 형식으로 선언 합니다. 다음 예제에서는 `PswsTest_ProcessModule` 이전 예제에서 선언 된 형식의 속성을 선언 하는 방법을 보여 줍니다.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>엔터티 연결

Association 및 AssociationClass 한정자를 사용 하 여 두 엔터티를 연결할 수 있습니다. 자세한 내용은 [관리 OData 엔터티 연결](./associating-management-odata-entities.md)을 참조 하세요.

### <a name="derived-types"></a>파생 형식

다른 형식에서 형식을 파생 시킬 수 있습니다. 파생 된 형식은 명시적으로 파생 된 모든 속성과 함께 파생 되는 형식의 모든 속성을 상속 합니다. 다음 예제에서는 형식 선언과 해당 형식에서 파생 된 두 형식의 선언을 보여 줍니다.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```
