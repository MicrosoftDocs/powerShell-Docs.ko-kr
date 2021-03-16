---
description: '**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.'
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_cimsession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CimSession
ms.openlocfilehash: 556c3db21ea5e410b28f5546cdd8a433e0bc3e50
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605252"
---
# <a name="about-cimsession"></a><span data-ttu-id="a7d27-103">CimSession 정보</span><span class="sxs-lookup"><span data-stu-id="a7d27-103">About CimSession</span></span>

## <a name="short-description"></a><span data-ttu-id="a7d27-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a7d27-104">Short description</span></span>
<span data-ttu-id="a7d27-105">**CimSession** 개체와 CIM 세션과 PowerShell 세션 간의 차이점에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-105">Describes a **CimSession** object and the difference between CIM sessions and PowerShell sessions.</span></span>

## <a name="long-description"></a><span data-ttu-id="a7d27-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-106">Long description</span></span>

<span data-ttu-id="a7d27-107">CIM (CIM(Common Information Model)) 세션은 로컬 컴퓨터 또는 원격 컴퓨터에 대 한 연결을 나타내는 클라이언트 쪽 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-107">A Common Information Model (CIM) session is a client-side object that represents a connection to a local computer or a remote computer.</span></span> <span data-ttu-id="a7d27-108">PowerShell 세션 (PSSessions) 대신 CIM 세션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-108">You can use CIM sessions as an alternative to PowerShell sessions (PSSessions).</span></span> <span data-ttu-id="a7d27-109">두 방법 모두 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-109">Both approaches have advantages.</span></span>

<span data-ttu-id="a7d27-110">Cmdlet을 사용 `New-CimSession` 하 여 컴퓨터 이름, 연결에 사용 되는 프로토콜, 세션 id 및 인스턴스 id와 같은 연결 정보가 포함 된 CIM 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-110">You can use the `New-CimSession` cmdlet to create a CIM session that contains information about a connection, such as computer name, the protocol used for the connection, session ID, and instance ID.</span></span>

<span data-ttu-id="a7d27-111">연결을 설정 하는 데 필요한 정보를 지정 하는 **CimSession** 개체를 만든 후에 PowerShell은 연결을 즉시 설정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-111">After you create a **CimSession** object that specifies information required to establish a connection, PowerShell does not establish the connection immediately.</span></span> <span data-ttu-id="a7d27-112">Cmdlet에서 CIM 세션을 사용 하는 경우 PowerShell은 지정 된 컴퓨터에 연결한 다음 cmdlet이 완료 되 면 PowerShell에서 연결을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-112">When a cmdlet uses the CIM session, PowerShell connects to the specified computer, and then, when the cmdlet finishes, PowerShell terminates the connection.</span></span>

<span data-ttu-id="a7d27-113">CIM 세션을 사용 하는 대신 **PSSession** 을 만드는 경우 PowerShell에서 연결 설정의 유효성을 검사 한 다음 연결을 설정 하 고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-113">If you create a **PSSession** instead of using a CIM session, PowerShell validates connection settings, and then establishes and maintains the connection.</span></span> <span data-ttu-id="a7d27-114">CIM 세션을 사용 하는 경우 PowerShell은 필요할 때까지 네트워크 연결을 열지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-114">If you use CIM sessions, PowerShell does not open a network connection until needed.</span></span> <span data-ttu-id="a7d27-115">PowerShell 세션에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d27-115">For more information about PowerShell sessions, see [about_PSSessions](about_PSSessions.md).</span></span>

## <a name="when-to-use-a-cim-session"></a><span data-ttu-id="a7d27-116">CIM 세션을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="a7d27-116">When to use a CIM session</span></span>

<span data-ttu-id="a7d27-117">WMI(Windows Management Instrumentation) (WMI) 공급자 또는 CIM을 사용 하는 cmdlet만 CIM 세션을 허용 WS-Man 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-117">Only cmdlets that work with a Windows Management Instrumentation (WMI) provider or CIM over WS-Man accept CIM sessions.</span></span> <span data-ttu-id="a7d27-118">다른 cmdlet의 경우에는 pssession **을 사용 합니다**.</span><span class="sxs-lookup"><span data-stu-id="a7d27-118">For other cmdlets, use **PSSessions**.</span></span>

<span data-ttu-id="a7d27-119">CIM 세션을 사용 하는 경우 PowerShell은 로컬 클라이언트에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-119">When you use a CIM session, PowerShell runs the cmdlet on the local client.</span></span> <span data-ttu-id="a7d27-120">CIM 세션을 사용 하 여 WMI 공급자에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-120">It connects to the WMI provider using the CIM session.</span></span> <span data-ttu-id="a7d27-121">대상 컴퓨터에는 PowerShell 또는 Windows 운영 체제 버전도 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-121">The target computer does not require PowerShell, or even any version of the Windows operating system.</span></span>

<span data-ttu-id="a7d27-122">반대로, **PSSession** 을 사용 하 여 실행 되는 cmdlet은 대상 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-122">In contrast, a cmdlet run using a **PSSession** runs on the target computer.</span></span>
<span data-ttu-id="a7d27-123">대상 시스템의 PowerShell이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-123">It requires PowerShell on the target system.</span></span> <span data-ttu-id="a7d27-124">또한 cmdlet은 로컬 컴퓨터에 데이터를 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-124">Furthermore, the cmdlet sends data back to the local computer.</span></span> <span data-ttu-id="a7d27-125">PowerShell은 연결을 통해 전송 되는 데이터를 관리 하 고 Windows 원격 관리 (WinRM)로 설정 된 제한 내에 크기를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-125">PowerShell manages the data sent over the connection, and keeps the size within the limits set by Windows Remote Management (WinRM).</span></span> <span data-ttu-id="a7d27-126">CIM 세션은 WinRM 제한을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-126">CIM sessions do not impose the WinRM limits.</span></span>

## <a name="using-cdxml-cmdlets"></a><span data-ttu-id="a7d27-127">CDXML cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="a7d27-127">Using CDXML cmdlets</span></span>

<span data-ttu-id="a7d27-128">CIM 기반 CDXML (Cmdlet 정의 XML) cmdlet은 WMI 공급자를 사용 하도록 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-128">CIM-based Cmdlet Definition XML (CDXML) cmdlets can be written to use any WMI Provider.</span></span> <span data-ttu-id="a7d27-129">모든 WMI 공급자는 **CimSession** 개체를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-129">All WMI providers use **CimSession** objects.</span></span> <span data-ttu-id="a7d27-130">CDXML에 대 한 자세한 내용은 [cdxml 정의 및 용어](/previous-versions/windows/desktop/wmi_v2/cdxml-overview)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d27-130">For more information about CDXML, see [CDXML definition and terms](/previous-versions/windows/desktop/wmi_v2/cdxml-overview).</span></span>

<span data-ttu-id="a7d27-131">CDXML cmdlet에는 **CimSession** 개체의 배열을 사용할 수 있는 자동 **CimSession** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-131">CDXML cmdlets have an automatic **CimSession** parameter that can take an array of **CimSession** objects.</span></span> <span data-ttu-id="a7d27-132">기본적으로 PowerShell은 동시 CIM 연결 수를 15로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-132">By default, PowerShell limits number of concurrent CIM Connections to 15.</span></span> <span data-ttu-id="a7d27-133">이 제한은 **ThrottleLimit** 을 구현 하는 CDXML cmdlet에 의해 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7d27-133">This limit can be overridden by CDXML cmdlets that implement the **ThrottleLimit**.</span></span> <span data-ttu-id="a7d27-134">**ThrottleLimit** 을 이해 하려면 개별 cmdlet 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7d27-134">See the individual cmdlet documentation to understand the **ThrottleLimit**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7d27-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7d27-135">SEE ALSO</span></span>

[<span data-ttu-id="a7d27-136">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="a7d27-136">New-CimSession</span></span>](xref:CimCmdlets.New-CimSession)

[<span data-ttu-id="a7d27-137">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="a7d27-137">about_PSSessions</span></span>](about_PSSessions.md)
