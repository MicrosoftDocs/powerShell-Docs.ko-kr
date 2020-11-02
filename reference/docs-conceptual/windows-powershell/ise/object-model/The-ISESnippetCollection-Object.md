---
ms.date: 12/31/2019
title: ISESnippetCollection 개체
description: ISESnippetCollection 개체는 ISESnippet 개체의 컬렉션입니다. PowerShellTab 개체와 연결되어 있는 파일 컬렉션이 이 클래스의 멤버입니다.
ms.openlocfilehash: e6170ddf72d5ead840aa3015d4de1dcb21dbfeff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655982"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="9c8ee-104">ISESnippetCollection 개체</span><span class="sxs-lookup"><span data-stu-id="9c8ee-104">The ISESnippetCollection Object</span></span>

<span data-ttu-id="9c8ee-105">**ISESnippetCollection** 개체는 **ISESnippet** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-105">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="9c8ee-106">**PowerShellTab** 개체와 연결되어 있는 파일 컬렉션이 이 클래스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-106">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="9c8ee-107">`$psISE.CurrentPowerShellTab.Files` 컬렉션을 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-107">An example is the `$psISE.CurrentPowerShellTab.Files` collection.</span></span>

## <a name="methods"></a><span data-ttu-id="9c8ee-108">메서드</span><span class="sxs-lookup"><span data-stu-id="9c8ee-108">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="9c8ee-109">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="9c8ee-109">Load\( FilePathName \)</span></span>

<span data-ttu-id="9c8ee-110">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-110">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="9c8ee-111">사용자가 정의한 코드 조각을 포함하는 `.snippets.ps1xml` 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-111">Loads a `.snippets.ps1xml` file that contains user-defined snippets.</span></span> <span data-ttu-id="9c8ee-112">코드 조각을 만드는 가장 쉬운 방법은 `New-IseSnippet` cmdlet을 사용하는 것입니다. 이 cmdlet은 Windows PowerShell ISE를 시작할 때마다 코드 조각이 로드되도록 코드 조각을 프로필 폴더에 자동으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-112">The easiest way to create snippets is to use the `New-IseSnippet` cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="9c8ee-113">**FilePathName** – 문자열. 코드 조각 정의를 포함하는 .snippets.ps1xml 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9c8ee-113">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="9c8ee-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c8ee-114">See Also</span></span>

- [<span data-ttu-id="9c8ee-115">ISESnippet 개체</span><span class="sxs-lookup"><span data-stu-id="9c8ee-115">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="9c8ee-116">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="9c8ee-116">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="9c8ee-117">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="9c8ee-117">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
