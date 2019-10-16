---
title: Windows PowerShell 워크플로 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366012"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="86f4d-102">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="86f4d-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="86f4d-103">Windows PowerShell 어셈블리에 의해 노출 되는 활동을 Visual Studio의 Workflow designer에 추가 하 여 XAML 워크플로를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86f4d-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="86f4d-104">다음 Windows PowerShell 어셈블리는 워크플로 사용 활동을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="86f4d-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="86f4d-105">워크플로에 대 한 도움말을 제공 하려면 XAML 워크플로를 모듈로 패키지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86f4d-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="86f4d-106">모듈에 대 한 자세한 내용은 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="86f4d-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="86f4d-107">Microsoft. Powershell. 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="86f4d-108">Microsoft. Powershell. 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="86f4d-109">Microsoft. Powershell. 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="86f4d-110">Microsoft. Powershell. 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="86f4d-111">Microsoft. Powershell. 보안 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="86f4d-112">Microsoft. Powershell. 작업</span><span class="sxs-lookup"><span data-stu-id="86f4d-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="86f4d-113">다음 항목에서는 Windows PowerShell 작업을 사용 하 여 워크플로를 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="86f4d-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="86f4d-114">Visual Studio 도구 상자에 Windows PowerShell 활동 추가</span><span class="sxs-lookup"><span data-stu-id="86f4d-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="86f4d-115">Windows PowerShell 작업으로 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="86f4d-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="86f4d-116">Windows PowerShell 스크립트를 사용 하 여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="86f4d-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="86f4d-117">Windows PowerShell 워크플로 가져오기 및 호출</span><span class="sxs-lookup"><span data-stu-id="86f4d-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="86f4d-118">Windows PowerShell Cmdlet에서 워크플로 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="86f4d-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)