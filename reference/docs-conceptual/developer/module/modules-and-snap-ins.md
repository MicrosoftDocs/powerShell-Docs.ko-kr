---
title: 모듈 및 스냅인 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 07cdc55fd6d1462130f1a81deb30056623a525e6
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787311"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="5d5b3-102">모듈 및 스냅인</span><span class="sxs-lookup"><span data-stu-id="5d5b3-102">Modules and Snap-ins</span></span>

<span data-ttu-id="5d5b3-103">Cmdlet은 모듈 (Windows PowerShell 2.0에서 도입) 또는 스냅인을 사용 하 여 세션에 추가할 수 있습니다. Cmdlet이 세션에 추가 되 면 호스트 응용 프로그램에서 프로그래밍 방식으로 실행 하거나 명령줄에서 대화형으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="5d5b3-104">다음 이유 때문에 cmdlet을 세션에 추가 하기 위한 배달 방법으로 모듈을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="5d5b3-105">모듈을 사용 하 여 cmdlet이 정의 된 어셈블리를 로드 하 여 cmdlet을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="5d5b3-106">스냅인 클래스를 구현할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="5d5b3-107">모듈을 사용 하 여 변수, 함수, 스크립트, 형식 및 서식 파일 등의 다른 리소스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="5d5b3-108">스냅인은 cmdlet 및 공급자를 세션에 추가 하는 데만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="5d5b3-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d5b3-109">See Also</span></span>

[<span data-ttu-id="5d5b3-110">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="5d5b3-110">Writing a Windows PowerShell Module</span></span>](writing-a-windows-powershell-module.md)

[<span data-ttu-id="5d5b3-111">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="5d5b3-111">Writing a Windows PowerShell Cmdlet</span></span>](../cmdlet/cmdlet-overview.md)
