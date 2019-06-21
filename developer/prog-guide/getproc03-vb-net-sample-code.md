---
title: GetProc03 샘플 코드 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301565"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="a62a5-102">GetProc03(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="a62a5-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="a62a5-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 받아들일 수 있는 cmdlet은 파이프라인 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a62a5-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="a62a5-104">이 구현에서 정의 된 `Name` 파이프라인 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 사용 하 여는 [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 메서드.</span><span class="sxs-lookup"><span data-stu-id="a62a5-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="a62a5-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="a62a5-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
