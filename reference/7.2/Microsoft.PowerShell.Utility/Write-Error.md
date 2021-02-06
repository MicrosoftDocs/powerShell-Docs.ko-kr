---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-error?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Error
ms.openlocfilehash: d0ee66e1002e4f1d58f63e198bcb7f03b1c8d3a8
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599344"
---
# <span data-ttu-id="41afe-102">Write-Error</span><span class="sxs-lookup"><span data-stu-id="41afe-102">Write-Error</span></span>

## <span data-ttu-id="41afe-103">개요</span><span class="sxs-lookup"><span data-stu-id="41afe-103">SYNOPSIS</span></span>
<span data-ttu-id="41afe-104">오류 스트림에 개체를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-104">Writes an object to the error stream.</span></span>

## <span data-ttu-id="41afe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41afe-105">SYNTAX</span></span>

### <span data-ttu-id="41afe-106">NoException (기본값)</span><span class="sxs-lookup"><span data-stu-id="41afe-106">NoException (Default)</span></span>

```
Write-Error [-Message] <String> [-Category <ErrorCategory>] [-ErrorId <String>] [-TargetObject <Object>]
 [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="41afe-107">WithException</span><span class="sxs-lookup"><span data-stu-id="41afe-107">WithException</span></span>

```
Write-Error -Exception <Exception> [[-Message] <String>] [-Category <ErrorCategory>] [-ErrorId <String>]
 [-TargetObject <Object>] [-RecommendedAction <String>] [-CategoryActivity <String>] [-CategoryReason <String>]
 [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

### <span data-ttu-id="41afe-108">ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="41afe-108">ErrorRecord</span></span>

```
Write-Error -ErrorRecord <ErrorRecord> [-RecommendedAction <String>] [-CategoryActivity <String>]
 [-CategoryReason <String>] [-CategoryTargetName <String>] [-CategoryTargetType <String>] [<CommonParameters>]
```

## <span data-ttu-id="41afe-109">설명</span><span class="sxs-lookup"><span data-stu-id="41afe-109">DESCRIPTION</span></span>

<span data-ttu-id="41afe-110">`Write-Error`Cmdlet는 종료 되지 않는 오류를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-110">The `Write-Error` cmdlet declares a non-terminating error.</span></span> <span data-ttu-id="41afe-111">기본적으로 오류는 출력과 함께 표시되도록 오류 스트림을 통해 호스트 프로그램에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-111">By default, errors are sent in the error stream to the host program to be displayed, along with output.</span></span>

<span data-ttu-id="41afe-112">종료되지 않는 오류를 쓰려면 오류 메시지 문자열, **ErrorRecord** 개체 또는 **Exception** 개체를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-112">To write a non-terminating error, enter an error message string, an **ErrorRecord** object, or an **Exception** object.</span></span> <span data-ttu-id="41afe-113">의 다른 매개 변수 `Write-Error` 를 사용 하 여 오류 레코드를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-113">Use the other parameters of `Write-Error` to populate the error record.</span></span>

<span data-ttu-id="41afe-114">종료되지 않는 오류는 오류 스트림에 오류를 쓰지만 명령 처리를 중지하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-114">Non-terminating errors write an error to the error stream, but they do not stop command processing.</span></span>
<span data-ttu-id="41afe-115">입력 항목 컬렉션에 있는 하나의 항목에서 종료되지 않는 오류가 선언될 경우 명령이 컬렉션의 다른 항목을 계속 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-115">If a non-terminating error is declared on one item in a collection of input items, the command continues to process the other items in the collection.</span></span>

<span data-ttu-id="41afe-116">종료 오류를 선언 하려면 키워드를 사용 `Throw` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-116">To declare a terminating error, use the `Throw` keyword.</span></span>
<span data-ttu-id="41afe-117">자세한 내용은 [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41afe-117">For more information, see [about_Throw](../Microsoft.PowerShell.Core/About/about_Throw.md).</span></span>

## <span data-ttu-id="41afe-118">예제</span><span class="sxs-lookup"><span data-stu-id="41afe-118">EXAMPLES</span></span>

### <span data-ttu-id="41afe-119">예 1: RegistryKey 개체에 대 한 오류 쓰기</span><span class="sxs-lookup"><span data-stu-id="41afe-119">Example 1: Write an error for RegistryKey object</span></span>

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

<span data-ttu-id="41afe-120">이 명령은 `Get-ChildItem` cmdlet이 `Microsoft.Win32.RegistryKey` `HKLM:` PowerShell 레지스트리 공급자의 또는 드라이브에 있는 개체와 같은 개체를 반환할 때 종료 되지 않는 오류를 선언 `HKCU:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-120">This command declares a non-terminating error when the `Get-ChildItem` cmdlet returns a `Microsoft.Win32.RegistryKey` object, such as the objects in the `HKLM:` or `HKCU:` drives of the PowerShell Registry provider.</span></span>

### <span data-ttu-id="41afe-121">예제 2: 콘솔에 오류 메시지 쓰기</span><span class="sxs-lookup"><span data-stu-id="41afe-121">Example 2: Write an error message to the console</span></span>

```powershell
Write-Error "Access denied."
```

<span data-ttu-id="41afe-122">이 명령은 종료되지 않는 오류를 선언하고 "액세스 거부됨" 오류를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-122">This command declares a non-terminating error and writes an "Access denied" error.</span></span> <span data-ttu-id="41afe-123">**Message** 매개 변수를 사용하여 메시지를 지정하지만 선택적 매개 변수 이름 **Message** 는 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-123">The command uses the **Message** parameter to specify the message, but omits the optional **Message** parameter name.</span></span>

### <span data-ttu-id="41afe-124">예 3: 콘솔에 오류를 기록 하 고 범주 지정</span><span class="sxs-lookup"><span data-stu-id="41afe-124">Example 3: Write an error to the console and specify the category</span></span>

```powershell
Write-Error -Message "Error: Too many input values." -Category InvalidArgument
```

<span data-ttu-id="41afe-125">이 명령은 종료되지 않는 오류를 선언하고 오류 범주를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-125">This command declares a non-terminating error and specifies an error category.</span></span>

### <span data-ttu-id="41afe-126">예제 4: 예외 개체를 사용 하 여 오류 쓰기</span><span class="sxs-lookup"><span data-stu-id="41afe-126">Example 4: Write an error using an Exception object</span></span>

```powershell
$E = [System.Exception]@{Source="Get-ParameterNames.ps1";HelpLink="https://go.microsoft.com/fwlink/?LinkID=113425"}
Write-Error -Exception $E -Message "Files not found. The $Files location does not contain any XML files."
```

<span data-ttu-id="41afe-127">이 명령은 **Exception** 개체를 사용하여 종료되지 않는 오류를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-127">This command uses an **Exception** object to declare a non-terminating error.</span></span>

<span data-ttu-id="41afe-128">첫 번째 명령은 해시 테이블을 사용하여 **System.Exception** 개체를 만들고</span><span class="sxs-lookup"><span data-stu-id="41afe-128">The first command uses a hash table to create the **System.Exception** object.</span></span> <span data-ttu-id="41afe-129">이 메서드는 예외 개체를 `$E` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-129">It saves the exception object in the `$E` variable.</span></span> <span data-ttu-id="41afe-130">해시 테이블을 사용하여 null 생성자가 있는 유형의 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-130">You can use a hash table to create any object of a type that has a null constructor.</span></span>

<span data-ttu-id="41afe-131">두 번째 명령은 cmdlet을 사용 하 여 `Write-Error` 종료 되지 않는 오류를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-131">The second command uses the `Write-Error` cmdlet to declare a non-terminating error.</span></span> <span data-ttu-id="41afe-132">**Exception** 매개 변수 값은 변수의 **예외** 개체입니다 `$E` .</span><span class="sxs-lookup"><span data-stu-id="41afe-132">The value of the **Exception** parameter is the **Exception** object in the `$E` variable.</span></span>

## <span data-ttu-id="41afe-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41afe-133">PARAMETERS</span></span>

### <span data-ttu-id="41afe-134">-범주</span><span class="sxs-lookup"><span data-stu-id="41afe-134">-Category</span></span>

<span data-ttu-id="41afe-135">오류의 범주를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-135">Specifies the category of the error.</span></span> <span data-ttu-id="41afe-136">기본값은 **NotSpecified** 입니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-136">The default value is **NotSpecified**.</span></span> <span data-ttu-id="41afe-137">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-137">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="41afe-138">NotSpecified</span><span class="sxs-lookup"><span data-stu-id="41afe-138">NotSpecified</span></span>
- <span data-ttu-id="41afe-139">OpenError</span><span class="sxs-lookup"><span data-stu-id="41afe-139">OpenError</span></span>
- <span data-ttu-id="41afe-140">CloseError</span><span class="sxs-lookup"><span data-stu-id="41afe-140">CloseError</span></span>
- <span data-ttu-id="41afe-141">DeviceError</span><span class="sxs-lookup"><span data-stu-id="41afe-141">DeviceError</span></span>
- <span data-ttu-id="41afe-142">DeadlockDetected</span><span class="sxs-lookup"><span data-stu-id="41afe-142">DeadlockDetected</span></span>
- <span data-ttu-id="41afe-143">InvalidArgument</span><span class="sxs-lookup"><span data-stu-id="41afe-143">InvalidArgument</span></span>
- <span data-ttu-id="41afe-144">InvalidData</span><span class="sxs-lookup"><span data-stu-id="41afe-144">InvalidData</span></span>
- <span data-ttu-id="41afe-145">InvalidOperation</span><span class="sxs-lookup"><span data-stu-id="41afe-145">InvalidOperation</span></span>
- <span data-ttu-id="41afe-146">InvalidResult</span><span class="sxs-lookup"><span data-stu-id="41afe-146">InvalidResult</span></span>
- <span data-ttu-id="41afe-147">InvalidType</span><span class="sxs-lookup"><span data-stu-id="41afe-147">InvalidType</span></span>
- <span data-ttu-id="41afe-148">MetadataError</span><span class="sxs-lookup"><span data-stu-id="41afe-148">MetadataError</span></span>
- <span data-ttu-id="41afe-149">NotImplemented</span><span class="sxs-lookup"><span data-stu-id="41afe-149">NotImplemented</span></span>
- <span data-ttu-id="41afe-150">NotInstalled</span><span class="sxs-lookup"><span data-stu-id="41afe-150">NotInstalled</span></span>
- <span data-ttu-id="41afe-151">ObjectNotFound</span><span class="sxs-lookup"><span data-stu-id="41afe-151">ObjectNotFound</span></span>
- <span data-ttu-id="41afe-152">OperationStopped 됨</span><span class="sxs-lookup"><span data-stu-id="41afe-152">OperationStopped</span></span>
- <span data-ttu-id="41afe-153">OperationTimeout</span><span class="sxs-lookup"><span data-stu-id="41afe-153">OperationTimeout</span></span>
- <span data-ttu-id="41afe-154">SyntaxError</span><span class="sxs-lookup"><span data-stu-id="41afe-154">SyntaxError</span></span>
- <span data-ttu-id="41afe-155">ParserError</span><span class="sxs-lookup"><span data-stu-id="41afe-155">ParserError</span></span>
- <span data-ttu-id="41afe-156">이상 거부 됨</span><span class="sxs-lookup"><span data-stu-id="41afe-156">PermissionDenied</span></span>
- <span data-ttu-id="41afe-157">ResourceBusy</span><span class="sxs-lookup"><span data-stu-id="41afe-157">ResourceBusy</span></span>
- <span data-ttu-id="41afe-158">ResourceExists</span><span class="sxs-lookup"><span data-stu-id="41afe-158">ResourceExists</span></span>
- <span data-ttu-id="41afe-159">ResourceUnavailable 수 없음</span><span class="sxs-lookup"><span data-stu-id="41afe-159">ResourceUnavailable</span></span>
- <span data-ttu-id="41afe-160">ReadError</span><span class="sxs-lookup"><span data-stu-id="41afe-160">ReadError</span></span>
- <span data-ttu-id="41afe-161">WriteError</span><span class="sxs-lookup"><span data-stu-id="41afe-161">WriteError</span></span>
- <span data-ttu-id="41afe-162">FromStdErr</span><span class="sxs-lookup"><span data-stu-id="41afe-162">FromStdErr</span></span>
- <span data-ttu-id="41afe-163">SecurityError</span><span class="sxs-lookup"><span data-stu-id="41afe-163">SecurityError</span></span>
- <span data-ttu-id="41afe-164">ProtocolError</span><span class="sxs-lookup"><span data-stu-id="41afe-164">ProtocolError</span></span>
- <span data-ttu-id="41afe-165">ConnectionError</span><span class="sxs-lookup"><span data-stu-id="41afe-165">ConnectionError</span></span>
- <span data-ttu-id="41afe-166">AuthenticationError</span><span class="sxs-lookup"><span data-stu-id="41afe-166">AuthenticationError</span></span>
- <span data-ttu-id="41afe-167">LimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="41afe-167">LimitsExceeded</span></span>
- <span data-ttu-id="41afe-168">QuotaExceeded</span><span class="sxs-lookup"><span data-stu-id="41afe-168">QuotaExceeded</span></span>
- <span data-ttu-id="41afe-169">NotEnabled</span><span class="sxs-lookup"><span data-stu-id="41afe-169">NotEnabled</span></span>

<span data-ttu-id="41afe-170">오류 범주에 대 한 자세한 내용은 [ErrorCategory 열거형](https://go.microsoft.com/fwlink/?LinkId=143600)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41afe-170">For information about the error categories, see [ErrorCategory Enumeration](https://go.microsoft.com/fwlink/?LinkId=143600).</span></span>

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

### <span data-ttu-id="41afe-171">-CategoryActivity</span><span class="sxs-lookup"><span data-stu-id="41afe-171">-CategoryActivity</span></span>

<span data-ttu-id="41afe-172">오류를 발생 시킨 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-172">Specifies the action that caused the error.</span></span>

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

### <span data-ttu-id="41afe-173">-CategoryReason</span><span class="sxs-lookup"><span data-stu-id="41afe-173">-CategoryReason</span></span>

<span data-ttu-id="41afe-174">활동에서 오류의 원인이 되는 방법 또는 이유를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-174">Specifies how or why the activity caused the error.</span></span>

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

### <span data-ttu-id="41afe-175">-CategoryTargetName</span><span class="sxs-lookup"><span data-stu-id="41afe-175">-CategoryTargetName</span></span>

<span data-ttu-id="41afe-176">오류가 발생했을 때 처리 중이던 개체의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-176">Specifies the name of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="41afe-177">-CategoryTargetType</span><span class="sxs-lookup"><span data-stu-id="41afe-177">-CategoryTargetType</span></span>

<span data-ttu-id="41afe-178">오류가 발생했을 때 처리 중이던 개체의 유형을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-178">Specifies the type of the object that was being processed when the error occurred.</span></span>

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

### <span data-ttu-id="41afe-179">-ErrorId</span><span class="sxs-lookup"><span data-stu-id="41afe-179">-ErrorId</span></span>

<span data-ttu-id="41afe-180">오류를 식별하는 ID 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-180">Specifies an ID string to identify the error.</span></span> <span data-ttu-id="41afe-181">오류에 대해 고유한 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-181">The string should be unique to the error.</span></span>

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

### <span data-ttu-id="41afe-182">-ErrorRecord</span><span class="sxs-lookup"><span data-stu-id="41afe-182">-ErrorRecord</span></span>

<span data-ttu-id="41afe-183">오류를 나타내는 오류 레코드 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-183">Specifies an error record object that represents the error.</span></span> <span data-ttu-id="41afe-184">개체의 속성을 사용하여 오류를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-184">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="41afe-185">오류 레코드 개체를 만들려면 cmdlet을 사용 `New-Object` 하거나 자동 변수의 배열에서 오류 레코드 개체를 가져옵니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="41afe-185">To create an error record object, use the `New-Object` cmdlet or get an error record object from the array in the `$Error` automatic variable.</span></span>

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

### <span data-ttu-id="41afe-186">-예외</span><span class="sxs-lookup"><span data-stu-id="41afe-186">-Exception</span></span>

<span data-ttu-id="41afe-187">오류를 나타내는 예외 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-187">Specifies an exception object that represents the error.</span></span> <span data-ttu-id="41afe-188">개체의 속성을 사용하여 오류를 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-188">Use the properties of the object to describe the error.</span></span>

<span data-ttu-id="41afe-189">예외 개체를 만들려면 해시 테이블을 사용 하거나 cmdlet을 사용 `New-Object` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-189">To create an exception object, use a hash table or use the `New-Object` cmdlet.</span></span>

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

### <span data-ttu-id="41afe-190">-메시지</span><span class="sxs-lookup"><span data-stu-id="41afe-190">-Message</span></span>

<span data-ttu-id="41afe-191">오류 메시지 텍스트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-191">Specifies the message text of the error.</span></span> <span data-ttu-id="41afe-192">텍스트에 공백이나 특수 문자가 포함되어 있으면 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-192">If the text includes spaces or special characters, enclose it in quotation marks.</span></span> <span data-ttu-id="41afe-193">메시지 문자열을로 파이프 할 수도 있습니다 `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="41afe-193">You can also pipe a message string to `Write-Error`.</span></span>

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

### <span data-ttu-id="41afe-194">-RecommendedAction</span><span class="sxs-lookup"><span data-stu-id="41afe-194">-RecommendedAction</span></span>

<span data-ttu-id="41afe-195">오류를 해결 하거나 방지 하기 위해 사용자가 수행 해야 하는 동작을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-195">Specifies the action that the user should take to resolve or prevent the error.</span></span>

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

### <span data-ttu-id="41afe-196">-TargetObject</span><span class="sxs-lookup"><span data-stu-id="41afe-196">-TargetObject</span></span>

<span data-ttu-id="41afe-197">오류가 발생했을 때 처리 중이던 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-197">Specifies the object that was being processed when the error occurred.</span></span> <span data-ttu-id="41afe-198">개체, 개체가 포함 된 변수 또는 개체를 가져오는 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-198">Enter the object, a variable that contains the object, or a command that gets the object.</span></span>

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

### <span data-ttu-id="41afe-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41afe-199">CommonParameters</span></span>

<span data-ttu-id="41afe-200">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41afe-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41afe-201">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41afe-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41afe-202">입력</span><span class="sxs-lookup"><span data-stu-id="41afe-202">INPUTS</span></span>

### <span data-ttu-id="41afe-203">System.String</span><span class="sxs-lookup"><span data-stu-id="41afe-203">System.String</span></span>

<span data-ttu-id="41afe-204">오류 메시지를 포함 하는 문자열을로 파이프 할 수 있습니다 `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="41afe-204">You can pipe a string that contains an error message to `Write-Error`.</span></span>

## <span data-ttu-id="41afe-205">출력</span><span class="sxs-lookup"><span data-stu-id="41afe-205">OUTPUTS</span></span>

### <span data-ttu-id="41afe-206">Error 개체</span><span class="sxs-lookup"><span data-stu-id="41afe-206">Error object</span></span>

<span data-ttu-id="41afe-207">`Write-Error` 오류 스트림에만 씁니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-207">`Write-Error` writes only to the error stream.</span></span> <span data-ttu-id="41afe-208">개체를 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-208">It does not return any objects.</span></span>

## <span data-ttu-id="41afe-209">참고</span><span class="sxs-lookup"><span data-stu-id="41afe-209">NOTES</span></span>

<span data-ttu-id="41afe-210">`Write-Error` 는 자동 변수 값을 변경 하지 않으므로 `$?` 종료 오류 조건을 신호 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-210">`Write-Error` does not change the value of the `$?` automatic variable, therefore it does not signal a terminating error condition.</span></span> <span data-ttu-id="41afe-211">종료 오류를 알리려면 [$PSCmdlet WriteError ()](/dotnet/api/system.management.automation.cmdlet.writeerror) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="41afe-211">To signal a terminating error, use the [$PSCmdlet.WriteError()](/dotnet/api/system.management.automation.cmdlet.writeerror) method.</span></span>

## <span data-ttu-id="41afe-212">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41afe-212">RELATED LINKS</span></span>

[<span data-ttu-id="41afe-213">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="41afe-213">about_Automatic_Variables</span></span>](../microsoft.powershell.core/about/about_automatic_variables.md)

[<span data-ttu-id="41afe-214">about_Output_Streams</span><span class="sxs-lookup"><span data-stu-id="41afe-214">about_Output_Streams</span></span>](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[<span data-ttu-id="41afe-215">about_Redirection</span><span class="sxs-lookup"><span data-stu-id="41afe-215">about_Redirection</span></span>](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[<span data-ttu-id="41afe-216">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="41afe-216">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="41afe-217">Write-Host</span><span class="sxs-lookup"><span data-stu-id="41afe-217">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="41afe-218">Write-Output</span><span class="sxs-lookup"><span data-stu-id="41afe-218">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="41afe-219">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="41afe-219">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="41afe-220">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="41afe-220">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="41afe-221">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="41afe-221">Write-Warning</span></span>](Write-Warning.md)
