---
title: GetProc02 샘플 코드 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301340"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="fe375-102">GetProc02(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="fe375-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="fe375-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="fe375-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="fe375-104">이 구현을 정의 하는 `Name` 사용 하 고 명령줄 입력을 허용 하도록 매개 변수를 [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드 출력을 보내기 위한 출력 메커니즘으로 개체를 파이프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="fe375-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="fe375-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="fe375-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="fe375-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe375-106">See Also</span></span>

[<span data-ttu-id="fe375-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="fe375-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
