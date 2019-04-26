---
title: RunSpace09 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 136e451f-767b-42e0-bd6f-6486693abd5e
caps.latest.revision: 6
ms.openlocfilehash: e21ef8685598db9a1ae0fcd86051386af526f2a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081226"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="1411a-102">RunSpace09 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="1411a-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="1411a-103">에 설명 된 Runspace09 샘플에 대 한 소스 코드를 다음과 같습니다 [는 콘솔 응용 프로그램을 호출 하는 파이프라인 비동기적으로 만드는](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47)합니다.</span><span class="sxs-lookup"><span data-stu-id="1411a-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](http://msdn.microsoft.com/en-us/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span> <span data-ttu-id="1411a-104">이 샘플 응용 프로그램 및 runspace를 엽니다, 그리고 만듭니다 비동기적으로 호출 하는 파이프라인을 만들고 사용 하 여 스크립트를 비동기적으로 처리 하는 이벤트 파이프라인 하는 다음.</span><span class="sxs-lookup"><span data-stu-id="1411a-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="1411a-105">이 응용 프로그램에서 실행 되는 스크립트를 0.5 초 간격으로 (500 밀리초)에 1부터 10 까지의 정수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1411a-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="1411a-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="1411a-106">Code Sample</span></span>

[!code-csharp[Runspace09.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs#L11-L113 "Runspace09.cs")]

## <a name="see-also"></a><span data-ttu-id="1411a-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1411a-107">See Also</span></span>

[<span data-ttu-id="1411a-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1411a-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)