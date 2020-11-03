---
description: '**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 21015e1457dfcc037dd65cbf3b2f7f85c9076106
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220753"
---
# <a name="about-cimsession"></a><span data-ttu-id="5a62c-104">CimSession 정보</span><span class="sxs-lookup"><span data-stu-id="5a62c-104">About CimSession</span></span>

## <a name="short-description"></a><span data-ttu-id="5a62c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="5a62c-105">Short description</span></span>
<span data-ttu-id="5a62c-106">**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-106">Describes a **CimSession** object and the difference between CIM sessions and PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="5a62c-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-107">Long description</span></span>

<span data-ttu-id="5a62c-108">CIM (CIM(Common Information Model)) 세션은 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 연결을 나타내는 클라이언트 쪽 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-108">A Common Information Model (CIM) session is a client-side object that represents a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="5a62c-109">PowerShell 세션 (PSSessions) 대신 CIM 세션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-109">You can use CIM sessions as an alternative to PowerShell sessions (PSSessions).</span></span> <span data-ttu-id="5a62c-110">두 방법 모두 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-110">Both approaches have advantages.</span></span>

<span data-ttu-id="5a62c-111">Cmdlet을 사용 `New-CimSession` 하 여 컴퓨터 이름, 연결에 사용 되는 프로토콜, 세션 id 및 인스턴스 id와 같은 연결 정보가 포함 된 CIM 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-111">You can use the `New-CimSession` cmdlet to create a CIM session that contains information about a connection, such as computer name, the protocol used for the connection, session ID, and instance ID.</span></span>

<span data-ttu-id="5a62c-112">연결을 설정 하는 데 필요한 정보를 지정 하는 **CimSession** 개체를 만든 후에 PowerShell은 연결을 즉시 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-112">After you create a **CimSession** object that specifies information required to establish a connection, PowerShell does not establish the connection immediately.</span></span> <span data-ttu-id="5a62c-113">Cmdlet에서 CIM 세션을 사용 하는 경우 PowerShell은 지정 된 컴퓨터에 연결한 다음 cmdlet이 완료 되 면 PowerShell에서 연결을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-113">When a cmdlet uses the CIM session, PowerShell connects to the specified computer, and then, when the cmdlet finishes, PowerShell terminates the connection.</span></span>

<span data-ttu-id="5a62c-114">CIM 세션을 사용 하는 대신 **PSSession** 을 만드는 경우 PowerShell에서 연결 설정의 유효성을 검사 한 다음 연결을 설정 하 고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-114">If you create a **PSSession** instead of using a CIM session, PowerShell validates connection settings, and then establishes and maintains the connection.</span></span> <span data-ttu-id="5a62c-115">CIM 세션을 사용 하는 경우 PowerShell은 필요할 때까지 네트워크 연결을 열지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-115">If you use CIM sessions, PowerShell does not open a network connection until needed.</span></span> <span data-ttu-id="5a62c-116">PowerShell 세션에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a62c-116">For more information about PowerShell sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="when-to-use-a-cim-session"></a><span data-ttu-id="5a62c-117">CIM 세션을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="5a62c-117">When to use a CIM session</span></span>

<span data-ttu-id="5a62c-118">WMI(Windows Management Instrumentation) (WMI) 공급자 또는 CIM을 사용 하는 cmdlet만 CIM 세션을 허용 WS-Man 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-118">Only cmdlets that work with a Windows Management Instrumentation (WMI) provider or CIM over WS-Man accept CIM sessions.</span></span> <span data-ttu-id="5a62c-119">다른 cmdlet의 경우에는 pssession **을 사용 합니다**.</span><span class="sxs-lookup"><span data-stu-id="5a62c-119">For other cmdlets, use **PSSessions**.</span></span>

<span data-ttu-id="5a62c-120">CIM 세션을 사용 하는 경우 PowerShell은 로컬 클라이언트에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-120">When you use a CIM session, PowerShell runs the cmdlet on the local client.</span></span> <span data-ttu-id="5a62c-121">CIM 세션을 사용 하 여 WMI 공급자에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-121">It connects to the WMI provider using the CIM session.</span></span> <span data-ttu-id="5a62c-122">대상 컴퓨터에는 PowerShell 또는 Windows 운영 체제 버전도 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-122">The target computer does not require PowerShell, or even any version of the Windows operating system.</span></span>

<span data-ttu-id="5a62c-123">반대로, **PSSession** 을 사용 하 여 실행 되는 cmdlet은 대상 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-123">In contrast, a cmdlet run using a **PSSession** runs on the target computer.</span></span>
<span data-ttu-id="5a62c-124">대상 시스템의 PowerShell이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-124">It requires PowerShell on the target system.</span></span> <span data-ttu-id="5a62c-125">또한 cmdlet은 로컬 컴퓨터에 데이터를 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-125">Furthermore, the cmdlet sends data back to the local computer.</span></span> <span data-ttu-id="5a62c-126">PowerShell은 연결을 통해 전송 되는 데이터를 관리 하 고 Windows 원격 관리 (WinRM)로 설정 된 제한 내에 크기를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-126">PowerShell manages the data sent over the connection, and keeps the size within the limits set by Windows Remote Management (WinRM).</span></span> <span data-ttu-id="5a62c-127">CIM 세션은 WinRM 제한을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-127">CIM sessions do not impose the WinRM limits.</span></span>

## <a name="using-cdxml-cmdlets"></a><span data-ttu-id="5a62c-128">CDXML cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="5a62c-128">Using CDXML cmdlets</span></span>

<span data-ttu-id="5a62c-129">CIM 기반 CDXML (Cmdlet 정의 XML) cmdlet은 WMI 공급자를 사용 하도록 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-129">CIM-based Cmdlet Definition XML (CDXML) cmdlets can be written to use any WMI Provider.</span></span> <span data-ttu-id="5a62c-130">모든 WMI 공급자는 **CimSession** 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-130">All WMI providers use **CimSession** objects.</span></span> <span data-ttu-id="5a62c-131">CDXML에 대 한 자세한 내용은 [cdxml 정의 및 용어](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a62c-131">For more information about CDXML, see [CDXML definition and terms](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).</span></span>

<span data-ttu-id="5a62c-132">CDXML cmdlet에는 **CimSession** 개체의 배열을 사용할 수 있는 자동 **CimSession** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-132">CDXML cmdlets have an automatic **CimSession** parameter that can take an array of **CimSession** objects.</span></span> <span data-ttu-id="5a62c-133">기본적으로 PowerShell은 동시 CIM 연결 수를 15로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-133">By default, PowerShell limits number of concurrent CIM Connections to 15.</span></span> <span data-ttu-id="5a62c-134">이 제한은 **ThrottleLimit** 을 구현 하는 CDXML cmdlet에 의해 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a62c-134">This limit can be overridden by CDXML cmdlets that implement the **ThrottleLimit**.</span></span> <span data-ttu-id="5a62c-135">**ThrottleLimit** 을 이해 하려면 개별 cmdlet 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a62c-135">See the individual cmdlet documentation to understand the **ThrottleLimit**.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a62c-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a62c-136">SEE ALSO</span></span>

[<span data-ttu-id="5a62c-137">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="5a62c-137">New-CimSession</span></span>](xref:CimCmdlets.New-CimSession)

[<span data-ttu-id="5a62c-138">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="5a62c-138">about_PSSessions</span></span>](about_PSSessions.md)
