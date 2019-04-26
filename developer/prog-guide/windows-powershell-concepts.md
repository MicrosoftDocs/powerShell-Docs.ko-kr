---
title: Windows PowerShell 개념 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081039"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="ef201-102">Windows PowerShell 개념</span><span class="sxs-lookup"><span data-stu-id="ef201-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="ef201-103">이 섹션에서는 개발자의 관점에서 Windows PowerShell을 이해 하는 데 도움이 되는 개념 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="ef201-104">항목 이름</span><span class="sxs-lookup"><span data-stu-id="ef201-104">Topic Name</span></span>|<span data-ttu-id="ef201-105">설명</span><span class="sxs-lookup"><span data-stu-id="ef201-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="ef201-106">Windows PowerShell 공급자</span><span class="sxs-lookup"><span data-stu-id="ef201-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="ef201-107">데이터에 액세스 하는 데 사용 되는 Windows PowerShell 공급자에 대 한 토론을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="ef201-108">Windows PowerShell 스냅인</span><span class="sxs-lookup"><span data-stu-id="ef201-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="ef201-109">Cmdlet 및 공급자를 등록 하기 위한 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="ef201-110">(참고 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md).)</span><span class="sxs-lookup"><span data-stu-id="ef201-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="ef201-111">Windows PowerShell 런타임</span><span class="sxs-lookup"><span data-stu-id="ef201-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="ef201-112">Windows PowerShell runspace의 현재 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="ef201-113">Windows PowerShell Runspace</span><span class="sxs-lookup"><span data-stu-id="ef201-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="ef201-114">명령이 처리 되는 운영 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="ef201-115">Windows PowerShell 네임 스페이스</span><span class="sxs-lookup"><span data-stu-id="ef201-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="ef201-116">Windows PowerShell API 네임 스페이스의 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="ef201-117">Windows PowerShell 도움말</span><span class="sxs-lookup"><span data-stu-id="ef201-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="ef201-118">Cmdlet 도움말을 작성 하는 방법에 대 한 자세한 내용은 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="ef201-119">요청 확인</span><span class="sxs-lookup"><span data-stu-id="ef201-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="ef201-120">Cmdlet 및 공급자에서에서 요청 방법을 피드백 작업 전에 사용자에 대해 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="ef201-121">Windows PowerShell 개체 개념</span><span class="sxs-lookup"><span data-stu-id="ef201-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="ef201-122">Windows PowerShell 개체를 처리 하는 방법을 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="ef201-123">Windows PowerShell 형식 시스템 (ETS) 확장</span><span class="sxs-lookup"><span data-stu-id="ef201-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="ef201-124">프로그래밍 방식으로 개체를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef201-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="ef201-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef201-125">See Also</span></span>

[<span data-ttu-id="ef201-126">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="ef201-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)