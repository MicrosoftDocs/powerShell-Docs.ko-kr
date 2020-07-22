---
title: 공급자 도움말 항목에 참고 항목 섹션을 추가하는 방법
ms.date: 09/12/2016
ms.openlocfilehash: 54adf4bb941888583eb749b7b5322b27d84c7af7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893478"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>공급자 도움말 항목에 참고 항목 섹션을 추가하는 방법

이 섹션에서는 공급자 도움말 항목의 **참고** 항목 섹션을 채우는 방법에 대해 설명 합니다.

**참고** 항목 섹션은 공급자와 관련 된 항목의 목록으로 구성 되거나 사용자가 공급자를 보다 잘 이해 하 고 사용 하는 데 도움이 될 수 있습니다. 항목 목록에는 Windows PowerShell의 cmdlet 도움말, 공급자 도움말 및 개념 ("about") 도움말 항목이 포함 될 수 있습니다. 또한 현재 공급자 도움말 항목의 온라인 버전을 비롯 하 여 책, 용지 및 온라인 항목에 대 한 참조를 포함할 수 있습니다.

온라인 항목을 참조 하는 경우 URI 또는 검색 용어를 일반 텍스트로 제공 합니다. `Get-Help`Cmdlet은 목록에 있는 항목에 연결 하거나 리디렉션하지 않습니다. 또한 `Online` cmdlet의 매개 변수는 `Get-Help` 공급자 도움말에서 작동 하지 않습니다.

**참고** 항목 섹션은 `RelatedLinks` 요소와 요소에 포함 된 태그에서 생성 됩니다.
다음 XML은 태그를 추가 하는 방법을 보여 줍니다.

### <a name="to-add-see-also-topics"></a>항목을 추가 하려면 항목을 참조 하세요.

1. 파일의 `<AssemblyName>.dll-help.xml` 요소 내에 `providerHelp` 요소를 추가 `RelatedLinks` 합니다. 요소는 `RelatedLinks` 요소의 마지막 요소 여야 합니다 `providerHelp` . `RelatedLinks`각 공급자 도움말 항목에는 하나의 요소만 허용 됩니다.

   예:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. **참고** 항목 섹션의 각 항목에 대해 요소 내에서 `RelatedLinks` 요소를 추가 `navigationLink` 합니다. 그런 다음 각 요소 내에서 `navigationLink` 요소 하 나와 요소 하나를 추가 `linkText` `uri` 합니다. 요소를 사용 하지 않는 경우 `uri` 빈 요소 ()로 추가할 수 있습니다 \<uri/> .

   예:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

1. 태그 사이에 항목 이름을 입력 합니다 `linkText` . URI를 제공 하는 경우 태그 사이에 입력 `uri` 합니다. 현재 공급자 도움말 항목의 온라인 버전을 나타내려면 태그 사이에 `linkText` 항목 이름 대신 "online version:"을 입력 합니다. 일반적으로 "온라인 버전:" 링크는 항목 항목 목록의 첫 번째 항목입니다.

   다음 예제에는 세 개의 참고 항목 항목이 포함 되어 있습니다. 첫 번째는 현재 항목의 온라인 버전을 참조 합니다. 두 번째는 Windows PowerShell cmdlet 도움말 항목을 참조 합니다. 세 번째는 다른 온라인 항목을 참조 합니다.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
