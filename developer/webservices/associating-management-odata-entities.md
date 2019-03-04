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
# <a name="associating-management-odata-entities"></a>관리 OData 엔터티 연결

서로 다른 두 관리 OData 엔터티 사이 연결 하는 것이 유용 합니다. 관리 OData 서비스를 범주에서 구성 되는 제품의 카탈로그를 관리 하는 엔터티를 가질 수 없습니다 및 엔터티를 정의 되는 예를 들어 `Product` 고 `Category`입니다. 이러한 두 엔터티를 연결 하 여 클라이언트가 웹 서비스에 대 한 단일 요청을 사용 하 여 범주에서 모든 제품에 대 한 정보를 가져올 수 있습니다.

엔터티 간의 연결을 만드는 방법을 보여 주는 샘플을 다운로드할 수 있습니다 [연결 샘플](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e)합니다.

## <a name="creating-the-association-in-the-resource-schema-file"></a>리소스 스키마 파일에서 연결 만들기

다음 MOF 두 엔터티를 정의합니다. 이들 간의 연결을 만들겠습니다.

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

`Category` 클래스는 해당 범주에 속하는 제품의 이름 배열이 속성을 정의 합니다.

두 엔터티를 연결 하려면 클래스를 정의 해야 합니다 `Association` 서비스에 대 한 리소스 스키마 MOF 파일에는 특성입니다. 클래스는 두 엔터티를 연결 된 호출 수를 정의 해야 `ends` 연결 합니다. 다음 예제에서는 범주 및 제품 엔터티 간의 연결을 정의 하는 클래스의 정의 보여 줍니다.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

범주 클래스의 Products 속성의 선언을 변경 해야 합니다. 사용 된 `AssociationClass` 속성이 연결의 한쪽 끝 임을 지정 하는 키워드입니다. 속성은 문자열의 배열 대신 별도 엔터티를 참조로도 정의 되어야 합니다. 사용 하 여이 작업을 수행 합니다 `ref` 키워드입니다. 다음 예제에서는 연결에 대 한 속성 정을 보여 줍니다.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

속성 정의를 추가 하 여 연결의 반대쪽을 선언 해야 합니다는 마지막으로 `Product` 클래스입니다. 이 배열 또는 단일 엔터티를 참조 합니다. 각 제품 하나의 범주에 속하는 가정 정의 다음과 같은 것입니다.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

연결의 두 end를 나타내는 속성에는 탐색 속성 이라고 합니다.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>리소스 스키마 파일에서 엔터티를 연결 하는 단계

- 연결을 사용 하 여 클래스로 정의 된 `Association` 키워드입니다.

- 연결 된 엔터티의 속성을 한정 연관 클래스 키워드를 사용 하 여 연결의 end를 정의 합니다.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>리소스 매핑 XML 파일에서 연결 만들기

리소스 매핑 XML 파일에서 연결을 매핑하면 때 고려해 야 할 세 가지 다른 경우가 있습니다.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>리소스 매핑 파일에서 엔터티를 연결 하는 방법 결정

- 탐색 속성은 경우에 기본 제공 합니다. .NET framework 형식 및 속성에 외래 키를 명시적 매핑이 필요 하지 않습니다.

- 기본.NET Framework 형식에 탐색 속성이 없으면 연결된 된 인스턴스 키의 목록을 검색 하는 cmdlet을 지정 해야 합니다. 추가 하 여이 작업을 수행는 `Association` 요소 아래에 중첩 합니다 `CmdletImplementation` 요소를 정의 하는 요소 뒤를 `cmdlets` 다른 CRUD 명령에 대 한 합니다.

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

- 기본.NET Framework 형식에 탐색 속성이 존재 하지만 외래 키 대신 개체 인스턴스가 포함 된 경우 (Windows PowerShell 함수 또는 스크립트 작성)에서 cmdlet을 만들어야 합니다 외래 키를 검색 합니다. 다음 리소스 매핑 파일에서 해당 cmdlet을 지정합니다. 예를 들어, 키를 검색 하는 스크립트는 다음과 같습니다.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  및 리소스 매핑 파일에서 XML은 다음과 같습니다.

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

- 연결된 된 엔터티를 검색 하는 cmdlet를 지정 하는 것 외에도 추가 하 고 컬렉션에서 참조를 제거 하는 cmdlet도 지정할 수 있습니다. 다음 예제에서는 ProductToCategory 추가 및 제거 ProductFromCategory cmdlet 있는지 (도 정의할 수 있습니다 이전 예제와 같이 함수나 스크립트에서).

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

## <a name="querying-associated-entities"></a>연결 된 엔터티를 쿼리합니다.

클라이언트는 특정 쿼리를 만들어 엔터티를 사용 하 여 연결 된 인스턴스 목록을 검색할 수 있습니다.

#### <a name="constructing-queries-for-associated-entities"></a>연결 된 엔터티에 대 한 쿼리를 생성합니다.

- 클라이언트는 해당 관련된 제품을 검색 하지 않고 범주의 세부 정보를 요청할 수 있습니다. 예를 들어 다음 요청 세부 정보를 가져옵니다는 `food` 범주입니다.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  연결 된 제품 범주를 가져오려면 (하지만 세부 정보를 하지 범주의 자체 클라이언트 요청에 탐색 속성을 지정 합니다.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- 제품의 Url만 검색 하려면 사용는 `$links` 요청에는 한정자입니다.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- 클라이언트를 사용 하 여 범주 세부 정보 및 해당 관련된 제품이 모두를 가져올 수는 `$expand` 한정자입니다.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>참고 항목

[관리 OData IIS 확장 웹 서비스 만들기](./creating-a-management-odata-web-service.md)