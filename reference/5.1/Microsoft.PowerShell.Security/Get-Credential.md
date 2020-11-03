---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 10/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-credential?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Credential
ms.openlocfilehash: 26c4f8c8dcc1fbd56e29f55a6a8c2e6aa37a2842
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93225202"
---
# <span data-ttu-id="7f4d3-103">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="7f4d3-103">Get-Credential</span></span>

## <span data-ttu-id="7f4d3-104">개요</span><span class="sxs-lookup"><span data-stu-id="7f4d3-104">SYNOPSIS</span></span>
<span data-ttu-id="7f4d3-105">사용자 이름 및 암호를 기반으로 자격 증명 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-105">Gets a credential object based on a user name and password.</span></span>

## <span data-ttu-id="7f4d3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7f4d3-106">SYNTAX</span></span>

### <span data-ttu-id="7f4d3-107">CredentialSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="7f4d3-107">CredentialSet (Default)</span></span>

```
Get-Credential [-Credential] <PSCredential> [<CommonParameters>]
```

### <span data-ttu-id="7f4d3-108">MessageSet</span><span class="sxs-lookup"><span data-stu-id="7f4d3-108">MessageSet</span></span>

```
Get-Credential -Message <String> [[-UserName] <String>] [<CommonParameters>]
```

## <span data-ttu-id="7f4d3-109">설명</span><span class="sxs-lookup"><span data-stu-id="7f4d3-109">DESCRIPTION</span></span>

<span data-ttu-id="7f4d3-110">`Get-Credential`Cmdlet은 지정 된 사용자 이름 및 암호에 대 한 자격 증명 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-110">The `Get-Credential` cmdlet creates a credential object for a specified user name and password.</span></span> <span data-ttu-id="7f4d3-111">보안 작업에서 자격 증명 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-111">You can use the credential object in security operations.</span></span>

<span data-ttu-id="7f4d3-112">PowerShell 3.0부터 **메시지** 매개 변수를 사용 하 여 대화 상자에서 사용자 이름과 암호를 입력 하 라는 사용자 지정 메시지를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-112">Beginning in PowerShell 3.0, you can use the **Message** parameter to specify a customized message on the dialog box that prompts the user for their name and password.</span></span>

<span data-ttu-id="7f4d3-113">Cmdlet은 사용자에 게 `Get-Credential` 암호나 사용자 이름 및 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-113">The `Get-Credential` cmdlet prompts the user for a password or a user name and password.</span></span> <span data-ttu-id="7f4d3-114">기본적으로 사용자에게 입력을 요구하는 인증 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-114">By default, an authentication dialog box appears to prompt the user.</span></span> <span data-ttu-id="7f4d3-115">그러나 PowerShell 콘솔과 같은 일부 호스트 프로그램에서는 레지스트리 항목을 변경 하 여 명령줄에서 사용자에 게 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-115">However, in some host programs, such as the PowerShell console, you can prompt the user at the command line by changing a registry entry.</span></span> <span data-ttu-id="7f4d3-116">이 레지스트리 항목에 대한 자세한 내용은 설명 및 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-116">For more information about this registry entry, see the notes and examples.</span></span>

## <span data-ttu-id="7f4d3-117">예제</span><span class="sxs-lookup"><span data-stu-id="7f4d3-117">EXAMPLES</span></span>

### <span data-ttu-id="7f4d3-118">예 1</span><span class="sxs-lookup"><span data-stu-id="7f4d3-118">Example 1</span></span>

```powershell
$c = Get-Credential
```

<span data-ttu-id="7f4d3-119">이 명령은 자격 증명 개체를 가져와서 `$c` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-119">This command gets a credential object and saves it in the `$c` variable.</span></span>

<span data-ttu-id="7f4d3-120">명령을 입력하면 사용자 이름 및 암호를 요청하는 대화 상자가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-120">When you enter the command, a dialog box appears requesting a user name and password.</span></span> <span data-ttu-id="7f4d3-121">요청 된 정보를 입력 하면 cmdlet이 사용자의 자격 증명을 나타내는 **PSCredential** 개체를 만들어 변수에 저장 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-121">When you enter the requested information, the cmdlet creates a **PSCredential** object representing the credentials of the user and saves it in the `$c` variable.</span></span>

<span data-ttu-id="7f4d3-122">사용자 인증을 요청하는 cmdlet(예: **Credential** 매개 변수를 사용하는 cmdlet)의 입력으로 이 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-122">You can use the object as input to cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span> <span data-ttu-id="7f4d3-123">그러나 PowerShell과 함께 설치 되는 일부 공급자는 **Credential** 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-123">However, some providers that are installed with PowerShell do not support the **Credential** parameter.</span></span>

### <span data-ttu-id="7f4d3-124">예제 2</span><span class="sxs-lookup"><span data-stu-id="7f4d3-124">Example 2</span></span>

```powershell
$c = Get-Credential
Get-CimInstance Win32_DiskDrive -ComputerName Server01 -Credential $c
```

<span data-ttu-id="7f4d3-125">이러한 명령은 `Get-Credential` WMI(Windows Management Instrumentation) (WMI)를 사용 하 여 컴퓨터를 관리할 수 있도록 cmdlet이 반환 하는 자격 증명 개체를 사용 하 여 원격 컴퓨터에서 사용자를 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-125">These commands use a credential object that the `Get-Credential` cmdlet returns to authenticate a user on a remote computer so they can use Windows Management Instrumentation (WMI) to manage the computer.</span></span>

<span data-ttu-id="7f4d3-126">첫 번째 명령은 자격 증명 개체를 가져와서 변수에 저장 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-126">The first command gets a credential object and saves it in the `$c` variable.</span></span> <span data-ttu-id="7f4d3-127">두 번째 명령은 명령에 credential 개체를 사용 합니다 `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-127">The second command uses the credential object in a `Get-CimInstance` command.</span></span> <span data-ttu-id="7f4d3-128">이 명령은 Server01 컴퓨터의 디스크 드라이브 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-128">This command gets information about the disk drives on the Server01 computer.</span></span>

### <span data-ttu-id="7f4d3-129">예제 3</span><span class="sxs-lookup"><span data-stu-id="7f4d3-129">Example 3</span></span>

```powershell
Get-CimInstance Win32_BIOS -ComputerName Server01 -Credential (Get-Credential -Credential Domain01\User01)
```

<span data-ttu-id="7f4d3-130">이 명령은 명령에 명령을 포함 하는 방법을 보여 줍니다 `Get-Credential`  `Get-CimInstance` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-130">This command shows how to include a `Get-Credential` command in a  `Get-CimInstance` command.</span></span>

<span data-ttu-id="7f4d3-131">이 명령은 cmdlet을 사용 `Get-CimInstance` 하 여 Server01 컴퓨터의 BIOS에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-131">This command uses the `Get-CimInstance` cmdlet to get information about the BIOS on the Server01 computer.</span></span> <span data-ttu-id="7f4d3-132">**Credential** 매개 변수를 사용 하 여 사용자, Domain01\User01 및 `Get-Credential` 명령을 **credential** 매개 변수 값으로 인증 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-132">It uses the **Credential** parameter to authenticate the user, Domain01\User01, and a `Get-Credential` command as the value of the **Credential** parameter.</span></span>

### <span data-ttu-id="7f4d3-133">예제 4</span><span class="sxs-lookup"><span data-stu-id="7f4d3-133">Example 4</span></span>

```powershell
$c = Get-Credential -credential User01
$c.Username
User01
```

<span data-ttu-id="7f4d3-134">이 예제에서는 도메인 이름이 없는 사용자 이름을 포함하는 자격 증명을 만들며,</span><span class="sxs-lookup"><span data-stu-id="7f4d3-134">This example creates a credential that includes a user name without a domain name.</span></span>

<span data-ttu-id="7f4d3-135">첫 번째 명령은 사용자 이름 User01를 사용 하 여 자격 증명을 가져온 다음 변수에 저장 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-135">The first command gets a credential with the user name User01 and stores it in the `$c` variable.</span></span>
<span data-ttu-id="7f4d3-136">두 번째 명령은 생성된 자격 증명 개체의 **Username** 속성 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-136">The second command displays the value of the **Username** property of the resulting credential object.</span></span>

### <span data-ttu-id="7f4d3-137">예제 5</span><span class="sxs-lookup"><span data-stu-id="7f4d3-137">Example 5</span></span>

```powershell
$Credential = $host.ui.PromptForCredential("Need credentials", "Please enter your user name and password.", "", "NetBiosUserName")
```

<span data-ttu-id="7f4d3-138">이 명령은 **PromptForCredential** 메서드를 사용하여 사용자에게 사용자 이름과 암호를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-138">This command uses the **PromptForCredential** method to prompt the user for their user name and password.</span></span> <span data-ttu-id="7f4d3-139">이 명령은 결과 자격 증명을 변수에 저장 합니다 `$Credential` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-139">The command saves the resulting credentials in the `$Credential` variable.</span></span>

<span data-ttu-id="7f4d3-140">**PromptForCredential** 메서드를 사용 하는 대신 cmdlet을 사용할 수 `Get-Credential` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-140">The **PromptForCredential** method is an alternative to using the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7f4d3-141">**PromptForCredential** 을 사용할 경우 메시지 상자에 표시되는 설명, 메시지 및 사용자 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-141">When you use **PromptForCredential** , you can specify the caption, messages, and user name that appear in the message box.</span></span>

<span data-ttu-id="7f4d3-142">자세한 내용은 SDK의 [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-142">For more information, see the [PromptForCredential](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential) documentation in the SDK.</span></span>

### <span data-ttu-id="7f4d3-143">예제 6</span><span class="sxs-lookup"><span data-stu-id="7f4d3-143">Example 6</span></span>

```powershell
Set-ItemProperty "HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds" -Name ConsolePrompting -Value $true
```

<span data-ttu-id="7f4d3-144">이 예제에서는 대화 상자를 사용하지 않고 명령줄에서 표시되도록 레지스트리를 수정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-144">This example shows how to modify the registry so that the user is prompted at the command line, instead of by using a dialog box.</span></span>

<span data-ttu-id="7f4d3-145">이 명령은 **ConsolePrompting** 레지스트리 항목을 만들어  해당 값을 True로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-145">The command creates the **ConsolePrompting** registry entry and sets its value to True.</span></span> <span data-ttu-id="7f4d3-146">이 명령을 실행 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-146">To run this command, start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="7f4d3-147">메시지를 표시 하는 대화 상자를 사용 하려면 ConsolePrompting의 값을 false ($false)로 설정 하거나 cmdlet을 사용 하 여 `Remove-ItemProperty` 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-147">To use a dialog box for prompting, set the value of the ConsolePrompting to false ($false) or use the `Remove-ItemProperty` cmdlet to delete it.</span></span>

<span data-ttu-id="7f4d3-148">ConsolePrompting 레지스트리 항목은 PowerShell 콘솔과 같은 일부 호스트 프로그램에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-148">The ConsolePrompting registry entry works in some host programs, such as the PowerShell console.</span></span> <span data-ttu-id="7f4d3-149">일부 호스트 프로그램에서는 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-149">It might not work in all host programs.</span></span>

### <span data-ttu-id="7f4d3-150">예제 7</span><span class="sxs-lookup"><span data-stu-id="7f4d3-150">Example 7</span></span>

<span data-ttu-id="7f4d3-151">이 예제에서는 `Get-Credential` 사용자에 게 메시지를 표시 하지 않고 반환 되는 개체와 동일한 자격 증명 개체를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-151">This example shows how to create a credential object that is identical to the object that `Get-Credential` returns without prompting the user.</span></span> <span data-ttu-id="7f4d3-152">이 메서드에는 일반 텍스트 암호가 필요하며, 그에 따라 일부 기업의 보안 표준을 위반할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-152">This method requires a plain text password, which might violate the security standards in some enterprises.</span></span>

```powershell
$User = "Domain01\User01"
$PWord = ConvertTo-SecureString -String "P@sSwOrd" -AsPlainText -Force
$Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $User, $PWord
```

<span data-ttu-id="7f4d3-153">첫 번째 명령은 사용자 계정 이름을 매개 변수에 저장 합니다 `$User` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-153">The first command saves the user account name in the `$User` parameter.</span></span> <span data-ttu-id="7f4d3-154">이 값은 "도메인\사용자" 또는 "컴퓨터이름\사용자" 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-154">The value must have the "Domain\User" or "ComputerName\User" format.</span></span>

<span data-ttu-id="7f4d3-155">두 번째 명령은 cmdlet을 사용 하 여 `ConvertTo-SecureString` 일반 텍스트 암호에서 보안 문자열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-155">The second command uses the `ConvertTo-SecureString` cmdlet to create a secure string from a plain text password.</span></span> <span data-ttu-id="7f4d3-156">이 명령은 **AsPlainText** 매개 변수를 사용하여 문자열이 일반 텍스트인 것을 나타내며 **Force** 매개 변수를 사용하여 일반 텍스트를 사용할 경우 발생할 수 있는 위험을 이해하고 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-156">The command uses the **AsPlainText** parameter to indicate that the string is plain text and the **Force** parameter to confirm that you understand the risks of using plain text.</span></span>

<span data-ttu-id="7f4d3-157">세 번째 명령은 cmdlet을 사용 하 여 `New-Object` 및 변수의 값에서 **PSCredential** 개체를 만듭니다 `$User` `$PWord` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-157">The third command uses the `New-Object` cmdlet to create a **PSCredential** object from the values in the `$User` and `$PWord` variables.</span></span>

### <span data-ttu-id="7f4d3-158">예제 8</span><span class="sxs-lookup"><span data-stu-id="7f4d3-158">Example 8</span></span>

```powershell
Get-Credential -Message "Credential are required for access to the \\Server1\Scripts file share." -User Server01\PowerUser
```

```Output
PowerShell Credential Request
Credential are required for access to the \\Server1\Scripts file share.
Password for user Server01\PowerUser:
```

<span data-ttu-id="7f4d3-159">이 명령은 cmdlet의 **메시지** 및 **사용자 이름** 매개 변수를 사용 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-159">This command uses the **Message** and **UserName** parameters of the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7f4d3-160">이 명령 형식은 공유 스크립트와 함수를 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-160">This command format is designed for shared scripts and functions.</span></span> <span data-ttu-id="7f4d3-161">이런 경우, 메시지를 통해 자격 증명이 필요한 이유를 알려 주며 요청이 적합하다는 확신을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-161">In this case, the message tells the user why credentials are needed and gives them confidence that the request is legitimate.</span></span>

### <span data-ttu-id="7f4d3-162">예제 9</span><span class="sxs-lookup"><span data-stu-id="7f4d3-162">Example 9</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Get-Credential Domain01\User02}
```

```Output
PowerShell Credential Request : PowerShell Credential Request
Warning: This credential is being requested by a script or application on the SERVER01 remote computer. Enter your credentials only if you
 trust the remote computer and the application or script requesting it.

Enter your credentials.
Password for user Domain01\User02: ***************

PSComputerName     : Server01
RunspaceId         : 422bdf52-9886-4ada-ab2f-130497c6777f
PSShowComputerName : True
UserName           : Domain01\User01
Password           : System.Security.SecureString
```

<span data-ttu-id="7f4d3-163">이 명령은 Server01 원격 컴퓨터에서 자격 증명을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-163">This command gets a credential from the Server01 remote computer.</span></span> <span data-ttu-id="7f4d3-164">이 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Get-Credential` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-164">The command uses the `Invoke-Command` cmdlet to run a `Get-Credential` command on the remote computer.</span></span> <span data-ttu-id="7f4d3-165">출력에는 인증 프롬프트에가 포함 된 원격 보안 메시지가 표시 `Get-Credential` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-165">The output shows the remote security message that `Get-Credential` includes in the authentication prompt.</span></span>

## <span data-ttu-id="7f4d3-166">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="7f4d3-166">PARAMETERS</span></span>

### <span data-ttu-id="7f4d3-167">-Credential</span><span class="sxs-lookup"><span data-stu-id="7f4d3-167">-Credential</span></span>

<span data-ttu-id="7f4d3-168">**User01** 또는 **Domain01\User01** 와 같은 자격 증명의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-168">Specifies a user name for the credential, such as **User01** or **Domain01\User01**.</span></span> <span data-ttu-id="7f4d3-169">매개 변수 이름는 `-Credential` 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-169">The parameter name, `-Credential`, is optional.</span></span>

<span data-ttu-id="7f4d3-170">명령을 제출 하 고 사용자 이름을 지정 하는 경우 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-170">When you submit the command and specify a user name, you're prompted for a password.</span></span> <span data-ttu-id="7f4d3-171">이 매개 변수를 생략 하면 사용자 이름과 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-171">If you omit this parameter, you're prompted for a user name and a password.</span></span>

<span data-ttu-id="7f4d3-172">PowerShell 3.0부터 도메인 없이 사용자 이름을 입력 하는 경우는 `Get-Credential` 더 이상 이름 앞에 백슬래시를 삽입 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-172">Starting in PowerShell 3.0, if you enter a user name without a domain, `Get-Credential` no longer inserts a backslash before the name.</span></span>

<span data-ttu-id="7f4d3-173">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-173">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="7f4d3-174">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="7f4d3-174">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: CredentialSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f4d3-175">-메시지</span><span class="sxs-lookup"><span data-stu-id="7f4d3-175">-Message</span></span>

<span data-ttu-id="7f4d3-176">인증 프롬프트에 표시되는 메시지를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-176">Specifies a message that appears in the authentication prompt.</span></span> <span data-ttu-id="7f4d3-177">이 매개 변수는 함수나 스크립트에서 사용하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-177">This parameter is designed for use in a function or script.</span></span> <span data-ttu-id="7f4d3-178">메시지를 사용하여 자격 증명을 요청하는 이유와 사용자에게 설명하는 방법을 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-178">You can use the message to explain to the user why you are requesting credentials and how they will be used.</span></span>

<span data-ttu-id="7f4d3-179">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-179">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f4d3-180">-UserName</span><span class="sxs-lookup"><span data-stu-id="7f4d3-180">-UserName</span></span>

<span data-ttu-id="7f4d3-181">사용자 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-181">Specifies a user name.</span></span> <span data-ttu-id="7f4d3-182">인증 프롬프트에서 사용자 이름에 대한 암호를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-182">The authentication prompt requests a password for the user name.</span></span> <span data-ttu-id="7f4d3-183">기본적으로 사용자 이름이 비어 있으며 인증 프롬프트에서 사용자 이름과 암호를 모두 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-183">By default, the user name is blank and the authentication prompt requests both a user name and password.</span></span>

<span data-ttu-id="7f4d3-184">인증 프롬프트가 대화 상자에 나타나면 사용자가 지정된 사용자 이름을 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-184">When the authentication prompt appears in a dialog box, the user can edit the specified user name.</span></span>
<span data-ttu-id="7f4d3-185">하지만 프롬프트가 명령줄에 표시될 때에는 사용자 이름을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-185">However, the user cannot change the user name when the prompt appears at the command line.</span></span> <span data-ttu-id="7f4d3-186">공유 함수 또는 스크립트에서 이 매개 변수를 사용할 때 가능한 모든 표시 방법을 고려해보세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-186">When using this parameter in a shared function or script, consider all possible presentations.</span></span>

<span data-ttu-id="7f4d3-187">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-187">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: MessageSet
Aliases:

Required: False
Position: 1
Default value: None (blank)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7f4d3-188">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7f4d3-188">CommonParameters</span></span>

<span data-ttu-id="7f4d3-189">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-189">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7f4d3-190">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-190">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7f4d3-191">입력</span><span class="sxs-lookup"><span data-stu-id="7f4d3-191">INPUTS</span></span>

### <span data-ttu-id="7f4d3-192">없음</span><span class="sxs-lookup"><span data-stu-id="7f4d3-192">None</span></span>

<span data-ttu-id="7f4d3-193">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-193">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="7f4d3-194">출력</span><span class="sxs-lookup"><span data-stu-id="7f4d3-194">OUTPUTS</span></span>

### <span data-ttu-id="7f4d3-195">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="7f4d3-195">System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="7f4d3-196">`Get-Credential` 자격 증명 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-196">`Get-Credential` returns a credential object.</span></span>

## <span data-ttu-id="7f4d3-197">참고</span><span class="sxs-lookup"><span data-stu-id="7f4d3-197">NOTES</span></span>

<span data-ttu-id="7f4d3-198">Credential 매개 변수를 **PSCredential** 사용 하는 `Get-Credential` 것과 같이 사용자 인증을 요청 하는 Cmdlet에서 만드는 PSCredential **Credential** 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-198">You can use the **PSCredential** object that `Get-Credential` creates in cmdlets that request user authentication, such as those with a **Credential** parameter.</span></span>

<span data-ttu-id="7f4d3-199">기본적으로 인증 프롬프트가 대화 상자에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-199">By default, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="7f4d3-200">명령줄에 인증 프롬프트를 표시 하려면 **ConsolePrompting** 레지스트리 항목 ()을 추가 하 `HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting` 고 해당 값을 **True** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-200">To display the authentication prompt at the command line, add the **ConsolePrompting** registry entry (`HKLM:\SOFTWARE\Microsoft\PowerShell\1\ShellIds\ConsolePrompting`) and set its value to **True**.</span></span>
<span data-ttu-id="7f4d3-201">**ConsolePrompting** 레지스트리 항목이 존재하지 않거나 해당 값이 False이면 인증 프롬프트가 대화 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-201">If the **ConsolePrompting** registry entry does not exist or if its value is False, the authentication prompt appears in a dialog box.</span></span> <span data-ttu-id="7f4d3-202">지침에 대해서는 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-202">For instructions, see the examples.</span></span>

<span data-ttu-id="7f4d3-203">**ConsolePrompting** 레지스트리 항목은 PowerShell 콘솔에서 작동 하지만 일부 호스트 프로그램에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-203">The **ConsolePrompting** registry entry works in the PowerShell console, but it does not work in all host programs.</span></span>

<span data-ttu-id="7f4d3-204">예를 들어 PowerShell ISE (통합 스크립팅 환경)에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-204">For example, it has no effect in the PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="7f4d3-205">**ConsolePrompting** 레지스트리 항목의 효과에 대해서는 호스트 프로그램에 대한 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-205">For information about the effect of the **ConsolePrompting** registry entry, see the help topics for the host program.</span></span>

<span data-ttu-id="7f4d3-206">**Credential** 매개 변수는 PowerShell과 함께 설치 된 모든 공급자에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d3-206">The **Credential** parameter is not supported by all providers that are installed with PowerShell.</span></span>
<span data-ttu-id="7f4d3-207">PowerShell 3.0부터 및 cmdlet과 같은 select cmdlet에서 지원 됩니다 `Get-Content` `New-PSDrive` .</span><span class="sxs-lookup"><span data-stu-id="7f4d3-207">Beginning in PowerShell 3.0, it is supported on select cmdlets, such as the `Get-Content` and `New-PSDrive` cmdlets.</span></span>

## <span data-ttu-id="7f4d3-208">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7f4d3-208">RELATED LINKS</span></span>

[<span data-ttu-id="7f4d3-209">PromptForCredential</span><span class="sxs-lookup"><span data-stu-id="7f4d3-209">PromptForCredential</span></span>](/dotnet/api/system.management.automation.host.pshostuserinterface.promptforcredential)
