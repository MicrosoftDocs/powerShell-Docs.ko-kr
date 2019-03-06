---
title: RunSpace10 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5337dc40-c56e-458b-aedc-5f5d401dfd28
caps.latest.revision: 6
ms.openlocfilehash: 77c0675b45bf4ff6f8c6a85ff9a090c13c199c6d
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429587"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="ab390-102">RunSpace10 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ab390-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="ab390-103">Runspace10 샘플에 대 한 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ab390-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="ab390-104">이 샘플 응용 프로그램 추가 하는 cmdlet [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) 다음 수정 된 구성 정보를 사용 하 여 runspace를 만들려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ab390-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="ab390-105">다운로드할 수 있습니다는 C# Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및 Microsoft.NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace10.cs).</span><span class="sxs-lookup"><span data-stu-id="ab390-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="ab390-106">다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.</span><span class="sxs-lookup"><span data-stu-id="ab390-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="ab390-107">다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="ab390-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ab390-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ab390-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="ab390-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ab390-109">See Also</span></span>

[<span data-ttu-id="ab390-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="ab390-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="ab390-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ab390-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)