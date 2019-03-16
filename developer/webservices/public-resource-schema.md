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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057249"
---
# <a name="public-resource-schema"></a>공용 리소스 스키마

관리 OData MOF를 사용 하 여 리소스 및 해당 속성을 정의 합니다. 기본 cmdlet에서 반환 되는 관리 되는 형식의 속성에 직접 해당 하는 관리 OData 엔터티의 속성입니다.

## <a name="defining-a-resource"></a>리소스를 정의합니다.

각 리소스는 Windows PowerShell cmdlet에서 반환 된 개체에 해당 합니다. 공용 리소스 MOF 파일에서 클래스를 선언 하 여 리소스를 정의 합니다. 클래스 개체의 속성에 해당 하는 속성으로 구성 됩니다. 예를 들어, 다음 예제에에서는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 클래스 MOF를 다음으로 표시 됩니다.

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

각 속성 이름 앞에 데이터 형식입니다. 이 예제의 데이터 형식은.NET Framework의 기본 CLR 데이터 형식에 해당 하지만 속성에 다른 리소스 또는 둘 다 뒷부분에서 설명 하는 복합 형식에 대 한 참조 될 수도 있습니다.

`Key` 한정자 리소스 인스턴스를 고유 하 게 식별 하는 속성 사용 됨을 나타냅니다. 리소스를 둘 이상의 키를 있습니다.

`Required` 한정자 속성이 필수임을 나타냅니다. 속성은 레이블이 지정 된 경우는 `Key` 필요한으로 간주 됩니다 한정자 및 `Required` 한정자 필요 하지 않습니다.

### <a name="complex-data-types"></a>복잡 한 데이터 형식

엔터티의 속성에는 복잡 한 데이터 형식을 가질 수 있습니다. 복합 데이터 형식은 C 프로그래밍 언어의 구조체에 다른 종류의 구성 된 형식입니다. 복합 형식을 사용 하 여 클래스도 MOF 파일에 선언 되는 `ComplexType` 다음 예제와 같이 한정자입니다.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

복합 형식으로 엔터티 속성을 선언 하면 선언으로 `string` 유형과 `EmbeddedInstance` 복합 형식의 이름을 포함 하 여 한정자입니다. 다음 예제에서는 속성의 선언을 보여 줍니다는 `PswsTest_ProcessModule` 이전 예제에서 형식 선언 합니다.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>엔터티 연결

연결과 연관 클래스 한정자를 사용 하 여 두 엔터티를 연결할 수 있습니다. 자세한 내용은 [연결 관리 OData 엔터티](./associating-management-odata-entities.md)합니다.

### <a name="derived-types"></a>파생된 형식

다른 형식에서 형식을 파생할 수 있습니다. 파생된 된 형식의 모든 파생 되는 명시적으로 파생 된 모든 속성 외에도 유형의 속성을 상속 합니다. 다음 예제에서는 형식 선언 및 해당 형식에서 파생 된 두 종류의 선언을 보여 줍니다.

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