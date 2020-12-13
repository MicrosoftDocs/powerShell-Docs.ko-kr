---
ms.date: 09/13/2016
ms.topic: reference
title: RunSpace03(C#) 코드 샘플
description: RunSpace03(C#) 코드 샘플
ms.openlocfilehash: cdb08811de13f8bbf5cd91fcbef552c78594b788
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653833"
---
# <a name="runspace03-c-code-sample"></a><span data-ttu-id="65faf-103">RunSpace03(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="65faf-103">RunSpace03 (C#) Code Sample</span></span>

<span data-ttu-id="65faf-104">다음은 "지정 된 스크립트를 실행 하는 콘솔 응용 프로그램 만들기"에 설명 된 콘솔 응용 프로그램에 대 한 c # 소스 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="65faf-104">Here is the C# source code for the console application described in "Creating a Console Application That Runs a Specified Script".</span></span> <span data-ttu-id="65faf-105">이 샘플에서는 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하 여 스크립트에 전달 된 프로세스 이름 목록을 사용 하 여 프로세스 정보를 검색 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="65faf-105">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that retrieves process information by using the list of process names passed into the script.</span></span> <span data-ttu-id="65faf-106">입력 개체를 스크립트에 전달 하는 방법 및 출력 개체 뿐만 아니라 오류 개체를 검색 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="65faf-106">It shows how to pass input objects to a script and how to retrieve error objects as well as the output objects.</span></span>

> [!NOTE]
> <span data-ttu-id="65faf-107">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 샘플에 대 한 c # 소스 파일 (runspace03.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="65faf-107">You can download the C# source file (runspace03.cs) for this sample using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="65faf-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="65faf-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="65faf-109">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="65faf-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="65faf-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="65faf-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace03/Runspace03.cs" range="11-88":::

## <a name="see-also"></a><span data-ttu-id="65faf-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="65faf-111">See Also</span></span>

[<span data-ttu-id="65faf-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="65faf-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="65faf-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="65faf-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
