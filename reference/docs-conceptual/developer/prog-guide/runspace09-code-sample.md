---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace09 코드 샘플
description: RunSpace09 코드 샘플
ms.openlocfilehash: 52ebfa5dcfd6c12d2ded78a41a6090caa5087149
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654202"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="9c2bc-103">RunSpace09 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="9c2bc-103">RunSpace09 Code Sample</span></span>

<span data-ttu-id="9c2bc-104">다음은 [비동기적으로 파이프라인을 호출 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)에서 설명한 Runspace09 샘플에 대 한 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-104">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="9c2bc-105">이 샘플 응용 프로그램은 runspace를 만들어 열고, 파이프라인을 만들고 비동기식으로 호출한 다음 파이프라인 이벤트를 사용 하 여 비동기적으로 스크립트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-105">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="9c2bc-106">이 응용 프로그램에서 실행 하는 스크립트는 0.5 초 간격 (500 밀리초)의 정수 1 ~ 10을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9c2bc-106">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="9c2bc-107">코드 예제</span><span class="sxs-lookup"><span data-stu-id="9c2bc-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="9c2bc-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c2bc-108">See Also</span></span>

[<span data-ttu-id="9c2bc-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9c2bc-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
