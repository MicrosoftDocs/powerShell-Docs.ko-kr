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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366272"
---
# <a name="public-resource-schema"></a><span data-ttu-id="f9169-102">공용 리소스 스키마</span><span class="sxs-lookup"><span data-stu-id="f9169-102">Public Resource Schema</span></span>

<span data-ttu-id="f9169-103">관리 OData는 MOF를 사용 하 여 리소스 및 해당 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="f9169-104">관리 OData 엔터티의 속성은 기본 cmdlet에서 반환 된 관리 되는 형식의 속성에 직접 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="f9169-105">리소스 정의</span><span class="sxs-lookup"><span data-stu-id="f9169-105">Defining a resource</span></span>

<span data-ttu-id="f9169-106">각 리소스는 Windows PowerShell cmdlet에서 반환 되는 개체에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="f9169-107">공용 리소스 MOF 파일에서 클래스를 선언 하 여 리소스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="f9169-108">클래스는 개체의 속성에 해당 하는 속성으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="f9169-109">예를 들어 다음 예제에서 [system.object](/dotnet/api/System.Diagnostics.Process) 클래스는 다음 MOF로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="f9169-110">각 속성 이름 앞에는 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="f9169-111">이 예제의 데이터 형식은 .NET Framework의 기본 CLR 데이터 형식에 해당 하지만 속성은 나중에 설명 하는 다른 리소스나 복합 형식에 대 한 참조일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="f9169-112">`Key` 한정자는 속성이 리소스 인스턴스를 고유 하 게 식별 하는 데 사용 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="f9169-113">리소스에는 두 개 이상의 키가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-113">A resource can have more than one key.</span></span>

<span data-ttu-id="f9169-114">`Required` 한정자는 속성이 필요 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="f9169-115">속성에 `Key` 한정자가 지정 된 경우 필요한 것으로 간주 되며 `Required` 한정자는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="f9169-116">복합 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="f9169-116">Complex data types</span></span>

<span data-ttu-id="f9169-117">엔터티의 속성에는 복잡 한 데이터 형식이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="f9169-118">복합 데이터 형식은 C 프로그래밍 언어의 구조체와 마찬가지로 다른 형식으로 구성 된 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="f9169-119">복합 형식은 다음 예제와 같이 `ComplexType` 한정자를 사용 하 여 MOF 파일에서 클래스로 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="f9169-120">엔터티 속성을 복합 형식으로 선언 하려면 복합 형식의 이름을 포함 하 여 `EmbeddedInstance` 한정자를 사용 하 여 `string` 형식으로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="f9169-121">다음 예제에서는 이전 예제에서 선언 된 `PswsTest_ProcessModule` 형식의 속성을 선언 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="f9169-122">엔터티 연결</span><span class="sxs-lookup"><span data-stu-id="f9169-122">Associating entities</span></span>

<span data-ttu-id="f9169-123">Association 및 AssociationClass 한정자를 사용 하 여 두 엔터티를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="f9169-124">자세한 내용은 [관리 OData 엔터티 연결](./associating-management-odata-entities.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f9169-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="f9169-125">파생 형식</span><span class="sxs-lookup"><span data-stu-id="f9169-125">Derived types</span></span>

<span data-ttu-id="f9169-126">다른 형식에서 형식을 파생 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-126">You can derive a type from another type.</span></span> <span data-ttu-id="f9169-127">파생 된 형식은 명시적으로 파생 된 모든 속성과 함께 파생 되는 형식의 모든 속성을 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="f9169-128">다음 예제에서는 형식 선언과 해당 형식에서 파생 된 두 형식의 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9169-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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