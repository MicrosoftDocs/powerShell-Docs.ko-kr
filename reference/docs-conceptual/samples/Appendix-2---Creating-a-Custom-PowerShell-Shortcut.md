---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 부록 2 사용자 지정 PowerShell 바로 가기 만들기
description: 다음 절차에서는 편리한 여러 옵션이 사용자 지정되어 있는 Windows PowerShell 바로 가기를 만드는 방법을 설명합니다.
ms.openlocfilehash: abdab517dec1357050bf431b6f2e35311ad49976
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500728"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="ecca1-104">부록 2 - 사용자 지정 PowerShell 바로 가기 만들기</span><span class="sxs-lookup"><span data-stu-id="ecca1-104">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="ecca1-105">다음 절차에서는 편리한 여러 옵션이 사용자 지정되어 있는 Windows PowerShell 바로 가기를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-105">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="ecca1-106">Powershell.exe를 가리키는 바로 가기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-106">Create a shortcut that points to Powershell.exe.</span></span>

1. <span data-ttu-id="ecca1-107">바로 가기를 마우스 오른쪽 단추로 클릭한 다음 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-107">Right-click the shortcut, and then click **Properties** .</span></span>

1. <span data-ttu-id="ecca1-108">**옵션** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-108">Click the **Options** tab.</span></span>

1. <span data-ttu-id="ecca1-109">**옵션 편집** 섹션에서 **빠른 편집** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-109">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="ecca1-110">이 설정을 사용하면 마우스 왼쪽 단추를 끌어 Windows PowerShell 콘솔 창에서 텍스트를 선택하고 Enter 키를 누르거나 마우스 오른쪽 단추를 클릭하여 텍스트를 클립보드에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-110">This setting lets you select text in the Windows PowerShell console window by dragging the left  mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking  the mouse.</span></span>

1. <span data-ttu-id="ecca1-111">**옵션 편집** 섹션에서 **삽입 모드** 확인란을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-111">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="ecca1-112">이 설정을 사용하면 콘솔 창에서 마우스 오른쪽 단추를 클릭하여 클립보드의 텍스트를 자동으로 붙여넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-112">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

1. <span data-ttu-id="ecca1-113">**명령 기록** 섹션의 **버퍼 크기** 상자에 1에서 999 사이의 숫자를 입력하거나 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-113">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="ecca1-114">이렇게 하면 콘솔 버퍼에 유지되는 입력한 명령 수가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-114">This sets the number of typed commands that will be kept in the console buffer.</span></span>

1. <span data-ttu-id="ecca1-115">**명령 기록** 섹션에서 **중복 시 이전 항목 삭제** 확인란을 선택하여 콘솔 버퍼에서 반복 명령을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-115">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

1. <span data-ttu-id="ecca1-116">**레이아웃** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-116">Click the **Layout** tab.</span></span>

1. <span data-ttu-id="ecca1-117">**화면 버퍼** 섹션의 **높이** 상자에 1에서 9999 사이의 숫자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-117">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="ecca1-118">높이는 버퍼링된 출력의 줄 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-118">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="ecca1-119">콘솔 창을 스크롤할 때 보기에 유지되는 최대 줄 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-119">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="ecca1-120">이 숫자가 **창 크기** 섹션에 표시된 높이보다 작으면 창 크기 높이가 동일한 값으로 자동으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-120">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

1. <span data-ttu-id="ecca1-121">**창 크기** 섹션에서 너비에 대해 1에서 9999 사이의 숫자를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-121">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="ecca1-122">이 숫자는 콘솔 창에 가로로 표시되는 문자 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-122">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="ecca1-123">기본 너비는 80이며, Windows PowerShell의 출력 형식은 이 너비로 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-123">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

1. <span data-ttu-id="ecca1-124">콘솔을 열 때 바탕 화면의 특정 지점에 배치하려는 경우 **창 위치** 섹션에서 **시스템이 창 위치 지정** 확인란의 선택을 취소하고 **창 위치** 섹션에서 **왼쪽** 및 **위쪽** 상자의 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-124">If you want to place the console at a particular point on the desktop when it is opened, clear  the **Let system position window** check box in the **Window position** section, and then change  the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

1. <span data-ttu-id="ecca1-125">**확인** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ecca1-125">Click **OK** .</span></span>
