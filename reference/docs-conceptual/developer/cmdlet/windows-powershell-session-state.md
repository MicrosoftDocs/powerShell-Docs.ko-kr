---
title: Windows PowerShell 세션 상태 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369102"
---
# <a name="windows-powershell-session-state"></a><span data-ttu-id="75b94-102">Windows PowerShell 세션 상태</span><span class="sxs-lookup"><span data-stu-id="75b94-102">Windows PowerShell Session State</span></span>

<span data-ttu-id="75b94-103">세션 상태는 Windows PowerShell 세션 또는 모듈의 현재 구성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-103">Session state refers to the current configuration of a Windows PowerShell session or module.</span></span> <span data-ttu-id="75b94-104">Windows PowerShell 세션은 명령줄 사용자가 대화형으로 사용 하거나 호스트 응용 프로그램에서 프로그래밍 방식으로 사용 하는 작업 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-104">A Windows PowerShell session is the operational environment that is used interactively by the command-line user or programmatically by a host application.</span></span> <span data-ttu-id="75b94-105">세션에 대 한 세션 상태를 전역 세션 상태 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-105">The session state for a session is referred to as the global session state.</span></span>

<span data-ttu-id="75b94-106">개발자 관점에서 Windows PowerShell 세션은 호스트 응용 프로그램이 Windows PowerShell runspace를 열고 runspace를 닫을 때 까지의 시간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-106">From a developer perspective, a Windows PowerShell session refers to the time between when a host application opens a Windows PowerShell runspace and when it closes the runspace.</span></span> <span data-ttu-id="75b94-107">다른 방법으로는 runspace가 존재 하는 동안 호출 되는 Windows PowerShell 엔진 인스턴스의 수명 세션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-107">Looked at another way, the session is the lifetime of an instance of the Windows PowerShell engine that is invoked while the runspace exists.</span></span>

## <a name="module-session-state"></a><span data-ttu-id="75b94-108">모듈 세션 상태</span><span class="sxs-lookup"><span data-stu-id="75b94-108">Module Session State</span></span>

<span data-ttu-id="75b94-109">모듈 세션 상태는 모듈 또는 중첩 된 모듈 중 하나를 세션으로 가져올 때마다 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-109">Module session states are created whenever the module or one of its nested modules is imported into the session.</span></span> <span data-ttu-id="75b94-110">모듈에서 cmdlet, 함수 또는 스크립트와 같은 요소를 내보내는 경우 해당 요소에 대 한 참조가 세션의 전역 세션 상태에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-110">When a module exports an element such as a cmdlet, function, or script, a reference to that element is added to the global session state of the session.</span></span> <span data-ttu-id="75b94-111">그러나 요소를 실행 하면 모듈의 세션 상태 내에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-111">However, when the element is run, it is executed within the session state of the module.</span></span>

## <a name="session-state-data"></a><span data-ttu-id="75b94-112">세션 상태 데이터</span><span class="sxs-lookup"><span data-stu-id="75b94-112">Session-State Data</span></span>

<span data-ttu-id="75b94-113">세션 상태 데이터는 공개 또는 비공개 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-113">Session state data can be public or private.</span></span> <span data-ttu-id="75b94-114">공용 데이터는 세션 상태 외부에서 호출 하는 데 사용할 수 있지만, 전용 데이터는 세션 상태 내의 호출에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-114">Public data is available to calls from outside the session state while private data is available only to calls from within the session state.</span></span> <span data-ttu-id="75b94-115">예를 들어 모듈은 모듈에 의해서만 호출 되거나 내보낸 public 요소에 의해서만 내부적으로 호출 될 수 있는 전용 함수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-115">For example, a module can have a private function that can be called only by the module or only internally by a public element that has been exported.</span></span> <span data-ttu-id="75b94-116">이는 .NET Framework 형식의 private 및 public 멤버와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-116">This is similar to the private and public members of a .NET Framework type.</span></span>

<span data-ttu-id="75b94-117">세션 상태 데이터는 현재 Windows PowerShell 세션 컨텍스트 내에서 실행 엔진의 현재 인스턴스에 의해 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-117">Session-state data is stored by the current instance of the execution engine within the context of the current Windows PowerShell session.</span></span> <span data-ttu-id="75b94-118">세션 상태 데이터는 다음 항목으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-118">Session-state data consists of the following items:</span></span>

- <span data-ttu-id="75b94-119">경로 정보</span><span class="sxs-lookup"><span data-stu-id="75b94-119">Path information</span></span>

- <span data-ttu-id="75b94-120">드라이브 정보</span><span class="sxs-lookup"><span data-stu-id="75b94-120">Drive information</span></span>

- <span data-ttu-id="75b94-121">Windows PowerShell 공급자 정보</span><span class="sxs-lookup"><span data-stu-id="75b94-121">Windows PowerShell provider information</span></span>

- <span data-ttu-id="75b94-122">모듈에서 내보낸 모듈 요소 (예: cmdlet, 함수 및 스크립트)에 대 한 참조 및 가져온 모듈에 대 한 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-122">Information about the imported modules and references to the module elements (such as cmdlets, functions, and scripts) that are exported by the module.</span></span> <span data-ttu-id="75b94-123">이 정보와 이러한 참조는 전역 세션 상태 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-123">This information and these references are for the global session state only.</span></span>

- <span data-ttu-id="75b94-124">세션 상태 변수 정보</span><span class="sxs-lookup"><span data-stu-id="75b94-124">Session-state variable information</span></span>

## <a name="accessing-session-state-data-within-cmdlets"></a><span data-ttu-id="75b94-125">Cmdlet 내 세션 상태 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="75b94-125">Accessing Session-State Data Within Cmdlets</span></span>

<span data-ttu-id="75b94-126">Cmdlet은 cmdlet 클래스의 [PSCmdlet. Sessionstate \*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) 속성을 통해 간접적으로 또는 [Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스를 통해 직접 세션 상태 데이터에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-126">Cmdlets can access session-state data either indirectly through the [System.Management.Automation.PSCmdlet.Sessionstate\*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) property of the cmdlet class or directly through the [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class.</span></span> <span data-ttu-id="75b94-127">[Sessionstate](/dotnet/api/System.Management.Automation.SessionState) 클래스는 여러 유형의 세션 상태 데이터를 조사 하는 데 사용할 수 있는 속성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="75b94-127">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) class provides properties that can be used to investigate different types of session-state data.</span></span>

## <a name="see-also"></a><span data-ttu-id="75b94-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="75b94-128">See Also</span></span>

[<span data-ttu-id="75b94-129">PSCmdlet. Sessionstate</span><span class="sxs-lookup"><span data-stu-id="75b94-129">System.Management.Automation.PSCmdlet.Sessionstate</span></span>](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[<span data-ttu-id="75b94-130">. Sessionstate? Displayproperty = Fullname</span><span class="sxs-lookup"><span data-stu-id="75b94-130">System.Management.Automation.Sessionstate?Displayproperty=Fullname</span></span>](/dotnet/api/System.Management.Automation.SessionState)

[<span data-ttu-id="75b94-131">Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="75b94-131">Windows PowerShell Cmdlets</span></span>](./cmdlet-overview.md)

<span data-ttu-id="75b94-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="75b94-132">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>

[<span data-ttu-id="75b94-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="75b94-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
