---
title: AccessDbProviderSample02 Code Sample | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b89a4903-3efc-4b08-9b20-2baadf1d1b66
caps.latest.revision: 6
ms.openlocfilehash: 33cdebd7f2f5ae21ec7aff559382362025d12e47
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416253"
---
# <a name="accessdbprovidersample02-code-sample"></a><span data-ttu-id="aa113-102">AccessDbProviderSample02 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="aa113-102">AccessDbProviderSample02 Code Sample</span></span>

<span data-ttu-id="aa113-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span><span class="sxs-lookup"><span data-stu-id="aa113-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Windows PowerShell Drive Provider](./creating-a-windows-powershell-drive-provider.md).</span></span> <span data-ttu-id="aa113-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span><span class="sxs-lookup"><span data-stu-id="aa113-104">This implementation creates a path, makes a connection to an Access database, and then removes the drive.</span></span>

> [!NOTE]
> <span data-ttu-id="aa113-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span><span class="sxs-lookup"><span data-stu-id="aa113-105">You can download the C# source file (AccessDBSampleProvider02.cs) for this provider using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="aa113-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="aa113-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="aa113-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span><span class="sxs-lookup"><span data-stu-id="aa113-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="aa113-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="aa113-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="aa113-109">Code Sample</span><span class="sxs-lookup"><span data-stu-id="aa113-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L11-L154 "AccessDBProviderSample02.cs")]


## <a name="see-also"></a><span data-ttu-id="aa113-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa113-110">See Also</span></span>

[<span data-ttu-id="aa113-111">Windows PowerShell Programmer's Guide</span><span class="sxs-lookup"><span data-stu-id="aa113-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="aa113-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="aa113-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
