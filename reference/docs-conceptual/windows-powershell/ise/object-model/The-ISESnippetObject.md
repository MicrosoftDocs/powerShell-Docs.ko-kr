---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippet 개체
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809579"
---
# <a name="the-isesnippetobject"></a><span data-ttu-id="14696-103">ISESnippet 개체</span><span class="sxs-lookup"><span data-stu-id="14696-103">The ISESnippetObject</span></span>

<span data-ttu-id="14696-104">**ISESnippet** 개체는 Microsoft.PowerShell.Host.ISE.ISESnippet 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-104">An **ISESnippet** object is an instance of the Microsoft.PowerShell.Host.ISE.ISESnippet class.</span></span> <span data-ttu-id="14696-105">`$psISE.CurrentPowerShellTab.Snippets` 컬렉션의 멤버는 모두 **ISESnippet** 개체의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-105">The members of the `$psISE.CurrentPowerShellTab.Snippets` collection are all examples of **ISESnippet** objects.</span></span> <span data-ttu-id="14696-106">코드 조각을 만드는 가장 쉬운 방법은 [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-106">The easiest way to create a snippet is to use the [New-IseSnippet](/powershell/module/ISE/New-IseSnippet) cmdlet.</span></span>

## <a name="properties"></a><span data-ttu-id="14696-107">속성</span><span class="sxs-lookup"><span data-stu-id="14696-107">Properties</span></span>

### <a name="author"></a><span data-ttu-id="14696-108">작성자</span><span class="sxs-lookup"><span data-stu-id="14696-108">Author</span></span>

<span data-ttu-id="14696-109">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14696-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14696-110">코드 조각 작성자의 이름을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-110">The read-only property that gets the name of the author of the snippet.</span></span>

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a><span data-ttu-id="14696-111">CodeFragment</span><span class="sxs-lookup"><span data-stu-id="14696-111">CodeFragment</span></span>

<span data-ttu-id="14696-112">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14696-112">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14696-113">편집기에 삽입할 코드 조각을 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-113">The read-only property that gets the code fragment to be inserted into the editor.</span></span>

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a><span data-ttu-id="14696-114">바로 가기</span><span class="sxs-lookup"><span data-stu-id="14696-114">Shortcut</span></span>

<span data-ttu-id="14696-115">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14696-115">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="14696-116">메뉴 항목에 대한 Windows 바로 가기 키를 가져오는 읽기 전용 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="14696-116">The read-only property that gets the Windows keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a><span data-ttu-id="14696-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="14696-117">See Also</span></span>

- [<span data-ttu-id="14696-118">ISESnippetCollection 개체</span><span class="sxs-lookup"><span data-stu-id="14696-118">The ISESnippetCollection Object</span></span>](The-ISESnippetCollection-Object.md)
- [<span data-ttu-id="14696-119">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="14696-119">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [<span data-ttu-id="14696-120">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="14696-120">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
