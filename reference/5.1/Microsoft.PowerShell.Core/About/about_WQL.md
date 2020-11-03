---
description: Windows PowerShell에서 WMI 개체를 가져오는 데 사용할 수 있는 WQL(WMI Query Language)에 대해 설명합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223186"
---
# <a name="about-wql"></a><span data-ttu-id="b2031-104">WQL 정보</span><span class="sxs-lookup"><span data-stu-id="b2031-104">About WQL</span></span>

## <a name="short-description"></a><span data-ttu-id="b2031-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="b2031-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="b2031-106">Windows PowerShell에서 WMI 개체를 가져오는 데 사용할 수 있는 WQL(WMI Query Language)에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-106">Describes WMI Query Language (WQL), which can be used to get WMI objects in Windows PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="b2031-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="b2031-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="b2031-108">WQL은 WMI에서 정보를 가져오는 데 사용 되는 언어인 WMI (WMI(Windows Management Instrumentation)) 쿼리 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-108">WQL is the Windows Management Instrumentation (WMI) query language, which is the language used to get information from WMI.</span></span>

<span data-ttu-id="b2031-109">WQL을 사용 하 여 Windows PowerShell에서 WMI 쿼리를 수행할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-109">You are not required to use WQL to perform a WMI query in Windows PowerShell.</span></span>
<span data-ttu-id="b2031-110">대신 Get-WmiObject 또는 Get-CimInstance cmdlet의 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-110">Instead, you can use the parameters of the Get-WmiObject or Get-CimInstance cmdlets.</span></span> <span data-ttu-id="b2031-111">WQL 쿼리는 표준 Get-WmiObject 명령 보다 다소 빠르지만, 명령이 수백 대의 시스템에서 실행 되는 경우 성능이 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-111">WQL queries are somewhat faster than standard Get-WmiObject commands and the improved performance is evident when the commands run on hundreds of systems.</span></span> <span data-ttu-id="b2031-112">그러나 성공적인 WQL 쿼리를 작성 하는 데 소요 되는 시간이 성능 향상 보다 더 중요 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-112">However, be sure that the time you spend to write a successful WQL query doesn't outweigh the performance improvement.</span></span>

<span data-ttu-id="b2031-113">WQL을 사용 하는 데 필요한 기본 WQL 문은 Select, Where 및 From입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-113">The basic WQL statements you need to use WQL are Select, Where, and From.</span></span>

## <a name="when-to-use-wql"></a><span data-ttu-id="b2031-114">WQL을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="b2031-114">WHEN TO USE WQL</span></span>

<span data-ttu-id="b2031-115">WMI를 사용할 때 특히 WQL을 사용 하는 경우 Windows PowerShell도 사용 하 고 있다는 것을 잊지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b2031-115">When working with WMI, and especially with WQL, do not forget that you are also using Windows PowerShell.</span></span> <span data-ttu-id="b2031-116">WQL 쿼리가 정상적으로 작동 하지 않는 경우가 종종 있지만 표준 Windows PowerShell 명령을 사용 하 여 WQL 쿼리를 디버그 하는 것이 더 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-116">Often, if a WQL query does not work as expected, it's easier to use a standard Windows PowerShell command than to debug the WQL query.</span></span>

<span data-ttu-id="b2031-117">대역폭이 제한 된 원격 시스템에서 다량의 데이터를 반환 하는 경우가 아니면 약간 느리게 수행 되는 동일한 작업을 수행 하는 완벽 하 게 허용 되는 Windows cmdlet이 있는 경우 복잡 하 고 복잡 WQL 쿼리를 수행 하는 데 시간이 많이 소요 되는 경우가 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-117">Unless you are returning massive amounts of data from across bandwidth-constrained remote systems, it is rarely productive to spend hours trying to perfect a complicated and convoluted WQL query when there is a perfectly acceptable Windows cmdlet that does the same thing, if a bit more slowly.</span></span>

## <a name="using-the-select-statement"></a><span data-ttu-id="b2031-118">SELECT 문 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-118">USING THE SELECT STATEMENT</span></span>

<span data-ttu-id="b2031-119">일반적인 WMI 쿼리는 WMI 클래스의 모든 속성 또는 특정 속성을 가져오는 Select 문으로 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-119">A typical WMI query begins with a Select statement that gets all properties or particular properties of a WMI class.</span></span> <span data-ttu-id="b2031-120">WMI 클래스의 모든 속성을 선택 하려면 별표 ()를 사용 \* 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-120">To select all properties of a WMI class, use an asterisk (\*).</span></span> <span data-ttu-id="b2031-121">From 키워드는 WMI 클래스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-121">The From keyword specifies the WMI class.</span></span>

<span data-ttu-id="b2031-122">Select 문의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-122">A Select statement has the following format:</span></span>

```
Select <property> from <WMI-class>
```

<span data-ttu-id="b2031-123">예를 들어 다음 Select 문은 Win32_Bios WMI 클래스의 인스턴스에서 모든 속성 (\*)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-123">For example, the following Select statement selects all properties (\*) from the instances of the Win32_Bios WMI class.</span></span>

```
Select * from Win32_Bios
```

<span data-ttu-id="b2031-124">WMI 클래스의 특정 속성을 선택 하려면 Select 및 From 키워드 사이에 속성 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-124">To select a particular property of a WMI class, place the property name between the Select and From keywords.</span></span>

<span data-ttu-id="b2031-125">다음 쿼리는 Win32_Bios WMI 클래스의 BIOS 이름만 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-125">The following query selects only the name of the BIOS from the Win32_Bios WMI class.</span></span> <span data-ttu-id="b2031-126">명령은 $queryName 변수에 쿼리를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-126">The command saves the query in the $queryName variable.</span></span>

```
Select Name from Win32_Bios
```

<span data-ttu-id="b2031-127">둘 이상의 속성을 선택 하려면 쉼표를 사용 하 여 속성 이름을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-127">To select more than one property, use commas to separate the property names.</span></span>
<span data-ttu-id="b2031-128">다음 WMI 쿼리는 Win32_Bios WMI 클래스의 이름 및 버전을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-128">The following WMI query selects the name and the version of the Win32_Bios WMI class.</span></span> <span data-ttu-id="b2031-129">명령은 $queryNameVersion 변수에 쿼리를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-129">The command saves the query in the $queryNameVersion variable.</span></span>

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a><span data-ttu-id="b2031-130">WQL 쿼리 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-130">USING THE WQL QUERY</span></span>

<span data-ttu-id="b2031-131">Windows PowerShell 명령에서 WQL 쿼리를 사용 하는 방법에는 세 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-131">There are three ways to use WQL query in Windows PowerShell command.</span></span>

- <span data-ttu-id="b2031-132">Get-WmiObject cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-132">Use the Get-WmiObject cmdlet</span></span>
- <span data-ttu-id="b2031-133">Get-CimInstance cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-133">Use the Get-CimInstance cmdlet</span></span>
- <span data-ttu-id="b2031-134">[Wmisearcher] 형식 액셀러레이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-134">Use the [wmisearcher] type accelerator.</span></span>

## <a name="using-the-get-wmiobject-cmdlet"></a><span data-ttu-id="b2031-135">GET-WMIOBJECT CMDLET 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-135">USING THE GET-WMIOBJECT CMDLET</span></span>

<span data-ttu-id="b2031-136">WQL 쿼리를 사용 하는 가장 기본적인 방법은 다음 예제와 같이 따옴표 (문자열)로 묶고 쿼리 문자열을 Get-WmiObject cmdlet의 쿼리 매개 변수 값으로 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-136">The most basic way to use the WQL query is to enclose it in quotation marks (as a string) and then use the query string as the value of the Query parameter of the Get-WmiObject cmdlet, as shown in the following example.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="b2031-137">다음 명령에 표시 된 것 처럼 WQL 문을 변수에 저장 한 다음이 변수를 쿼리 매개 변수 값으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-137">You can also save the WQL statement in a variable and then use the variable as the value of the Query parameter, as shown in the following command.</span></span>

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

<span data-ttu-id="b2031-138">모든 WQL 문에 두 형식 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-138">You can use either format with any WQL statement.</span></span> <span data-ttu-id="b2031-139">다음 명령은 $queryName 변수의 쿼리를 사용 하 여 시스템 BIOS의 이름 및 버전 속성만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-139">The following command uses the query in the $queryName variable to get only the name and version properties of the system BIOS.</span></span>

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

<span data-ttu-id="b2031-140">Get-WmiObject cmdlet의 매개 변수를 사용 하 여 동일한 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-140">Remember that you can use the parameters of the Get-WmiObject cmdlet to get the same result.</span></span> <span data-ttu-id="b2031-141">예를 들어 다음 명령은 Win32_Bios WMI 클래스 인스턴스의 이름 및 버전 속성 값도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-141">For example, the following command also gets the values of the Name and Version properties of instances of the Win32_Bios WMI class.</span></span>

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a><span data-ttu-id="b2031-142">CIMINSTANCE 개체로 CMDLET 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-142">USING THE GET-CIMINSTANCE CMDLET</span></span>

<span data-ttu-id="b2031-143">Windows PowerShell 3.0 부터는 Get-CimInstance cmdlet을 사용 하 여 WQL 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-143">Beginning in Windows PowerShell 3.0, you can use the Get-CimInstance cmdlet to run WQL queries.</span></span>

<span data-ttu-id="b2031-144">Get-CimInstance은 WMI 클래스를 포함 하 여 CIM 규격 클래스의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-144">Get-CimInstance gets instances of CIM-compliant classes, including WMI classes.</span></span> <span data-ttu-id="b2031-145">Windows PowerShell 3.0을 소개 하는 CIM cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-145">The CIM cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="b2031-146">CIM cmdlet은 WSMan (WS-Management) 표준과 CIM(Common Information Model) (CIM) 표준을 준수 하 여 cmdlet이 동일한 기술을 사용 하 여 다른 운영 체제를 실행 하는 컴퓨터 및 컴퓨터를 관리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-146">The CIM cmdlets comply with WS-Management (WSMan) standards and with the Common Information Model (CIM) standard, which enables the cmdlets to use the same techniques to manage Windows computers and computers that are running other operating systems.</span></span>

<span data-ttu-id="b2031-147">다음 명령은 Get-CimInstance cmdlet을 사용 하 여 WQL 쿼리를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-147">The following command uses the Get-CimInstance cmdlet to run a WQL query.</span></span>

<span data-ttu-id="b2031-148">Get-WmiObject와 함께 사용할 수 있는 모든 WQL 쿼리를 Ciminstance 개체로와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-148">Any WQL query that can be used with Get-WmiObject can also be used with Get-CimInstance.</span></span>

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="b2031-149">Get-CimInstance는 Get-WmiObject 반환 하는 ManagementObject 대신 Ciminstance 개체로 개체를 반환 하지만 개체는 매우 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-149">Get-CimInstance returns a CimInstance object, instead of the ManagementObject that Get-WmiObject returns, but the objects are quite similar.</span></span>

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a><span data-ttu-id="b2031-150">[Wmisearcher] 형식 액셀러레이터 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-150">USING THE [wmisearcher] TYPE ACCELERATOR</span></span>

<span data-ttu-id="b2031-151">[Wmisearcher] 형식 액셀러레이터는 WQL 문 문자열에서 ManagementObjectSearcher 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-151">The [wmisearcher] type accelerator creates a ManagementObjectSearcher object from a WQL statement string.</span></span> <span data-ttu-id="b2031-152">ManagementObjectSearcher 개체에는 많은 속성 및 메서드가 있지만 가장 기본적인 메서드는 지정 된 WMI 쿼리를 호출 하 고 결과 개체를 반환 하는 Get 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-152">The ManagementObjectSearcher object has many properties and methods, but the most basic method is the Get method, which invokes the specified WMI query and returns the resulting objects.</span></span>

<span data-ttu-id="b2031-153">[Wmisearcher]를 사용 하 여 ManagementObjectSearcher .NET Framework 클래스에 쉽게 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-153">By using the [wmisearcher], you gain easy access to the ManagementObjectSearcher .NET Framework class.</span></span> <span data-ttu-id="b2031-154">이렇게 하면 WMI를 쿼리하고 쿼리를 수행 하는 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-154">This lets you query WMI and to configure the way the query is conducted.</span></span>

<span data-ttu-id="b2031-155">[Wmisearcher] 유형 가속기를 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-155">To use the [wmisearcher] type accelerator:</span></span>

1. <span data-ttu-id="b2031-156">WQL 문자열을 ManagementObjectSearcher 개체로 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-156">Cast the  WQL string into a ManagementObjectSearcher object.</span></span>
2. <span data-ttu-id="b2031-157">ManagementObjectSearcher 개체의 Get 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-157">Call the Get method of the ManagementObjectSearcher object.</span></span>

<span data-ttu-id="b2031-158">예를 들어 다음 명령은 "모두 선택" 쿼리를 캐스팅 하 고 결과를 $bios 변수에 저장 한 다음 $bios 변수에 ManagementObjectSearcher 개체의 Get 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-158">For example, the following command casts the "select all" query, saves the result in the $bios variable, and then calls the Get method of the ManagementObjectSearcher object in the $bios variable.</span></span>

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="b2031-159">참고: 선택한 개체 속성만 기본적으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-159">NOTE: Only selected object properties are displayed by default.</span></span> <span data-ttu-id="b2031-160">이러한 속성은 Types.ps1xml 파일에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-160">These properties are defined in the Types.ps1xml file.</span></span>

<span data-ttu-id="b2031-161">[Wmisearcher] 형식 액셀러레이터를 사용 하 여 쿼리 또는 변수를 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-161">You can use the [wmisearcher] type accelerator to cast the query or the variable.</span></span> <span data-ttu-id="b2031-162">다음 예제에서는 [wmisearcher] 형식 액셀러레이터를 사용 하 여 변수를 캐스팅 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-162">In the following example, the [wmisearcher] type accelerator is used to cast the variable.</span></span> <span data-ttu-id="b2031-163">결과는 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-163">The result is the same.</span></span>

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

<span data-ttu-id="b2031-164">[Wmisearcher] 형식 액셀러레이터를 사용 하는 경우 다음 명령에 표시 된 것 처럼 쿼리 문자열을 ManagementObjectSearcher 개체로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-164">When you use the [wmisearcher] type accelerator, it changes the query string into a ManagementObjectSearcher object, as shown in the following commands.</span></span>

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

<span data-ttu-id="b2031-165">이 명령 형식은 모든 쿼리에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-165">This command format works on any query.</span></span> <span data-ttu-id="b2031-166">다음 명령은 Win32_Bios WMI 클래스의 Name 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-166">The following command gets the value of the Name property of the Win32_Bios WMI class.</span></span>

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

<span data-ttu-id="b2031-167">이 작업을 단일 명령으로 수행할 수 있지만이 명령은 해석 하기가 약간 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-167">You can perform this operation in a single command, although the command is a bit more difficult to interpret.</span></span>

<span data-ttu-id="b2031-168">이 형식에서는 [wmisearcher] 형식 액셀러레이터를 사용 하 여 WQL 쿼리 문자열을 ManagementObjectSearcher로 캐스팅 한 다음 개체에 대해 Get 메서드를 호출 합니다. 모두 단일 명령으로 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-168">In this format, you use the [wmisearcher] type accelerator to cast the WQL query string to a ManagementObjectSearcher, and then call the Get method on the object -- all in a single command.</span></span> <span data-ttu-id="b2031-169">메서드를 호출 하기 전에 Windows PowerShell에서 문자열을 캐스트 하도록 캐스트 된 문자열을 묶는 괄호 ()입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-169">The parentheses () that enclose the casted string direct Windows PowerShell to cast the string before calling the method.</span></span>

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a><span data-ttu-id="b2031-170">기본 WQL WHERE 문 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-170">USING THE BASIC WQL WHERE STATEMENT</span></span>

<span data-ttu-id="b2031-171">Where 문은 Select 문이 반환 하는 데이터에 대 한 조건을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-171">A Where statement establishes conditions for the data that a Select statement returns.</span></span>

<span data-ttu-id="b2031-172">Where 문의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-172">The Where statement has the following format:</span></span>

```
where <property> <operator> <value>
```

<span data-ttu-id="b2031-173">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b2031-173">For example:</span></span>

```
where Name = 'Notepad.exe'
```

<span data-ttu-id="b2031-174">Where 문은 다음 예제와 같이 Select 문에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-174">The Where statement is used with the Select statement, as shown in the following example.</span></span>

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

<span data-ttu-id="b2031-175">Where 문을 사용 하는 경우 속성 이름 및 값은 정확 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-175">When using the Where statement, the property name and value must be accurate.</span></span>

<span data-ttu-id="b2031-176">예를 들어 다음 명령은 로컬 컴퓨터에서 메모장 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-176">For example, the following command gets the Notepad processes on the local computer.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

<span data-ttu-id="b2031-177">그러나 프로세스 이름에 ".exe" 파일 이름 확장명이 포함 되어 있으므로 다음 명령은 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-177">However, the following command fails, because the process name includes the ".exe" file name extension.</span></span>

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a><span data-ttu-id="b2031-178">WHERE 문 비교 연산자</span><span class="sxs-lookup"><span data-stu-id="b2031-178">WHERE STATEMENT COMPARISON OPERATORS</span></span>

<span data-ttu-id="b2031-179">WQL Where 문에는 다음과 같은 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-179">The following operators are valid in a WQL Where statement.</span></span>

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

<span data-ttu-id="b2031-180">다른 연산자가 있지만 비교를 수행 하는 데 사용 되는 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-180">There are other operators, but these are the ones used for making comparisons.</span></span>

<span data-ttu-id="b2031-181">예를 들어 다음 쿼리는 Win32_Process 클래스에서 프로세스 우선 순위가 11 이상인 프로세스의 이름 및 우선 순위 속성을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-181">For example, the following query selects the Name and Priority properties from processes in the Win32_Process class where the process priority is greater than or equal to 11.</span></span> <span data-ttu-id="b2031-182">Get-WmiObject cmdlet은 쿼리를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-182">The Get-WmiObject cmdlet runs the query.</span></span>

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a><span data-ttu-id="b2031-183">FILTER 매개 변수에 WQL 연산자 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-183">USING THE WQL OPERATORS IN THE FILTER PARAMETER</span></span>

<span data-ttu-id="b2031-184">WQL 연산자는 Get-WmiObject 또는 Get-CimInstance cmdlet의 Filter 매개 변수 값 뿐만 아니라 이러한 cmdlet의 쿼리 매개 변수 값에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-184">The WQL operators can also be used in the value of the Filter parameter of the Get-WmiObject or Get-CimInstance cmdlets, as well as in the value of the Query parameters of these cmdlets.</span></span>

<span data-ttu-id="b2031-185">예를 들어 다음 명령은 ProcessID 값이 1004 보다 큰 마지막 5 개 프로세스의 이름 및 ProcessID 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-185">For example, the following command gets the Name and ProcessID properties of the last five processes that have ProcessID values greater than 1004.</span></span> <span data-ttu-id="b2031-186">이 명령은 Filter 매개 변수를 사용 하 여 ProcessID 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-186">The command uses the Filter parameter to specify the ProcessID condition.</span></span>

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a><span data-ttu-id="b2031-187">LIKE 연산자 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-187">USING THE LIKE OPERATOR</span></span>

<span data-ttu-id="b2031-188">Like 연산자를 사용 하면 와일드 카드 문자를 사용 하 여 WQL 쿼리 결과를 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-188">The Like operator lets you use wildcard characters to filter the results of a WQL query.</span></span>

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

<span data-ttu-id="b2031-189">와일드 카드 문자 또는 범위 연산자 없이 Like 연산자를 사용 하는 경우 같음 연산자 (=) 처럼 동작 하며 패턴과 정확히 일치 하는 경우에만 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-189">When the Like operator is used without any wildcard characters or range operators, it behaves like the equality operator (=) and returns objects only when they are an exact match for the pattern.</span></span>

<span data-ttu-id="b2031-190">Range 연산을 백분율 와일드 카드 문자와 결합 하 여 간단 하면서도 강력한 필터를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-190">You can combine the range operation with the percent wildcard character to create simple, yet powerful filters.</span></span>

### <a name="like-operator-examples"></a><span data-ttu-id="b2031-191">LIKE 연산자 예제</span><span class="sxs-lookup"><span data-stu-id="b2031-191">LIKE OPERATOR EXAMPLES</span></span>

#### <a name="example-1-range"></a><span data-ttu-id="b2031-192">예 1: [ \<range> ]</span><span class="sxs-lookup"><span data-stu-id="b2031-192">EXAMPLE 1: [\<range>]</span></span>

<span data-ttu-id="b2031-193">다음 명령을 사용 하 여 메모장을 시작한 다음 이름이 "H"와 "N" (대/소문자 구분 안 함)로 시작 하는 Win32_Process 클래스의 인스턴스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-193">The following commands start Notepad and then search for an instance of the Win32_Process class that has a name that starts with a letter between "H" and "N" (case-insensitive).</span></span>

<span data-ttu-id="b2031-194">쿼리가 Notepad.exe를 통해 Hotpad.exe의 모든 프로세스를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-194">The query should return any process from Hotpad.exe through Notepad.exe.</span></span>

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a><span data-ttu-id="b2031-195">예 2: [ \<range> ] 및%</span><span class="sxs-lookup"><span data-stu-id="b2031-195">EXAMPLE 2: [\<range>] and %</span></span>

<span data-ttu-id="b2031-196">다음 명령은 이름과 P (대/소문자 구분 안 함) 사이에 있는 문자로 시작 하는 모든 프로세스와 임의의 조합에서 0 개 이상의 문자로 시작 하는 모든 프로세스를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-196">The following commands select all process that have a name that begins with a letter between A and P (case-insensitive) followed by zero or more letters in any combination.</span></span>

<span data-ttu-id="b2031-197">Get-WmiObject cmdlet은 쿼리를 실행 하 고, Select-Object cmdlet은 Name 및 ProcessID 속성을 가져오며, Sort-Object cmdlet은 이름을 기준으로 결과를 사전순으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-197">The Get-WmiObject cmdlet runs the query, the Select-Object cmdlet gets the Name and ProcessID properties, and the Sort-Object cmdlet sorts the results in alphabetical order by name.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a><span data-ttu-id="b2031-198">예 3: 범위에 없음 (^)</span><span class="sxs-lookup"><span data-stu-id="b2031-198">EXAMPLE 3: Not in Range (^)</span></span>

<span data-ttu-id="b2031-199">다음 명령은 이름이 A, S, W, P, R, C, U, N 중 하나로 시작 하지 않는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-199">The following command gets processes whose names do not begin with any of the following letters: A, S, W, P, R, C, U, N</span></span>

<span data-ttu-id="b2031-200">0 개 이상의 문자를 팔 로우 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-200">and followed zero or more letters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a><span data-ttu-id="b2031-201">예 4: 모든 문자 또는 없음 (%)</span><span class="sxs-lookup"><span data-stu-id="b2031-201">EXAMPLE 4: Any characters -- or none (%)</span></span>

<span data-ttu-id="b2031-202">다음 명령은 이름이 "calc"로 시작 하는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-202">The following commands get processes that have names that begin with "calc".</span></span>
<span data-ttu-id="b2031-203">WQL 의% 기호는 \* 정규식의 별표 () 기호와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-203">The % symbol in WQL is equivalent to the asterisk (\*) symbol in regular expressions.</span></span>

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a><span data-ttu-id="b2031-204">예 5: 한 문자 (_)</span><span class="sxs-lookup"><span data-stu-id="b2031-204">EXAMPLE 5: One character (_)</span></span>

<span data-ttu-id="b2031-205">다음 명령은 "c_lc.exe" 패턴이 있는 이름을 가진 프로세스를 가져옵니다. 여기서 밑줄 문자는 한 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-205">The following commands get processes that have names that have the following pattern, "c_lc.exe" where the underscore character represents any one character.</span></span> <span data-ttu-id="b2031-206">이 패턴은 calc.exe czlc.exe 또는 c9lc.exe를 통해 모든 이름을 찾지만 "c"와 "l"이 둘 이상의 문자로 구분 된 이름과는 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-206">This pattern matches any name from calc.exe through czlc.exe, or c9lc.exe, but does not match names in which the "c" and "l" are separated by more than one character.</span></span>

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a><span data-ttu-id="b2031-207">예 6: 정확히 일치</span><span class="sxs-lookup"><span data-stu-id="b2031-207">EXAMPLE 6: Exact match</span></span>

<span data-ttu-id="b2031-208">다음 명령은 WLIDSVC.exe 이라는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-208">The following commands get processes named WLIDSVC.exe.</span></span> <span data-ttu-id="b2031-209">쿼리에서 Like 키워드를 사용 하는 경우에도 값에 와일드 카드 문자가 포함 되지 않으므로 정확히 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-209">Even though the query uses the Like keyword, it requires an exact match, because the value does not include any wildcard characters.</span></span>

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a><span data-ttu-id="b2031-210">OR 연산자 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-210">USING THE OR OPERATOR</span></span>

<span data-ttu-id="b2031-211">여러 독립 조건을 지정 하려면 또는 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-211">To specify multiple independent conditions, use the Or keyword.</span></span> <span data-ttu-id="b2031-212">Where 절에 또는 키워드가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-212">The Or keyword appears in the Where clause.</span></span> <span data-ttu-id="b2031-213">두 개 이상의 조건에 대해 포괄적 OR 연산을 수행 하 고 조건을 충족 하는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-213">It performs an inclusive OR operation on two (or more) conditions and returns items that meet any of the conditions.</span></span>

<span data-ttu-id="b2031-214">Or 연산자의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-214">The Or operator has the following format:</span></span>

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

<span data-ttu-id="b2031-215">예를 들어 다음 명령은 Win32_Process WMI 클래스의 모든 인스턴스를 가져오지만 프로세스 이름이 winword.exe 또는 excel.exe 경우에만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-215">For example, the following commands get all instances of the Win32_Process WMI class but returns them only if the process name is winword.exe or excel.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

<span data-ttu-id="b2031-216">또는 문은 세 개 이상의 조건에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-216">The Or statement can be used with more than two conditions.</span></span> <span data-ttu-id="b2031-217">다음 쿼리에서 또는 문은 Winword.exe, Excel.exe 또는 Powershell.exe를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-217">In the following query, the Or statement gets Winword.exe, Excel.exe, or Powershell.exe.</span></span>

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a><span data-ttu-id="b2031-218">AND 연산자 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-218">USING THE AND OPERATOR</span></span>

<span data-ttu-id="b2031-219">여러 관련 조건을 지정 하려면 및 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-219">To specify multiple related conditions, use the And keyword.</span></span> <span data-ttu-id="b2031-220">및 키워드가 Where 절에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-220">The And keyword appears in the Where clause.</span></span> <span data-ttu-id="b2031-221">모든 조건을 충족 하는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-221">It returns items that meet all of the conditions.</span></span>

<span data-ttu-id="b2031-222">And 연산자의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-222">The And operator has the following format:</span></span>

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

<span data-ttu-id="b2031-223">예를 들어 다음 명령은 이름이 "Winword.exe"이 고 프로세스 ID가 6512 인 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-223">For example, the following commands get processes that have a name of "Winword.exe" and the process ID of 6512.</span></span>

<span data-ttu-id="b2031-224">명령은 Get-CimInstance cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-224">Note that the commands use the Get-CimInstance cmdlet.</span></span>

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

<span data-ttu-id="b2031-225">Like 연산자를 비롯 한 모든 연산자는 Or 및 And 연산자와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-225">All operators, including the Like operators are valid with the Or and And operators.</span></span> <span data-ttu-id="b2031-226">그리고 먼저 처리할 절을 Windows PowerShell에 지시 하는 괄호를 사용 하 여 단일 쿼리에서 Or 및 And 연산자를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-226">And, you can combine the Or and And operators in a single query with parentheses that tell Windows PowerShell which clauses to process first.</span></span>

<span data-ttu-id="b2031-227">이 명령은 Windows PowerShell 연속 문자 (')를 사용 하 여 명령을 두 줄로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-227">This command uses the Windows PowerShell continuation character (\`) divide the command into two lines.</span></span>

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a><span data-ttu-id="b2031-228">NULL 값 검색</span><span class="sxs-lookup"><span data-stu-id="b2031-228">SEARCHING FOR NULL VALUES</span></span>

<span data-ttu-id="b2031-229">예기치 않은 결과가 발생할 수 있으므로 WMI에서 null 값을 검색 하는 것은 어려운 일입니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-229">Searching for null values in WMI is challenging, because it can lead to unpredictable results.</span></span> <span data-ttu-id="b2031-230">Null이 0이 아닌 경우 또는 빈 문자열과 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-230">Null is not zero and it is not equivalent or to an empty string.</span></span> <span data-ttu-id="b2031-231">일부 WMI 클래스 속성은 초기화 되 고 다른 속성은 초기화 되지 않으므로 null에 대 한 검색이 모든 속성에 대해 작동 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-231">Some WMI class properties are initialized and others are not, so a search for null might not work for all properties.</span></span>

<span data-ttu-id="b2031-232">Null 값을 검색 하려면 "null" 값을 포함 하는 Is 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-232">To search for null values, use the Is operator with a value of "null".</span></span>

<span data-ttu-id="b2031-233">예를 들어 다음 명령은 IntallDate 속성에 대해 null 값이 있는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-233">For example, the following commands get processes that have a null value for the IntallDate property.</span></span> <span data-ttu-id="b2031-234">명령은 많은 프로세스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-234">The commands return many processes.</span></span>

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="b2031-235">반면, 다음 명령은 Description 속성에 대해 null 값이 있는 사용자 계정을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-235">In contrast, the following command, gets user accounts that have a null value for the Description property.</span></span> <span data-ttu-id="b2031-236">대부분의 사용자 계정에 Description 속성에 대 한 값이 없는 경우에도이 명령은 사용자 계정을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-236">This command does not return any user accounts, even though most user accounts do not have any value for the Description property.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

<span data-ttu-id="b2031-237">Description 속성에 대 한 값이 없는 사용자 계정을 찾으려면 같음 연산자를 사용 하 여 빈 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-237">To find the user accounts that have no value for the Description property, use the equality operator to get an empty string.</span></span> <span data-ttu-id="b2031-238">빈 문자열을 나타내려면 두 개의 연속 작은따옴표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-238">To represent the empty string, use two consecutive single quotation marks.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a><span data-ttu-id="b2031-239">TRUE 또는 FALSE 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-239">USING TRUE OR FALSE</span></span>

<span data-ttu-id="b2031-240">WMI 개체의 속성에서 부울 값을 가져오려면 True 및 False를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-240">To get Boolean values in the properties of WMI objects, use True and False.</span></span>
<span data-ttu-id="b2031-241">대소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-241">They are not case sensitive.</span></span>

<span data-ttu-id="b2031-242">다음 WQL 쿼리는 도메인에 가입 된 컴퓨터에서 로컬 사용자 계정만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-242">The following WQL query returns only local user accounts from a domain joined computer.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

<span data-ttu-id="b2031-243">도메인 계정을 찾으려면 다음 예에 표시 된 것 처럼 False 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-243">To find domain accounts, use a value of False, as shown in the following example.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a><span data-ttu-id="b2031-244">이스케이프 문자 사용</span><span class="sxs-lookup"><span data-stu-id="b2031-244">USING THE ESCAPE CHARACTER</span></span>

<span data-ttu-id="b2031-245">WQL은 이스케이프 문자로 백슬래시를 사용 \) 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-245">WQL uses the backslash (\) as its escape character.</span></span> <span data-ttu-id="b2031-246">이는 억음 문자 (')를 사용 하는 Windows PowerShell과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-246">This is different from Windows PowerShell, which uses the backtick character (\`).</span></span>

<span data-ttu-id="b2031-247">따옴표와 따옴표에 사용 되는 문자는 잘못 해석 되지 않도록 이스케이프 처리 해야 하는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-247">Quotation marks, and the characters used for quotation marks, often need to be escaped so that they are not misinterpreted.</span></span>

<span data-ttu-id="b2031-248">이름이 작은따옴표로 묶여 있는 사용자를 찾으려면 다음 명령에 표시 된 것 처럼 백슬래시를 사용 하 여 작은따옴표를 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-248">To find a user whose name includes a single quotation mark, use a backslash to escape the single quotation mark, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

<span data-ttu-id="b2031-249">경우에 따라 백슬래시도 이스케이프 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-249">In some case, the backslash also needs to be escaped.</span></span> <span data-ttu-id="b2031-250">예를 들어 다음 명령은 Caption 값의 백슬래시로 인해 잘못 된 쿼리 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-250">For example, the following commands generate an Invalid Query error due to the backslash in the Caption value.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

<span data-ttu-id="b2031-251">백슬래시를 이스케이프 하려면 다음 명령에 표시 된 것 처럼 두 번째 백슬래시 문자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2031-251">To escape the backslash, use a second backslash character, as shown in the following command.</span></span>

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a><span data-ttu-id="b2031-252">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b2031-252">SEE ALSO</span></span>

[<span data-ttu-id="b2031-253">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="b2031-253">about_Special_Characters</span></span>](about_Special_Characters.md)

[<span data-ttu-id="b2031-254">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="b2031-254">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)

[<span data-ttu-id="b2031-255">about_WMI</span><span class="sxs-lookup"><span data-stu-id="b2031-255">about_WMI</span></span>](about_WMI.md)

[<span data-ttu-id="b2031-256">about_WMI_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b2031-256">about_WMI_Cmdlets</span></span>](about_WMI_Cmdlets.md)
