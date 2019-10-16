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
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361262"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="b71e1-102">공급자 도움말 항목에 동적 매개 변수를 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="b71e1-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="b71e1-103">이 섹션에서는 공급자 도움말 항목의 **동적 매개 변수** 섹션을 채우는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="b71e1-104">*동적 매개 변수* 는 지정 된 조건 에서만 사용할 수 있는 cmdlet 또는 함수의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="b71e1-105">공급자 도움말 항목에 설명 된 동적 매개 변수는 공급자 드라이브에서 cmdlet 또는 함수를 사용할 때 공급자가 cmdlet 또는 함수에 추가 하는 동적 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="b71e1-106">동적 매개 변수는 공급자에 대 한 사용자 지정 cmdlet 도움말에도 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="b71e1-107">공급자 도움말과 사용자 지정 cmdlet 도움말을 모두 작성할 때 두 문서 모두에 동적 매개 변수 설명서를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="b71e1-108">공급자가 동적 매개 변수를 구현 하지 않으면 공급자 도움말 항목에 빈 `DynamicParameters` 요소가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="b71e1-109">동적 매개 변수를 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="b71e1-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="b71e1-110">Dll-help 파일의 `providerHelp` 요소 내에서 `DynamicParameters` 요소를 추가 *합니다.*</span><span class="sxs-lookup"><span data-stu-id="b71e1-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="b71e1-111">@No__t-0 요소는 `Tasks` 요소와 `RelatedLinks` 요소 앞에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="b71e1-112">예:</span><span class="sxs-lookup"><span data-stu-id="b71e1-112">For example:</span></span>

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

   <span data-ttu-id="b71e1-113">공급자가 동적 매개 변수를 구현 하지 않는 경우 `DynamicParameters` 요소가 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="b71e1-114">@No__t-0 요소 내에서 각 동적 매개 변수에 대해 `DynamicParameter` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="b71e1-115">예:</span><span class="sxs-lookup"><span data-stu-id="b71e1-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="b71e1-116">각 `DynamicParameter` 요소에서 `Name` 및 `CmdletSupported` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="b71e1-117">요소 이름</span><span class="sxs-lookup"><span data-stu-id="b71e1-117">Element Name</span></span>|<span data-ttu-id="b71e1-118">설명</span><span class="sxs-lookup"><span data-stu-id="b71e1-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="b71e1-119">Name</span><span class="sxs-lookup"><span data-stu-id="b71e1-119">Name</span></span>|<span data-ttu-id="b71e1-120">매개 변수 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="b71e1-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="b71e1-121">CmdletSupported</span></span>|<span data-ttu-id="b71e1-122">매개 변수가 유효한 cmdlet을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="b71e1-123">쉼표로 구분 된 cmdlet 이름 목록을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="b71e1-124">예를 들어 다음 XML은 Windows PowerShell 파일 시스템 공급자가 `Add-Content`, `Get-Content` @no__t cmdlet에 추가 하는 `Encoding` 동적 매개 변수를 문서화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="b71e1-125">각 `DynamicParameter` 요소에서 `Type` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="b71e1-126">@No__t-0 요소는 동적 매개 변수 값의 .NET 형식을 포함 하는 `Name` 요소의 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="b71e1-127">예를 들어 다음 XML은 `Encoding` 동적 매개 변수의 .NET 형식이 [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 열거형 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="b71e1-128">동적 매개 변수에 대 한 간단한 설명을 포함 하는 `Description` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="b71e1-129">설명을 작성할 때 [매개 변수 정보를 추가 하는 방법](./how-to-add-parameter-information.md)의 모든 cmdlet 매개 변수에 대해 지정 된 지침을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="b71e1-130">예를 들어 다음 XML에는 `Encoding` 동적 매개 변수에 대 한 설명이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="b71e1-131">@No__t-0 요소 및 해당 자식 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="b71e1-132">이러한 요소는 모두 동적 매개 변수의 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="b71e1-133">이 요소는 열거 값을 위해 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="b71e1-134">스위치 매개 변수를 사용 하는 경우와 같이 동적 매개 변수가 값을 사용 하지 않거나 값을 열거할 수 없으면 빈 `PossibleValues` 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="b71e1-135">다음 표에서는 `PossibleValues` 요소 및 해당 자식 요소를 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="b71e1-136">요소 이름</span><span class="sxs-lookup"><span data-stu-id="b71e1-136">Element Name</span></span>|<span data-ttu-id="b71e1-137">설명</span><span class="sxs-lookup"><span data-stu-id="b71e1-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="b71e1-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="b71e1-138">PossibleValues</span></span>|<span data-ttu-id="b71e1-139">이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-139">This element is a container.</span></span> <span data-ttu-id="b71e1-140">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-140">Its child elements are described below.</span></span> <span data-ttu-id="b71e1-141">각 공급자 도움말 항목에 `PossibleValues` 요소 하나를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="b71e1-142">요소는 비어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-142">The element can be empty.</span></span>|
   |<span data-ttu-id="b71e1-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="b71e1-143">PossibleValue</span></span>|<span data-ttu-id="b71e1-144">이 요소는 컨테이너입니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-144">This element is a container.</span></span> <span data-ttu-id="b71e1-145">자식 요소는 아래에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-145">Its child elements are described below.</span></span> <span data-ttu-id="b71e1-146">동적 매개 변수의 각 값에 대해 `PossibleValue` 요소를 하나 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="b71e1-147">Value</span><span class="sxs-lookup"><span data-stu-id="b71e1-147">Value</span></span>|<span data-ttu-id="b71e1-148">값 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="b71e1-149">설명</span><span class="sxs-lookup"><span data-stu-id="b71e1-149">Description</span></span>|<span data-ttu-id="b71e1-150">이 요소는 `Para` 요소를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-150">This element contains a `Para` element.</span></span> <span data-ttu-id="b71e1-151">@No__t-0 요소의 텍스트는 `Value` 요소에 명명 된 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="b71e1-152">예를 들어 다음 XML은 `Encoding` 동적 매개 변수의 한 `PossibleValue` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="b71e1-153">예제</span><span class="sxs-lookup"><span data-stu-id="b71e1-153">Example</span></span>

<span data-ttu-id="b71e1-154">다음 예에서는 `Encoding` 동적 매개 변수의 `DynamicParameters` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b71e1-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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