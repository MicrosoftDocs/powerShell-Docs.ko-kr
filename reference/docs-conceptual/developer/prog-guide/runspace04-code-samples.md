---
title: RunSpace04 코드 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb6fcc47-cf89-43e7-b686-3d60934ce3e7
caps.latest.revision: 6
ms.openlocfilehash: e9a79e90da7e0a8232280fa2275d357cb633f4d6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416085"
---
# <a name="runspace04-code-samples"></a><span data-ttu-id="0e1cb-102">RunSpace04 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="0e1cb-102">RunSpace04 Code Samples</span></span>

<span data-ttu-id="0e1cb-103">다음은 종료 오류를 생성 하는 스크립트를 실행 하기 위해 [Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) 클래스를 사용 하는 runspace에 대 한 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-103">Here is a code sample for a runspace that uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute a script that generates a terminating error.</span></span> <span data-ttu-id="0e1cb-104">호스트 응용 프로그램은 오류를 catch 하 고 오류 레코드를 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-104">The host application is responsible for catching the error and interpreting the error record.</span></span>

> [!NOTE]
> <span data-ttu-id="0e1cb-105">Windows Vista 용 Windows 소프트웨어 개발 키트 및 Microsoft .NET Framework 3.0 런타임 구성 요소를 사용 하 여이 runspace에 대 한 VB.NET 원본 파일 (Runspace04)을 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-105">You can download the VB.NET source file (Runspace04.vb) for this runspace using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="0e1cb-106">다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="0e1cb-107">다운로드 된 원본 파일은 **\<PowerShell Samples >** 디렉터리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

<span data-ttu-id="0e1cb-108">전체 샘플 코드는 다음 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0e1cb-108">For complete sample code, see the following topics.</span></span>

|<span data-ttu-id="0e1cb-109">Language</span><span class="sxs-lookup"><span data-stu-id="0e1cb-109">Language</span></span>|<span data-ttu-id="0e1cb-110">항목</span><span class="sxs-lookup"><span data-stu-id="0e1cb-110">Topic</span></span>|
|--------------|-----------|
|<span data-ttu-id="0e1cb-111">VB.NET</span><span class="sxs-lookup"><span data-stu-id="0e1cb-111">VB.NET</span></span>|[<span data-ttu-id="0e1cb-112">Runspace01 (VB.NET) 코드 샘플</span><span class="sxs-lookup"><span data-stu-id="0e1cb-112">Runspace01 (VB.NET) Code Sample</span></span>](./runspace01-vb-net-code-sample.md)|

## <a name="see-also"></a><span data-ttu-id="0e1cb-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e1cb-113">See Also</span></span>

[<span data-ttu-id="0e1cb-114">Windows PowerShell 프로그래머 가이드</span><span class="sxs-lookup"><span data-stu-id="0e1cb-114">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="0e1cb-115">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0e1cb-115">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
