---
title: AccessDbProviderSample02 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 67a169bfac0b0fc90e6ccd276d3d3592d1b70bb0
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082034"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="bda35-102">AccessDbProviderSample02 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="bda35-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="bda35-103">다음 코드에 설명 된 Windows PowerShell 공급자의 구현을 보여 줍니다 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bda35-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="bda35-104">이 구현 경로 만든 다음, Access 데이터베이스에 대 한 연결을 사용 하면 드라이브를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="bda35-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="bda35-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider02.cs).</span><span class="sxs-lookup"><span data-stu-id="bda35-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="bda35-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="bda35-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="bda35-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="bda35-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="bda35-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="bda35-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="bda35-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="bda35-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="bda35-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bda35-110">See Also</span></span>

[<span data-ttu-id="bda35-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="bda35-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="bda35-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="bda35-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)