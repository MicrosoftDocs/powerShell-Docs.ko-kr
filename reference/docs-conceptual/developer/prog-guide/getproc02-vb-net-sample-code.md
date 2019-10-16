---
title: GetProc02 (VB.NET) 샘플 코드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3497546-5b3a-4e29-84ba-cd9747be64b3
caps.latest.revision: 6
ms.openlocfilehash: 4ec63ed32bd2906f5b027523aa0f253b51a5d873
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366772"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="6ef41-102">GetProc02(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="6ef41-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="6ef41-103">다음 코드는 명령줄 입력을 허용 하는 `Get-Process` cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ef41-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="6ef41-104">이 구현에서는 명령줄 입력을 허용 하는 `Name` 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ef41-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="6ef41-105">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="6ef41-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="6ef41-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6ef41-106">See Also</span></span>

[<span data-ttu-id="6ef41-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="6ef41-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
