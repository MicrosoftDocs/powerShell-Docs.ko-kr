---
ms.date: 06/12/2017
title: WMF 5.0 제거
description: 이 문서에서는 이전 버전의 Windows에서 WMF를 제거하는 방법을 설명합니다.
ms.openlocfilehash: d8078ea918db2c1cf9a7ddd6ea8d1413b593c0ff
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660812"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="18981-103">제거 지침</span><span class="sxs-lookup"><span data-stu-id="18981-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="18981-104">명령 프롬프트 사용</span><span class="sxs-lookup"><span data-stu-id="18981-104">Using Command Prompt</span></span>

1. <span data-ttu-id="18981-105">**명령 프롬프트** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18981-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="18981-106">아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/kb/934307)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="18981-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/kb/934307) as shown below:</span></span>

<span data-ttu-id="18981-107">Windows Server 2012 R2 및 Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="18981-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="18981-108">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="18981-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="18981-109">Windows Server 2008 R2 SP1 및 Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="18981-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="18981-110">제어판 사용</span><span class="sxs-lookup"><span data-stu-id="18981-110">Using Control Panel</span></span>

1. <span data-ttu-id="18981-111">**제어판** 을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18981-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="18981-112">**프로그램** 을 연 다음 **프로그램 제거** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="18981-112">Open **Programs** , then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="18981-113">**설치된 업데이트 보기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="18981-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="18981-114">설치된 업데이트 목록에서 **Windows Management Framework 5.0** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="18981-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="18981-115">*KB3134758* , *KB3134759* 또는 *KB3134760* 에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="18981-115">This corresponds to *KB3134758* , *KB3134759* , or *KB3134760*.</span></span> <span data-ttu-id="18981-116">**제거** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="18981-116">Click **Uninstall.**</span></span>
