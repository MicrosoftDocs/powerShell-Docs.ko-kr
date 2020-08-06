---
title: AccessDbProviderSample01 코드 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2e9f81b3011ea1b27bafd9e02ea7e0faf7903a62
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784829"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="d0991-102">AccessDbProviderSample01 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="d0991-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="d0991-103">다음 코드는 [기본 Windows Powershell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)에 설명 된 windows powershell 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0991-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span>
<span data-ttu-id="d0991-104">이 구현은 공급자를 시작 및 중지 하는 메서드를 제공 하며 데이터 저장소에 액세스 하거나 데이터 저장소의 데이터를 가져오거나 설정 하는 방법을 제공 하지 않지만 모든 공급자가 필요로 하는 기본 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0991-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="d0991-105">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 c # 소스 파일 (AccessDBSampleProvider01.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0991-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="d0991-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0991-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="d0991-107">다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** .</span><span class="sxs-lookup"><span data-stu-id="d0991-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="d0991-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d0991-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="d0991-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="d0991-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs" range="11-30":::

## <a name="see-also"></a><span data-ttu-id="d0991-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d0991-110">See Also</span></span>

[<span data-ttu-id="d0991-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="d0991-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="d0991-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d0991-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
