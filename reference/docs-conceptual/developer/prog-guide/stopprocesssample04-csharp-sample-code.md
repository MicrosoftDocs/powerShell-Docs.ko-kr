---
title: StopProcessSample04 (C#) 샘플 코드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 778ce1a2-e16d-4af5-b15b-77ca4326bdc4
caps.latest.revision: 5
ms.openlocfilehash: df5591e351790d18bf2a5b5554d792ab8175dcc6
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416050"
---
# <a name="stopprocesssample04-c-sample-code"></a><span data-ttu-id="1584b-102">StopProcessSample04(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="1584b-102">StopProcessSample04 (C#) Sample Code</span></span>

<span data-ttu-id="1584b-103">StopProc04 sample cmdlet에 C# 대 한 전체 샘플 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1584b-103">Here is the complete C# sample code for the StopProc04 sample cmdlet.</span></span> <span data-ttu-id="1584b-104">[Cmdlet에 매개 변수 집합 추가](../cmdlet/adding-parameter-sets-to-a-cmdlet.md)에 설명 된 `Stop-Process` cmdlet에 대 한 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1584b-104">This is the code for the `Stop-Process` cmdlet described in [Adding Parameter Sets to a Cmdlet](../cmdlet/adding-parameter-sets-to-a-cmdlet.md).</span></span> <span data-ttu-id="1584b-105">`Stop-Process` cmdlet은 [첫 번째 Cmdlet 만들기](../cmdlet/creating-a-cmdlet-without-parameters.md)에 설명 된 대로 Get Proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1584b-105">The `Stop-Process` cmdlet is designed to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](../cmdlet/creating-a-cmdlet-without-parameters.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="1584b-106">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 stopprocesssample04.cs cmdlet에 대 한 () 원본 파일을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1584b-106">You can download the C# (stopprocesssample04.cs) source file for this Stop-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="1584b-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1584b-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="1584b-108">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1584b-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L11-L435 "StopProcessSample04.cs")]

## <a name="see-also"></a><span data-ttu-id="1584b-109">관련 항목</span><span class="sxs-lookup"><span data-stu-id="1584b-109">See Also</span></span>

[<span data-ttu-id="1584b-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="1584b-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="1584b-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1584b-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
