---
title: RunSpace05 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9688cd69-07ea-4ea0-8822-0a4850bcf86c
caps.latest.revision: 7
ms.openlocfilehash: 4d9a2db76fe69a8509d33a22124f5f952b1d3c80
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978307"
---
# <a name="runspace05-code-sample"></a><span data-ttu-id="8c3fd-102">RunSpace05 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="8c3fd-102">RunSpace05 Code Sample</span></span>

<span data-ttu-id="8c3fd-103">다음은 [RunspaceConfiguration를 사용 하 여 Runspace 구성](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2)에 설명 된 Runspace05 샘플에 대 한 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-103">Here is the source code for the Runspace05 sample that is described in [Configuring a Runspace Using RunspaceConfiguration](https://msdn.microsoft.com/42681d19-2d05-4975-befd-afb1990e79b2).</span></span>
<span data-ttu-id="8c3fd-104">이 샘플에서는 runspace 구성 정보를 만들고, runspace를 만들고, 단일 명령을 사용 하 여 파이프라인을 만들고, 파이프라인을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-104">This sample shows how to create the runspace configuration information, create a runspace, create a pipeline with a single command, and then execute the pipeline.</span></span> <span data-ttu-id="8c3fd-105">실행 되는 명령은 `Get-Process` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-105">The command that is executed is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8c3fd-106">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace05.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-106">You can download the C# source file (runspace05.cs) by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="8c3fd-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="8c3fd-108">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c3fd-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="8c3fd-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="8c3fd-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace05/Runspace05.cs" range="11-86":::

## <a name="see-also"></a><span data-ttu-id="8c3fd-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8c3fd-110">See Also</span></span>

[<span data-ttu-id="8c3fd-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="8c3fd-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="8c3fd-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="8c3fd-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
