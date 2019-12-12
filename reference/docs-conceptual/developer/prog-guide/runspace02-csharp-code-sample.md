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
ms.openlocfilehash: abf539bc29bd9ccac59bd5957397fbe68951f266
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366622"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="222db-102">Runspace02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="222db-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="222db-103">Runspace02 샘플에 C# 대 한 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="222db-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="222db-104">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 `Get-Process` cmdlet을 동기적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="222db-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="222db-105">그러면 Windows Forms 및 데이터 바인딩이 DataGridView 컨트롤에 결과를 표시 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="222db-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="222db-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="222db-106">Code Sample</span></span>

[!code-csharp[Runspace02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs#L11-L82 "Runspace02.cs")]

## <a name="see-also"></a><span data-ttu-id="222db-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="222db-107">See Also</span></span>

[<span data-ttu-id="222db-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="222db-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
