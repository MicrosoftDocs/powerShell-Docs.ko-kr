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
ms.openlocfilehash: 57978616f4a868b1ad260f4b557f9b699a1ef3ab
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557127"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>공급자 도움말 항목에 동적 매개 변수를 추가하는 방법

이 섹션에서는 공급자 도움말 항목의 **동적 매개 변수** 섹션을 채우는 방법에 대해 설명 합니다.

*동적 매개 변수* 는 지정 된 조건 에서만 사용할 수 있는 cmdlet 또는 함수의 매개 변수입니다.

공급자 도움말 항목에 설명 된 동적 매개 변수는 공급자 드라이브에서 cmdlet 또는 함수를 사용할 때 공급자가 cmdlet 또는 함수에 추가 하는 동적 매개 변수입니다.

동적 매개 변수는 공급자에 대 한 사용자 지정 cmdlet 도움말에도 설명 되어 있습니다. 공급자 도움말과 사용자 지정 cmdlet 도움말을 모두 작성할 때 두 문서 모두에 동적 매개 변수 설명서를 포함 합니다.

공급자가 동적 매개 변수를 구현 하지 않으면 공급자 도움말 항목에 빈 `DynamicParameters` 요소가 포함 됩니다.

### <a name="to-add-dynamic-parameters"></a>동적 매개 변수를 추가 하려면

1. Dll-help 파일 *AssemblyName*의 요소 내에서 `providerHelp` 요소를 추가 `DynamicParameters` 합니다. 요소는 요소 `DynamicParameters` 뒤 `Tasks` 와 요소 앞에 표시 되어야 합니다 `RelatedLinks` .

   다음은 그 예입니다.

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

   공급자가 동적 매개 변수를 구현 하지 않는 경우 `DynamicParameters` 요소는 비어 있을 수 있습니다.

2. 요소 내에서 `DynamicParameters` 각 동적 매개 변수에 대해 요소를 추가 `DynamicParameter` 합니다.

   다음은 그 예입니다.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. 각 `DynamicParameter` 요소에서 `Name` 및 요소를 추가 `CmdletSupported` 합니다.

   |요소 이름|설명|
   |------------------|-----------------|
   |이름|매개 변수 이름을 지정 합니다.|
   |CmdletSupported|매개 변수가 유효한 cmdlet을 지정 합니다. 쉼표로 구분 된 cmdlet 이름 목록을 입력 합니다.|

   예를 들어 다음 XML은 `Encoding` Windows PowerShell 파일 시스템 공급자가 `Add-Content` ,, cmdlet에 추가 하는 동적 매개 변수를 문서화 합니다 `Get-Content` `Set-Content` .

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. 각 `DynamicParameter` 요소에서 요소를 추가 `Type` 합니다. `Type`요소는 `Name` 동적 매개 변수 값의 .net 형식을 포함 하는 요소에 대 한 컨테이너입니다.

   예를 들어 다음 XML에서는 `Encoding` 동적 매개 변수의 .net 형식이 [FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) 열거형 임을 보여 줍니다.

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

5. `Description`동적 매개 변수에 대 한 간단한 설명을 포함 하는 요소를 추가 합니다. 설명을 작성할 때 [매개 변수 정보를 추가 하는 방법](./how-to-add-parameter-information.md)의 모든 cmdlet 매개 변수에 대해 지정 된 지침을 사용 합니다.

   예를 들어 다음 XML에는 동적 매개 변수에 대 한 설명이 포함 되어 있습니다 `Encoding` .

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

6. `PossibleValues`요소와 해당 자식 요소를 추가 합니다. 이러한 요소는 모두 동적 매개 변수의 값을 설명 합니다. 이 요소는 열거 값을 위해 디자인 되었습니다. 스위치 매개 변수를 사용 하는 경우와 같이 동적 매개 변수가 값을 사용 하지 않거나 값을 열거할 수 없는 경우 빈 요소를 추가 `PossibleValues` 합니다.

   다음 표에서는 `PossibleValues` 요소 및 해당 자식 요소를 나열 하 고 설명 합니다.

   |요소 이름|설명|
   |------------------|-----------------|
   |PossibleValues|이 요소는 컨테이너입니다. 자식 요소는 아래에 설명 되어 있습니다. `PossibleValues`각 공급자 도움말 항목에 요소를 하나씩 추가 합니다. 요소는 비어 있을 수 있습니다.|
   |PossibleValue|이 요소는 컨테이너입니다. 자식 요소는 아래에 설명 되어 있습니다. `PossibleValue`동적 매개 변수의 각 값에 대해 하나의 요소를 추가 합니다.|
   |Value|값 이름을 지정 합니다.|
   |설명|이 요소는 요소를 포함 `Para` 합니다. 요소의 텍스트는 `Para` 요소에 명명 된 값을 설명 합니다 `Value` .|

   예를 들어 다음 XML은 `PossibleValue` 동적 매개 변수의 한 요소를 보여 줍니다 `Encoding` .

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

## <a name="example"></a>예제

다음 예에서는 `DynamicParameters` 동적 매개 변수의 요소를 보여 줍니다 `Encoding` .

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
