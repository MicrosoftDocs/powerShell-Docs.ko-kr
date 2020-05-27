---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: Windows PowerShell ISE 스크립팅 개체 모델의 용도
ms.openlocfilehash: 1f48df112bd19297baa311116e79d3d7603d7c81
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809749"
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="72e6b-103">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="72e6b-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>

<span data-ttu-id="72e6b-104">개체는 Windows PowerShell ISE(통합 스크립팅 환경)의 형식 및 함수와 연결되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="72e6b-105">개체 모델 참조에서는 이러한 개체를 노출하는 멤버 속성 및 메서드에 대한 세부 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="72e6b-106">스크립트를 사용하여 이러한 메서드와 속성에 직접 액세스하는 방법을 보여 주기 위해 예제가 제공되었습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="72e6b-107">스크립팅 개체 모델은 다음 범위의 작업을 보다 쉽게 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="72e6b-108">Windows PowerShell ISE의 모양 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="72e6b-108">Customizing the appearance of Windows PowerShell ISE</span></span>

<span data-ttu-id="72e6b-109">개체 모델을 사용하여 애플리케이션 설정 및 옵션을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="72e6b-110">예를 들어, 다음과 같이 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-110">For example, you can modify them as follows:</span></span>

- <span data-ttu-id="72e6b-111">오류, 경고, 자세한 정보 출력 및 디버그 출력의 색을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-111">Change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>
- <span data-ttu-id="72e6b-112">명령 창, 출력 창 및 스크립트 창의 배경색을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-112">Get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>
- <span data-ttu-id="72e6b-113">출력 창의 전경색을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-113">Set the foreground color for the Output pane.</span></span>
- <span data-ttu-id="72e6b-114">Windows PowerShell ISE의 글꼴 이름 및 글꼴 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-114">Set the font name and font size for Windows PowerShell ISE.</span></span>
- <span data-ttu-id="72e6b-115">경고를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-115">Configure warnings.</span></span> <span data-ttu-id="72e6b-116">이 설정에는 파일이 여러 PowerShell 탭에 열려 있거나, 파일에 있는 스크립트가 파일이 저장되기 전에 실행되는 경우 발생하는 경고가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>
- <span data-ttu-id="72e6b-117">스크립트 창과 출력 창이 나란히 있는 보기와 스크립트 창이 출력 창 위에 있는 보기 간에 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-117">Switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span>
- <span data-ttu-id="72e6b-118">명령 창을 출력 창의 맨 아래 또는 위에 고정합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-118">Dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="72e6b-119">Windows PowerShell ISE의 기능 향상</span><span class="sxs-lookup"><span data-stu-id="72e6b-119">Enhancing the functionality of Windows PowerShell ISE</span></span>

<span data-ttu-id="72e6b-120">개체 모델을 사용하여 Windows PowerShell ISE의 기능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="72e6b-121">예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-121">For example, you can:</span></span>

- <span data-ttu-id="72e6b-122">Windows PowerShell ISE 자체의 인스턴스를 추가 및 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="72e6b-123">예를 들어 메뉴를 변경하려면 새 메뉴 항목을 추가하고 이 새 메뉴 항목을 스크립트에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>
- <span data-ttu-id="72e6b-124">Windows PowerShell ISE의 메뉴 명령 및 단추를 사용하여 수행할 수 있는 작업 중 일부를 수행하는 스크립트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="72e6b-125">예를 들어 PowerShell 탭을 추가, 제거 또는 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-125">For example, you can add, remove, or select a PowerShell tab.</span></span>
- <span data-ttu-id="72e6b-126">메뉴 명령 및 단추를 사용하여 수행할 수 있는 작업을 보완합니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="72e6b-127">예를 들어 PowerShell 탭의 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-127">For example, you can rename a PowerShell tab.</span></span>
- <span data-ttu-id="72e6b-128">파일과 한 연결된 명령 창, 출력 창 및 스크립트 창용의 텍스트 버퍼를 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="72e6b-129">예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-129">For example, you can:</span></span>
  - <span data-ttu-id="72e6b-130">모든 텍스트를 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-130">Get or set all text.</span></span>
  - <span data-ttu-id="72e6b-131">텍스트 선택 내용을 가져오거나 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-131">Get or set a text selection.</span></span>
  - <span data-ttu-id="72e6b-132">스크립트를 실행하거나 스크립트에서 선택된 부분을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-132">Run a script or run a selected portion of a script.</span></span>
  - <span data-ttu-id="72e6b-133">줄을 스크롤하여 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-133">Scroll a line into view.</span></span>
  - <span data-ttu-id="72e6b-134">캐럿 위치에 텍스트를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-134">Insert text at a caret position.</span></span>
  - <span data-ttu-id="72e6b-135">텍스트 블록을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-135">Select a block of text.</span></span>
  - <span data-ttu-id="72e6b-136">마지막 줄 번호를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-136">Get the last line number.</span></span>
- <span data-ttu-id="72e6b-137">파일 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-137">Perform file operations.</span></span> <span data-ttu-id="72e6b-138">예를 들어, 다음을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-138">For example, you can:</span></span>
  - <span data-ttu-id="72e6b-139">파일을 열거나, 파일을 저장하거나, 다른 이름을 사용하여 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-139">Open a file, save a file, or save a file by using a different name.</span></span>
  - <span data-ttu-id="72e6b-140">파일이 마지막으로 저장된 후 변경되었는지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-140">Determine whether a file has been changed after it was last saved.</span></span>
  - <span data-ttu-id="72e6b-141">파일 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-141">Get the file name.</span></span>
  - <span data-ttu-id="72e6b-142">파일을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="72e6b-143">작업 자동화</span><span class="sxs-lookup"><span data-stu-id="72e6b-143">Automating tasks</span></span>

<span data-ttu-id="72e6b-144">스크립팅 개체 모델을 사용하여 자주 수행하는 작업에 대한 바로 가기 키를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="72e6b-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="72e6b-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="72e6b-145">See also</span></span>

- [<span data-ttu-id="72e6b-146">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="72e6b-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
