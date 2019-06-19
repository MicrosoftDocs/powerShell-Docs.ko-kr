---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: ISESnippetCollection 개체
ms.openlocfilehash: 6c392c08767fba004f63155d5a469777856a0b59
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030506"
---
# <a name="the-isesnippetcollection-object"></a><span data-ttu-id="51d60-103">ISESnippetCollection 개체</span><span class="sxs-lookup"><span data-stu-id="51d60-103">The ISESnippetCollection Object</span></span>

<span data-ttu-id="51d60-104">**ISESnippetCollection** 개체는 **ISESnippet** 개체의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-104">The **ISESnippetCollection** object is a collection of **ISESnippet** objects.</span></span> <span data-ttu-id="51d60-105">**PowerShellTab** 개체와 연결되어 있는 파일 컬렉션이 이 클래스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-105">The files collection that is associated with a **PowerShellTab** object is a member of this class.</span></span> <span data-ttu-id="51d60-106">예제는 **$psISE.CurrentPowerShellTab.Files** 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-106">An example is the **$psISE.CurrentPowerShellTab.Files** collection.</span></span>

## <a name="methods"></a><span data-ttu-id="51d60-107">메서드</span><span class="sxs-lookup"><span data-stu-id="51d60-107">Methods</span></span>

### <a name="load-filepathname-"></a><span data-ttu-id="51d60-108">Load\( FilePathName \)</span><span class="sxs-lookup"><span data-stu-id="51d60-108">Load\( FilePathName \)</span></span>

<span data-ttu-id="51d60-109">Windows PowerShell ISE 3.0 이상에서 지원되며, 이전 버전에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-109">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="51d60-110">사용자가 정의한 코드 조각을 포함하는 .snippets.ps1xml 파일을 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-110">Loads a .snippets.ps1xml file that contains user-defined snippets.</span></span> <span data-ttu-id="51d60-111">코드 조각을 만드는 가장 쉬운 방법은 New-IseSnippet cmdlet을 사용하는 것입니다. 이 cmdlet은 Windows PowerShell ISE를 시작할 때마다 코드 조각이 로드되도록 코드 조각을 프로필 폴더에 자동으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-111">The easiest way to create snippets is to use the New-IseSnippet cmdlet, which automatically stores them in your profile folder so that they are loaded every time that you start Windows PowerShell ISE.</span></span>

<span data-ttu-id="51d60-112">**FilePathName** – 문자열. 코드 조각 정의를 포함하는 .snippets.ps1xml 파일의 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="51d60-112">**FilePathName** - String The path and file name to a .snippets.ps1xml file that contains snippet definitions.</span></span>

```powershell
# Loads a custom snippet file into the current PowerShell tab.
$SnipFile = Join-Path ( Split-Path $profile) 'Snippets\MySnips.snippets.ps1xml' $psISE.CurrentPowerShellTab.Snippets.Add($SnipPath)
```

## <a name="see-also"></a><span data-ttu-id="51d60-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51d60-113">See Also</span></span>

- [<span data-ttu-id="51d60-114">ISESnippet 개체</span><span class="sxs-lookup"><span data-stu-id="51d60-114">The ISESnippetObject</span></span>](The-ISESnippetObject.md)
- [<span data-ttu-id="51d60-115">Windows PowerShell ISE 스크립팅 개체 모델의 용도</span><span class="sxs-lookup"><span data-stu-id="51d60-115">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="51d60-116">ISE 개체 모델 계층 구조</span><span class="sxs-lookup"><span data-stu-id="51d60-116">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
