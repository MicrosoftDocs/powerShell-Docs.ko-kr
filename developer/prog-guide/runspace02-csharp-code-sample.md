---
title: Runspace02 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 0a8fc05db74529e2bfb88820b9cfd988245e0aeb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854619"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="c143d-102">Runspace02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="c143d-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="c143d-103">다음은 C# Runspace02 샘플의 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="c143d-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="c143d-104">이 샘플에서는 합니다 [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 실행 하는 클래스는 `Get-Process` cmdlet 동기적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c143d-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="c143d-105">데이터 바인딩 및 Windows Forms DataGridView 컨트롤에서 결과 표시 하려면 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c143d-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="c143d-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="c143d-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="c143d-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c143d-107">See Also</span></span>

[<span data-ttu-id="c143d-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c143d-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)