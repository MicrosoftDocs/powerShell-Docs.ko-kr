---
title: 추가 하는 방법 참조도 섹션 공급자 도움말 항목 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858349"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>공급자 도움말 항목에 참고 항목 섹션을 추가하는 방법

이 섹션에서는를 채우는 방법을 설명 합니다 **참고** 공급자 도움말 항목의 섹션입니다.

합니다 **참고** 공급자에 게 관련 된 또는 사용자를 더 잘 이해 하 고 공급자를 사용 하 여는 데 도움이 되는 항목의 목록 섹션으로 구성 됩니다. 항목 목록에는 cmdlet 도움말, 공급자 도움말 포함 될 수 있습니다 ("정보") 도움말 항목 Windows PowerShell의 개념 및 합니다. 온라인 설명서, 백서, 및 현재 공급자 도움말 항목의 온라인 버전을 비롯 하 여 온라인 항목에 대 한 참조를 포함할 수도 있습니다.

온라인 항목을 참조 하는 경우 URI 또는 일반 텍스트에서 검색어를 제공 합니다. `Get-Help` cmdlet에 연결 하지 않거나 목록의 항목 중 하나에 리디렉션합니다. 또한 합니다 `Online` 의 매개 변수는 `Get-Help` 공급자 도움말을 사용 하 여 cmdlet이 작동 하지 않습니다.

참고 항목 섹션에서 만든는 `RelatedLinks` 요소 및 포함 하는 태그입니다. 다음 XML 태그를 추가 하는 방법을 보여 줍니다.

### <a name="to-add-see-also-topics"></a>"참조" 항목을 추가 하려면

1. 에 *AssemblyName*help.xml.dll 파일 내 합니다 `providerHelp` 요소를 추가 `RelatedLinks` 요소. 합니다 `RelatedLinks` 요소에는 마지막 요소 여야 합니다.는 `providerHelp` 요소입니다. 하나의 `RelatedLinks` 요소는 각 공급자 도움말 항목에 허용 됩니다.

   예:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. 각 항목에 대 합니다 **참고** 섹션 내는 `RelatedLinks` 요소를 추가 `navigationLink` 요소입니다. 그런 다음, 각 `navigationLink` 요소를 추가할 `linkText` 요소와 `uri` 요소입니다. 사용 하지 않는 경우는 `uri` 요소를 추가할 수 있습니다 빈 요소로 (\<uri / >).

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

3. 이름을 입력 하 고 항목 간에 `linkText` 태그입니다. URI를 제공 하는 경우 입력 간에 `uri` 태그입니다. 현재 공급자 도움말 항목의 온라인 버전 간에 나타내려면는 `linkText` 태그, 형식 "온라인 버전:" 항목 이름 대신 합니다. 일반적으로 "온라인 버전:" 링크 참고 항목 목록에서 첫 번째 항목입니다.

   다음 예제에서는 세 가지 참고 항목을 포함 합니다. 첫 번째 현재 항목의 온라인 버전을 가리킵니다. 두 번째 Windows PowerShell cmdlet 도움말 항목을 가리킵니다. 세 번째 다른 온라인 항목을 가리킵니다.

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
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```