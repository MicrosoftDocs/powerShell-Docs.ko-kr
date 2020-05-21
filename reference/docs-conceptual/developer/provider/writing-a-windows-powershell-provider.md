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
ms.openlocfilehash: 74e11e03e8a01568dad7c038de0b3ecebb2117e5
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83562242"
---
# <a name="writing-a-windows-powershell-provider"></a><span data-ttu-id="d0552-102">Windows PowerShell 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="d0552-102">Writing a Windows PowerShell Provider</span></span>

<span data-ttu-id="d0552-103">"Windows PowerShell 공급자 작성"은 Windows PowerShell 공급자를 디자인 하는 프로그램 관리자와 공급자 코드를 구현 하는 개발자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-103">"Writing a Windows PowerShell Provider" is for program managers who are designing Windows PowerShell providers and for developers who are implementing provider code.</span></span> <span data-ttu-id="d0552-104">Windows PowerShell 공급자의 작동 방식을 이해 하는 데 도움이 되며, 사용자가 직접 공급자를 디자인 하거나 작성 하는 데 사용할 수 있는 샘플 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-104">It will help you understand how Windows PowerShell providers work, and it provides sample code that you can use to start designing or writing your own providers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d0552-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="d0552-105">In This Section</span></span>

<span data-ttu-id="d0552-106">[Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md) 시작 예제 코드 및 매우 기본적인 공급자의 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-106">[Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md) Example code and walkthrough of a very basic provider.</span></span>

<span data-ttu-id="d0552-107">[Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md) 이 섹션에는 Windows PowerShell 공급자의 정의와 작동 방식을 설명 하는 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-107">[Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md) This section contains topics that describe what Windows PowerShell providers are and how they work.</span></span>

<span data-ttu-id="d0552-108">[항목 공급자 작성](./writing-an-item-provider.md) 항목 가져오기 및 설정을 지 원하는 메서드의 예제 코드 및 연습</span><span class="sxs-lookup"><span data-stu-id="d0552-108">[Writing an item provider](./writing-an-item-provider.md) Example code and walkthrough of methods that support getting and setting items.</span></span>

<span data-ttu-id="d0552-109">[컨테이너 공급자 작성](./writing-a-container-provider.md) 컨테이너를 지 원하는 메서드 (다른 항목을 자식으로 포함 하는 항목)의 예제 코드 및 연습</span><span class="sxs-lookup"><span data-stu-id="d0552-109">[Writing a container provider](./writing-a-container-provider.md) Example code and walkthrough of methods that support containers (items that have other items as children).</span></span>

<span data-ttu-id="d0552-110">[탐색 공급자 작성](./writing-a-navigation-provider.md) 중첩 된 컨테이너와 상대 경로를 지원 하 고 한 경로에서 다른 경로로 항목을 이동 하는 방법에 대 한 예제 코드 및 연습입니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-110">[Writing a navigation provider](./writing-a-navigation-provider.md) Example code and walkthrough of methods that support nested containers, relative paths, and moving items from one path to another.</span></span>

<span data-ttu-id="d0552-111">[공급자 샘플](./provider-samples.md) 이 섹션에서는 공급자의 샘플을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0552-111">[Provider Samples](./provider-samples.md) This section provides samples of providers.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0552-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0552-112">See Also</span></span>

[<span data-ttu-id="d0552-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d0552-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
