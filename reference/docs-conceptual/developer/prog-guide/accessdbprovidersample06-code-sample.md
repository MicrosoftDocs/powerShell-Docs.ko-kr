---
ms.date: 09/13/2016
ms.topic: reference
title: AccessDbProviderSample06 코드 샘플
description: AccessDbProviderSample06 코드 샘플
ms.openlocfilehash: 401aca7fab86cfbf3fa8d671eab17412dd162a88
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647499"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="0fccf-103">AccessDbProviderSample06 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="0fccf-103">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="0fccf-104">다음 코드는 [Windows Powershell 콘텐츠 공급자 만들기](./creating-a-windows-powershell-content-provider.md)에 설명 된 windows powershell 콘텐츠 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0fccf-104">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span>
<span data-ttu-id="0fccf-105">이 공급자를 사용 하면 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fccf-105">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="0fccf-106">Windows Vista 용 Microsoft Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 c # 소스 파일 (AccessDBSampleProvider06.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0fccf-106">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0fccf-107">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0fccf-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="0fccf-108">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="0fccf-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="0fccf-109">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0fccf-109">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="0fccf-110">코드 예제</span><span class="sxs-lookup"><span data-stu-id="0fccf-110">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="11-2399":::

## <a name="see-also"></a><span data-ttu-id="0fccf-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0fccf-111">See Also</span></span>

[<span data-ttu-id="0fccf-112">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="0fccf-112">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0fccf-113">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0fccf-113">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
