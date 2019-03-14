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
ms.openlocfilehash: 6e86318573df92b9ec84056631843e0efa096a3b
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795609"
---
# <a name="accessdbprovidersample06-code-sample"></a><span data-ttu-id="cb53c-102">AccessDbProviderSample06 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="cb53c-102">AccessDbProviderSample06 Code Sample</span></span>

<span data-ttu-id="cb53c-103">다음 코드에 설명 된 콘텐츠 공급자는 Windows PowerShell의 구현을 보여 줍니다 [Windows PowerShell 콘텐츠 공급자를 만들](./creating-a-windows-powershell-content-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb53c-103">The following code shows the implementation of the Windows PowerShell content provider described in [Creating a Windows PowerShell Content Provider](./creating-a-windows-powershell-content-provider.md).</span></span> <span data-ttu-id="cb53c-104">이 공급자는 데이터 저장소에 있는 항목의 콘텐츠를 조작 하는 사용자를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb53c-104">This provider enables the user to manipulate the contents of the items in a data store.</span></span>

> [!NOTE]
> <span data-ttu-id="cb53c-105">다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 소스 파일 (AccessDBSampleProvider06.cs).</span><span class="sxs-lookup"><span data-stu-id="cb53c-105">You can download the C# source file (AccessDBSampleProvider06.cs) for this provider by using the Microsoft Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="cb53c-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb53c-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="cb53c-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="cb53c-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="cb53c-108">다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb53c-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="cb53c-109">코드 예제</span><span class="sxs-lookup"><span data-stu-id="cb53c-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a><span data-ttu-id="cb53c-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb53c-110">See Also</span></span>

[<span data-ttu-id="cb53c-111">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="cb53c-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="cb53c-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cb53c-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)