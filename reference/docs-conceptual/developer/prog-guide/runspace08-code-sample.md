---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace08 코드 샘플
description: RunSpace08 코드 샘플
ms.openlocfilehash: f8d08e5b6bbd98d0901abe5b05c8b9ee682b8e04
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654234"
---
# <a name="runspace08-code-sample"></a><span data-ttu-id="600a9-103">RunSpace08 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="600a9-103">RunSpace08 Code Sample</span></span>

<span data-ttu-id="600a9-104">다음은 [명령에 매개 변수를 추가 하는 콘솔 응용 프로그램 만들기](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba)에서 설명한 Runspace08 샘플의 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="600a9-104">Here is the source code for the Runspace08 sample described in [Creating a Console Application That Adds Parameters to a Command](https://msdn.microsoft.com/848b2b46-60f1-4a86-b448-cfc7c0cccfba).</span></span>
<span data-ttu-id="600a9-105">이 샘플 응용 프로그램은 runspace를 만들고, 파이프라인을 만들고, 파이프라인에 두 개의 명령을 추가 하 고, 두 번째 명령에 두 개의 매개 변수를 추가한 다음, 파이프라인을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="600a9-105">This sample application creates a runspace, creates a pipeline, adds two commands to the pipeline, adds two parameters to the second command, and then executes the pipeline.</span></span> <span data-ttu-id="600a9-106">파이프라인에 추가 되는 명령은 `Get-Process` 및 `Sort-Object` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="600a9-106">The commands that are added to the pipeline are the `Get-Process` and `Sort-Object` cmdlets.</span></span>

## <a name="code-sample"></a><span data-ttu-id="600a9-107">코드 예제</span><span class="sxs-lookup"><span data-stu-id="600a9-107">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace08/Runspace08.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="600a9-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="600a9-108">See Also</span></span>

[<span data-ttu-id="600a9-109">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="600a9-109">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
