---
ms.date: 09/13/2016
ms.topic: reference
title: 공급자 도움말 항목에 동적 매개 변수를 추가하는 방법
description: 공급자 도움말 항목에 동적 매개 변수를 추가하는 방법
ms.openlocfilehash: 9542538cfacf5fb293ca8d1350b80fb250c71ac6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649644"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="d9457-103">공급자 도움말 항목에 동적 매개 변수를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="d9457-103">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="d9457-104">이 섹션에서는 공급자 도움말 항목의 **동적 매개 변수** 섹션을 채우는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-104">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="d9457-105">*동적 매개 변수* 는 지정 된 조건 에서만 사용할 수 있는 cmdlet 또는 함수의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-105">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="d9457-106">공급자 도움말 항목에 설명 된 동적 매개 변수는 공급자 드라이브에서 cmdlet 또는 함수를 사용할 때 공급자가 cmdlet 또는 함수에 추가 하는 동적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-106">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="d9457-107">동적 매개 변수는 공급자에 대 한 사용자 지정 cmdlet 도움말에도 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-107">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="d9457-108">공급자 도움말과 사용자 지정 cmdlet 도움말을 모두 작성할 때 두 문서 모두에 동적 매개 변수 설명서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-108">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="d9457-109">공급자가 동적 매개 변수를 구현 하지 않으면 공급자 도움말 항목에 빈 `DynamicParameters` 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="d9457-110">동적 매개 변수를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="d9457-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="d9457-111">파일의 `<AssemblyName>.dll-help.xml` 요소 내에 `providerHelp` 요소를 추가 `DynamicParameters` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-111">In the `<AssemblyName>.dll-help.xml` file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="d9457-112">요소는 요소 `DynamicParameters` 뒤 `Tasks` 와 요소 앞에 표시 되어야 합니다 `RelatedLinks` .</span><span class="sxs-lookup"><span data-stu-id="d9457-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="d9457-113">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="d9457-113">For example:</span></span>

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   <span data-ttu-id="d9457-114">공급자가 동적 매개 변수를 구현 하지 않는 경우 `DynamicParameters` 요소는 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

1. <span data-ttu-id="d9457-115">요소 내에서 `DynamicParameters` 각 동적 매개 변수에 대해 요소를 추가 `DynamicParameter` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="d9457-116">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="d9457-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

1. <span data-ttu-id="d9457-117">각 `DynamicParameter` 요소에서 `Name` 및 요소를 추가 `CmdletSupported` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   - <span data-ttu-id="d9457-118">이름-매개 변수 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-118">Name - Specifies the parameter name</span></span>
   - <span data-ttu-id="d9457-119">CmdletSupported-매개 변수가 유효한 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-119">CmdletSupported - Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="d9457-120">쉼표로 구분 된 cmdlet 이름 목록을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-120">Type a comma-separated list of cmdlet names.</span></span>

   <span data-ttu-id="d9457-121">예를 들어 다음 XML은 `Encoding` Windows PowerShell 파일 시스템 공급자가 `Add-Content` ,, cmdlet에 추가 하는 동적 매개 변수를 문서화 합니다 `Get-Content` `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="d9457-121">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

1. <span data-ttu-id="d9457-122">각 `DynamicParameter` 요소에서 요소를 추가 `Type` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-122">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="d9457-123">`Type`요소는 `Name` 동적 매개 변수 값의 .net 형식을 포함 하는 요소에 대 한 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-123">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="d9457-124">예를 들어 다음 XML에서는 `Encoding` 동적 매개 변수의 .net 형식이 [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 열거형 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-124">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

1. <span data-ttu-id="d9457-125">`Description`동적 매개 변수에 대 한 간단한 설명을 포함 하는 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-125">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="d9457-126">설명을 작성할 때 [매개 변수 정보를 추가 하는 방법](./how-to-add-parameter-information.md)의 모든 cmdlet 매개 변수에 대해 지정 된 지침을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-126">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="d9457-127">예를 들어 다음 XML에는 동적 매개 변수에 대 한 설명이 포함 되어 있습니다 `Encoding` .</span><span class="sxs-lookup"><span data-stu-id="d9457-127">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

1. <span data-ttu-id="d9457-128">`PossibleValues`요소와 해당 자식 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-128">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="d9457-129">이러한 요소는 모두 동적 매개 변수의 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-129">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="d9457-130">이 요소는 열거 값을 위해 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-130">This element is designed for enumerated values.</span></span> <span data-ttu-id="d9457-131">스위치 매개 변수를 사용 하는 경우와 같이 동적 매개 변수가 값을 사용 하지 않거나 값을 열거할 수 없는 경우 빈 요소를 추가 `PossibleValues` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-131">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="d9457-132">다음 표에서는 `PossibleValues` 요소 및 해당 자식 요소를 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-132">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   - <span data-ttu-id="d9457-133">PossibleValues-이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-133">PossibleValues - This element is a container.</span></span> <span data-ttu-id="d9457-134">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-134">Its child elements are described below.</span></span> <span data-ttu-id="d9457-135">`PossibleValues`각 공급자 도움말 항목에 요소를 하나씩 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-135">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="d9457-136">요소는 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-136">The element can be empty.</span></span>
   - <span data-ttu-id="d9457-137">PossibleValue-이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-137">PossibleValue - This element is a container.</span></span> <span data-ttu-id="d9457-138">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-138">Its child elements are described below.</span></span> <span data-ttu-id="d9457-139">`PossibleValue`동적 매개 변수의 각 값에 대해 하나의 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-139">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>
   - <span data-ttu-id="d9457-140">값-값 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-140">Value - Specifies the value name.</span></span>
   - <span data-ttu-id="d9457-141">설명-이 요소는 요소를 포함 `Para` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9457-141">Description - This element contains a `Para` element.</span></span> <span data-ttu-id="d9457-142">요소의 텍스트는 `Para` 요소에 명명 된 값을 설명 합니다 `Value` .</span><span class="sxs-lookup"><span data-stu-id="d9457-142">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>

   <span data-ttu-id="d9457-143">예를 들어 다음 XML은 `PossibleValue` 동적 매개 변수의 한 요소를 보여 줍니다 `Encoding` .</span><span class="sxs-lookup"><span data-stu-id="d9457-143">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a><span data-ttu-id="d9457-144">예제</span><span class="sxs-lookup"><span data-stu-id="d9457-144">Example</span></span>

<span data-ttu-id="d9457-145">다음 예에서는 `DynamicParameters` 동적 매개 변수의 요소를 보여 줍니다 `Encoding` .</span><span class="sxs-lookup"><span data-stu-id="d9457-145">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```
