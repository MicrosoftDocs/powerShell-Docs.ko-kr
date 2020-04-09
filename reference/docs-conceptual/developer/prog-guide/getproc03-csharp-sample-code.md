---
title: GetProc03 (C#) 샘플 코드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 24f47ab8d99683e6d0024bd8073b6d7bb5dcbd90
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978375"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="58c42-102">GetProc03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="58c42-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="58c42-103">다음 코드는 파이프라인 입력을 수락할 수 있는 `Get-Process` cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="58c42-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="58c42-104">이 구현은 파이프라인 입력을 허용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 하 고, [WriteObject (system.object, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 파이프라인으로 보내기 위한 출력 메커니즘으로 사용 하는 `Name` 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="58c42-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="58c42-105">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 getprov03.cs cmdlet에 대 한 원본 파일 ()을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c42-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="58c42-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58c42-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="58c42-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58c42-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="58c42-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="58c42-108">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="58c42-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58c42-109">See Also</span></span>

[<span data-ttu-id="58c42-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="58c42-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="58c42-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="58c42-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
