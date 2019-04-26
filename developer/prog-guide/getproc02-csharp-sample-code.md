---
title: GetProc02 (C#) 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 2ac4aea2fdefdfe86349c14fe9b87cd8c41db090
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081708"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="82018-102">GetProc02(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="82018-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="82018-103">다음 코드의 구현을 보여 줍니다는 `Get-Process` 명령줄 입력을 허용 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="82018-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="82018-104">이 구현을 정의 하는 `Name` 사용 하 고 명령줄 입력을 허용 하도록 매개 변수를 [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 출력으로 메서드 출력을 보내기 위한 메커니즘을 파이프라인에는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="82018-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="82018-105">코드 예제</span><span class="sxs-lookup"><span data-stu-id="82018-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="82018-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82018-106">See Also</span></span>

[<span data-ttu-id="82018-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="82018-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)