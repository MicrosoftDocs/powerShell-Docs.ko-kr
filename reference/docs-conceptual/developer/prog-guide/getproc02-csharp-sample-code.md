---
title: GetProc02 (C#) 샘플 코드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360372"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="698d0-102">GetProc02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="698d0-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="698d0-103">다음 코드는 명령줄 입력을 허용 하는 `Get-Process` cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="698d0-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="698d0-104">이 구현에서는 명령줄 입력을 허용 하는 `Name` 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="698d0-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="698d0-105">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="698d0-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="698d0-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="698d0-106">See Also</span></span>

[<span data-ttu-id="698d0-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="698d0-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
