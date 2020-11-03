---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/test-pssessionconfigurationfile?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-PSSessionConfigurationFile
ms.openlocfilehash: b240a66304a2721b1bae67ed2cca669f564e8f66
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212714"
---
# <span data-ttu-id="a7955-103">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a7955-103">Test-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="a7955-104">개요</span><span class="sxs-lookup"><span data-stu-id="a7955-104">SYNOPSIS</span></span>
<span data-ttu-id="a7955-105">세션 구성 파일에서 키와 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-105">Verifies the keys and values in a session configuration file.</span></span>

## <span data-ttu-id="a7955-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7955-106">SYNTAX</span></span>

```
Test-PSSessionConfigurationFile [-Path] <String> [<CommonParameters>]
```

## <span data-ttu-id="a7955-107">설명</span><span class="sxs-lookup"><span data-stu-id="a7955-107">DESCRIPTION</span></span>

<span data-ttu-id="a7955-108">이 cmdlet은 세션 구성 파일에 유효한 키가 포함 되어 있고 값이 올바른 형식 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-108">This cmdlet verifies that a session configuration file contains valid keys and the values are of the correct type.</span></span> <span data-ttu-id="a7955-109">열거형 값의 경우 cmdlet은 지정한 값이 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-109">For enumerated values, the cmdlet verifies that the specified values are valid.</span></span>

<span data-ttu-id="a7955-110">이 cmdlet은 `$True` 파일이 모든 테스트를 통과 하는 경우를 반환 하 고 `$False` 그렇지 않은 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-110">The cmdlet returns `$True` if the file passes all tests and `$False` if it does not.</span></span> <span data-ttu-id="a7955-111">오류를 찾으려면 **Verbose** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-111">To find any errors, use the **Verbose** parameter.</span></span>

<span data-ttu-id="a7955-112">`Test-PSSessionConfigurationFile` cmdlet에서 만든 파일 등의 세션 구성 파일을 확인 합니다 `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="a7955-112">`Test-PSSessionConfigurationFile` verifies the session configuration files, such as those created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="a7955-113">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7955-113">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span> <span data-ttu-id="a7955-114">세션 구성 파일에 대 한 자세한 내용은 [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7955-114">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="a7955-115">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-115">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="a7955-116">예제</span><span class="sxs-lookup"><span data-stu-id="a7955-116">EXAMPLES</span></span>

### <span data-ttu-id="a7955-117">예제 1: 세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="a7955-117">Example 1: Test a session configuration file</span></span>

```powershell
Test-PSSessionConfigurationFile -Path "FullLanguage.pssc"
```

```Output
True
```

### <span data-ttu-id="a7955-118">예 2: 세션 구성의 세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="a7955-118">Example 2: Test the session configuration file of a session configuration</span></span>

<span data-ttu-id="a7955-119">이 예제에서는 **제한** 된 세션 구성에 사용 되는 구성 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-119">In this example, we test the configuration file used in the **Restricted** session configuration.</span></span>
<span data-ttu-id="a7955-120">**Path** 매개 변수 값은 `Get-PSSessionConfiguration` **제한** 된 세션 구성을 가져오는 명령의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-120">The value of the **Path** parameter is the result of the `Get-PSSessionConfiguration` command that gets the **Restricted** session configuration.</span></span> <span data-ttu-id="a7955-121">세션 구성 파일의 경로는 세션 구성의 **Configfilepath** 속성 값에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-121">The path of the session configuration file is stored in the value of the **ConfigFilePath** property of the session configuration.</span></span>

```powershell
Test-PSSessionConfigurationFile -Path (Get-PSSessionConfiguration -Name Restricted).ConfigFilePath
```

### <span data-ttu-id="a7955-122">예제 3: 모든 세션 구성 파일 테스트</span><span class="sxs-lookup"><span data-stu-id="a7955-122">Example 3: Test all session configuration files</span></span>

<span data-ttu-id="a7955-123">이 예제의 함수는 로컬 컴퓨터의 모든 세션 구성 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-123">The function in this example tests all session configuration files on the local computer.</span></span> <span data-ttu-id="a7955-124">함수는 cmdlet을 사용 하 여 `Get-PSSessionConfiguration` 모든 세션 구성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-124">The function uses the `Get-PSSessionConfiguration` cmdlet to get all session configurations.</span></span> <span data-ttu-id="a7955-125">루프 내의 코드는 `ForEach-Object` 파일 경로를 표시 하 고 각 세션 구성을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-125">The code inside the `ForEach-Object` loop displays the file path and tests each of the session configurations.</span></span>

```powershell
function Test-AllConfigFiles
{
    Get-PSSessionConfiguration | ForEach-Object {
        if ($_.ConfigFilePath) {
            $_.ConfigFilePath
            Test-PSSessionConfigurationFile -Verbose -Path $_.ConfigFilePath
        }
    }
}
Test-AllConfigFiles
```

```Output
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Empty_6fd77bf6-e084-4372-bd8a-af3e207354d3.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
VERBOSE: The member 'AliasDefinitions' must contain the required key 'Description'. Add the require key
to the fileC:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc.
False
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\NoLanguage_0c115179-ff2a-4f66-a5eb-e56e5692ba22.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RestrictedLang_b6bd9474-0a6c-4e06-8722-c2c95bb10d3e.pssc
True
C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\RRS_3fb29420-2c87-46e5-a402-e21436331efc.pssc
True
```

<span data-ttu-id="a7955-126">세션 구성의 **Configfilepath** 속성에는 세션 구성에 사용 되는 세션 구성 파일의 경로 (있는 경우)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-126">The **ConfigFilePath** property of a session configuration contains the path of the session configuration file that is used in the session configuration, if any.</span></span>

<span data-ttu-id="a7955-127">**ConfigFilePath** 속성 값이 채워져 있을 경우(true) 이 명령은 **ConfigFilePath** 속성 값을 가져옵니다(인쇄).</span><span class="sxs-lookup"><span data-stu-id="a7955-127">If the value of the **ConfigFilePath** property is populated (is true), the command gets (prints) the **ConfigFilePath** property value.</span></span> <span data-ttu-id="a7955-128">그런 다음 cmdlet을 사용 하 여 `Test-PSSessionConfigurationFile` **configfilepath** 값의 파일을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-128">Then it uses the `Test-PSSessionConfigurationFile` cmdlet to test the file in the **ConfigFilePath** value.</span></span> <span data-ttu-id="a7955-129">**Verbose** 매개 변수는 파일이 테스트에 실패할 경우 파일 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-129">The **Verbose** parameter returns the file error when the file fails the test.</span></span>

## <span data-ttu-id="a7955-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7955-130">PARAMETERS</span></span>

### <span data-ttu-id="a7955-131">-Path</span><span class="sxs-lookup"><span data-stu-id="a7955-131">-Path</span></span>

<span data-ttu-id="a7955-132">세션 구성 파일 (.psc)의 경로와 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-132">Specifies the path and filename of a session configuration file (.pssc).</span></span> <span data-ttu-id="a7955-133">경로를 생략할 경우 기본값은 현재 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-133">If you omit the path, the default is the current folder.</span></span> <span data-ttu-id="a7955-134">와일드 카드 문자는 지원 되지만 단일 파일로 확인 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7955-134">Wildcard characters are supported, but they must resolve to a single file.</span></span> <span data-ttu-id="a7955-135">세션 구성 파일 경로를로 파이프 할 수도 있습니다 `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="a7955-135">You can also pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="a7955-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7955-136">CommonParameters</span></span>

<span data-ttu-id="a7955-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7955-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7955-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7955-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7955-139">입력</span><span class="sxs-lookup"><span data-stu-id="a7955-139">INPUTS</span></span>

### <span data-ttu-id="a7955-140">System.String</span><span class="sxs-lookup"><span data-stu-id="a7955-140">System.String</span></span>

<span data-ttu-id="a7955-141">세션 구성 파일 경로를로 파이프 할 수 있습니다 `Test-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="a7955-141">You can pipe a session configuration file path to `Test-PSSessionConfigurationFile`.</span></span>

## <span data-ttu-id="a7955-142">출력</span><span class="sxs-lookup"><span data-stu-id="a7955-142">OUTPUTS</span></span>

### <span data-ttu-id="a7955-143">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="a7955-143">System.Boolean</span></span>

## <span data-ttu-id="a7955-144">참고</span><span class="sxs-lookup"><span data-stu-id="a7955-144">NOTES</span></span>

## <span data-ttu-id="a7955-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a7955-145">RELATED LINKS</span></span>

[<span data-ttu-id="a7955-146">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-146">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-147">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-147">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-148">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-148">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-149">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a7955-149">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="a7955-150">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="a7955-150">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="a7955-151">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-151">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-152">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-152">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-153">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a7955-153">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="a7955-154">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a7955-154">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="a7955-155">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="a7955-155">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="a7955-156">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="a7955-156">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="a7955-157">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="a7955-157">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
