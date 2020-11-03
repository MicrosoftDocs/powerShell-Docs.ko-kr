---
description: 스크립트에서 사용자에 게 UI (사용자 인터페이스) 언어로 메시지와 지침을 쉽게 표시할 수 있도록 하는 스크립트 국제화 기능에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_script_internationalization?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Script_Internationalization
ms.openlocfilehash: 63df9d87e78c3308f71c19f1008951fbbf879d04
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221186"
---
# <a name="about-script-internationalization"></a><span data-ttu-id="a8893-104">스크립트 국제화 정보</span><span class="sxs-lookup"><span data-stu-id="a8893-104">About Script Internationalization</span></span>

## <a name="short-description"></a><span data-ttu-id="a8893-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a8893-105">Short Description</span></span>
<span data-ttu-id="a8893-106">스크립트에서 사용자에 게 UI (사용자 인터페이스) 언어로 메시지와 지침을 쉽게 표시할 수 있도록 하는 스크립트 국제화 기능에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-106">Describes the script internationalization features that make it easy for scripts to display messages and instructions to users in their user interface (UI) language.</span></span>

## <a name="long-description"></a><span data-ttu-id="a8893-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="a8893-107">Long Description</span></span>

<span data-ttu-id="a8893-108">PowerShell 스크립트 국제화 기능을 사용 하면 사용자의 언어로 도움말 및 사용자 메시지를 표시 하 여 전 세계 사용자에 게 더 나은 서비스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-108">The PowerShell script internationalization features allow you to better serve users throughout the world by displaying help and user messages in the user's language.</span></span>

<span data-ttu-id="a8893-109">스크립트 국제화 기능은 실행 중 운영 체제의 UI 문화권을 쿼리하고, 적절 하 게 번역 된 텍스트 문자열을 가져와 사용자에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-109">The script internationalization features query the UI culture of the operating system during execution, import the appropriate translated text strings, and display them to the user.</span></span> <span data-ttu-id="a8893-110">데이터 섹션에서는 쉽게 식별 하 고 추출할 수 있도록 텍스트 문자열을 코드와 구분 하 여 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-110">The Data section lets you store text strings separate from code so they are easily identified and extracted.</span></span> <span data-ttu-id="a8893-111">새 cmdlet는 `ConvertFrom-StringData` 텍스트 문자열을 사전 유사 해시 테이블로 변환 하 여 변환을 용이 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-111">A new cmdlet, `ConvertFrom-StringData`, converts text strings into dictionary-like hash tables to facilitate translation.</span></span>

<span data-ttu-id="a8893-112">국가별 도움말 텍스트를 지원 하기 위해 PowerShell에는 다음과 같은 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-112">To support international Help text, PowerShell includes the following features:</span></span>

- <span data-ttu-id="a8893-113">텍스트 문자열을 코드 명령과 구분 하는 데이터 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-113">A Data section that separates text strings from code instructions.</span></span> <span data-ttu-id="a8893-114">데이터 섹션에 대 한 자세한 내용은 [about_Data_Sections](about_Data_Sections.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8893-114">For more information about the Data section, see [about_Data_Sections](about_Data_Sections.md).</span></span>

- <span data-ttu-id="a8893-115">새 자동 변수 `$PSCulture` 및 `$PSUICulture` 입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-115">New automatic variables, `$PSCulture` and `$PSUICulture`.</span></span> <span data-ttu-id="a8893-116">`$PSCulture` 날짜, 시간 및 통화와 같은 요소에 대해 시스템에서 사용 되는 UI 언어의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-116">`$PSCulture` stores the name of the UI language used on the system for elements such as the date, time, and currency.</span></span> <span data-ttu-id="a8893-117">`$PSUICulture`변수는 메뉴 및 텍스트 문자열과 같은 사용자 인터페이스 요소에 대해 시스템에서 사용 되는 UI 언어의 이름을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-117">The `$PSUICulture` variable stores the name of the UI language used on the system for user interface elements such as menus and text strings.</span></span>

- <span data-ttu-id="a8893-118">`ConvertFrom-StringData`텍스트 문자열을 사전 유사 해시 테이블로 변환 하 여 변환을 용이 하 게 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-118">A cmdlet, `ConvertFrom-StringData`, that converts text strings into dictionary-like hash tables to facilitate translation.</span></span> <span data-ttu-id="a8893-119">자세한 내용은 [convertfrom-csv-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8893-119">For more information, see [ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData).</span></span>

- <span data-ttu-id="a8893-120">`.psd1`번역 된 텍스트 문자열을 저장 하는 새 파일 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-120">A new file type, `.psd1`, that stores translated text strings.</span></span> <span data-ttu-id="a8893-121">`.psd1`파일은 스크립트 디렉터리의 언어별 하위 디렉터리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-121">The `.psd1` files are stored in language-specific subdirectories of the script directory.</span></span>

- <span data-ttu-id="a8893-122">Cmdlet는 `Import-LocalizedData` 지정 된 언어에 대 한 번역 된 텍스트 문자열을 런타임에 스크립트에 가져오는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-122">A cmdlet, `Import-LocalizedData`, that imports translated text strings for a specified language into a script at runtime.</span></span> <span data-ttu-id="a8893-123">이 cmdlet은 Windows에서 지 원하는 언어로 문자열을 인식 하 고 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-123">This cmdlet recognizes and imports strings in any Windows-supported language.</span></span> <span data-ttu-id="a8893-124">자세한 내용은 [import-localizeddata](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8893-124">For more information see [Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData).</span></span>

### <a name="the-data-section-storing-default-strings"></a><span data-ttu-id="a8893-125">데이터 섹션: 기본 문자열 저장</span><span class="sxs-lookup"><span data-stu-id="a8893-125">The Data Section: Storing Default Strings</span></span>

<span data-ttu-id="a8893-126">스크립트의 데이터 섹션을 사용 하 여 텍스트 문자열을 기본 언어로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-126">Use a Data section in the script to store the text strings in the default language.</span></span> <span data-ttu-id="a8893-127">문자열을 여기에 있는 키/값 쌍으로 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-127">Arrange the strings in key/value pairs in a here-string.</span></span> <span data-ttu-id="a8893-128">각 키/값 쌍은 별도의 줄에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-128">Each key/value pair must be on a separate line.</span></span> <span data-ttu-id="a8893-129">주석을 포함 하는 경우 주석은 별도의 줄에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-129">If you include comments, the comments must be on separate lines.</span></span>

<span data-ttu-id="a8893-130">`ConvertFrom-StringData`Cmdlet은 다음 문자열의 키/값 쌍을 데이터 섹션 변수 값에 저장 된 사전 형식의 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-130">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a dictionary-like hash table that is stored in the value of the Data section variable.</span></span>

<span data-ttu-id="a8893-131">다음 예에서 스크립트의 데이터 섹션에는 `World.ps1` 스크립트에 대 한 프롬프트 메시지의 English-United 상태 (en-us)가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-131">In the following example, the Data section of the `World.ps1` script includes the English-United States (en-US) set of prompt messages for a script.</span></span> <span data-ttu-id="a8893-132">`ConvertFrom-StringData`Cmdlet은 문자열을 해시 테이블로 변환 하 고 변수에 저장 합니다 `$msgtable` .</span><span class="sxs-lookup"><span data-stu-id="a8893-132">The `ConvertFrom-StringData` cmdlet converts the strings into a hash table and stores them in the `$msgtable` variable.</span></span>

```powershell
$msgTable = Data {
    #culture="en-US"
    ConvertFrom-StringData @'
    helloWorld = Hello, World.
    errorMsg1 = You cannot leave the user name field blank.
    promptMsg = Please enter your user name.
'@
}
```

<span data-ttu-id="a8893-133">이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a8893-133">For more information about here-strings, see [about_Quoting_Rules](about_Quoting_Rules.md).</span></span>

### <a name="psd1-files-storing-translated-strings"></a><span data-ttu-id="a8893-134">PSD1 Files: 번역 된 문자열 저장</span><span class="sxs-lookup"><span data-stu-id="a8893-134">PSD1 Files: Storing Translated Strings</span></span>

<span data-ttu-id="a8893-135">각 UI 언어에 대 한 스크립트 메시지를 스크립트 및 파일 이름 확장명과 동일한 이름으로 별도의 텍스트 파일에 저장 `.psd1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-135">Save the script messages for each UI language in separate text files with the same name as the script and the `.psd1` file name extension.</span></span> <span data-ttu-id="a8893-136">다음 형식의 문화권 이름을 사용 하 여 스크립트 디렉터리의 하위 디렉터리에 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-136">Store the files in subdirectories of the script directory with names of cultures in the following format:</span></span>

`<language>-<region>`

<span data-ttu-id="a8893-137">예: de-de, ar-SA 및 zh-cn-Hans</span><span class="sxs-lookup"><span data-stu-id="a8893-137">Examples: de-DE, ar-SA, and zh-Hans</span></span>

<span data-ttu-id="a8893-138">예를 들어 스크립트를 `World.ps1` 디렉터리에 저장 하는 경우 `C:\Scripts` 다음과 같은 파일 디렉터리 구조를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-138">For example, if the `World.ps1` script is stored in the `C:\Scripts` directory, you would create a file directory structure that resembles the following:</span></span>

```
C:\Scripts
C:\Scripts\World.ps1
C:\Scripts\de-DE\World.psd1
C:\Scripts\ar-SA\World.psd1
C:\Scripts\zh-CN\World.psd1
...
```

<span data-ttu-id="a8893-139">`World.psd1`스크립트 디렉터리의 de 하위 디렉터리에 있는 파일에는 다음 문이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-139">The `World.psd1` file in the de-DE subdirectory of the script directory might include the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = Hallo, Welt.
errorMsg1 = Das Feld Benutzername darf nicht leer sein.
promptMsg = Geben Sie Ihren Benutzernamen ein.
'@
```

<span data-ttu-id="a8893-140">마찬가지로 `World.psd1` 스크립트 디렉터리의 ar-SA 하위 디렉터리에 있는 파일에는 다음 문이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-140">Similarly, the `World.psd1` file in the ar-SA subdirectory of the script directory might includes the following statement:</span></span>

```powershell
ConvertFrom-StringData -StringData @'
helloWorld = مرحبًا أيها العالَم
errorMsg1 = لا يمكنك ترك حقل اسم المستخدم فارغًا
promptMsg = يرجى إدخال اسم المستخدم الخاص بك
'@
```

### <a name="import-localizeddata-dynamic-retrieval-of-translated-strings"></a><span data-ttu-id="a8893-141">Import-localizeddata: 번역 된 문자열의 동적 검색</span><span class="sxs-lookup"><span data-stu-id="a8893-141">Import-LocalizedData: Dynamic Retrieval of Translated Strings</span></span>

<span data-ttu-id="a8893-142">현재 사용자의 UI 언어에서 문자열을 검색 하려면 cmdlet을 사용 `Import-LocalizedData` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-142">To retrieve the strings in the UI language of the current user, use the `Import-LocalizedData` cmdlet.</span></span>

<span data-ttu-id="a8893-143">`Import-LocalizedData` 자동 변수의 값을 찾아 해당 `$PSUICulture` `<script-name>.psd1` 값과 일치 하는 하위 디렉터리에 있는 파일의 내용을 가져옵니다 `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="a8893-143">`Import-LocalizedData` finds the value of the `$PSUICulture` automatic variable and imports the content of the `<script-name>.psd1` files in the subdirectory that matches the `$PSUICulture` value.</span></span> <span data-ttu-id="a8893-144">그런 다음 **bindingvariable** 매개 변수의 값으로 지정 된 변수에 가져온 콘텐츠를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-144">Then, it saves the imported content in the variable specified by the value of the **BindingVariable** parameter.</span></span>

```powershell
Import-LocalizedData -BindingVariable msgTable
```

<span data-ttu-id="a8893-145">예를 들어 `Import-LocalizedData` 명령이 스크립트에 표시 되 `C:\Scripts\World.ps1` 고의 값 `$PSUICulture` 이 "ar-SA" 이면 `Import-LocalizedData` 다음 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-145">For example, if the `Import-LocalizedData` command appears in the `C:\Scripts\World.ps1` script and the value of `$PSUICulture` is "ar-SA", `Import-LocalizedData` finds the following file:</span></span>

`C:\Scripts\ar-SA\World.psd1`

<span data-ttu-id="a8893-146">그런 다음 파일에서 변수로 아랍어 텍스트 문자열을 가져와 `$msgTable` 스크립트의 데이터 섹션에서 정의 될 수 있는 기본 문자열을 대체 합니다 `World.ps1` .</span><span class="sxs-lookup"><span data-stu-id="a8893-146">Then, it imports the Arabic text strings from the file into the `$msgTable` variable, replacing any default strings that might be defined in the Data section of the `World.ps1` script.</span></span>

<span data-ttu-id="a8893-147">따라서 스크립트에서 변수를 사용 하 여 `$msgTable` 사용자 메시지를 표시할 때 메시지는 아랍어로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-147">As a result, when the script uses the `$msgTable` variable to display user messages, the messages are displayed in Arabic.</span></span>

<span data-ttu-id="a8893-148">예를 들어 다음 스크립트는 아랍어의 "사용자 이름을 입력 하십시오." 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-148">For example, the following script displays the "Please enter your user name" message in Arabic:</span></span>

```powershell
if (!($username)) { $msgTable.promptMsg }
```

<span data-ttu-id="a8893-149">`Import-LocalizedData` `.psd1` 가의 값과 일치 하는 파일을 찾을 수 없는 경우 `$PSUIculture` 의 값은 `$msgTable` 대체 되지 않으며에 대 한 호출은 `$msgTable.promptMsg` 대체 en-us 문자열을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-149">If `Import-LocalizedData` cannot find a `.psd1` file that matches the value of `$PSUIculture`, the value of `$msgTable` is not replaced, and the call to `$msgTable.promptMsg` displays the fallback en-US strings.</span></span>

## <a name="examples"></a><span data-ttu-id="a8893-150">예</span><span class="sxs-lookup"><span data-stu-id="a8893-150">Examples</span></span>

<span data-ttu-id="a8893-151">이 예에서는 스크립트에서 스크립트 국제화 기능을 사용 하 여 컴퓨터에 설정 된 언어로 사용자에 게 요일을 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-151">This example shows how the script internationalization features are used in a script to display a day of the week to users in the language that is set on the computer.</span></span>

<span data-ttu-id="a8893-152">다음은 Sample1.ps1 스크립트 파일의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-152">The following is a complete listing of the Sample1.ps1 script file.</span></span>

<span data-ttu-id="a8893-153">이 스크립트는 명령을 포함 하는 Day ($Day) 라는 데이터 섹션으로 시작 합니다 `ConvertFrom-StringData` .</span><span class="sxs-lookup"><span data-stu-id="a8893-153">The script begins with a Data section named Day ($Day) that contains a `ConvertFrom-StringData` command.</span></span> <span data-ttu-id="a8893-154">에 제출 된 식은 `ConvertFrom-StringData` 키/값 쌍의 기본 UI 문화권 en-us에서 요일 이름을 포함 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-154">The expression submitted to `ConvertFrom-StringData` is a here-string that contains the day names in the default UI culture, en-US, in key/value pairs.</span></span> <span data-ttu-id="a8893-155">`ConvertFrom-StringData`Cmdlet은이 문자열의 키/값 쌍을 해시 테이블로 변환한 다음 변수 값에 저장 합니다 `$Day` .</span><span class="sxs-lookup"><span data-stu-id="a8893-155">The `ConvertFrom-StringData` cmdlet converts the key/value pairs in the here-string into a hash table and then saves it in the value of the `$Day` variable.</span></span>

<span data-ttu-id="a8893-156">`Import-LocalizedData` `.psd1` 이 명령은 자동 변수의 값과 일치 하는 디렉터리에 있는 파일의 내용을 가져온 `$PSUICulture` 다음 변수에 저장 하 여 `$Day` `$Day` 데이터 섹션에 정의 된 값을 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-156">The `Import-LocalizedData` command imports the contents of the `.psd1` file in the directory that matches the value of the `$PSUICulture` automatic variable and then saves it in the `$Day` variable, replacing the values of `$Day` that are defined in the Data section.</span></span>

<span data-ttu-id="a8893-157">나머지 명령은 문자열을 배열로 로드 하 고 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-157">The remaining commands load the strings into an array and display them.</span></span>

```powershell
$Day = Data {
#culture="en-US"
ConvertFrom-StringData -StringData @'
    messageDate = Today is
    d0 = Sunday
    d1 = Monday
    d2 = Tuesday
    d3 = Wednesday
    d4 = Thursday
    d5 = Friday
    d6 = Saturday
'@
}

Import-LocalizedData -BindingVariable Day

#Build an array of weekdays.
$a = $Day.d0, $Day.d1, $Day.d2, $Day.d3, $Day.d4, $Day.d5, $Day.d6

# Get the day of the week as a number (Monday = 1).
# Index into $a to get the name of the day.
# Use string formatting to build a sentence.

"{0} {1}" -f $Day.messageDate, $a[(Get-Date -UFormat %u)] | Out-Host
```

<span data-ttu-id="a8893-158">`.psd1`스크립트를 지 원하는 파일은 해당 값과 일치 하는 이름을 가진 스크립트 디렉터리의 하위 디렉터리에 저장 됩니다 `$PSUICulture` .</span><span class="sxs-lookup"><span data-stu-id="a8893-158">The `.psd1` files that support the script are saved in subdirectories of the script directory with names that match the `$PSUICulture` values.</span></span>

<span data-ttu-id="a8893-159">다음은의 전체 목록입니다 `.\de-DE\sample1.psd1` .</span><span class="sxs-lookup"><span data-stu-id="a8893-159">The following is a complete listing of `.\de-DE\sample1.psd1`:</span></span>

```powershell
# culture="de-DE"
ConvertFrom-StringData @'
    messageDate = Heute ist
    d0 = Sonntag
    d1 = Montag
    d2 = Dienstag
    d3 = Mittwoch
    d4 = Donnerstag
    d5 = Freitag
    d6 = Samstag
'@
```

<span data-ttu-id="a8893-160">따라서 값이 de-de 인 시스템에서 Sample.ps1를 실행 하는 경우 `$PSUICulture` 스크립트의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a8893-160">As a result, when you run Sample.ps1 on a system on which the value of `$PSUICulture` is de-DE, the output of the script is:</span></span>

```Output
Heute ist Freitag
```

## <a name="see-also"></a><span data-ttu-id="a8893-161">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8893-161">See also</span></span>

- [<span data-ttu-id="a8893-162">about_Data_Sections</span><span class="sxs-lookup"><span data-stu-id="a8893-162">about_Data_Sections</span></span>](about_Data_Sections.md)
- [<span data-ttu-id="a8893-163">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="a8893-163">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)
- [<span data-ttu-id="a8893-164">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="a8893-164">about_Hash_Tables</span></span>](about_Hash_Tables.md)
- [<span data-ttu-id="a8893-165">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="a8893-165">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="a8893-166">ConvertFrom-StringData</span><span class="sxs-lookup"><span data-stu-id="a8893-166">ConvertFrom-StringData</span></span>](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)
- [<span data-ttu-id="a8893-167">Import-LocalizedData</span><span class="sxs-lookup"><span data-stu-id="a8893-167">Import-LocalizedData</span></span>](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)
