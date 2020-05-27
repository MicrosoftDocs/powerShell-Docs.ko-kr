---
ms.date: 12/31/2019
keywords: powershell,cmdlet
title: ISEFileCollection 개체
ms.openlocfilehash: 4192afa9dc91d9ea4c4c084d3ba0175483620229
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809339"
---
# <a name="the-isefilecollection-object"></a><span data-ttu-id="cefe8-103">ISEFileCollection 개체</span><span class="sxs-lookup"><span data-stu-id="cefe8-103">The ISEFileCollection Object</span></span>

<span data-ttu-id="cefe8-104">**ISEFileCollection** 개체는 **ISEFile** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-104">The **ISEFileCollection** object is a collection of **ISEFile** objects.</span></span> <span data-ttu-id="cefe8-105">`$psISE.CurrentPowerShellTab.Files` 컬렉션을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-105">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="cefe8-106">메서드</span><span class="sxs-lookup"><span data-stu-id="cefe8-106">Methods</span></span>

### <a name="add-fullpath-"></a><span data-ttu-id="cefe8-107">Add\( \[FullPath\] \)</span><span class="sxs-lookup"><span data-stu-id="cefe8-107">Add\( \[FullPath\] \)</span></span>

<span data-ttu-id="cefe8-108">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cefe8-109">제목이 없는 새 파일을 만들고 반환하고 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-109">Creates and returns a new untitled file and adds it to the collection.</span></span> <span data-ttu-id="cefe8-110">새로 생성된 파일의 **IsUntitled** 속성은 `$true`입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-110">The **IsUntitled** property of the newly created file is `$true`.</span></span>

<span data-ttu-id="cefe8-111">**\[FullPath\]** – 선택적 문자열. 완전히 지정된 파일 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-111">**\[FullPath\]** - Optional string The fully specified path of the file.</span></span> <span data-ttu-id="cefe8-112">**FullPath** 매개 변수 및 상대 경로를 포함하거나, 전체 경로 대신 파일 이름을 사용하는 경우 예외가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-112">An exception is generated if you include the **FullPath** parameter and a relative path, or if you use a file name instead of the full path.</span></span>

```powershell
# Adds a new untitled file to the collection of files in the current PowerShell tab.
$newFile = $psISE.CurrentPowerShellTab.Files.Add()

# Adds a file specified by its full path to the collection of files in the current PowerShell tab.
$psISE.CurrentPowerShellTab.Files.Add("$pshome\Examples\profile.ps1")
```

### <a name="remove-file-force-"></a><span data-ttu-id="cefe8-113">Remove\( File, \[Force\] \)</span><span class="sxs-lookup"><span data-stu-id="cefe8-113">Remove\( File, \[Force\] \)</span></span>

<span data-ttu-id="cefe8-114">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cefe8-115">현재 PowerShell 탭에서 지정된 파일을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-115">Removes a specified file from the current PowerShell tab.</span></span>

<span data-ttu-id="cefe8-116">**File** – 문자열. 컬렉션에서 제거하려는 ISEFile 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-116">**File** - String The ISEFile file that you want to remove from the collection.</span></span> <span data-ttu-id="cefe8-117">파일이 저장되지 않은 경우 이 메서드에서 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-117">If the file has not been saved, this method throws an exception.</span></span> <span data-ttu-id="cefe8-118">저장되지 않은 파일의 제거를 강제로 수행하려면 이 **Force** 스위치 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-118">Use the **Force** switch parameter to force the removal of an unsaved file.</span></span>

<span data-ttu-id="cefe8-119">**\[Force\]** - 선택적 부울. `$true`로 설정된 경우, 마지막 사용 후 저장하지 않았더라도 파일을 제거할 수 있는 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-119">**\[Force\]** - optional Boolean If set to `$true`, grants permission to remove the file even if it has not been saved after last use.</span></span> <span data-ttu-id="cefe8-120">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-120">The default is `$false`.</span></span>

```powershell
# Removes the first opened file from the file collection associated with the current PowerShell tab.
# If the file has not yet been saved, then an exception is generated.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile)

# Removes the first opened file from the file collection associated with the current PowerShell tab, even if it has not been saved.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.Remove($firstfile, $true)
```

### <a name="setselectedfile-selectedfile-"></a><span data-ttu-id="cefe8-121">SetSelectedFile\( selectedFile \)</span><span class="sxs-lookup"><span data-stu-id="cefe8-121">SetSelectedFile\( selectedFile \)</span></span>

<span data-ttu-id="cefe8-122">Windows PowerShell ISE 2.0 이상에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-122">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="cefe8-123">**SelectedFile** 매개 변수로 지정된 파일을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-123">Selects the file that is specified by the **SelectedFile** parameter.</span></span>

<span data-ttu-id="cefe8-124">**SelectedFile** – Microsoft.PowerShell.Host.ISE.ISEFile. 선택할 ISEFile 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="cefe8-124">**SelectedFile** - Microsoft.PowerShell.Host.ISE.ISEFile The ISEFile file that you want to select.</span></span>

```powershell
# Selects the specified file.
$firstfile = $psISE.CurrentPowerShellTab.Files[0]
$psISE.CurrentPowerShellTab.Files.SetSelectedFile($firstfile)
```

## <a name="see-also"></a><span data-ttu-id="cefe8-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cefe8-125">See Also</span></span>

- [<span data-ttu-id="cefe8-126">ISEFile 개체</span><span class="sxs-lookup"><span data-stu-id="cefe8-126">The ISEFile Object</span></span>](The-ISEFile-Object.md)
- [<span data-ttu-id="cefe8-127">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="cefe8-127">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="cefe8-128">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="cefe8-128">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
