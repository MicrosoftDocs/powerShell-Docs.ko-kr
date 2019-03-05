---
title: ErrorRecord 개체 해석 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: d77e4daf25bfcd5e76c184f6dbdb619368627bfa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857229"
---
# <a name="interpreting-errorrecord-objects"></a><span data-ttu-id="581d2-102">ErrorRecord 개체 해석</span><span class="sxs-lookup"><span data-stu-id="581d2-102">Interpreting ErrorRecord Objects</span></span>

<span data-ttu-id="581d2-103">대부분의 경우에는 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체 명령 또는 스크립트에서 생성 된 종료 되지 않는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-103">In most cases, an [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object represents a non-terminating error generated by a command or script.</span></span> <span data-ttu-id="581d2-104">종료 오류를 통해는 ErrorRecord의 추가 정보를 지정할 수도 합니다 [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-104">Terminating errors can also specify the additional information in an ErrorRecord via the [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interface.</span></span>

<span data-ttu-id="581d2-105">스크립트 또는 해석 해야 스크립트나 명령을 실행 하는 동안 발생 하는 특정 오류를 처리 하는 호스트에 오류 처리기를 작성 하려는 경우는 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체를 확인 하는지 여부를 것 오류를 처리 하려는 클래스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-105">If you want to write an error handler in your script or a host to handle specific errors that occur during command or script execution, you must interpret the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object to determine whether it represents the class of error that you want to handle.</span></span>

<span data-ttu-id="581d2-106">Cmdlet을 발견할 종료 하는 경우 또는 종료 되지 않는 오류, 오류 조건을 설명 하는 오류 레코드를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-106">When a cmdlet encounters a terminating or non-terminating error, it should create an error record that describes the error condition.</span></span> <span data-ttu-id="581d2-107">호스트 응용 프로그램 이러한 오류 레코드를 조사 하 고 모든 작업 오류를 완화는 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-107">The host application must investigate these error records and perform whatever action will mitigate the error.</span></span> <span data-ttu-id="581d2-108">호스트 응용 프로그램 레코드를 처리 하는 데 실패 했지만 계속 수 하는 종료 되지 않는 오류에 대 한 오류 레코드 조사 해야 하 고 중지 하려면 파이프라인 종료 오류에 대 한 오류 레코드를 조사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-108">The host application must also investigate error records for nonterminating errors that failed to process a record but were able to continue, and it must investigate error records for terminating errors that caused the pipeline to stop.</span></span>

> [!NOTE]
> <span data-ttu-id="581d2-109">종료 오류에 대 한 cmdlet을 호출 합니다 [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) 메서드.</span><span class="sxs-lookup"><span data-stu-id="581d2-109">For terminating errors, the cmdlet calls the [System.Management.Automation.Cmdlet.Throwterminatingerror\*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) method.</span></span> <span data-ttu-id="581d2-110">비종료 오류에 대 한 cmdlet을 호출 합니다 [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) 메서드.</span><span class="sxs-lookup"><span data-stu-id="581d2-110">For non-terminating errors, the cmdlet calls the [System.Management.Automation.Cmdlet.Writeerror\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) method.</span></span>

## <a name="error-record-design"></a><span data-ttu-id="581d2-111">오류 레코드 디자인</span><span class="sxs-lookup"><span data-stu-id="581d2-111">Error Record Design</span></span>

<span data-ttu-id="581d2-112">오류 레코드는 각 error 레코드에서 결합 된 정보가 고유한 지 확인 하는 동안 예외에 사용할 수 없는 추가 오류 정보를 제공 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-112">Error records are designed to provide additional error information that is not available in exceptions while ensuring that the combined information in each error record is unique.</span></span> <span data-ttu-id="581d2-113">이 고유성 오류 조건을 식별할 수 있습니다 하 고 호스트 작업을 수행 해야 있도록 error 레코드의 다른 부분을 검사 하는 호스트 응용 프로그램을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-113">This uniqueness allows the host application to inspect the different parts of the error record so that it can identify the error condition and the action the host must take.</span></span>

## <a name="interpreting-error-records"></a><span data-ttu-id="581d2-114">오류 레코드를 해석합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-114">Interpreting Error Records</span></span>

<span data-ttu-id="581d2-115">오류를 파악 하기 error 레코드의 여러 부분을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-115">You can review several parts of the error record to identify the error.</span></span> <span data-ttu-id="581d2-116">이러한 파트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-116">These parts include the following:</span></span>

- <span data-ttu-id="581d2-117">오류 범주</span><span class="sxs-lookup"><span data-stu-id="581d2-117">The error category</span></span>

- <span data-ttu-id="581d2-118">오류 예외</span><span class="sxs-lookup"><span data-stu-id="581d2-118">The error exception</span></span>

- <span data-ttu-id="581d2-119">정규화 된 오류 식별자 (FQID)</span><span class="sxs-lookup"><span data-stu-id="581d2-119">The fully qualified error identifier (FQID)</span></span>

- <span data-ttu-id="581d2-120">기타 정보</span><span class="sxs-lookup"><span data-stu-id="581d2-120">Other information</span></span>

### <a name="the-error-category"></a><span data-ttu-id="581d2-121">오류 범주</span><span class="sxs-lookup"><span data-stu-id="581d2-121">The Error Category</span></span>

<span data-ttu-id="581d2-122">Error 레코드의 오류 범주를 사용 하면 제공한 미리 정의 된 상수 중 하나인 합니다 [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-122">The error category of the error record is one of the predefined constants provided by the [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumeration.</span></span> <span data-ttu-id="581d2-123">이 정보를 통해 사용할 수는 [System.Management.Automation.Errorrecord.Categoryinfo\*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) 의 속성을 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-123">This information  is available through the [System.Management.Automation.Errorrecord.Categoryinfo\*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) property of the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.</span></span>

<span data-ttu-id="581d2-124">Cmdlet은 CloseError "," OpenError "," InvalidType "," ReadError, "및" WriteError 범주 및 기타 오류 범주를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-124">The cmdlet can specify the CloseError, OpenError, InvalidType, ReadError, and WriteError categories, and other error categories.</span></span> <span data-ttu-id="581d2-125">호스트 응용 프로그램 오류 범주를 사용 하 여 오류 그룹을 캡처할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-125">The host application can use the error category to capture groups of errors.</span></span>

### <a name="the-exception"></a><span data-ttu-id="581d2-126">예외</span><span class="sxs-lookup"><span data-stu-id="581d2-126">The Exception</span></span>

<span data-ttu-id="581d2-127">Error 레코드에 포함 된 예외는 cmdlet에서 제공 되며를 통해 액세스할 수 합니다 [System.Management.Automation.Errorrecord.Exception\*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) 의 속성을 [ System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-127">The exception included in the error record is provided by the cmdlet and can be accessed through the [System.Management.Automation.Errorrecord.Exception\*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) property of the [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object.</span></span>

<span data-ttu-id="581d2-128">호스트 응용 프로그램이 사용할 수는 `is` 예외가 특정 클래스 또는 파생된 클래스를 식별 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-128">Host applications can use the `is` keyword to identify that the exception is of a specific class or of a derived class.</span></span> <span data-ttu-id="581d2-129">다음 예제에서와 같이 것 예외 형식에 따라 분기에 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-129">It is better to branch on the exception type, as shown in the following example.</span></span>

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

<span data-ttu-id="581d2-130">이 따라서 파생된 클래스 catch 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-130">This way, you catch the derived classes.</span></span> <span data-ttu-id="581d2-131">그러나 예외를 deserialize 하는 경우 문제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-131">However, there are problems if the exception is deserialized.</span></span>

### <a name="the-fqid"></a><span data-ttu-id="581d2-132">FQID</span><span class="sxs-lookup"><span data-stu-id="581d2-132">The FQID</span></span>

<span data-ttu-id="581d2-133">FQID에 오류를 식별 하 여 가장 구체적인 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-133">The FQID is the most specific information you can use to identify the error.</span></span> <span data-ttu-id="581d2-134">Cmdlet 클래스와 오류를 보고 하는 원본 이름, cmdlet 정의 식별자를 포함 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-134">It is a string that includes a cmdlet-defined identifier, the name of the cmdlet class, and the source that reported the error.</span></span> <span data-ttu-id="581d2-135">일반적으로 오류 레코드는 Windows 이벤트 로그의 이벤트 레코드는 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-135">In general, an error record is analogous to an event record of a Windows Event log.</span></span> <span data-ttu-id="581d2-136">이벤트 레코드의 클래스를 식별 하는 다음 튜플은 FQID 비슷합니다: (*로그 이름*, *원본*합니다 *이벤트 ID*).</span><span class="sxs-lookup"><span data-stu-id="581d2-136">The FQID is analogous to the following tuple, which identifies the class of the event record: (*log name*, *source*, *event ID*).</span></span>

<span data-ttu-id="581d2-137">FQID 단일 문자열을 검사 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-137">The FQID is designed to be inspected as a single string.</span></span> <span data-ttu-id="581d2-138">그러나 사례 (가) 있는 오류 식별자는 호스트 응용 프로그램에서 구문 분석 하도록 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-138">However, cases exist in which the error identifier is designed to be parsed by the host application.</span></span> <span data-ttu-id="581d2-139">다음 예제에서는 잘 구성 된 정규화 된 오류 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-139">The following example is a well-formed fully qualified error identifier.</span></span>

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

<span data-ttu-id="581d2-140">앞의 예에서 첫 번째 토큰 오류 식별자 뒤에 cmdlet 클래스의 이름이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="581d2-140">In the previous example, the first token is the error identifier, which is followed by the name of the cmdlet class.</span></span> <span data-ttu-id="581d2-141">오류 식별자는 단일 토큰 이거나 검사 식별자의 분기에 대 한 허용 하는 마침표로 구분 식별자를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-141">The error identifier can be a single token, or it can be a dot-separated identifier that allows for branching on inspection of the identifier.</span></span> <span data-ttu-id="581d2-142">오류 식별자에 공백 또는 문장 부호를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="581d2-142">Do not use white space or punctuation in the error identifier.</span></span> <span data-ttu-id="581d2-143">것이 특히 중요를; 쉼표를 사용 하지 않도록 쉼표는 cmdlet 클래스 이름과 식별자를 구분 하려면 Windows PowerShell에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-143">It is especially important not to use a comma; a comma is used by Windows PowerShell to separate the identifier and the cmdlet class name.</span></span>

### <a name="other-information"></a><span data-ttu-id="581d2-144">기타 정보</span><span class="sxs-lookup"><span data-stu-id="581d2-144">Other Information</span></span>

<span data-ttu-id="581d2-145">합니다 [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) 개체 오류가 발생 한 환경을 설명 하는 정보를 제공할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-145">The [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) object might also provide information that describes the environment in which the error occurred.</span></span> <span data-ttu-id="581d2-146">이 정보에는 오류 세부 정보, 호출 정보 및 오류가 발생할 때 처리 중이 던는 대상 개체와 같은 항목이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-146">This information includes items such as error details, invocation information, and the target object that was being processed when the error occurred.</span></span> <span data-ttu-id="581d2-147">이 정보는 호스트 응용 프로그램에 유용 하지만 오류를 파악 하기 일반적으로 사용 되는 것은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-147">Although this information might be useful to the host application, it is not typically used to identify the error.</span></span> <span data-ttu-id="581d2-148">이 정보는 다음 속성을 통해 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-148">This information is available through the following properties:</span></span>

[<span data-ttu-id="581d2-149">System.Management.Automation.Errorrecord.Errordetails\*</span><span class="sxs-lookup"><span data-stu-id="581d2-149">System.Management.Automation.Errorrecord.Errordetails\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[<span data-ttu-id="581d2-150">System.Management.Automation.Errorrecord.Invocationinfo\*</span><span class="sxs-lookup"><span data-stu-id="581d2-150">System.Management.Automation.Errorrecord.Invocationinfo\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[<span data-ttu-id="581d2-151">System.Management.Automation.Errorrecord.Targetobject\*</span><span class="sxs-lookup"><span data-stu-id="581d2-151">System.Management.Automation.Errorrecord.Targetobject\*</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a><span data-ttu-id="581d2-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="581d2-152">See Also</span></span>

[<span data-ttu-id="581d2-153">System.Management.Automation.Errorrecord</span><span class="sxs-lookup"><span data-stu-id="581d2-153">System.Management.Automation.Errorrecord</span></span>](/dotnet/api/System.Management.Automation.ErrorRecord)

[<span data-ttu-id="581d2-154">System.Management.Automation.Errorcategory</span><span class="sxs-lookup"><span data-stu-id="581d2-154">System.Management.Automation.Errorcategory</span></span>](/dotnet/api/System.Management.Automation.ErrorCategory)

[<span data-ttu-id="581d2-155">System.Management.Automation.Errorcategoryinfo</span><span class="sxs-lookup"><span data-stu-id="581d2-155">System.Management.Automation.Errorcategoryinfo</span></span>](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[<span data-ttu-id="581d2-156">System.Management.Automation.Cmdlet.Writeerror\*</span><span class="sxs-lookup"><span data-stu-id="581d2-156">System.Management.Automation.Cmdlet.Writeerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[<span data-ttu-id="581d2-157">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span><span class="sxs-lookup"><span data-stu-id="581d2-157">System.Management.Automation.Cmdlet.Throwterminatingerror\*</span></span>](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[<span data-ttu-id="581d2-158">비종료 오류 보고를 Cmdlet에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="581d2-158">Adding Non-Terminating Error Reporting to Your Cmdlet</span></span>](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[<span data-ttu-id="581d2-159">Windows PowerShell 오류 보고</span><span class="sxs-lookup"><span data-stu-id="581d2-159">Windows PowerShell Error Reporting</span></span>](./error-reporting-concepts.md)

<span data-ttu-id="581d2-160">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="581d2-160">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>