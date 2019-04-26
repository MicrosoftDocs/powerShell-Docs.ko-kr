---
title: AccessDbProviderSample01 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081991"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="7e0a8-102">AccessDbProviderSample01 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="7e0a8-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="7e0a8-103">다음 코드에 설명 된 Windows PowerShell 공급자의 구현을 보여 줍니다 [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="7e0a8-104">이 구현을 시작 및 중지를 공급자에 대 한 메서드를 제공 하 고 데이터 저장소에 액세스 하려면 또는 가져오기 또는 데이터 저장소에서 데이터를 설정 하는 수단을 제공 하지 않습니다, 하지만 모든 공급자에 필요한 기본 기능을 제공지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="7e0a8-105">다운로드할 수 있습니다는 C# Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 소스 파일 (AccessDBSampleProvider01.cs).</span><span class="sxs-lookup"><span data-stu-id="7e0a8-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="7e0a8-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="7e0a8-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="7e0a8-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7e0a8-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="7e0a8-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="7e0a8-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="7e0a8-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7e0a8-110">See Also</span></span>

[<span data-ttu-id="7e0a8-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="7e0a8-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="7e0a8-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="7e0a8-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)