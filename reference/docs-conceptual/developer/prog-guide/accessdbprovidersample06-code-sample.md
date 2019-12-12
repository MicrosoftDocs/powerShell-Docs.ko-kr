---
title: AccessDbProviderSample06 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: baab6a56-c199-48d7-a03e-a904b1bb1baa
caps.latest.revision: 7
ms.openlocfilehash: 7f75a3a3d2ab89696bb34ec2fdf7ba7a5ce0f9b1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416228"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="93837-102">AccessDbProviderSample06 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="93837-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="93837-103">다음 코드는 [Windows Powershell 콘텐츠 공급자 만들기](./creating-a-windows-powershell-content-provider.md)에 설명 된 windows powershell 콘텐츠 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="93837-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="93837-104">이 공급자를 사용 하면 사용자가 데이터 저장소에 있는 항목의 내용을 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93837-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="93837-105">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider06.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93837-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="93837-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93837-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="93837-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93837-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="93837-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="93837-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="93837-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="93837-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="93837-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93837-110">See Also</span></span>

[<span data-ttu-id="93837-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="93837-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="93837-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="93837-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
