---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-process?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Process
ms.openlocfilehash: 53c06982abcf980897c049b6f6bd0c159f2eb4b5
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524691"
---
# <span data-ttu-id="f3890-103">Start-Process</span><span class="sxs-lookup"><span data-stu-id="f3890-103">Start-Process</span></span>

## <span data-ttu-id="f3890-104">개요</span><span class="sxs-lookup"><span data-stu-id="f3890-104">SYNOPSIS</span></span>
<span data-ttu-id="f3890-105">로컬 컴퓨터에서 하나 이상의 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-105">Starts one or more processes on the local computer.</span></span>

## <span data-ttu-id="f3890-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f3890-106">SYNTAX</span></span>

### <span data-ttu-id="f3890-107">Default (기본값)</span><span class="sxs-lookup"><span data-stu-id="f3890-107">Default (Default)</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-Credential <PSCredential>]
 [-WorkingDirectory <String>] [-LoadUserProfile] [-NoNewWindow] [-PassThru]
 [-RedirectStandardError <String>] [-RedirectStandardInput <String>]
 [-RedirectStandardOutput <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-UseNewEnvironment]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f3890-108">UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="f3890-108">UseShellExecute</span></span>

```
Start-Process [-FilePath] <String> [[-ArgumentList] <String[]>] [-WorkingDirectory <String>]
 [-PassThru] [-Verb <String>] [-WindowStyle <ProcessWindowStyle>] [-Wait] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f3890-109">설명</span><span class="sxs-lookup"><span data-stu-id="f3890-109">DESCRIPTION</span></span>

<span data-ttu-id="f3890-110">`Start-Process`Cmdlet은 로컬 컴퓨터에서 하나 이상의 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-110">The `Start-Process` cmdlet starts one or more processes on the local computer.</span></span> <span data-ttu-id="f3890-111">기본적으로는 `Start-Process` 현재 프로세스에 정의 된 모든 환경 변수를 상속 하는 새 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-111">By default, `Start-Process` creates a new process that inherits all the environment variables that are defined in the current process.</span></span>

<span data-ttu-id="f3890-112">프로세스에서 실행되는 프로그램을 지정하려면 실행 파일 또는 스크립트 파일을 입력하거나 컴퓨터의 프로그램을 사용하여 열 수 있는 파일을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-112">To specify the program that runs in the process, enter an executable file or script file, or a file that can be opened by using a program on the computer.</span></span> <span data-ttu-id="f3890-113">실행 파일이 아닌 파일을 지정 하는 경우는 `Start-Process` cmdlet과 유사 하 게 파일과 연결 된 프로그램을 시작 합니다 `Invoke-Item` .</span><span class="sxs-lookup"><span data-stu-id="f3890-113">If you specify a non-executable file, `Start-Process` starts the program that is associated with the file, similar to the `Invoke-Item` cmdlet.</span></span>

<span data-ttu-id="f3890-114">의 매개 변수를 사용 `Start-Process` 하 여 사용자 프로필을 로드 하거나 새 창에서 프로세스를 시작 하거나 대체 자격 증명을 사용 하는 등의 옵션을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-114">You can use the parameters of `Start-Process` to specify options, such as loading a user profile, starting the process in a new window, or using alternate credentials.</span></span>

## <span data-ttu-id="f3890-115">예제</span><span class="sxs-lookup"><span data-stu-id="f3890-115">EXAMPLES</span></span>

### <span data-ttu-id="f3890-116">예제 1: 기본값을 사용 하는 프로세스 시작</span><span class="sxs-lookup"><span data-stu-id="f3890-116">Example 1: Start a process that uses default values</span></span>

<span data-ttu-id="f3890-117">이 예에서는 현재 폴더에 있는 파일을 사용 하는 프로세스를 시작 `Sort.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-117">This example starts a process that uses the `Sort.exe` file in the current folder.</span></span> <span data-ttu-id="f3890-118">이 명령은 기본 창 스타일, 작업 폴더 및 자격 증명을 비롯 한 모든 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-118">The command uses all of the default values, including the default window style, working folder, and credentials.</span></span>

```powershell
Start-Process -FilePath "sort.exe"
```

### <span data-ttu-id="f3890-119">예제 2: 텍스트 파일 인쇄</span><span class="sxs-lookup"><span data-stu-id="f3890-119">Example 2: Print a text file</span></span>

<span data-ttu-id="f3890-120">이 예제에서는 파일을 인쇄 하는 프로세스를 시작 `C:\PS-Test\MyFile.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-120">This example starts a process that prints the `C:\PS-Test\MyFile.txt` file.</span></span>

```powershell
Start-Process -FilePath "myfile.txt" -WorkingDirectory "C:\PS-Test" -Verb Print
```

### <span data-ttu-id="f3890-121">예 3: 새 파일에 항목을 정렬 하는 프로세스 시작</span><span class="sxs-lookup"><span data-stu-id="f3890-121">Example 3: Start a process to sort items to a new file</span></span>

<span data-ttu-id="f3890-122">이 예제에서는 파일의 항목을 정렬 하 `Testsort.txt` 고 정렬 된 항목을 파일에 반환 하는 프로세스를 시작 `Sorted.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-122">This example starts a process that sorts items in the `Testsort.txt` file and returns the sorted items in the `Sorted.txt` files.</span></span> <span data-ttu-id="f3890-123">모든 오류는 파일에 기록 됩니다 `SortError.txt` .</span><span class="sxs-lookup"><span data-stu-id="f3890-123">Any errors are written to the `SortError.txt` file.</span></span>

```powershell
Start-Process -FilePath "Sort.exe" -RedirectStandardInput "Testsort.txt" -RedirectStandardOutput "Sorted.txt" -RedirectStandardError "SortError.txt" -UseNewEnvironment
```

<span data-ttu-id="f3890-124">**UseNewEnvironment** 매개 변수는 프로세스가 고유한 환경 변수를 사용 하 여 실행 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-124">The **UseNewEnvironment** parameter specifies that the process runs with its own environment variables.</span></span>

### <span data-ttu-id="f3890-125">예제 4: 최대화 된 창에서 프로세스 시작</span><span class="sxs-lookup"><span data-stu-id="f3890-125">Example 4: Start a process in a maximized window</span></span>

<span data-ttu-id="f3890-126">이 예제에서는 프로세스를 시작 `Notepad.exe` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-126">This example starts the `Notepad.exe` process.</span></span> <span data-ttu-id="f3890-127">창을 최대화하고 프로세스가 완료될 때까지 창을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-127">It maximizes the window and retains the window until the process completes.</span></span>

```powershell
Start-Process -FilePath "notepad" -Wait -WindowStyle Maximized
```

### <span data-ttu-id="f3890-128">예 5: 관리자 권한으로 PowerShell 시작</span><span class="sxs-lookup"><span data-stu-id="f3890-128">Example 5: Start PowerShell as an administrator</span></span>

<span data-ttu-id="f3890-129">이 예에서는 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-129">This example starts PowerShell by using the **Run as administrator** option.</span></span>

```powershell
Start-Process -FilePath "powershell" -Verb RunAs
```

### <span data-ttu-id="f3890-130">예제 6: 다른 동사를 사용 하 여 프로세스 시작</span><span class="sxs-lookup"><span data-stu-id="f3890-130">Example 6: Using different verbs to start a process</span></span>

<span data-ttu-id="f3890-131">이 예제에서는 프로세스를 시작할 때 사용할 수 있는 동사를 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-131">This example shows how to find the verbs that can be used when starting a process.</span></span> <span data-ttu-id="f3890-132">사용 가능한 동사는 프로세스에서 실행 되는 파일의 파일 이름 확장명에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-132">The available verbs are determined by the filename extension of the file that runs in the process.</span></span>

```powershell
$startExe = New-Object System.Diagnostics.ProcessStartInfo -Args PowerShell.exe
$startExe.verbs
```

```Output
open
runas
runasuser
```

<span data-ttu-id="f3890-133">이 예에서는 `New-Object` 를 사용 하 여 PowerShell 프로세스에서 실행 되는 **PowerShell.exe** 에 대 한 **ProcessStartInfo** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-133">The example uses `New-Object` to create a **System.Diagnostics.ProcessStartInfo** object for **PowerShell.exe** , the file that runs in the PowerShell process.</span></span> <span data-ttu-id="f3890-134">**ProcessStartInfo** 개체의 **Verbs** 속성은에서 **Open** 및 **RunAs** 동사를 사용 `PowerShell.exe` 하거나 파일을 실행 하는 모든 프로세스를 사용할 수 있음을 보여 줍니다 `.exe` .</span><span class="sxs-lookup"><span data-stu-id="f3890-134">The **Verbs** property of the **ProcessStartInfo** object shows that you can use the **Open** and **RunAs** verbs with `PowerShell.exe`, or with any process that runs a `.exe` file.</span></span>

### <span data-ttu-id="f3890-135">예 7: 프로세스에 인수 지정</span><span class="sxs-lookup"><span data-stu-id="f3890-135">Example 7: Specifying arguments to the process</span></span>

<span data-ttu-id="f3890-136">두 명령은 모두 `dir` 폴더에 대해 명령을 실행 하 여 Windows 명령 인터프리터를 시작 합니다 `Program Files` .</span><span class="sxs-lookup"><span data-stu-id="f3890-136">Both commands start the Windows command interpreter, issuing a `dir` command on the `Program Files` folder.</span></span> <span data-ttu-id="f3890-137">이 foldername에 공백이 포함 되어 있으므로 값은 이스케이프 된 따옴표로 묶여 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-137">Because this foldername contains a space, the value needs surrounded with escaped quotes.</span></span>
<span data-ttu-id="f3890-138">첫 번째 명령은 문자열을 **Argumentlist** 로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-138">Note that the first command specifies a string as **ArgumentList**.</span></span> <span data-ttu-id="f3890-139">두 번째 명령은 문자열 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-139">The second command is a string array.</span></span>

```powershell
Start-Process -FilePath "$env:comspec" -ArgumentList "/c dir `"%systemdrive%\program files`""
Start-Process -FilePath "$env:comspec" -ArgumentList "/c","dir","`"%systemdrive%\program files`""
```

### <span data-ttu-id="f3890-140">예 8: Linux에서 분리 된 프로세스 만들기</span><span class="sxs-lookup"><span data-stu-id="f3890-140">Example 8: Create a detached process on Linux</span></span>

<span data-ttu-id="f3890-141">Windows에서 시작 하는 `Start-Process` 셸에서 독립적으로 실행 되는 독립 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-141">On Windows, `Start-Process` creates an independent process that remains running independently of the launching shell.</span></span> <span data-ttu-id="f3890-142">Windows가 아닌 플랫폼에서 새로 시작 된 프로세스는 시작 된 셸에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-142">On non-Windows platforms, the newly started process is attached to the shell that launched.</span></span> <span data-ttu-id="f3890-143">시작 셸을 닫으면 자식 프로세스가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-143">If the launching shell is closed, the child process is terminated.</span></span>

<span data-ttu-id="f3890-144">Unix와 같은 플랫폼에서 자식 프로세스가 종료 되지 않도록 하려면와 결합 하면 `Start-Process` `nohup` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-144">To avoid terminating the child process on Unix-like platforms, you can combine `Start-Process` with `nohup`.</span></span> <span data-ttu-id="f3890-145">다음 예제에서는 시작 세션을 닫은 후에도 활성 상태로 유지 되는 Linux에서 PowerShell의 백그라운드 인스턴스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-145">The following example launches a background instance of PowerShell on Linux that stays alive even after you close the launching session.</span></span> <span data-ttu-id="f3890-146">`nohup`명령은 현재 디렉터리의 파일에서 출력을 수집 합니다 `nohup.out` .</span><span class="sxs-lookup"><span data-stu-id="f3890-146">The `nohup` command collects output in file `nohup.out` in the current directory.</span></span>

```powershell
# Runs for 2 minutes and appends output to ./nohup.out
Start-Process nohup 'pwsh -noprofile -c "1..120 | % { Write-Host . -NoNewline; sleep 1 }"'
```

<span data-ttu-id="f3890-147">이 예제에서는 `Start-Process` 가 분리 된 프로세스로 시작 하는 Linux 명령을 실행 하 고 `nohup` `pwsh` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-147">In this example, `Start-Process` is running the Linux `nohup` command, which launches `pwsh` as a detached process.</span></span> <span data-ttu-id="f3890-148">자세한 내용은 [nohup](https://linux.die.net/man/1/nohup)의 man 페이지를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-148">For more information, see the man page for [nohup](https://linux.die.net/man/1/nohup).</span></span>

## <span data-ttu-id="f3890-149">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f3890-149">PARAMETERS</span></span>

### <span data-ttu-id="f3890-150">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="f3890-150">-ArgumentList</span></span>

<span data-ttu-id="f3890-151">이 cmdlet이 프로세스를 시작할 때 사용할 매개 변수 또는 매개 변수 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-151">Specifies parameters or parameter values to use when this cmdlet starts the process.</span></span> <span data-ttu-id="f3890-152">인수를 공백으로 구분 하는 단일 문자열이 나 쉼표로 구분 된 문자열 배열로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-152">Arguments can be accepted as a single string with the arguments separated by spaces, or as an array of strings separated by commas.</span></span>

<span data-ttu-id="f3890-153">매개 변수 또는 매개 변수 값에 공백이 있는 경우 이스케이프 된 큰따옴표로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-153">If parameters or parameter values contain a space, they need to be surrounded with escaped double quotes.</span></span> <span data-ttu-id="f3890-154">자세한 내용은 [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-154">For more information, see [about_Quoting_Rules](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="f3890-155">-Credential</span></span>

<span data-ttu-id="f3890-156">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-156">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="f3890-157">기본적으로 이 cmdlet은 현재 사용자의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-157">By default, the cmdlet uses the credentials of the current user.</span></span>

<span data-ttu-id="f3890-158">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="f3890-158">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f3890-159">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-159">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f3890-160">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-160">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f3890-161">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="f3890-161">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: Default
Aliases: RunAs

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-162">-FilePath</span><span class="sxs-lookup"><span data-stu-id="f3890-162">-FilePath</span></span>

<span data-ttu-id="f3890-163">프로세스에서 실행 되는 프로그램의 선택적 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-163">Specifies the optional path and filename of the program that runs in the process.</span></span> <span data-ttu-id="f3890-164">컴퓨터의 프로그램과 연결 된 실행 파일 또는 문서 (예: 또는 파일)의 이름을 입력 합니다 `.txt` `.doc` .</span><span class="sxs-lookup"><span data-stu-id="f3890-164">Enter the name of an executable file or of a document, such as a `.txt` or `.doc` file, that is associated with a program on the computer.</span></span> <span data-ttu-id="f3890-165">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-165">This parameter is required.</span></span>

<span data-ttu-id="f3890-166">파일 이름만 지정 하는 경우 **WorkingDirectory** 매개 변수를 사용 하 여 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-166">If you specify only a filename, use the **WorkingDirectory** parameter to specify the path.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-167">-Processmodel.loaduserprofile</span><span class="sxs-lookup"><span data-stu-id="f3890-167">-LoadUserProfile</span></span>

<span data-ttu-id="f3890-168">이 cmdlet은 `HKEY_USERS` 현재 사용자의 레지스트리 키에 저장 된 Windows 사용자 프로필을 로드 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-168">Indicates that this cmdlet loads the Windows user profile stored in the `HKEY_USERS` registry key for the current user.</span></span> <span data-ttu-id="f3890-169">Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-169">The parameter does not apply for non-Windows systems.</span></span>

<span data-ttu-id="f3890-170">이 매개 변수는 PowerShell 프로필에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-170">This parameter does not affect the PowerShell profiles.</span></span> <span data-ttu-id="f3890-171">자세한 내용은 [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-171">For more information, see [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: Lup

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-172">-NoNewWindow</span><span class="sxs-lookup"><span data-stu-id="f3890-172">-NoNewWindow</span></span>

<span data-ttu-id="f3890-173">현재 콘솔 창에서 새 프로세스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-173">Start the new process in the current console window.</span></span> <span data-ttu-id="f3890-174">기본적으로 Windows에서 PowerShell은 새 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-174">By default on Windows, PowerShell opens a new window.</span></span> <span data-ttu-id="f3890-175">비 Windows 시스템에서는 새 터미널 창이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-175">On non-Windows systems, you never get a new terminal window.</span></span>

<span data-ttu-id="f3890-176">동일한 명령에서 **Nonewwindow** 및 **system.windows.window.windowstyle** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-176">You cannot use the **NoNewWindow** and **WindowStyle** parameters in the same command.</span></span>

<span data-ttu-id="f3890-177">Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-177">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases: nnw

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-178">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f3890-178">-PassThru</span></span>

<span data-ttu-id="f3890-179">cmdlet이 시작한 각 프로세스에 대한 프로세스 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-179">Returns a process object for each process that the cmdlet started.</span></span> <span data-ttu-id="f3890-180">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-180">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-181">-RedirectStandardError</span><span class="sxs-lookup"><span data-stu-id="f3890-181">-RedirectStandardError</span></span>

<span data-ttu-id="f3890-182">파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-182">Specifies a file.</span></span> <span data-ttu-id="f3890-183">이 cmdlet은 프로세스에서 생성 된 모든 오류를 지정한 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-183">This cmdlet sends any errors generated by the process to a file that you specify.</span></span>
<span data-ttu-id="f3890-184">경로 및 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-184">Enter the path and filename.</span></span> <span data-ttu-id="f3890-185">기본적으로 오류는 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-185">By default, the errors are displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSE

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-186">-RedirectStandardInput</span><span class="sxs-lookup"><span data-stu-id="f3890-186">-RedirectStandardInput</span></span>

<span data-ttu-id="f3890-187">파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-187">Specifies a file.</span></span> <span data-ttu-id="f3890-188">이 cmdlet은 지정 된 파일에서 입력을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-188">This cmdlet reads input from the specified file.</span></span> <span data-ttu-id="f3890-189">입력 파일의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-189">Enter the path and filename of the input file.</span></span> <span data-ttu-id="f3890-190">기본적으로 프로세스는 키보드에서 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-190">By default, the process gets its input from the keyboard.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-191">-RedirectStandardOutput</span><span class="sxs-lookup"><span data-stu-id="f3890-191">-RedirectStandardOutput</span></span>

<span data-ttu-id="f3890-192">파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-192">Specifies a file.</span></span> <span data-ttu-id="f3890-193">이 cmdlet은 프로세스에서 생성 된 출력을 지정한 파일로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-193">This cmdlet sends the output generated by the process to a file that you specify.</span></span>
<span data-ttu-id="f3890-194">경로 및 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-194">Enter the path and filename.</span></span> <span data-ttu-id="f3890-195">기본적으로 출력은 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-195">By default, the output is displayed in the console.</span></span>

```yaml
Type: System.String
Parameter Sets: Default
Aliases: RSO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-196">-UseNewEnvironment</span><span class="sxs-lookup"><span data-stu-id="f3890-196">-UseNewEnvironment</span></span>

<span data-ttu-id="f3890-197">이 cmdlet이 프로세스에 대해 지정 된 새 환경 변수를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-197">Indicates that this cmdlet uses new environment variables specified for the process.</span></span> <span data-ttu-id="f3890-198">기본적으로 시작 된 프로세스는 부모 프로세스에서 상속 된 환경 변수를 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-198">By default, the started process runs with the environment variables inherited from the parent process.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Default
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-199">-동사</span><span class="sxs-lookup"><span data-stu-id="f3890-199">-Verb</span></span>

<span data-ttu-id="f3890-200">이 cmdlet이 프로세스를 시작할 때 사용할 동사를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-200">Specifies a verb to use when this cmdlet starts the process.</span></span> <span data-ttu-id="f3890-201">사용 가능한 동사는 프로세스에서 실행 되는 파일의 파일 이름 확장명에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-201">The verbs that are available are determined by the filename extension of the file that runs in the process.</span></span>

<span data-ttu-id="f3890-202">다음 표에서는 몇 가지 일반적인 프로세스 파일 형식에 대한 동사를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-202">The following table shows the verbs for some common process file types.</span></span>

| <span data-ttu-id="f3890-203">파일 형식</span><span class="sxs-lookup"><span data-stu-id="f3890-203">File type</span></span> |                <span data-ttu-id="f3890-204">동사</span><span class="sxs-lookup"><span data-stu-id="f3890-204">Verbs</span></span>                |
| --------- | ----------------------------------- |
| <span data-ttu-id="f3890-205">.cmd</span><span class="sxs-lookup"><span data-stu-id="f3890-205">.cmd</span></span>      | <span data-ttu-id="f3890-206">편집, 열기, 인쇄, 실행, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="f3890-206">Edit, Open, Print, RunAs, RunAsUser</span></span> |
| <span data-ttu-id="f3890-207">.exe</span><span class="sxs-lookup"><span data-stu-id="f3890-207">.exe</span></span>      | <span data-ttu-id="f3890-208">Open, RunAs, RunAsUser</span><span class="sxs-lookup"><span data-stu-id="f3890-208">Open, RunAs, RunAsUser</span></span>              |
| <span data-ttu-id="f3890-209">.txt</span><span class="sxs-lookup"><span data-stu-id="f3890-209">.txt</span></span>      | <span data-ttu-id="f3890-210">열기, 인쇄, PrintTo</span><span class="sxs-lookup"><span data-stu-id="f3890-210">Open, Print, PrintTo</span></span>                |
| <span data-ttu-id="f3890-211">.wav</span><span class="sxs-lookup"><span data-stu-id="f3890-211">.wav</span></span>      | <span data-ttu-id="f3890-212">열기, 재생</span><span class="sxs-lookup"><span data-stu-id="f3890-212">Open, Play</span></span>                          |

<span data-ttu-id="f3890-213">프로세스에서 실행 되는 파일에 사용할 수 있는 동사를 찾으려면 cmdlet을 사용 `New-Object` 하 여 파일에 대 한 **ProcessStartInfo** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-213">To find the verbs that can be used with the file that runs in a process, use the `New-Object` cmdlet to create a **System.Diagnostics.ProcessStartInfo** object for the file.</span></span> <span data-ttu-id="f3890-214">사용 가능한 동사는 **ProcessStartInfo** 개체의 **verbs** 속성에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-214">The available verbs are in the **Verbs** property of the **ProcessStartInfo** object.</span></span> <span data-ttu-id="f3890-215">자세한 내용은 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-215">For details, see the examples.</span></span>

<span data-ttu-id="f3890-216">Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-216">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.String
Parameter Sets: UseShellExecute
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-217">-Wait</span><span class="sxs-lookup"><span data-stu-id="f3890-217">-Wait</span></span>

<span data-ttu-id="f3890-218">이 cmdlet은 지정 된 프로세스와 해당 하위 항목이 완료 될 때까지 대기한 후 추가 입력을 수락 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-218">Indicates that this cmdlet waits for the specified process and its descendants to complete before accepting more input.</span></span> <span data-ttu-id="f3890-219">이 매개 변수는 프로세스가 완료 될 때까지 명령 프롬프트를 표시 하지 않거나 창을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-219">This parameter suppresses the command prompt or retains the window until the processes finish.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-220">-WindowStyle</span><span class="sxs-lookup"><span data-stu-id="f3890-220">-WindowStyle</span></span>

<span data-ttu-id="f3890-221">새 프로세스에 사용되는 창의 상태를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-221">Specifies the state of the window that is used for the new process.</span></span> <span data-ttu-id="f3890-222">이 매개 변수에 허용 되는 값은 **Normal** , **Hidden** , **최소화** 및 **최대화** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-222">The acceptable values for this parameter are: **Normal** , **Hidden** , **Minimized** , and **Maximized**.</span></span> <span data-ttu-id="f3890-223">기본값은 **Normal** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-223">The default value is **Normal**.</span></span>

<span data-ttu-id="f3890-224">동일한 명령에서 **system.windows.window.windowstyle** 및 **nonewwindow** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-224">You cannot use the **WindowStyle** and **NoNewWindow** parameters in the same command.</span></span>

<span data-ttu-id="f3890-225">Windows 이외의 시스템에는이 매개 변수가 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-225">The parameter does not apply for non-Windows systems.</span></span>

```yaml
Type: System.Diagnostics.ProcessWindowStyle
Parameter Sets: (All)
Aliases:
Accepted values: Normal, Hidden, Minimized, Maximized

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-226">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="f3890-226">-WorkingDirectory</span></span>

<span data-ttu-id="f3890-227">새 프로세스를 시작할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-227">Specifies the location that the new process should start in.</span></span> <span data-ttu-id="f3890-228">기본값은 시작 되는 실행 파일 또는 문서의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-228">The default is the location of the executable file or document being started.</span></span> <span data-ttu-id="f3890-229">와일드카드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-229">Wildcards are not supported.</span></span> <span data-ttu-id="f3890-230">경로 이름에는 와일드 카드로 해석 될 문자를 포함 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-230">The path name must not contain characters that would be interpreted as wildcards.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-231">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f3890-231">-Confirm</span></span>

<span data-ttu-id="f3890-232">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-232">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-233">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f3890-233">-WhatIf</span></span>

<span data-ttu-id="f3890-234">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-234">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f3890-235">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-235">The cmdlet is not run.</span></span>

<span data-ttu-id="f3890-236">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-236">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f3890-237">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f3890-237">CommonParameters</span></span>

<span data-ttu-id="f3890-238">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f3890-238">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f3890-239">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-239">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f3890-240">입력</span><span class="sxs-lookup"><span data-stu-id="f3890-240">INPUTS</span></span>

### <span data-ttu-id="f3890-241">없음</span><span class="sxs-lookup"><span data-stu-id="f3890-241">None</span></span>

<span data-ttu-id="f3890-242">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-242">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f3890-243">출력</span><span class="sxs-lookup"><span data-stu-id="f3890-243">OUTPUTS</span></span>

### <span data-ttu-id="f3890-244">없음, 시스템 진단 프로세스</span><span class="sxs-lookup"><span data-stu-id="f3890-244">None, System.Diagnostics.Process</span></span>

<span data-ttu-id="f3890-245">이 cmdlet은 **PassThru** 매개 변수를 지정 하는 경우 **system.object** 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-245">This cmdlet generates a **System.Diagnostics.Process** object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f3890-246">그러지 않으면 아무 출력도 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-246">Otherwise, this cmdlet does not return any output.</span></span>

## <span data-ttu-id="f3890-247">참고</span><span class="sxs-lookup"><span data-stu-id="f3890-247">NOTES</span></span>

- <span data-ttu-id="f3890-248">이 cmdlet은 **system.web. Process** 클래스의 **Start** 메서드를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-248">This cmdlet is implemented by using the **Start** method of the **System.Diagnostics.Process** class.</span></span> <span data-ttu-id="f3890-249">이 메서드에 대 한 자세한 내용은 [Process. Start 메서드](/dotnet/api/system.diagnostics.process.start#overloads)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f3890-249">For more information about this method, see [Process.Start Method](/dotnet/api/system.diagnostics.process.start#overloads).</span></span>

- <span data-ttu-id="f3890-250">Windows에서 **UseNewEnvironment** 를 사용 하는 경우 새 프로세스가 **컴퓨터** 범위에 대해 정의 된 기본 환경 변수만 포함 하는 것으로 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-250">On Windows, when you use **UseNewEnvironment** , the new process starts only containing the default environment variables defined for the **Machine** scope.</span></span> <span data-ttu-id="f3890-251">이를 통해 `$env:USERNAME` 가 **시스템** 으로 설정 된다는 측면에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-251">This has the side affect that the `$env:USERNAME` is set to **SYSTEM**.</span></span> <span data-ttu-id="f3890-252">**사용자** 범위의 변수가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-252">None of the variables from the **User** scope are included.</span></span>

- <span data-ttu-id="f3890-253">Windows에서의 가장 일반적인 사용 사례는 `Start-Process` **Wait** 매개 변수를 사용 하 여 새 프로세스가 종료 될 때까지 진행을 차단 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-253">On Windows, the most common use case for `Start-Process` is to use the **Wait** parameter to block progress until the new process exits.</span></span> <span data-ttu-id="f3890-254">비 Windows 시스템에서는 명령줄 응용 프로그램의 기본 동작이와 동일 하기 때문에이 작업이 거의 필요 하지 않습니다 `Start-Process -Wait` .</span><span class="sxs-lookup"><span data-stu-id="f3890-254">On non-Windows system, this is rarely needed since the default behavior for command-line applications is equivalent to `Start-Process -Wait`.</span></span>

- <span data-ttu-id="f3890-255">`Start-Process`Windows 이외의 시스템에서를 사용 하는 경우 새 터미널 창이 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3890-255">When using `Start-Process` on non-Windows systems, you never get a new terminal window.</span></span>

## <span data-ttu-id="f3890-256">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f3890-256">RELATED LINKS</span></span>

[<span data-ttu-id="f3890-257">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="f3890-257">about_Quoting_Rules</span></span>](../Microsoft.PowerShell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="f3890-258">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="f3890-258">Debug-Process</span></span>](Debug-Process.md)

[<span data-ttu-id="f3890-259">Get-Process</span><span class="sxs-lookup"><span data-stu-id="f3890-259">Get-Process</span></span>](Get-Process.md)

[<span data-ttu-id="f3890-260">Start-Service</span><span class="sxs-lookup"><span data-stu-id="f3890-260">Start-Service</span></span>](Start-Service.md)

[<span data-ttu-id="f3890-261">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="f3890-261">Stop-Process</span></span>](Stop-Process.md)

[<span data-ttu-id="f3890-262">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="f3890-262">Wait-Process</span></span>](Wait-Process.md)
