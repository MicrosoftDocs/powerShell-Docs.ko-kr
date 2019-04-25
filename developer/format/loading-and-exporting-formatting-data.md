---
title: 형식 지정 데이터를 내보내고 로드 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a48de31-7961-4b0e-b58b-93466e38370b
caps.latest.revision: 6
ms.openlocfilehash: 5c5168ffd74c15066b914ad1b39d9ead947c5e7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065209"
---
# <a name="loading-and-exporting-formatting-data"></a><span data-ttu-id="fa472-102">형식 지정 데이터 로드 및 내보내기</span><span class="sxs-lookup"><span data-stu-id="fa472-102">Loading and Exporting Formatting Data</span></span>

<span data-ttu-id="fa472-103">서식 파일을 만든 후에 현재 세션으로 파일을 로드 하 여 세션의 형식 데이터를 업데이트 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-103">Once you have created your formatting file, you need to update the format data of the session by loading your files into the current session.</span></span> <span data-ttu-id="fa472-104">(Windows PowerShell에서 제공 하는 서식 파일은 현재 세션에 열려 있을 때 등록 된 스냅인에서 로드 됩니다.) 현재 세션의 형식으로 데이터 업데이트 되 면 Windows PowerShell에서 로드 된 형식 지정 파일에 정의 된 보기와 연결 된.NET 개체를 표시 하려면 해당 데이터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-104">(The formatting files provided by Windows PowerShell are loaded by snap-ins that are registered when the current session is opened.) Once the format data of the current session is updated, Windows PowerShell uses that data to display the .NET objects associated with the views defined in the loaded formatting files.</span></span> <span data-ttu-id="fa472-105">현재 세션으로 로드할 수 있는 형식 지정 파일의 수 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-105">There is no limit to the number of formatting files that you can load into the current session.</span></span> <span data-ttu-id="fa472-106">형식 지정 데이터를 업데이트 하는 것 외에도 형식 지정 파일에 다시 현재 세션의 형식 데이터를 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-106">In addition to updating the formatting data, you can export the format data in the current session back to a formatting file.</span></span>

## <a name="loading-format-data"></a><span data-ttu-id="fa472-107">형식으로 데이터 로드</span><span class="sxs-lookup"><span data-stu-id="fa472-107">Loading format data</span></span>

<span data-ttu-id="fa472-108">다음 메서드를 사용 하 여 현재 세션에 형식 지정 파일을 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-108">Formatting files can be loaded into the current session using the following methods:</span></span>

- <span data-ttu-id="fa472-109">명령줄에서 현재 세션으로 형식 지정 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-109">You can import the formatting file into the current session from the command line.</span></span> <span data-ttu-id="fa472-110">사용 된 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 다음 절차에 설명 된 대로 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa472-110">Use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet as described in the following procedure.</span></span>

- <span data-ttu-id="fa472-111">서식 파일을 참조 하는 모듈 매니페스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-111">You can create a module manifest that references your formatting file.</span></span> <span data-ttu-id="fa472-112">모듈을 사용 하면 배포에 대 한 파일 서식 지정 하면 패키지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-112">Modules allow you to package you formatting files for distribution.</span></span> <span data-ttu-id="fa472-113">사용 합니다 [New-modulemanifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) 매니페스트를 만드는 cmdlet 및 [Import-module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) 현재 세션으로 모듈을 로드 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-113">Use the [New-ModuleManifest](/powershell/module/Microsoft.PowerShell.Core/New-ModuleManifest) cmdlet to create the manifest, and the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet to load the module into the current session.</span></span> <span data-ttu-id="fa472-114">모듈에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-114">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="fa472-115">서식 파일을 참조 하는 스냅인 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-115">You can create a snap-in that references your formatting file.</span></span> <span data-ttu-id="fa472-116">사용 된 [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) 서식 파일을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-116">Use the [System.Management.Automation.PSSnapIn.Formats](/dotnet/api/System.Management.Automation.PSSnapIn.Formats) to reference your formatting files.</span></span> <span data-ttu-id="fa472-117">것 배포용 패키지 cmdlet 모듈 및 모든 관련 형식 및 형식 파일을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-117">It is strongly encouraged to use modules to package cmdlets, and any associated formatting and types files for distribution.</span></span> <span data-ttu-id="fa472-118">모듈에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 모듈 작성](../module/writing-a-windows-powershell-module.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-118">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- <span data-ttu-id="fa472-119">호출 하는 경우 명령을 프로그래밍 방식으로, 여기서 명령이 실행 되는 초기 세션 상태 runspace에 형식 지정 파일 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-119">If you are invoking commands programmatically, you can add a formatting file entry to the initial session state of the runspace where the commands are run.</span></span> <span data-ttu-id="fa472-120">서식 파일을 추가 하는 데 사용 되는.NET 형식에 대 한 자세한 내용은 참조는 [System.Management.Automation.Runspaces.Sessionstateformatentry? Displayproperty =](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-120">For more information about .NET type used to add the formatting file, see the [System.Management.Automation.Runspaces.Sessionstateformatentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateFormatEntry) class.</span></span>

<span data-ttu-id="fa472-121">형식 지정 파일 로드 되 면 추가 됩니다 내부 목록에 Windows PowerShell 명령줄에서 개체를 표시할 때 사용 하는 뷰를 확인 하는.</span><span class="sxs-lookup"><span data-stu-id="fa472-121">When a formatting file is loaded, it is added to an internal list that Windows PowerShell uses to determine which view to use when displaying objects at the command line.</span></span> <span data-ttu-id="fa472-122">목록의 시작 부분에 형식 지정 파일을 앞 수 또는 목록 끝에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-122">You can prepend your formatting file to the beginning of the list, or you can append it to the end of the list.</span></span> <span data-ttu-id="fa472-123">서식 파일에이 목록에 추가 되는 위치를 파악 하는 것이 중요 Windows PowerShell 핵심 cmdlet에서 반환 되는 개체는 어떻게 변경 하려는 경우 같은 정의 된 기존 뷰를 포함 하는 개체에 대 한 뷰를 정의 하는 서식 파일을 로드 하는 경우  표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-123">Knowing where your formatting file is added to this list is important if you are loading formatting file that defines a view for an object that has an existing view defined, such as when you want to change how an object that is returned by a Windows PowerShell core cmdlet is displayed.</span></span> <span data-ttu-id="fa472-124">개체에 대 한 전용 뷰를 정의 하는 서식 파일을 로드 하는 경우에 앞에서 설명한 방법 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-124">If you are loading a formatting file that defines the only view for an object, you can use any of the methods described previously.</span></span>  <span data-ttu-id="fa472-125">개체에 대 한 다른 뷰를 정의 하는 서식 파일을 로드 하는 경우 사용 해야 합니다 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet 및 목록의 시작 부분에 대 한 파일 앞에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-125">If you are loading a formatting file that defines another view for an object, you must use the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet and prepend your file to the beginning of the list.</span></span>

## <a name="storing-your-formatting-file"></a><span data-ttu-id="fa472-126">서식 파일에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-126">Storing Your Formatting File</span></span>

<span data-ttu-id="fa472-127">서식 파일은 디스크에 저장 하는 것에 대 한 사항은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-127">There is no requirement for where your formatting files are stored on disk.</span></span> <span data-ttu-id="fa472-128">그러나으로 다음 폴더에 저장 하는 것이 좋습니다 강력한: `user\documents\windowspowershell\`</span><span class="sxs-lookup"><span data-stu-id="fa472-128">However, it is strongly suggested that you store them in the following folder: `user\documents\windowspowershell\`</span></span>

#### <a name="loading-a-format-file-using-import-formatdata"></a><span data-ttu-id="fa472-129">가져오기-FormatData를 사용 하 여 서식 파일 로드</span><span class="sxs-lookup"><span data-stu-id="fa472-129">Loading a format file using Import-FormatData</span></span>

1. <span data-ttu-id="fa472-130">디스크에 대 한 서식 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-130">Store your formatting file to disk.</span></span>

2. <span data-ttu-id="fa472-131">실행 합니다 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) 다음 명령 중 하나를 사용 하 여 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fa472-131">Run the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet using one of the following commands.</span></span>

   <span data-ttu-id="fa472-132">목록 맨 앞으로는 파일 형식을 추가 하려면이 명령을 사용 하 여 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-132">To add your formatting file to the front of the list use this command.</span></span> <span data-ttu-id="fa472-133">개체로 표시 되는 방식을 변경 하는 경우이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-133">Use this command if you are changing how an object is displayed.</span></span>

   ```powershell
   Update-FormatData -PrependPath PathToFormattingFile
   ```

   <span data-ttu-id="fa472-134">형식을 추가 하려면 목록의 끝에는 파일에는이 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-134">To add your formatting file to the end of the list use this command.</span></span>

   ```powershell
   Update-FormatData -AppendPath PathToFormattingFile
   ```

   <span data-ttu-id="fa472-135">사용 하 여 파일을 추가 하는 [Update-formatdata](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet을 제거할 수 없습니다 파일 목록에서 세션이 열려 있는 동안.</span><span class="sxs-lookup"><span data-stu-id="fa472-135">Once you have added a file using the [Update-FormatData](/powershell/module/Microsoft.PowerShell.Utility/Update-FormatData) cmdlet, you cannot remove the file from the list while the session is open.</span></span> <span data-ttu-id="fa472-136">목록에서 서식 파일을 제거 하려면 세션을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-136">You must close the session to remove the formatting file from the list.</span></span>

## <a name="exporting-format-data"></a><span data-ttu-id="fa472-137">내보내기 형식 데이터</span><span class="sxs-lookup"><span data-stu-id="fa472-137">Exporting format data</span></span>

<span data-ttu-id="fa472-138">여기에 지정 된 섹션 본문을 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa472-138">Insert section body here.</span></span>
