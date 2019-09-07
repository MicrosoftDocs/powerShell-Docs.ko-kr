---
title: 공급자 도움말 항목에 동적 매개 변수를 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737593"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="9b0e2-102">공급자 도움말 항목에 동적 매개 변수를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="9b0e2-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="9b0e2-103">이 섹션에서는 공급자 도움말 항목의 **동적 매개 변수** 섹션을 채우는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="9b0e2-104">*동적 매개 변수* 는 지정 된 조건 에서만 사용할 수 있는 cmdlet 또는 함수의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="9b0e2-105">공급자 도움말 항목에 설명 된 동적 매개 변수는 공급자 드라이브에서 cmdlet 또는 함수를 사용할 때 공급자가 cmdlet 또는 함수에 추가 하는 동적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="9b0e2-106">동적 매개 변수는 공급자에 대 한 사용자 지정 cmdlet 도움말에도 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="9b0e2-107">공급자 도움말과 사용자 지정 cmdlet 도움말을 모두 작성할 때 두 문서 모두에 동적 매개 변수 설명서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="9b0e2-108">사용자 지정 cmdlet 도움말에 대 한 자세한 내용은 [공급자에 대 한 Windows PowerShell 사용자 지정 Cmdlet 도움말 작성](./writing-custom-cmdlet-help-for-windows-powershell-providers.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="9b0e2-109">공급자가 동적 매개 변수를 구현 하지 않으면 공급자 도움말 항목에 빈 `DynamicParameters` 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="9b0e2-110">동적 매개 변수를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="9b0e2-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="9b0e2-111">Dll-help 파일 `providerHelp` 의`DynamicParameters` 요소 내에서 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="9b0e2-112">요소는 요소 `Tasks` 뒤와 `RelatedLinks` 요소 앞에 표시 되어야 합니다. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="9b0e2-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="9b0e2-113">예:</span><span class="sxs-lookup"><span data-stu-id="9b0e2-113">For example:</span></span>

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

   <span data-ttu-id="9b0e2-114">공급자가 동적 매개 변수를 구현 하지 않는 경우 요소 `DynamicParameters` 는 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="9b0e2-115">요소 내에서 각 동적 매개 변수에 대해 `DynamicParameter` 요소를 추가 합니다. `DynamicParameters`</span><span class="sxs-lookup"><span data-stu-id="9b0e2-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="9b0e2-116">예:</span><span class="sxs-lookup"><span data-stu-id="9b0e2-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="9b0e2-117">각 `DynamicParameter` 요소에서 `Name` 및 `CmdletSupported` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="9b0e2-118">요소 이름</span><span class="sxs-lookup"><span data-stu-id="9b0e2-118">Element Name</span></span>|<span data-ttu-id="9b0e2-119">Description</span><span class="sxs-lookup"><span data-stu-id="9b0e2-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="9b0e2-120">이름</span><span class="sxs-lookup"><span data-stu-id="9b0e2-120">Name</span></span>|<span data-ttu-id="9b0e2-121">매개 변수 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="9b0e2-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="9b0e2-122">CmdletSupported</span></span>|<span data-ttu-id="9b0e2-123">매개 변수가 유효한 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="9b0e2-124">쉼표로 구분 된 cmdlet 이름 목록을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="9b0e2-125">예를 들어 다음 XML은 Windows PowerShell `Encoding` 파일 시스템 공급자가 `Add-Content`, `Get-Content`, `Set-Content` cmdlet에 추가 하는 동적 매개 변수를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="9b0e2-126">각 `DynamicParameter` 요소에서 `Type` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="9b0e2-127">요소는 동적 매개 변수 값의 `Name` .net 형식을 포함 하는 요소에 대 한 컨테이너입니다. `Type`</span><span class="sxs-lookup"><span data-stu-id="9b0e2-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="9b0e2-128">예를 들어 다음 XML에서는 `Encoding` 동적 매개 변수의 .net 형식이 [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 열거형 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="9b0e2-129">동적 매개 변수에 대 한 간단한 설명을 포함 하는 요소를추가합니다.`Description`</span><span class="sxs-lookup"><span data-stu-id="9b0e2-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="9b0e2-130">설명을 작성할 때 [매개 변수 정보를 추가 하는 방법](./how-to-add-parameter-information.md)의 모든 cmdlet 매개 변수에 대해 지정 된 지침을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="9b0e2-131">예를 들어 다음 XML에는 `Encoding` 동적 매개 변수에 대 한 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="9b0e2-132">요소와 `PossibleValues` 해당 자식 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="9b0e2-133">이러한 요소는 모두 동적 매개 변수의 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="9b0e2-134">이 요소는 열거 값을 위해 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="9b0e2-135">스위치 매개 변수를 사용 하는 경우와 같이 동적 매개 변수가 값을 사용 하지 않거나 값을 열거할 수 없는 경우 빈 `PossibleValues` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="9b0e2-136">다음 표에서는 요소 및 해당 자식 `PossibleValues` 요소를 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="9b0e2-137">요소 이름</span><span class="sxs-lookup"><span data-stu-id="9b0e2-137">Element Name</span></span>|<span data-ttu-id="9b0e2-138">Description</span><span class="sxs-lookup"><span data-stu-id="9b0e2-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="9b0e2-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="9b0e2-139">PossibleValues</span></span>|<span data-ttu-id="9b0e2-140">이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-140">This element is a container.</span></span> <span data-ttu-id="9b0e2-141">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-141">Its child elements are described below.</span></span> <span data-ttu-id="9b0e2-142">각 공급자 `PossibleValues` 도움말 항목에 요소를 하나씩 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="9b0e2-143">요소는 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-143">The element can be empty.</span></span>|
   |<span data-ttu-id="9b0e2-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="9b0e2-144">PossibleValue</span></span>|<span data-ttu-id="9b0e2-145">이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-145">This element is a container.</span></span> <span data-ttu-id="9b0e2-146">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-146">Its child elements are described below.</span></span> <span data-ttu-id="9b0e2-147">동적 매개 `PossibleValue` 변수의 각 값에 대해 하나의 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="9b0e2-148">값</span><span class="sxs-lookup"><span data-stu-id="9b0e2-148">Value</span></span>|<span data-ttu-id="9b0e2-149">값 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="9b0e2-150">Description</span><span class="sxs-lookup"><span data-stu-id="9b0e2-150">Description</span></span>|<span data-ttu-id="9b0e2-151">이 요소는 요소 `Para` 를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-151">This element contains a `Para` element.</span></span> <span data-ttu-id="9b0e2-152">`Para` 요소의 텍스트는 `Value` 요소에 명명 된 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="9b0e2-153">예를 들어 다음 XML은 `PossibleValue` `Encoding` 동적 매개 변수의 한 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="9b0e2-154">예제</span><span class="sxs-lookup"><span data-stu-id="9b0e2-154">Example</span></span>

<span data-ttu-id="9b0e2-155">다음 예에서는 `Encoding` 동적 매개 `DynamicParameters` 변수의 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b0e2-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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