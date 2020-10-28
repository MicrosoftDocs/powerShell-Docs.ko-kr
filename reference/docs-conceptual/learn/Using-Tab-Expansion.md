---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: 탭 확장 사용
description: PowerShell에서 탭 확장 기능을 사용하는 방법을 설명합니다.
ms.openlocfilehash: d3408aac8cc9325666082577a7b00bc3362bfca3
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500048"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="fd523-104">탭 확장 사용</span><span class="sxs-lookup"><span data-stu-id="fd523-104">Using Tab Expansion</span></span>

<span data-ttu-id="fd523-105">명령줄 셸은 종종 긴 파일 또는 명령의 이름을 자동으로 완성하는 기능을 제공하여 명령 입력 시간을 단축하고 힌트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-105">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing hints.</span></span> <span data-ttu-id="fd523-106">PowerShell에서는 <kbd>Tab</kbd> 키를 눌러 파일 이름과 cmdlet 이름을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-106">PowerShell allows you to fill in file names and cmdlet names by pressing the <kbd>Tab</kbd> key.</span></span>

> [!NOTE]
> <span data-ttu-id="fd523-107">탭 확장은 내부 함수인 TabExpansion 또는 TabExpansion2에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-107">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="fd523-108">이 함수는 수정 또는 재정의가 가능하므로 이 설명서에서는 기본 PowerShell 구성의 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-108">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="fd523-109">사용 가능한 선택 항목으로 파일 이름이나 경로를 채우려면 이름의 일부를 입력한 다음 <kbd>Tab</kbd> 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-109">To fill in a filename or path from the available choices automatically, type part of the name and press the <kbd>Tab</kbd> key.</span></span> <span data-ttu-id="fd523-110">PowerShell은 첫 번째로 찾은 일치 항목으로 이름을 자동 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-110">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="fd523-111"><kbd>Tab</kbd> 키를 반복해서 누르면 사용 가능한 모든 선택 항목이 번갈아 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-111">Pressing the <kbd>Tab</kbd> key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="fd523-112">cmdlet 이름의 탭 확장은 약간 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-112">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="fd523-113">cmdlet 이름에 대해 탭 확장을 사용하려면 이름의 첫 번째 부분(즉, 동사) 전체와 하이픈을 차례로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-113">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="fd523-114">그러면 부분 일치를 위해 더 많은 이름을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-114">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="fd523-115">예를 들어 `get-co`를 입력한 다음, <kbd>Tab</kbd> 키를 누르면 PowerShell이 이를 자동으로 `Get-Command` cmdlet으로 확장합니다(이때 문자의 대/소문자도 표준 형식으로 변경됨).</span><span class="sxs-lookup"><span data-stu-id="fd523-115">For example, if you type `get-co` and then press the <kbd>Tab</kbd> key, PowerShell will automatically expand this to the `Get-Command` cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="fd523-116"><kbd>Tab</kbd> 키를 다시 누르면, PowerShell은 일치하는 유일한 다른 cmdlet 이름인 `Get-Content`로 이 cmdlet을 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-116">If you press <kbd>Tab</kbd> key again, PowerShell replaces this with the only other matching cmdlet name, `Get-Content`.</span></span>

<span data-ttu-id="fd523-117">탭 확장은 동일한 줄에서 반복해서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-117">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="fd523-118">예를 들어 다음을 입력하여 `Get-Content` cmdlet의 이름에 대해 탭 확장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-118">For example, you can use tab expansion on the name of the `Get-Content` cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="fd523-119"><kbd>Tab</kbd> 키를 누르면 이 명령이 다음과 같이 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-119">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="fd523-120">그러면 다음과 같이 Active Setup 로그 파일의 경로를 일부만 지정하고 다시 탭 확장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-120">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="fd523-121"><kbd>Tab</kbd> 키를 누르면 이 명령이 다음과 같이 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-121">When you press the <kbd>Tab</kbd> key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="fd523-122">탭 확장 프로세스의 유일한 제한 사항은 탭이 항상 단어를 완성하려는 시도로 해석된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-122">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="fd523-123">따라서 명령 예제를 복사하여 PowerShell 콘솔에 붙여 넣을 경우 명령 예제에 탭이 포함되지 않도록 해야 합니다. 명령 예제에 탭이 포함되어 있으면 예측할 수 없는 결과가 발생하고 대부분 의도한 대로 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd523-123">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>
