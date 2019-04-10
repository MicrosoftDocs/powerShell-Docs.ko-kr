---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 네트워킹 작업 수행
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 250ae6e5f6431ce659b3600188d7e30e501c3247
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293132"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="2c01a-103">네트워킹 작업 수행</span><span class="sxs-lookup"><span data-stu-id="2c01a-103">Performing Networking Tasks</span></span>

<span data-ttu-id="2c01a-104">TCP/IP는 가장 일반적으로 사용되는 네트워크 프로토콜이므로 대부분의 간단한 네트워크 프로토콜 관리 작업은 TCP/IP와 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="2c01a-105">이 섹션에서는 Windows PowerShell 및 WMI를 사용하여 이러한 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="2c01a-106">컴퓨터의 IP 주소 표시</span><span class="sxs-lookup"><span data-stu-id="2c01a-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="2c01a-107">로컬 컴퓨터에서 사용 중인 모든 IP 주소를 가져오려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="2c01a-108">이 명령의 출력 결과는 다음과 같이 값이 중괄호로 묶여 있기 때문에 일반적인 속성 목록과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="2c01a-109">중괄호로 표시되는 이유를 이해하려면 Get-Member cmdlet을 사용하여 **IPAddress** 속성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="2c01a-110">각 네트워크 어댑터의 IP주소 속성은 실제 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="2c01a-111">정의에 있는 중괄호는 **IPAddress**가 **System.String** 값이 아니라 **System.String** 값의 배열임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="2c01a-112">IP 구성 데이터 표시</span><span class="sxs-lookup"><span data-stu-id="2c01a-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="2c01a-113">각 네트워크 어댑터의 자세한 IP 구성 데이터를 표시하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="2c01a-114">네트워크 어댑터 구성 개체의 기본 표시에는 매우 간단한 정보만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="2c01a-115">자세히 검사하고 문제를 해결하려면 Select-Object 또는 형식 지정 cmdlet(예: Format-List)을 사용하여 표시할 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="2c01a-116">최신 TCP/IP 네트워크를 사용하는 경우와 같이 IPX 또는 WINS 속성이 필요 없는 경우 다음과 같이 Select-Object의 ExcludeProperty 매개 변수를 사용하여 이름이 "WINS" 또는 "IPX:"로 시작하는 속성을 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="2c01a-117">이 명령은 DHCP, DNS, 라우팅 및 기타 보조 IP 구성 속성에 대한 세부 정보를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="2c01a-118">컴퓨터에 대해 ping 수행</span><span class="sxs-lookup"><span data-stu-id="2c01a-118">Pinging Computers</span></span>

<span data-ttu-id="2c01a-119">**Win32_PingStatus**를 사용하여 컴퓨터에 대해 간단한 ping을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="2c01a-120">다음 명령은 ping을 수행하지만 긴 출력 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="2c01a-121">이 출력을 보기 쉽게 요약하려면 다음 명령에 의해 생성되는 Address, ResponseTime 및 StatusCode 속성을 표시하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="2c01a-122">Format-Table의 Autosize 매개 변수는 테이블 열 크기를 조정하여 Windows PowerShell에 올바로 표시되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="2c01a-123">StatusCode 0은 성공적인 ping을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="2c01a-124">배열을 사용하여 하나의 명령으로 여러 컴퓨터를 ping할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="2c01a-125">여러 개의 주소가 있기 때문에 다음과 같이 **ForEach-Object**를 사용하여 각 주소를 따로 ping합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="2c01a-126">같은 명령 형식을 사용하여 네트워크 번호 192.168.1.0을 사용하는 개인 네트워크, 표준 클래스 C 서브넷 마스크(255.255.255.0) 등 서브넷에 있는 모든 컴퓨터를 ping할 수 있습니다. 192.168.1.1에서 192.168.1.254 범위에 있는 주소만 유효한 로컬 주소입니다. 0은 항상 네트워크 번호로 예약되어 있고 255는 서브넷 브로드캐스트 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="2c01a-127">Windows PowerShell에서 1에서 254까지의 번호 배열을 나타내려면 **1..254** 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="2c01a-128">배열을 생성하고 ping 문의 부분 주소에 값을 추가하여 서브넷 ping을 완료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="2c01a-129">주소 범위를 생성하는 방법을 다른 작업에 적용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="2c01a-130">예를 들어 다음과 같이 전체 주소 집합을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="2c01a-131">네트워크 어댑터 속성 검색</span><span class="sxs-lookup"><span data-stu-id="2c01a-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="2c01a-132">이 사용 설명서 앞부분에서는 **Win32_NetworkAdapterConfiguration**을 사용하여 일반적인 구성 속성을 검색할 수 있다고 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="2c01a-133">TCP/IP 정보에는 그대로 적용되지 않을 수 있지만 MAC 주소와 어댑터 유형 같은 네트워크 어댑터 정보는 컴퓨터의 상태를 파악하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="2c01a-134">이 정보의 요약을 보려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="2c01a-135">네트워크 어댑터의 DNS 도메인 할당</span><span class="sxs-lookup"><span data-stu-id="2c01a-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="2c01a-136">자동 이름 확인에 사용할 DNS 도메인을 할당하려면 **Win32_NetworkAdapterConfiguration SetDNSDomain** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="2c01a-137">각 네트워크 어댑터 구성에 대해 개별적으로 DNS 도메인을 할당하기 때문에 다음과 같이 **ForEach-Object** 문을 사용하여 각 어댑터에 도메인을 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="2c01a-138">TCP/IP만 사용하는 네트워크에 있는 컴퓨터의 몇 가지 네트워크 어댑터 구성이 실제 TCP/IP 어댑터가 아니므로 필터링 문 “IPEnabled=$true”가 필요합니다. 즉, 이 구성은 모든 어댑터에 대해 RAS, PPTP, QoS 및 기타 서비스를 지원하는 일반 소프트웨어 요소이기 때문에 자체 주소를 가지고 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="2c01a-139">**Get-WmiObject** 필터를 사용하는 대신 **Where-Object** cmdlet을 사용하여 명령을 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="2c01a-140">DHCP 구성 작업 수행</span><span class="sxs-lookup"><span data-stu-id="2c01a-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="2c01a-141">DHCP 세부 정보는 DNS 구성과 같이 네트워크 어댑터 집합을 사용하여 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="2c01a-142">WMI에서는 여러 가지 고유한 작업을 수행할 수 있는데, 이 설명서에서는 몇 가지 일반적인 작업을 단계별로 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="2c01a-143">DHCP 사용 가능 어댑터 확인</span><span class="sxs-lookup"><span data-stu-id="2c01a-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="2c01a-144">컴퓨터에서 DHCP 사용 가능 어댑터를 찾으려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="2c01a-145">IP 구성에 문제가 있는 어댑터를 제외하려면 IP 사용 어댑터만 검색하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="2c01a-146">DHCP 속성 검색</span><span class="sxs-lookup"><span data-stu-id="2c01a-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="2c01a-147">어댑터의 DHCP 관련 속성은 일반적으로 "DHCP"로 시작되므로 Format-Table의 Property 매개 변수를 사용하여 해당 속성만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="2c01a-148">각 어댑터에서 DHCP 사용</span><span class="sxs-lookup"><span data-stu-id="2c01a-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="2c01a-149">모든 어댑터에서 DHCP를 사용하도록 설정하려면 다음 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="2c01a-150">**Filter** 문 “IPEnabled=$true and DHCPEnabled=$false”를 사용하여 이미 설정된 곳에서는 DHCP를 설정하지 않도록 할 수 있습니다. 그러나 이 단계를 생략해도 오류가 발생하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="2c01a-151">특정 어댑터에서 DHCP 임대 해제 및 갱신</span><span class="sxs-lookup"><span data-stu-id="2c01a-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="2c01a-152">**Win32_NetworkAdapterConfiguration** 클래스에는 **ReleaseDHCPLease** 및 **RenewDHCPLease** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="2c01a-153">두 메서드의 사용 방법은 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-153">Both are used in the same way.</span></span> <span data-ttu-id="2c01a-154">일반적으로 이러한 메서드는 특정 서브넷에 있는 어댑터 주소를 임대 해제 또는 갱신만 하면 되는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="2c01a-155">서브넷에서 어댑터를 필터링하는 가장 쉬운 방법은 이 서브넷의 게이트웨이를 사용하는 어댑터 구성만 선택하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="2c01a-156">예를 들어 다음 명령은 192.168.1.254에서 DHCP를 임대하는 로컬 컴퓨터에 있는 어댑터의 모든 DHCP를 임대 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="2c01a-157">DHCP 임대를 갱신하려면 다음과 같이 **ReleaseDHCPLease** 메서드 대신 **RenewDHCPLease** 메서드를 호출하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="2c01a-158">원격 컴퓨터에서 이 메서드를 사용하면 임대 해제 또는 갱신된 어댑터를 통해 원격 시스템에 연결하는 경우 이 시스템에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="2c01a-159">모든 어댑터에서 DHCP 임대 해제 및 갱신</span><span class="sxs-lookup"><span data-stu-id="2c01a-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="2c01a-160">**Win32_NetworkAdapterConfiguration** 메서드, **ReleaseDHCPLeaseAll** 및 **RenewDHCPLeaseAll**을 사용하여 모든 어댑터에서 DHCP 주소를 한꺼번에 임대 해제 또는 갱신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="2c01a-161">그러나 특정 어댑터 대신 WMI 클래스에서 한꺼번에 임대 해제하고 갱신하므로 이 명령을 특정 어댑터가 아니라 WMI 클래스에 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="2c01a-162">WMI 클래스를 모두 표시하고 원하는 클래스만 이름으로 선택하여 클래스 인스턴스 대신 WMI 클래스에 대한 참조를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="2c01a-163">예를 들어 다음 명령은 Win32_NetworkAdapterConfiguration 클래스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="2c01a-164">전체 명령을 클래스로 처리한 다음 이 클래스에서 **ReleaseDHCPAdapterLease** 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="2c01a-165">다음 명령에서는 **Get-WmiObject** 및 **Where-Object** 파이프라인 요소가 괄호로 묶여 있기 때문에 Windows PowerShell에서 먼저 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="2c01a-166">다음과 같이 동일한 명령 형식을 사용하여 **RenewDHCPLeaseAll** 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="2c01a-167">네트워크 공유 만들기</span><span class="sxs-lookup"><span data-stu-id="2c01a-167">Creating a Network Share</span></span>

<span data-ttu-id="2c01a-168">네트워크 공유를 만들려면 다음과 같이 **Win32_Share Create** 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="2c01a-169">Windows PowerShell에서 **net share**를 사용하여 공유를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="2c01a-170">네트워크 공유 제거</span><span class="sxs-lookup"><span data-stu-id="2c01a-170">Removing a Network Share</span></span>

<span data-ttu-id="2c01a-171">**Win32_Share**와 함께 네트워크 공유를 제거할 수 있지만 **Win32_Share** 클래스 대신 제거할 특정 공유를 검색해야 하므로 제거 프로세스는 공유 만들기와 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="2c01a-172">다음 문은 "TempShare" 공유를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="2c01a-173">다음과 같이 **Net share**를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="2c01a-174">액세스 가능한 Windows 네트워크 드라이브 연결</span><span class="sxs-lookup"><span data-stu-id="2c01a-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="2c01a-175">**New-PSDrive** cmdlet은 Windows PowerShell 드라이브를 만들지만 이런 방식으로 만든 드라이브는 Windows PowerShell에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="2c01a-176">새 네트워크 드라이브를 만들려면 **WScript.Network** COM 개체를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="2c01a-177">다음 명령은 \\\\FPS01\\users 공유를 로컬 드라이브 B:에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="2c01a-178">다음과 같이 **net use** 명령을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="2c01a-179">**WScript.Network** 또는 net use를 사용하여 매핑된 드라이브는 Windows PowerShell에서 즉시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c01a-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>