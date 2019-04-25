---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 385bb7223b19c8ace8088ba469e543721a527b99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057528"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="1a571-102">제거 지침</span><span class="sxs-lookup"><span data-stu-id="1a571-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="1a571-103">명령 프롬프트 사용</span><span class="sxs-lookup"><span data-stu-id="1a571-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="1a571-104">**명령 프롬프트**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="1a571-105">아래와 같이 [Windows 업데이트 독립 실행형 시작 관리자](https://support.microsoft.com/en-us/kb/934307)를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="1a571-106">Windows Server 2012 R2 및 Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="1a571-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="1a571-107">Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="1a571-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="1a571-108">Windows Server 2008 R2 SP1 및 Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="1a571-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="1a571-109">제어판 사용</span><span class="sxs-lookup"><span data-stu-id="1a571-109">Using Control Panel</span></span>
1.  <span data-ttu-id="1a571-110">**제어판**을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="1a571-111">**프로그램**을 연 다음 **프로그램 제거**를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="1a571-112">**설치된 업데이트 보기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="1a571-113">설치된 업데이트 목록에서 **Windows Management Framework 5.0**을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="1a571-114">*KB3134758*, *KB3134759* 또는 *KB3134760*에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="1a571-115">**제거**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="1a571-115">Click **Uninstall.**</span></span>
