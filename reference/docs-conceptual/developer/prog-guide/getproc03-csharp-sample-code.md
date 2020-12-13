---
ms.date: 09/13/2016
ms.topic: reference
title: GetProc03(C#) 코드 샘플
description: GetProc03(C#) 코드 샘플
ms.openlocfilehash: c81ba04b2b335f4ce992c6b3ed2f019cf6d7d20f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355581"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="f00a1-103">GetProc03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="f00a1-103">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="f00a1-104">다음 코드는 `Get-Process` 파이프라인 입력을 수락할 수 있는 cmdlet의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f00a1-104">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="f00a1-105">이 구현은 `Name` 파이프라인 입력을 허용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 하 고, 개체를 파이프라인으로 보내기 위한 출력 메커니즘으로 [WriteObject (system.string, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 메서드를 사용 하는 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f00a1-105">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="f00a1-106">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 Get-Proc cmdlet에 대 한 c # 소스 파일 (getprov03.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f00a1-106">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="f00a1-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f00a1-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="f00a1-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="f00a1-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="f00a1-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="f00a1-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="11-78":::

## <a name="see-also"></a><span data-ttu-id="f00a1-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f00a1-110">See Also</span></span>

[<span data-ttu-id="f00a1-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="f00a1-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="f00a1-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="f00a1-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
