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
ms.openlocfilehash: d7fa39485eea833483682c91c96417a76e5d770f
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977542"
---
# <a name="runspace09-code-sample"></a><span data-ttu-id="e54ad-102">RunSpace09 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="e54ad-102">RunSpace09 Code Sample</span></span>

<span data-ttu-id="e54ad-103">다음은 [비동기적으로 파이프라인을 호출 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47)에서 설명한 Runspace09 샘플에 대 한 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e54ad-103">Here is the source code for the Runspace09 sample described in [Creating a Console Application That Invokes a Pipeline Asynchronously](https://msdn.microsoft.com/198c1c94-2a06-457e-93ce-c0d910618e47).</span></span>
<span data-ttu-id="e54ad-104">이 샘플 응용 프로그램은 runspace를 만들어 열고, 파이프라인을 만들고 비동기식으로 호출한 다음 파이프라인 이벤트를 사용 하 여 비동기적으로 스크립트를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="e54ad-104">This sample application creates and opens a runspace, creates and asynchronously invokes a pipeline, and then uses pipeline events to process the script asynchronously.</span></span> <span data-ttu-id="e54ad-105">이 응용 프로그램에서 실행 하는 스크립트는 0.5 초 간격 (500 밀리초)의 정수 1 ~ 10을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e54ad-105">The script that is run by this application creates the integers 1 through 10 in 0.5-second intervals (500 ms).</span></span>

## <a name="code-sample"></a><span data-ttu-id="e54ad-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="e54ad-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace09/Runspace09.cs" range="11-113":::

## <a name="see-also"></a><span data-ttu-id="e54ad-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e54ad-107">See Also</span></span>

[<span data-ttu-id="e54ad-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e54ad-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
