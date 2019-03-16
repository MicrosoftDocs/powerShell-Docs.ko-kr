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
# <a name="public-resource-schema"></a><span data-ttu-id="a0e4b-102">공용 리소스 스키마</span><span class="sxs-lookup"><span data-stu-id="a0e4b-102">Public Resource Schema</span></span>

<span data-ttu-id="a0e4b-103">관리 OData MOF를 사용 하 여 리소스 및 해당 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="a0e4b-104">기본 cmdlet에서 반환 되는 관리 되는 형식의 속성에 직접 해당 하는 관리 OData 엔터티의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="a0e4b-105">리소스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-105">Defining a resource</span></span>

<span data-ttu-id="a0e4b-106">각 리소스는 Windows PowerShell cmdlet에서 반환 된 개체에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="a0e4b-107">공용 리소스 MOF 파일에서 클래스를 선언 하 여 리소스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="a0e4b-108">클래스 개체의 속성에 해당 하는 속성으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="a0e4b-109">예를 들어, 다음 예제에에서는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 클래스 MOF를 다음으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="a0e4b-110">각 속성 이름 앞에 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="a0e4b-111">이 예제의 데이터 형식은.NET Framework의 기본 CLR 데이터 형식에 해당 하지만 속성에 다른 리소스 또는 둘 다 뒷부분에서 설명 하는 복합 형식에 대 한 참조 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="a0e4b-112">`Key` 한정자 리소스 인스턴스를 고유 하 게 식별 하는 속성 사용 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="a0e4b-113">리소스를 둘 이상의 키를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-113">A resource can have more than one key.</span></span>

<span data-ttu-id="a0e4b-114">`Required` 한정자 속성이 필수임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="a0e4b-115">속성은 레이블이 지정 된 경우는 `Key` 필요한으로 간주 됩니다 한정자 및 `Required` 한정자 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="a0e4b-116">복잡 한 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="a0e4b-116">Complex data types</span></span>

<span data-ttu-id="a0e4b-117">엔터티의 속성에는 복잡 한 데이터 형식을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="a0e4b-118">복합 데이터 형식은 C 프로그래밍 언어의 구조체에 다른 종류의 구성 된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="a0e4b-119">복합 형식을 사용 하 여 클래스도 MOF 파일에 선언 되는 `ComplexType` 다음 예제와 같이 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="a0e4b-120">복합 형식으로 엔터티 속성을 선언 하면 선언으로 `string` 유형과 `EmbeddedInstance` 복합 형식의 이름을 포함 하 여 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="a0e4b-121">다음 예제에서는 속성의 선언을 보여 줍니다는 `PswsTest_ProcessModule` 이전 예제에서 형식 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="a0e4b-122">엔터티 연결</span><span class="sxs-lookup"><span data-stu-id="a0e4b-122">Associating entities</span></span>

<span data-ttu-id="a0e4b-123">연결과 연관 클래스 한정자를 사용 하 여 두 엔터티를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="a0e4b-124">자세한 내용은 [연결 관리 OData 엔터티](./associating-management-odata-entities.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="a0e4b-125">파생된 형식</span><span class="sxs-lookup"><span data-stu-id="a0e4b-125">Derived types</span></span>

<span data-ttu-id="a0e4b-126">다른 형식에서 형식을 파생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-126">You can derive a type from another type.</span></span> <span data-ttu-id="a0e4b-127">파생된 된 형식의 모든 파생 되는 명시적으로 파생 된 모든 속성 외에도 유형의 속성을 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="a0e4b-128">다음 예제에서는 형식 선언 및 해당 형식에서 파생 된 두 종류의 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a0e4b-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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