---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 03/02/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 5563413400abd28ce376265970631ad1206ca518
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685258"
---
# <span data-ttu-id="b2071-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="b2071-102">Read-Host</span></span>

## <span data-ttu-id="b2071-103">개요</span><span class="sxs-lookup"><span data-stu-id="b2071-103">SYNOPSIS</span></span>
<span data-ttu-id="b2071-104">콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="b2071-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2071-105">SYNTAX</span></span>

### <span data-ttu-id="b2071-106">AsString (기본값)</span><span class="sxs-lookup"><span data-stu-id="b2071-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="b2071-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b2071-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="b2071-108">설명</span><span class="sxs-lookup"><span data-stu-id="b2071-108">DESCRIPTION</span></span>

<span data-ttu-id="b2071-109">`Read-Host`Cmdlet은 콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="b2071-110">이 cmdlet을 사용하여 사용자에게 입력하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="b2071-111">입력을 보안 문자열로 저장할 수 있으므로 이 cmdlet을 사용하여 암호 등의 보안 데이터와 공유 데이터를 입력하라는 메시지를 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

> [!NOTE]
> <span data-ttu-id="b2071-112">`Read-Host` 는 사용자의 입력으로 수락할 수 있는 1022 자로 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-112">`Read-Host` has a limit of 1022 characters it can accept as input from a user.</span></span>

## <span data-ttu-id="b2071-113">예제</span><span class="sxs-lookup"><span data-stu-id="b2071-113">EXAMPLES</span></span>

### <span data-ttu-id="b2071-114">예제 1: 콘솔 입력을 변수에 저장</span><span class="sxs-lookup"><span data-stu-id="b2071-114">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="b2071-115">이 예에서는 "age를 입력 하십시오." 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-115">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="b2071-116">값을 입력 하 고 Enter 키를 누르면 값이 변수에 저장 됩니다 `$Age` .</span><span class="sxs-lookup"><span data-stu-id="b2071-116">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="b2071-117">예제 2: 콘솔 입력을 보안 문자열로 저장</span><span class="sxs-lookup"><span data-stu-id="b2071-117">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="b2071-118">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-118">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b2071-119">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-119">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b2071-120">Enter 키를 누르면 값이 변수에 **SecureString** 개체로 저장 됩니다 `$pwd_secure_string` .</span><span class="sxs-lookup"><span data-stu-id="b2071-120">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="b2071-121">예제 3: 입력 및 일반 텍스트 문자열로 마스크</span><span class="sxs-lookup"><span data-stu-id="b2071-121">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="b2071-122">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-122">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="b2071-123">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-123">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="b2071-124">Enter 키를 누르면 값이 변수에 일반 텍스트 **문자열** 개체로 저장 됩니다 `$pwd_string` .</span><span class="sxs-lookup"><span data-stu-id="b2071-124">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="b2071-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b2071-125">PARAMETERS</span></span>

### <span data-ttu-id="b2071-126">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="b2071-126">-AsSecureString</span></span>

<span data-ttu-id="b2071-127">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-127">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b2071-128">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **SecureString** 개체 (**system.web**)입니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-128">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsSecureString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2071-129">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="b2071-129">-MaskInput</span></span>

<span data-ttu-id="b2071-130">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-130">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="b2071-131">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-131">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="b2071-132">이렇게 하면 **SecureString** 대신 일반 텍스트로 반환 되는 암호를 안전 하 게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-132">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AsString
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b2071-133">-Prompt</span><span class="sxs-lookup"><span data-stu-id="b2071-133">-Prompt</span></span>

<span data-ttu-id="b2071-134">프롬프트 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-134">Specifies the text of the prompt.</span></span> <span data-ttu-id="b2071-135">문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-135">Type a string.</span></span> <span data-ttu-id="b2071-136">문자열에 공백이 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-136">If the string includes spaces, enclose it in quotation marks.</span></span> <span data-ttu-id="b2071-137">PowerShell은 입력 한 텍스트에 콜론 ()을 추가 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-137">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="b2071-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2071-138">CommonParameters</span></span>

<span data-ttu-id="b2071-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2071-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2071-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b2071-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2071-141">입력</span><span class="sxs-lookup"><span data-stu-id="b2071-141">INPUTS</span></span>

### <span data-ttu-id="b2071-142">없음</span><span class="sxs-lookup"><span data-stu-id="b2071-142">None</span></span>

<span data-ttu-id="b2071-143">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="b2071-144">출력</span><span class="sxs-lookup"><span data-stu-id="b2071-144">OUTPUTS</span></span>

### <span data-ttu-id="b2071-145">System.string 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="b2071-145">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="b2071-146">**Assecurestring** 매개 변수를 사용 하는 경우은 `Read-Host` **SecureString** 을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-146">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="b2071-147">그러지 않으면 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b2071-147">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="b2071-148">참고</span><span class="sxs-lookup"><span data-stu-id="b2071-148">NOTES</span></span>

## <span data-ttu-id="b2071-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b2071-149">RELATED LINKS</span></span>

[<span data-ttu-id="b2071-150">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="b2071-150">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="b2071-151">Get-Host</span><span class="sxs-lookup"><span data-stu-id="b2071-151">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="b2071-152">Write-Host</span><span class="sxs-lookup"><span data-stu-id="b2071-152">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="b2071-153">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="b2071-153">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
