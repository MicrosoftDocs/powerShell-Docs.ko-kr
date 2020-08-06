---
title: 'Runspace01 (c #) 코드 샘플 | Microsoft Docs'
ms.date: 09/13/2016
ms.openlocfilehash: 418162731b4a98989642e1c61c655fdb0f002698
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787062"
---
# <a name="runspace01-c-code-sample"></a><span data-ttu-id="ca01b-102">Runspace01(C#) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ca01b-102">Runspace01 (C#) Code Sample</span></span>

<span data-ttu-id="ca01b-103">다음은 [지정 된 명령을 실행 하는 콘솔 응용 프로그램 만들기](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program)에서 설명 하는 runspace에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01b-103">Here are the code samples for the runspace described in [Creating a Console Application That Runs a Specified Command](/dotnet/csharp/programming-guide/inside-a-program/hello-world-your-first-program).</span></span>
<span data-ttu-id="ca01b-104">이렇게 하기 위해 응용 프로그램은 runspace를 호출한 다음 명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca01b-104">To do this, the application invokes a runspace, and then invokes a command.</span></span> <span data-ttu-id="ca01b-105">이 응용 프로그램은 runspace 구성 정보를 지정 하지 않으며 파이프라인을 명시적으로 만들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01b-105">(Note that this application does not specify runspace configuration information, nor does it explicitly create a pipeline).</span></span> <span data-ttu-id="ca01b-106">호출 되는 명령은 `Get-Process` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="ca01b-106">The command that is invoked is the `Get-Process` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="ca01b-107">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 c # 소스 파일 (runspace01.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca01b-107">You can download the C# source file (runspace01.cs) for this runspace using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span>
> <span data-ttu-id="ca01b-108">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ca01b-108">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="ca01b-109">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="ca01b-109">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ca01b-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ca01b-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace01/Runspace01.cs" range="11-62":::

## <a name="see-also"></a><span data-ttu-id="ca01b-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca01b-111">See Also</span></span>

[<span data-ttu-id="ca01b-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="ca01b-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ca01b-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ca01b-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
