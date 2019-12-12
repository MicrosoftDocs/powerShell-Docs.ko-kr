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
ms.openlocfilehash: fcc424f83275452e223ef025cc8d95128520bdbc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417858"
---
# <a name="runspace10-code-sample"></a><span data-ttu-id="c1406-102">RunSpace10 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="c1406-102">RunSpace10 Code Sample</span></span>

<span data-ttu-id="c1406-103">Runspace10 샘플에 대 한 소스 코드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c1406-103">Here is the source code for the Runspace10 sample.</span></span> <span data-ttu-id="c1406-104">이 샘플 응용 프로그램은 [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) 에 cmdlet을 추가한 다음 수정 된 구성 정보를 사용 하 여 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1406-104">This sample application adds a cmdlet to [System.Management.Automation.Runspaces.Runspaceconfiguration](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConfiguration) and then uses the modified configuration information to create the runspace.</span></span>

> [!NOTE]
> <span data-ttu-id="c1406-105">Windows Vista 용 Windows C# 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여 원본 파일 (runspace10.cs)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1406-105">You can download the C# source file (runspace10.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="c1406-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c1406-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="c1406-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1406-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c1406-108">코드 예제</span><span class="sxs-lookup"><span data-stu-id="c1406-108">Code Sample</span></span>

[!code-csharp[Runspace10.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/Runspace10/Runspace10.cs#L11-L118 "Runspace10.cs")]

## <a name="see-also"></a><span data-ttu-id="c1406-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1406-109">See Also</span></span>

[<span data-ttu-id="c1406-110">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="c1406-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="c1406-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c1406-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
