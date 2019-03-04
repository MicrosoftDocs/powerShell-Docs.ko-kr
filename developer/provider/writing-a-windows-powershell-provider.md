---
title: Windows PowerShell 공급자 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a54ce657-e0e0-4b3e-b9dc-aed39876f933
caps.latest.revision: 11
ms.openlocfilehash: 58252956184703fdcdb3aa9b1db617c6e91294c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860059"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="b6dd2-102">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="b6dd2-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="b6dd2-103">"Windows PowerShell 공급자 쓰기"는 Windows PowerShell 공급자를 디자인 하는 프로그램 관리자 공급자 코드를 구현 하는 개발자를 위한 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="b6dd2-104">Windows PowerShell 공급자의 작동 방식을 이해 하는 데 도움이 됩니다 하 고 디자인 하거나 고유한 공급자 작성을 시작 하는 데 사용할 수 있는 샘플 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b6dd2-105">이 섹션의 내용</span><span class="sxs-lookup"><span data-stu-id="b6dd2-105">In This Section</span></span>

<span data-ttu-id="b6dd2-106">[Windows PowerShell 공급자 퀵 스타트](./windows-powershell-provider-quickstart.md) 매우 기본적인 공급자의 연습 및 예제 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="b6dd2-107">[Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md) 이 섹션에서는 Windows PowerShell 공급자 이란 무엇 이며 작동 방식을 설명 하는 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="b6dd2-108">[항목 공급자 작성](./writing-an-item-provider.md) 예제 코드 및 가져오기 및 설정 항목을 지 원하는 방법을 연습 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="b6dd2-109">[컨테이너 공급자 작성](./writing-a-container-provider.md) 예제 코드 및 컨테이너 (자식으로 다른 항목에 있는 항목)를 지 원하는 메서드를 연습 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="b6dd2-110">[탐색 공급자 작성](./writing-a-navigation-provider.md) 예제 코드와 설명은 메서드를 지 원하는 중첩 된 컨테이너, 상대 경로 및 다른 하나의 경로에서 항목을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="b6dd2-111">[공급자 샘플](./provider-samples.md) 이 섹션에서는 공급자의 샘플을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6dd2-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6dd2-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b6dd2-112">See Also</span></span>

[<span data-ttu-id="b6dd2-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b6dd2-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)