---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 모듈 작성
description: Windows PowerShell 모듈 작성
ms.openlocfilehash: 307241f0fb4d12c1a5cbd651a0ae4d5303098b27
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659427"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="efa77-103">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="efa77-103">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="efa77-104">이 문서는 Windows PowerShell cmdlet을 패키지 하 고 배포 해야 하는 관리자, 스크립트 개발자 및 cmdlet 개발자를 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-104">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="efa77-105">Windows PowerShell 모듈을 사용 하 여 컴파일된 언어를 사용 하지 않고 Windows PowerShell 솔루션을 패키지 하 고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-105">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="efa77-106">Windows PowerShell 모듈을 사용 하 여 Windows PowerShell 코드를 독립적이 고 재사용 가능한 단위로 분할, 구성 및 추상화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-106">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="efa77-107">이러한 재사용 가능한 단위를 사용 하면 모듈을 다른 사용자와 직접 쉽게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-107">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="efa77-108">스크립트 개발자 인 경우 타사 모듈을 다시 패키지 하 여 사용자 지정 스크립트 기반 응용 프로그램을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-108">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="efa77-109">Perl 및 Python과 같은 다른 스크립팅 언어의 모듈과 유사한 모듈은 재사용 가능한 재배포 가능 구성 요소를 사용 하는 프로덕션 지원 스크립팅 솔루션을 지원 하며, 여러 구성 요소를 다시 패키징 하 고 추상화 하 여 사용자 지정 솔루션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-109">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="efa77-110">가장 기본적인 Windows PowerShell은 .psm1 파일에 저장 된 모든 유효한 Windows PowerShell 스크립트 코드를 모듈로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-110">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="efa77-111">또한 PowerShell은 모든 이진 cmdlet 어셈블리를 모듈로 자동으로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-111">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="efa77-112">그러나 모듈 (또는 구체적으로 모듈 매니페스트)을 사용 하 여 전체 솔루션을 함께 묶을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-112">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="efa77-113">다음 시나리오는 Windows PowerShell 모듈의 일반적인 용도를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-113">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="efa77-114">라이브러리</span><span class="sxs-lookup"><span data-stu-id="efa77-114">Libraries</span></span>

<span data-ttu-id="efa77-115">모듈을 사용 하 여 일반적인 작업을 수행 하는 함수에 대 한 긴밀 한 라이브러리를 패키지 하 고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-115">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="efa77-116">일반적으로 이러한 함수의 이름은 일반적으로 사용 되는 작업을 반영 하는 하나 이상의 명사를 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-116">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="efa77-117">이러한 함수는 public 및 private 멤버를 가질 수 있다는 점에서 .NET Framework 클래스와 유사할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-117">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="efa77-118">예를 들어 라이브러리에 파일 전송에 대 한 함수 집합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-118">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="efa77-119">이 경우 공통 작업을 반영 하는 명사는 "file" 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-119">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="efa77-120">Configuration</span><span class="sxs-lookup"><span data-stu-id="efa77-120">Configuration</span></span>

<span data-ttu-id="efa77-121">모듈은 특정 cmdlet, 공급자, 함수 및 변수를 추가 하 여 환경을 사용자 지정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-121">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="efa77-122">컴파일된 코드 개발 및 배포</span><span class="sxs-lookup"><span data-stu-id="efa77-122">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="efa77-123">Cmdlet 및 공급자 개발자는 스냅인을 만들 필요 없이 모듈을 사용 하 여 컴파일된 코드를 테스트 하 고 배포할 수 있습니다. 스냅인을 만들고 등록할 필요 없이 컴파일된 코드를 포함 하는 어셈블리를 모듈 (이진 모듈)로 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efa77-123">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="efa77-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="efa77-124">See Also</span></span>

[<span data-ttu-id="efa77-125">Windows PowerShell 모듈 이해</span><span class="sxs-lookup"><span data-stu-id="efa77-125">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="efa77-126">PowerShell 스크립트 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="efa77-126">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="efa77-127">PowerShell 이진 모듈을 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="efa77-127">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="efa77-128">PowerShell 모듈 매니페스트를 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="efa77-128">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="efa77-129">PSModulePath 설치 경로 수정</span><span class="sxs-lookup"><span data-stu-id="efa77-129">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="efa77-130">PowerShell 모듈 가져오기</span><span class="sxs-lookup"><span data-stu-id="efa77-130">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="efa77-131">PowerShell 모듈 설치</span><span class="sxs-lookup"><span data-stu-id="efa77-131">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
