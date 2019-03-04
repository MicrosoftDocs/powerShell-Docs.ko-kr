---
title: 관리 OData 엔터티를 연결 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860829"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="02e15-102">관리 OData 엔터티 연결</span><span class="sxs-lookup"><span data-stu-id="02e15-102">Associating Management OData Entities</span></span>

<span data-ttu-id="02e15-103">서로 다른 두 관리 OData 엔터티 사이 연결 하는 것이 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="02e15-104">관리 OData 서비스를 범주에서 구성 되는 제품의 카탈로그를 관리 하는 엔터티를 가질 수 없습니다 및 엔터티를 정의 되는 예를 들어 `Product` 고 `Category`입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="02e15-105">이러한 두 엔터티를 연결 하 여 클라이언트가 웹 서비스에 대 한 단일 요청을 사용 하 여 범주에서 모든 제품에 대 한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="02e15-106">엔터티 간의 연결을 만드는 방법을 보여 주는 샘플을 다운로드할 수 있습니다 [연결 샘플](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="02e15-107">리소스 스키마 파일에서 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="02e15-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="02e15-108">다음 MOF 두 엔터티를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-108">The following MOF defines two entities.</span></span> <span data-ttu-id="02e15-109">이들 간의 연결을 만들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="02e15-110">`Category` 클래스는 해당 범주에 속하는 제품의 이름 배열이 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="02e15-111">두 엔터티를 연결 하려면 클래스를 정의 해야 합니다 `Association` 서비스에 대 한 리소스 스키마 MOF 파일에는 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="02e15-112">클래스는 두 엔터티를 연결 된 호출 수를 정의 해야 `ends` 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="02e15-113">다음 예제에서는 범주 및 제품 엔터티 간의 연결을 정의 하는 클래스의 정의 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="02e15-114">범주 클래스의 Products 속성의 선언을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="02e15-115">사용 된 `AssociationClass` 속성이 연결의 한쪽 끝 임을 지정 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="02e15-116">속성은 문자열의 배열 대신 별도 엔터티를 참조로도 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="02e15-117">사용 하 여이 작업을 수행 합니다 `ref` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="02e15-118">다음 예제에서는 연결에 대 한 속성 정을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="02e15-119">속성 정의를 추가 하 여 연결의 반대쪽을 선언 해야 합니다는 마지막으로 `Product` 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="02e15-120">이 배열 또는 단일 엔터티를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="02e15-121">각 제품 하나의 범주에 속하는 가정 정의 다음과 같은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="02e15-122">연결의 두 end를 나타내는 속성에는 탐색 속성 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="02e15-123">리소스 스키마 파일에서 엔터티를 연결 하는 단계</span><span class="sxs-lookup"><span data-stu-id="02e15-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="02e15-124">연결을 사용 하 여 클래스로 정의 된 `Association` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="02e15-125">연결 된 엔터티의 속성을 한정 연관 클래스 키워드를 사용 하 여 연결의 end를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="02e15-126">리소스 매핑 XML 파일에서 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="02e15-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="02e15-127">리소스 매핑 XML 파일에서 연결을 매핑하면 때 고려해 야 할 세 가지 다른 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="02e15-128">리소스 매핑 파일에서 엔터티를 연결 하는 방법 결정</span><span class="sxs-lookup"><span data-stu-id="02e15-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="02e15-129">탐색 속성은 경우에 기본 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="02e15-130">.NET framework 형식 및 속성에 외래 키를 명시적 매핑이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="02e15-131">기본.NET Framework 형식에 탐색 속성이 없으면 연결된 된 인스턴스 키의 목록을 검색 하는 cmdlet을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="02e15-132">추가 하 여이 작업을 수행는 `Association` 요소 아래에 중첩 합니다 `CmdletImplementation` 요소를 정의 하는 요소 뒤를 `cmdlets` 다른 CRUD 명령에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="02e15-133">기본.NET Framework 형식에 탐색 속성이 존재 하지만 외래 키 대신 개체 인스턴스가 포함 된 경우 (Windows PowerShell 함수 또는 스크립트 작성)에서 cmdlet을 만들어야 합니다 외래 키를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="02e15-134">다음 리소스 매핑 파일에서 해당 cmdlet을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="02e15-135">예를 들어, 키를 검색 하는 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="02e15-136">및 리소스 매핑 파일에서 XML은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="02e15-137">연결된 된 엔터티를 검색 하는 cmdlet를 지정 하는 것 외에도 추가 하 고 컬렉션에서 참조를 제거 하는 cmdlet도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="02e15-138">다음 예제에서는 ProductToCategory 추가 및 제거 ProductFromCategory cmdlet 있는지 (도 정의할 수 있습니다 이전 예제와 같이 함수나 스크립트에서).</span><span class="sxs-lookup"><span data-stu-id="02e15-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="02e15-139">연결 된 엔터티를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-139">Querying associated entities</span></span>

<span data-ttu-id="02e15-140">클라이언트는 특정 쿼리를 만들어 엔터티를 사용 하 여 연결 된 인스턴스 목록을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="02e15-141">연결 된 엔터티에 대 한 쿼리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="02e15-142">클라이언트는 해당 관련된 제품을 검색 하지 않고 범주의 세부 정보를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="02e15-143">예를 들어 다음 요청 세부 정보를 가져옵니다는 `food` 범주입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="02e15-144">연결 된 제품 범주를 가져오려면 (하지만 세부 정보를 하지 범주의 자체 클라이언트 요청에 탐색 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="02e15-145">제품의 Url만 검색 하려면 사용는 `$links` 요청에는 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="02e15-146">클라이언트를 사용 하 여 범주 세부 정보 및 해당 관련된 제품이 모두를 가져올 수는 `$expand` 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="02e15-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="02e15-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="02e15-147">See Also</span></span>

[<span data-ttu-id="02e15-148">관리 OData IIS 확장 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="02e15-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)