---
description: PowerShell 세션 (PSSessions)을 설명 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 하는 방법을 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pssessions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PSSessions
ms.openlocfilehash: edc7109f3f79376ac1d348d3c3cd65e3a8d3e69c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599742"
---
# <a name="about-pssessions"></a><span data-ttu-id="95ade-103">PSSessions 정보</span><span class="sxs-lookup"><span data-stu-id="95ade-103">About PSSessions</span></span>

## <a name="short-description"></a><span data-ttu-id="95ade-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="95ade-104">Short Description</span></span>
<span data-ttu-id="95ade-105">PowerShell 세션 (PSSessions)을 설명 하 고 원격 컴퓨터에 대 한 영구 연결을 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-105">Describes PowerShell sessions (PSSessions) and explains how to establish a persistent connection to a remote computer.</span></span>

## <a name="long-description"></a><span data-ttu-id="95ade-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="95ade-106">Long Description</span></span>

<span data-ttu-id="95ade-107">원격 컴퓨터에서 PowerShell 명령을 실행 하려면 cmdlet의 **ComputerName** 매개 변수를 사용 하거나, powershell 세션 (pssession)을 만들고 pssession에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-107">To run PowerShell commands on a remote computer, you can use the **ComputerName** parameter of a cmdlet, or you can create a PowerShell session (PSSession) and run commands in the PSSession.</span></span>

<span data-ttu-id="95ade-108">PSSession을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-108">When you create a PSSession, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="95ade-109">PSSession을 사용 하 여 원격 컴퓨터에서 일련의 관련 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-109">Use a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="95ade-110">동일한 PSSession에서 실행 되는 명령은 변수, 별칭 및 함수 값과 같은 데이터를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-110">Commands that run in the same PSSession can share data, such as the values of variables, aliases, and functions.</span></span>

<span data-ttu-id="95ade-111">로컬 컴퓨터에서 PSSession을 만들고 명령을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-111">You can also create a PSSession on the local computer and run commands in it.</span></span>
<span data-ttu-id="95ade-112">로컬 PSSession은 PowerShell 원격 인프라를 사용 하 여 PSSession을 만들고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-112">A local PSSession uses the PowerShell remoting infrastructure to create and maintain the PSSession.</span></span>

<span data-ttu-id="95ade-113">Windows PowerShell 3.0부터 pssession은 생성 된 세션과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-113">Beginning in Windows PowerShell 3.0, PSSessions are independent of the sessions in which they are created.</span></span> <span data-ttu-id="95ade-114">활성 pssession은 원격 컴퓨터 (또는 원격 끝에 있는 컴퓨터 또는 연결의 "서버 쪽")에서 유지 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-114">Active PSSessions are maintained on the remote computer (or the computer at the remote end or "server-side" of the connection).</span></span> <span data-ttu-id="95ade-115">결과적으로 PSSession에서 연결을 끊고 나중에 동일한 컴퓨터 또는 다른 컴퓨터에서 다시 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-115">As a result, you can disconnect from the PSSession and reconnect to it at a later time from the same computer or from a different computer.</span></span>

<span data-ttu-id="95ade-116">이 항목에서는 pssession을 만들고 사용 하 고 가져오고 삭제 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-116">This topic explains how to create, use, get, and delete PSSessions.</span></span> <span data-ttu-id="95ade-117">자세한 내용은 [about_PSSession_Details](about_PSSession_Details.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95ade-117">For more advanced information, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

<span data-ttu-id="95ade-118">참고: PSSessions는 PowerShell 원격 인프라를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-118">Note: PSSessions use the PowerShell remoting infrastructure.</span></span> <span data-ttu-id="95ade-119">Pssession을 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-119">To use PSSessions, the local and remote computers must be configured for remoting.</span></span>
<span data-ttu-id="95ade-120">자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="95ade-120">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

<span data-ttu-id="95ade-121">Windows Vista 이상 버전에서 로컬 컴퓨터에 PSSession을 만들려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-121">In Windows Vista and later versions of Windows, to create a PSSession on a local computer, you must start PowerShell with the "Run as administrator" option.</span></span>

## <a name="what-is-a-session"></a><span data-ttu-id="95ade-122">세션 이란?</span><span class="sxs-lookup"><span data-stu-id="95ade-122">What Is a Session?</span></span>

<span data-ttu-id="95ade-123">세션은 PowerShell을 실행 하는 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-123">A session is an environment in which PowerShell runs.</span></span>

<span data-ttu-id="95ade-124">PowerShell을 시작할 때마다 세션이 만들어지고 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-124">Each time you start PowerShell, a session is created for you, and you can run commands in the session.</span></span> <span data-ttu-id="95ade-125">모듈 및 스냅인과 같은 항목을 세션에 추가 하 고 변수, 함수 및 별칭과 같은 항목을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-125">You can also add items to your session, such as modules and snap-ins, and you can create items, such as variables, functions, and aliases.</span></span> <span data-ttu-id="95ade-126">이러한 항목은 세션에만 존재 하며 세션이 종료 될 때 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-126">These items exist only in the session and are deleted when the session ends.</span></span>

<span data-ttu-id="95ade-127">로컬 컴퓨터 또는 원격 컴퓨터에서 사용자 관리 세션 ("PowerShell 세션" 또는 "PSSessions")을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-127">You can also create user-managed sessions, known as " PowerShell sessions" or "PSSessions," on the local computer or on a remote computer.</span></span> <span data-ttu-id="95ade-128">기본 세션과 마찬가지로 PSSession에서 명령을 실행 하 고 항목을 추가 하 고 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-128">Like the default session, you can run commands in a PSSession and add and create items.</span></span> <span data-ttu-id="95ade-129">그러나 자동으로 시작 되는 세션과 달리 사용자가 만든 pssession을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-129">However, unlike the session that starts automatically, you can control the PSSessions that you create.</span></span> <span data-ttu-id="95ade-130">이러한 항목을 가져오고, 만들고, 구성 하 고, 제거 하 고, 연결을 끊고 다시 연결 하 고, 동일한 PSSession에서 여러 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-130">You can get, create, configure, and remove them, disconnect and reconnect to them, and run multiple commands in the same PSSession.</span></span> <span data-ttu-id="95ade-131">PSSession을 삭제 하거나 시간 초과가 발생할 때까지 PSSession을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-131">The PSSession remains available until you delete it or it times out.</span></span>

<span data-ttu-id="95ade-132">일반적으로 원격 컴퓨터에서 일련의 관련 명령을 실행 하려면 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-132">Typically, you create a PSSession to run a series of related commands on a remote computer.</span></span> <span data-ttu-id="95ade-133">원격 컴퓨터에서 PSSession을 만들 때 PowerShell은 세션을 지원 하기 위해 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-133">When you create a PSSession on a remote computer, PowerShell establishes a persistent connection to the remote computer to support the session.</span></span>

<span data-ttu-id="95ade-134">또는 cmdlet의 **ComputerName** 매개 변수를 사용 하 여 `Invoke-Command` `Enter-PSSession` 원격 명령을 실행 하거나 대화형 세션을 시작 하는 경우 PowerShell은 원격 컴퓨터에 임시 세션을 만들고 명령이 완료 되는 즉시 또는 대화형 세션이 종료 되는 즉시 세션을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-134">If you use the **ComputerName** parameter of the `Invoke-Command` or `Enter-PSSession` cmdlet to run a remote command or to start an interactive session, PowerShell creates a temporary session on the remote computer and closes the session as soon as the command is complete or as soon as the interactive session ends.</span></span> <span data-ttu-id="95ade-135">이러한 임시 세션은 제어할 수 없으며 단일 명령 또는 단일 대화형 세션에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-135">You cannot control these temporary sessions, and you cannot use them for more than a single command or a single interactive session.</span></span>

<span data-ttu-id="95ade-136">PowerShell에서 "현재 세션"은 작업 중인 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-136">In PowerShell, the "current session" is the session that you are working in.</span></span> <span data-ttu-id="95ade-137">"현재 세션"은 임시 세션이 나 PSSession을 비롯 한 모든 세션을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-137">The "current session" can refer to any session, including a temporary session or a PSSession.</span></span>

## <a name="why-use-a-pssession"></a><span data-ttu-id="95ade-138">PSSession을 사용 하는 이유</span><span class="sxs-lookup"><span data-stu-id="95ade-138">Why Use a PSSession?</span></span>

<span data-ttu-id="95ade-139">원격 컴퓨터에 대 한 영구 연결이 필요한 경우 PSSession을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-139">Use a PSSession when you need a persistent connection to a remote computer.</span></span>
<span data-ttu-id="95ade-140">PSSession을 사용 하 여 변수 값, 함수의 내용 또는 별칭 정의와 같은 데이터를 공유 하는 일련의 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-140">With a PSSession, you can run a series of commands that share data, such as the value of variables, the contents of a function, or the definition of an alias.</span></span>

<span data-ttu-id="95ade-141">PSSession을 만들지 않고 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-141">You can run remote commands without creating a PSSession.</span></span> <span data-ttu-id="95ade-142">원격 지원 cmdlet의 **ComputerName** 매개 변수를 사용 하 여 하나 이상의 컴퓨터에서 단일 명령이 나 일련의 관련 되지 않은 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-142">Use the **ComputerName** parameter of remote-enabled cmdlets to run a single command or a series of unrelated commands on one or many computers.</span></span>

<span data-ttu-id="95ade-143">또는의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` PowerShell은 `Enter-PSSession` 원격 컴퓨터에 대 한 임시 연결을 설정한 다음 명령이 완료 되는 즉시 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-143">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection to the remote computer and then closes the connection as soon as the command is complete.</span></span> <span data-ttu-id="95ade-144">연결을 닫을 때 사용자가 만드는 모든 데이터 요소가 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-144">Any data elements that you create are lost when the connection is closed.</span></span>

<span data-ttu-id="95ade-145">**ComputerName** 매개 변수가 있는 다른 cmdlet (예: 및)은 `Get-Eventlog` 다양 한 `Get-WmiObject` 원격 기술을 사용 하 여 데이터를 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-145">Other cmdlets that have a **ComputerName** parameter, such as `Get-Eventlog` and `Get-WmiObject`, use different remoting technologies to gather data.</span></span> <span data-ttu-id="95ade-146">없음 PSSession과 같은 영구 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-146">None create a persistent connection like a PSSession.</span></span>

## <a name="how-to-create-a-pssession"></a><span data-ttu-id="95ade-147">PSSession을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="95ade-147">How to Create a PSSession</span></span>

<span data-ttu-id="95ade-148">PSSession을 만들려면 cmdlet을 사용 `New-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-148">To create a PSSession, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="95ade-149">원격 컴퓨터에서 PSSession을 만들려면 cmdlet의 **ComputerName** 매개 변수를 사용 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="95ade-149">To create the PSSession on a remote computer, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="95ade-150">예를 들어 다음 명령은 Server01 컴퓨터에 새 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-150">For example, the following command creates a new PSSession on the Server01 computer.</span></span>

```powershell
New-PSSession -ComputerName Server01
```

<span data-ttu-id="95ade-151">명령을 제출할 때는 PSSession을 `New-PSSession` 만들고 pssession을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-151">When you submit the command, `New-PSSession` creates the PSSession and returns an object that represents the PSSession.</span></span> <span data-ttu-id="95ade-152">PSSession을 만들 때 개체를 변수에 저장 하거나, 명령을 사용 하 여 나중에 PSSession을 가져올 수 있습니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="95ade-152">You can save the object in a variable when you create the PSSession, or you can use a `Get-PSSession` command to get the PSSession at a later time.</span></span>

<span data-ttu-id="95ade-153">예를 들어 다음 명령은 Server01 컴퓨터에 새 PSSession을 만든 다음 결과 개체를 $ps 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-153">For example, the following command creates a new PSSession on the Server01 computer and saves the resulting object in the $ps variable.</span></span>

```powershell
$ps = New-PSSession -ComputerName Server01
```

## <a name="how-to-create-pssessions-on-multiple-computers"></a><span data-ttu-id="95ade-154">여러 컴퓨터에서 PSSessions를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="95ade-154">How to Create PSSessions on Multiple Computers</span></span>

<span data-ttu-id="95ade-155">여러 컴퓨터에서 PSSessions를 만들려면 cmdlet의 **ComputerName** 매개 변수를 사용 `New-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-155">To create PSSessions on multiple computers, use the **ComputerName** parameter of the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="95ade-156">원격 컴퓨터의 이름을 쉼표로 구분 된 목록으로 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-156">Type the names of the remote computers in a comma-separated list.</span></span>

<span data-ttu-id="95ade-157">예를 들어 Server01, Server02 및 Server03 컴퓨터에서 PSSessions를 만들려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-157">For example, to create PSSessions on the Server01, Server02, and Server03 computers, type:</span></span>

```powershell
New-PSSession -ComputerName Server01, Server02, Server03
```

<span data-ttu-id="95ade-158">`New-PSSession` 각 원격 컴퓨터에 하나의 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-158">`New-PSSession` creates one PSSession on each of the remote computers.</span></span>

## <a name="how-to-get-pssessions"></a><span data-ttu-id="95ade-159">PSSessions를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="95ade-159">How to Get PSSessions</span></span>

<span data-ttu-id="95ade-160">현재 세션에서 만들어진 pssession을 가져오려면 `Get-PSSession` **ComputerName** 매개 변수 없이 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-160">To get the PSSessions that were created in your current session, use the `Get-PSSession` cmdlet without the **ComputerName** parameter.</span></span> <span data-ttu-id="95ade-161">`Get-PSSession` 가 반환 하는 개체의 동일한 형식을 반환 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="95ade-161">`Get-PSSession` returns the same type of object that `New-PSSession` returns.</span></span>

<span data-ttu-id="95ade-162">다음 명령은 현재 세션에서 만들어진 모든 pssession을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-162">The following command gets all the PSSessions that were created in the current session.</span></span>

```powershell
Get-PSSession
```

<span data-ttu-id="95ade-163">Pssession의 기본 표시에는 ID 및 기본 표시 이름이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-163">The default display of the PSSessions shows their ID and a default display name.</span></span> <span data-ttu-id="95ade-164">세션을 만들 때 대체 표시 이름을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-164">You can assign an alternate display name when you create the session.</span></span>

```output
Id   Name       ComputerName    State    ConfigurationName
---  ----       ------------    -----    ---------------------
1    Session1   Server01        Opened   Microsoft.PowerShell
2    Session2   Server02        Opened   Microsoft.PowerShell
3    Session3   Server03        Opened   Microsoft.PowerShell
```

<span data-ttu-id="95ade-165">PSSessions를 변수에 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-165">You can also save the PSSessions in a variable.</span></span> <span data-ttu-id="95ade-166">다음 명령은 PSSessions를 가져와 \$ ps123 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-166">The following command gets the PSSessions and saves them in the \$ps123 variable.</span></span>

```powershell
$ps123 = Get-PSSession
```

<span data-ttu-id="95ade-167">PSSession cmdlet을 사용 하는 경우 해당 ID, 이름 또는 인스턴스 ID (GUID)로 PSSession을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-167">When using the PSSession cmdlets, you can refer to a PSSession by its ID, by its name, or by its instance ID (a GUID).</span></span> <span data-ttu-id="95ade-168">다음 명령은 해당 ID로 PSSession을 가져와 \$ ps01 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-168">The following command gets a PSSession by its ID and saves it in the \$ps01 variable.</span></span>

```powershell
$ps01 = Get-PSSession -Id 1
```

<span data-ttu-id="95ade-169">Windows PowerShell 3.0부터 pssession은 원격 컴퓨터에 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-169">Beginning in Windows PowerShell 3.0, PSSessions are maintained on the remote computer.</span></span> <span data-ttu-id="95ade-170">특정 원격 컴퓨터에서 만든 pssession을 가져오려면 cmdlet의 **ComputerName** 매개 변수를 사용 `Get-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-170">To get PSSessions that you created on particular remote computers, use the **ComputerName** parameter of the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="95ade-171">다음 명령은 Server01 원격 컴퓨터에서 만든 PSSessions를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-171">The following command gets the PSSessions that you created on the Server01 remote computer.</span></span> <span data-ttu-id="95ade-172">여기에는 현재 세션에서 생성 된 pssession과 로컬 컴퓨터 또는 다른 컴퓨터의 다른 세션이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-172">This includes PSSessions created in the current session and in other sessions on the local computer or other computers.</span></span>

```powershell
Get-PSSession -ComputerName Server01
```

<span data-ttu-id="95ade-173">Windows PowerShell 2.0에서는 `Get-PSSession` 현재 세션에서 만들어진 pssession만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-173">In Windows PowerShell 2.0, `Get-PSSession` gets only the PSSessions that were created in the current session.</span></span> <span data-ttu-id="95ade-174">세션이에 연결 되어 있고 로컬 컴퓨터에서 명령을 실행 하는 경우에도 다른 세션이 나 다른 컴퓨터에서 만들어진 pssession은 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-174">It does not get PSSessions that were created in other sessions or on other computers, even if the sessions are connected to and are running commands on the local computer.</span></span>

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="95ade-175">PSSession에서 명령을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="95ade-175">How to Run Commands in a PSSession</span></span>

<span data-ttu-id="95ade-176">하나 이상의 pssession에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-176">To run a command in one or more PSSessions, use the `Invoke-Command` cmdlet.</span></span>
<span data-ttu-id="95ade-177">Session 매개 변수를 사용 하 여 PSSessions을 지정 하 고 **ScriptBlock** 매개 변수를 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-177">Use the Session parameter to specify the PSSessions and the **ScriptBlock** parameter to specify the command.</span></span>

<span data-ttu-id="95ade-178">예를 들어 `Get-ChildItem` $ps 123 변수에 저장 된 각각의 3 개의 pssession에서 ("dir") 명령을 실행 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-178">For example, to run a `Get-ChildItem` ("dir") command in each of the three PSSessions saved in the $ps123 variable, type:</span></span>

```powershell
Invoke-Command -Session $ps123 -ScriptBlock { Get-ChildItem }
```

## <a name="how-to-delete-pssessions"></a><span data-ttu-id="95ade-179">Pssession을 삭제 하는 방법</span><span class="sxs-lookup"><span data-stu-id="95ade-179">How to Delete PSSessions</span></span>

<span data-ttu-id="95ade-180">PSSession을 마친 후에는 cmdlet을 사용 하 여 `Remove-PSSession` pssession을 삭제 하 고 사용 중인 리소스를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-180">When you are finished with the PSSession, use the `Remove-PSSession` cmdlet to delete the PSSession and to release the resources that it was using.</span></span>

```powershell
Remove-PSSession -Session $ps
```

<span data-ttu-id="95ade-181">or</span><span class="sxs-lookup"><span data-stu-id="95ade-181">or</span></span>

```powershell
Remove-PSSession -Id 1
```

<span data-ttu-id="95ade-182">원격 컴퓨터에서 PSSession을 제거 하려면 cmdlet의 **ComputerName** 매개 변수를 사용 `Remove-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-182">To remove a PSSession from a remote computer, use the **ComputerName** parameter of the `Remove-PSSession` cmdlet.</span></span>

```powershell
Remove-PSSession -ComputerName Server01 -Id 1
```

<span data-ttu-id="95ade-183">PSSession을 삭제 하지 않은 경우에는 제한 시간이 초과 될 때까지 PSSession을 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-183">If you do not delete the PSSession, the PSSession remains available for use until it times out.</span></span>

<span data-ttu-id="95ade-184">또한 cmdlet의 **IdleTimeout** 매개 변수를 사용 `New-PSSessionOption` 하 여 유휴 PSSession에 대 한 만료 시간을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-184">You can also use the **IdleTimeout** parameter of the `New-PSSessionOption` cmdlet to set an expiration time for an idle PSSession.</span></span> <span data-ttu-id="95ade-185">자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95ade-185">For more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

## <a name="the-pssession-cmdlets"></a><span data-ttu-id="95ade-186">PSSession Cmdlet</span><span class="sxs-lookup"><span data-stu-id="95ade-186">The PSSession Cmdlets</span></span>

<span data-ttu-id="95ade-187">PSSession cmdlet 목록을 보려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-187">For a list of PSSession cmdlets, type:</span></span>

```powershell
Get-Help *-PSSession
```

- <span data-ttu-id="95ade-188">연결-PSSession: PSSession을 현재 세션에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-188">Connect-PSSession: Connects a PSSession to the current session</span></span>
- <span data-ttu-id="95ade-189">연결 끊기-PSSession: 현재 세션에서 PSSession의 연결을 끊습니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-189">Disconnect-PSSession: Disconnects a PSSession from the current session</span></span>
- <span data-ttu-id="95ade-190">Enter-PSSession: 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-190">Enter-PSSession: Starts an interactive session</span></span>
- <span data-ttu-id="95ade-191">종료-PSSession: 대화형 세션 종료</span><span class="sxs-lookup"><span data-stu-id="95ade-191">Exit-PSSession: Ends an interactive session</span></span>
- <span data-ttu-id="95ade-192">Get PSSession: 현재 세션의 PSSession을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-192">Get-PSSession: Gets the PSSessions in the current session</span></span>
- <span data-ttu-id="95ade-193">새-PSSession: 로컬 또는 원격 컴퓨터에 새 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-193">New-PSSession: Creates a new PSSession on a local or remote computer</span></span>
- <span data-ttu-id="95ade-194">수신 PSSession: 연결 되지 않은 세션에서 실행 된 명령의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-194">Receive-PSSession: Gets the results of commands that ran in a disconnected session</span></span>
- <span data-ttu-id="95ade-195">제거-PSSession: 현재 세션의 PSSession을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="95ade-195">Remove-PSSession: Deletes the PSSessions in the current session</span></span>

## <a name="for-more-information"></a><span data-ttu-id="95ade-196">참조 항목</span><span class="sxs-lookup"><span data-stu-id="95ade-196">For More Information</span></span>

<span data-ttu-id="95ade-197">Pssession에 대 한 자세한 내용은 [about_PSSession_Details](about_PSSession_Details.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95ade-197">For more information about PSSessions, see [about_PSSession_Details](about_PSSession_Details.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95ade-198">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95ade-198">See Also</span></span>

[<span data-ttu-id="95ade-199">about_Remote</span><span class="sxs-lookup"><span data-stu-id="95ade-199">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="95ade-200">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="95ade-200">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="95ade-201">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="95ade-201">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="95ade-202">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-202">Connect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Connect-PSSession)

[<span data-ttu-id="95ade-203">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-203">Disconnect-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Disconnect-PSSession)

[<span data-ttu-id="95ade-204">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-204">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="95ade-205">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-205">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)

[<span data-ttu-id="95ade-206">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-206">Get-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Get-PSSession)

[<span data-ttu-id="95ade-207">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="95ade-207">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="95ade-208">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-208">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

[<span data-ttu-id="95ade-209">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="95ade-209">Remove-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Remove-PSSession)
