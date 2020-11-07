---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unblock-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unblock-File
ms.openlocfilehash: 57c8c6f2ceda124b3dc89c363c6cf942680781ca
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344510"
---
# <span data-ttu-id="f0ebf-103">Unblock-File</span><span class="sxs-lookup"><span data-stu-id="f0ebf-103">Unblock-File</span></span>

## <span data-ttu-id="f0ebf-104">개요</span><span class="sxs-lookup"><span data-stu-id="f0ebf-104">SYNOPSIS</span></span>
<span data-ttu-id="f0ebf-105">인터넷에서 다운로드한 파일 차단을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-105">Unblocks files that were downloaded from the Internet.</span></span>

## <span data-ttu-id="f0ebf-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0ebf-106">SYNTAX</span></span>

### <span data-ttu-id="f0ebf-107">ByPath (기본값)</span><span class="sxs-lookup"><span data-stu-id="f0ebf-107">ByPath (Default)</span></span>

```
Unblock-File [-Path] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0ebf-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0ebf-108">ByLiteralPath</span></span>

```
Unblock-File -LiteralPath <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f0ebf-109">설명</span><span class="sxs-lookup"><span data-stu-id="f0ebf-109">DESCRIPTION</span></span>

<span data-ttu-id="f0ebf-110">`Unblock-File`Cmdlet을 사용 하면 인터넷에서 다운로드 한 파일을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-110">The `Unblock-File` cmdlet lets you open files that were downloaded from the Internet.</span></span> <span data-ttu-id="f0ebf-111">PowerShell 실행 정책이 **RemoteSigned** 때에도 실행할 수 있도록 인터넷에서 다운로드 된 powershell 스크립트 파일을 차단 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-111">It unblocks PowerShell script files that were downloaded from the Internet so you can run them, even when the PowerShell execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="f0ebf-112">기본적으로 이러한 파일은 신뢰할 수 없는 파일로부터 컴퓨터를 보호하도록 차단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-112">By default, these files are blocked to protect the computer from untrusted files.</span></span>

<span data-ttu-id="f0ebf-113">Cmdlet을 사용 하기 전에 `Unblock-File` 파일 및 소스를 검토 하 고 열어도 안전한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-113">Before using the `Unblock-File` cmdlet, review the file and its source and verify that it is safe to open.</span></span>

<span data-ttu-id="f0ebf-114">내부적으로 `Unblock-File` cmdlet은 값이 "3" 인 영역을 제거 하 여 인터넷에서 다운로드 되었음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-114">Internally, the `Unblock-File` cmdlet removes the Zone.Identifier alternate data stream, which has a value of "3" to indicate that it was downloaded from the Internet.</span></span>

<span data-ttu-id="f0ebf-115">PowerShell 실행 정책에 대 한 자세한 내용은 [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-115">For more information about PowerShell execution policies, see [about_Execution_Policies](../Microsoft.PowerShell.Core/about/about_Execution_Policies.md).</span></span>

<span data-ttu-id="f0ebf-116">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-116">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="f0ebf-117">예제</span><span class="sxs-lookup"><span data-stu-id="f0ebf-117">EXAMPLES</span></span>

### <span data-ttu-id="f0ebf-118">예제 1: 파일 차단 해제</span><span class="sxs-lookup"><span data-stu-id="f0ebf-118">Example 1: Unblock a file</span></span>

<span data-ttu-id="f0ebf-119">이 명령은 PowerShellTips.chm 파일을 차단 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-119">This command unblocks the PowerShellTips.chm file.</span></span>

```
PS C:\> Unblock-File -Path C:\Users\User01\Documents\Downloads\PowerShellTips.chm
```

### <span data-ttu-id="f0ebf-120">예 2: 여러 파일 차단 해제</span><span class="sxs-lookup"><span data-stu-id="f0ebf-120">Example 2: Unblock multiple files</span></span>

<span data-ttu-id="f0ebf-121">이 명령은 이름에 "PowerShell"이 포함 된 디렉터리의 모든 파일을 차단 해제 `C:\Downloads` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-121">This command unblocks all of the files in the `C:\Downloads` directory whose names include "PowerShell".</span></span> <span data-ttu-id="f0ebf-122">모든 파일이 안전한지 확인할 때까지 이와 같은 명령을 실행하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-122">Do not run a command like this one until you have verified that all files are safe.</span></span>

```
PS C:\> dir C:\Downloads\*PowerShell* | Unblock-File
```

### <span data-ttu-id="f0ebf-123">예제 3: 스크립트 찾기 및 차단 해제</span><span class="sxs-lookup"><span data-stu-id="f0ebf-123">Example 3: Find and unblock scripts</span></span>

<span data-ttu-id="f0ebf-124">이 명령은 PowerShell 스크립트를 찾아 차단 해제 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-124">This command shows how to find and unblock PowerShell scripts.</span></span>

<span data-ttu-id="f0ebf-125">첫 번째 명령은 *get-help* Cmdlet의 **Stream** 매개 변수를 사용 하 여 Zone. Identifier Stream으로 파일을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-125">The first command uses the **Stream** parameter of the *Get-Item* cmdlet get files with the Zone.Identifier stream.</span></span>

<span data-ttu-id="f0ebf-126">두 번째 명령은 실행 정책이 **RemoteSigned** PowerShell 세션에서 차단 된 스크립트를 실행할 때 발생 하는 상황을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-126">The second command shows what happens when you run a blocked script in a PowerShell session in which the execution policy is **RemoteSigned**.</span></span> <span data-ttu-id="f0ebf-127">RemoteSigned 정책은 디지털 서명되지 않은 경우 인터넷에서 다운로드한 스크립트를 실행할 수 없도록 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-127">The RemoteSigned policy prevents you from running scripts that are downloaded from the Internet unless they are digitally signed.</span></span>

<span data-ttu-id="f0ebf-128">세 번째 명령은 cmdlet을 사용 하 여 `Unblock-File` 세션에서 실행할 수 있도록 스크립트를 차단 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-128">The third command uses the `Unblock-File` cmdlet to unblock the script so it can run in the session.</span></span>

```
PS C:\> Get-Item * -Stream "Zone.Identifier" -ErrorAction SilentlyContinue
   FileName: C:\ps-test\Start-ActivityTracker.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

PS C:\> C:\ps-test\Start-ActivityTracker.ps1
c:\ps-test\Start-ActivityTracker.ps1 : File c:\ps-test\Start-ActivityTracker.ps1 cannot
be loaded. The file c:\ps-test\Start-ActivityTracker.ps1 is not digitally signed. The script
will not execute on the system. For more information, see about_Execution_Policies.

At line:1 char:1
+ c:\ps-test\Start-ActivityTracker.ps1
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess

PS C:\> Get-Item C:\ps-test\Start-ActivityTracker.ps1 | Unblock-File
```

## <span data-ttu-id="f0ebf-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f0ebf-129">PARAMETERS</span></span>

### <span data-ttu-id="f0ebf-130">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0ebf-130">-LiteralPath</span></span>

<span data-ttu-id="f0ebf-131">차단을 해제할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-131">Specifies the files to unblock.</span></span> <span data-ttu-id="f0ebf-132">**Path** 와 달리 **LiteralPath** 매개 변수 값은 입력한 대로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-132">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f0ebf-133">어떠한 문자도 와일드카드로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-133">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="f0ebf-134">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-134">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f0ebf-135">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-135">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f0ebf-136">-Path</span><span class="sxs-lookup"><span data-stu-id="f0ebf-136">-Path</span></span>

<span data-ttu-id="f0ebf-137">차단을 해제할 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-137">Specifies the files to unblock.</span></span> <span data-ttu-id="f0ebf-138">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-138">Wildcard characters are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="f0ebf-139">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f0ebf-139">-Confirm</span></span>

<span data-ttu-id="f0ebf-140">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-140">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0ebf-141">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f0ebf-141">-WhatIf</span></span>

<span data-ttu-id="f0ebf-142">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-142">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f0ebf-143">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-143">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f0ebf-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0ebf-144">CommonParameters</span></span>

<span data-ttu-id="f0ebf-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0ebf-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0ebf-147">입력</span><span class="sxs-lookup"><span data-stu-id="f0ebf-147">INPUTS</span></span>

### <span data-ttu-id="f0ebf-148">System.String</span><span class="sxs-lookup"><span data-stu-id="f0ebf-148">System.String</span></span>

<span data-ttu-id="f0ebf-149">파일 경로를로 파이프 할 수 있습니다 `Unblock-File` .</span><span class="sxs-lookup"><span data-stu-id="f0ebf-149">You can pipe a file path to `Unblock-File`.</span></span>

## <span data-ttu-id="f0ebf-150">출력</span><span class="sxs-lookup"><span data-stu-id="f0ebf-150">OUTPUTS</span></span>

### <span data-ttu-id="f0ebf-151">없음</span><span class="sxs-lookup"><span data-stu-id="f0ebf-151">None</span></span>

<span data-ttu-id="f0ebf-152">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-152">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f0ebf-153">참고</span><span class="sxs-lookup"><span data-stu-id="f0ebf-153">NOTES</span></span>

- <span data-ttu-id="f0ebf-154">`Unblock-File`Cmdlet은 파일 시스템 드라이브 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-154">The `Unblock-File` cmdlet works only in file system drives.</span></span>
- <span data-ttu-id="f0ebf-155">`Unblock-File`파일 탐색기의 **속성** 대화 상자에 있는 **차단 해제** 단추와 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-155">`Unblock-File` performs the same operation as the **Unblock** button on the **Properties** dialog box in File Explorer.</span></span>
- <span data-ttu-id="f0ebf-156">차단 되지 않은 파일에서 cmdlet을 사용 하는 경우 `Unblock-File` 명령은 차단 해제 된 파일에 영향을 주지 않으며 cmdlet은 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0ebf-156">If you use the `Unblock-File` cmdlet on a file that is not blocked, the command has no effect on the unblocked file and the cmdlet does not generate errors.</span></span>

## <span data-ttu-id="f0ebf-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f0ebf-157">RELATED LINKS</span></span>

[<span data-ttu-id="f0ebf-158">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="f0ebf-158">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="f0ebf-159">Get-Item</span><span class="sxs-lookup"><span data-stu-id="f0ebf-159">Get-Item</span></span>](../Microsoft.PowerShell.Management/Get-Item.md)

[<span data-ttu-id="f0ebf-160">Out-File</span><span class="sxs-lookup"><span data-stu-id="f0ebf-160">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="f0ebf-161">파일 시스템 공급자</span><span class="sxs-lookup"><span data-stu-id="f0ebf-161">FileSystem Provider</span></span>](../Microsoft.PowerShell.Core/about/about_FileSystem_Provider.md)
