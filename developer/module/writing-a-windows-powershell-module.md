---
title: Windows PowerShell 모듈 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082059"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="94866-102">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="94866-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="94866-103">이 문서는 관리자, 스크립트 개발자 및 패키지 및 해당 Windows PowerShell cmdlet을 배포 해야 하는 cmdlet 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="94866-104">Windows PowerShell 모듈을 사용 하 여 패키지 수 있으며 컴파일된 언어를 사용 하지 않고 Windows PowerShell 솔루션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="94866-105">Windows PowerShell 모듈을 사용 하면 파티션 수, 구성 및 다시 사용할 수 있는 자체 포함된 단위를 Windows PowerShell 코드를 추상화 합니다.</span><span class="sxs-lookup"><span data-stu-id="94866-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="94866-106">이러한 재사용 가능한 단위를 사용 하 여 다른 사용자와 직접 모듈을 쉽게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="94866-107">스크립트 개발자 인 경우 사용자 지정 스크립트 기반 응용 프로그램을 만들 뿐만 아니라 타사 모듈을 다시 패키지도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="94866-108">모듈, Perl, Python 등 다른 스크립팅 언어로 모듈을 유사한 다시 패키지 하 고 여러 구성 요소를 추상화할 수의 추가 혜택을 사용 하 여 다시 사용할 수 있는, 재배포 가능 구성 요소를 사용 하는 프로덕션이 준비 된 스크립팅 솔루션을 사용 하도록 설정 사용자 지정 솔루션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="94866-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="94866-109">가장 기본적인에서 Windows PowerShell 모듈. psm1 파일에 저장 된 모든 유효한 Windows PowerShell 스크립트 코드에서 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="94866-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="94866-110">PowerShell 모듈로 이진 cmdlet 어셈블리도 자동으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="94866-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="94866-111">그러나 전체 솔루션을 함께 번들로 묶는 모듈 (또는 보다 구체적으로, 모듈 매니페스트)도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="94866-112">다음 시나리오는 Windows PowerShell 모듈에 대 한 일반적인 용도 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="94866-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="94866-113">라이브러리</span><span class="sxs-lookup"><span data-stu-id="94866-113">Libraries</span></span>

<span data-ttu-id="94866-114">패키지 및 일반적인 작업을 수행 하는 함수의 응집성 라이브러리 배포 모듈을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="94866-115">일반적으로 이러한 함수 중 이름에 사용 되는 일반적인 작업을 반영 하는 하나 이상의 명사를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="94866-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="94866-116">이러한 함수는 public 및 private 멤버를가지고 수.NET Framework 클래스와 유사 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="94866-117">예를 들어, 라이브러리 파일 전송에 대 한 일련의 함수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="94866-118">이 경우 일반적인 작업을 반영 명사 "file." 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="94866-119">구성</span><span class="sxs-lookup"><span data-stu-id="94866-119">Configuration</span></span>

<span data-ttu-id="94866-120">모듈은 특정 cmdlet, 공급자, 함수 및 변수를 추가 하 여 사용자 환경에 맞게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="94866-121">컴파일된 코드 개발 및 배포</span><span class="sxs-lookup"><span data-stu-id="94866-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="94866-122">Cmdlet 및 공급자 개발자는 테스트 하 고 스냅인을 만들 필요 없이 컴파일된 코드를 배포 하려면 모듈을 사용할 수 있습니다. 모듈로 (이진 모듈) 컴파일된 코드를 포함 하는 어셈블리를 만들고 스냅인을 등록할 필요 없이 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94866-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="94866-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94866-123">See Also</span></span>

[<span data-ttu-id="94866-124">Windows PowerShell 모듈 이해</span><span class="sxs-lookup"><span data-stu-id="94866-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="94866-125">PowerShell 스크립트 모듈을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="94866-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="94866-126">PowerShell 이진 모듈을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="94866-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="94866-127">PowerShell 모듈 매니페스트를 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="94866-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="94866-128">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="94866-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="94866-129">PowerShell 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="94866-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="94866-130">PowerShell 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="94866-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
