---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: 883990ace87c947ad9f0e10100d4d1dc7f1b8cbe
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224377"
---
# <span data-ttu-id="bd349-103">Write-Error</span><span class="sxs-lookup"><span data-stu-id="bd349-103">Write-Error</span></span>

## <span data-ttu-id="bd349-104">개요</span><span class="sxs-lookup"><span data-stu-id="bd349-104">SYNOPSIS</span></span>
<span data-ttu-id="bd349-105">오류 스트림에 개체를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-105">Writes an object to the error stream.</span></span>

## <span data-ttu-id="bd349-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd349-106">SYNTAX</span></span>

### <span data-ttu-id="bd349-107">NoException (기본값)</span><span class="sxs-lookup"><span data-stu-id="bd349-107">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="bd349-108">WithException</span><span class="sxs-lookup"><span data-stu-id="bd349-108">WithException</span></span>

```
Write-Error -Exception <Exception> [-Message <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="bd349-109">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="bd349-109">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="bd349-110">설명</span><span class="sxs-lookup"><span data-stu-id="bd349-110">DESCRIPTION</span></span>

<span data-ttu-id="bd349-111">`Write-Error`Cmdlet는 종료 되지 않는 오류를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-111">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="bd349-112">기본적으로 오류는 출력과 함께 표시되도록 오류 스트림을 통해 호스트 프로그램에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-112">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="bd349-113">종료되지 않는 오류를 쓰려면 오류 메시지 문자열, **ErrorRecord** 개체 또는 **Exception** 개체를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-113">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="bd349-114">의 다른 매개 변수 `Write-Error` 를 사용 하 여 오류 레코드를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-114">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="bd349-115">종료되지 않는 오류는 오류 스트림에 오류를 쓰지만 명령 처리를 중지하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-115">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="bd349-116">입력 항목 컬렉션에 있는 하나의 항목에서 종료되지 않는 오류가 선언될 경우 명령이 컬렉션의 다른 항목을 계속 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-116">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="bd349-117">종료 오류를 선언 하려면 키워드를 사용 `Throw` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-117">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="bd349-118">자세한 내용은 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd349-118">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="bd349-119">예제</span><span class="sxs-lookup"><span data-stu-id="bd349-119">EXAMPLES</span></span>

### <span data-ttu-id="bd349-120">예 1: RegistryKey 개체에 대 한 오류 쓰기</span><span class="sxs-lookup"><span data-stu-id="bd349-120">Example 1: Write an error for RegistryKey object</span></span>

```powershell
Get-ChildItem | ForEach-Object {
    if ($_.GetType().ToString() -eq "Microsoft.Win32.RegistryKey")
    {
        Write-Error "Invalid object" -ErrorId B1 -TargetObject $_
    }
    else
    {
        $_
    }
}
```

<span data-ttu-id="bd349-121">이 명령은 `Get-ChildItem` cmdlet이 `Microsoft.Win32.RegistryKey` `HKLM:` PowerShell 레지스트리 공급자의 또는 드라이브에 있는 개체와 같은 개체를 반환할 때 종료 되지 않는 오류를 선언 `HKCU:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-121">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="bd349-122">예제 2: 콘솔에 오류 메시지 쓰기</span><span class="sxs-lookup"><span data-stu-id="bd349-122">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="bd349-123">이 명령은 종료되지 않는 오류를 선언하고 "액세스 거부됨" 오류를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-123">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="bd349-124">**Message** 매개 변수를 사용하여 메시지를 지정하지만 선택적 매개 변수 이름 **Message** 는 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-124">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="bd349-125">예 3: 콘솔에 오류를 기록 하 고 범주 지정</span><span class="sxs-lookup"><span data-stu-id="bd349-125">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="bd349-126">이 명령은 종료되지 않는 오류를 선언하고 오류 범주를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-126">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="bd349-127">예제 4: 예외 개체를 사용 하 여 오류 쓰기</span><span class="sxs-lookup"><span data-stu-id="bd349-127">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="bd349-128">이 명령은 **Exception** 개체를 사용하여 종료되지 않는 오류를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-128">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="bd349-129">첫 번째 명령은 해시 테이블을 사용하여 **System.Exception** 개체를 만들고</span><span class="sxs-lookup"><span data-stu-id="bd349-129">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="bd349-130">이 메서드는 예외 개체를 `$E` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-130">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="bd349-131">해시 테이블을 사용하여 null 생성자가 있는 유형의 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-131">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="bd349-132">두 번째 명령은 cmdlet을 사용 하 여 `Write-Error` 종료 되지 않는 오류를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-132">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="bd349-133">**Exception** 매개 변수 값은 변수의 **예외** 개체입니다 `$E` .</span><span class="sxs-lookup"><span data-stu-id="bd349-133">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="bd349-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="bd349-134">PARAMETERS</span></span>

### <span data-ttu-id="bd349-135">-범주</span><span class="sxs-lookup"><span data-stu-id="bd349-135">-Category</span></span>

<span data-ttu-id="bd349-136">오류의 범주를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-136">Specifies the category of the error.</span></span> <span data-ttu-id="bd349-137">기본값은 **NotSpecified** 입니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-137">The default value is **NotSpecified** .</span></span> <span data-ttu-id="bd349-138">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-138">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bd349-139">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="bd349-139">NotSpecified</span></span>
- <span data-ttu-id="bd349-140">OpenError</span><span class="sxs-lookup"><span data-stu-id="bd349-140">OpenError</span></span>
- <span data-ttu-id="bd349-141">CloseError</span><span class="sxs-lookup"><span data-stu-id="bd349-141">CloseError</span></span>
- <span data-ttu-id="bd349-142">DeviceError</span><span class="sxs-lookup"><span data-stu-id="bd349-142">DeviceError</span></span>
- <span data-ttu-id="bd349-143">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="bd349-143">DeadlockDetected</span></span>
- <span data-ttu-id="bd349-144">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="bd349-144">InvalidArgument</span></span>
- <span data-ttu-id="bd349-145">InvalidData</span><span class="sxs-lookup"><span data-stu-id="bd349-145">InvalidData</span></span>
- <span data-ttu-id="bd349-146">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="bd349-146">InvalidOperation</span></span>
- <span data-ttu-id="bd349-147">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="bd349-147">InvalidResult</span></span>
- <span data-ttu-id="bd349-148">InvalidType</span><span class="sxs-lookup"><span data-stu-id="bd349-148">InvalidType</span></span>
- <span data-ttu-id="bd349-149">MetadataError</span><span class="sxs-lookup"><span data-stu-id="bd349-149">MetadataError</span></span>
- <span data-ttu-id="bd349-150">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="bd349-150">NotImplemented</span></span>
- <span data-ttu-id="bd349-151">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="bd349-151">NotInstalled</span></span>
- <span data-ttu-id="bd349-152">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="bd349-152">ObjectNotFound</span></span>
- <span data-ttu-id="bd349-153">OperationStopped 됨</span><span class="sxs-lookup"><span data-stu-id="bd349-153">OperationStopped</span></span>
- <span data-ttu-id="bd349-154">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="bd349-154">OperationTimeout</span></span>
- <span data-ttu-id="bd349-155">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="bd349-155">SyntaxError</span></span>
- <span data-ttu-id="bd349-156">ParserError</span><span class="sxs-lookup"><span data-stu-id="bd349-156">ParserError</span></span>
- <span data-ttu-id="bd349-157">이상 거부 됨</span><span class="sxs-lookup"><span data-stu-id="bd349-157">PermissionDenied</span></span>
- <span data-ttu-id="bd349-158">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="bd349-158">ResourceBusy</span></span>
- <span data-ttu-id="bd349-159">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="bd349-159">ResourceExists</span></span>
- <span data-ttu-id="bd349-160">ResourceUnavailable 수 없음</span><span class="sxs-lookup"><span data-stu-id="bd349-160">ResourceUnavailable</span></span>
- <span data-ttu-id="bd349-161">ReadError</span><span class="sxs-lookup"><span data-stu-id="bd349-161">ReadError</span></span>
- <span data-ttu-id="bd349-162">WriteError</span><span class="sxs-lookup"><span data-stu-id="bd349-162">WriteError</span></span>
- <span data-ttu-id="bd349-163">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="bd349-163">FromStdErr</span></span>
- <span data-ttu-id="bd349-164">SecurityError</span><span class="sxs-lookup"><span data-stu-id="bd349-164">SecurityError</span></span>
- <span data-ttu-id="bd349-165">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="bd349-165">ProtocolError</span></span>
- <span data-ttu-id="bd349-166">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="bd349-166">ConnectionError</span></span>
- <span data-ttu-id="bd349-167">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="bd349-167">AuthenticationError</span></span>
- <span data-ttu-id="bd349-168">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="bd349-168">LimitsExceeded</span></span>
- <span data-ttu-id="bd349-169">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="bd349-169">QuotaExceeded</span></span>
- <span data-ttu-id="bd349-170">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="bd349-170">NotEnabled</span></span>

<span data-ttu-id="bd349-171">오류 범주에 대 한 자세한 내용은 [ErrorCategory 열거형](https://go.microsoft.com/fwlink/?LinkId=143600)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bd349-171">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

```yaml
Type: System.Management.Automation.ErrorCategory
Parameter Sets: NoException, WithException
Aliases:
Accepted values: NotSpecified, OpenError, CloseError, DeviceError, DeadlockDetected, InvalidArgument, InvalidData, InvalidOperation, InvalidResult, InvalidType, MetadataError, NotImplemented, NotInstalled, ObjectNotFound, OperationStopped, OperationTimeout, SyntaxError, ParserError, PermissionDenied, ResourceBusy, ResourceExists, ResourceUnavailable, ReadError, WriteError, FromStdErr, SecurityError, ProtocolError, ConnectionError, AuthenticationError, LimitsExceeded, QuotaExceeded, NotEnabled

Required: False
Position: Named
Default value: NotSpecified
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-172">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="bd349-172">-CategoryActivity</span></span>

<span data-ttu-id="bd349-173">오류를 발생 시킨 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-173">Specifies the action that caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Activity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-174">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="bd349-174">-CategoryReason</span></span>

<span data-ttu-id="bd349-175">활동에서 오류의 원인이 되는 방법 또는 이유를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-175">Specifies how or why the activity caused the error.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Reason

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-176">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="bd349-176">-CategoryTargetName</span></span>

<span data-ttu-id="bd349-177">오류가 발생했을 때 처리 중이던 개체의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-177">Specifies the name of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetName

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-178">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="bd349-178">-CategoryTargetType</span></span>

<span data-ttu-id="bd349-179">오류가 발생했을 때 처리 중이던 개체의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-179">Specifies the type of the object that was being processed when the error occurred.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: TargetType

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-180">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="bd349-180">-ErrorId</span></span>

<span data-ttu-id="bd349-181">오류를 식별하는 ID 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-181">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="bd349-182">오류에 대해 고유한 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-182">The string should be unique to the error.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-183">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="bd349-183">-ErrorRecord</span></span>

<span data-ttu-id="bd349-184">오류를 나타내는 오류 레코드 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-184">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="bd349-185">개체의 속성을 사용하여 오류를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-185">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="bd349-186">오류 레코드 개체를 만들려면 cmdlet을 사용 `New-Object` 하거나 자동 변수의 배열에서 오류 레코드 개체를 가져옵니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="bd349-186">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

```yaml
Type: System.Management.Automation.ErrorRecord
Parameter Sets: ErrorRecord
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-187">-예외</span><span class="sxs-lookup"><span data-stu-id="bd349-187">-Exception</span></span>

<span data-ttu-id="bd349-188">오류를 나타내는 예외 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-188">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="bd349-189">개체의 속성을 사용하여 오류를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-189">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="bd349-190">예외 개체를 만들려면 해시 테이블을 사용 하거나 cmdlet을 사용 `New-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-190">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

```yaml
Type: System.Exception
Parameter Sets: WithException
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-191">-메시지</span><span class="sxs-lookup"><span data-stu-id="bd349-191">-Message</span></span>

<span data-ttu-id="bd349-192">오류 메시지 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-192">Specifies the message text of the error.</span></span> <span data-ttu-id="bd349-193">텍스트에 공백이나 특수 문자가 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-193">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="bd349-194">메시지 문자열을로 파이프 할 수도 있습니다 `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="bd349-194">You can also pipe a message string to `Write-Error`.</span></span>

```yaml
Type: System.String
Parameter Sets: NoException, WithException
Aliases: Msg

Required: True (NoException), False (WithException)
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-195">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="bd349-195">-RecommendedAction</span></span>

<span data-ttu-id="bd349-196">오류를 해결 하거나 방지 하기 위해 사용자가 수행 해야 하는 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-196">Specifies the action that the user should take to resolve or prevent the error.</span></span>

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

### <span data-ttu-id="bd349-197">-TargetObject</span><span class="sxs-lookup"><span data-stu-id="bd349-197">-TargetObject</span></span>

<span data-ttu-id="bd349-198">오류가 발생했을 때 처리 중이던 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-198">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="bd349-199">개체, 개체가 포함 된 변수 또는 개체를 가져오는 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-199">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

```yaml
Type: System.Object
Parameter Sets: NoException, WithException
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bd349-200">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd349-200">CommonParameters</span></span>

<span data-ttu-id="bd349-201">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd349-201">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd349-202">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bd349-202">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd349-203">입력</span><span class="sxs-lookup"><span data-stu-id="bd349-203">INPUTS</span></span>

### <span data-ttu-id="bd349-204">System.String</span><span class="sxs-lookup"><span data-stu-id="bd349-204">System.String</span></span>

<span data-ttu-id="bd349-205">오류 메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="bd349-205">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="bd349-206">출력</span><span class="sxs-lookup"><span data-stu-id="bd349-206">OUTPUTS</span></span>

### <span data-ttu-id="bd349-207">Error 개체</span><span class="sxs-lookup"><span data-stu-id="bd349-207">Error object</span></span>

<span data-ttu-id="bd349-208">`Write-Error` 오류 스트림에만 씁니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-208">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="bd349-209">개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-209">It does not return any objects.</span></span>

## <span data-ttu-id="bd349-210">참고</span><span class="sxs-lookup"><span data-stu-id="bd349-210">NOTES</span></span>

<span data-ttu-id="bd349-211">`Write-Error` 는 자동 변수 값을 변경 하지 않으므로 `$?` 종료 오류 조건을 신호 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-211">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="bd349-212">종료 오류를 알리려면 [$PSCmdlet WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bd349-212">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="bd349-213">관련 링크</span><span class="sxs-lookup"><span data-stu-id="bd349-213">RELATED LINKS</span></span>

[<span data-ttu-id="bd349-214">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="bd349-214">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="bd349-215">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="bd349-215">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="bd349-216">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="bd349-216">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="bd349-217">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="bd349-217">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="bd349-218">Write-Host</span><span class="sxs-lookup"><span data-stu-id="bd349-218">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="bd349-219">Write-Output</span><span class="sxs-lookup"><span data-stu-id="bd349-219">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="bd349-220">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="bd349-220">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="bd349-221">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="bd349-221">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="bd349-222">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="bd349-222">Write-Warning</span></span>](Write-Warning.md)
