---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-localizeddata?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-LocalizedData
ms.openlocfilehash: 08f959d38fc8ab861934f9a93004e67c649d9786
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93240004"
---
# <span data-ttu-id="43b42-103">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="43b42-103">Import-LocalizedData</span></span>

## <span data-ttu-id="43b42-104">개요</span><span class="sxs-lookup"><span data-stu-id="43b42-104">SYNOPSIS</span></span>
<span data-ttu-id="43b42-105">운영 체제에 대해 선택한 UI 문화권을 기준으로 하여 언어별 데이터를 스크립트 및 함수로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-105">Imports language-specific data into scripts and functions based on the UI culture that is selected for the operating system.</span></span>

## <span data-ttu-id="43b42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43b42-106">SYNTAX</span></span>

```
Import-LocalizedData [[-BindingVariable] <String>] [[-UICulture] <String>] [-BaseDirectory <String>]
 [-FileName <String>] [-SupportedCommand <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="43b42-107">설명</span><span class="sxs-lookup"><span data-stu-id="43b42-107">DESCRIPTION</span></span>

<span data-ttu-id="43b42-108">`Import-LocalizedData`Cmdlet은 이름이 운영 체제의 현재 사용자에 대해 설정 된 UI 언어와 일치 하는 하위 디렉터리에서 문자열을 동적으로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-108">The `Import-LocalizedData` cmdlet dynamically retrieves strings from a subdirectory whose name matches the UI language set for the current user of the operating system.</span></span> <span data-ttu-id="43b42-109">이 cmdlet을 통해 스크립트는 현재 사용자가 선택한 UI 언어로 사용자 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-109">It is designed to enable scripts to display user messages in the UI language selected by the current user.</span></span>

<span data-ttu-id="43b42-110">`Import-LocalizedData``.psd1`스크립트 디렉터리의 언어별 하위 디렉터리에 있는 파일에서 데이터를 가져와 명령에 지정 된 지역 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-110">`Import-LocalizedData` imports data from `.psd1` files in language-specific subdirectories of the script directory and saves them in a local variable that is specified in the command.</span></span> <span data-ttu-id="43b42-111">Cmdlet은 자동 변수의 값을 기준으로 하위 디렉터리 및 파일을 선택 합니다 `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="43b42-111">The cmdlet selects the subdirectory and file based on the value of the `$PSUICulture` automatic variable.</span></span> <span data-ttu-id="43b42-112">스크립트의 지역 변수를 사용하여 사용자 메시지를 표시하는 경우 메시지는 사용자의 UI 언어로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-112">When you use the local variable in the script to display a user message, the message appears in the user's UI language.</span></span>

<span data-ttu-id="43b42-113">의 매개 변수를 사용 하 여 `Import-LocalizedData` 대체 UI 문화권, 경로 및 파일 이름을 지정 하 고, 지원 되는 명령을 추가 하 고, 파일을 찾을 수 없는 경우 표시 되는 오류 메시지를 표시 하지 않을 수 있습니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-113">You can use the parameters of `Import-LocalizedData` to specify an alternate UI culture, path, and filename, to add supported commands, and to suppress the error message that appears if the `.psd1` files are not found.</span></span>

<span data-ttu-id="43b42-114">`Import-LocalizedData`Cmdlet은 Windows PowerShell 2.0에 도입 된 스크립트 국제화 이니셔티브를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-114">The `Import-LocalizedData` cmdlet supports the script internationalization initiative that was introduced in Windows PowerShell 2.0.</span></span> <span data-ttu-id="43b42-115">이 이니셔티브는 스크립트에서 사용자 메시지를 현재 사용자의 UI 언어로 쉽게 표시할 수 있도록 설정하여 전 세계 사용자에게 더 나은 서비스를 제공하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-115">This initiative aims to better serve users worldwide by making it easy for scripts to display user messages in the UI language of the current user.</span></span> <span data-ttu-id="43b42-116">이에 대 한 자세한 내용과 파일 형식에 대 한 자세한 내용은 `.psd1` [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b42-116">For more information about this and about the format of the `.psd1` files, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="43b42-117">예제</span><span class="sxs-lookup"><span data-stu-id="43b42-117">EXAMPLES</span></span>

### <span data-ttu-id="43b42-118">예제 1: 텍스트 문자열 가져오기</span><span class="sxs-lookup"><span data-stu-id="43b42-118">Example 1: Import text strings</span></span>

<span data-ttu-id="43b42-119">이 예에서는 텍스트 문자열을 `$Messages` 변수로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-119">This example imports text strings into the `$Messages` variable.</span></span> <span data-ttu-id="43b42-120">그리고 다른 모든 cmdlet의 매개 변수에 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-120">It uses the default values of all other cmdlet parameters.</span></span>

```powershell
Import-LocalizedData -BindingVariable "Messages"
```

<span data-ttu-id="43b42-121">명령이 디렉터리의 Archives.ps1 스크립트에 포함 되 `C:\Test` 고 `$PsUICulture` 자동 변수 값이 zh-cn 인 경우는 `Import-LocalizedData` `Archives.psd1` 디렉터리의 파일을 `C:\test\zh-CN` 변수로 가져옵니다 `$Messages` .</span><span class="sxs-lookup"><span data-stu-id="43b42-121">If the command is included in the Archives.ps1 script in the `C:\Test` directory, and the value of the `$PsUICulture` automatic variable is zh-CN, `Import-LocalizedData` imports the `Archives.psd1` file in the `C:\test\zh-CN` directory into the `$Messages` variable.</span></span>

### <span data-ttu-id="43b42-122">예제 2: 지역화 된 데이터 문자열 가져오기</span><span class="sxs-lookup"><span data-stu-id="43b42-122">Example 2: Import localized data strings</span></span>

<span data-ttu-id="43b42-123">이 예제는 스크립트가 아닌 명령줄에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-123">This example is run at the command line not in a script.</span></span> <span data-ttu-id="43b42-124">Test.psd1 파일에서 지역화된 데이터를 가져와 명령줄에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-124">It gets localized data strings from the Test.psd1 file and displays them at the command line.</span></span> <span data-ttu-id="43b42-125">이 명령은 스크립트에서 사용되지 않으므로 **FileName** 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-125">Because the command is not used in a script, the **FileName** parameter is required.</span></span> <span data-ttu-id="43b42-126">이 명령은 **UICulture** 매개 변수를 사용 하 여 en-us 문화권을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-126">The command uses the **UICulture** parameter to specify the en-US culture.</span></span>

```powershell
Import-LocalizedData -FileName "Test.psd1" -UICulture "en-US"
```

```Output
Name                           Value
----                           -----
Msg3                           "Use $_ to represent the object that is being processed."
Msg2                           "This command requires the credentials of a member of the Administrators group on the...
Msg1                           "The Name parameter is missing from the command."
```

<span data-ttu-id="43b42-127">`Import-LocalizedData` 지역화 된 데이터 문자열을 포함 하는 해시 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-127">`Import-LocalizedData` returns a hash table that contains the localized data strings.</span></span>

### <span data-ttu-id="43b42-128">예제 3: UI 문화권 문자열 가져오기</span><span class="sxs-lookup"><span data-stu-id="43b42-128">Example 3: Import UI culture strings</span></span>

```powershell
Import-LocalizedData -BindingVariable "MsgTbl" -UICulture "ar-SA" -FileName "Simple" -BaseDirectory "C:\Data\Localized"
```

<span data-ttu-id="43b42-129">이 명령은 텍스트 문자열을 `$MsgTbl` 스크립트의 변수로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-129">This command imports text strings into the `$MsgTbl` variable of a script.</span></span>

<span data-ttu-id="43b42-130">**UICulture** 매개 변수를 사용 하 여 cmdlet이 `Simple.psd1` 의 하위 디렉터리에 있는 파일에서 데이터를 가져오도록 지시 합니다 `ar-SA` `C:\Data\Localized` .</span><span class="sxs-lookup"><span data-stu-id="43b42-130">It uses the **UICulture** parameter to direct the cmdlet to import data from the `Simple.psd1` file in the `ar-SA` subdirectory of `C:\Data\Localized`.</span></span>

### <span data-ttu-id="43b42-131">예제 4: 스크립트로 지역화 된 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="43b42-131">Example 4: Import localized data into a script</span></span>

<span data-ttu-id="43b42-132">이 예제에서는 간단한 스크립트에서 데이터를 지역화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-132">This example shows how to use localized data in a simple script.</span></span>

```powershell
PS C:\> # In C:\Test\en-US\Test.psd1:

ConvertFrom-StringData @'

# English strings

Msg1 = "The Name parameter is missing from the command."
Msg2 = "This command requires the credentials of a member of the Administrators group on the computer."
Msg3 = "Use $_ to represent the object that is being processed."
'@

# In C:\Test\Test.ps1

Import-LocalizedData -BindingVariable "Messages"
Write-Host $Messages.Msg2

# In Windows PowerShell

PS C:\> .\Test.ps1

This command requires the credentials of a member of the Administrators group on the computer.
```

<span data-ttu-id="43b42-133">이 예제의 첫 번째 부분에서는 파일의 내용을 보여 줍니다 `Test.psd1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-133">The first part of the example shows the contents of the `Test.psd1` file.</span></span> <span data-ttu-id="43b42-134">여기에는 `ConvertFrom-StringData` 일련의 명명 된 텍스트 문자열을 해시 테이블로 변환 하는 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-134">It contains a `ConvertFrom-StringData` command that converts a series of named text strings into a hash table.</span></span> <span data-ttu-id="43b42-135">`Test.psd1`이 파일은 `C:\Test` 스크립트가 포함 된 디렉터리의 en-us 하위 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-135">The `Test.psd1` file is located in the en-US subdirectory of the `C:\Test` directory that contains the script.</span></span>

<span data-ttu-id="43b42-136">예제의 두 번째 부분에서는 스크립트의 내용을 보여 줍니다 `Test.ps1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-136">The second part of the example shows the contents of the `Test.ps1` script.</span></span> <span data-ttu-id="43b42-137">이 파일에는 `Import-LocalizedData` 일치 하는 파일에서 변수로 데이터를 가져오는 명령과 `.psd1` `$Messages` `Write-Host` 변수에 있는 메시지 중 하나를 `$Messages` 호스트 프로그램에 기록 하는 명령이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-137">It contains an `Import-LocalizedData` command that imports the data from the matching `.psd1` file into the `$Messages` variable and a `Write-Host` command that writes one of the messages in the `$Messages` variable to the host program.</span></span>

<span data-ttu-id="43b42-138">이 예제의 마지막 부분에서는 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-138">The last part of the example runs the script.</span></span> <span data-ttu-id="43b42-139">출력을 보면 운영 체제의 현재 사용자에 대해 설정된 UI 언어로 올바른 사용자 메시지가 표시되는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-139">The output shows that it displays the correct user message in the UI language set for the current user of the operating system.</span></span>

### <span data-ttu-id="43b42-140">예 5: 스크립트에서 기본 텍스트 문자열 바꾸기</span><span class="sxs-lookup"><span data-stu-id="43b42-140">Example 5: Replace default text strings in a script</span></span>

<span data-ttu-id="43b42-141">이 예에서는를 사용 하 여 `Import-LocalizedData` 스크립트의 데이터 섹션에 정의 된 기본 텍스트 문자열을 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-141">This example shows how to use `Import-LocalizedData` to replace default text strings defined in the DATA section of a script.</span></span>

```powershell
PS C:\> # In TestScript.ps1
$UserMessages = DATA

{    ConvertFrom-StringData @'

    # English strings

        Msg1 = "Enter a name."
        Msg2 = "Enter your employee ID."
        Msg3 = "Enter your building number."
'@
}

Import-LocalizedData -BindingVariable "UserMessages"
$UserMessages.Msg1...
```

<span data-ttu-id="43b42-142">이 예에서 TestScript.ps1 스크립트의 데이터 섹션에는 `ConvertFrom-StringData` 데이터 섹션의 내용을 해시 테이블로 변환 하 고 변수 값에 저장 하는 명령이 포함 되어 있습니다 `$UserMessages` .</span><span class="sxs-lookup"><span data-stu-id="43b42-142">In this example, the DATA section of the TestScript.ps1 script contains a `ConvertFrom-StringData` command that converts the contents of the DATA section to a hash table and stores in the value of the `$UserMessages` variable.</span></span>

<span data-ttu-id="43b42-143">스크립트에는 `Import-LocalizedData` 변수 값으로 지정 된 하위 디렉터리의 TestScript.psd1 파일에서 번역 된 텍스트 문자열의 해시 테이블을 가져오는 명령도 포함 되어 있습니다 `$PsUICulture` .</span><span class="sxs-lookup"><span data-stu-id="43b42-143">The script also includes an `Import-LocalizedData` command, which imports a hash table of translated text strings from the TestScript.psd1 file in the subdirectory specified by the value of the `$PsUICulture` variable.</span></span> <span data-ttu-id="43b42-144">이 명령은 파일을 찾은 경우 `.psd1` 파일의 번역 된 문자열을 동일한 변수의 값에 저장 `$UserMessages` 하 여 데이터 섹션 논리에 의해 저장 된 해시 테이블을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-144">If the command finds the `.psd1` file, it saves the translated strings from the file in the value of the same `$UserMessages` variable, overwriting the hash table saved by the DATA section logic.</span></span>

<span data-ttu-id="43b42-145">세 번째 명령은 변수의 첫 번째 메시지를 표시 합니다 `$UserMessages` .</span><span class="sxs-lookup"><span data-stu-id="43b42-145">The third command displays the first message in the `$UserMessages` variable.</span></span>

<span data-ttu-id="43b42-146">명령에서 `Import-LocalizedData` `.psd1` 언어에 대 한 파일을 찾은 경우 `$PsUICulture` 변수 값에는 `$UserMessages` 번역 된 텍스트 문자열이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-146">If the `Import-LocalizedData` command finds a `.psd1` file for the `$PsUICulture` language, the value of the `$UserMessages` variable contains the translated text strings.</span></span> <span data-ttu-id="43b42-147">어떤 이유로든 명령이 실패하면 명령이 스크립트의 DATA 섹션에 정의된 기본 텍스트 문자열을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-147">If the command fails for any reason, the command displays the default text strings defined in the DATA section of the script.</span></span>

### <span data-ttu-id="43b42-148">예제 6: UI 문화권을 찾을 수 없는 경우 오류 메시지 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="43b42-148">Example 6: Suppress error messages if the UI culture is not found</span></span>

<span data-ttu-id="43b42-149">이 예제에서는 `Import-LocalizedData` 가 사용자의 UI 문화권과 일치 하는 디렉터리를 찾을 수 없거나 `.psd1` 해당 디렉터리에서 스크립트에 대 한 파일을 찾을 수 없는 경우 표시 되는 오류 메시지를 표시 하지 않도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-149">This example shows how to suppress the error messages that appear when `Import-LocalizedData` cannot find the directories that match the user's UI culture or cannot find a `.psd1` file for the script in those directories.</span></span>

```powershell
PS C:\> # In Day1.ps1

Import-LocalizedData -BindingVariable "Day"

# In Day2.ps1

Import-LocalizedData -BindingVariable "Day" -ErrorAction:SilentlyContinue

PS C:\> .\Day1.ps1
Import-LocalizedData : Cannot find PowerShell data file 'Day1.psd1' in directory 'C:\ps-test\fr-BE\' or any parent culture directories.
At C:\ps-test\Day1.ps1:17 char:21+ Import-LocalizedData <<<<  Day
Today is Tuesday

PS C:\> .\Day2.ps1
Today is Tuesday
```

<span data-ttu-id="43b42-150">SilentlyContinue 값과 함께 **Erroraction** 일반 매개 변수를 사용 하 여 오류 메시지를 표시 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-150">You can use the **ErrorAction** common parameter with a value of SilentlyContinue to suppress the error message.</span></span> <span data-ttu-id="43b42-151">이는 기본 또는 대체 언어로 사용자 메시지를 제공 하 고 오류 메시지가 필요 하지 않은 경우에 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-151">This is especially useful when you have provided user messages in a default or fallback language, and no error message is needed.</span></span>

<span data-ttu-id="43b42-152">이 예제에서는 `Day1.ps1` 명령을 포함 하는 두 개의 스크립트와 Day2.ps1를 비교 `Import-LocalizedData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-152">This example compares two scripts, `Day1.ps1` and Day2.ps1, that include an `Import-LocalizedData` command.</span></span> <span data-ttu-id="43b42-153">출력만는 값이 인 **Erroraction** 일반 매개 변수를 사용 한다는 점을 제외 하 고 스크립트는 동일 `SilentlyContinue` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-153">The scripts are identical, except that Day2 uses the **ErrorAction** common parameter with a value of `SilentlyContinue`.</span></span>

<span data-ttu-id="43b42-154">샘플 출력에서는 UI 문화권이로 설정 되 `fr-BE` 고 해당 ui 문화권에 일치 하는 파일 또는 디렉터리가 없을 때 두 스크립트를 모두 실행 한 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-154">The sample output shows the results of running both scripts when the UI culture is set to `fr-BE` and there are no matching files or directories for that UI culture.</span></span> <span data-ttu-id="43b42-155">`Day1.ps1` 오류 메시지 및 영어 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-155">`Day1.ps1` displays an error message and English output.</span></span> <span data-ttu-id="43b42-156">`Day2.ps1` 영어 출력만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-156">`Day2.ps1` just displays the English output.</span></span>

## <span data-ttu-id="43b42-157">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43b42-157">PARAMETERS</span></span>

### <span data-ttu-id="43b42-158">-BaseDirectory</span><span class="sxs-lookup"><span data-stu-id="43b42-158">-BaseDirectory</span></span>

<span data-ttu-id="43b42-159">파일이 있는 기본 디렉터리를 지정 합니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-159">Specifies the base directory where the `.psd1` files are located.</span></span> <span data-ttu-id="43b42-160">기본값은 스크립트가 있는 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-160">The default is the directory where the script is located.</span></span> <span data-ttu-id="43b42-161">`Import-LocalizedData``.psd1`기본 디렉터리의 언어별 하위 디렉터리에서 스크립트에 대 한 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-161">`Import-LocalizedData` searches for the `.psd1` file for the script in a language-specific subdirectory of the base directory.</span></span>

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

### <span data-ttu-id="43b42-162">-BindingVariable</span><span class="sxs-lookup"><span data-stu-id="43b42-162">-BindingVariable</span></span>

<span data-ttu-id="43b42-163">텍스트 문자열을 가져와 넣을 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-163">Specifies the variable into which the text strings are imported.</span></span> <span data-ttu-id="43b42-164">달러 기호 () 없이 변수 이름을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-164">Enter a variable name without a dollar sign (`$`).</span></span>

<span data-ttu-id="43b42-165">Windows PowerShell 2.0에서는 이 매개 변수가 필수이지만</span><span class="sxs-lookup"><span data-stu-id="43b42-165">In Windows PowerShell 2.0, this parameter is required.</span></span> <span data-ttu-id="43b42-166">Windows PowerShell 3.0에서는 이 매개 변수가 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-166">In Windows PowerShell 3.0, this parameter is optional.</span></span> <span data-ttu-id="43b42-167">이 매개 변수를 생략 하면는 `Import-LocalizedData` 텍스트 문자열의 해시 테이블을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-167">If you omit this parameter, `Import-LocalizedData` returns a hash table of the text strings.</span></span> <span data-ttu-id="43b42-168">해시 테이블은 파이프라인으로 전달되거나 명령줄에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-168">The hash table is passed down the pipeline or displayed at the command line.</span></span>

<span data-ttu-id="43b42-169">를 사용 하 여 `Import-LocalizedData` 스크립트의 데이터 섹션에 지정 된 기본 텍스트 문자열을 바꿀 때 데이터 섹션을 변수에 할당 하 고 **bindingvariable** 매개 변수 값에 data section 변수의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-169">When using `Import-LocalizedData` to replace default text strings specified in the DATA section of a script, assign the DATA section to a variable and enter the name of the DATA section variable in the value of the **BindingVariable** parameter.</span></span> <span data-ttu-id="43b42-170">그러면에서 `Import-LocalizedData` 가져온 콘텐츠를 **bindingvariable** 에 저장할 때 가져온 데이터는 기본 텍스트 문자열을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-170">Then, when `Import-LocalizedData` saves the imported content in the **BindingVariable** , the imported data will replace the default text strings.</span></span> <span data-ttu-id="43b42-171">기본 텍스트 문자열을 지정하지 않으면 어떤 변수 이름이든 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-171">If you are not specifying default text strings, you can select any variable name.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Variable

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43b42-172">-FileName</span><span class="sxs-lookup"><span data-stu-id="43b42-172">-FileName</span></span>

<span data-ttu-id="43b42-173">가져올 데이터 파일의 이름을 지정 합니다 `.psd1)` .</span><span class="sxs-lookup"><span data-stu-id="43b42-173">Specifies the name of the data file (`.psd1)` to be imported.</span></span> <span data-ttu-id="43b42-174">파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-174">Enter a file name.</span></span> <span data-ttu-id="43b42-175">파일 이름 확장명을 포함 하지 않는 파일 이름을 지정 하거나 파일 이름 확장명을 포함 하는 파일 이름을 지정할 수 있습니다 `.psd1` `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-175">You can specify a file name that does not include its `.psd1` file name extension, or you can specify the file name including the `.psd1` file name extension.</span></span> <span data-ttu-id="43b42-176">데이터 파일은 Unicode 또는 u t f-8로 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-176">Data files should be saved as Unicode or UTF-8.</span></span>

<span data-ttu-id="43b42-177">**파일 이름** 매개 변수는 `Import-LocalizedData` 가 스크립트에서 사용 되지 않는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-177">The **FileName** parameter is required when `Import-LocalizedData` is not used in a script.</span></span>
<span data-ttu-id="43b42-178">그러지 않으면 이 매개 변수는 선택 사항이며 기본값은 스크립트의 기본 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-178">Otherwise, the parameter is optional and the default value is the base name of the script.</span></span> <span data-ttu-id="43b42-179">이 매개 변수를 사용 하 여 `Import-LocalizedData` 다른 파일을 검색 하도록 지시할 수 있습니다 `.psd1` .</span><span class="sxs-lookup"><span data-stu-id="43b42-179">You can use this parameter to direct `Import-LocalizedData` to search for a different `.psd1` file.</span></span>

<span data-ttu-id="43b42-180">예를 들어 **파일 이름이** 생략 되 고 스크립트 이름이 FindFiles.ps1 인 경우는 `Import-LocalizedData` FindFiles.psd1 데이터 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-180">For example, if the **FileName** is omitted and the script name is FindFiles.ps1, `Import-LocalizedData` searches for the FindFiles.psd1 data file.</span></span>

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

### <span data-ttu-id="43b42-181">-SupportedCommand</span><span class="sxs-lookup"><span data-stu-id="43b42-181">-SupportedCommand</span></span>

<span data-ttu-id="43b42-182">데이터만 생성하는 cmdlet 및 함수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-182">Specifies cmdlets and functions that generate only data.</span></span>

<span data-ttu-id="43b42-183">이 매개 변수를 사용하면 사용자가 작성하거나 테스트한 cmdlet 및 함수를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-183">Use this parameter to include cmdlets and functions that you have written or tested.</span></span> <span data-ttu-id="43b42-184">자세한 내용은 [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b42-184">For more information, see [about_Script_Internationalization](../Microsoft.PowerShell.Core/About/about_Script_Internationalization.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43b42-185">-UICulture</span><span class="sxs-lookup"><span data-stu-id="43b42-185">-UICulture</span></span>

<span data-ttu-id="43b42-186">대체 UI 문화권을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-186">Specifies an alternate UI culture.</span></span>
<span data-ttu-id="43b42-187">기본값은 `$PsUICulture` 자동 변수의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-187">The default is the value of the `$PsUICulture` automatic variable.</span></span>
<span data-ttu-id="43b42-188">UI 문화권을 형식 (예 `<language>-<region>` :, 또는)으로 입력 `en-US` `de-DE` `ar-SA` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-188">Enter a UI culture in `<language>-<region>` format, such as `en-US`, `de-DE`, or `ar-SA`.</span></span>

<span data-ttu-id="43b42-189">**UICulture** 매개 변수 값은 `Import-LocalizedData` `.psd1` 스크립트에 대 한 파일을 가져오는의 언어별 하위 디렉터리 (기본 디렉터리 내)를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-189">The value of the **UICulture** parameter determines the language-specific subdirectory (within the base directory) from which `Import-LocalizedData` gets the `.psd1` file for the script.</span></span>

<span data-ttu-id="43b42-190">Cmdlet은 **UICulture** 매개 변수 값과 같은 이름 또는 `$PsUICulture` 자동 변수 (예: 또는)를 사용 하 여 하위 디렉터리를 검색 합니다 `de-DE` `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="43b42-190">The cmdlet searches for a subdirectory with the same name as the value of the **UICulture** parameter or the `$PsUICulture` automatic variable, such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="43b42-191">디렉터리를 찾을 수 없거나 디렉터리에 스크립트에 대 한 파일이 포함 되어 있지 않은 경우에는 `.psd1` 언어 코드 (예: de 또는 ar)의 이름을 사용 하 여 하위 디렉터리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-191">If it cannot find the directory, or the directory does not contain a `.psd1` file for the script, it searches for a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="43b42-192">하위 디렉터리 또는 파일을 찾을 수 없는 경우 `.psd1` 명령이 실패 하 고 데이터가 스크립트에 지정 된 기본 언어로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-192">If it cannot find the subdirectory or `.psd1` file, the command fails and the data is displayed in the default language specified in the script.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43b42-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43b42-193">CommonParameters</span></span>

<span data-ttu-id="43b42-194">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43b42-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43b42-195">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43b42-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="43b42-196">입력</span><span class="sxs-lookup"><span data-stu-id="43b42-196">INPUTS</span></span>

### <span data-ttu-id="43b42-197">없음</span><span class="sxs-lookup"><span data-stu-id="43b42-197">None</span></span>

<span data-ttu-id="43b42-198">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-198">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="43b42-199">출력</span><span class="sxs-lookup"><span data-stu-id="43b42-199">OUTPUTS</span></span>

### <span data-ttu-id="43b42-200">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="43b42-200">System.Collections.Hashtable</span></span>

<span data-ttu-id="43b42-201">`Import-LocalizedData`**bindingvariable** 매개 변수의 값으로 지정 된 변수에 해시 테이블을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-201">`Import-LocalizedData` saves the hash table in the variable that is specified by the value of the **BindingVariable** parameter.</span></span>

## <span data-ttu-id="43b42-202">참고</span><span class="sxs-lookup"><span data-stu-id="43b42-202">NOTES</span></span>

- <span data-ttu-id="43b42-203">를 사용 하기 전에 `Import-LocalizedData` 사용자 메시지를 지역화 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-203">Before using `Import-LocalizedData`, localize your user messages.</span></span> <span data-ttu-id="43b42-204">키-값 쌍의 해시 테이블에서 각 로캘 (UI 문화권)에 대 한 메시지의 형식을 지정 하 고, 스크립트 및 파일 이름 확장명과 이름이 같은 파일에 해시 테이블을 저장 `.psd1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-204">Format the messages for each locale (UI culture) in a hash table of key-value pairs, and save the hash table in a file with the same name as the script and a `.psd1` file name extension.</span></span> <span data-ttu-id="43b42-205">지원 되는 각 UI 문화권에 대 한 스크립트 디렉터리에 디렉터리를 만든 다음 `.psd1` ui 문화권 이름을 사용 하 여 디렉터리에 각 ui 문화권에 대 한 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-205">Create a directory under the script directory for each supported UI culture, and then save the `.psd1` file for each UI culture in the directory with the UI culture name.</span></span>

  <span data-ttu-id="43b42-206">예를 들어 사용자 메시지를 de-DE 로캘로 지역화하여 해시 테이블에서 해당 메시지의 형식을 지정하고,</span><span class="sxs-lookup"><span data-stu-id="43b42-206">For example, localize your user messages for the de-DE locale and format them in a hash table.</span></span>
  <span data-ttu-id="43b42-207">해시 테이블을 파일에 저장 `<ScriptName>.psd1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-207">Save the hash table in a `<ScriptName>.psd1` file.</span></span> <span data-ttu-id="43b42-208">그런 다음 `de-DE` 스크립트 디렉터리 아래에 하위 디렉터리를 만들고 독일어 파일을 `<ScriptName\>.psd1` `de-DE` 하위 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-208">Then create a `de-DE` subdirectory under the script directory, and save the German `<ScriptName\>.psd1` file in the `de-DE` subdirectory.</span></span>
  <span data-ttu-id="43b42-209">지원하는 각 로캘에 대해 이 방법을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-209">Repeat this method for each locale that you support.</span></span>

- <span data-ttu-id="43b42-210">`Import-LocalizedData` 스크립트에 대 한 지역화 된 사용자 메시지에 대해 구조화 된 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-210">`Import-LocalizedData` performs a structured search for the localized user messages for a script.</span></span>

  <span data-ttu-id="43b42-211">`Import-LocalizedData` 스크립트 파일이 있는 디렉터리 (또는 **BaseDirectory** 매개 변수 값)에서 검색을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-211">`Import-LocalizedData` begins the search in the directory where the script file is located (or the value of the **BaseDirectory** parameter).</span></span> <span data-ttu-id="43b42-212">그런 다음 기본 디렉터리 내에서 `$PsUICulture` 또는와 같은 변수 값 (또는 **UICulture** 매개 변수 값)과 동일한 이름의 하위 디렉터리를 검색 합니다 `de-DE` `ar-SA` .</span><span class="sxs-lookup"><span data-stu-id="43b42-212">It then searches within the base directory for a subdirectory with the same name as the value of the `$PsUICulture` variable (or the value of the **UICulture** parameter), such as `de-DE` or `ar-SA`.</span></span> <span data-ttu-id="43b42-213">그런 다음 `.psd1` 스크립트 (또는 **FileName** 매개 변수 값)와 이름이 같은 파일을 해당 하위 디렉터리에서 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-213">Then, it searches in that subdirectory for a `.psd1` file with the same name as the script (or the value of the **FileName** parameter).</span></span>

  <span data-ttu-id="43b42-214">에서 `Import-LocalizedData` UI 문화권의 이름을 가진 하위 디렉터리를 찾을 수 없거나 하위 디렉터리에 스크립트에 대 한 파일이 포함 되어 있지 않은 경우에는 `.psd1` `.psd1` 언어 코드 (예: de 또는 ar)의 이름을 사용 하 여 하위 디렉터리에서 스크립트에 대 한 파일을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-214">If `Import-LocalizedData` cannot find a subdirectory with the name of the UI culture, or the subdirectory does not contain a `.psd1` file for the script, it searches for a `.psd1` file for the script in a subdirectory with the name of the language code, such as de or ar.</span></span> <span data-ttu-id="43b42-215">하위 디렉터리 또는 파일을 찾을 수 없는 경우 `.psd1` 명령이 실패 하 고 데이터가 스크립트의 기본 언어로 표시 되 고 데이터를 가져올 수 없다는 오류 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-215">If it cannot find the subdirectory or `.psd1` file, the command fails, the data is displayed in the default language in the script, and an error message is displayed explaining that the data could not be imported.</span></span> <span data-ttu-id="43b42-216">메시지를 표시 하지 않고 정상적으로 실패 하려면 SilentlyContinue 값과 함께 **Erroraction** 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-216">To suppress the message and fail gracefully, use the **ErrorAction** common parameter with a value of SilentlyContinue.</span></span>

  <span data-ttu-id="43b42-217">`Import-LocalizedData`에서 하위 디렉터리와 `.psd1` 파일을 찾으면 사용자 메시지의 해시 테이블을 명령의 **bindingvariable** 매개 변수 값으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-217">If `Import-LocalizedData` finds the subdirectory and the `.psd1` file, it imports the hash table of user messages into the value of the **BindingVariable** parameter in the command.</span></span> <span data-ttu-id="43b42-218">그러면 해시 테이블의 메시지를 변수에 표시할 때 지역화된 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="43b42-218">Then, when you display a message from the hash table in the variable, the localized message is displayed.</span></span>

  <span data-ttu-id="43b42-219">자세한 내용은 [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="43b42-219">For more information, see [about_Script_Internationalization](../Microsoft.Powershell.Core/About/about_Script_Internationalization.md).</span></span>

## <span data-ttu-id="43b42-220">관련 링크</span><span class="sxs-lookup"><span data-stu-id="43b42-220">RELATED LINKS</span></span>

[<span data-ttu-id="43b42-221">Write-Host</span><span class="sxs-lookup"><span data-stu-id="43b42-221">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="43b42-222">Import-PowerShellDataFile</span><span class="sxs-lookup"><span data-stu-id="43b42-222">Import-PowerShellDataFile</span></span>](Import-PowerShellDataFile.md)
