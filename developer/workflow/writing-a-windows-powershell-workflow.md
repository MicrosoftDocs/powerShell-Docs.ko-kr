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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857409"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="7ad2b-102">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="7ad2b-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="7ad2b-103">Visual Studio에서 워크플로 디자이너에 Windows PowerShell 어셈블리에서 노출 하는 활동을 추가 하 여 XAML 워크플로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="7ad2b-104">다음 Windows PowerShell 어셈블리 워크플로 작업을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ad2b-105">XAML 워크플로 워크플로에 대 한 도움말을 제공 하려는 경우 모듈로 패키지할 수 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="7ad2b-106">모듈에 대 한 정보를 참조 하세요 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="7ad2b-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="7ad2b-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="7ad2b-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="7ad2b-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="7ad2b-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="7ad2b-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="7ad2b-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="7ad2b-113">다음 항목에는 Windows PowerShell 작업을 사용 하 여 워크플로 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="7ad2b-114">Visual Studio 도구 상자에 Windows PowerShell 활동을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="7ad2b-115">Windows PowerShell 작업을 사용 하 여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="7ad2b-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="7ad2b-116">Windows PowerShell 스크립트를 사용 하 여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="7ad2b-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="7ad2b-117">가져오기 및 Windows PowerShell 워크플로 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ad2b-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="7ad2b-118">Windows PowerShell Cmdlet에서 워크플로 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="7ad2b-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)