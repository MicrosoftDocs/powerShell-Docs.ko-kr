---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794498"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a>OData 엔드포인트에 따라 PowerShell Cmdlet 생성

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a>OData 엔드포인트에 따라 Windows PowerShell cmdlet 생성

**Export-ODataEndpointProxy**는 지정된 OData 엔드포인트에서 제공하는 기능에 따라 Windows PowerShell cmdlet 집합을 생성하는 cmdlet입니다.

다음 예제에서 이 새로운 cmdlet을 사용하는 방법을 보여 줍니다.

```powershell
Export-ODataEndpointProxy -Uri 'http://services.odata.org/v3/(S(snyobsk1hhutkb2yulwldgf1))/odata/odata.svc' -OutputModule C:\Users\user\Generated.psd1

ipmo 'C:\Users\user\Generated.psd1'
# Cmdlets are created based on the following heuristics
# New-<EntityType> -<Key> [-<Other Attributes>]
#
# Get-<EntityType> [-<Key> -Top –Skip –Filter -OrderBy]
# # If there is a complex key, the keys will actually be -<Key1> -<Key2>…
# # Note this rule applies to any other instances of the key
#
# Set-<EntityType> -<Key> [-<Other Attributes>]
#
# Remove-<EntityType> -<Key>
#
# Invoke-<EntityType><Action> [-<Key> -<Other Parameters>]
#
#
# Cmdlets from associations (Note: Get and Remove get additional parameter sets)
# Get-<EntityType> -<AssociatedEntity>
# New-<EntityType> -<AssociatedEntity> -<Key>
# Remove-<EntityType> -<AssociatedEntity> -<Key>
#
#
# Note: Every cmdlet has the –ConnectionURI parameter for explicitly setting the URI of the endpoint. This normally uses the same address that you gave the Export-ODataEndpointProxy cmdlet, but can be overridden in this fashion for the sake of similar endpoints.
#
```

이 기능의 개발에 대한 몇 가지 주요 사용 사례가 있으며, 다음을 포함하되 이에 국한되지 않습니다.
-   연결
-   스트림 전달

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a>ODataUtils를 사용하여 OData 엔드포인트에 따라 Windows PowerShell cmdlet 생성

ODataUtils 모듈에서는 OData를 지원하는 REST 엔드포인트에서 Windows PowerShell cmdlet을 생성할 수 있습니다. 다음과 같은 증분 향상 기능이 Microsoft.PowerShell.ODataUtils Windows PowerShell 모듈에 있습니다.
-   서버 쪽 엔드포인트와 클라이언트 쪽 사이에서 추가 정보 연결
-   클라이언트 쪽 페이징 지원
-   -Select 매개 변수를 사용하여 서버 쪽 필터링
-   웹 요청 헤더에 대한 지원

Export-ODataEndPointProxy cmdlet에서 생성된 프록시 cmdlet은 정보 스트림(새로운 Windows PowerShell 5.0 기능)의 서버 쪽 OData 엔드포인트에서 추가 정보(클라이언트 쪽 프록시 생성 중 사용된 $metadata에 언급되지 않은 정보)를 제공합니다. 다음은 해당 정보를 가져오는 방법에 대한 예입니다.

```powershell
Import-Module Microsoft.PowerShell.ODataUtils -Force
$generatedProxyModuleDir = Join-Path -Path $env:SystemDrive -ChildPath 'ODataDemoProxy'
$uri = "http://services.odata.org/V3/(S(fhleiief23wrm5a5nhf542q5))/OData/OData.svc/"
Export-ODataEndpointProxy -Uri $uri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -AllowClobber
Import-Module $generatedProxyModuleDir -Force

# In the below command, we are retrieving top 1 product.
# By specifying -IncludeTotalResponseCount parameter,
# we are getting the total count of all the Product records
# available on the server side. This information
# is surfaced on the client side through the Information stream.
$product = Get-Product -Top 1 -AllowUnsecureConnection -AllowAdditionalData -IncludeTotalResponseCount -InformationVariable infoStream
# The Information stream contains the additional
# information sent from the server side.
$additionalInfo = $infoStream.GetEnumerator() | % MessageData
# 'Odata.Count' indicates the total product records
# available on the server side Odata endpoint.
$additionalInfo['odata.count']
```

클라이언트 쪽 페이징 지원을 사용하여 서버 쪽에서 레코드를 일괄 처리로 가져올 수 있습니다. 이 방법은 네트워크를 통해 서버에서 많은 양의 데이터를 가져와야 하는 경우에 유용합니다.

```powershell
$skipCount = 0
$batchSize = 3
# Client-Side Paging Support: The records from the server side
# are retrieved in batches of $batchSize
while($skipCount -le $additionalInfo['odata.count'])
{
Get-Product -AllowUnsecureConnection -AllowAdditionalData -Top $batchSize -Skip $skipCount
$skipCount += $batchSize
}
```

생성된 프록시 cmdlet은 클라이언트에 필요한 레코드 속성만 받는 필터로 사용할 수 있는 –Select 매개 변수를 지원합니다. 이렇게 하면 필터링이 서버 쪽에서 수행되므로 네트워크를 통해 전송되는 데이터의 양이 줄어듭니다.

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

Export-ODataEndpointProxy cmdlet과 이 cmdlet에서 생성된 프록시 cmdlet은 Headers 매개 변수(해시 테이블로 값 제공)를 지원하여 서버 쪽 OData 엔드포인트에 필요한 추가 정보를 연결하는 데 사용할 수 있습니다. 다음 예제에서는 인증에 구독 키가 필요한 서비스에 대해 Headers를 통해 구독 키를 연결할 수 있습니다.

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
