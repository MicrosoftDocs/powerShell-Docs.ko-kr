---
title: 관리 OData 엔터티 연결 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359812"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="d889a-102">관리 OData 엔터티 연결</span><span class="sxs-lookup"><span data-stu-id="d889a-102">Associating Management OData Entities</span></span>

<span data-ttu-id="d889a-103">서로 다른 두 관리 OData 엔터티 간에 연결을 만드는 것이 유용한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="d889a-104">예를 들어 관리 OData 서비스는 범주로 구성 된 제품의 카탈로그를 관리 하는 엔터티를 가질 수 있으며 `Product` 및 `Category`엔터티를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="d889a-105">클라이언트는 이러한 두 엔터티를 연결 하 여 웹 서비스에 대 한 단일 요청으로 범주의 모든 제품에 대 한 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="d889a-106">엔터티 간의 연결을 만드는 방법을 보여 주는 샘플은 [연결 샘플](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="d889a-107">리소스 스키마 파일에서 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="d889a-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="d889a-108">다음 MOF는 두 엔터티를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-108">The following MOF defines two entities.</span></span> <span data-ttu-id="d889a-109">두 항목 간에 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-109">We will create an association between them.</span></span>

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

<span data-ttu-id="d889a-110">`Category` 클래스는 해당 범주에 속하는 제품의 이름 배열인 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="d889a-111">두 엔터티를 연결 하려면 서비스에 대 한 리소스 스키마 MOF 파일에서 `Association` 특성을 사용 하 여 클래스를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="d889a-112">클래스는 연결 된 두 엔터티를 정의 해야 합니다 (연결의 `ends` 이라고 함).</span><span class="sxs-lookup"><span data-stu-id="d889a-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="d889a-113">다음 예제에서는 Category와 Products 엔터티 간의 연결을 정의 하는 클래스의 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="d889a-114">또한 Category 클래스에서 Products 속성의 선언을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="d889a-115">`AssociationClass` 키워드를 사용 하 여 속성이 연결의 한쪽 end 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="d889a-116">또한 속성은 문자열 배열이 아니라 개별 엔터티에 대 한 참조로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="d889a-117">`ref` 키워드를 사용 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="d889a-118">다음 예에서는 연결에 대 한 속성 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="d889a-119">마지막으로 `Product` 클래스에 속성 정의를 추가 하 여 연결의 다른 end를 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="d889a-120">배열이 나 단일 엔터티에 대 한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="d889a-121">각 제품이 하나의 범주에만 속해 있다고 가정할 경우 정의는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="d889a-122">연결의 두 end를 나타내는 속성을 탐색 속성 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="d889a-123">리소스 스키마 파일에서 엔터티를 연결 하는 단계</span><span class="sxs-lookup"><span data-stu-id="d889a-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="d889a-124">`Association` 키워드를 사용 하 여 연결을 클래스로 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="d889a-125">AssociationClass 키워드를 사용 하 여 연결의 끝을 정의 하 여 연결 된 엔터티의 속성을 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="d889a-126">리소스 매핑 XML 파일에 연결 만들기</span><span class="sxs-lookup"><span data-stu-id="d889a-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="d889a-127">리소스 매핑 XML 파일에서 연결을 매핑할 때 세 가지 다른 사례를 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="d889a-128">리소스 매핑 파일에서 엔터티를 연결 하는 방법 결정</span><span class="sxs-lookup"><span data-stu-id="d889a-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="d889a-129">탐색 속성이 내부에 있으면입니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="d889a-130">.NET Framework 형식이 고이 속성에 외래 키가 포함 되어 있으면 명시적 매핑이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="d889a-131">탐색 속성이 내부 .NET Framework 형식에 없는 경우 연결 된 인스턴스의 키 목록을 검색 하는 cmdlet을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="d889a-132">이렇게 하려면 다른 CRUD 명령의 `cmdlets`을 정의 하는 요소를 따라 `CmdletImplementation` 요소 아래에 중첩 된 `Association` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

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

- <span data-ttu-id="d889a-133">탐색 속성이 기본 .NET Framework 형식에 있지만 외래 키 대신 개체 인스턴스를 포함 하는 경우에는 외래 키를 검색 하기 위해 Windows PowerShell 함수 또는 스크립트를 작성 하 여 cmdlet을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="d889a-134">그런 다음 리소스 매핑 파일에서 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="d889a-135">예를 들어 키를 검색 하는 스크립트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="d889a-136">리소스 매핑 파일의 XML은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-136">And the XML in the resource mapping file would look like the following.</span></span>

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

- <span data-ttu-id="d889a-137">연결 된 엔터티를 검색 하는 cmdlet을 지정 하는 것 외에도 cmdlet을 지정 하 여 컬렉션에서 참조를 추가 하 고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="d889a-138">다음 예에서는 추가-제품 이름 및 제품 제거 (이전 예제와 같이 스크립트나 함수에서 정의 될 수도 있음)가 있는 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

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

## <a name="querying-associated-entities"></a><span data-ttu-id="d889a-139">연결 된 엔터티 쿼리</span><span class="sxs-lookup"><span data-stu-id="d889a-139">Querying associated entities</span></span>

<span data-ttu-id="d889a-140">클라이언트는 특정 쿼리를 만들어 엔터티와 연결 된 인스턴스 목록을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="d889a-141">연결 된 엔터티에 대 한 쿼리 생성</span><span class="sxs-lookup"><span data-stu-id="d889a-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="d889a-142">클라이언트는 연결 된 제품을 검색 하지 않고 범주의 세부 정보를 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="d889a-143">예를 들어 다음 요청은 `food` 범주에 대 한 세부 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="d889a-144">범주 자체의 세부 정보는 제외 하 고 범주의 관련 된 제품을 가져오기 위해 클라이언트는 요청에서 탐색 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="d889a-145">제품의 Url만 검색 하려면 요청에 `$links` 한정자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="d889a-146">클라이언트는 `$expand` 한정자를 사용 하 여 범주 세부 정보와 연결 된 제품을 모두 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d889a-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="d889a-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d889a-147">See Also</span></span>

[<span data-ttu-id="d889a-148">관리 OData IIS 확장 웹 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="d889a-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)