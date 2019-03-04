---
title: 모듈 및 스냅인 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860499"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="df6f9-102">모듈 및 스냅인</span><span class="sxs-lookup"><span data-stu-id="df6f9-102">Modules and Snap-ins</span></span>

<span data-ttu-id="df6f9-103">Cmdlet (Windows PowerShell 2.0에서 도입 됨) 하는 모듈이 나 스냅인을 사용 하 여 세션에 추가할 수 있습니다. Cmdlet은 호스트 응용 프로그램 또는 명령줄에서 대화형으로 프로그래밍 방식으로 실행할 수 있습니다 세션에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="df6f9-104">다음과 같은 이유로 세션에 cmdlet을 추가 하는 것에 대 한 배달 방법으로 모듈을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="df6f9-105">모듈의 cmdlet가 정의 되어 있는 어셈블리를 로드 하 여 cmdlet을 추가 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="df6f9-106">스냅인 클래스를 구현할 필요가 없습니다 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="df6f9-107">모듈을 사용 하면 변수, 함수, 스크립트, 형식 및 서식 파일 등과 같은 기타 리소스를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="df6f9-108">스냅인만 세션에 cmdlet 및 공급자를 추가 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df6f9-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="df6f9-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df6f9-109">See Also</span></span>

[<span data-ttu-id="df6f9-110">Windows PowerShell 모듈 작성</span><span class="sxs-lookup"><span data-stu-id="df6f9-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

<span data-ttu-id="df6f9-111">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="df6f9-111">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
