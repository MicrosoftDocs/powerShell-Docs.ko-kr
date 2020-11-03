---
description: 콘솔 프롬프트에서 PowerShell에서 입력을 읽는 방법을 사용자 지정 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/04/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_psconsolehostreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSConsoleHostReadLine
ms.openlocfilehash: 3c5f629471ce2a4315e3e90f2baec86dfda1506b
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224946"
---
# <a name="about_psconsolehostreadline"></a><span data-ttu-id="1f96d-104">about_PSConsoleHostReadLine</span><span class="sxs-lookup"><span data-stu-id="1f96d-104">about_PSConsoleHostReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="1f96d-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="1f96d-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="1f96d-106">콘솔 프롬프트에서 PowerShell에서 입력을 읽는 방법을 사용자 지정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-106">Explains how to create a customize how PowerShell reads input at the console prompt.</span></span>

## <a name="long-description"></a><span data-ttu-id="1f96d-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="1f96d-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="1f96d-108">Windows PowerShell V3부터 콘솔 입력이 처리 되는 기본 방법을 재정의 하는 PSConsoleHostReadLine 라는 함수를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-108">Starting in Windows PowerShell V3, you can write a function named PSConsoleHostReadLine that overrides the default way that console input is processed.</span></span>

### <a name="examples"></a><span data-ttu-id="1f96d-109">예제</span><span class="sxs-lookup"><span data-stu-id="1f96d-109">EXAMPLES</span></span>

<span data-ttu-id="1f96d-110">다음 예제에서는 메모장을 시작 하 고 사용자가 만드는 텍스트 파일에서 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-110">The following example launches Notepad and gets input from a text File that the user creates:</span></span>

```powershell
function PSConsoleHostReadLine
{
  $inputFile = Join-Path $env:TEMP PSConsoleHostReadLine
  Set-Content $inputFile "PS > "

  # Notepad opens. Enter your command in it, save the file, and then exit.
  notepad $inputFile | Out-Null
  $userInput = Get-Content $inputFile
  $resultingCommand = $userInput.Replace("PS >", "")
  $resultingCommand
}
```

### <a name="remarks"></a><span data-ttu-id="1f96d-111">REMARKS</span><span class="sxs-lookup"><span data-stu-id="1f96d-111">REMARKS</span></span>

<span data-ttu-id="1f96d-112">기본적으로 PowerShell은 Windows 콘솔 하위 시스템이 모든 keypresses, F7 메뉴 및 기타 입력을 처리 하는 "가공 된 모드" 라고 하는 콘솔에서 입력을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-112">By default, PowerShell reads input from the console in what is known as "Cooked Mode" -- in which the Windows console subsystem handles all the keypresses, F7 menus, and other input.</span></span> <span data-ttu-id="1f96d-113">Enter 또는 Tab 키를 누르면 Windows PowerShell에서 해당 지점까지 입력 한 텍스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-113">When you press Enter or Tab, Windows PowerShell gets the text that you have typed up to that point.</span></span> <span data-ttu-id="1f96d-114">Enter 또는 Tab 키를 누르기 전에 Ctrl + R, Ctrl + A, Ctrl + E 또는 다른 키를 눌렀음을 확인할 수 있는 방법은 없습니다. Windows PowerShell 버전 3에서 PSConsoleHostReadLine 함수는이 문제를 해결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-114">There is no way for it to know that you pressed Ctrl-R, Ctrl-A, Ctrl-E, or any other keys before pressing Enter or Tab. In Windows PowerShell version 3, the PSConsoleHostReadLine function solves this issue.</span></span> <span data-ttu-id="1f96d-115">Windows PowerShell 콘솔 호스트에서 PSConsoleHostReadline 이라는 함수를 정의 하는 경우 Windows PowerShell은 "가공 된 Mode" 입력 메커니즘 대신 해당 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f96d-115">When you define a function named PSConsoleHostReadline in the Windows PowerShell console host, Windows PowerShell calls that function instead of the "Cooked Mode" input mechanism.</span></span>

### <a name="see-also"></a><span data-ttu-id="1f96d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1f96d-116">SEE ALSO</span></span>

[<span data-ttu-id="1f96d-117">about_Prompts</span><span class="sxs-lookup"><span data-stu-id="1f96d-117">about_Prompts</span></span>](about_Prompts.md)
