---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리 검색 구문
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084303"
---
# <a name="gallery-search-syntax"></a>갤러리 검색 구문

[PowerShell 갤러리 웹 사이트](https://www.powershellgallery.com/)를 사용하여 PowerShell 갤러리를 검색할 수 있습니다.
PowerShell 갤러리 웹 사이트는 단어, 구 및 키워드 식을 사용하여 검색 결과 범위를 좁힐 수 있는 텍스트 검색 상자를 제공합니다.

## <a name="search-by-keywords"></a>키워드로 검색

    dsc azure sql

검색은 3가지 키워드를 모두 포함하는 관련 문서를 찾으려고 하며 일치하는 문서를 반환합니다.

## <a name="search-using-phrases-and-keywords"></a>구문 및 키워드를 사용하여 검색

    "azure sql" deployment

따옴표("") 사이에 구를 입력하면 별도 키워드가 아닌 특정 구를 찾도록 검색이 변경됩니다.
일반적으로 일치하는 문서에는 대/소문자 변형(예: "Azure SQL")을 포함하여 "azure sql" 구가 정확하게 포함되어야 하며, 대체로 '배포'라는 단어도 포함됩니다.

## <a name="filtering-on-fields"></a>필드 필터링

특정 패키지 ID(또는 'Id' 또는 'id')를 검색하거나 검색어 앞에 필드 이름을 추가하여 다른 특정 필드를 검색할 수 있습니다.

현재 검색 가능한 필드는 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' 및 'PowerShellVersion'입니다.

[ID와 제목 간의 차이점은 무엇인가요? ID는 콘솔에서 사용하는 이름입니다. 제목은 검색 결과에서 패키지 페이지의 맨 위에 표시되는 내용입니다.]

## <a name="examples"></a>예

    ID:PSReadline
    
"PSReadline"을 포함하는 ID를 사용하여 패키지를 찾습니다.

    Id:"AzureRM.Profile"

ID 필드에 "AzureRM.Profile"이 포함된 패키지를 찾는 다른 방법입니다.

'Id' 필터는 부분 문자열 일치이므로 다음을 검색하는 경우

    Id:"azure"

이 검색은 'AzureRM.Profile' 및 'Azure.Storage'를 포함하는 결과를 제공합니다.

또한 단일 필드에서 여러 키워드를 검색할 수 있습니다. 

    id:azure tags:intellisense

또한 큰따옴표를 사용하여 구를 검색할 수 있습니다.

    id:"azure.storage"

DSC 태그가 있는 패키지를 모두 검색합니다.

    Tags:DSC

지정된 함수가 있는 패키지를 모두 검색합니다.

    Functions:Get-TreeSize

지정된 cmdlet이 있는 패키지를 모두 검색합니다.

    Cmdlets:Get-AzureRmEnvironment

지정된 DSC 리소스 이름이 있는 패키지를 모두 검색합니다.

    DscResources:xArchive

지정된 PowerShellVersion이 있는 패키지를 모두 검색합니다.

    PowerShellVersion:2.0

마지막으로, 지원되지 않는 필드(예: 'commands')를 사용하는 경우 필드가 무시되고 모든 필드가 검색됩니다. 따라서 다음 쿼리의 경우

    commands:blobs storage

다음 쿼리와 똑같이 해석됩니다.

    blobs storage
