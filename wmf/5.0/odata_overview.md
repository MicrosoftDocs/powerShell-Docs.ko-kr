---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 1153738fdf6f926d5d819bbf91450408dcb17f71
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057811"
---
# <a name="generate-powershell-cmdlets-based-on-odata-endpoint"></a><span data-ttu-id="1052f-102">OData 엔드포인트에 따라 PowerShell Cmdlet 생성</span><span class="sxs-lookup"><span data-stu-id="1052f-102">Generate PowerShell Cmdlets based on OData Endpoint</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint"></a><span data-ttu-id="1052f-103">OData 엔드포인트에 따라 Windows PowerShell cmdlet 생성</span><span class="sxs-lookup"><span data-stu-id="1052f-103">Generate Windows PowerShell cmdlets based on an OData endpoint</span></span>

<span data-ttu-id="1052f-104">**Export-ODataEndpointProxy**는 지정된 OData 엔드포인트에서 제공하는 기능에 따라 Windows PowerShell cmdlet 집합을 생성하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-104">**Export-ODataEndpointProxy** is a cmdlet that generates a set of Windows PowerShell cmdlets based on the functionality exposed by a given OData endpoint.</span></span>

<span data-ttu-id="1052f-105">다음 예제에서 이 새로운 cmdlet을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-105">The following example shows how to use this new cmdlet:</span></span>

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

<span data-ttu-id="1052f-106">이 기능의 개발에 대한 몇 가지 주요 사용 사례가 있으며, 다음을 포함하되 이에 국한되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-106">There are still parts of key use cases in development for this functionality, including, but not limited to:</span></span>
-   <span data-ttu-id="1052f-107">연결</span><span class="sxs-lookup"><span data-stu-id="1052f-107">Associations</span></span>
-   <span data-ttu-id="1052f-108">스트림 전달</span><span class="sxs-lookup"><span data-stu-id="1052f-108">Passing streams</span></span>

## <a name="generate-windows-powershell-cmdlets-based-on-an-odata-endpoint-with-odatautils"></a><span data-ttu-id="1052f-109">ODataUtils를 사용하여 OData 엔드포인트에 따라 Windows PowerShell cmdlet 생성</span><span class="sxs-lookup"><span data-stu-id="1052f-109">Generate Windows PowerShell cmdlets based on an OData endpoint with ODataUtils</span></span>

<span data-ttu-id="1052f-110">ODataUtils 모듈에서는 OData를 지원하는 REST 엔드포인트에서 Windows PowerShell cmdlet을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-110">The ODataUtils module allows generation of Windows PowerShell cmdlets from REST endpoints that support OData.</span></span> <span data-ttu-id="1052f-111">다음과 같은 증분 향상 기능이 Microsoft.PowerShell.ODataUtils Windows PowerShell 모듈에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-111">The following incremental enhancements are in the Microsoft.PowerShell.ODataUtils Windows PowerShell module.</span></span>
-   <span data-ttu-id="1052f-112">서버 쪽 엔드포인트와 클라이언트 쪽 사이에서 추가 정보 연결</span><span class="sxs-lookup"><span data-stu-id="1052f-112">Channel additional information from server-side endpoint to client side.</span></span>
-   <span data-ttu-id="1052f-113">클라이언트 쪽 페이징 지원</span><span class="sxs-lookup"><span data-stu-id="1052f-113">Client-side paging support</span></span>
-   <span data-ttu-id="1052f-114">-Select 매개 변수를 사용하여 서버 쪽 필터링</span><span class="sxs-lookup"><span data-stu-id="1052f-114">Server-side filtering by using the -Select parameter</span></span>
-   <span data-ttu-id="1052f-115">웹 요청 헤더에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="1052f-115">Support for web request headers</span></span>

<span data-ttu-id="1052f-116">Export-ODataEndPointProxy cmdlet에서 생성된 프록시 cmdlet은 정보 스트림(새로운 Windows PowerShell 5.0 기능)의 서버 쪽 OData 엔드포인트에서 추가 정보(클라이언트 쪽 프록시 생성 중 사용된 $metadata에 언급되지 않은 정보)를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-116">The proxy cmdlets generated by the Export-ODataEndPointProxy cmdlet provide additional information (not mentioned in the $metadata used during the client-side proxy generation) from the server side OData endpoint on the Information stream (a new Windows PowerShell 5.0 feature).</span></span> <span data-ttu-id="1052f-117">다음은 해당 정보를 가져오는 방법에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-117">Here is an example of how to get that information.</span></span>

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

<span data-ttu-id="1052f-118">클라이언트 쪽 페이징 지원을 사용하여 서버 쪽에서 레코드를 일괄 처리로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-118">You can get the records from the server side in batches by using client-side paging support.</span></span> <span data-ttu-id="1052f-119">이 방법은 네트워크를 통해 서버에서 많은 양의 데이터를 가져와야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-119">This is useful when you must get a large amount of data from the server over the network.</span></span>

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

<span data-ttu-id="1052f-120">생성된 프록시 cmdlet은 클라이언트에 필요한 레코드 속성만 받는 필터로 사용할 수 있는 –Select 매개 변수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-120">The generated proxy cmdlets support the –Select parameter which you can use as a filter to receive only the record properties that the client needs.</span></span> <span data-ttu-id="1052f-121">이렇게 하면 필터링이 서버 쪽에서 수행되므로 네트워크를 통해 전송되는 데이터의 양이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-121">This reduces the amount of data that is transferred over the network, because the filtering occurs on the server side.</span></span>

```powershell
# In the below example only the Name property of the
# Product record is retrieved from the server side.
Get-Product -Top 2 -AllowUnsecureConnection -AllowAdditionalData -Select Name
```

<span data-ttu-id="1052f-122">Export-ODataEndpointProxy cmdlet과 이 cmdlet에서 생성된 프록시 cmdlet은 Headers 매개 변수(해시 테이블로 값 제공)를 지원하여 서버 쪽 OData 엔드포인트에 필요한 추가 정보를 연결하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-122">The Export-ODataEndpointProxy cmdlet, and the proxy cmdlets generated by it, now support the Headers parameter (supply values as a hash table), which you can use to channel any additional information that is expected by the server-side OData endpoint.</span></span> <span data-ttu-id="1052f-123">다음 예제에서는 인증에 구독 키가 필요한 서비스에 대해 Headers를 통해 구독 키를 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1052f-123">In the following example, you can channel a Subscription key through Headers for services that are expecting a Subscription key for authentication.</span></span>

```powershell
# As an example, in the below command 'XXXX' is the authentication used by the
# Export-ODataEndpointProxy cmdlet to interact with the server-side
# OData endpoint accessed through $endPointUri.

Export-ODataEndpointProxy -Uri $endPointUri -OutputModule $generatedProxyModuleDir -Force -AllowUnSecureConnection -Verbose -Headers @{'subscription-key'='XXXX'}
```
