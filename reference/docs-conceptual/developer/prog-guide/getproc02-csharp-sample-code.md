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
ms.openlocfilehash: c5e71ddacae1036164c5e8e579ddc8704d30670e
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978392"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="30718-102">GetProc02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="30718-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="30718-103">다음 코드는 명령줄 입력을 허용 하는 `Get-Process` cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="30718-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="30718-104">이 구현에서는 명령줄 입력을 허용 하는 `Name` 매개 변수를 정의 하 고, 출력 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="30718-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="30718-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="30718-105">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs" range="11-76":::

## <a name="see-also"></a><span data-ttu-id="30718-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="30718-106">See Also</span></span>

[<span data-ttu-id="30718-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="30718-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
