---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: ec4ae8e4b2ef0ec226cb75607f7aaf34b48f6b76
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682938"
---
# <a name="authoring-improvements-using-powershell-ise"></a><span data-ttu-id="f54c5-102">PowerShell ISE를 사용하여 작성 기능 향상</span><span class="sxs-lookup"><span data-stu-id="f54c5-102">Authoring Improvements using PowerShell ISE</span></span>

<span data-ttu-id="f54c5-103">Windows PowerShell ISE에서는 다음과 같은 기능이 향상되어 DSC 구성을 훨씬 더 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f54c5-103">Authoring DSC configurations in Windows PowerShell ISE is much easier, thanks to the following improvements:</span></span>

- <span data-ttu-id="f54c5-104">**구성** 블록이나 **노드** 블록 내 빈 줄에 **Ctrl+Space**를 입력하여 해당 블록 내의 모든 DSC 리소스 나열</span><span class="sxs-lookup"><span data-stu-id="f54c5-104">List all DSC resources within a **configuration** block or **node** block by entering **Ctrl+Space** on a blank line within it.</span></span>
- <span data-ttu-id="f54c5-105">**열거형** 형식인 리소스 속성 자동 완성</span><span class="sxs-lookup"><span data-stu-id="f54c5-105">Automatic completion on resource properties that are of the **enumeration** type.</span></span>
- <span data-ttu-id="f54c5-106">구성에 있는 다른 리소스 인스턴스에 따라 DSC 리소스의 **DependsOn** 속성 자동 완성</span><span class="sxs-lookup"><span data-stu-id="f54c5-106">Automatic completion on the **DependsOn** property of DSC resources, based on other resource instances in the configuration.</span></span>
- <span data-ttu-id="f54c5-107">리소스 속성 값의 탭 완성 기능 향상</span><span class="sxs-lookup"><span data-stu-id="f54c5-107">Better tab completion of resource property values.</span></span>

<span data-ttu-id="f54c5-108">**참고:** Ctrl+Space를 사용하여 옵션을 나열하려면 먼저 리소스 속성 값에 대해 빈 문자열이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f54c5-108">**Note:** You must have an empty string for resource property values before you can use Ctrl+Space to list the options.</span></span> <span data-ttu-id="f54c5-109">**Tab** 키를 누르면 옵션이 차례대로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="f54c5-109">Pressing **Tab** cycles through options.</span></span>
