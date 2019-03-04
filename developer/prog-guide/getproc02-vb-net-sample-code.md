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
ms.openlocfilehash: 5b5cefae1be3ccf6aec819df83363b7161955b0c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860189"
---
# <a name="getproc02-vbnet-sample-code"></a><span data-ttu-id="e5eb8-102">GetProc02(VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="e5eb8-102">GetProc02 (VB.NET) Sample Code</span></span>

<span data-ttu-id="e5eb8-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="e5eb8-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="e5eb8-104">이 구현을 정의 하는 `Name` 사용 하 고 명령줄 입력을 허용 하도록 매개 변수를 [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 출력으로 메서드 출력을 보내기 위한 메커니즘을 파이프라인에는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e5eb8-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.Writeobject%28System.Object%2Csystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="e5eb8-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="e5eb8-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc02#getproc02vball](Msh_samplesgetproc02#getproc02vball)]  -->

## <a name="see-also"></a><span data-ttu-id="e5eb8-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5eb8-106">See Also</span></span>

[<span data-ttu-id="e5eb8-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="e5eb8-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)