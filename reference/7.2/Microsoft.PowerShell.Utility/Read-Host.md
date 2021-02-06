---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/read-host?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Read-Host
ms.openlocfilehash: 2efe75730ef7d35618dc0d1fbf7a8d6f8a5db5ae
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601062"
---
# <span data-ttu-id="ffb5f-102">Read-Host</span><span class="sxs-lookup"><span data-stu-id="ffb5f-102">Read-Host</span></span>

## <span data-ttu-id="ffb5f-103">개요</span><span class="sxs-lookup"><span data-stu-id="ffb5f-103">SYNOPSIS</span></span>
<span data-ttu-id="ffb5f-104">콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-104">Reads a line of input from the console.</span></span>

## <span data-ttu-id="ffb5f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ffb5f-105">SYNTAX</span></span>

### <span data-ttu-id="ffb5f-106">AsString (기본값)</span><span class="sxs-lookup"><span data-stu-id="ffb5f-106">AsString (Default)</span></span>

```
Read-Host [[-Prompt] <Object>] [-MaskInput] [<CommonParameters>]
```

### <span data-ttu-id="ffb5f-107">AsSecureString</span><span class="sxs-lookup"><span data-stu-id="ffb5f-107">AsSecureString</span></span>

```
Read-Host [[-Prompt] <Object>] [-AsSecureString] [<CommonParameters>]
```

## <span data-ttu-id="ffb5f-108">설명</span><span class="sxs-lookup"><span data-stu-id="ffb5f-108">DESCRIPTION</span></span>

<span data-ttu-id="ffb5f-109">`Read-Host`Cmdlet은 콘솔에서 입력 줄을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-109">The `Read-Host` cmdlet reads a line of input from the console.</span></span> <span data-ttu-id="ffb5f-110">이 cmdlet을 사용하여 사용자에게 입력하라는 메시지를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-110">You can use it to prompt a user for input.</span></span> <span data-ttu-id="ffb5f-111">입력을 보안 문자열로 저장할 수 있으므로 이 cmdlet을 사용하여 암호 등의 보안 데이터와 공유 데이터를 입력하라는 메시지를 사용자에게 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-111">Because you can save the input as a secure string, you can use this cmdlet to prompt users for secure data, such as passwords, as well as shared data.</span></span>

## <span data-ttu-id="ffb5f-112">예제</span><span class="sxs-lookup"><span data-stu-id="ffb5f-112">EXAMPLES</span></span>

### <span data-ttu-id="ffb5f-113">예제 1: 콘솔 입력을 변수에 저장</span><span class="sxs-lookup"><span data-stu-id="ffb5f-113">Example 1: Save console input to a variable</span></span>

<span data-ttu-id="ffb5f-114">이 예에서는 "age를 입력 하십시오." 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-114">This example displays the string "Please enter your age:" as a prompt.</span></span> <span data-ttu-id="ffb5f-115">값을 입력 하 고 Enter 키를 누르면 값이 변수에 저장 됩니다 `$Age` .</span><span class="sxs-lookup"><span data-stu-id="ffb5f-115">When a value is entered and the Enter key is pressed, the value is stored in the `$Age` variable.</span></span>

```powershell
$Age = Read-Host "Please enter your age"
```

### <span data-ttu-id="ffb5f-116">예제 2: 콘솔 입력을 보안 문자열로 저장</span><span class="sxs-lookup"><span data-stu-id="ffb5f-116">Example 2: Save console input as a secure string</span></span>

<span data-ttu-id="ffb5f-117">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-117">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="ffb5f-118">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-118">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="ffb5f-119">Enter 키를 누르면 값이 변수에 **SecureString** 개체로 저장 됩니다 `$pwd_secure_string` .</span><span class="sxs-lookup"><span data-stu-id="ffb5f-119">When the Enter key is pressed, the value is stored as a **SecureString** object in the `$pwd_secure_string` variable.</span></span>

```powershell
$pwd_secure_string = Read-Host "Enter a Password" -AsSecureString
```

### <span data-ttu-id="ffb5f-120">예제 3: 입력 및 일반 텍스트 문자열로 마스크</span><span class="sxs-lookup"><span data-stu-id="ffb5f-120">Example 3: Mask input and as a plaintext string</span></span>

<span data-ttu-id="ffb5f-121">이 예에서는 "Enter a Password:" 문자열을 프롬프트로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-121">This example displays the string "Enter a Password:" as a prompt.</span></span> <span data-ttu-id="ffb5f-122">값을 입력 하면 입력 대신 별표 ( `*` )가 콘솔에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-122">As a value is being entered, asterisks (`*`) appear on the console in place of the input.</span></span> <span data-ttu-id="ffb5f-123">Enter 키를 누르면 값이 변수에 일반 텍스트 **문자열** 개체로 저장 됩니다 `$pwd_string` .</span><span class="sxs-lookup"><span data-stu-id="ffb5f-123">When the Enter key is pressed, the value is stored as a plaintext **String** object in the `$pwd_string` variable.</span></span>

```powershell
$pwd_string = Read-Host "Enter a Password" -MaskInput
```

## <span data-ttu-id="ffb5f-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ffb5f-124">PARAMETERS</span></span>

### <span data-ttu-id="ffb5f-125">-AsSecureString</span><span class="sxs-lookup"><span data-stu-id="ffb5f-125">-AsSecureString</span></span>

<span data-ttu-id="ffb5f-126">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-126">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="ffb5f-127">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **SecureString** 개체 (**system.web**)입니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-127">When you use this parameter, the output of the `Read-Host` cmdlet is a **SecureString** object (**System.Security.SecureString**).</span></span>

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

### <span data-ttu-id="ffb5f-128">-MaskInput</span><span class="sxs-lookup"><span data-stu-id="ffb5f-128">-MaskInput</span></span>

<span data-ttu-id="ffb5f-129">Cmdlet이 `*` 사용자가 입력으로 입력 하는 문자 대신 별표 ()를 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-129">Indicates that the cmdlet displays asterisks (`*`) in place of the characters that the user types as input.</span></span> <span data-ttu-id="ffb5f-130">이 매개 변수를 사용 하는 경우 cmdlet의 출력은 `Read-Host` **문자열** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-130">When you use this parameter, the output of the `Read-Host` cmdlet is a **String** object.</span></span>
<span data-ttu-id="ffb5f-131">이렇게 하면 **SecureString** 대신 일반 텍스트로 반환 되는 암호를 안전 하 게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-131">This allows you to safely prompt for a password that is returned as plaintext instead of **SecureString**.</span></span>

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

### <span data-ttu-id="ffb5f-132">-Prompt</span><span class="sxs-lookup"><span data-stu-id="ffb5f-132">-Prompt</span></span>

<span data-ttu-id="ffb5f-133">프롬프트 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-133">Specifies the text of the prompt.</span></span>
<span data-ttu-id="ffb5f-134">문자열을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-134">Type a string.</span></span>
<span data-ttu-id="ffb5f-135">문자열에 공백이 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-135">If the string includes spaces, enclose it in quotation marks.</span></span>
<span data-ttu-id="ffb5f-136">PowerShell은 입력 한 텍스트에 콜론 ()을 추가 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-136">PowerShell appends a colon (`:`) to the text that you enter.</span></span>

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

### <span data-ttu-id="ffb5f-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ffb5f-137">CommonParameters</span></span>

<span data-ttu-id="ffb5f-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ffb5f-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ffb5f-140">입력</span><span class="sxs-lookup"><span data-stu-id="ffb5f-140">INPUTS</span></span>

### <span data-ttu-id="ffb5f-141">없음</span><span class="sxs-lookup"><span data-stu-id="ffb5f-141">None</span></span>

<span data-ttu-id="ffb5f-142">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="ffb5f-143">출력</span><span class="sxs-lookup"><span data-stu-id="ffb5f-143">OUTPUTS</span></span>

### <span data-ttu-id="ffb5f-144">System.string 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="ffb5f-144">System.String or System.Security.SecureString</span></span>

<span data-ttu-id="ffb5f-145">**Assecurestring** 매개 변수를 사용 하는 경우은 `Read-Host` **SecureString** 을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-145">If the **AsSecureString** parameter is used, `Read-Host` returns a **SecureString**.</span></span> <span data-ttu-id="ffb5f-146">그러지 않으면 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffb5f-146">Otherwise, it returns a string.</span></span>

## <span data-ttu-id="ffb5f-147">참고</span><span class="sxs-lookup"><span data-stu-id="ffb5f-147">NOTES</span></span>

## <span data-ttu-id="ffb5f-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ffb5f-148">RELATED LINKS</span></span>

[<span data-ttu-id="ffb5f-149">Clear-Host</span><span class="sxs-lookup"><span data-stu-id="ffb5f-149">Clear-Host</span></span>](../microsoft.powershell.core/clear-host.md)

[<span data-ttu-id="ffb5f-150">Get-Host</span><span class="sxs-lookup"><span data-stu-id="ffb5f-150">Get-Host</span></span>](Get-Host.md)

[<span data-ttu-id="ffb5f-151">Write-Host</span><span class="sxs-lookup"><span data-stu-id="ffb5f-151">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="ffb5f-152">ConvertFrom-SecureString</span><span class="sxs-lookup"><span data-stu-id="ffb5f-152">ConvertFrom-SecureString</span></span>](../Microsoft.PowerShell.Security/ConvertFrom-SecureString.md)
