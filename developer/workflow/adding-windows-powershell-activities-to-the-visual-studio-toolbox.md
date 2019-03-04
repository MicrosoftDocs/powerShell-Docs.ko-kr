---
title: Visual Studio 도구 상자에 Windows PowerShell 활동을 추가 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863569"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="cd643-102">Visual Studio 도구 상자에 Windows PowerShell 활동 추가</span><span class="sxs-lookup"><span data-stu-id="cd643-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="cd643-103">워크플로 디자이너를 사용 하 여 PowerShell 워크플로 작성 하기 전에 Visual Studio 워크플로 콘솔 응용 프로그램 프로젝트 도구 상자에는 PowerShell 작업을 먼저 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="cd643-104">다음 절차에는 Microsoft.PowerShell.Core.Activities 어셈블리에서 Visual Studio 도구 상자에 활동을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="cd643-105">도구 상자에 Windows PowerShell 활동을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="cd643-106">Visual Studio에서 새 워크플로 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="cd643-107">에 **뷰** 메뉴에서 클릭 **도구 상자**합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="cd643-108">도구 상자 내부를 마우스 오른쪽 단추로 클릭 하 고 클릭 하 여 도구 상자에서 새 탭을 추가 **추가 탭**을 고 새 탭에 "PowerShell 활동" 같은 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="cd643-109">탭 추가 도구 상자에서 다른 도구에서 별도 PowerShell 작업을 그룹화 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="cd643-110">새 도구 상자 탭 클릭 **항목 선택...** . 합니다 **도구 상자 항목 선택** 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="cd643-111">에 **도구 상자 항목 선택** 대화 상자에서 클릭 합니다 **System.Activities** 탭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="cd643-112">**찾아보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-112">Click **Browse**.</span></span>

7. <span data-ttu-id="cd643-113">%WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e 폴더로 이동한 후 Microsoft.PowerShell.Core.Activities.dll를 두 번 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="cd643-114">**확인**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-114">Click **OK**.</span></span> <span data-ttu-id="cd643-115">Microsoft.PowerShell.Core.Activities 어셈블리에서 정의 된 활동 도구 상자에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd643-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd643-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd643-116">See Also</span></span>

[<span data-ttu-id="cd643-117">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="cd643-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="cd643-118">Windows PowerShell 작업을 사용 하 여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="cd643-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)