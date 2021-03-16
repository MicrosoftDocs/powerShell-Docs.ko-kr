---
description: PowerShell을 사용 하 여 실행 기능을 사용 하 여 파일 시스템 드라이브에서 스크립트를 실행 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_run_with_powershell?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Run_With_PowerShell
ms.openlocfilehash: 7070fa2bc8bb30e83f59e3d1193faa3a8495f109
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601469"
---
# <a name="about-run-with-powershell"></a><span data-ttu-id="7a6ae-103">PowerShell을 사용 하 여 실행 정보</span><span class="sxs-lookup"><span data-stu-id="7a6ae-103">About Run With PowerShell</span></span>

## <a name="short-description"></a><span data-ttu-id="7a6ae-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7a6ae-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="7a6ae-105">"PowerShell에서 실행" 기능을 사용 하 여 파일 시스템 드라이브에서 스크립트를 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-105">Explains how to use the "Run with PowerShell" feature to run a script from a file system drive.</span></span>

## <a name="long-description"></a><span data-ttu-id="7a6ae-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="7a6ae-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="7a6ae-107">Windows PowerShell 3.0부터 "PowerShell에서 실행" 기능을 사용 하 여 Windows 8 및 Windows Server 2012의 파일 탐색기와 이전 Windows 버전의 windows 탐색기에서 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-107">Beginning in Windows PowerShell 3.0, you can use the "Run with PowerShell" feature to run scripts from File Explorer in Windows 8 and Windows Server 2012 and from Windows Explorer in earlier versions of Windows.</span></span>

<span data-ttu-id="7a6ae-108">"PowerShell에서 실행" 기능은 필수 매개 변수가 없는 스크립트를 실행 하 고 출력을 명령 프롬프트로 반환 하지 않도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-108">The "Run with PowerShell" feature is designed to run scripts that do not have required parameters and do not return output to the command prompt.</span></span>

<span data-ttu-id="7a6ae-109">"PowerShell에서 실행" 기능을 사용 하는 경우 PowerShell 콘솔 창이 잠깐 표시 됩니다 (있는 경우).</span><span class="sxs-lookup"><span data-stu-id="7a6ae-109">When you use the "Run with PowerShell" feature, the PowerShell console window appears only briefly, if at all.</span></span> <span data-ttu-id="7a6ae-110">상호 작용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-110">You cannot interact with it.</span></span>

<span data-ttu-id="7a6ae-111">"PowerShell에서 실행" 기능을 사용 하려면 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-111">To use the "Run with PowerShell" feature:</span></span>

<span data-ttu-id="7a6ae-112">파일 탐색기 (또는 Windows 탐색기)에서 스크립트 파일 이름을 마우스 오른쪽 단추로 클릭 한 다음 "PowerShell에서 실행"을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-112">In File Explorer (or Windows Explorer), right-click the script file name and then select "Run with PowerShell".</span></span>

<span data-ttu-id="7a6ae-113">"PowerShell을 사용 하 여 실행" 기능은 바이패스 실행 정책이 있는 PowerShell 세션을 시작 하 고, 스크립트를 실행 하 고, 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-113">The "Run with PowerShell" feature starts a PowerShell session that has an execution policy of Bypass, runs the script, and closes the session.</span></span>

<span data-ttu-id="7a6ae-114">다음 형식의 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-114">It runs a command that has the following format:</span></span>

```
PowerShell.exe -File <FileName> -ExecutionPolicy Bypass
```

<span data-ttu-id="7a6ae-115">"PowerShell에서 실행"은 스크립트가 실행 되는 세션 (PowerShell 프로세스의 현재 인스턴스)에 대해서만 바이패스 실행 정책을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-115">"Run with PowerShell" sets the Bypass execution policy only for the session (the current instance of the PowerShell process) in which the script runs.</span></span>
<span data-ttu-id="7a6ae-116">이 기능은 컴퓨터 또는 사용자에 대 한 실행 정책을 변경 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-116">This feature does not change the execution policy for the computer or the user.</span></span>

<span data-ttu-id="7a6ae-117">"PowerShell에서 실행" 기능은 AllSigned 실행 정책에 의해서만 영향을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-117">The "Run with PowerShell" feature is affected only by the AllSigned execution policy.</span></span> <span data-ttu-id="7a6ae-118">AllSigned 실행 정책이 컴퓨터 또는 사용자에 게 적용 되는 경우 "PowerShell에서 실행"은 서명 된 스크립트만 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-118">If the AllSigned execution policy is effective for the computer or the user, "Run with PowerShell" runs only signed scripts.</span></span> <span data-ttu-id="7a6ae-119">"PowerShell에서 실행"은 다른 실행 정책의 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-119">"Run with PowerShell" is not affected by any other execution policy.</span></span> <span data-ttu-id="7a6ae-120">자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-120">For more information, see [about_Execution_Policies](about_Execution_Policies.md).</span></span>

<span data-ttu-id="7a6ae-121">문제 해결 참고: PowerShell을 사용 하 여 실행 명령은 실행 정책 변경을 확인 하는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a6ae-121">Troubleshooting Note: Run with PowerShell command might prompt you to confirm the execution policy change.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a6ae-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7a6ae-122">SEE ALSO</span></span>

[<span data-ttu-id="7a6ae-123">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="7a6ae-123">about_Execution_Policies</span></span>](about_Execution_Policies.md)

[<span data-ttu-id="7a6ae-124">about_Group_Policy_Settings</span><span class="sxs-lookup"><span data-stu-id="7a6ae-124">about_Group_Policy_Settings</span></span>](about_Group_Policy_Settings.md)

[<span data-ttu-id="7a6ae-125">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="7a6ae-125">about_Scripts</span></span>](about_Scripts.md)
