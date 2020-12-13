---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc02(VB.NET) 코드 샘플
description: GetProc02(VB.NET) 코드 샘플
ms.openlocfilehash: aefc3a4df5e0f29120916648ecdca41931a4c1c6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354544"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="a7c6c-103">GetProc02(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a7c6c-103">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="a7c6c-104">다음 코드는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7c6c-104">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="a7c6c-105">이 구현에서는 `Name` 명령줄 입력을 허용 하는 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7c6c-105">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a7c6c-106">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a7c6c-106">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="a7c6c-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7c6c-107">See Also</span></span>

[<span data-ttu-id="a7c6c-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="a7c6c-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
