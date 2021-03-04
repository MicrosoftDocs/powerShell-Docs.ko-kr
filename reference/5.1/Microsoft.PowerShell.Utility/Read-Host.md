---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 83ddac1e157f26d6a437716e9ae95e258aa1eecb
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685849"
---
# <span data-ttu-id="b6740-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="b6740-103">Read-Host</span></span>

## <span data-ttu-id="b6740-104">개요</span><span class="sxs-lookup"><span data-stu-id="b6740-104">SYNOPSIS</span></span>
<span data-ttu-id="b6740-105">콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="b6740-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b6740-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="b6740-107">설명</span><span class="sxs-lookup"><span data-stu-id="b6740-107">DESCRIPTION</span></span>

<span data-ttu-id="b6740-108">`Read-Host`Cmdlet은 콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="b6740-109">이 cmdlet을 사용하여 사용자에게 입력하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="b6740-110">입력을 보안 문자열로 저장할 수 있으므로 이 cmdlet을 사용하여 암호 등의 보안 데이터와 공유 데이터를 입력하라는 메시지를 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="b6740-111">`Read-Host` 는 사용자의 입력으로 수락할 수 있는 8190 자로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-111">`Read-Host` has a limit of 8190 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="b6740-112">예제</span><span class="sxs-lookup"><span data-stu-id="b6740-112">EXAMPLES</span></span>

### <span data-ttu-id="b6740-113">예제 1: 콘솔 입력을 변수에 저장</span><span class="sxs-lookup"><span data-stu-id="b6740-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="b6740-114">이 예에서는 "age를 입력 하십시오." 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="b6740-115">값을 입력 하 고 Enter 키를 누르면 값이 변수에 저장 됩니다 `$Age` .</span><span class="sxs-lookup"><span data-stu-id="b6740-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="b6740-116">예제 2: 콘솔 입력을 보안 문자열로 저장</span><span class="sxs-lookup"><span data-stu-id="b6740-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="b6740-117">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b6740-118">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b6740-119">Enter 키를 누르면 값이 변수에 **SecureString** 개체로 저장 됩니다 `$pwd_secure_string` .</span><span class="sxs-lookup"><span data-stu-id="b6740-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="b6740-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b6740-120">PARAMETERS</span></span>

### <span data-ttu-id="b6740-121">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b6740-121">-AsSecureString</span></span>

<span data-ttu-id="b6740-122">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-122">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b6740-123">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **SecureString** 개체 (**system.web**)입니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-123">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="b6740-124">-Prompt</span><span class="sxs-lookup"><span data-stu-id="b6740-124">-Prompt</span></span>

<span data-ttu-id="b6740-125">프롬프트 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-125">Specifies the text of the prompt.</span></span> <span data-ttu-id="b6740-126">문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-126">Type a string.</span></span> <span data-ttu-id="b6740-127">문자열에 공백이 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-127">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="b6740-128">PowerShell은 입력 한 텍스트에 콜론 ()을 추가 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-128">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b6740-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b6740-129">CommonParameters</span></span>

<span data-ttu-id="b6740-130">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b6740-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b6740-131">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6740-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b6740-132">입력</span><span class="sxs-lookup"><span data-stu-id="b6740-132">INPUTS</span></span>

### <span data-ttu-id="b6740-133">없음</span><span class="sxs-lookup"><span data-stu-id="b6740-133">None</span></span>

<span data-ttu-id="b6740-134">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-134">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b6740-135">출력</span><span class="sxs-lookup"><span data-stu-id="b6740-135">OUTPUTS</span></span>

### <span data-ttu-id="b6740-136">System.string 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="b6740-136">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="b6740-137">**Assecurestring** 매개 변수를 사용 하는 경우은 `Read-Host` **SecureString** 을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-137">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="b6740-138">그러지 않으면 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6740-138">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="b6740-139">참고</span><span class="sxs-lookup"><span data-stu-id="b6740-139">NOTES</span></span>

## <span data-ttu-id="b6740-140">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b6740-140">RELATED LINKS</span></span>

[<span data-ttu-id="b6740-141">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="b6740-141">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="b6740-142">Get-Host</span><span class="sxs-lookup"><span data-stu-id="b6740-142">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="b6740-143">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b6740-143">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b6740-144">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="b6740-144">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
