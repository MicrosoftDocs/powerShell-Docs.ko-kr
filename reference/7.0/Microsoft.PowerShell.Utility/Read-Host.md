---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: aacc89001373ecc8ef75e630f965a8d807bd4ac3
ms.sourcegitcommit: 57df49488015e7ac17ff1df402a94441aa6d6064
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2020
ms.locfileid: "93217921"
---
# <span data-ttu-id="31bed-103">Read-Host</span><span class="sxs-lookup"><span data-stu-id="31bed-103">Read-Host</span></span>

## <span data-ttu-id="31bed-104">개요</span><span class="sxs-lookup"><span data-stu-id="31bed-104">SYNOPSIS</span></span>
<span data-ttu-id="31bed-105">콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-105">Reads a line of input from the console.</span></span>

## <span data-ttu-id="31bed-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="31bed-106">SYNTAX</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="31bed-107">설명</span><span class="sxs-lookup"><span data-stu-id="31bed-107">DESCRIPTION</span></span>

<span data-ttu-id="31bed-108">`Read-Host`Cmdlet은 콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-108">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="31bed-109">이 cmdlet을 사용하여 사용자에게 입력하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-109">You can use it to prompt a user for input.</span></span> <span data-ttu-id="31bed-110">입력을 보안 문자열로 저장할 수 있으므로 이 cmdlet을 사용하여 암호 등의 보안 데이터와 공유 데이터를 입력하라는 메시지를 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-110">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="31bed-111">예제</span><span class="sxs-lookup"><span data-stu-id="31bed-111">EXAMPLES</span></span>

### <span data-ttu-id="31bed-112">예제 1: 콘솔 입력을 변수에 저장</span><span class="sxs-lookup"><span data-stu-id="31bed-112">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="31bed-113">이 예에서는 "age를 입력 하십시오." 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-113">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="31bed-114">값을 입력 하 고 Enter 키를 누르면 값이 변수에 저장 됩니다 `$Age` .</span><span class="sxs-lookup"><span data-stu-id="31bed-114">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="31bed-115">예제 2: 콘솔 입력을 보안 문자열로 저장</span><span class="sxs-lookup"><span data-stu-id="31bed-115">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="31bed-116">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-116">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="31bed-117">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-117">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="31bed-118">Enter 키를 누르면 값이 변수에 **SecureString** 개체로 저장 됩니다 `$pwd_secure_string` .</span><span class="sxs-lookup"><span data-stu-id="31bed-118">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

## <span data-ttu-id="31bed-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="31bed-119">PARAMETERS</span></span>

### <span data-ttu-id="31bed-120">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="31bed-120">-AsSecureString</span></span>

<span data-ttu-id="31bed-121">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-121">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="31bed-122">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **SecureString** 개체 ( **system.web** )입니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-122">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object ( **System.Security.SecureString** ).</span></span>

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

### <span data-ttu-id="31bed-123">-Prompt</span><span class="sxs-lookup"><span data-stu-id="31bed-123">-Prompt</span></span>

<span data-ttu-id="31bed-124">프롬프트 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-124">Specifies the text of the prompt.</span></span>
<span data-ttu-id="31bed-125">문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-125">Type a string.</span></span>
<span data-ttu-id="31bed-126">문자열에 공백이 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-126">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="31bed-127">PowerShell은 입력 한 텍스트에 콜론 ()을 추가 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-127">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="31bed-128">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="31bed-128">CommonParameters</span></span>

<span data-ttu-id="31bed-129">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="31bed-129">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="31bed-130">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31bed-130">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="31bed-131">입력</span><span class="sxs-lookup"><span data-stu-id="31bed-131">INPUTS</span></span>

### <span data-ttu-id="31bed-132">없음</span><span class="sxs-lookup"><span data-stu-id="31bed-132">None</span></span>

<span data-ttu-id="31bed-133">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-133">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="31bed-134">출력</span><span class="sxs-lookup"><span data-stu-id="31bed-134">OUTPUTS</span></span>

### <span data-ttu-id="31bed-135">System.string 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="31bed-135">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="31bed-136">**Assecurestring** 매개 변수를 사용 하는 경우은 `Read-Host` **SecureString** 을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-136">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="31bed-137">그러지 않으면 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="31bed-137">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="31bed-138">참고</span><span class="sxs-lookup"><span data-stu-id="31bed-138">NOTES</span></span>

## <span data-ttu-id="31bed-139">관련 링크</span><span class="sxs-lookup"><span data-stu-id="31bed-139">RELATED LINKS</span></span>

[<span data-ttu-id="31bed-140">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="31bed-140">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="31bed-141">Get-Host</span><span class="sxs-lookup"><span data-stu-id="31bed-141">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="31bed-142">Write-Host</span><span class="sxs-lookup"><span data-stu-id="31bed-142">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="31bed-143">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="31bed-143">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
