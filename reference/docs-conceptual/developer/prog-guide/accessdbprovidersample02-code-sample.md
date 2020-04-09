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
ms.openlocfilehash: 32abcfafb207ada23667cc6f0f03d382c6868ccb
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978613"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="66e00-102">AccessDbProviderSample02 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="66e00-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="66e00-103">다음 코드는 [Windows Powershell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)에 설명 된 windows powershell 공급자의 구현을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="66e00-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span>
<span data-ttu-id="66e00-104">이 구현에서는 경로를 만들고 Access 데이터베이스에 연결한 다음 드라이브를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="66e00-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="66e00-105">Windows Vista 용 Microsoft C# Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider02.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e00-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="66e00-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66e00-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
> <span data-ttu-id="66e00-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66e00-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span> <span data-ttu-id="66e00-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66e00-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="66e00-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="66e00-109">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs" range="11-154":::

## <a name="see-also"></a><span data-ttu-id="66e00-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66e00-110">See Also</span></span>

[<span data-ttu-id="66e00-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="66e00-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="66e00-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="66e00-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
